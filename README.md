# POC JNI Whitelist

This project shows how adding the build flag `-H:JNIConfigurationFiles=xxx` causes some build error that is seemingly unrelated to the content of the configuration. If the file `jniconfig.json` is changed to be an empty array the build works fine.

The error complains about not finding a class that truly isn't there (at least not explicitly). This class can be added when adding a dependency to `implementation 'io.netty:netty-tcnative-boringssl-static'`. This requires some additional configurations to inform some classes to be initialized at run time. When these changes are done another compile error occurrs saying that `org.conscrypt.BufferAllocator` is missing, like found in this [issue](https://github.com/quarkusio/quarkus/issues/4248).

