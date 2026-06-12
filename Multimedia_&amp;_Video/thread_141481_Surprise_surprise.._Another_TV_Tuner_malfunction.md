---
title: "Surprise surprise.. Another TV Tuner malfunction"
date: 2006-03-08
forum: Multimedia &amp; Video
---

### Post by jokr2thief on 2006-03-08
Okay, I've been banging my head against my desk about this one for weeks. 

I recently purchaced a Saberent SBT-TVFM tuner card for my PC. Now this card works _near_ flawlessly in Windows, but for some reason, It's just not getting along in Linux.

I can start a TV application, (I'm using tvtime) and I see a picture, but I see the last thing I was watching in Windows and when I try to change channels, they don't actually change. It's sort of a 'the same thing on every channel'. It will change the numbers, but won't actually tune to the new channel.

Then there's the FM Radio portion of the card that dosen't work at all because it's missing a device node for /dev/radio and my attempts to add one failed miserably. 


```
Could not open device "/dev/radio" !

Check your Settings and make sure that no other
program is using /dev/radio.
Make also sure that you have read-access to it. 
```

There is no /dev/radio, nor is there another another device in /dev that looks like it would be anything close. I tried to mknod it, but that didn't seem to be working out too well.

And finally, there's the remote that came with the card. lirc dosen't seem to be working, as it dosen't recognize where the input is coming from... And I'm not quite sure what to do about that, but that is the least of my conserns, as the remote is useless if I don't have the rest of the card functioning, so I haven't put a lot of time and effort into figuring out why that's not working yet.

An lspci identifies it as the following... 

```
0000:01:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:01:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

And an lsmod | grep bt shows the following.

```
bt878                   9912  0
bttv                  141456  1 bt878
video_buf              19844  1 bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
videodev                9344  1 bttv
```

So if anyone has any ideas on how to get this working, I would be most grateful.

--Jokr2Thief -- Your speed bump on the Information Superhighway

---

### Post by jokr2thief on 2006-03-10
I'm going to go ahead and give this a bump considering no one's replied to it and  I'm still not any closer to figuring out why it dosen't work.

I've tried both the saa3174 and bt878 modules because for reasons I can't figure out, the card is identifying itself as a Brooktree, but all the documentation I've read proclaims that it's a phillips chipset.

---

### Post by lupin492 on 2006-09-15
I get similar results on Dapper.
Regarding your video and radio devices, they ARE there, it´s just they are under /dev/.static/dev/radio (and video).
Anyway, having read, write or execute permissions on these devices won´t help.
Based on what I read in forums, this behaviour of your TV-watching apps. means that you (we  :-( ) have the driver(s) properly working, but the card and tuner aren´t properly chosen.  It seems this card (Sabrent SBT-TVFM with Conexant Fusion BT878 chip) is not
included in the driver packed with Ubuntu.  Some people advise to patch the drivers and recompile, but I don´t have the knowledge to do that.
I´ll be looking for answers on other sites, and I´ll post if I find something useful.
Regards.

---

### Post by lupin492 on 2006-09-16
I got some good news:

The only thing I had to do is to create a file called 'bttv' in '/etc/modprobe.d' with the following content:

options bttv card=142 tuner=68

( it doesn't matter here if you specify radio=1 or pll=1)
card=142 is for the bt878 version of the board, card=42 is for the SAA7134 version.
tuner=68 is the best approximation I got for the TNF5835-MFF tuner.
---YOU HAVE TO RELOAD THE PC FOR CHANGES TO TAKE EFFECT ---
You can see cable channels from 2 to 62 ( I don't know how to get the last channels until 84). It works well WITH sound, but the radio part does not work with these settings.
My TV standard is PAL-Nc (Argentina).

If you issue the command 'dmesg | grep bt', you can see something like this when the card paramenters are unspecified:

dmesg:

[ 43.172721] bttv: driver version 0.9.16 loaded
[ 43.172726] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 43.172770] bttv: Bt8xx card found (0).
[ 43.172794] GSI 19 sharing vector 0xC1 and IRQ 19
[ 43.172798] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 193
[ 43.172811] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 193, latency: 64, mmi o: 0xf5300000
[ 43.172823] bttv0: using: [COLOR="Red"]*** UNKNOWN/GENERIC ***[/COLOR] [card=0,autodetected]
[ 43.172859] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[ 43.381415] bttv0: i2c scan: found device @ 0xc0 [tuner (analog)]
[ 43.381931] bttv0: i2c scan: found device @ 0xc2 [tuner (analog)]
[ 43.448617] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[ 43.448621] bttv0: using tuner=-1
[ 43.448624] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 43.450746] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[ 43.452873] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 43.454994] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 43.457170] bttv0: registered device video0
[ 43.457199] bttv0: registered device vbi0
[ 43.530866] bt878: AUDIO driver version 0.0.0 loaded
[ 43.530885] bt878: Bt878 AUDIO function found (0).
[ 43.530905] ACPI: PCI Interrupt 0000:00:0e.1[A] -> GSI 19 (level, low) -> IRQ 193
[ 43.530914] bt878(0): Bt878 (rev 17) at 00:0e.1, irq: 193, latency: 64, memor y: 0xf5400000

-------------------------------------------------------------------------
When you do specify the mentioned parameters for the board, you get something like this:

'dmesg | grep bt':
claudio@flash64:/etc/modprobe.d$ dmesg | grep bt
[ 39.974522] bttv: driver version 0.9.16 loaded
[ 39.974527] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 39.974566] bttv: Bt8xx card found (0).
[ 39.974607] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 193, latency: 64, mmio: 0xf5300000
[ 39.974618] bttv0: using: [COLOR="SeaGreen"]Sabrent TV-FM (bttv version) [card=142[/COLOR],insmod option]
[ 39.974654] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[ 39.976871] bttv0: using tuner=68
[ 39.976876] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 40.079234] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[ 40.079775] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[ 40.110314] bttv0: registered device video0
[ 40.110339] bttv0: registered device vbi0
[ 40.110362] bttv0: registered device radio0
[ 40.110382] bttv0: PLL: 28636363 => 35468950 .. ok
[ 40.199501] bt878: AUDIO driver version 0.0.0 loaded
[ 40.199532] bt878: Bt878 AUDIO function found (0).
[ 40.199560] bt878(0): Bt878 (rev 17) at 00:0e.1, irq: 193, latency: 64, memory: 0xf5400000

I&#314;l further investigate to get the card 100% operational.
I think next step is Dscaler, btspy, and the like.
Hope this will be helpful.  
 Regards.

---

### Post by rustlerharv on 2006-10-01
> **lupin492 said:**
> I got some good news:

The only thing I had to do is to create a file called 'bttv' in '/etc/modprobe.d' with the following content:

options bttv card=142 tuner=68

( it doesn't matter here if you specify radio=1 or pll=1)
card=142 is for the bt878 version of the board, card=42 is for the SAA7134 version.
tuner=68 is the best approximation I got for the TNF5835-MFF tuner.
---YOU HAVE TO RELOAD THE PC FOR CHANGES TO TAKE EFFECT ---
You can see cable channels from 2 to 62 ( I don't know how to get the last channels until 84). It works well WITH sound, but the radio part does not work with these settings.
My TV standard is PAL-Nc (Argentina).

If you issue the command 'dmesg | grep bt', you can see something like this when the card paramenters are unspecified:

dmesg:

[ 43.172721] bttv: driver version 0.9.16 loaded
[ 43.172726] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 43.172770] bttv: Bt8xx card found (0).
[ 43.172794] GSI 19 sharing vector 0xC1 and IRQ 19
[ 43.172798] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 193
[ 43.172811] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 193, latency: 64, mmi o: 0xf5300000
[ 43.172823] bttv0: using: [COLOR="Red"]*** UNKNOWN/GENERIC ***[/COLOR] [card=0,autodetected]
[ 43.172859] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[ 43.381415] bttv0: i2c scan: found device @ 0xc0 [tuner (analog)]
[ 43.381931] bttv0: i2c scan: found device @ 0xc2 [tuner (analog)]
[ 43.448617] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[ 43.448621] bttv0: using tuner=-1
[ 43.448624] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 43.450746] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[ 43.452873] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 43.454994] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 43.457170] bttv0: registered device video0
[ 43.457199] bttv0: registered device vbi0
[ 43.530866] bt878: AUDIO driver version 0.0.0 loaded
[ 43.530885] bt878: Bt878 AUDIO function found (0).
[ 43.530905] ACPI: PCI Interrupt 0000:00:0e.1[A] -> GSI 19 (level, low) -> IRQ 193
[ 43.530914] bt878(0): Bt878 (rev 17) at 00:0e.1, irq: 193, latency: 64, memor y: 0xf5400000

-------------------------------------------------------------------------
When you do specify the mentioned parameters for the board, you get something like this:

'dmesg | grep bt':
claudio@flash64:/etc/modprobe.d$ dmesg | grep bt
[ 39.974522] bttv: driver version 0.9.16 loaded
[ 39.974527] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 39.974566] bttv: Bt8xx card found (0).
[ 39.974607] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 193, latency: 64, mmio: 0xf5300000
[ 39.974618] bttv0: using: [COLOR="SeaGreen"]Sabrent TV-FM (bttv version) [card=142[/COLOR],insmod option]
[ 39.974654] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[ 39.976871] bttv0: using tuner=68
[ 39.976876] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 40.079234] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[ 40.079775] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[ 40.110314] bttv0: registered device video0
[ 40.110339] bttv0: registered device vbi0
[ 40.110362] bttv0: registered device radio0
[ 40.110382] bttv0: PLL: 28636363 => 35468950 .. ok
[ 40.199501] bt878: AUDIO driver version 0.0.0 loaded
[ 40.199532] bt878: Bt878 AUDIO function found (0).
[ 40.199560] bt878(0): Bt878 (rev 17) at 00:0e.1, irq: 193, latency: 64, memory: 0xf5400000

I&#314;l further investigate to get the card 100% operational.
I think next step is Dscaler, btspy, and the like.
Hope this will be helpful.  
 Regards.


yay I got video and can finally change channels.  My problem is that I don't have sound.  It appears the problem is that my sound card isn't taking the line in input and running it into the speaker output.  I am able to get sound from the tv tuner by plugging my speakers into the output of the tv tuner.  My sound card is a sound blaster audigy 2 ZS. If anyone has any ideas it would help thanks.

---

### Post by observative on 2008-01-04
Hey glad you got it working, and I realize this is an older thread. I'm posting because I though it helpful to others to know about this great HOWTO, that helped me install and use my Sabrent SBT-TVFM tuner card.
[http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)
and this one
[http://ubuntuforums.org/showthread.php?t=408307](http://ubuntuforums.org/showthread.php?t=408307)
that has a bit more of a newb approach and refers to the HOWTO.

---

