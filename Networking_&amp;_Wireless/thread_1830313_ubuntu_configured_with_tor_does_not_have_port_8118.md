---
title: "ubuntu configured with tor does not have port 8118 open?"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2011-08-21
I installed TOR by following the documentation on their website, as follows:
I added this to my /etc/apt/sources.list file ```
deb http://deb.torproject.org/torproject.org natty main
```I added the gpg key using these steps: ```

gpg --keyserver  keys.gnupg.net --recv 886DDD89
gpg --export  A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```Then I installed TOR: ```

apt-get update
apt-get install tor tor-geoipdb polipo privoxy socat

```
I configured polipo using the instructions found here: [https://help.ubuntu.com/community/Tor#Configure%20the%20HTTP%20proxy](https://help.ubuntu.com/community/Tor#Configure%20the%20HTTP%20proxy) I copied the configuration file using those commands, started the services, but still, nothing on port 8118. 
And I added this code to /home/<myusername>/.bash_rc file:
```
http_proxy=http://127.0.0.1:8118/
HTTP_PROXY=$http_proxy
export http_proxy HTTP_PROXY
```After a reboot, I audited my ports to see if 8118, the standard TOR port, was open, but unfortunately, it's not. Here are the results of the audit: ```

80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql
9050/tcp open  tor-socks

```I'm trying to configure a python script that uses TOR, and the recommendation is to use port 8118 if 9050 isn't working. However, I can't use the port if it's not open, so is there something I'm doing wrong, or is this normal behaviour?

Thank you!

---

