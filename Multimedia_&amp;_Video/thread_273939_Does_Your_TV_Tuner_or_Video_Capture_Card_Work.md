---
title: "Does Your TV Tuner or Video Capture Card Work?"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by insub2 on 2006-10-09
What Card do you have? (where'd you get it, maybe?)

Does it work in Ubuntu?

How much work effort did it take you to get it to work?/What did you have to do?

---

### Post by woekele on 2006-10-09
I have one with a bt878 chipset (dont remember which card exactly, sorry), I put it in, booted Ubuntu, downloaded 'tvtime', started it and it worked :)

---

### Post by bearswatchin on 2006-10-09
I have a bt878 card from Hauppauge that has good video and audio in TVTime but I cannot change the channels. It is 'stuck' on whatever channel was last viewed in win2k. (I am trying to move away from Windoze).

dmesg indicates that no tuner is detected. I have tried to remove and reinstall the card and reinstall. No luck. Uninstall doesn't work and I haven't been able to manually force the tuner to be detected. 

I have been to the TVTime web site and haven't seen this problem either there or here.

Please help.

---

### Post by anaconda on 2006-10-10
I have Hauppauge WinTv NOVA-T USB2 and all I had to do was download the correct firmware  (dvb-usb-nova-t-usb2-01.fw) and copy it to /lib/firmware folder and reboot.

---

### Post by eldragon on 2006-11-02
ive got a flyvideo with the  saa7134 chipset. worked right away.
now if i only could record the streams!...

---

### Post by insub2 on 2006-11-03
> **eldragon said:**
> ive got a flyvideo with the  saa7134 chipset. worked right away.
now if i only could record the streams!...

I ended up getting a couple off ebay with BT848 chipsets, both work great for viewing!

there is a way to [record with vlc]("http://www.ubuntuforums.org/showthread.php?t=143732") but you can't see what you're recording and the quality isn't *great*.

---

### Post by belly917 on 2006-11-03
Hauppage PVR-150

