---
title: "DSL Connectivity Problem at Boot Ubuntu 9.10 Karmic Kola"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by fslurrehman on 2010-04-26
Hi to all!
Last week I downloaded and installed Ubuntu Karmic Kola and wanted to experience it before trying Ubuntu 10.04 LTS. But I got a internet connectivity problem.

I am using wired network with ADSL. I have 2 computers on my home network connected to ADSL router through switch.
 [B]
Problem:[/B]
When I boot Ubuntu 9.10 Karmic Kola, the network is disconnected during the boot process. I can see this from the light of my network ethernet card and also light is off from  from my network switch.

**Partial Solution:**
I found a solution to that by unplugging the network cable of my second connected computer and then replugging it. By this, the network is established on  my PC running Ubuntu OS. But the net speed is so much slow. 

If I boot XP on same system, then the internet is connected and works fine with its full speed. This suggests that there is a network problem with Ubuntu Karmic Kola.

**Solution Needed:** 
But I want the Karmic Kola to automatically connect and switch on the ethernet card as WIn XP does it


Till now I never posted on this forum as all my answers were available before. 
I googled my problem but could not found any solution.
 
I ask all You Guys to help me please to correct this bug. So that I can connect to internet without un plugging the net cable and can browse with full speed in Ubuntu. I am waiting for a reply. 

Thanks

---

### Post by fslurrehman on 2010-06-12
I got the same problem in Lucid Lynx that when I boot the lucid lynx, the ethernet card gets disconnected. I need its solution.

This only happens when I have another PC (with win xp) already running (and both lynx lucid PC and XP PC connected through switch).

---

### Post by fslurrehman on 2010-06-12
I found the solution later after surfing through ubuntu forum archive. The solution which worked for me in both karmic kola and lucid lynx is that I just reinstalled the network-manager from synaptic package manager. 
But I did that after the OS was fully updated.

I think there is a bug in network program of lynx lucid and karmic kola and that this require re-installation of network-manager. I don't know why these guys shipping the new version with this bug. Correct me if I am wrong. 

Believe me this makes really bad impression when some one tries ubuntu for first time and even he/she may quit it forever.

---

