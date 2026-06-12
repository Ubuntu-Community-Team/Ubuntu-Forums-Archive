---
title: "WinTV-PVR-USB2 works, just not in MythTV"
date: 2009-07-03
forum: Mythbuntu
---

### Post by Bizzako on 2009-07-03
Hello all,

I am trying to configure a Hauppauge WinTV-PVR-USB2 to work with MythTV.  I know that I have the card working within Ubuntu, as both ```
sudo cat /dev/video0 > test.mpeg
``` and ```
sudo mplayer /dev/video0
``` produce a clear picture from the PVR-USB2.  Now to the problem: I can't seem to find a configuration for MythTV backend which will allow me to watch tv through the frontend. (If I click on "Watch TV" in the frontend nothing happens). I have tried setting the card up as a "Analog V4L capture card", "MJPEG capture card", "IVTV MPEG-2 encoder card", and "USB MPEG-4 encoder box", but none of them seem to work.  Can anyone write up their configuration for the WinTV-PVR-USB2 or indicate what I've done wrong?

Thanks,
Daniel

---

### Post by buzzlightyear2 on 2009-07-03
Have you had a look in the mythtvbackend.log and other logs for any clues?

---

### Post by Damanther on 2009-07-03
I believe I got mine working as a DVB card. I'll double check my settings when I get home and post them here.

---

### Post by Bizzako on 2009-07-03
Sorry, my bad...I forgot to associate the TV output with the SchedulesDirect guide data under "Input Connections".

---

