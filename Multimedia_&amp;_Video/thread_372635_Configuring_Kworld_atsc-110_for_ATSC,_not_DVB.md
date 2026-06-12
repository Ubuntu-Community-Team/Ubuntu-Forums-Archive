---
title: "Configuring Kworld atsc-110 for ATSC, not DVB"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by Tdonohue on 2007-02-28
I cannot get this card to work.  Every guide that does get it to work shows installing some DVB firmware.  Unless I'm mistaken, this isn't going to help me in the US.  Has anyone gotton this card to work with ATSC?  Mythtv shows it as kworld atsc-110, but I can't use it to watch tv.  It will only pull signal from the other kworld analog tuner (seperate card, not the bottom input).  I can't get a signal through any of the inputs on this card.

Obviously people have more than one tuner in their system, but for some reason I can't get it to work.  There are no guides to help me with this problem, so I am clearly the only person struggling with this.

I can't verify that the card even works.  cat /dev/video1 ....  returns error.  Trying to play it in mplayer returns an error.  TVtime only gives me the signal from the other tuner card.  How do I tell it to use a different card?

Should I install this DVB firmware to get NTSC or ATSC reception in the US?  Seems all wrong to me!

In order to get the other card to work (single analog kworld tuner), I had to add "saa7134" to the bottom of some module (don't know the details as I'm at work, but it was mentioned in several other threads).  Do I need to do something for this card?

After getting wireless internet with WPA working, Mysql and Mythtv working, and all the other quirks that come with configuring a linux pc for daily use, this problem I'm having seems trivial but I just can't figure it out. 

Can somebody please help me.  I'll be forever grateful!

---

