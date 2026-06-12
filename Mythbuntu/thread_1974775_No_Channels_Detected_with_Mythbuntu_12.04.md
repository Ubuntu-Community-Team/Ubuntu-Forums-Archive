---
title: "No Channels Detected with Mythbuntu 12.04"
date: 2012-05-06
forum: Mythbuntu
---

### Post by prof3205 on 2012-05-06
Hi All,

I've got an interesting problem.  My Mythbuntu box has been running fine (able to get all of the non-encrypted analog channels from cable company) on version 10.10.  The system is a Pentium 4-based box with 2GB memory, an nVidia 6800 video card and a PVR-500 tuner.

Decided to try to upgrade to 12.04.  At first, did an in-place upgrade, which completed with no problems, but when I went in and setup the tuner card, video sources and then inputs the "Scan" for channels functions shows there are no channels to add.  Checked the channel list and, yep, no channels.

Then tried a clean install of 12.04.  Same result.

Went back to a clean install of 10.10 and this time ... with the same settings, all of the channels are loaded in.

Any clue in the right direction would be greatly appreciated.

Thanks in advance.

---

### Post by jaakan on 2012-05-06
> **prof3205 said:**
> Hi All,

I've got an interesting problem.  My Mythbuntu box has been running fine (able to get all of the non-encrypted analog channels from cable company) on version 10.10.  The system is a Pentium 4-based box with 2GB memory, an nVidia 6800 video card and a PVR-500 tuner.

Decided to try to upgrade to 12.04.  At first, did an in-place upgrade, which completed with no problems, but when I went in and setup the tuner card, video sources and then inputs the "Scan" for channels functions shows there are no channels to add.  Checked the channel list and, yep, no channels.

Then tried a clean install of 12.04.  Same result.

Went back to a clean install of 10.10 and this time ... with the same settings, all of the channels are loaded in.

Any clue in the right direction would be greatly appreciated.

Thanks in advance.

did you try 11.04/.10?

Almost sound like analog channel support got dropped ( I don't think it was dropped ) anyways you might need to use different scanning settings or try one of the 11.XX versions.

I have a Hauppauge WinTV HVR 1250 and not the card you have so hopefully someone that has your card might be able to post some more ideas.

---

### Post by Quadari on 2012-05-06
I have a somewhat related problem.  Had everything working fine under 10.04 and 0.24.  Upgraded to 12.04 and 0.25 and I know can't get a few channels.  Most work fine, but any channels being broadcast on this one multiplex just won't tune in.  I'm using a Hauppage HVR-1600.  I posted another thread about this  ([http://ubuntuforums.org/showthread.php?t=1971894]("http://ubuntuforums.org/showthread.php?t=1971894")), but haven't gotten too much feedback yet, so am curious if this is a bigger problem.

---

### Post by Goncezilla on 2012-05-07
I have a 1250 as well and all my channels either don't come in or come in very scrambled. I think this is either a driver or decoder issue. No clue how to fix it or if it is even being worked on.

Upgraded from Mythbuntu 11.10 and MythTV 0.24 (with everything working well) to Mythbuntu 12.04 and MythTV 0.25 (which broke live TV).

---

### Post by prof3205 on 2012-05-13
Went back and tried out versions 11.04 and 11.10 and both versions do not detect any channels.  The capture card for the WinTV PVR500 is the IVTV MPEG-2 Decoder.

Did something get dropped starting with version 11?

---

### Post by nickrout on 2012-05-14
> **prof3205 said:**
> Went back and tried out versions 11.04 and 11.10 and both versions do not detect any channels.  The capture card for the WinTV PVR500 is the IVTV MPEG-2 Decoder.

Did something get dropped starting with version 11?

Where are you? In many places there is no more analogue tv.

---

### Post by GeoffTV on 2012-05-19
Hi,

I have the same problem. Broke the TV when updating from 11.10 (very stable) to 12.04 Myth 0.25:
The Backend sees the tuners - Dvico Fusion Dual Express
But when tuning no signal and no nois.

I am using a fairly old ibm thinkpad with extra memory.

Then tried new install of 12.04. No joy.

Went back to new install of 11.10. Would not find channels.

This is the only TV I have in the house. Not all bad as I am rediscovering radio, but, it would be nice if we could get a handle on this.

Regards,
Geoff

---

### Post by singedwings on 2012-05-20
I know this suggestion might sound simplistic and you have probably looked already. The mythtv wiki and/or the linuxtv wiki may have info on changes to your card's drivers mentioned. Ages ago I used to have to update the linuxtv drivers being used on my system to solve similar problems.

---

### Post by klc5555 on 2012-05-20
> **prof3205 said:**
> Hi All,

I've got an interesting problem.  My Mythbuntu box has been running fine (able to get all of the non-encrypted analog channels from cable company) on version 10.10.  The system is a Pentium 4-based box with 2GB memory, an nVidia 6800 video card and a PVR-500 tuner.

Decided to try to upgrade to 12.04.  At first, did an in-place upgrade, which completed with no problems, but when I went in and setup the tuner card, video sources and then inputs the "Scan" for channels functions shows there are no channels to add.  Checked the channel list and, yep, no channels.

Then tried a clean install of 12.04.  Same result.

Went back to a clean install of 10.10 and this time ... with the same settings, all of the channels are loaded in.

Any clue in the right direction would be greatly appreciated.

Thanks in advance.

It may be that analog channel scanning is broken, as it has been from time to time since most US analogs went away 3 years ago.

However, you don't actually need to scan for analog channels --unlike digitals, analog channels are easy to add manually in the channel editor. 

To test whether this is your issue, add one or two channels using the "add channels" form in the channel editor. Use the channel number in the front page of the form, and also further in, where it asks for "channel or frequency". Set this added channel as the "startup channel" for your tuner, and see whether livetv can tune it.  

If the manually added channel is tunable, you can go back into channel editor and edit its information (name, callsign, xmltvid), and add the rest of your analogs in similar fashion.

---

### Post by poe503 on 2012-05-21
If you originally had to install drivers to get your tuner cards to work (see [my tutorial]("http://ubuntuforums.org/showthread.php?t=1648472&highlight=1250") as an example) you probably need to reinstall them after an upgrade.

---

