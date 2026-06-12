---
title: "Need help with HVR-1600, HVR-1800 or PVR-500"
date: 2012-07-24
forum: Mythbuntu
---

### Post by glenn3451 on 2012-07-24
ok, so first off i am extremely new to linux in general. now onto the problems. i have a media center computer that i (mostly my gf) use to record tv (main purpose). i was using windows 7 media center to do so but as of lately the guide went out and so we've been scheduling recordings based off the time we know the show is gonna play. i really dont like doing this so i thought "hey i know there are other solutions ill try some". well none really panned out (nextpvr, mythbuntu, knoppmyth, re-trying windows media center). turns out the HVR-1800 is apparently difficult to get operating. so i decided to buy few new cards (to make life easier). turns out none of them make anything easier. i really want to stick with mythbuntu if at all possible. i cant install older versions for some reason(installation gives I/O errors). 12.04 will install, but i cant use analog sides to get anything. the pvr-500 was the closest to running but i guess in the newest release of mythtv it doesnt work quite right. I NEED HELP! my girlfriend is about to kill me because she cant watch her shows!

ps i use analog cable (that i think has a few QAM channels, so it would be nice to have working but not really that important)

---

### Post by faginbagin on 2012-07-25
I have two HVR-1600 working well well with mythbuntu 10.10 (linux 2.6.35) and mythtv 0.23-fixes. Although I'm not currently using the analog tuners on these cards, I have used them with 10.10 and 0.23. I'm not using them any more because my cable provider, WOW, now provides all the basic cable channels via clear QAM, so I don't need to use the analog tuners anymore.

I also support another family member's mythtv setup with a PVR-150 (which uses the same ivtv driver as the PVR-500) and an HD-5500. She still needs the PVR-150 to get some content from her cable provider, Comcast. She is running the same 10.10, 0.23 version that I am running.

I think mythtv 0.24-fixes will probably work as well as, and maybe better than 0.23-fixes, but I haven't upgraded. One thing I've learned in the nearly five years I've used mythtv is "if it ain't broke, don't fix it." So I plan on sticking with the environment I have until I'm forced to upgrade, like if/when a mother board dies and needs to be replaced with something that is only supported by a newer kernel.

Based on the reports I've seen on the mythtv mailing lists, my impression is that support for analog tuners has regressed with the 3.x kernels and/or mythtv 0.25 found in ubuntu/mythbuntu 11.10 and 12.04. Maybe it will improve with 12.10.

