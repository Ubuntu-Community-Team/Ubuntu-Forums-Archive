---
title: "Pinnacle PCTV HD 800i with mythbuntu 9.04 problem"
date: 2009-09-27
forum: Mythbuntu
---

### Post by SpicyLemon on 2009-09-27
I'm trying to set up mythtv to use a Pinnacle PCTV HD 800i card.

I'm using a fresh install of mythbuntu 9.04.

All I seem to be able to get is a black screen sparsely populated with vertically moving dots.  When I try to scan for channels, none can be found.

The signal is from Bresnan cable and is coming in via a coaxial cable. All I'm trying to get are the basic low numbered channels.

I've used the [wiki page for the card]("http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Card_(800i)") as a reference but I must still missing something.

I've retrieved the [firmware file](http://www.kernellabs.com/firmware/xc5000/) (the one from the wiki update).

I've retrieved the v4l-dvb directory and ran "make" and "make install" without any errors.

I've tried multiple setups with the capture cards:

[LIST=1]
[*]Just a V4L
[*]A V4L then a DVB
[*]A DVB then a V4L
[*]A USB MPEG-4 encoder
[*]I can't remember all the other random setups I've tried.
[/LIST]

The only video device available for selection is /dev/video0.  I tried changing it to /dev/video but it wouldn't let me save that.

The card worked in my previous computer (Mythbuntu 8.10).

I know the signal is getting to the card because I hooked the cable up to the Analog tuner in my TV and received the channels.

My previous setup was using the same cable provider too.

Can anyone help me out here? I'm not completely new to linux, but I still consider myself a noob.  I can get around, I just don't know where to go or where to put things.

edit: I can see the HUD just fine too.

---

### Post by Crash87ss on 2009-09-28
Sounds like your almost there. I just set one up not too long ago in my system. Took me a while, but turned out the drivers were working and I was just setting myth up wrong. 

The cature card should be set up as DVB. The card type should (at least in my case) come up as a samsung somthing. 

Then make sure you set up the video sources and input connections. Appartenly these are pretty important :)

take your time going through the screens and give them valid names (I used Transmitted for video sources and TV for input).

Seems silly, but I installed/re-installed drivers and firmware half a dozen time before realizing. Hope this helps! let us know!

---

### Post by efolse on 2009-09-28
do you have an ati graphics card?
Did you restart the machine after copying the firmware update?

crash87ss is right it is a dvb that reads as a samsung s5h1409 something.  turn off the EIT and check the use the card on demand option under the recording options section of the card setup screen.  (or the back end crashes)

I would delete all other cards on the machine if the 800i is the only thing installed on the machine.  Do not forget to tell Mythtv to use the cable as default in the general section.  Then double check the video sources input connections.  The channel frequency table in the video sources is default.  The EIT is not check.  Then try the channel editor scan.  Let me know how that works.

---

### Post by SpicyLemon on 2009-09-28
No luck yet.

My motherboard has an "Integrated ATI® Radeon™ HD 3200 Hybrid Graphics with up to 256MB of Shared Video Memory"
I didn't think the graphics card would be a problem since I get the HUD when "watching" live TV, even though the feed is black.

I'm a little confused about where to place the firmware.  One place says /lib/firmware. Another says /lib/firmware/2.6.28-11-generic.  I also have a directory /lib/firmware/2.6.28.15-generic. Also, the wiki mentions to use dvb-fe-xc5000-1.6.114.fw instead of the one extracted from the windows driver. Is that correct?

I've tried all three individually with restarts between tries.  I even tried all three at once.  Does it matter which of those it's in?

Per suggestions, I deleted all of my capture cards and created this one:
Card Type: **DVB DTV capture card (v3.x)**
DVB Device Number: 0      (only option)
Frontend ID: Samsung S5H1409 QAM/Subtype: ATSC
Signal Timeout(msec): 3000
Tuning Timeout (msec): 5500
Under Recording Options:
Max recordings: 2
**unchecked** :Wait for SEQ start Header.
**checked**   :Open DVB card on demand
**unchecked** :Use DVB Card for active EIT scan
DVB Tuning Delay (msec): 0

Under video sources, I have a schedules direct source set up called "source_cable".  Channel frequency table: default

Under Input Connections I set up
[ DVB : 0 ](DVBInput) -> source_cable

details:
Display name: **DVB_cable**
Video source: **source_cable**
Use quick tuning: Live TV only
checked   :Unencrypted channels only
checked   : Allow audio only channels
unchecked :Use DishNet Long-term EIT Data

On the next page I have
Input priority: 0
Input Group 1: DVB0
Input Group 2: Generic

On the second page of the "general" setup I selected Channel frequency table: **us-cable**

Anything in bold is something that I changed from the defaults

I've tried the following parameters to scan for channels and none of them found anything (I usually stopped it after channel 5 or 6 since it should pick up 2, 3, and 4).  The Signal Strength stays at 0% and where applicable, so does Signal/Noise. Also, the message "No Lock" appears right after the scan starts.

Failed scanning parameters tried:

