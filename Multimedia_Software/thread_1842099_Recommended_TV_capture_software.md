---
title: "Recommended TV capture software"
date: 2011-09-10
forum: Multimedia Software
---

### Post by Muldon on 2011-09-10
I'm fairly new to  Ubuntu and installed TVtime, but all I could get is video and no audio. I have an Hauppauge 1800. I've searched for hours and tried a myriad of different suggestions but none have worked so far.

---

### Post by vidtek on 2011-09-11
> **Muldon said:**
> I'm fairly new to  Ubuntu and installed TVtime, but all I could get is video and no audio. I have an Hauppauge 1800. I've searched for hours and tried a myriad of different suggestions but none have worked so far.

Muldon-

We need more information about your system if we are to assist you.

Motherboard, videocard ram etc. as well as Ubuntu version.

Best regards, Tony.

---

### Post by Muldon on 2011-09-11
Thanks Tony.

I was originally just hoping for different suggestions since I read that TVtime uses OSS which evidently is no longer compiled in Ubuntu 11.04. But if we can get it to work than that would be awesome! 

My motherboard is a [GA-EP45-DS3L]("http://www.gigabyte.com/products/product-page.aspx?pid=2844#ov") 
My video capture card is a [[URL="http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800"]Hauppauge 1800]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800#Drivers")
[/URL]
This link allowed me to be able to adjust the sound: [http://ubuntuforums.org/showthread.php?t=1814991](http://ubuntuforums.org/showthread.php?t=1814991)
I have installed Gnome ALSA Mixed and made sure that all of the volume levels were not muted and up almost of all the way.

I am using the S-video and red/white RCA audio inputs. I know that all everything is going into the computer correctly since I can use the exact same setup on a tv and get both video and sound.

Thanks,
Ron

---

### Post by vidtek on 2011-09-11
> **Muldon said:**
> Thanks Tony.

I was originally just hoping for different suggestions since I read that TVtime uses OSS which evidently is no longer compiled in Ubuntu 11.04. But if we can get it to work than that would be awesome! 

My motherboard is a [GA-EP45-DS3L]("http://www.gigabyte.com/products/product-page.aspx?pid=2844#ov") 
My video capture card is a [Hauppauge 1800]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800")

This link allowed me to be able to adjust the sound: [http://ubuntuforums.org/showthread.php?t=1814991](http://ubuntuforums.org/showthread.php?t=1814991)
I have installed Gnome ALSA Mixed and made sure that all of the volume levels were not muted and up almost of all the way.

I am using the S-video and red/white RCA audio inputs. I know that all everything is going into the computer correctly since I can use the exact same setup on a tv and get both video and sound.

Thanks,
Ron

Ron-

It's good you have tested the actual physical outputs of the device you wish to capture on another tv.
If you go to the top of the Ubuntu Multimedia forum, you will fins a comprehensive sticky of troubleshooting sound problems.
I found that installing (terminal command-line) alsmixer and then installing gui pulse audio mixers worked for me.  I was able to go through the various switches and sliders and get everything to work.  No single solution presented itself, I had to use a combination of different mixers.
Best of luck, Tony.

---

### Post by Muldon on 2011-09-13
I did also look into the Comprehensive Sound Problem Solutions Guide and tried everything up to compiling a new kernel.... 

I did look into using MythTV, but it looks like a pretty daunting task just to watch TV though a cable box. This is why I was hoping there was an alternate TV capturing software.

---

### Post by vidtek on 2011-09-13
> **Muldon said:**
> I did also look into the Comprehensive Sound Problem Solutions Guide and tried everything up to compiling a new kernel.... 

I did look into using MythTV, but it looks like a pretty daunting task just to watch TV though a cable box. This is why I was hoping there was an alternate TV capturing software.

Mythtv is really great, 10 minutes to install and 2 years to configure!

An easy to use yet comprehensive solution is Kaffeine. It is reasonably configurable yet ticks all your boxes.
I had a lot of aggravation getting my sound system to work properly in Ubuntu, I have my HTPC in the garage next to the lounge, and use HDMI form my videocard, co-ax SPDIF and a piped USB socket on the wall to connect wireless key/mouse.  The coax sound was the hardest.  Persevere and you'll get there.

Tony

---

### Post by Quadari on 2011-09-14
I use MythTV (Mythbuntu, actually) on a dedicated HTPC.   The hardest part of the setup was getting all the channels set up to display correctly and download the XML data from schedules direct correctly.  That's probably because I have sort of a weird setup with the incoming cable.

Getting the drivers for the TV card and the graphics card to work together was also a fun bug to solve, but I think that isn't particular to any capture software.

If it helps, I found that the people in the Mythbuntu forum (within this site) were very responsive.

---

### Post by kwalters on 2011-09-14
I am using Ubuntu 10.04. I too tried Myth TV without success, and TV time.  I then tried Metv (I could only get it from the Ubuntu Software entry under Applications; it did not feature in Synaptic) It is a Gnome TV viewer.

It found all the Freeview channels quite easily on my card (Hauppage PVR1100).  When the program starts, go to View and Channels.  You are offered a selection of areas (geographic areas in most European countries) to scan.  I chose UK Sandy Heath, my local TV transmitter, and it immediately brought in the channels with sound and the ability to record.

All that said, today is the day when I had to retuned every digital TV in the house, and I have managed to lose all channels on MeTV; but I am sure I will get them back eventually

Keith walters

---

### Post by kwalters on 2011-09-14
I am using Ubuntu 10.04. I too tried Myth TV without success, and TV time. I then tried Metv (I could only get it from the Ubuntu Software entry under Applications; it did not feature in Synaptic) It is a Gnome TV viewer.

It found all the Freeview channels quite easily on my card (Hauppage PVR1100). When the program starts, go to View and Channels. You are offered a selection of areas (geographic areas in most European countries) to scan. I chose UK Sandy Heath, my local TV transmitter, and it immediately brought in the channels with sound and the ability to record.

All that said, today is the day when I had to retuned every digital TV in the house, and I have managed to lose all channels on MeTV; but I am sure I will get them back eventually

Keith walters
kwalters is online now Report Post   	Edit/Delete Message:P

---

### Post by TopEnder on 2011-09-16
kwalters, metv is in Synaptic Package Manager (SPM) as me-tv version 1.1.2-1 for Ubuntu 10.04 Lucid Lynx.  It is also in Linux Mint 11 SPM.  TopEnder

---