### Post by heywire on 2007-03-12
I use this card under ubuntu using the dvb firmware.  I am tuning QAM 256 channels from Time Warner (I'm in Ohio).

This guide works for me:

[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)

Let me know if you need any help setting this up.  This card seems to work better under linux than windows!

---

### Post by Vincent_Lin on 2007-03-12
Oh yes, you need to have the firmware loaded before atsc-110 works.

Follow the link provided by heywire and it will work.  It is also advised if you work on one card at a time before you put them together.  Pull your ananog card and use atsc-110 only, and then follow the instruction in above link.

Does anyone know for sure that atsc-110's qam256 works for Comcast digital cable signal?  Even currently I only use mythtv+atsc-110 to receive ATSC OTA HD signals, I really like to "hook" my Comcast cable to this card as well. 

Thanks.

Vincent

---

### Post by smit0737 on 2007-03-18
I keep seeing references to /[kernel source directory]/Documentation/dvb, but I can't find this directory.  I've tried using slocate to find this directory and the get_dvb_firmware perl script that should reside in this location.

I'm trying to install mythtv with a Kworld ATSC 110 card on a fresh install of Edgy.  Can anyone help me understand where to look or if I need to do set something else up in order to get to the point where this directory exists?

---

### Post by modorf on 2007-03-19
> **smit0737 said:**
> I keep seeing references to /[kernel source directory]/Documentation/dvb, but I can't find this directory.  I've tried using slocate to find this directory and the get_dvb_firmware perl script that should reside in this location.

I'm trying to install mythtv with a Kworld ATSC 110 card on a fresh install of Edgy.  Can anyone help me understand where to look or if I need to do set something else up in order to get to the point where this directory exists?

From MythTV Hardware DVB, ATI HDTW Wonder section, instructions on downloading and installing KWorld ATSC 110 firmware.  The ATI and KWorld cards use the same firmware:
  [https://help.ubuntu.com/community/MythTV_Hardware_DVB]("https://help.ubuntu.com/community/MythTV_Hardware_DVB")

```
 
The firmware can be obtained as follows:

    *

      1) Download this script.
          o

            get_dvb_firmware

      2) Make it executable.
          o

            chmod +x get_dvb_firmware

      3) Run the script to obtain the firmware
          o

            ./get_dvb_firmware nxt2004

      4) Copy the firmware to /lib/firmware
          o

            sudo cp dvb-fe-nxt2004.fw /lib/firmware

       5) Test the module

     *
         sudo modprobe saa7134-dvb

         dmesg | tail 

          look for: 
          [   27.434358] DVB: registering new adapter (saa7133[0]).
          [   27.434362] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)..

          [   46.779693] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
          [   46.824299] nxt2004: Waiting for firmware upload(2)...
          [   47.617330] nxt2004: Firmware upload complete

          HDTV interface is ready.     

```


Currently have KWorld ATSC 110 tuning Comcast cable - Boston, MA (QAM 256, us-cable-hrc).
I am receiving the basic networks (GBH, CBS, NBC, FOX, CW, ... , plus a few movie networks).   I haven't figured out what the movie networks are yet.

---

### Post by smit0737 on 2007-03-21
Thanks!  I ran the script, got the firmware, copied it to /lib/firmware and modprobed saa7134.  I also added saa7134, saa7134-dvb and saa7134-alsa to my /etc/modules file so they'll come back.  I'm not sure how to test this out to understand if it works, but when I dmesg | tail I see that the modprobe command worked.

I'm trying to set this all up in mythtv-setup now, and I'm stuck on setting up the capture card.  Does this card show up as /dev/video0 or /dev/dvb/adapter0/?  In the adapter0 directory, I see 4 entires (dvr0, net0, frontend0, demux0).  This [page]("http://www.mythtv.org/wiki/index.php/AVerTV_HD_A180") from the mythtv wiki seems to indicate referencing the card as /dev/adapter0, but mythtv-setup doesn't seem to recognize that.

Any help would be appreciated!  Thanks.

---

### Post by modorf on 2007-03-23
> **smit0737 said:**
> Thanks!  I ran the script, got the firmware, copied it to /lib/firmware and modprobed saa7134.  I also added saa7134, saa7134-dvb and saa7134-alsa to my /etc/modules file so they'll come back.  I'm not sure how to test this out to understand if it works, but when I dmesg | tail I see that the modprobe command worked.

I'm trying to set this all up in mythtv-setup now, and I'm stuck on setting up the capture card.  Does this card show up as /dev/video0 or /dev/dvb/adapter0/?  In the adapter0 directory, I see 4 entires (dvr0, net0, frontend0, demux0).  This [page]("http://www.mythtv.org/wiki/index.php/AVerTV_HD_A180") from the mythtv wiki seems to indicate referencing the card as /dev/adapter0, but mythtv-setup doesn't seem to recognize that.

Any help would be appreciated!  Thanks.



/dev/dvb/adapter0 will be created for the DVB - ATSC / QAM input - HD
/dev/video0 will be created for the NTSC input - SD

in Myth you will setup two cards, one for V4L - sd signal and the other DVB for HD signal

---

### Post by newlinux on 2007-03-26
> **Tdonohue said:**
> I cannot get this card to work.  Every guide that does get it to work shows installing some DVB firmware.  Unless I'm mistaken, this isn't going to help me in the US.  Has anyone gotton this card to work with ATSC?  Mythtv shows it as kworld atsc-110, but I can't use it to watch tv.  It will only pull signal from the other kworld analog tuner (seperate card, not the bottom input).  I can't get a signal through any of the inputs on this card.

Obviously people have more than one tuner in their system, but for some reason I can't get it to work.  There are no guides to help me with this problem, so I am clearly the only person struggling with this.

I can't verify that the card even works.  cat /dev/video1 ....  returns error.  Trying to play it in mplayer returns an error.  TVtime only gives me the signal from the other tuner card.  How do I tell it to use a different card?

Should I install this DVB firmware to get NTSC or ATSC reception in the US?  Seems all wrong to me!

In order to get the other card to work (single analog kworld tuner), I had to add "saa7134" to the bottom of some module (don't know the details as I'm at work, but it was mentioned in several other threads).  Do I need to do something for this card?

After getting wireless internet with WPA working, Mysql and Mythtv working, and all the other quirks that come with configuring a linux pc for daily use, this problem I'm having seems trivial but I just can't figure it out. 

Can somebody please help me.  I'll be forever grateful!


Just as a point of clarification (this confused me to) my understanding is that the DVB drivers used for reception of digital TV in linux and the DVB standards use for transmission of digital tv  (DVB-S, DVB-T, etc.) are two different, yet related and confusing things. But as already gone through in detail in this thread, you do use DVB drivers for ATSC and QAM.

---

### Post by Vincent_Lin on 2007-03-27
Dear all,

Sorry I did not pay much attention of this thread until last night.  mordof and newlinux made it clear that QAM is using firmware to tune, and stupid me for forgetting seeing DVB/QAM specifically printed on screen when I selected V4L DVB driver to setup my ATSC-110 to receive ATSC signals.  I have been scratching my head for a couple months wondering why QAM is not working and where I can find the place to set QAM for tuning, after having put ATSC-110 to work for receivng OTA HD for that long time.

So, I tried last night.  It works.  I use zap2it to retrieve channel information (BTW, Comcast at Wayland, MA 01778, but zap2it says Needham Comcast) and some channels start to tune in.  yay!!  Since I use zap2it information, I did not successfully utilize QAM256 and us-cable-hrc setting for scanning channel informaiton.  Actually I did try to use QAM256 and us-cable-hrc, along with all the combinations (QAM256, QAM128, QAM64, vs. us-cable, us-cable-hrc, us-cable-irc, us-cable-high, us-cable-high-hrc, us-cable-high-irc, and DEFAULT), but none of those scanning combination actually found a lock of any frequencies.  I even imported the downloaded channels.conf for Boston Comcast listed at mythtv wiki, still, but not success.  I guess locality for Comcast is very different.

Still have another question, it seems to me that the only channels got tuned are practically local HD stations.  I have WGBH (2_2), CBS, ABC, FOX, CW tuned with HD signals, even I did not subscribe to HD channels from Comcast.  I know that to subscribe to HD contents actually means to "lease" an HD setup box from Comcast.  Either way, the HD signals are there waiting for you to  "decode" using Comcast boxes.  But, I could not tune to any other SD channels, that are available through even a regular TV set. 

In other words, I can't get those so called "clear" channels but HD channels.  Can someone help me out here?

I don't have saa7134-alsa loaded, neither tuner.  saa7134 and saa7134-dvb give me ATSC capability while the datastream, mpeg2 practically, gives me HD video and audio, that my mythtv, mplayer,and vlc altogether work beautifully.

I did this all through mythtv-setup 0.20, under Edgy with NVidia driver, if that matters.

Thanks to all.

Vincent

---

### Post by newlinux on 2007-03-27
Your post confuses me a little bit. So are you using ATSC for OTA or QAM for digital cable tuning? I think your are using QAM based on your mention of the comcast. And you are right, where those stations are, and even what you can get are highly location dependent.

If using QAM, it is quite possible that all you can get are the local HD stations. Those are the only stations cable companies are required to send unencrypted digitally. In my area via QAM I get the local HDs, digital versions of the locals in SD, and a couple other stations. But when I first started I used to get ESPNHD and some others via QAM, and slowly some of them went away. But I believe there is a "must carry" rule that local stations can use to force cable companies to carry the HD stations free and clear. They don't have to decrypt any other stations digitally. They just send them analog (NTSC). On the flipside, having a QAM tuner also means you don't need a box or cable card to get HD locals from comcast. Also keep in mind they can change the location of these channels at any time (happened 2 times in the last 6 months where I live) and this is easiest to fix be rescanning, so I hope you get your scanning to work. You may find other channels if you do. It's weird that you can tune stations that you can't scan. What happened when you tried those scanning methods? You just got no locks? Seems like something is wrong then... Can you scan any channels using dvb-apps?

Also, are you scanning while mythtv backend is running? If so you should stop the backend first...

---

### Post by Vincent_Lin on 2007-03-27
newlinux,

1. The answer to the confusion part is obvious - I have two Kworld ATSC-110 cards.  So the first one I use it for OTA ATSC, which has been working for over a couple of months.  I did not notice , as I mentioned in last post,  that I have to use DVB interface to tune into Comcast cable channels.  I used to have a Samsung ATSC tuner but it only works in winter, when leaves are all gone and are not blocking OTA signals.  As spring is coming, I am king of eager to get tuning to Comcast, since my OTA could vanish again.  Or, I have to pay an electrician $$$ to install a rooftop antenna.

2. Before you reply, I was reading this [http://www.gossamer-threads.com/lists/mythtv/users/234611](http://www.gossamer-threads.com/lists/mythtv/users/234611) , which describes exactly what happened to my zap2it channels.  HD channels have LAMGV lock, and I can see them great.  Other channels are LAM lock, with a black screen.  The thread indicates that it is caused by a fake decryption flag on those channels sent out by Comcast, which these channels themselves are likely not encrypted.  Of course some channels do not tune at all.  But this information gives me some relief as I can wait for next mythtv release assuming that that SVN patch is going to rolled into production.

3. As I mentioned, I tried QAM256, QAM128, QAM64 vs. Default, us-cable, us-cable-high, us-cable-hrc, us-cable-irc, us-cable-high-hrc, us-cable-high-irc, (totally 3x7=21 combinations), but none of these scans give me a single lock.  Plus the import of channels.conf from wiki.mythtv.org for Boston Comcast.  It is a long long long time of playing with it last night.  Maybe there are other flags I should pay attention to, such as EIT scan or something like that?
Or I should try it again after I kill mythtv-backend.  Ummm, I did not kill it before I did all the scans.  What a waste of time :)

Thanks a lot for helping me out this much,

Vincent

---

### Post by newlinux on 2007-03-27
That thread is interesting. Maybe I get more channels than I think. I have a QAM tuner on my TV which I don't use (I have a cable card). I'm going to see what channels it can get and compare...

Have you tried using dvb-apps/VLC at all and scanning and viewing outside of mythtv?

Sorry I couldn't be of more help... I've spent many a night on things with mythtv too. Now that it's working the way I want - I'm scared to touch it :)

---

### Post by Vincent_Lin on 2007-03-28
newlinux,

So I /etc/init.d/mythtv-backend stop and then run mythtv-setup to scan Comcast channels with QAM and us-cable-hrc, and it works!  Thanks for that tip!

I get many locks that I did not even go over them.  Still, as expected, local HD channels have LAMGV lock and viewable, and other channels have LAM lock without pictures.  I did not try vlc for these channels because I don't understand the cl syntax of vlc to get dvb tuning.

I will be waiting for new release of mythtv, hopefully with "that" fix rolled in.

By the way, I don't like mythmusic too much.  I feel that I don't have a total control of mp3 playing.  Do you know of any media player, or something such that I can plug into mythtv for playing mp3, aac, and music CDs?  Obviously I am dreaming about iTunes inteface integrated as part of mythtv music playing.

Vincent

---

### Post by Vincent_Lin on 2007-03-29
newlinux,

I spent too much time last night playing with this QAM thingy.  Here is the list I have got, all using QMA256 and us-cable-hrc scanning on Comcast digital cable subscription:

1. All local HD channels - not a surprise as you've mentioned.  Also mentioned in FAQ from  mythtv.org.
2. All other sensible channel numbers scattered in <100's and 200's<>300's have LAM lock, but black screens.
3. 100's, 300's, 400's, 500's, 600's, 700's - some have LAM locks without screen, others could not be tuned at all.
4. 800's (HD channels) have LAMGV locks, but still no screens.  So ESPNHD is not available to me, not like someone else said.
5. This is the fun part.  KWorld ATSC-110 also tuned into some other channels such as UNKNOWN 110#0, UNKNOWN80#0, etc..  They are local SD channels and other analog clear channels, as a regular TV can easily tune into.
6. UNKNOWN91#1 comes and goes.  I heard someone said it is a "shared" PPV/ONDEMAND from neighbors signals, judged by the fact that the contents are sometime DiscoveryHD, and sometimes it's "exotic" stuff, with FF and REW from time to time(I did not do it).
7. I was disappointed by the fact that channels at 200's are not viewable, since these kids channels are the reason why I had cable subscription in the first place.

So, that's it.  Happily waitng OTA signals to go away when trees with full-grown leaves start to block them all.

Vincent

---

### Post by newlinux on 2007-03-29
Those sound about like the same QAM channels i get (including the PPV/ONDEMAND from the neighbors - scans here and there and I get these on different channels, probably depends on on what node in the neighborhood is watching what). Some people are really not happy that all the stations you can get with analog cable are not available with digital. I know later versions of myth (from SVN) allow the Kworld to be used as a tuner for both NTSC and ATSC/QAM at the same time (like can be done with pchdtv5500 now) without reconfiguring (but you can't tune an ATSC/QAM and NTSC station at the same time using one card)  which would allow for getting all the basic stations in addition to the QAM ones. I wish cable companies would at least decrypt any digital versions of their basic cable channels, but I guess there is no incentive too...

Mythmusic is too laborious to use. It doesn't even natively support .m3u playlists. That needs real improvement (I have about 80GB of mp3s). I just use amarok outside of myth...

---

### Post by biker19 on 2007-04-01
Does anyone know if all the above applies to the 115 ATSC card? From a casual look it seems like the 115 card is the same as the 110 but they added the remote and the TotalMedia interface (which is supposed to make use of the QAM tuner in Windows - it didn't work for me). I got no reply form tech support at Kworld when I asked this question.

dmesg gives:

[   31.806011] Uniform CD-ROM driver Revision: 3.20
[   31.895748] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   31.895757] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.895765] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.895773] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.895780] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.895787] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.895795] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.895802] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.896136] saa7133[0]: registered device video0 [v4l2]
[   31.896255] saa7133[0]: registered device vbi0
[   32.089943] saa7134 ALSA driver for DMA sound loaded
[   32.089970] saa7133[0]/alsa: saa7133[0] at 0xfdcff000 irq 20 registered as card -2
[   32.254597] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 22

