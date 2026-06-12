---
title: "Unable to ping Windows 7 box by hostname"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by arnabbiswas on 2011-02-10
Hello, I have a windows 7 desktop hardwired to my wireless router and a windows xp laptop connecting wirelessly on the same network. I am able to ping the windows 7 box by its ip address but unable to do so by its hostname. This is very inconvenient since I would like to set up a share by hostname (doesnt change) and not by ip (changes occasionally since its dhcp).

Can someone please help?

---

### Post by Dark_Stang on 2011-02-10
You don't need to ping it by hostname in order to see shares on it by hostname. Just setup the share on the Windows 7 Box. Then on Ubuntu click Places > Network. You should be able to navigate to your share from there.

---

### Post by arnabbiswas on 2011-02-10
I tried that but it did not work - 1. I shared all my drives on the windows 7 box. 2. I navigated to Places > Network > Windows Network. There were two icons - HOME and WORKGROUP. On clicking both I get a 'Unable to mount location, Failed to retrieve share list from server' error.

---

### Post by Dark_Stang on 2011-02-10
Two things here...

> **arnabbiswas said:**
> 1. I shared all my drives on the windows 7 box.
Woah, that is a really bad idea.
> **arnabbiswas said:**
> 2. I navigated to Places > Network > Windows Network. There were two icons - HOME and WORKGROUP. On clicking both I get a 'Unable to mount location, Failed to retrieve share list from server' error.
So here's what sucks about Windows. A firewall could be messing with you, including the built in firewall. Or, some file sharing encryption could be messing with you. If you open up your advanced file sharing options, you can check your encryption and password settings there. Home Group sharing could also be screwing with you. A guest account might not be enabled (also, there is a difference between network guest access and physical guest access...) ... Yay Microsoft!

---

### Post by arnabbiswas on 2011-02-11
Ok - I will try to connect again from another windows xp laptop to this windows 7 desktop and report back. If I get the same behavior then I would know that it is the settings on the win 7 box, as per your feedback. If I can connect fine from win xp to win 7 then I would know its something between ubuntu 10.10 to win 7 that is screwing me. Will find out and circle back.

---

### Post by Dark_Stang on 2011-02-11
> **arnabbiswas said:**
> Ok - I will try to connect again from another windows xp laptop to this windows 7 desktop and report back. If I get the same behavior then I would know that it is the settings on the win 7 box, as per your feedback. If I can connect fine from win xp to win 7 then I would know its something between ubuntu 10.10 to win 7 that is screwing me. Will find out and circle back.
Shouldn't be anything between Ubuntu and 7. At home I run two Linux boxes and my Fiancé runs a Windows 7 box. They share files flawlessly. 

At my work we have a few Linux boxes, loads of Windows Servers, and all of our desktop boxes run Windows 7. Again, all of them share files flawlessly.

---

### Post by arnabbiswas on 2011-02-11
> **Dark_Stang said:**
> Two things here...

So here's what sucks about Windows. A firewall could be messing with you, including the built in firewall. Or, some file sharing encryption could be messing with you. If you open up your advanced file sharing options, you can check your encryption and password settings there. Home Group sharing could also be screwing with you. A guest account might not be enabled (also, there is a difference between network guest access and physical guest access...) ... Yay Microsoft!

Ok, so any suggestions on how I could go about debugging all these possibilities? I dont have any other firewall installed besides the windows default one. Under my Advanced sharing settings I have enabled sharing for devices using 40 or 56 bit encryption and I have turned off password protected sharing. Also I am allowing Windows to manage homegroup connections. What else can I check?

---

### Post by Dark_Stang on 2011-02-12
Settings on my Fiancé's machine...
Network Discovery - On
File and Printer Sharing - On (duh)
Public Folder Sharing - Set for Read/Write for me as I use them as dropboxes.
Media Streaming - On for some reason. O.o
File Sharing - Set for 40-56 bit encryption
Password Protected Sharing - Off
HomeGroup Connections - Use user accounts and passwords to connect to other computers. (off)

Also, her windows firewall is off as she runs Kaspersky Internet Security on the box.

---

### Post by dmizer on 2011-02-12
Please see the 6th link in my sig.

---