Frequency Table: Cable   Modulation: Terrestrial (8-VSB)
Frequency Table: Cable   Modulation: Cable (QAM-256)
Frequency Table: Cable   Modulation: Cable (QAM-128)
Frequency Table: Cable   Modulation: Cable (QAM-64)

Frequency Table: Broadcast   Modulation: Terrestrial (8-VSB)

Frequency Table: Cable HRC   Modulation: Terrestrial (8-VSB)
Frequency Table: Cable HRC   Modulation: Cable (QAM-256)
Frequency Table: Cable HRC   Modulation: Cable (QAM-128)
Frequency Table: Cable HRC   Modulation: Cable (QAM-64)

Frequency Table: Cable IRC   Modulation: Terrestrial (8-VSB)
Frequency Table: Cable IRC   Modulation: Cable (QAM-256)
Frequency Table: Cable IRC   Modulation: Cable (QAM-128)
Frequency Table: Cable IRC   Modulation: Cable (QAM-64)

In all of those scans, the type was "Full Scan" and Input was "[ DVB : 0 ](DVBInput)"

Am I missing something somewhere else? Do I need to check where the drivers went or something?

---

### Post by efolse on 2009-09-28
ok, everything sounds right except the firmware update.

in the directory with the download open the terminal in that directory then type bash extract.sh

Let me know if it complains about unzip. The last line says something like eg sudo cp dvb-fe-xc5000-1.1.fw /lib/firmware/2.6.28-15-generic.  Just copy the part that says "sudo cp dvb-fe-xc5000-1.1.fw /lib/firmware/2.6.28-15-generic" and paste it on a new line( no quotes).  you will have to type in your pastword then after you will need to restart the machine.  then try those rescans again.  BTW it would be something like 2.6.28-11-generic if you did not update recently.

I will check back in a few min. to see how it worked.  If it did not work I would google the cable provider and mythtv on the search line and see if anyone else has posted which scan works.

---

### Post by SpicyLemon on 2009-09-28
I switched back to the older firmware - dvb-fe-xc5000-1.1.fw - and deleted the one I had in there, dvb-fe-xc5000-1.6.114.fw. Rebooted, tried all the scans again, still nothing.

Should I get an older v4l-dvb tree? If so, do I need to worry about removing the old one?

---

### Post by efolse on 2009-09-28
The new kernel has the support for the card built in. so we should have been ok.  I have a easier fix if you are game.  Analog is still available if you wish I can walk you through that.  Most of the cable transmitted is the older analog which is why you did not need the converter box when the nation switch over.  Or we can Google and find the qam for you cable service provider.

you did not need to rebuild the v4l; it use to be needed but not anymore with mythbuntu.

---

### Post by efolse on 2009-09-28
I just tried dvb-fe-xc5000-1.6.114.fw.  It did not work in my system  either.

---

### Post by SpicyLemon on 2009-09-28
Yeah, swapping back to the  dvb-fe-xc5000-1.1.fw firmware and adding/using a V4L analog capture card did it.

I still have the DBD capture card in there so that it keeps the setting about DBD only being on when active.  However, in the input connections for the DVB entry, I changed video_source back to "(none)".

Thanks for the help!

---

### Post by efolse on 2009-09-28
I been wondering... did you rebuild the v4l prior to the kernal update or after.  If before you would need to rebuild the v4l and then use the new firmware.  If not ... well you seem to have it working.  Just it kept me from sleeping.

---

### Post by SpicyLemon on 2009-09-29
I had the 1.1 fw in place when I downloaded the V4L, ran make and make install on it, and rebooted.  Later, I couldn't get things working and saw a note on my card's wiki page stating that I needed to use the newer 1.6.114 fw. That's when I tried swapping to the newer firmware.

---

### Post by grenloch101056 on 2009-10-06
did you ever get digital portion of this card working?  I'm running into the same problem with 9.04 as well.  I have tried both versions of the firmware and cant get it to work.  The card isnt even recognized with the new firmware, only with the older version.  would rebuilding the drivers with the new version of the firmware in place solve the problem??

---

### Post by twelve17 on 2009-10-19
I am having the same exact issue.  Neither firmware version is working for me.  The driver seems to be explicitly looking for the 1.1 version, so if I only have the 1.6.115 version, it won't work:

```



Oct 19 23:11:48 austin kernel: [  199.352046] xc5000: Firmware has not been loaded previously
Oct 19 23:11:48 austin kernel: [  199.352049] xc5000: xc5000_init()
Oct 19 23:11:48 austin kernel: [  199.354149] xc5000: xc5000_is_firmware_loaded() returns False id = 0x2000
Oct 19 23:11:48 austin kernel: [  199.354154] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
Oct 19 23:11:48 austin kernel: [  199.354159] i2c-adapter i2c-0: firmware: requesting dvb-fe-xc5000-1.1.fw
Oct 19 23:11:48 austin kernel: [  199.359797] DVB: registering new adapter (cx88[0])
Oct 19 23:11:48 austin kernel: [  199.359801] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
Oct 19 23:11:48 austin firmware.sh[5484]: Cannot find  firmware file 'dvb-fe-xc5000-1.1.fw'

```

Using the 1.1. firmware, the tuner finds no channels.

---

