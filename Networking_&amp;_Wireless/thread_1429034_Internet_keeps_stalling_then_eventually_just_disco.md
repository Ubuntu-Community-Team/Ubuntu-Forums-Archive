---
title: "Internet keeps stalling then eventually just disconnects"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by stakodiak on 2010-03-13
I just installed Ubuntu this morning and don't have much time to detail my problem before my internet goes out again. I am currently running Ubuntu 9.10 (Karmic Koala?). I just got this laptop earlier this week with windows 7 and decided to put ubuntu on it via Wubi. Anyhoo, I login and then enter my wifi password and eveythings fine. I can surf the internet for a bit and everythings fine. but after a while, the wireless indicator on the keyboard begins to flicker on and off (between a connection and no connection) then starts to stall. The first thing I did was install google chrome (always the first thing to do) and I accidentally downloaded the wrong version A-OK. After I saw I downloaded the wrong version, I downloaded the correct, 32-bit version and installed it. During the download it said I had a 750kBs speed, but took much longer to download than had it been downloaded at a consistent 750kBs speed. I then tried to use update synaptic and it began to download reload all 44 packages and stalled around 38 or so. My internet then disconnected (wouldn't reconnect) and the download failed. I went back into windows uninstalled Ubuntu and then reinstalled it. After going through the first few steps again I began to update via update manager and surfed the web. After a few minutes of surfing the indicator began to flicker than just went off. I then connected to my neighbors internet, continued surfing and then the internet just crashed. I've found that when its just lightweight surfing, everythings okay, but during a download or any 2.0 surfing, then things start to get funky. I'm sorry this was so long, I just really don't know how to describe it. If any diagnostics are needed, i'm going to load up ubuntuforums on another pc and just communicate their. How can I fix this? I need a solid, consistent connection. Please help and thank you.

---

### Post by OldMerovingian on 2010-03-13
> **stakodiak said:**
> I just installed Ubuntu this morning and don't have much time to detail my problem before my internet goes out again. I am currently running Ubuntu 9.10 (Karmic Koala?). I just got this laptop earlier this week with windows 7 and decided to put ubuntu on it via Wubi. Anyhoo, I login and then enter my wifi password and eveythings fine. I can surf the internet for a bit and everythings fine. but after a while, the wireless indicator on the keyboard begins to flicker on and off (between a connection and no connection) then starts to stall. The first thing I did was install google chrome (always the first thing to do) and I accidentally downloaded the wrong version A-OK. After I saw I downloaded the wrong version, I downloaded the correct, 32-bit version and installed it. During the download it said I had a 750kBs speed, but took much longer to download than had it been downloaded at a consistent 750kBs speed. I then tried to use update synaptic and it began to download reload all 44 packages and stalled around 38 or so. My internet then disconnected (wouldn't reconnect) and the download failed. I went back into windows uninstalled Ubuntu and then reinstalled it. After going through the first few steps again I began to update via update manager and surfed the web. After a few minutes of surfing the indicator began to flicker than just went off. I then connected to my neighbors internet, continued surfing and then the internet just crashed. I've found that when its just lightweight surfing, everythings okay, but during a download or any 2.0 surfing, then things start to get funky. I'm sorry this was so long, I just really don't know how to describe it. If any diagnostics are needed, i'm going to load up ubuntuforums on another pc and just communicate their. How can I fix this? I need a solid, consistent connection. Please help and thank you.

It could be the network-manager that comes with Ubuntu.  I personally never cared for it because I would get disconnected every two or three minutes.  I have since installed Wicd and I rarely have any problems.  I would try that, as I doubt it is a hardware issue since you can and are able to connect.  You can search for it in Synaptic or go to a terminal and type 

```
sudo apt-get install wicd
```

---

### Post by jklopez on 2010-03-13
i have the same problem so i tryed sudo apt-get install wicd and it installed fine but how do i turn the wireless adapter back on,whats the command??

---

### Post by jklopez on 2010-03-13
> **jklopez said:**
> i have the same problem so i tryed sudo apt-get install wicd and it installed fine but how do i turn the wireless adapter back on,whats the command??
now it's even worse,the adapter still isnt on and before i had signals but when i connect i still could'nt surf now i don't even get a signal...can someone please respond,i'm getting very discuraged with ubuntu 9.10 and no one answered my post at any site exept 2 post here at the ubuntu forums ,windows never gave me problems but i stoped using windows because i don't like what they stand for but it looks like i have nothing left but to go back,any last shot ideas before i go...

---

### Post by chkneater on 2011-02-28
open up a terminal under applications-accessories near the bottom, once you open it up type "sudo nm-applet" with out the quotes.  You can copy/paste that.  It should ask for password and bring back the network manager.  Wicd should not have removed network manager so I'm sure you're ok.

---

