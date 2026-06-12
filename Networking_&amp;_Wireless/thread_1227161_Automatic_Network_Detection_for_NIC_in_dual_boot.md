---
title: "Automatic Network Detection for NIC in dual boot"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by d0ming on 2009-07-30
I'm still new with Ubuntu. I recently moved to a new apartment where they provide free internet access thru ethernet. Initially I have WinXP installed and whenever i tried to connect, it goes to "limited or no connectivity". I didn't bother to have that fixed, not until I installed Ubuntu 8.10 to dual boot along with XP. Now after installing ubuntu, guess what? My free internet actually works and is automatically detected... but only in Ubuntu!. Now I love Ubuntu, though I can't get rid of windows because I use Adobe Premiere quite a lot, and I need to download stuff while i'm editing. So what I did, was to get the IP address, subnet mask etc. of my working internet connection in ubuntu, restarted and booted into XP then did a manual configuration of the IP address and etc and successfully got connected in windows. Now i thought my problem was over, but just recently, my windows connection doesn't seem to work, there are packets sent but none received, yet still shows connected. When I try connecting in ubuntu, it still works like a charm!, i checked to see if there was any changes to the IP or subnet mask in the automatic configuration of ubuntu so that I can update the manual settings in Xp, but the it is still the same! I still can't get the internet to work in XP!

My question is, hopefully that I'm asking this in the right place... is why am I able to connect automatically in Ubuntu but not in Windows? what specifically does Linux has, that Xp hasn't that is causing this specific problem?
I am a veteran computer user and I know hot to troubleshoot windows environments, so I tried every software troubleshooting like  reinstalling drivers or updating the BIOS. but I still can't get it to work. Since I just started with ubuntu, i need help on getting any info about this, so can find at least a temporary remedy to the crazy xp problem. So if i know what makes it work in ubuntu, I can try to make it work as well in xp, thanks!

---

### Post by superprash2003 on 2009-07-30
well do you have multiple network cards in your machine? do you run vmware in windows? set windows xp network settings to automatically receive ip and then in the command prompt type **ipconfig /renew** and then post output of **ipconfig**

---