I got Myth to come up in Feisty but no tuner available - I assume cause it's not configured right. I can't find the tuner config page in Myth. Ubuntu newbie looking for a little help.

---

### Post by biker19 on 2007-04-01
Oops, forgot a few lines of the dmesg:

[   31.725361] saa7130/34: v4l2 driver version 0.2.14 loaded
[   31.725423] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[   31.725433] saa7133[0]: found at 0000:02:00.0, rev: 209, irq: 20, latency: 64, mmio: 0xfdcff000
[   31.725440] saa7133[0]: subsystem: 17de:7352, board: UNKNOWN/GENERIC [card=0,autodetected]
[   31.725449] saa7133[0]: board init: gpio is 100
[

---

### Post by biker19 on 2007-04-01
Just noticed in the CARDLIT.saa7134 file that the ATSC110 tuner (tuner # 90) is listed as [17de:7350] while my ATSC115 is [17de:7352].  So does this mean I'm SOL? Or can I force my system to use the configurations of the 110 card and hope for the best? How do I do that?

---

### Post by biker19 on 2007-04-01
So I changed the tuner by adding file saa7134 in /etc/modprobe.d with the following

 options saa7134 card=90

now my dmesg says:

[   31.921080] saa7130/34: v4l2 driver version 0.2.14 loaded
[   31.921366] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[   31.921376] saa7133[0]: found at 0000:02:00.0, rev: 209, irq: 20, latency: 64, mmio: 0xfdcff000
[   31.921384] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110 [card=90,insmod option]
[   31.921394] saa7133[0]: board init: gpio is 100
[   32.054366] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   32.054375] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.054382] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.054389] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.054396] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.054402] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.054409] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.054415] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.190234] tuner 1-0061: chip found @ 0xc2 (saa7133[0])
[   32.190269] tuner 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   32.190273] tuner 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   32.203416] saa7133[0]: registered device video0 [v4l2]
[   32.203526] saa7133[0]: registered device vbi0
[   32.216833] saa7134 ALSA driver for DMA sound loaded
[   32.216861] saa7133[0]/alsa: saa7133[0] at 0xfdcff000 irq 20 registered as card -2
[   32.237295] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 22
[   32.377409] fuse init (API version 7.8)
[   32.402511] lp0: using parport0 (interrupt-driven).
[   32.517741] nxt200x: NXT2004 Detected
[   32.517767] DVB: registering new adapter (saa7133[0]).
[   32.517771] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...

