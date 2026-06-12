---
title: "Wpa"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by exisn on 2006-06-17
I got some problems with my wireless interfaces and my WPA network. When connecting through NetworkManager the process stalls at "Activation stage: Configuring device" (28%) on 2 intel wireless chipsets. When connecting to an open network the process completes without a hitch. Anyone got an way to fix this problem?

(The syslog says something about "eth1: link timed out")

---

### Post by nagilum on 2006-06-18
I just tried the network manager, didn't know it before. I couldn't connect to my AP (WPA2) at first, too. Turned out that it does an AP scan before it actually tries to connect. Since I had my SSID set to invisible it couldn't find it and got a timeout. Maybe it's the same problem you have.

---

### Post by exisn on 2006-06-18
I don't know why this works, but apparently it works under Ubuntu if I remove all interfaces in /etc/network/interfaes except lo and create a file, /etc/default/wpasupplicant, with the sole entry "ENABLED=0". This doesn't work under Kubuntu however, guess I'll just have to settle with GNOME for the moment.

---

### Post by wieman01 on 2006-06-24
Hello, 

This does work under KUbuntu as well. It's just that you need to use the KNetworkManager which is the NetworkManager GUI for KDE. Nice little applet and very useful in connection with KWallet for storing passwords.

The connection time-out you get has either to do with your "interfaces" file (as indicated above) which needs to be empty OR wrong credentials / network settings on the client.

---

### Post by exisn on 2006-06-25
Actually I did use KNetworkManager under KDE though I forgot to mention it. The funny thing is even though I follow the exact same steps under Ubuntu and Kubuntu, the wireless access only works under Ubuntu with network-manager-gnomeG I guess the next step would be to try with the Gnome applet under KDE (If that's possible), but I'll wait for Edgy before I try again.

---

### Post by nab on 2006-07-06
I have a simular problem with wpa. 

As long as the SSID is visible everthing works without any problem, but with invisible SSID I get an timeout.

It's no big deal, but I would like to be able to connect to an invisible SSID :rolleyes: 

Any suggestions?

Thanks,
Niko

---

### Post by wieman01 on 2006-07-06
> **nab said:**
> 
Any suggestions?

I compiled a howto a while ago that explains how you can set up WPA2 with static IP (incl. hidden ESSID) using the "/etc/network/interfaces" file. This is not as convenient as using NetworkManager, but it works well.

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

