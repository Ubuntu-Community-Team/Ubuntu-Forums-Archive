---
title: "help in getting mythbuntu working"
date: 2009-08-01
forum: Mythbuntu
---

### Post by Mia_tech on 2009-08-01
guys, I installed MythTV on top of ubuntu, but when I start it, it says mythbuntu. So I guess posting here will be just fine. My problem is that I'm trying to get my Hauppauge usb TV Video Tunner/Recorder working, since it an analog usb tunner, I don't expect to get any broadcast channels, but I hooked up the cable to it, and when I get to "Input Connections" the "Scan for Channels" is not available. Maybe, I'm trying something that is not possible like get the listing from my cable company....... the card was detected.

could anyone give me a hand with this?

Thanks in advance

---

### Post by newlinux on 2009-08-01
which hauppage tuner do you have? Have you added the capture card and created a video source?

---

### Post by Mia_tech on 2009-08-01
> **newlinux said:**
> which hauppage tuner do you have? Have you added the capture card and created a video source?

this is my card [WinTV-HVR-950Q]("http://www.happage.com/site/products/data_hvr950q.html"). I just created my video source, gave it a name and selected "cable", it started to scan, but it is not detecting anything....I'm getting "Timeout Scanning ATSC Channel # -- No Signal"

---

### Post by newlinux on 2009-08-01
How did you set your card up in myth (as a DVB would be the right way). Did you install the firmware file in /lib/firmware?

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

---

### Post by Mia_tech on 2009-08-01
> **newlinux said:**
> How did you set your card up in myth (as a DVB would be the right way). Did you install the firmware file in /lib/firmware?

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

yes, it is setup as DVB, but I haven't install any firmware, as mythtv seems to recognize it on "Card Setup"....

---

### Post by newlinux on 2009-08-01
> **Mia_tech said:**
> yes, it is setup as DVB, but I haven't install any firmware, as mythtv seems to recognize it on "Card Setup"....

Pretty sure you still need the firmware. It can recognize the card without being able to properly use it. Not getting any locks is exactly what happens with the cards I have that require firmware if the firmware isn't installed.

---

### Post by newlinux on 2009-08-01
Are you trying to scan for QAM channels or ATSC OTA channels (you mentioned something about cable before, and then you also mentioned ATSC scanning...)?

---

### Post by Mia_tech on 2009-08-02
> **newlinux said:**
> Are you trying to scan for QAM channels or ATSC OTA channels (you mentioned something about cable before, and then you also mentioned ATSC scanning...)?

what's the difference between QAM and ATSC. I setup mine with ATSC. I'm familiar with NTSC and PAL; the first one is the system use in US and the latter in Europe, but I've never heard about the other two up until now.

---

### Post by Mia_tech on 2009-08-02
ok, I found an article online that explains the difference [here]("http://www.dvrplayground.com/article/14399/What-is-the-difference-between-NTSC--ATSC-and-QAM-/"). I think that my tuner is analog, so it would not receive ATSC which is the new digital standard for broadcast TV. But if I want to get my cable through the tuner, I have to set it to QAM. I watched a tutorial where they mention using "Schedule Direct TV," which is only 20$ a year for the subscription. Is this signal broadcast through the air? How does it works? I went over their [website]("http://www.schedulesdirect.org/") but didn't find enough info.

Thanks

---

### Post by newlinux on 2009-08-02
> **Mia_tech said:**
> ok, I found an article online that explains the difference [here]("http://www.dvrplayground.com/article/14399/What-is-the-difference-between-NTSC--ATSC-and-QAM-/"). I think that my tuner is analog, so it would not receive ATSC which is the new digital standard for broadcast TV. But if I want to get my cable through the tuner, I have to set it to QAM. I watched a tutorial where they mention using "Schedule Direct TV," which is only 20$ a year for the subscription. Is this signal broadcast through the air? How does it works? I went over their [website]("http://www.schedulesdirect.org/") but didn't find enough info.

Thanks
Your tuner supports NTSC (analog only used for cable in the U.S. now) QAM, and ATSC (OTA 8vsb). What are you trying to tune?

Schedules direct is only for guide information. you don't need it to watch channels, and there are other places to get guide information. You download it from their servers nightly (or how often you'd like). 

With QAM, you can only get unencrypted channels. You can try and look at [http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us) to see what channels are available digitally (OTA-8vsb and unencrypted QAM) in your area.

---

### Post by newlinux on 2009-08-02
Have you loaded the firmware? If you have if you want to do QAM, set your card as DVB and when you scan do a full scan for QAM-256 (what most providers use in most areas) and QAM-64. They may take a while to complete.

---

### Post by Mia_tech on 2009-08-02
I have installed the driver. How do I find out whether it detected the card? Oh, I did another scan, and I still didn't get any locks on channels.... I posting two screenshots of my configuration, take a look and let me know if you see something odd.

---

### Post by Mia_tech on 2009-08-02
I finally got it working, but the image is not showing with the correct depth, which is 16:9, in other words is not taking up all the screen

---

### Post by newlinux on 2009-08-02
> **Mia_tech said:**
> I have installed the driver. How do I find out whether it detected the card? Oh, I did another scan, and I still didn't get any locks on channels.... I posting two screenshots of my configuration, take a look and let me know if you see something odd.

Driver and firmware are not the same thing. The drivers should be in the kernel, the firmware is what you needed to install.
> **Mia_tech said:**
> I finally got it working, but the image is not showing with the correct depth, which is 16:9, in other words is not taking up all the screen
I assume you have installed the firmware now. It might be helpful if you tell others what you did between the last post and this one to get it working. The aspect ratio is partially controlled by the what the channel you are tuning is, how you have your monitor aspect setup in the playback settings in mythfrontend, and what screen resolution you are passing to your monitor. You'll need to check all three...

If the TV source is actually transmitting 16:9 with black bars on the side (which many digital stations do when broadcasting non HD content) then there isn't much you can do.

---

### Post by Mia_tech on 2009-08-02
well, I installed the firmware and selected the right setting before scanning for channels in my case QAM-64 or 256 (Cable). Don't get impatient, if at first when you start scanning, it says "No Lock" it is just looking for channels eventually it will get a lock on the channels and add them. About the ratio, in my case it is for a LCD TV, so I will try to play with the frontend setting and see if I can make it fill the screen for those channels where it is possible to do so; I'm aware that not every channel transmit in that ration; therefore, it is not possible to view the image in 16:9. 

One question: after the new firmware is installed, is it possible to get ATSC channels with this tuner?

---

### Post by newlinux on 2009-08-02
> **Mia_tech said:**
> well, I installed the firmware and selected the right setting before scanning for channels in my case QAM-64 or 256 (Cable). Don't get impatient, if at first when you start scanning, it says "No Lock" it is just looking for channels eventually it will get a lock on the channels and add them. About the ratio, in my case it is for a LCD TV, so I will try to play with the frontend setting and see if I can make it fill the screen for those channels where it is possible to do so; I'm aware that not every channel transmit in that ration; therefore, it is not possible to view the image in 16:9. 

What resolution are you displaying at? What is the native resolution of your tV set? You should be able to get everything to actually display at 16:9. It just may not look like it if the channel has put black bars to make a 4x3 image fit a 16:9 aspet ratio.

> 
One question: after the new firmware is installed, is it possible to get ATSC channels with this tuner?

According to the specs it should be.

---

