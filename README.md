# Docker Extension

# Description
The Docker Extension uses the CA APM Restful EPAgent to monitor Docker.

Docker is an open platform to build, ship, and run distributed applications. The Docker extension gathers metrics from [Docker Remote API](https://docs.docker.com/reference/api/docker_remote_api/) via HTTPS.

For installation instructions, see the README.md file.

# Short Description
The Docker Extension uses uses the CA APM Restful EPAgent to monitor Docker.

# APM version
Restful EPAgent 9.7.1 and later

# Dependencies
Python 3 with requests module.

Obtain in one of the following ways:
* `# yum install python-requests`
* `# pip install requests`
* `# easy_install requests`

# Supported Third Party Versions
Tested with Docker version 1.6.1, API version 1.18.

# License
[Apache License, Version 2.0, January 2004](http://www.apache.org/licenses/)

# Prerequisite
An installed and configured EPAgent.

Find the version 9.7 to 10.x documentation on [the CA APM documentation wiki.](https://docops.ca.com)

# Install and Configure the Docker Extension

1. Download the extension from the [CA APM Marketplace.] (http://marketplace.ca.com/shop/ca/?cat=29)
2. Navigate to the downloaded extension and unzip or untar the file as appropriate into the <*EPAgent_Home*> directory.
3. Configure the IntroscopeEPAgent.properties file <*EPAgent_Home*> directory.
4. Copy the docker.typeviewers.xml file from the extension <docker-EPA_REST> directory to the <MOM_HOME>/ext/xmltv directory.

# Use the Docker Extension

1. Run `python3 docker.py` from the command line.
   For example:

   `python3 docker.py -p 8080 -d boot2docker -r 2376 --certificate=$DOCKER_CERT_PATH/cert.pem -k $DOCKER_CERT_PATH/key.pem`

2. Change the parameters to fit your environment.

Run the script with option `-h` to get this usage information:

```
   Usage: docker.py [options]

   Options:
     -h, --help            show this help message and exit
     -v, --verbose         verbose output
     -H HOSTNAME, --hostname=HOSTNAME
                          hostname EPAgent is running on (default: localhost)
     -p PORT, --port=PORT  http port of the EPAgent (introscope.epagent.config.httpServerPort)
     -m METRICPATH, --metric_path=METRICPATH
                          metric path prefix for all metrics
     -d DOCKERHOST, --docker_host=DOCKERHOST
                          docker hostname (default: localhost)
     -r DOCKERPORT, --docker_port=DOCKERPORT
                          docker Remote API port (default: 2376)
     -c CERTFILE, --certificate=CERTFILE
                          https certificate
     -k KEYFILE, --private_key=KEYFILE
                          https private key
```

# Metrics
These metrics about the Docker engine display under the **Docker** node:
* Container Count
* Image Count
* Running Containers
* Total Memory
* MemoryLimit (boolean: 0/1)
* SwapLimit (boolean: 0/1)

These Container metrics for running containers display under the **Docker|Containers|<name>** node:
* Image name
* SizeRw and SizeRootFS: file system sizes
* Status
* CPU metrics (in Ticks)
* Memory metrics
* Network metrics (receive and transmit)

**More information:** [Docker Remote API](https://docs.docker.com/reference/api/docker_remote_api/)

# Custom Tab
The docker.typeviewers.xml matches metric paths starting with **Docker**.

Provide an Overview Tab

1. Copy the docker.typeviewers.xml file from the Docker extension <docker-EPA_REST> directory to the `ext/xmltv` Enterprise Manager directory. 
2. Restart WebView or log off and back on to Workstation. 

An Overview provides general metrics and a list of containers. Container metrics about the file system, CPU, memory, and the network metrics display as graphs.

# Debugging and Troubleshooting
Your can run `docker.py` with option `-v` to provide verbose output. You can also remove the `#` in front of several print statements throughput the script.

# Support
This document and extension are made available from CA Technologies. They are provided as examples at no charge as a courtesy to the CA APM Community at large. This extension might require modification for use in your environment. However, this extension is not supported by CA Technologies, and inclusion in this site should not be construed to be an endorsement or recommendation by CA Technologies. This extension is not covered by the CA Technologies software license agreement and there is no explicit or implied warranty from CA Technologies. The extension can be used and distributed freely amongst the CA APM Community, but not sold. As such, it is unsupported software, provided as is without warranty of any kind, express or implied, including but not limited to warranties of merchantability and fitness for a particular purpose. CA Technologies does not warrant that this resource will meet your requirements or that the operation of the resource will be uninterrupted or error free or that any defects will be corrected. The use of this extension implies that you understand and agree to the terms listed herein.
Although this extension is unsupported, please let us know if you have any problems or questions. You can add comments to the CA CA APM Community site so that the author(s) can attempt to address the issue or question.
Unless explicitly stated otherwise this extension is only supported on the same platforms as the CA APM Java agent. 

# Support URL
https://github.com/CA-APM/ca-apm-fieldpack-docker/issues

# Product Compatibilty Matrix
http://pcm.ca.com/

# Categories
Cloud, Virtualization/Containers

# Change Log
Version | Author | Comment
--------|--------|--------
1.0 | [Guenter Grossberger](mailto:Guenter.Grossberger@ca.com) | First version of the extension.