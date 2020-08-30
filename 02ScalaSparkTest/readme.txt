Spark Overview
Apache Spark is a fast and general-purpose cluster computing system. It provides high-level APIs in Java, Scala, Python and R, and an optimized engine that supports general execution graphs. It also supports a rich set of higher-level tools including Spark SQL for SQL and structured data processing, MLlib for machine learning, GraphX for graph processing, and Spark Streaming.

Security
Security in Spark is OFF by default. This could mean you are vulnerable to attack by default. Please see Spark Security before downloading and running Spark.

Downloading
Get Spark from the downloads page of the project website. This documentation is for Spark version 2.4.6. Spark uses Hadoop’s client libraries for HDFS and YARN. Downloads are pre-packaged for a handful of popular Hadoop versions. Users can also download a “Hadoop free” binary and run Spark with any Hadoop version by augmenting Spark’s classpath. Scala and Java users can include Spark in their projects using its Maven coordinates and in the future Python users can also install Spark from PyPI.

If you’d like to build Spark from source, visit Building Spark.

Spark runs on both Windows and UNIX-like systems (e.g. Linux, Mac OS). It’s easy to run locally on one machine — all you need is to have java installed on your system PATH, or the JAVA_HOME environment variable pointing to a Java installation.

Spark runs on Java 8, Python 2.7+/3.4+ and R 3.1+. For the Scala API, Spark 2.4.6 uses Scala 2.12. You will need to use a compatible Scala version (2.12.x).

Note that support for Java 7, Python 2.6 and old Hadoop versions before 2.6.5 were removed as of Spark 2.2.0. Support for Scala 2.10 was removed as of 2.3.0. Support for Scala 2.11 is deprecated as of Spark 2.4.1 and will be removed in Spark 3.0.

For Java 8u251+, HTTP2_DISABLE=true and spark.kubernetes.driverEnv.HTTP2_DISABLE=true are required additionally for fabric8 kubernetes-client library to talk to Kubernetes clusters. This prevents KubernetesClientException when kubernetes-client library uses okhttp library internally.

Running the Examples and Shell
Spark comes with several sample programs. Scala, Java, Python and R examples are in the examples/src/main directory. To run one of the Java or Scala sample programs, use bin/run-example <class> [params] in the top-level Spark directory. (Behind the scenes, this invokes the more general spark-submit script for launching applications). For example,

./bin/run-example SparkPi 10
You can also run Spark interactively through a modified version of the Scala shell. This is a great way to learn the framework.

./bin/spark-shell --master local[2]
The --master option specifies the master URL for a distributed cluster, or local to run locally with one thread, or local[N] to run locally with N threads. You should start by using local for testing. For a full list of options, run Spark shell with the --help option.

Spark also provides a Python API. To run Spark interactively in a Python interpreter, use bin/pyspark:

./bin/pyspark --master local[2]
Example applications are also provided in Python. For example,

./bin/spark-submit examples/src/main/python/pi.py 10
Spark also provides an experimental R API since 1.4 (only DataFrames APIs included). To run Spark interactively in a R interpreter, use bin/sparkR:

./bin/sparkR --master local[2]
Example applications are also provided in R. For example,

./bin/spark-submit examples/src/main/r/dataframe.R