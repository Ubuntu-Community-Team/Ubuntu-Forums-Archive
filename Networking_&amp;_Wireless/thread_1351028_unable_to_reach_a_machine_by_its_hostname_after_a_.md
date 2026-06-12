---
title: "unable to reach a machine by its hostname after a while"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by paranoid_humanoid on 2009-12-09
Hi, I have a desktop and a laptop computers, both running Ubuntu and connected to the same LAN.
I am able to connect to my machines by their hostnames followed by ".local" just fine, but after a while of online activity I lose that ability and pinging my machine by its hostname times out. I can reach it by its IP though, so it's only a hostname problem. This problem is only fixed by reconnecting to the network (usually through the NetworkManager applet).
My two machines are connected through an ADSL router without any special fancy configuration. My router is LINKSYS WAG200G if that matters.

---

### Post by paranoid_humanoid on 2009-12-10
<Bump. The forums died for a whole day after I posted this.>

---

### Post by ant2ne on 2009-12-10
what are you using for DNS?

I know that, in a Windows work group setting, the computers will occasionally broadcast who is who so every computer has an IP to name after awhile.

I don't think linux does the same.

you could set up static IPs in /etc/network/interfaces and then put static entries in your /etc/hosts file.

---

### Post by Mski35 on 2009-12-11
> **ant2ne said:**
> what are you using for DNS?

I know that, in a Windows work group setting, the computers will occasionally broadcast who is who so every computer has an IP to name after awhile.

I don't think linux does the same.

you could set up static IPs in /etc/network/interfaces and then put static entries in your /etc/hosts file.

ant2ne brings up a good point about your DNS settings.  Also when you can no longer access the ubuntu machine by host name is the name still resolving on the local host?  You can type hostname at the terminal to verify.  Also do you currently have a static entry in your /etc/hosts file?

---

### Post by paranoid_humanoid on 2009-12-11
I'm using my ISP's DNS server and DHCP I guess, that lies in my network router right? I did not configure anything special.
The problem is definitely name resolving, as I can reach these machines by their IPs but using their hostnames does not work.

---

### Post by Iowan on 2009-12-11
Seems odd that it'd work for awhile...
See if [this]("http://ubuntuforums.org/showpost.php?p=8380385&postcount=2") one helps.

---