but now I don't know how to make use of this new setup in Myth.

---

### Post by newlinux on 2007-04-01
I hope this isn't too basic, but is it that you don't know how to set up dvb tuners in myth? Or that you do and can't find the tuner when using mythtv-setup?

I need to know a couple of things before I can be of (hopefully) some help. I'm not using Feisty, so somethins might be different...

How many tuner cards do you have installed?
Do you have a /dev/video or /dev/video0 or something similar?

If it that you aren't sure how to set the card up (again, pardon me if this is too basic):
Basically, what you would normally do is stop the backend.

```
sudo /etc/init.d/mythtv-backend stop
```

 then run

```
mythtv-setup
```

Then add the capture card as a DVB card (it would read something like nxt2004 device or something in the setup screen when you select the card), then setup up a video source, then assign that video source to the card's tuner input (via input connections menu) and scan for QAM channels.

You will find some channels (which may need mapping, but you can do this later). Then exit mythtv-setup, restart the backend, 
```
sudo /etc/init.d/mythtv-backend start
```

and try to view the channels.

---

### Post by biker19 on 2007-04-05
Oops, I didn't stop the backend when trying to setup myth.

This is to setup my Kworld 115 ATSC card. Ubuntu didn't recognize it, but then I manually set it to work like the 110 card. I then reran myth setup, but didn't stop the back end.

I got a bit confused inside the setup and I think didn't setup the source - I'll try it again later - thanks.

---

### Post by biker19 on 2007-04-05
For some reason my setup boots right into Myth and I can't get out to Ubuntu to make any changes. When I say "Yes, exit Myth" I get a black screen and nothing. Help!
#-o:confused: ](*,)

---

### Post by biker19 on 2007-04-05
This tuner/MythTv setup is certainly not for the faint of heart.

Just when I thought I was home free I get stuck again. I reinstalled everything from scratch and this time the card install worked like it's supposed to - I think. I added a file to /etc/modprobe.d to have the system use tuner=90, the ATSC 110 tuner. I loaded the nxt2004 firmware to /lib/firmware. I went through the mythtv setup to set the tuner, source and scanned chs with the ATSC tuner - it picked up some chs my TV didn't. I ran mythfill. It seemed like everything went off without a hitch. Then I start the frontend and got the following in the terminal window:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-05 22:37:44.118 Using runtime prefix = /usr
2007-04-05 22:37:44.126 Gnome-Screensaver support enabled
2007-04-05 22:37:44.126 DPMS is active.
2007-04-05 22:37:44.136 New DB connection, total: 1
2007-04-05 22:37:44.141 Connected to database 'mythconverg' at host: localhost
2007-04-05 22:37:44.151 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-05 22:37:44.153 Using screen 0, 1024x768 at 0,0
2007-04-05 22:37:44.159 Current Schema Version: 1160
2007-04-05 22:37:44.159 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-05 22:37:44.159 Enabled verbose msgs:  important general
2007-04-05 22:37:44.581 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-05 22:37:44.582 Using screen 0, 1024x768 at 0,0
2007-04-05 22:37:44.582 Switching to square mode (G.A.N.T.)
2007-04-05 22:37:44.591 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-04-05 22:37:45.349 Joystick disabled.
2007-04-05 22:37:46.459 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-04-05 22:37:46.580 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-05 22:37:46.622 Registering Internal as a media playback plugin.

