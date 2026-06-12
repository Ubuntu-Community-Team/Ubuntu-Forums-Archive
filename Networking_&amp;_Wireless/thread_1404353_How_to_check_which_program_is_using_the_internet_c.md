---
title: "How to check which program is using the internet connection"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by surja on 2010-02-11
I'm using Ubuntu 9.10. My internet connection is an ADSL which I have set up using "pppoeconf". The connection starts at boot up. I can also start it if needed by using "sudo pon dsl-provider" and can stop it by using "poff dsl-provider".

Recently I noticed that when I start my computer, there is some program (or programs) which is connecting automatically to the internet and downloading and uploading a lot of data. The data transferred can exceed 200 mb or 300 mb in an hour. I don't know what is being uploaded or downloaded. I know for sure that no file sharing programs like bittorrent clients are started at bootup so it is strange that this much data to be downloaded and uploaded without me sharing files or downloading files explicitly. The update software also does not run by default as I have opted to start it manually.

Is there any application which shows the programs that are connected to any particular port and transmitting and receiving data?

In Windows XP I use a program called "What's Running" which clearly lists the programs using the different ports in the local machine and the remote IP addresses that the program is connected to. It also shows which program is transmitting and receiving data at any point in time. Is there any similar program for Linux?

My internet connection is a data limited package otherwise I probably would not have bothered.

---

### Post by Xog on 2010-02-11
Try out one of the various firewalls for linux. I'm pretty sure any one of these will show you what's accessing the internet, as well as give you IPs which you can block.

---

### Post by iponeverything on 2010-02-11
wireshark, tcpdump and lsof might help you out.

---

