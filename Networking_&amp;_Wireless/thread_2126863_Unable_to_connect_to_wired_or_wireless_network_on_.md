---
title: "Unable to connect to wired or wireless network on Ubuntu server 12.04.2 LTS"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by BHD25 on 2013-03-18
I have been trying to set up an Ubuntu 12.04.2 LTS Server and have been unable to connect to the internet with either a wired or wireless connection. My college requires a username and password when connecting to the internet and I'm not sure how to enter those in on a terminal interface. I have tried to use wpa_supplicant but I am having a hard time understanding how to use it. When I check the network details on my Ubuntu 12.10 Desktop version I get:

[ipv6]
method=auto


[connection]
id=MU-WIRELESS
uuid=85b9a95e-0f47-45d2-af03-0386bf519def
type=802-11-wireless


[802-11-wireless]
ssid=MU-WIRELESS
mode=infrastructure
mac-address=94:39:E5:4C:F1:5B
security=802-11-wireless-security


[802-1x]
eap=ttls;
identity=<username>
phase2-auth=mschapv2
password=<password>


[ipv4]
method=auto


[802-11-wireless-security]
key-mgmt=wpa-eap
auth-alg=open

How would I set up the wpa_supplicant.conf file and what other commands would I need to run to connect to the network? I believe the school uses WPA2. I have also tried to connect via wired connection when wireless wasn't working so I did a clean install and used eth0 as the primary network device. It looked like it was able to successfully connect and when I did ifconfig after the OS was completely installed the eth0 information was all filled in as though it was connected. When I tried to do sudo apt-get update though I get this error:

E: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: NODATA 1 NODATA 2

Even when connecting to a wired connection we need to use our username and password to gain full access to the internet. How would I go about entering in that information so that I can connect to the internet? Any help with either wireless, wired, or both connections would be greatly appreciated!

-John

---