Inside the frontend I keep getting errors that it can't connect to the backend when know it is running. And when I try to start the backend in terminal I get the following:

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

BTW the relevant dmesg is as follows:

[   31.192474] saa7133[0]: found at 0000:02:00.0, rev: 209, irq: 20, latency: 64, mmio: 0xfdcff000
[   31.192482] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110 [card=90,insmod option]
[   31.411343] tuner 1-0061: chip found @ 0xc2 (saa7133[0])
[   31.411379] tuner 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   31.411383] tuner 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   31.417577] saa7133[0]: registered device video0 [v4l2]
[   31.417604] saa7133[0]: registered device vbi0
[   31.505419] saa7134 ALSA driver for DMA sound loaded
[   31.505445] saa7133[0]/alsa: saa7133[0] at 0xfdcff000 irq 20 registered as card -2
[ 3110.432000] nxt200x: NXT2004 Detected
[ 3110.432000] DVB: registering new adapter (saa7133[0]).
[ 3110.432000] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[ 4044.176000] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[ 4044.192000] nxt2004: Waiting for firmware upload(2)...
[ 4045.740000] nxt2004: Firmware upload complete
[ 4540.372000] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -5)
[ 4540.372000] nxt200x: error writing to tuner

After that there are a bunch of error lines like the last line.

I know I'm really close - how about some help for a newbie.:confused:

---

### Post by newlinux on 2007-04-05
Believe it or not, those frontend messages and errors are normal. I get those every time I start a frontend.


also have you looked at your backend log? That might have some clues...
```

cat /var/log/mythtv/mythbackend.log
```

what message do you get when you type:```

ps -p `cat /var/run/mythtv/mythbackend.pid`
``` 

and if it is running, try restarting it.
```
sudo /etc/init.d/mythtv-backend restart
```

Let's just verify it was running.

---

### Post by newlinux on 2007-04-05
based on your dmesg output it looks like there is some error with the card... however...

what does 
```

lspci 

```
return...

---

### Post by biker19 on 2007-04-07
Here are the results:

> **newlinux said:**
> 
also have you looked at your backend log? That might have some clues...
```

cat /var/log/mythtv/mythbackend.log
```

2007-04-07 13:07:05.825 Using runtime prefix = /usr
2007-04-07 13:07:06.216 New DB connection, total: 1
2007-04-07 13:07:06.273 Connected to database 'mythconverg' at host: localhost
2007-04-07 13:07:06.457 Current Schema Version: 1160
Starting up as the master server.
2007-04-07 13:07:06.779 New DB connection, total: 2
2007-04-07 13:07:06.810 Connected to database 'mythconverg' at host: localhost
2007-04-07 13:07:06.928 EITHelper: localtime offset -4:00:00 
2007-04-07 13:07:07.042 DVBChan(0) Error: Opening DVB frontend device failed.
                        eno: No such file or directory (2)
2007-04-07 13:07:07.063 EITHelper: localtime offset -4:00:00 
2007-04-07 13:07:07.155 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2007-04-07 13:07:07.183 ChannelBase(2) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-04-07 13:07:07.189 Main::Starting HttpServer
2007-04-07 13:07:07.252 Main::Registering HttpStatus Extension
2007-04-07 13:07:07.334 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-07 13:07:07.339 Enabled verbose msgs:  important general
2007-04-07 13:07:07.351 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2007-04-07 13:07:07.355 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min

what message do you get when you type:```

ps -p `cat /var/run/mythtv/mythbackend.pid`
``` 

 PID TTY          TIME CMD
 5090 ?        00:00:00 mythbackend


and if it is running, try restarting it.
```
sudo /etc/init.d/mythtv-backend restart
```

Restarting MythTV server: mythbackend.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed



Let's just verify it was running.

---

### Post by biker19 on 2007-04-07
> **newlinux said:**
> based on your dmesg output it looks like there is some error with the card... however...

what does 
```

lspci 

```
return...

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 04)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by biker19 on 2007-04-07
Other than run:

sudo modprobe saa7134-dvb  - I forgot to put that in the /etc/modules file

I don't think I ran anything else and now I can watch live TV on the front end via the ATSC tuner.

Now for the tricky part - the get the QAM tuner working. I know that's on the lower RF input of the card - which tuner do I use in the setup?

---

### Post by biker19 on 2007-04-07
During the running of the mythfilldatabase I get the following errors:

Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.

and the program guide is empty. What's wrong?

---

### Post by newlinux on 2007-04-07
glad you got it working. It could be that you supplied the wrong username/password. Double check. Thanks to you I can now tell others the Kworld 115 will work as well...

---

### Post by newlinux on 2007-04-07
You use the all the same settings for QAM in setup except when scanning you tell it to scan QAM instead of ATSC (8vsb). Fair warning. They are both DVB. You won't be able to do QAM and ATSC at the same time because they both use the digital tuner. On my Kworld, the QAM input is the same as the ATSC input. The NTSC input is the one thats different. Also, I've noticed that when I've rebooted sometimes which one is which changes... I think they both run through the same circuitry and one input gets bound to digital and the other analog at boot or driver load time. So if you get nothing when you scan just try switching the rf input (easy to do with the kind of inputs they have on these)...

---

