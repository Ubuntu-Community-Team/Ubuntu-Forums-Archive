---
title: "AMD 690G based MB"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by biker19 on 2007-04-01
I plan to use an MSI K9AGM2-FIH MB as the basis for a MythTV PVR project. I also plan to use a Kworld tuner card - if I ever get it working. 

What are the chances that Ubuntu (any flavor) will work right away on such a new platform?

---

### Post by HotFoot on 2007-04-03
I've just bought an ASUS M2A-VM board and I'm playing around with the beta release of 7.04 on it.  I don't plan on using MythTV, but I hope to get all the basic features working, such as 3D acceleration.  The onboard sound was working out-of the box, but I haven't gotten all the video system set up yet.

---

### Post by biker19 on 2007-04-05
My main worry is the functionality of the HDMI port - that's how I plan to connect to the TV - the main reason I'm waiting for the MSI MB. That and things like a SATA DVD drive.

I'm also waiting a bit since I heard that there'll be cuts in AMD CPU prices next week.

---

### Post by HotFoot on 2007-04-05
Okay.  I have the version with DVI-out (I use a DVI-HDMI cable).  The graphics acceleration works just fine, though I haven't gotten my resolution to output to 1360x768 yet.  I'm running at 1280x720 instead for now.  DVI and HDMI are pin-compatible, so you should get very similar results.  I think the biggest problem is going to be HDCP.  I don't imagine playback of blu-ray or HD-DVD will work in Linux.

I should note that, with Feisty, getting the video drivers working was easier than ever before.  The "Restricted Drivers Managament" function worked great.  My only complaint is the lack of support for the 1360x768 resolution.

Operation of the SATA HDD is normal.  I have no idea what's involved beyond that for a DVD drive.  I would like to know, however, since I am planning to get a new drive soon and SATA would be a plus.

---

### Post by biker19 on 2007-04-05
Other than a PCI tuner card I plan to leave behind all old technology including floppy and all IDE devices.Trying to shoehorn the wide ribbon cables for floppy and IDE HDDs and optical drives in a small case is for the birds when SATA devices are readily available.

It's good to hear the DVI port works and I'll assume the HDMI port will as well. I'm not worried too much about HDCP - it will be a very long time before I use any HD type drive. As  matter of fact my set up might not have any optical drives at all after install. I just basically want to built a Tivo like PVR with no need to archive. I can do that on another PC if needed.

---

### Post by maynoth on 2007-04-12
can you tell me how you got it to install on that motherboard... I have the M2A-VM (Asus) and latest bios update... but I the install cd's (edgy and feisty 32bit) lock up...

---

### Post by HotFoot on 2007-04-12
I haven't tried the 32-bit versions, but I can't see why they wouldn't be working while the 64-bit one does.  The installation for me was normal...just followed the instructions, though the installation setup program would crash often during the manual configuration of the HDD parititions, the actual installation worked.  Oddly enough, the 64-bit Edgy CD wouldn't boot into LiveCD mode once I had Feisty installed, so maybe I'm just lucky to have gotten things working in the first place.

More information that may be relevant to you is that my HDD is a Seagate 7.10 SATA drive, and the DVD drive uses an IDE connection.  If you have a SATA DVD drive, I have no idea if that could cause a problem.

---

### Post by maynoth on 2007-04-14
yes the 64bit at least loads... but the ethernet driver doesn't seem to work :C

---

### Post by maynoth on 2007-04-19
the latest 32bit feisty fawn will work if you disable HPET(High Precision Event Timer) in the bios

---

### Post by biker19 on 2007-04-22
So I got my MSI 690G based board and set up the new PC this weekend. I got just about everything working in Vista so it was onto Ubuntu - no go. Right at boot up from the beta Feisty CD I get an error after the initial screen saying the xorg won't work cause it can't find a compatible display. I have the PC connected via HDMI to my Sony TV. Anyone know how to get around this? The display obviously works enough to see the initial boot screen.

---

### Post by HotFoot on 2007-04-22
> **biker19 said:**
> So I got my MSI 690G based board and set up the new PC this weekend. I got just about everything working in Vista so it was onto Ubuntu - no go. Right at boot up from the beta Feisty CD I get an error after the initial screen saying the xorg won't work cause it can't find a compatible display. I have the PC connected via HDMI to my Sony TV. Anyone know how to get around this? The display obviously works enough to see the initial boot screen.

I have a lot of problems using the DVI-HDMI connection on my M2A-VM board.  I can get the display working, but not at the right resolutions and there are issues with the TV not recognizing the signal.  For now I'm using the VGA connection, but I'm beginning to wonder if the display issues we're having are to do with some sort of DRM keys required to properly use the DVI/HDMI connection features.  I wonder because it's working in Vista, you say, but not in Ubuntu.

---

### Post by biker19 on 2007-04-23
I don't think it's DRM related - Vista at least can get by the installation by keeping the default VGA settings. I can then install the ATI control center to adjust the settings to properly fit on the TV screen. Ubuntu won't proceed with the default settings - it tries to find a setting and when it can't, it crashes. I thought there might be a switch during the install to skip the display discovery process and let it install with the default settings. :confused:

---

### Post by chiques on 2007-10-22
> **HotFoot said:**
> I have a lot of problems using the DVI-HDMI connection on my M2A-VM board.  I can get the display working, but not at the right resolutions and there are issues with the TV not recognizing the signal.  For now I'm using the VGA connection, but I'm beginning to wonder if the display issues we're having are to do with some sort of DRM keys required to properly use the DVI/HDMI connection features.  I wonder because it's working in Vista, you say, but not in Ubuntu.

Well there seems to be a known issue with the TV port "flickering" acknowledge by ATI. Check out the release notes on [http://game.amd.com/us-en/drivers_catalyst.aspx?p=xp/integrated-xp]("http://game.amd.com/us-en/drivers_catalyst.aspx?p=xp/integrated-xp") . This fix is only for Windows right now, I hope they fix it for Linux soon. I'm ONLY using the M2A-VM HDMI board and I have a Sharp LCD TV. :(

---

