# EMQ X Kuiper - 超轻量物联网边缘数据分析软件

[English](README.md) | [简体中文](README-CN.md)

## 概览

EMQ X Kuiper 是 Golang 实现的轻量级物联网边缘分析、流式处理开源软件，可以运行在各类资源受限的边缘设备上。Kuiper 设计的一个主要目标就是将在云端运行的实时流式计算框架（比如 [Apache Spark](https://spark.apache.org)，[Apache Storm](https://storm.apache.org) 和 [Apache Flink](https://flink.apache.org) 等）迁移到边缘端。Kuiper 参考了上述云端流式处理项目的架构与实现，结合边缘流式数据处理的特点，采用了编写基于``源 (Source)``，``SQL (业务逻辑处理)``, ``目标 (Sink)`` 的规则引擎来实现边缘端的流式数据处理。

![arch](docs/resources/arch.png)

**应用场景**

Kuiper 可以运行在各类物联网的边缘使用场景中，比如工业物联网中对生产线数据进行实时处理；车联网中的车机对来自汽车总线数据的即时分析；智能城市场景中，对来自于各类城市设施数据的实时分析。通过 Kuiper 在边缘端的处理，可以提升系统响应速度，节省网络带宽费用和存储成本，以及提高系统安全性等。

## 功能

- 超轻量

  - 核心服务安装包约 3.5MB，初始运行时占用内存约 10MB

- 跨平台

  - 流行 CPU 架构：X86 AMD * 32, X86 AMD * 64; ARM * 32, ARM * 64位; PPC
  - 常见 Linux 发行版、MacOS、Docker 等
  - 工控机、树莓派、工业网关、家庭网关、MEC 边缘云等

- 完整的数据分析

  - 通过 SQL 支持数据抽取、转换和过滤
  - 数据排序、分组、聚合、连接
  - 60+ 各类函数，覆盖数学运算、字符串处理、聚合运算和哈希运算等
  - 4 类时间窗口

- 高可扩展性

  提供插件扩展机制，可以支持在``源 (Source)``，``SQL 函数 ``, ``目标 (Sink)`` 三个方面的扩展

  - 源 (Source) ：内置支持 MQTT 数据的接入，提供了扩展点支持任意的类型的接入
  - 目标(Sink)：内置支持 MQTT、HTTP，提供扩展点支持任意数据目标的支持
  - SQL 函数：内置支持60+常见的函数，提供扩展点可以扩展自定义函数

- 管理能力

  - 命令行对流、规则进行管理
  - 通过 REST API 也可以流与规则进行管理（规划中）
  - 与 [KubeEdge](https://github.com/kubeedge/kubeedge)、[K3s](https://github.com/rancher/k3s) 等基于边缘 Kubernetes 框架的集成能力

- 与 EMQ X Edge 集成

  提供了与 EMQ X Edge 的无缝集成，实现在边缘端从消息接入到数据分析端到端的场景实现能力

<!--性能测试结果-->

## 文档

- [开始使用](docs/zh_CN/getting_started.md) 

- [参考指南](docs/zh_CN/reference.md)
  - [安装与操作](docs/zh_CN/operation/overview.md)
  - [命令行界面工具-CLI](docs/zh_CN/cli/overview.md)
  - [Kuiper SQL参考](docs/zh_CN/sqls/overview.md)
  - [规则](docs/zh_CN/rules/overview.md)
  - [扩展Kuiper](docs/zh_CN/extension/overview.md)
  - [插件](docs/zh_CN/plugins/overview.md)

## 从源码编译

#### 准备

+ Go version >= 1.11

#### 编译

+ 编译二进制：``$ make``

+ 安装文件打包：`` $ make pkg``

+ Docker 镜像：``$ make docker``


如果您要实现交叉编译，请参考[此文档](docs/zh_CN/cross-compile.md)。

## 开源版权

[Apache 2.0](LICENSE)

