---
title: "Karmic 9.10 Mythtv can't scan for channels"
date: 2009-11-07
forum: Multimedia Software
---

### Post by wincen on 2009-11-07
I just installed Ubuntu 9.10 and Mythtv.  I've got an older Pinnacle PCTV Pro (Analog only) which uses the bttv and snd_bt87x modules.  When setting up the backend I cannot scan for channels or fetch channels from listings source.  The scan for channels button is disabled and the fetch channels from listings source does nothing.  How do you fix this?

I did install Mythtv on Ubuntu 9.04 and got it working.  The way I've set up the capture card is the same.  Is this a bug?  Are there workarounds?

---

### Post by Ugly! on 2009-11-07
Same problem here. Worked fine in jaunty. Now Scan channels button is disabled. Maybe a problem with mythtv 0.22?
This might need a bug report.

Regards

---

### Post by davidhoenig on 2009-12-22
I have the same problem. Stock install Karmic 9.10. My hardware is a Hauppauge HVR-850 USB tuner. I had it working fine on 9.04. When I am in Mythtv setup the "scan for channels" is disabled, and when I click on "fetch listings from source" nothing happens.

Under the general page there is no option for ATSC, only NTSC. I thought ATSC is what is needed for OTA digital channels?

---

### Post by AW01545 on 2009-12-22
I'm looking at the same problem, I noticed that its under Input Connections now, under channel editor, then Channel Scan.
 
I didn't meet with much success though...still trying to understand.
 
Now I'm trying to download the channel logos, and that's taking awhile!
 
UPDATE, wrong about it being under Input Connections, its the next menu item after Input Connections on the Backend Configuration , not a submenu of it.
 
Now, under Input Connections, there is a Scan for Channels menu item, but its disabled for my two V4L cards.  I have one IVTV card (an HVR-1950), and that one has the scan for channels options.  The only thing for me is that it gets up to about Channel 5 and gets 'no lock', and then doesn't seem to proceed anymore.  Now, I can confirm that on my analog CATV service, channel 5 is problematic (I think they are still having trouble from the switchover to digital.)

---

### Post by davidhoenig on 2009-12-22
I did find the Channel Scan under Channel Editor, but I cannot select that button either -- when I use the arrow keys to change the selection it just skips right over it.

Interestingly I do have a few channels in my list, but none of them are from around here. I double checked my ScheduleDirect login info and Myth does show my channel listing so it is connecting. Not sure why it is not getting the right channel data.

---

### Post by sabs on 2009-12-26
I have experienced a similar problem. My Pinnacle PCI 310 worked perfectly with Kaffeine on Jaunty. But after changing to Karmic Kaffeine will scan but not achieve a signal lock.

I guess thats what I get for changing from Jaunty to Karmic before the bugs are ironed out.

---

### Post by davidhoenig on 2009-12-27
I solved my problem: it was not an issue with Mythtv but rather in my setup. Under "Capture Cards" I saw my hardware was correctly identified as Hauppauge, but did not notice that it defaulted to "Analog V4L device". When I changed this to DVB I was able to successfully scan channels and watch TV. I hope this helps.

---

### Post by samster on 2010-01-18
Same problem here.  Fresh install of 9.10, and I have an ATI TV-Wonder VE.
I have set the options so it is now card=64, and tuner type=2, and this is the most frustrating thing in the world! ](*,)

During MythTV setup, the scan for channels button is grayed out with this analog card.  I am spending way too much of my life trying different combinations of settings, etc, and nothing is working nor helping.  I have analog cable.

I can't do channel scan, so I can't use MythTV for anything except the weather forecast, which is pretty pointless.

IS THERE A WORKAROUND FOR GETTING ANALOG CHANNELS TO SCAN IN WITH MYTH TV?  WILL IT BE FIXED?

This card and setup works _flawlessly_ with TVTime - what's wrong with Myth TV?  

Thanks anyone for help and/or sympathy!
--Samster

---

### Post by coniefl on 2010-01-25
I had the same problem and what worked for me was that I set the Capture Card Setting from "Analog V4 capture card" to "IVTV MPEG-2 Encoder Card" and kept the input as "Television". I was able to do the channel scan. Then I changed he Capture Card Setting  back to "Analog V4 capture card", and used the channels that were successfully scanned.

There was a slight problem with the scan, it would get stuck on a channel and do nothing, I simply hit the back button, then the next button and the scan would continue, I had to do this 5 or 6 times, but I got all the channels.

Hope this helps.

---

### Post by jhbowlin on 2010-01-31
I have just installed MythBuntu 9.10 and I can't scan (scan button is disabled) using my Motorola DCT-6200, but my HDHomeRun scans fine.

---

### Post by marting1984 on 2010-02-23
Here is a workaround that Worked For Me (TM):

```
sudo apt-get install xawtv
scantv -c /dev/video0 -C /dev/vbi0 -o ~/.xawtv
```Then print the file ~/.xawtv and use that information to manually enter all channels into mythtv-setup. Somewhat labor-intensive but you only have to do it once.

---

### Post by dalhamir on 2010-02-27
scan-tv doesn't seem to work for me either. I have a hauppauge 150 and a digital antenna. I selected ntsc and us-bcast. There was an message:

invalid value for input: Television
valid choices for "input": "Tuner 1", "S-Video 1", "Composite 1", "S-Video 2", "Composite 2"

The antenna is plugged in to tuner 1, so I figure I need to change what scan-tv is trying to use as the input some how...

---

### Post by il-luzhin on 2010-03-25
Wow, I'm sorry I updated my OS.  

Anyone gotten anywhere with this battle?

---

### Post by eldragon on 2010-03-25
> **il-luzhin said:**
> Wow, I'm sorry I updated my OS.  

Anyone gotten anywhere with this battle?

there is nowhere to go since the myth devs disabled it for a reason, the driver is buggy and breaks, this is why it was disabled.

i guess you could always hunt the code down where it is being disabled and reenable scanning for analog capture cards. but who knows what might happen ;)

just add the channels manually. and backup your db in the future ;)

---

### Post by AKADAP on 2010-03-26
I have an ATI HDTV Wonder that I have never been able to get the analog portion working on.
I'm running the nightly builds of MythTV, and they have recently re-enabled the channel scan. Does not do me much good though since it whips through all the channels in about 10 seconds and finds nothing.

---

### Post by beerse on 2010-03-30
Unfortunately, myth 0.22 (as in ubuntu 8.10) has a problem scanning for analog channels. The myth that came  with 8.10 could scan for channels but did not work, the update in 0.22 is to disable the scanning.

To get analog channels configured in myth, there are some ways:
- install 8.04, configure myth and then upgrade. This has other flaws...
- copy the channel configuration from an other myth instance, its only one database table.
- configure the analog channels manually, either with the myth setup scheme or using mythweb and then direct in the database.

Nope, I donnot go in details here, use the documentation to get your way.

---

### Post by unclepedro on 2010-07-30
> **davidhoenig said:**
> I solved my problem: it was not an issue with Mythtv but rather in my setup. Under "Capture Cards" I saw my hardware was correctly identified as Hauppauge, but did not notice that it defaulted to "Analog V4L device". When I changed this to DVB I was able to successfully scan channels and watch TV. I hope this helps.

For posterity: On a new install of Lucid, I had the same error -- in my case I changed my cards to MPEG capture cards (since they are) and then I had no trouble with the channels.

---

