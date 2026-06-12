---
title: "DVDs won't play in Mythbuntu"
date: 2009-02-11
forum: Mythbuntu
---

### Post by brian_hayward on 2009-02-11
I am using the current release of Mythbuntu, with a Hauppauge PVR-350.  I can't get DVDs to play using the Mplayer or the internal player in Mythbuntu.  Is there some special setup that i need to do before i can play DVDs that i have missed.  any help would be greatly appreciated.  thanks

---

### Post by dad311 on 2009-02-11
> **brian_hayward said:**
> I am using the current release of Mythbuntu, with a Hauppauge PVR-350.  I can't get DVDs to play using the Mplayer or the internal player in Mythbuntu.  Is there some special setup that i need to do before i can play DVDs that i have missed.  any help would be greatly appreciated.  thanks

Did you read the Ubuntu install Doc?

[https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd)

---

### Post by klc5555 on 2009-02-11
> **brian_hayward said:**
> I am using the current release of Mythbuntu, with a Hauppauge PVR-350.  I can't get DVDs to play using the Mplayer or the internal player in Mythbuntu.  Is there some special setup that i need to do before i can play DVDs that i have missed.  any help would be greatly appreciated.  thanks

If you haven't done so, go to the Mythbuntu control center, open the Proprietary Codecs tab, and install the codices for playing commercial DVDs. It's not done automatically with the base install because of licensing issues.

---

### Post by brian_hayward on 2009-02-11
> **klc5555 said:**
> If you haven't done so, go to the Mythbuntu control center, open the Proprietary Codecs tab, and install the codices for playing commercial DVDs. It's not done automatically with the base install because of licensing issues.

Ok so i had all the plug-ins installed already and nothing works still.  I tried to play the dvd's in xine and mplayer (without mythtv running) and xine gave me a message that i may not have rights to the drive.  I checked the /etc/fstab file and the dvd rom doesnt even show up in it.  i did however run dmesg and i found the dvd drive in that output.  i thought i should try to manually mount the drive but my inexperience is holding me down...something i didnt mention before which i probabbly should have...i have both a dvd rom and cdrom drive...i took off the cover of my pc and i see that there are jumpers on the dvd drive and cd rom drive...im guess that the dvd drive is a slave...would that have any effect on playback and the permissions settings?

---

### Post by nickrout on 2009-02-11
> **brian_hayward said:**
> Ok so i had all the plug-ins installed already and nothing works still.  I tried to play the dvd's in xine and mplayer (without mythtv running) and xine gave me a message that i may not have rights to the drive.  I checked the /etc/fstab file and the dvd rom doesnt even show up in it.  i did however run dmesg and i found the dvd drive in that output.  i thought i should try to manually mount the drive but my inexperience is holding me down...something i didnt mention before which i probabbly should have...i have both a dvd rom and cdrom drive...i took off the cover of my pc and i see that there are jumpers on the dvd drive and cd rom drive...im guess that the dvd drive is a slave...would that have any effect on playback and the permissions settings?

no.

do you have libdvdcss installed?

---

### Post by brian_hayward on 2009-02-11
> **nickrout said:**
> no.

do you have libdvdcss installed?

Yes i have the libdvdcss installed...however it appears that i need to go back to school and learn how to read...my dvd rom drive that i thought i had is not a dvd rom drive at all...chalk this one up to stupidity...thank you all for you help though.

---

