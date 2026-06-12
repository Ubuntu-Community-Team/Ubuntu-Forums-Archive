---
title: "Call for Testers: HDHomerRun Utilities"
date: 2009-12-19
forum: Mythbuntu
---

### Post by rhpot1991 on 2009-12-19
I don't feel like re-typing the announcement so you can head over to my site to read about it:
[http://www.baablogic.net/drupal/node/10/](http://www.baablogic.net/drupal/node/10/)

Feel free to use this thread for discussion or to report any issues.

---

### Post by AKADAP on 2009-12-19
Not having much luck with this.
```
user@computer:~$ hdhomerun_config_gui
hdhomerun_config_gui: error while loading shared libraries: libhdhomerun.so: cannot open shared object file: No such file or directory
```

Should the installer have placed this command in one of the menus?

I do have libhdhomerun installed, but I had to install it manually. It does not appear to be in the dependencies.

---

### Post by rhpot1991 on 2009-12-20
> **AKADAP said:**
> Not having much luck with this.
```
user@computer:~$ hdhomerun_config_gui
hdhomerun_config_gui: error while loading shared libraries: libhdhomerun.so: cannot open shared object file: No such file or directory
```

Should the installer have placed this command in one of the menus?

I do have libhdhomerun installed, but I had to install it manually. It does not appear to be in the dependencies.

If you get the latest from the testing PPA this should be fixed.

---

### Post by AKADAP on 2009-12-20
> **rhpot1991 said:**
> If you get the latest from the testing PPA this should be fixed.

Got it, yes it is working now.

Some kind of progress indicator when updating the firmware would be nice, but it does appear to have successfully upgraded the firmware.

If I'm using these tuners with MythTV, how useful is the scan & other controls? How does one use this tool with MythTV for anything beyond upgrading the firmware?

---

### Post by AKADAP on 2009-12-20
I played around a bit with the scan features.
seemed to work fine until I clicked "view" on an encrypted cable channel. VLC opened, but did not bring up a video window. It did nothing so I closed it. The HDHomeRun Config window was unresponsive after that and would not redraw after it had been moved behind other windows. I had to kill it.

Are the various signal strength & quality bars in the status documented somewhere? any way to translate % to dBm or dB or bit error rate?

If signal strength reports 100% do I need to worry about overdriving the input of the tuner?

---

### Post by rhpot1991 on 2009-12-20
> **AKADAP said:**
> 
If I'm using these tuners with MythTV, how useful is the scan & other controls? How does one use this tool with MythTV for anything beyond upgrading the firmware?

Firmware and debugging are the main uses of this tool.  As far as helping with MythTV, I've always found it useful for identifying what channels are what after MythTV scans.

---

### Post by rhpot1991 on 2009-12-20
> **AKADAP said:**
> I played around a bit with the scan features.
seemed to work fine until I clicked "view" on an encrypted cable channel. VLC opened, but did not bring up a video window. It did nothing so I closed it. The HDHomeRun Config window was unresponsive after that and would not redraw after it had been moved behind other windows. I had to kill it.

Are the various signal strength & quality bars in the status documented somewhere? any way to translate % to dBm or dB or bit error rate?

If signal strength reports 100% do I need to worry about overdriving the input of the tuner?

You can't open encrypted channels with it, HDHR can only handle clear QAM.

Some of these might be better questions for upstream, you can hop in #hdhomerun on freenode and ask in there, but I'll try my best.  I think that only the tech version shows dB, and I don't signal strength of 100% should matter, but I'm also really not sure how you could get that high.  I hit mid 90's and my HDHR is right off of an amp.

---

### Post by AKADAP on 2009-12-20
> **rhpot1991 said:**
> You can't open encrypted channels with it, HDHR can only handle clear QAM.
I am aware of this, but the gui should not lock up when I try, or the gui should not allow me to try.

> 
Some of these might be better questions for upstream, you can hop in #hdhomerun on freenode and ask in there, but I'll try my best.  I think that only the tech version shows dB, and I don't signal strength of 100% should matter, but I'm also really not sure how you could get that high.  I hit mid 90's and my HDHR is right off of an amp.

Attached is a screen shot showing 100% signal. This is an OTA broadcast from 40 miles away received on a channel master 2001 antenna (about the smallest full bandwidth antenna they sell) amplified by an 8 way distribution amp with a gain of about 4 dB.
You can check out the signals at my location by looking here: [http://www.tvfool.com/?option=com_wrapper&Itemid=29&q=id%3d7b0e68523f57f1](http://www.tvfool.com/?option=com_wrapper&Itemid=29&q=id%3d7b0e68523f57f1)

---

