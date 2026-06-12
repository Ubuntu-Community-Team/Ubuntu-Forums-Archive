---
title: "Where &amp; How Did The Final 10.04 Go Wrong On Wireless?!?"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by MrWizard101 on 2010-04-30
Let me explain:

I had the 10.04 LTS Beta, and upgrading until today.

I got the wireless card ( the notorious broadcom ) in the beta by adding the CD to the repository, installing through synaptic ( the broadcom drivers available from the CD ), then selecting the driver from the Hardware Device Manager, enabled, restarted and was online.

I thought the Final version would be just as smooth right?

I didn't upgrade because the OS never showed up in the Beta's Software Updates, so I figured to just do a fresh install, my biggest issue with Linux in general was solely it's conflict with broadcom, never anything else.

So anyway, In this Final Release, I go to do the same routine, check this out:

The card wasn't even showing up this time, wasn't being recognized! In the beta, it atleast showed up.

That's minor but would be major to a new guy.

I figured to do the synaptic again, add the cd then the b43cutter( i think it's called ) and succeeded, got the Card to show this time.

When I went to add the other driver ( the bcmwl-kernel ) the file that would have the driver to be enabled, it tells me "File Not Found!"
:confused::confused::confused::confused::confused::confused::confused:

Please don't give me the cop out of "Hook it up to a cable modem and download the driver" bid because that just pisses people off, we don't all have the means to carry around massive PC's to a cable modem.

What I hope to expect is someone telling me to download a file and have it on the desktop then trying it that way because I know about all the other tricks, and I think you can see, I tried em.

I'm curious to know why it worked in a Beta release and not now :(

---

### Post by MrWizard101 on 2010-05-01
***** I SOLVED THE BROADCOM 10.04LTS ISSUE DAMNIT *******


Here is what I did, this should work for everyone else as well ( because I have tried the other tricks and ways and they haven't worked for me in this release as well lol )

I put the Ubuntu 10.04 LTS CD in the drive and ran the LIVE CD.

Now, **Pay attention**, when you are running in the **LIVE MODE**, do exactly what you would do if it was installed already.

1. **Activate the STA Driver ( Not the Cutter**, *Cutter wouldn't activate for some reason, leave this alone you won't need it* )

*Once you do that, it will tell you it needs to restart*, **DON'T**

Wait a few seconds then click on the Wifi Icon in the taskbar, a few networks will show, make sure you find the one you use. You will see the option for Hidden networks, you shouldn't need to go there so don't think you do. Just click the icon on and off until yours shows.

Once you find your connection, CONNECT!

2. Now, make sure everything is good. Browse to a few sites, etc. 

If everything is good, **THEN install the LTS from the desktop. DO NOT restart then install**, otherwise the system will start from scratch again and you will fall into the same problems all over again.

Once the install completes from the Live CD running, you will boot back up and goto the network icon, click, and TADA! You're network is there and you will begin to run around, waving your arms frantically that you have done it....\o/...... yes.... you have done it...little grasshopper 
:popcorn:


*phew*

By the way, 10.04 is that good of a release to me, that I put myself through this crap because of it :lolflag:

---

### Post by danteuk on 2010-05-01
"Activate the STA Driver"
Any chance you can explain the steps you performed to do this ?

I'm using 9.10 at the moment and have I to do a build of hybredwl driver every time I update the kernel, so if your method is easier then great.
It is annoying that on a live boot of 10.4 it shows the broadcom wifi and lists it as wlan0 but says DISABLED in the lshw -C network output.

---

### Post by MrWizard101 on 2010-05-01
> **danteuk said:**
> "Activate the STA Driver"
Any chance you can explain the steps you performed to do this ?

I'm using 9.10 at the moment and have I to do a build of hybredwl driver every time I update the kernel, so if your method is easier then great.
It is annoying that on a live boot of 10.4 it shows the broadcom wifi and lists it as wlan0 but says DISABLED in the lshw -C network output.

I literally did what I explained in the previous post. In a nutshell, like this.

1. Boot Live CD (Try Ubuntu Selection)
2. Went into Hardware Manager, activated the STA Driver there ( ignore B43Cutter, it wont activate )
3. Click your wifi and choose your connection ( give it a good 10 seconds or so to show yours if it doesn't already)
4.Once connected, browse around to a few sites, make sure everything is good to go.
5. Once you're good, **INSTALL from the desktop Icon DO NOT reboot then install** (otherwise, everything will be reset and it wont let you activate it later)
6. After you install from within the Live CD, You will be able to activate the STA and connect again.


I basically repeated myself but put it in a better form lol

I was able to activate and go online the way I stated after trying all the other steps ( of adding the CD to the repository for example ) that didn't work.

Hopefully that cleared it up a bit...

Goodluck...

---

### Post by chili555 on 2010-05-01
> Activate the STA Driver ( Not the Cutter, Cutter wouldn't activate for some reason, leave this alone you won't need it )It depends on the particular Broadcom card you have. STA is correct for your model but not all models.

---

### Post by danteuk on 2010-05-02
Thanks for that, my problem is the :
"2. Went into Hardware Manager, activated the STA Driver there"

Using Kubuntu I don't have a Hardware Manager, well not one that actually lets to do anything at all with the hardware.
It's a bit like the 'Network Manager' that doesn't let you manage your network ( like I need to change from DHCP to fixed )

I guess I'll have to install gnome just to configure the hardware!

UPDATE: I found Hardware Devices window that showed, b43 and STA, I click on activate STA and it does the Download okay ( using wired network ) but fails to activate.
> Sorry - Jockey
SystemError: installArchives()failed

Can't see why, I'm booting from usb key and it has free space 1.9gb, after download STA 1.7gb so downloaded okay i think.
no error in dmesg.

it's a BCM4312
modprode shows that b43 is loaded. Should I remove that first ?

---

