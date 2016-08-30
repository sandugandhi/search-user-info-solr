# Search User Information using Apache Solr 4.9.0 Search Engine 
This project contains the Apache Solr 4.9.0 search engine configuration files and architecture design for searching user or customer information from database.

 Reference:  
https://radicalvision.wordpress.com/2016/08/29/apache-solr-4-9-0-search-engine-configuration/

Running Solr in Apache Tomcat

1.  Download and extract Solr 4.9.0 .zip from Apache Solr
    [archive](http://archive.apache.org/dist/lucene/solr/) website in
    SOLR INSTALLATION directory, say C:\\Program Files\\solr-4.9.0.

2.  Download and install latest Java JDK 8 or 7 (Minimum above 1.7
    update 55) from [Oracle Java
    SE](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html) site.
    The install instructions and compatibility remain the same for both
    the versions.

3.  Create JAVA\_HOME environment variable pointing to the Java
    home directory. For example, on my command prompt, the following
    command gives,\
    echo %JAVA\_HOME%\
    C:\\Program Files\\Java\\jdk1.7.0\_67

4.  Download and extract latest Apache [Tomcat
    7](http://tomcat.apache.org/download-70.cgi) (7.0.55) OR [Tomcat
    8](http://tomcat.apache.org/download-80.cgi) (8.0.12) .zip files.
    The install instructions and compatibility remain the same for both
    the versions.

    Create CATALINA\_HOME environment variable with path to
    your apache-tomcat-extracted-folder. For example, on my command
    prompt,\
    echo %CATALINA\_HOME%

    D:\\apache-tomcat-7.0.55

5.  Create a folder anywhere in your drive for solr web application
    base directory. Give this directory path for CATALINA\_BASE
    environment variable.\
    For example, on my command prompt,

    echo %CATALINA\_BASE%

    R:\\Solr

6.  Create a Solr home directory anywhere locally. For example:\
    R:\\Solr\\solrhome\
    This directory will be referred to as SOLR\_HOME. This directory
    will contain all your solr configurations.

7.  Create the following folder structure in your CATALINA\_BASE

    ![](media/image1.png){width="0.7709405074365704in"
    height="1.8544258530183726in"}

8.  Copy CATALINA\_HOME/conf contents in CATALINA\_BASE/conf

9.  Create CATALINA\_BASE/conf/Catalina/localhost directories and add
    following conf file with the contents as shown below:

    &lt;?xml version="1.0" encoding="UTF-8" ?&gt;

    &lt;Context docBase="R:\\Solr\\solr-4.9.0.war" debug="0"
    crossContext="true" &gt;

    &lt;Environment name="solr/home" type="java.lang.String"
    value="R:\\Solr\\new\\solrhome4.9.0" override="true" /&gt;

    &lt;/Context&gt;

    The **docBase** is path to your war file found in your\
    &lt;SOLR INSTALLATION directory&gt;/dist/solr-4.9.0.war\
    The Environment tag “solr/home” is the path to your SOLR\_HOME

10. Copy the logging jars found in &lt;SOLR INSTALLATION
    directory&gt;/example/lib/ext/\*.jar into your CATALINA\_BASE/lib

11. Download ojdbc jar into CATALINA\_BASE/lib\
    Sample jar attached.

    The jars in CATALINA\_BASE/lib should look like this

    ![](media/image4.png){width="1.5833333333333333in"
    height="1.4583333333333333in"}

12. Sample SOLR\_HOME directory for solr 4.9.0 is attached here. You may
    copy the contents of the following extract as your SOLR\_HOME

The configuration changes that need to be done in the above zip extract
in your environment is as follows:

-   Edit &lt;SOLR\_HOME&gt;/solr.xml with your Solr instance server and
    port (default is localhost: 8080)\
    This file also contains the names of your Solr Cores. (default
    &lt;core&gt; is db-core) You will see separate folders in SOLR\_HOME
    for each core. Each core will have its own Solr configuration.

-   Edit &lt;SOLR\_HOME&gt;/&lt;core&gt;/db-data-config.xml with your
    database connection settings

-   Edit &lt;SOLR\_HOME&gt;/&lt;core&gt;/conf/dataimport.properties with
    your Solr instance server IP, port (if changed), Solr Core name (if
    changed), webapp name (if changed).

1.  Copy the following jars found in your &lt;SOLR INSTALLATION
    directory&gt; into &lt;SOLR\_HOME&gt;/lib

    ![](media/image6.png){width="2.531603237095363in"
    height="1.2085017497812773in"}

2.  Start Tomcat server by running
    &lt;CATALINA\_HOME&gt;/bin/startup.bat

3.  Point your browser to

> http://localhost:8080/solr-4.9.0

1.  Select your core in the drop down in the left side:

> ![](media/image7.png){width="3.9583333333333335in"
> height="2.9685312773403325in"}

1.  Import data for indexing by selecting DataImport of the left menu
    and then selecting ENTITIES as given below:

> ![](media/image8.png){width="3.9895833333333335in"
> height="2.9919652230971128in"}

1.  After 15 seconds, query for data by selecting Query in the left menu
    as follows:

> ![](media/image9.png){width="4.0in" height="2.999779090113736in"}

1.  Happy Searching!




