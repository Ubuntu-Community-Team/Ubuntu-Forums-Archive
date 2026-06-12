---
title: "Lenovo 3000 C100 &amp; Broadcom 4319 Problems"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by tehgooch on 2006-07-09
I just bought my first laptop, a Lenovo 3000 C100, and I have totally removed windows from it; I opted for Ubuntu since I am most familiar with this distro. I thought it was supposed to come with an Intel wireless network adapter, but apparently it has a Broadcom: what a pleasant surprise! I have tried several tutorials:
* [This one](http://ubuntuforums.org/showthread.php?t=185174) didn't do anything. I can still scan for networks, but when I try to connect nothing happens. I found that using "lspci | grep Broadcom\ Corporation" shows it as a "0000:01:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)". I tried it the first time with the .o file recomended by the post, but I then tried it with a .sys file I extracted from drivers I downloaded from the Lenovo website, and they were not recognized by the fwcutter program.
* I tried an ndiswrapper tutorial that I cannot find again. It had the same effect as above.

Any help getting this wireless adapter working would be appreciated, and I thank you all in advance. I tried to include as much info as I could remember, but I probably forgot something. Don't hesitate to ask :)

---

### Post by stevieb on 2006-07-11
I have the same computer (linux only!), same problem.  I've think I've been through every tutorial here so far; none have helped.  I've posted several questions, but have gotten no replies.  Here are my impressions so far:

I read somewhere in the forums that dapper now includes a bcm43xx that's compatible with our wireless card, so I believe ndiswrapper is the wrong solution.

As far a scanning for networks, I don't think that's actually happening in my case: I don't believe that the devices is actually turned on.  When I click on the  NetworkManager icon, I should get a list of available networks in the area (there should be several in my office bldg, both secure and unsecure), but there is nothing, and the windows laptop see them.

fwcutter is not an option for me, because I can't connect to the net in the first place to get it.  But, this seems related to ndiswrapper, and that should be unnecessary here.

I think you did the right thing by posting the lspci info; that seems to be a clue to our problem, although I don't know how.

Here's another thought: when I installed Dapper (and the GUI installer didn't work; had to use the alternate installer), I declined to configure DHCP- I wonder if that has something to do with it?  Also, at the end of the installation, the screen just went black with 2 white squares where it hung overnight; when I checked in the morning the CD Drive was open and when I touched the mousepad the thing rebooted and started up successfully.  Maybe my install isn't clean?

A final thought: this *can* be done; I submit as evidence this [link]("http://www.linuxemporium.co.uk/products/laptops/#pid84849"): these people are selling our laptop with Dapper preloaded.

Let's see if we can work on this together; I'm going to post on to craigslist and offer a case of beer to anyone who can help me!  I'll post what I find out.

Good luck!
-steve

---

### Post by tehgooch on 2006-07-11
I found something new: fwcutter seemed to recognize the adapter as a 4318! I think this may be the problem. Luckily I have easy access to my wired network, but I would like to take this laptop on the go. I will keep trying to get the wireless to work; I wish you luck on craigslist.

---

### Post by stevieb on 2006-07-11
I thought they used the same drivers...  maybe not.
-steve

---

### Post by jml on 2006-07-12
The Broadcom Chipset has a long history of being very Linux unfriendly.  I have a laptop with one and have never been able to get it to work with Linux.I looked at the link that stevie supplied and I agree with the vendor, use a PCMCIA card that is Linux friendly.

Joe

---

### Post by stevieb on 2006-07-12
You won't believe this, but I'm writing in a cafe using wireless right now:) !

I think what did it for me was a re-install of Ubuntu, then I did the procedure outlined in the link you cite in your first post.

With this install, I tried the GUI interface and it worked this time for some reason.

If you want to try again, I'll help you walk through the process, and email you any files you need.

-steve

---

### Post by tehgooch on 2006-07-13
I just tried the guide linked in my first post with a fresh install, but my wireless is still not functioning. I can see networks, but when I try to connect they fail to do anything. What driver file did you use in the guide?

---

### Post by stevieb on 2006-07-13
I went to the link listed (drinus or something) for wl_apsta.o.  do you have access to that?

-steve

---

### Post by tehgooch on 2006-07-14
bcm43xx-fwcutter seems to think that it is not supported, but I will try again later today.

---

### Post by tehgooch on 2006-07-16
Well I have tried a few things, and still no headway. I tried reinstalling ubuntu and trying the fwcutter tutorial again and using a shell script I found in /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh which seems to install the drivers automatically. Anyway, nothing has changed; I can see wireless networks in range, can try to connect to them, and then nothing happens. If you could contact me with a detailed list of what you did, stevieb, maybe I could figure out what is going wrong.

I think I might just buy a cheap wireless USB stick.

---

### Post by LinLenLap on 2006-10-31
Sorry to hear of your troubles. I have the same card and laptop. For me, I did a fresh install of Excellent Edgy, then the first thing I did was connect to a wired network and follow the instructions here:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

Use the preferred driver over all others. Copy the firmware to the kernel directory like it recommends. Unplug and reboot. Do nothing else in the instructions since it should be working now.

Disclaimer: My router is set to G only and it's the only one I connect to. Haven't tried other routers or those set to mixed band.

I writing using WAP as we speak, which i couldn't set up under Dapper at all, but which was good to go right out of the box. Also, I heard the kernel's included in Edgy support he media card readers we have. Haven't ried yet though, so I can't confirm.

Best,

LLL.

---

