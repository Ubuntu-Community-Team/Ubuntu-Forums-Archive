---
title: "Hauppage 1600 glitches"
date: 2009-02-22
forum: Mythbuntu
---

### Post by dotnick on 2009-02-22
I was curious if anyone else has had this same problem and if there was a work around.

I currently have 2 cards installed, 1 Hauppage 1600 and 1 pcHDtv-5500.  Both cards are installed correctly and work, mostly without problems.  

The trouble I'm running into is that when the media center boots before the next scheduled recording (using the RTC method), if a recording is scheduled on the Hauppage card, the recording will most likely be recorded in double time.  I.E. A one hour recording will only show up as a 30 minute recording and will play in "chipmunk" speed.  Using the 0.5x option in MythTv will only slightly help, but the audio is still garbled.

I've noticed that if the Hauppage card is opened for viewing, then closed, then reopened that it will record fine.  Has anyone else had this problem and found a work around?

Thanks,

---

### Post by klc5555 on 2009-02-22
> **dotnick said:**
> I was curious if anyone else has had this same problem and if there was a work around.

I currently have 2 cards installed, 1 Hauppage 1600 and 1 pcHDtv-5500.  Both cards are installed correctly and work, mostly without problems.  

The trouble I'm running into is that when the media center boots before the next scheduled recording (using the RTC method), if a recording is scheduled on the Hauppage card, the recording will most likely be recorded in double time.  I.E. A one hour recording will only show up as a 30 minute recording and will play in "chipmunk" speed.  Using the 0.5x option in MythTv will only slightly help, but the audio is still garbled.

I've noticed that if the Hauppage card is opened for viewing, then closed, then reopened that it will record fine.  Has anyone else had this problem and found a work around?

Thanks,

This is a well-known known bug with the cx18 beta driver the 1600 uses. First analog capture after modprobe is always corrupted.

The wiki page for the card on Mythtv [http://mythtv.org/wiki/Hauppauge_HVR-1600](http://mythtv.org/wiki/Hauppauge_HVR-1600)
includes a little script for a one-second capture after modprobe to get the corrupted capture out of the way.

---

### Post by dotnick on 2009-02-22
Thank you for the link.

---

### Post by klc5555 on 2009-03-03
> **klc5555 said:**
> This is a well-known known bug with the cx18 beta driver the 1600 uses. First analog capture after modprobe is always corrupted.

The wiki page for the card on Mythtv [http://mythtv.org/wiki/Hauppauge_HVR-1600](http://mythtv.org/wiki/Hauppauge_HVR-1600)
includes a little script for a one-second capture after modprobe to get the corrupted capture out of the way.

As an update, I just discovered today that this "first analog capture" problem has supposedly been fixed in the cx18 driver. See: [http://linuxtv.org/hg/v4l-dvb/rev/76c0ec8ab927](http://linuxtv.org/hg/v4l-dvb/rev/76c0ec8ab927)

I don't know whether the fixed version of the driver has been incorporated into any of the supported Mythbuntu versions yet. My own 1600 is on a non-Ubuntu machine, for which I'll compile the new module tonight to see whether it works as advertised. I'm excited!

Cheers! :)

---

### Post by dotnick on 2009-03-03
fantastic!!!

---