I installed the latest drivers from the [IVTV project](http://ivtvdriver.org/index.php/Main_Page)

Make sure you choose the proper drivers to match your kernel.

Then I followed a how-to that I found is specific for [ installing mythtv on ubuntu dapper server](http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation).  but I have edgy so I had to adapt some

the Hauppage PVR series work great because they have a built in mpeg2 encoder, so there's minimal cpu usage.

---

### Post by NemesisUK on 2006-11-03
I have a Compro DVB-T300 and all I had to do was insert saa7134-dvb into /etc/modules and then scan the channels with kaffeine. Works wonderfully.

---

### Post by RikBlankestijn on 2006-11-14
According to lspci I have:
02:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

The logo on the box: E-tech, and the type: TVPI03

And I am still struggling to get it to work. The best situation I could produce was watching tv without sound.

---

### Post by drphilngood on 2006-11-14
> **insub2 said:**
> What Card do you have? (where'd you get it, maybe?)
Leadtek's TV2000 XP Series Model 3 with FM radio, from [Monarch]("http://www.monarchcomputer.com/Merchant2/merchant.mv")(I buy most of my stuff from these guys because of their great CS & prices)

> **insub2 said:**
> Does it work in Ubuntu?
Works very well, even the FM tuner.

> **insub2 said:**
> How much work effort did it take you to get it to work?/What did you have to do?
Neither TVtime nor Gnomeradio had sound but reconfiguring Alsa fixed that.

---

### Post by RikBlankestijn on 2006-11-14
> **drphilngood said:**
> ...

Neither TVtime nor Gnomeradio had sound but reconfiguring Alsa fixed that.
Please tell me how you configured Alsa to fix the sound.

---

### Post by LeonHeart on 2006-12-14
drphilngood just one question,
i have the same problem you had.
tv card, fm tuner correctly recognized but no sound.
what excactly did you reconfigure in alsa?
please reply a post or pm me.
thanks...

---

### Post by bianconiglio on 2007-12-01
Success! I have cable in the Netherlands and a PC with a tvcard from e-tech. Model number TVPI03 (that's a cheap 30euro card). 
It works well under windows (with some hideous software that is on the product cd. 
It did not work easily in Ubuntu 7.10 Gutsy Gibbon. Now I have tv with sound (through sox, alsa using PAL-I) with tvtime.

Acknowledgements: My steps are based on advice by david_2001 on [http://ubuntuforums.org/showthread.php?t=352196&page=5](http://ubuntuforums.org/showthread.php?t=352196&page=5)
(which is for a different card though). And a great clue by peter missel on [http://marc.info/?l=linux-video&m=116811879125416&w=2](http://marc.info/?l=linux-video&m=116811879125416&w=2)
where he identifies the e-tech TVPI03 card as a flavour of Lifeview Platinum FM. 

My steps are as follows: 
I have  /etc/modules unchange (no extra line with saa7134 e.g.). 
I have a file /etc/modprobe.d/saa7134 with a single line:

options saa7134 card=54 alsa=1

I run dmesg to see if the card is detected, and get: 

saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 19, latency: 32, mmio: 0xe0004000
saa7133[0]: subsystem: 4e42:5214, board: LifeView FlyTV Platinum FM / Gold [card=54,insmod option]
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0
saa7133[0]: registered device radio0
saa7134 ALSA driver for DMA sound loaded
saa7133[0]/alsa: saa7133[0] at 0xe0004000 irq 19 registered as card -2

Then I run tvtime-scanner, which scans for channels (takes some time). You only need to do this once... the command creates a channel list. After finishing scanning, you can run tvtime. Either from the terminal, or from the applications menu. Tvtime should give you images. 

Now to get sound going... 

First I do: 

sudo alsactl names
 which writes in "/etc/asound.names". That file reads, in my case, 
 
ctl {
        alsactl1 {
                name hw:0
                comment 'Physical Device - NVidia nForce2 with ALC650F
at irq 18
'
        }
        alsactl2 {
                name hw:1
                comment 'Physical Device - MPU-401 UART at 0x330, irq
10'
        }
        alsactl3 {
                name **hw:2**
                comment 'Physical Device - saa7133[0] at 0xe0004000 irq
19'
        }....

The bold value (about the saa7133) is what you need in the command below: 
Type in a terminal:

sox -r 32000 -w -t alsa **hw:2**,0 -t alsa pcm.default &

This gives me tv+sound with tvtime audio set on PAL-BG! Slight sound-delay, same as under windows. 

Next time you log on "tvtime &" in a terminal and then the sox command suffice. 

Bye bye!

---

### Post by acoustibop on 2007-12-01
I have a couple of Hauppauge ImpactVCB cards running in two Gutsy machines; I literally just stuck them in, booted up and installed TVTime - instant result.

I don't need a card with a tuner as I'm on cable - I have to tune in channels with the box anyway.

The audio inputs directly into the soundcard, so was not a problem - on one machine, the sound is enabled automatically on starting TVTime, but doesn't mute when I stop TVTime; I have to do it manually.  On the other machine, I have to start and stop the sound manually.  I haven't installed anything for capture with these cards yet.

---

### Post by sturmey on 2007-12-06
I have a twinhan 1020 DVB-s card. it works fairly well under Windoze, and it's a complete pain under linux. I've searched off and on for three years to get it to work, and there is almost no information other than "it's supported" (my answer is not very well)

previous versions of debian, mandrake, redhat, etc. did not even load the device after doing modprob with the drivers. I lost two months trying to find out how to get the card to work. finally gave up and used m$, worked within 2 hours.

I decided to try again, and I've found almost no information for it, but with the help of a friend who knows linux fairly well, I've discovered that with mythbuntu, I still had to install dvb-utils, (not mentioned in any how to's) and then installed kaffeine, and after playing with the settings I was able to get some channels scanned in and I did get a picture for a second.

Myth is another story. showing the card, gave me "failed to open" errors, commented out the wacom lines in xorg.conf why they were there, I have no idea. reboot crashed X. reboot again, X tried to reconfigure. (never did change the display settings, only commented the graphics tablet lines). X still complains when I boot. now I can get the card to open, but it doesn't show any signal or quality when I try to scan, and it won't do a blind scan. 

Now do I put the frequency in by Khz, Mhz, hz? I really hate the fact that myth has such poor documentation when it comes to well... anything. nice program, but a PITA to setup

Sturmey

---

### Post by PhilJ on 2007-12-12
Tevion 713 XTV   TV7134FR   with saa 7134 chipset works  set as 
saa7134 card=5

Philj

---

### Post by awthomp on 2007-12-12
I have a Hauppauge PVR-150 that worked out of the box with Ubuntu 7.10.  It's great that Linux is starting to get to the point where one doesn't have to scratch his head or sift through tons of documentation for something pretty complicated to "just work"

---

### Post by steefjeqv on 2007-12-12
Hi,

I'm using the following cards :

- Terratec Cinergy 1400 DVB-T : plug 'n play in Feisty.
- Typhoon DVB-S plus (KNC1 clone) : needed a modprobe (saa7146) in Feisty.

For the moment I've got both cards running in a VDR-system based on Debian Etch.
They were both recognized by Etch (plug 'n play).

Greetings,
Steven

---

### Post by MaxWildwood on 2007-12-13
I am using pcHDTV HD-5500 with Mythbuntu 7.10, on 64-bit processor.

Card recognized during installation and no problems getting it to work.  Record/playback all works in MythTV.  I use the card only to receive terrestrial broadcast HDTV (no cable, no satellite) also known as ATSC in the USA.

---

### Post by Mad_Max_1412 on 2008-07-06
> **NemesisUK said:**
> I have a Compro DVB-T300 and all I had to do was insert saa7134-dvb into /etc/modules and then scan the channels with kaffeine. Works wonderfully.

My modules file reads:

fuse
lp
sbp2
saa7134 card=70 tuner=67
saa7134
saa7134-dvb
saa7134_alsa


But Kaffeine can only find 3 varieties of Channel 10 (Standard Definition, HD, etc.

Do I need to change/delete any of these lines?

Thanks

---

