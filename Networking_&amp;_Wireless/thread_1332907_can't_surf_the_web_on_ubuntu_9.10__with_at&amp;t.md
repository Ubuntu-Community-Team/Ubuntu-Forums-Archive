---
title: "can't surf the web on ubuntu 9.10  with at&amp;t"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by albert12m on 2009-11-20
I'm new to lunix and ubuntu and i have a big problem.I switched to ubuntu 9.10 64 bit desktop version 3 days ago from windows 7 and made ubuntu the only OS(which i regret).the first day everything was fine my internet connection was up i could browse the web and everything the the next day i couldn't browse the web but i was connected to Auto Ethernet so i decide it to leave it alone for a few days but after it became a problem so i tried to install windows 7 again with wine windows program loader(which i installed the first day)but it didn't start so i tried typing /media/cdrom0/setup.exe but came up with this"Trying to load PE image for unsupported architecture(AMD-64)"twice then"wine: could not load L"D:\\setup.exe":Bad EXE format for.The same for vista.My desktop info:Dell Inspiron with intel core 2 quad 64 bit capable.My modem/router info:i have at&t dsl elite wire connection with phone line not direct and i have 2wire 2701HG-B modem router.So can some help me now to get connected to the internet back again or how to install windows 7 or vista again or were i can get help or any type of help please please please im so worried and despreat.

---

### Post by imsdunn on 2009-11-23
I am having the same problem with the exception that I am using 32-bit Ubuntu 9.10. I also have At&T DSL modem and was able to connect on the first boot of v9.10 and then tried to setup up Firestarter to act as a firewall for my wireless network. After shutting down that night and rebooting the next day my internet will not work at all. I have even gone in and uninstalled Firestarter and cannot get back on the internet. Any help here would be great. Thanks!

---

### Post by Chamillo on 2009-11-23
I have an Ubuntu 9.10 laptop and it works fine with a wireless connection. Yesterday I installed Ubuntu 9.04 on my desktop that is connected to the 2wire modem with an ethernet cable. Unfortunately, after changing to Ubuntu I cannot connect to the internet anymore. I called AT&T for help and they were useless. Any help in this regard would be great. Otherwise, I might need to start looking for another provider. I'm not going back to MS Windows.

---

### Post by imsdunn on 2009-11-30
Well, I was gone for several days for the holidays and did not work on the issue until tonight but I was able to get connected tonight.

This was found on another link and is what worked for me. There is a lot of work arounds, but this was the simplest.

> 
I usually open /etc/NetworkManager/nm-system-settings.conf as root and edit "managed=flase" to "true" then save and restart, that should do it. I actually went in and used the sudo command without actually logging in as root.
```
sudo nano /etc/NetworkManager/nm-system-settings.conf
```edit the line of code, save the file, then restart the computer.

[[FONT=Times New Roman][SIZE=3]http://ubuntuforums.org/showthread.php?t=1303876&highlight=dsl[/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1303876&highlight=dsl")

---