### Post by biker19 on 2007-04-07
According to Kworld the QAM tuner is on the bottom and the ATSC tuner (the one I'm using now) - along with the NTSC tuner - is on top.

I really have to read the MythTV guide - I never setup a DirectData account at Zap2It to get the program guide data. The only problem I see now is that there's no data for the analog channels. :confused: 

The hardware I'm using is at the lower end to handle HD chs and encoding in software via the CPU of the analog chs. I'll have to wait till I build a more powerful PC to really make the setup useful.

Now for the ultimate - making the remote work - reading through the lirc documentation makes this a really tough task.

---

### Post by newlinux on 2007-04-07
Yeah, I know what the Kworld manual said, but I bet the windows and linux drivers behave a little differently. I can only speak from my experience, and it happen with all 3 of my Kworlds that sometimes it would change. Just something to look for if you have problems. I think it may vary a bit, looking at [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) there two different experiences as to which input is what from two different owners... Maybe for the 115 there is more consistency.

It seems very weird that there is no data for analog stations in your area. I use four different zap2it accounts to get my listings-one for analog, one for QAM, one for ATSC, and one for my firewire connection, because they all have a different set of stations. Doesn't your arae have listings for digital equivalents of your analog stations? You could just use those zap2it listings and delete the channels you don't get via analog.

What kind remote do you have? the Ubuntu LIRC guide actually went pretty well for me. Good luck!

---

### Post by biker19 on 2007-04-07
You were right - scanning for QAM on the lower RF input yielded nothing - I got about 20 chs on upper input. Since that's the only input I can use (if I remember the analog would only work on the upper RF input also) the availability of program guide data on analog chs at this point is rather moot - I'll probably only watch the QAM chs.

Now I wonder what if anything is available via the lower RF input. You are probably right that in Windows, those drivers make the card behave differently - I had it running in the TotalMedia app that ships with the card and got analog chs on the lower RF input. Kworld told me to use the lower input for QAM chs in Windows but I could never get QAM to work - hence my trial with Ubuntu and MythTV. I basically watch the same thing whether via OTA (analog or digital) or QAM - so I'm not really missing anything. The only downside is that if I could get the analog tuner working I could maybe have a 2 tuner solution in 1 card.

The remote is the one provided by Kworld - it ships with the card in the 115 packaging. The remote pickup plugs into the card. Does the 110 card even have a jack on the card for a remote and does it come with one? Which guide did you use to setup the remote? I see a listing at LIRC for Kworld but that is for card=78, not 90 like this card. Would that setup work?

---

### Post by newlinux on 2007-04-07
You might want to double check the analog port. for me on port always does ATSC/QAM and the other one does NTSC. Yeah, the one card I bought new did come with a remote, and it plugged into the jack on the card. I really think these are the same tuners, just different software :). I never used it in linux because i use my Harmony remote to control everything, so I bought an USB IR receiver and used that to work with LIRC. I never checked to see if LIRC could use the IR receiver that plugs into the card. If you get that working, you should update the wiki page :).

---

### Post by biker19 on 2007-04-07
For some reason 2 QAM chs won't lock - kinda weird on a cable setup - I had that issue with OTA ATSC (multipath and trees swaying) but should not be so with QAM (it certainly locks with the TV tuner on the same chs). Is there anything to do in such a case?

You were right again - I was able to setup the NTSC tuner (with program guide this time) on the lower RF input - but not much use with current hardware - it's not powerful enough to encode the analog ch in software with this CPU.

I'll try the remote setup later.

---

### Post by newlinux on 2007-04-08
Did the QAM scan pick up these channels? do you get a partial lock? I had two stations my TV picked up that my card didn't. Turned out these two channels were QAM 64, not 256, so when I scanned QAM64 I was able to get them.

Other than that I don't have too many ideas on the QAM issue, only to say that this is not unique. different stations do have different strengths, and some tuners are more sensative than others... You could look into a signal amp if you really  need it (that might do it if you are splitting you cable lines a bit. I have one and it did make a difference to both my cable box and QAM tuner).

