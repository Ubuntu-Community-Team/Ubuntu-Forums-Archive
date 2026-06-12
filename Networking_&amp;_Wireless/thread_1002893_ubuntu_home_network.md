---
title: "ubuntu home network"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by fcuk112 on 2008-12-05
sorry for my noob question.

i have a network of 2 PCs, both running ubuntu 8.10.  the problem is that i cannot browse the other PC on the network.  how can i do this?

thanks - fcuk112.

---

### Post by eder.apt-get on 2008-12-05
Are these two PCs connected to a hub/switch?
Are you using static Ip?
Can you ping the other PC?

---

### Post by LowSky on 2008-12-05
I am having the same issue, even when I install samba and set up folder sharing, I think there might be something wrong with one of the latest security updates... it's been driving me crazy for the last 18 hours, only reson I'm saying this is the one computer worked until I did the latest upgrades, so something smells fishy

---

### Post by fcuk112 on 2008-12-05
the PCs are connected to the same router.
no static IP configured.
yes, the 2 PCs can ping eachother.

---

### Post by LowSky on 2008-12-05
You installed Samba? Just to make sure

I'm in the same boat

---

### Post by cb951303 on 2008-12-05
first install Samba via "sudo tasksel" and than install system-config-samba pacakage. go to preferences and setup your sharing dir. I did it 2 days ago with 8.10 between two computers connected through router. I'm pretty sure it will work without problem.

---

### Post by txwooley on 2008-12-05
This ship is getting crowded.  I tried for months to get my Ubuntu laptop to play nice with my Vista desktop.  Yesterday I had a breakthrough and they shared!  I have no idea how I did it.  Then I DL'ed updates for Ubuntu.  Now- no sharing.  They can ping each other, and both have static IP's.  I have Samba and smbfs.  Need help too.

---

### Post by fcuk112 on 2008-12-05
ok, i did sudo tasksel and installed samba.  however i am not sure how to goto preferences to setup my sharing dir.  can someone pls advise?

---

### Post by cb951303 on 2008-12-05
> **fcuk112 said:**
> ok, i did sudo tasksel and installed samba.  however i am not sure how to goto preferences to setup my sharing dir.  can someone pls advise?

sorry it's in administration in menu

---

### Post by Zyferian on 2008-12-05
I'm going to hijack this thread a little bit, but just tell me if I should post a new thread. I can't seem to find anyone that has my problem. 

I installed Samba, and system-samba-config, and when I go in to change the options on my Samba stuff, it gives me a program crash error. It doesn't even make it all the way open. It just does the "Starting Samba" thing on the bottom and then crashes... any ideas? This is a fresh install.

---

### Post by catdriver on 2008-12-05
Can someone point me toward a how to to connect H Heron  to a macbook?

---

### Post by catdriver on 2008-12-05
> **cb951303 said:**
> first install Samba via "sudo tasksel" and than install system-config-samba pacakage. go to preferences and setup your sharing dir. I did it 2 days ago with 8.10 between two computers connected through router. I'm pretty sure it will work without problem.

S0 this is me back from my Macbook, since tasksel decided to eat my Hardy heron install...... I am now really pissed, because the rational for trying this was to install samba so I could migrate some things off the ubuntu machine and clean it up.... Now I may have lost it.  I'm so pleased the tasksel decided to remove my OS for me when All I ASKED FOR WAS A SAMBA INSTALL.  Yes I know back things up, well duh that's what I was trying to do.

I"M SO DONE WITH THIS.

---

### Post by cb951303 on 2008-12-06
> **catdriver said:**
> S0 this is me back from my Macbook, since tasksel decided to eat my Hardy heron install...... I am now really pissed, because the rational for trying this was to install samba so I could migrate some things off the ubuntu machine and clean it up.... Now I may have lost it.  I'm so pleased the tasksel decided to remove my OS for me when All I ASKED FOR WAS A SAMBA INSTALL.  Yes I know back things up, well duh that's what I was trying to do.

I"M SO DONE WITH THIS.

I'm sorry to hear that but I don't think tasksel has such a capability. What exactly happened? Which errors did you get?

---

### Post by cb951303 on 2008-12-06
> **Zyferian said:**
> I'm going to hijack this thread a little bit, but just tell me if I should post a new thread. I can't seem to find anyone that has my problem. 

I installed Samba, and system-samba-config, and when I go in to change the options on my Samba stuff, it gives me a program crash error. It doesn't even make it all the way open. It just does the "Starting Samba" thing on the bottom and then crashes... any ideas? This is a fresh install.

run system-sonfig-samba from console and copy the error message here :popcorn:

---

