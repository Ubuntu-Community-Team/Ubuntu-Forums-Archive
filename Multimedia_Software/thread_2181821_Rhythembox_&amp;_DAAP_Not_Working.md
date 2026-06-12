---
title: "Rhythembox &amp; DAAP Not Working"
date: 2013-10-19
forum: Multimedia Software
---

### Post by adam17 on 2013-10-19
Hi,

I have tries looking all over the internet for an answer to this but can't seem to find anything of any use! I am running Ubuntu 12.04 and Rhythembox 2.96. I have a DAAP share on my Nas4free server version **9.1.0.1 - Sandstorm** (revision 847). However, Rhythembox can see the DAAP share but cannot connect. I keep getting the error messges "Could not connect to shared music" & "Cannot connect to destination (HOST IP ADDRESS)

Does anyone know how to fix this?

Adam

---

### Post by tgalati4 on 2013-10-19
Do you have a firewall running on either your Ubuntu machine or on your router?  You need to make sure the correct ports are open.  Also, there are a few different versions of DAAP and the Rhythmbox plug-in and the Nas4Free version must match, otherwise you will have problems.

Open a terminal and run rhythmbox from there and watch for any additional error messages.

```
rhythmbox --debug
```

I'm running older freenas (0.7.2) with Rhythmbox (2.97) on 12.10 and it works out-of-the-box, so perhaps the Nas4Free is running a newer version of DAAP?

Additionally, I have my freenas server with a static IP address and added to /etc/hosts:

.
.
192.168.1.162 freenas


Then I hit "Connect to DAAP server" and type in "freenas" and it works.

---