What processor are you using? Even a PIII 800 should be able to encode analog... (if you computer isn't doing much else) You may not to play with your recording profiles and playback settings. Have you tried just recording analog and then playing back an analog recording (i.e. not viewing it "live" or encoding and decoding at the same time)

---

### Post by biker19 on 2007-04-09
I assumed that if during the scan the tuner picked it up it should lock - I assumed they're all QAM256 . My setup uses an AMD64 Athlon 3000 on an MSI MB with built in video (Radeon Express 200 chip). I'm not really worried about analog anymore - after seeing the clarity and steady signal of QAM there's no going back. The problem I see with analog is that Myth always encodes it, cause it's not live but always streaming through the HDD?.

I did a parallel setup on the same PC (different HDD) with Vista and all chs scanned and tuned just fine. And unlike in Linux, in Vista the bottom RF input is QAM and the top is ATSC so I could potential have two digital tuners in one card. There's no analog issue with the Vista setup since the app there doesn't encode the video stream - it just displays it (or records).

Kinda weird how on the same card Linux and Vista use different RF inputs for different functions.

---

### Post by newlinux on 2007-04-09
> **biker19 said:**
> I assumed that if during the scan the tuner picked it up it should lock - I assumed they're all QAM256 . My setup uses an AMD64 Athlon 3000 on an MSI MB with built in video (Radeon Express 200 chip). I'm not really worried about analog anymore - after seeing the clarity and steady signal of QAM there's no going back. The problem I see with analog is that Myth always encodes it, cause it's not live but always streaming through the HDD?.



Okay, yeah, if it came up on the scan for QAM256 it is a QAM256 stations. Something else is probably the issue. You're right, it always records it before displaying it, but that has nothing to do with whether it is encoded or not...

> 

I did a parallel setup on the same PC (different HDD) with Vista and all chs scanned and tuned just fine. And unlike in Linux, in Vista the bottom RF input is QAM and the top is ATSC so I could potential have two digital tuners in one card. There's no analog issue with the Vista setup since the app there doesn't encode the video stream - it just displays it (or records).




Vista still encodes analog signals. It just doesn't write it to disk first if it is not recording it. Encoding is the process of converting the signal from analog to digital, which must be done. The main speed difference between windows and linux with respect to video is that windows can take better advantage of the video card. The video card assists the processor greatly. Currently in Linux, this can only be helped using nvidia cards and you have to use the nvidia drivers to get this, not the generic drivers that are currently the defualt in Ubuntu install. For Myth (and linux in general) you are MUCH better off with Nvidia cards instead of ATI.

> 
Kinda weird how on the same card Linux and Vista use different RF inputs for different functions.

Yeah, this is why I said I think the circuitry for both inputs is the same. It's the drivers that determine one can do what. For my current uses, I prefer to have the NTSC input separate from the QAM input. However, what I'd really like is the ability for both inputs to do all. There doesn't seem to be a hardware issue with this, just a driver issue...

---

### Post by RipNLa on 2007-04-12
Excellent thread you guys have here.

I just got the 115 card last night and have had 0 luck getting it to pickup QAM channels in Windows XP.  Matter of fact, Ive only been getting 2 channels picked up on analog and thats it.  Thinking about installing linux for the first time ever just to see this work =p

Totally confused about which RF port is "top" and which is "bottom"

biker: in Vista, what software did you use to view the QAM? TotalMedia?

---

### Post by biker19 on 2007-04-13
> **RipNLa said:**
> Excellent thread you guys have here.

I just got the 115 card last night and have had 0 luck getting it to pickup QAM channels in Windows XP.  Matter of fact, Ive only been getting 2 channels picked up on analog and thats it.  Thinking about installing linux for the first time ever just to see this work =p

Totally confused about which RF port is "top" and which is "bottom"

biker: in Vista, what software did you use to view the QAM? TotalMedia?

Yeah, I finally got TotalMedia to find the QAM chs using the lower RF input - but it had issues.

In Ubuntu the QAM chs are on the upper RF input. Took some time to get it working in MythTV mainly because the card is not recognized by default - most of the things needed are outlined in this thread.

---

### Post by modorf on 2007-04-25
some updates with my Kworld Atsc-110 experience Ubuntu fiesty, and mythtv

I'm able to capture with both the V4L standard def interface on analog cable and the DVB interface digital cable interface.  My system sees them as two different devices and need to be activated in Myth as such.  In the build with Ubuntu Fiesty, Myth doesn't give an option to link the dvb and v4l devs together, this has been modified in later svn builds.  I was able to change a record for the capture card in the database to tell myth they are linked together as 1 card.

Database: mythconverg  -   Table: capturecard  -  Field: parentid
The value for this field should be changed from 0 -> the card id of the dvb port

since I only have 1 tuner card : KWorld ATSC-110 
Here is my capturecard table (trimmed some of the info out)
cardid 	videodevice 	audiodevice 	vbidevice 	cardtype 	defaultinput 	parentid 
1 	0 	  	  	DVB 	DVBInput 	0
2 	/dev/video0 	/dev/dsp1 	/dev/vbi0 	V4L 	Television 	1

notice that cardid 2 has parentid 1  or that card2 is a child of 1.

Then in Mythtv-Setup: Input Connection card options will be
[DVB:0] -> (none)
 -> [/dev/video0: Television] -> (none)
 -> [/dev/video0: Composite]
 -> [/dev/video0: S-Video]

then add the listings.  This will help resolve recording conflicts between analog and dvb tuner.

I'm still have an issue with switching from DVB -> Analog and the channel not tuning without switching to another analog station and then back.  Almost as if the dvb dev isn't releasing the tuner.

---

### Post by mekong on 2007-04-25
> **newlinux said:**
> You use the all the same settings for QAM in setup except when scanning you tell it to scan QAM instead of ATSC (8vsb). Fair warning. They are both DVB. You won't be able to do QAM and ATSC at the same time because they both use the digital tuner. On my Kworld, the QAM input is the same as the ATSC input. The NTSC input is the one thats different. Also, I've noticed that when I've rebooted sometimes which one is which changes... I think they both run through the same circuitry and one input gets bound to digital and the other analog at boot or driver load time. So if you get nothing when you scan just try switching the rf input (easy to do with the kind of inputs they have on these)...

I had a fully-functioning MythTV combined frontend/backend that utilized the ATSC-110 card under Edgy.  I used the bottom (closest to the motherboard) coaxial input for QAM-256 input to receive unencrypted local HDTV stations (ABC, NBC, CBS, FOX, PBS) from Comcast.  But, yesterday I decided I needed a thrill so I elected to upgrade to Feisty.  

After upgrade I had a few issues (Nvidia drivers, rebuild LIRC kernel modules) but everything seemed to working fine except the MythTV tuner.  I could no longer achive signal lock for the few stations I had in my "channel" table within mythconverg.  

After reading several posts and updating my /etc/modules multiple times to include or remove various saa7134 modules I came across the quote above from *newlinux* regarding the switch of the QAM and analog inputs on the card.  So, on a whim, I decided to move the incoming cable to the upper port and do an "Existing Transport Scan" within the Channel Scanner function of mythtv-setup (I knew which transports carried signals by obtaining the *mplexid* from the "channel" table and using that as an index to the "dtv-multiplex" table to obtain the transport *frequency*).  And, lo and behold, the QAM input has _moved_ to the upper input! :shock: 

I never experienced this before when running under Edgy after dozens of reboots, so I'm hoping it has just decided to switch inputs with the upgrade to Feisty, and will not move around on a regular basis. [-o<

---

### Post by newlinux on 2007-04-25
> **modorf said:**
> some updates with my Kworld Atsc-110 experience Ubuntu fiesty, and mythtv

I'm able to capture with both the V4L standard def interface on analog cable and the DVB interface digital cable interface.  My system sees them as two different devices and need to be activated in Myth as such.  In the build with Ubuntu Fiesty, Myth doesn't give an option to link the dvb and v4l devs together, this has been modified in later svn builds.  I was able to change a record for the capture card in the database to tell myth they are linked together as 1 card.

Database: mythconverg  -   Table: capturecard  -  Field: parentid
The value for this field should be changed from 0 -> the card id of the dvb port

since I only have 1 tuner card : KWorld ATSC-110 
Here is my capturecard table (trimmed some of the info out)
cardid 	videodevice 	audiodevice 	vbidevice 	cardtype 	defaultinput 	parentid 
1 	0 	  	  	DVB 	DVBInput 	0
2 	/dev/video0 	/dev/dsp1 	/dev/vbi0 	V4L 	Television 	1

notice that cardid 2 has parentid 1  or that card2 is a child of 1.

Then in Mythtv-Setup: Input Connection card options will be
[DVB:0] -> (none)
 -> [/dev/video0: Television] -> (none)
 -> [/dev/video0: Composite]
 -> [/dev/video0: S-Video]

then add the listings.  This will help resolve recording conflicts between analog and dvb tuner.

I'm still have an issue with switching from DVB -> Analog and the channel not tuning without switching to another analog station and then back.  Almost as if the dvb dev isn't releasing the tuner.


Thanks for this info. I new the ability was in SVN, but I wanted to use the repos... now I can do it, although that analog switching issue causes me a bit of concern. Let us know if you get that fixed and how you did it.

---

### Post by newlinux on 2007-04-25
> **mekong said:**
> I had a fully-functioning MythTV combined frontend/backend that utilized the ATSC-110 card under Edgy.  I used the bottom (closest to the motherboard) coaxial input for QAM-256 input to receive unencrypted local HDTV stations (ABC, NBC, CBS, FOX, PBS) from Comcast.  But, yesterday I decided I needed a thrill so I elected to upgrade to Feisty.  

After upgrade I had a few issues (Nvidia drivers, rebuild LIRC kernel modules) but everything seemed to working fine except the MythTV tuner.  I could no longer achive signal lock for the few stations I had in my "channel" table within mythconverg.  

After reading several posts and updating my /etc/modules multiple times to include or remove various saa7134 modules I came across the quote above from *newlinux* regarding the switch of the QAM and analog inputs on the card.  So, on a whim, I decided to move the incoming cable to the upper port and do an "Existing Transport Scan" within the Channel Scanner function of mythtv-setup (I knew which transports carried signals by obtaining the *mplexid* from the "channel" table and using that as an index to the "dtv-multiplex" table to obtain the transport *frequency*).  And, lo and behold, the QAM input has _moved_ to the upper input! :shock: 

I never experienced this before when running under Edgy after dozens of reboots, so I'm hoping it has just decided to switch inputs with the upgrade to Feisty, and will not move around on a regular basis. [-o<

I have this issue under edgy, but it was quite random. Fortunately it's been over 2 months since I've had to reboot. But when I was configuring and having problems and rebooting multiple times this was always something I checked when things didn't work. But it only happened on reboots, and it happened at least once with all 3 of my ATSC 110s

I'm glad this tidbit helped someone! Wish I knew. I thought I was losing my mind at first...

---

### Post by lwtbenben on 2007-05-20
> **heywire said:**
> I use this card under ubuntu using the dvb firmware.  I am tuning QAM 256 channels from Time Warner (I'm in Ohio).

This guide works for me:

[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)

Let me know if you need any help setting this up.  This card seems to work better under linux than windows!

Hi, I am using the ATSC-110 card to tune tv signal but no luck.
Ubuntu can recognize the card and I just can not see and tv using tvtime or xine or mythtv
Could u give some advice ?By the way ,which tv player do you use watching ntsc and which one do you using watching atsc?
Thank you .

---

### Post by newlinux on 2007-05-20
Let us know your scan and card settings and what you are trying to scan for. What happens when you try to scan? You said no luck, but that doesn't tell us much of what is going on. Error messages, scan results, mythbackend log info would all be useful. Did you read through all of this thread and try all of the things in it (loading the proper firmware and modules, switching the rf input when scanning, making mythbackend has stopped).

---

### Post by bliffle on 2007-09-27
> **biker19 said:**
> You were right - scanning for QAM on the lower RF input yielded nothing - I got about 20 chs on upper input. Since that's the only input I can use (if I remember the analog would only work on the upper RF input also) the availability of program guide data on analog chs at this point is rather moot - I'll probably only watch the QAM chs.

Now I wonder what if anything is available via the lower RF input. You are probably right that in Windows, those drivers make the card behave differently - I had it running in the TotalMedia app that ships with the card ...?

TotalMedia 3? Was that under windows or linux? I'd like to get it running under ubuntu using wine.

---

### Post by thecoolcat on 2008-01-26
> **modorf said:**
> some updates with my Kworld Atsc-110 experience Ubuntu fiesty, and mythtv

I'm able to capture with both the V4L standard def interface on analog cable and the DVB interface digital cable interface.  My system sees them as two different devices and need to be activated in Myth as such.  In the build with Ubuntu Fiesty, Myth doesn't give an option to link the dvb and v4l devs together, this has been modified in later svn builds.  I was able to change a record for the capture card in the database to tell myth they are linked together as 1 card.

Database: mythconverg  -   Table: capturecard  -  Field: parentid
The value for this field should be changed from 0 -> the card id of the dvb port

since I only have 1 tuner card : KWorld ATSC-110 
Here is my capturecard table (trimmed some of the info out)
cardid 	videodevice 	audiodevice 	vbidevice 	cardtype 	defaultinput 	parentid 
1 	0 	  	  	DVB 	DVBInput 	0
2 	/dev/video0 	/dev/dsp1 	/dev/vbi0 	V4L 	Television 	1

notice that cardid 2 has parentid 1  or that card2 is a child of 1.

Then in Mythtv-Setup: Input Connection card options will be
[DVB:0] -> (none)
 -> [/dev/video0: Television] -> (none)
 -> [/dev/video0: Composite]
 -> [/dev/video0: S-Video]

then add the listings.  This will help resolve recording conflicts between analog and dvb tuner.

I'm still have an issue with switching from DVB -> Analog and the channel not tuning without switching to another analog station and then back.  Almost as if the dvb dev isn't releasing the tuner.

Adding the following line in one of the files inside /etc/modprobe.d/* seems to solve the switching  between dvb --> analog problem. (I'm guessing you'd have already solved this issue, but should help others).
```
options dvb_core dvb_shutdown_timeout=0
```
 However, I'm not sure if the above option will impact the power management of the card.

---

