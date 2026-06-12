---
title: "Internet working, ping lan working but ping to internet doesn't work"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by jhd00023 on 2013-05-11
Hello!
I have ubuntu 12.04 with internet working, DNS are working, I can browse perfectly in Internet, and I have ping in the lan, but when I try to ping a internet IP address or domain the ping doesn't work  the console doesn't print any error until I make a Ctrl + C.

```

---
 ping google.com
PING google.com (173.194.34.232) 56(84) bytes of data.
^C
--- google.com ping statistics ---
158 packets transmitted, 0 received, 100% packet loss, time 158256ms
---

```
Other problem related to this is that I can't  install or update software by apt or the software center.

ubuntu firewall is disabled, and iptables has all the policies in ACCEPT:
```

---
sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
--

```
host.allow and host.deny has no rules...

This is the output of ifconfig:
```

:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:22:15:ef:da:c1  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64903698 (64.9 MB)  TX bytes:13136627 (13.1 MB)
          Interrupt:42 Base address:0xe000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300966 (300.9 KB)  TX bytes:300966 (300.9 KB)

```

Thanks a lot!
                     J:.

---

### Post by matt_symes on 2013-05-11
Hi

Are you behind a proxy server ?

Kind regards

---

### Post by jhd00023 on 2013-05-12
Thanks about your interest Matt,
The network has not a proxy, just a normal DSL router.

regards

---

### Post by prodigy_ on 2013-05-12
Check your router firewall configuration and ensure that ICMP isn't blocked.

---

### Post by matt_symes on 2013-05-12
Hi

Can you also post the output of

```
sudo apt-get update
```

Please post the output between code tags. 

To do this, highlight the text to appear between code tags in your post and hit the # button above where you type the text.

This makes it much easier to read the output.

I'll edit your fisrt post for you so you can see what it looks like.

Kind regards

---

### Post by jhd00023 on 2013-05-12
sorry about dont use the code tag in my first post.
here the output of the "sudo apt-get update":

