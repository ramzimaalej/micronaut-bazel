load("@rules_java//java:defs.bzl", "java_binary", "java_library", "java_plugin", "java_test")

java_plugin(
    name = "type_element_annotation_processor",
    processor_class = "io.micronaut.annotation.processing.TypeElementVisitorProcessor",
    deps = [
        "@maven//:io_micronaut_micronaut_inject_java",
        "@maven//:io_micronaut_micronaut_aop",
        "@maven//:io_micronaut_micronaut_inject",
        "@maven//:io_micronaut_micronaut_validation"
    ]
)

java_plugin(
    name = "aggregating_type_element_annotation_processor",
    processor_class = "io.micronaut.annotation.processing.AggregatingTypeElementVisitorProcessor",
    deps = [
        "@maven//:io_micronaut_micronaut_inject_java",
        "@maven//:io_micronaut_micronaut_aop",
        "@maven//:io_micronaut_micronaut_inject",
        "@maven//:io_micronaut_micronaut_validation"
    ]
)

java_plugin(
    name = "bean_definition_annotation_processor",
    processor_class = "io.micronaut.annotation.processing.BeanDefinitionInjectProcessor",
    deps = [
        "@maven//:io_micronaut_micronaut_inject_java",
        "@maven//:io_micronaut_micronaut_aop",
        "@maven//:io_micronaut_micronaut_inject",
        "@maven//:io_micronaut_micronaut_validation"
    ]
)

java_plugin(
    name = "service_descriptor_annotation_processor",
    processor_class = "io.micronaut.annotation.processing.ServiceDescriptionProcessor",
    deps = [
        "@maven//:io_micronaut_micronaut_inject_java",
        "@maven//:io_micronaut_micronaut_aop",
        "@maven//:io_micronaut_micronaut_inject",
        "@maven//:io_micronaut_micronaut_validation"
    ]
)

java_library(
    name = "micronaut_libs",
    exported_plugins = ["service_descriptor_annotation_processor","type_element_annotation_processor","aggregating_type_element_annotation_processor", "bean_definition_annotation_processor"],
    exports = [
        "@maven//:io_micronaut_micronaut_inject_java",
        "@maven//:io_micronaut_micronaut_aop",
        "@maven//:io_micronaut_micronaut_inject",
        "@maven//:io_micronaut_micronaut_validation"
    ]
)

java_library(
    name = "backend_deps",
    resources = glob(["src/backend/src/main/resources/**/*.xml", "src/backend/src/main/resources/**/*.yml"]),
    exports = [
         "@maven//:ch_qos_logback_logback_classic",
         "@maven//:io_micronaut_micronaut_runtime",
         "@maven//:io_micronaut_micronaut_http_server_netty",
         "@maven//:io_micronaut_micronaut_http_client",
         "@maven//:io_micronaut_micronaut_core",
         "@maven//:io_micronaut_micronaut_context",
         "@maven//:io_micronaut_micronaut_validation",
         "@maven//:io_micronaut_micronaut_aop",
         "@maven//:io_micronaut_micronaut_inject",
         "@maven//:io_micronaut_micronaut_inject_java"
    ]
)

java_library(
    name = "backend_libs",
    srcs = glob(["src/backend/src/main/java/**/*.java"]),
    deps = [
        ":micronaut_libs",
        ":backend_deps",
    ],
)

java_binary(
    name = "backend-services",
    main_class = "com.example.Application",
    runtime_deps = [":backend_libs"]
)
