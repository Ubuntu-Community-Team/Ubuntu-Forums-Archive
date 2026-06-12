---
title: "Installing Wintv PVR USB2 failed"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by dakochan on 2007-06-09
Hi,

I'm trying to install WinTV PVR USB2 but failed.
I following the instruction from the driver author's instruction in [http://www.isely.net/pvrusb2/setup.html](http://www.isely.net/pvrusb2/setup.html).
I already got the four firmware files needed:
>     v4l-pvrusb2-29xxx-01.fw	
    v4l-pvrusb2-24xxx-01.fw	
    v4l-cx2341x-enc.fw	
    v4l-cx25840.fw
and copied the files into "/lib/firmware/2.6.20-16-generic" folder.
After that I installed MythTV.

After several times reboot, I tried to run MythTV but when I chose "Watch TV", an error message showed.
> Could not connect to the master backend server -- is it running ?
Is the IP address set for it in the setup program correctly ?
Until here, I confused. What IP address ?
In the MythTV - Setup - General, there is "Host Name: localhost".
But, I thought "localhost" should be correct name. So what's wrong ?

And then, my WinTV PVR USB2's light is not show.
Usually when I use my device in WindowsXP, the light is on to show me that the device is ready to use.

Any clue what's wrong with my configuration ?

Note: I'm using Ubuntu 7.04.

Thanks.

---

### Post by cborga1985 on 2007-06-10
**Firstly**, you probably don't have the mythbackend running so open a terminal and run "mythbackend".

**Secondly**, try extracting the firmware manually following these [instructions]("http://www.isely.net/pvrusb2/setup.html#Firmware") and then do "sudo modprobe pvrusb2".

Tell me if this helps. I've got my card to work in mplayer by doing mplayer /dev/video0 but for some reason I can't get mythtv to work with it or tvtime.


Edit: Just found [this]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O") and my setup is now working.

---

### Post by cborga1985 on 2007-06-11
hello, am i talking to myself?

---

### Post by dakochan on 2007-06-17
Hi,

I'm sorry, I cannot try your advise and reply you. Just tried your advise this morning.
My device is in /dev/video1

I tried your advise:
 > Firstly, you probably don't have the mythbackend running so open a terminal and run "mythbackend".
My mythbackend is already running. But still cannot work.

> Secondly, try extracting the firmware manually following these instructions and then do "sudo modprobe pvrusb2".
I extrated the firmware and then run "sudo modprobe pvrusb2", but it nothing happened.

> Edit: Just found this and my setup is now working.
I tried and followed the steps in the documentation.
For setting up General Setup and Capture Card, I can set properly. I can see from the mysql tables.
But, when doing the setup, I cannot set the Video Source.
I always set XMLTV listing grabber to "No Grabber" and Channel Frequency Table to "Singapore".
I use other setting also it's not working.
I also cannot see the list of Input Connections and Channel Editors.

Any idea what happened ?

Best Regards,
Dakochan

---

### Post by dakochan on 2007-06-17
Hi,

I found FAQ in ubuntu documentation website.
I dropped my mythconverge database and reinstalled myth-database, and the mythtv is now working.
Thank you so much, cborga1985.

:)

Best Regards,
Dakochan

---

### Post by cborga1985 on 2007-07-06
> **dakochan said:**
> Hi,

I found FAQ in ubuntu documentation website.
I dropped my mythconverge database and reinstalled myth-database, and the mythtv is now working.
Thank you so much, cborga1985.

:)

Best Regards,
Dakochan

your welcome

---

