---
title: "Anyone know how to reboot the pptpd.conf settings?"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by optima4 on 2012-02-19
I was trying to follow this tut to set up a proxy. The tut had me go into sudo and edit pptpd.conf with Nano. Along the way the tut was not clear and I had already saved the new settings. I closed off my computer and the next day I had no Internet connection.

Heres what has happen so far.

```
sudo su
``````
apt-get install pptpd -y
``````
ifconfig
``````
nano /etc/pptpd.conf
``````
#localip 192.168.0.1     
#remoteip 192.168.0.234-238,192.168.0.245 
    # or     
#localip 192.168.101.1 
    #remoteip 192.168.101.200-245
```Change the previous box (uncomment)to this

```
#localip 192.168.0.1     
#remoteip 192.168.0.234-238,192.168.0.245     
# or 
    localip 192.168.1.70     
remoteip 192.168.1.72,192.168.1.74,192.168.1.76,192.168.1.78
```______________________________________________________________________

```
nano /etc/ppp/chap-secrets
```This box is blank and says to add this

```
# Secrets for authentication using CHAP 
    # client           server               secret    IP addresses
```At this point I realized the tut was a little too brief and decided its best to stop. Now I have no Internet.

On another forum they told me to kill the pptpd.conf process by running 

```
ps -eaf | grep pptpd
```My results were

```
root      1898     1  0 09:48 ?        00:00:00 /usr/sbin/pptpd 
kbj       3024  2997  0 10:03 pts/1    00:00:00 grep --color=auto pptpd
```I ran

```
kill -9 1898
```And nothing changed.

____________________________________________________________________

Someone else said 

> reset network configuration by */etc/init.d/networking restart*But idk which command they are saying to use in the absolute path.

---