It looks like mythbuntu 10.10 is still available for download via:
[http://mythbuntu.org/downloads](http://mythbuntu.org/downloads)
Click on "Historical downloads" to see it. What I'm not totally sure of is, if you install it, whether you'll be able to get the latest fixes for either 0.23 or 0.24. But since you don't seem to have a working solution, it might be worth a try. It's also possible that 11.04 will work, since it is based on linux 2.6.38. Plus 11.04 will be supported until this fall. I wouldn't waste time on 11.10, because it's based on linux 3.0.

Just be sure, whatever versions of mythbuntu and mythtv you choose, that you install mythbuntu-repos to get the latest bug fixes for the version of mythtv you plan to use. Then use Update Manager to update, and repeat until there are no more updates. Once that is done, and you've rebooted, only then should you try to configure mythtv.

HTH,
Helen

---

### Post by klc5555 on 2012-07-25
The cx18 driver for the HVR-1600 works fine for analog on all 3.x.x kernels I've tried. And, as I discovered last night when I blew the dust off an ancient PVR-150 ( = 1/2 of a PVR-500) after 4 years and plunked it into a machine in order to do some video capturing off a VCR, the ivtv driver for kernel 3.2.21 (at least) also works perfectly, once I tracked down the old ivtv firmware.

What doesn't necessarily seem to work perfectly is setting up analog on one of these cards in a clean new Mythtv installation on 0.24.0 and above including 0.25.x. mythtv-setup doesn't seem to be always able to find /dev/video0 to set it up though the device node gets properly registered when the driver loads at boot.

This glitch doesn't appear to affect Mythtv 0.23.x and earlier. And it doesn't seem to affect upgrades from 0.23.x and earlier installations to 0.24.x or 0.25.x, where analog continues to work after the upgrade. There was a thread on this earlier: [http://ubuntuforums.org/showthread.php?t=2004450](http://ubuntuforums.org/showthread.php?t=2004450)

I can't speak to the HVR-1800, which I've never used.

---

### Post by anonymousdog on 2012-07-25
> **klc5555 said:**
> the ivtv driver for kernel 3.2.21 (at least) also works perfectly, once I tracked down the old ivtv firmware.
KLC, you are royalty around here, but I'm challenging your assertion that the IVTV drivers work perfectly given our issues noted here: [http://code.mythtv.org/trac/ticket/10732](http://code.mythtv.org/trac/ticket/10732).  Were those issues sorted out by using older ivtv firmware, and, if so, where did you find it and what versions seemed to work best on the Hauppauge MPEG cards?

---

### Post by glenn3451 on 2012-07-25
thanks for the responses, but still doesnt really help because i still cant install older versions of mythbuntu for some reason(i also cant install older versions of ubuntu or any other flavor of linux on this machine for some reason). i tried to install 12.04 and make/install mythtv 0.24 but for some reason i ran into problems (something about not having a config.mak file). so im stuck with mythbuntu 12.04 and mythtv 0.25. i kinda got the digital side of the hvr1600 working (it found channels and it can change channels but the colors are all off?). i happened to find that article about the hvr-1600 analog, but it sounded like what he did was install an older working version of mythbuntu, backup the config files, then install the new mythbuntu and use the old settings. still stuck without a machine to run the older distributions.

---

### Post by klc5555 on 2012-07-25
> **anonymousdog said:**
> KLC, you are royalty around here, but I'm challenging your assertion that the IVTV drivers work perfectly given our issues noted here: [http://code.mythtv.org/trac/ticket/10732](http://code.mythtv.org/trac/ticket/10732).  Were those issues sorted out by using older ivtv firmware, and, if so, where did you find it and what versions seemed to work best on the Hauppauge MPEG cards?

The ivtv firmware version I ended up using was ivtv-firmware-20080701, which I found left over on one of my old drives. Worked fine. Still available, of course, here: [http://dl.ivtvdriver.org/ivtv/firmware/](http://dl.ivtvdriver.org/ivtv/firmware/) Transferred some 6 hours of VCR recordings so far to disk with this PVR-150 and firmware combination on the ivtv driver supplied with plain-vanilla 3.2.21 kernel source, with more recordings to follow.

However, since this is VCR video capture to disk, plain and simple, I haven't been using the PVR-150 card with Mythtv. Rather just tuning the card from a prompt with ivtv-tune and "cat"-ing the card's output directly to a file on disk, while watching the output on mplayer. Not worth all the mythtv claptrap for such a simple job. So while I full well believe the bugtrack report, I suspect that this problem might be purely Mythtv 0.25, not anything with the hardware, kernel driver, firmware or OS in general. 

On the other hand, I do use the four 1600s I own on Mythtv 0.24.2 and 0.24.3. I needed to install the cards in 0.22 or 0.23 first, configure analog, then upgrade to 0.24 to get their /dev/videoX recognized by Mythtv and their analog to function on the later version. But the 1600s have been completely indifferent to whatever kernel, firmware and cx18 driver version I've thrown at them, so long as the cx18 is later than mid-2010 when the digital amplification issue was fixed. The only current issue I'm aware of is the lag time getting the most recent analog tuners in the latest revisions of this card supported by the cx18 driver developers. Better to buy the older 1600 cards used.

But for the OP, color settings oddities (like "smurfing") can be fixed from the front end, while watching a recording, from the on-screen menu ("m"-key). 

I'm more curious about why a still-supported version like Mythbuntu 10.04 (with Mythtv 0.23) can't be installed on your particular machine, whatever it is. 

Also whether your 1600 analog suffers from the Mythtv 0.24-and-above bug. In particular whether the output of ```
dmesg | grep cx18
``` indicates that the card's analog device node /dev/video0 has been created. And if the node has been created, does "add Capture Card" in the backend setup indicate any analog tuner whatever (V4l analog or MPEG) on the /dev/video0 node, or if this node is just invisible to mythtv-setup.

---

### Post by anonymousdog on 2012-07-25
Yes, I do believe the ivtv bug I noted is **only** MythTV. Tuning actually seems quicker (than with previous distros I've used) and all the v4l-utils and ivtv-utils work like a charm.

---

### Post by faginbagin on 2012-07-26
So I stand corrected, it sounds like you should be able to use 12.04, IF you can somehow do an initial set up with mythtv 0.23, which, if you want to do it the "buntu" way means you first need to install an older distro. I don't recommend 10.04 because of the digital amplification issue that klc mentioned. That problem is fixed in 10.10. And since you want to first use mythtv 0.23 to get the analog side working, I don't think 0.23 is a choice in 11.04 or later. So I think what you need to do is to find a way to install 10.10. Here are some tips that might help.

When you try to boot a 10.10 CD, do you at least get a boot menu? E.g. the one letting you choose whether to install the distro or to run it or to execute memtest? If so, then I suggest the following:

[LIST]
[*]Choose the option to "try before installing", not the install option, but don't hit Enter just yet. You don't need to go straight into installing from the boot menu. The installer will be available if you can just get to the "try before installing" desktop.

[*]Press F6 followed by ESC. This causes the command line for the "try before installing" option to appear.

[*]Erase the words "quiet splash" from the command line, and replace them with the word "nomodeset". This will give you a chance to see what's going on during the boot process and, if there's a problem, some clue as to what the problem is. The nomodeset option can help work around issues with certain video hardware.
[/LIST]

It's been a while since I booted a 10.10 live CD, so I hope these instructions are good enough to get you to a point where you can install. If not, post back here with error messages you see and more info about your hardware, especially processor, chipset and GPU. Maybe it's just too new to run 10.10.

One more thing, I remember seeing complaints about bad sectors when I booted the mythbuntu 64 bit 10.10 CD. But these were nonfatal and I suspect are caused by some problem with the way the ISO was mastered. The errors just slow down the process of booting. For that reason, I have found booting from a USB stick to be much faster, especially if I didn't reserve space on the stick to save configuration information.

HTH,
Helen

---

### Post by klc5555 on 2012-07-26
I agree with faginbagin's approach. 

Except that 10.04 does not need to be ruled out because of the digital amplification issue in the HVR-1600 --there is no need to set up the digital side of the HVR-1600 in Mythbuntu 10.04/Mythtv 0.23 at all: only the analog side needs to be set up prior to the upgrade. The digital half of the 1600 can wait until after the upgrade to be set up and scanned. 

The OP should check the model number of his HVR-1600 to see whether it is one of the latest ones, 74301 and 74321, for which new tuners the analog support may still have issues. All the older models work fine.

---

### Post by glenn3451 on 2012-07-27
the hvr-1600 is a model 1101. the computer is built on this mobo [http://www.asus.com/Motherboards/AMD_AM2Plus/M4N72E/](http://www.asus.com/Motherboards/AMD_AM2Plus/M4N72E/) and im pretty sure it uses an athlon x2 250. 4 gigs memory and an amd 4670. still trying to work on the system and get things actually running. i guess if i could get the pvr-500 working that would be the best option as of right now, but ill take what i can get.

---

### Post by faginbagin on 2012-07-28
> **glenn3451 said:**
> the hvr-1600 is a model 1101. the computer is built on this mobo [http://www.asus.com/Motherboards/AMD_AM2Plus/M4N72E/](http://www.asus.com/Motherboards/AMD_AM2Plus/M4N72E/) and im pretty sure it uses an athlon x2 250. 4 gigs memory and an amd 4670. still trying to work on the system and get things actually running. i guess if i could get the pvr-500 working that would be the best option as of right now, but ill take what i can get.

I think you should be OK with this hardware, although the video card might be problematic.

According to Hauppauge's website, the HVR-1600 model 1101 has been discontinued and replaced with model 1387. Hopefully, that means the boards you have are not the latest ones that klc mentioned. FMI on linux support for the HVR-1600, see:
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)
To be sure, you need to get the product code found on the card, e.g. 74551. If it's not mentioned on the above web page, you could ask about it on the ivtv mailing list:
[http://ivtvdriver.org/mailman/listinfo/ivtv-users](http://ivtvdriver.org/mailman/listinfo/ivtv-users)

Your motherboard was released in early 2009, so it should be well supported by *buntu 10.10. For what it's worth, I have a frontend that uses an asus m4n68t-m v2, a phenom II x2 560, and 4 gigs of ram. So, a less capable nvidia chipset (630a vs 750a), and a more capable CPU. Other than that, they've got a lot in common, like the same lan and audio chipsets.

It might be tricky getting things to work well with your video card. You should do some research on whether to use AMD/ATI's proprietary driver (fglrx) or the open source driver (radeonhd). And the answer may be different for 10.10 than for 12.04. I think it's safe to say that most mythtv users use nvidia GPUs because they have been better supported by mythtv and nvidia on linux. But people do use AMD/ATI GPUs. I happen to have a circa 2004 thinkpad with a radeon IGP I'm using as a frontend. It has no problem playing 720p and 1080i video using the open source radeon driver. If you find the video card is a stumbling block, you might want to shop around for one with an nvidia gpu. It doesn't have to be high end. A GT430 or GT520 should be sufficient and you should be able to get one for under $30 if you shop around and trust mail-in rebates.

HTH,
Helen

---