```
Ign http://es.archive.ubuntu.com precise InReleaseIgn http://es.archive.ubuntu.com precise-updates InRelease
Ign http://es.archive.ubuntu.com precise-backports InRelease
Ign http://security.ubuntu.com precise-security InRelease
Ign http://extras.ubuntu.com precise InRelease
Ign http://archive.canonical.com precise InRelease
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease
Ign http://ppa.launchpad.net precise InRelease
Ign http://ppa.launchpad.net precise InRelease
Ign http://ppa.launchpad.net precise InRelease
Err http://es.archive.ubuntu.com precise Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://extras.ubuntu.com precise Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://archive.canonical.com precise Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://dl.google.com stable Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports Release.gpg
  Unable to connect to 122.252.246.139:8080:
Ign http://es.archive.ubuntu.com precise Release
Ign http://security.ubuntu.com precise-security Release
Ign http://extras.ubuntu.com precise Release
Ign http://archive.canonical.com precise Release
Err http://dl.google.com stable Release.gpg
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to 122.252.246.139:8080:
Ign http://ppa.launchpad.net precise Release
Ign http://es.archive.ubuntu.com precise-updates Release
Ign http://es.archive.ubuntu.com precise-backports Release
Ign http://security.ubuntu.com precise-security/main Sources/DiffIndex
Ign http://extras.ubuntu.com precise/main Sources/DiffIndex
Ign http://archive.canonical.com precise/partner Sources/DiffIndex
Ign http://dl.google.com stable Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://es.archive.ubuntu.com precise/main Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise/restricted Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise/universe Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise/multiverse Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise/main i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise/universe i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise/main TranslationIndex
Ign http://es.archive.ubuntu.com precise/multiverse TranslationIndex
Ign http://security.ubuntu.com precise-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com precise-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com precise-security/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com precise-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/main TranslationIndex
Ign http://security.ubuntu.com precise-security/multiverse TranslationIndex
Ign http://security.ubuntu.com precise-security/restricted TranslationIndex
Ign http://extras.ubuntu.com precise/main i386 Packages/DiffIndex
Ign http://extras.ubuntu.com precise/main TranslationIndex
Ign http://archive.canonical.com precise/partner i386 Packages/DiffIndex
Ign http://archive.canonical.com precise/partner TranslationIndex
Ign http://dl.google.com stable Release
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://es.archive.ubuntu.com precise/restricted TranslationIndex
Ign http://es.archive.ubuntu.com precise/universe TranslationIndex
Ign http://es.archive.ubuntu.com precise-updates/main Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-updates/restricted Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-updates/universe Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-updates/multiverse Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-updates/main i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise-updates/restricted i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise-updates/universe i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise-updates/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/universe TranslationIndex
Ign http://dl.google.com stable/main i386 Packages/DiffIndex
Ign http://dl.google.com stable/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://es.archive.ubuntu.com precise-updates/main TranslationIndex
Ign http://es.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Ign http://es.archive.ubuntu.com precise-updates/restricted TranslationIndex
Ign http://es.archive.ubuntu.com precise-updates/universe TranslationIndex
Ign http://es.archive.ubuntu.com precise-backports/main Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-backports/restricted Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-backports/universe Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-backports/multiverse Sources/DiffIndex
Ign http://es.archive.ubuntu.com precise-backports/main i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise-backports/restricted i386 Packages/DiffIndex
Ign http://dl.google.com stable/main TranslationIndex
Ign http://es.archive.ubuntu.com precise-backports/universe i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise-backports/multiverse i386 Packages/DiffIndex
Ign http://es.archive.ubuntu.com precise-backports/main TranslationIndex
Ign http://es.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Ign http://es.archive.ubuntu.com precise-backports/restricted TranslationIndex
Ign http://es.archive.ubuntu.com precise-backports/universe TranslationIndex
Err http://extras.ubuntu.com precise/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://archive.canonical.com precise/partner Sources
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/restricted Sources
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/universe Sources
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/multiverse Sources
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://extras.ubuntu.com precise/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://extras.ubuntu.com precise/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://extras.ubuntu.com precise/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://archive.canonical.com precise/partner i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://archive.canonical.com precise/partner Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://archive.canonical.com precise/partner Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://dl.google.com stable/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://dl.google.com stable/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://dl.google.com stable/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://ppa.launchpad.net precise/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/restricted i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/universe i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/multiverse i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/multiverse Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/multiverse Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/restricted Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/restricted Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/universe Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://dl.google.com stable/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://dl.google.com stable/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://dl.google.com stable/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://security.ubuntu.com precise-security/universe Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/restricted Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/universe Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/multiverse Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/restricted i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/universe i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/multiverse i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/multiverse Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/multiverse Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/restricted Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/restricted Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/universe Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise/universe Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/restricted Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/universe Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/multiverse Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/restricted i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/universe i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/multiverse i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/multiverse Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/multiverse Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/restricted Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/restricted Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/universe Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-updates/universe Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/main Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/restricted Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/universe Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/multiverse Sources
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/main i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/restricted i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/universe i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/multiverse i386 Packages
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/main Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/main Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/multiverse Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/multiverse Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/restricted Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/restricted Translation-es
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/universe Translation-en
  Unable to connect to 122.252.246.139:8080:
Err http://es.archive.ubuntu.com precise-backports/universe Translation-es
  Unable to connect to 122.252.246.139:8080:



```

---

### Post by matt_symes on 2013-05-12
Hi

DNS resolution looks to be working.

Check your router as suggested.

Also from the terminal, post the output of this command

```
tracepath 122.252.246.139/8080
```

Let's see where,  udp packet at least, it may be failing.

Kind regards

---

### Post by jhd00023 on 2013-05-18
Thank you all!
Finally I took another machine to ping outside from the lan and it has the same trouble. When I was trying to configure the DSL router, I couldn't found the problem and finally I make a hardreset to the router. This was the solution.

---

