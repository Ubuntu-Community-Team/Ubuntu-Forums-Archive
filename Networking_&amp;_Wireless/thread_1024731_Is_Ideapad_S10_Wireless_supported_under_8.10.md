---
title: "Is Ideapad S10 Wireless supported under 8.10?"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by callmebruce on 2008-12-29
I was reading through some of the forum looking for information on the Lenovo Ideapad S10 with Broadcom wireless adapter. My youngest son's Thinkpad R61 is on the way out (12 year old boys and laptops don't mix well - I need to replace the laptop sreen), and I'm thinking of replacing it with a low end netbook. 

I installed Kubuntu 8.09 on a Thinkpad T41, and upgraded to 8.10. I'm really liking it. So - my thought is to pick up a little S10 for my kid, scrape Windows off it (his laptop is dreadfully slow, antivirus no longer runs, I'm sure it has it's share of virii and junk on it), and go Kubuntu.

So - Kubuntu on new Ideapad S10 if wireless is supported natively under Kubuntu 8.10. Scrape Windows XP off his R61 and install Kubuntu IF I decide to repair it yet again.

Any scoop on wireless specifically for the S10? I have it working just fine on a T41 - but don't like the idea of installing 3rd party drivers or making drivers. That tends to make upgrades a hassle, at least for me.

Anyone running Kubuntu on an S10? Like it? Like the laptop, or is the screen too small?

---

### Post by callmebruce on 2009-01-09
Replying to myself. The Ideapad does not have an optical drive. I had a USB-Attached CD-RW sitting around, so used that. There were no issues in booting off the external CD, and wireless worked out of the box.

I decided to scrape Windows XP off the Ideapad. I was not happy having to pay for Windows XP that is losing support soon - but I was happy getting rid of it.

Installation was trivial. Sound works out of the box. Wireless worked fine (I am not using WPA Authentication at home - I use a firewall with MAC address filtering, assigning IPs by MAC, IP address filtering, and blocking all the - ahem - good stuff). So - I did not test WEP or WPA. Probably will, but my Linksys WAP seemed to drop connections whenever re-negotiating keys.

Back to the install: I set up the Medibuntu repositories, but still could not get audio to play when watching YouTube. I went here and followed instructions: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I received no errors, but still no sound. I decided to click on my Speaker icon - it was not muted, levels looked good. Then I clicked on Mixer and saw that PCM was muted. I opened that up and am able to hear streaming audio.

Coolness!

The screen is small. The keyboard is small. But it is pretty cool for general usage. I had wanted to use the Ideapad Netbook for my Elementary grade son's online school. It works just fine (well, I haven't tried the microphone yet - or the camera) - but I'll put on a USB attached keyboard, mouse and external monitor for school work.

So - no major issues with the Ideapad. I need to test a few more things. But it really is a small, limited usage netbook. (hmmmm, I have a spare desktop sitting around. Maybe I'll set that up for his schol work, and snag the Ideapad for myself)

---

### Post by drinkmocha on 2009-01-12
hi there, i just installed ubuntu 8.1 on my ideapad/S10. my wireless is still not working (it worked when i was on the liveUSB, but not after I installed the OS). could you please let me know how you were able to make your wireless work?

---

### Post by sergueik on 2009-01-18
Hi there...
8.10 comes with good enough proprietary driver "Broadcom STA wireless driver", which needs to be activated by System->Administration->Hardware Drivers tool.

The default Network Manager program does not support secured Wifi, not at leasxt with Broadcom adapter. You need to uninstall it, from terminal with something like

> sudo apt-get purge network-manager-gnome

Then you need to install Wicd network manager

> sudo apt-get install wicd

Once rebooted, it will show up in the launch-bar and you should be able to connect to secured wi-fi. If it does not have option for WPA encryption support, install wpasupplicant (search this forum for how)

On a completely different note (has nothing to do with networking), you might want to update Sound Card driver as well in order for it to function properly. Perhaps there are easier ways of doing that, but I have downloaded latest driver for linux from realtek.com and followed the instruction. I got some crashes in the proceess but the new driver is up and working great.

---

