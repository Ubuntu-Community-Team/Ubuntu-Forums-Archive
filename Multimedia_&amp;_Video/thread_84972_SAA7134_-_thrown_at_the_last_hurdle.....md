---
title: "SAA7134 - thrown at the last hurdle...."
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by xymox12 on 2005-11-01
fter a steep learning curve (linux newbie) I have got all my hardware working in Breezy 5.10....

except my Creatix Hybrid (Polymedia) SAA7134 TV card.  I use my pc as my tv so if I can't fix this its back to XP for me! As far as my computer manufacturer, Windows XP (fully functional analogue and DVB-T) and Breezy5.10 (card=12 (medion 7134) tuner=38 (Philips PAL/SECAM multi (FM1216ME MK3)) are concerned this card is detected correctly.



However in Breezy I get no picture just a blue screen in tvtime unless I (as root) -



> rmmod saa7134 

> modprobe saa7134 card=12 tuner=22 oss=1 



Tuner=22 (Temic PAL/SECAM multi (4046 FM5)) is not the correct hardware (tuner=38 is) so why does this work and tuner=38 does not!? 
Very confusing&#133;. 
 (note: I live in the UK so I want to use PAL-I )


As with many people I also get no sound - this card does not have a sound-out jack but rather processes the sound itself - I believe this is what the oss=1 is meant to catch. Dmesg gives me

[4295108.272000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4295108.277000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[4295108.277000] saa7134[0]: found at 0000:01:07.0, rev: 1, irq: 19, latency: 32, mmio: 0xf0015000
[4295108.277000] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,insmod option]
[4295108.277000] saa7134[0]: board init: gpio is 0
[4295108.403000] tuner 2-0061: chip found @ 0xc2 (saa7134[0])
[4295108.403000] tuner 2-0061: type set to 22 (Temic PAL/SECAM multi (4046 FM5))
[4295108.415000] saa7134[0]: i2c eeprom 00: be 16 03 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[4295108.415000] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[4295108.415000] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 1f 02 51 96 2b
[4295108.415000] saa7134[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[4295108.440000] saa7134[0]: registered device video0 [v4l2]
[4295108.441000] saa7134[0]: registered device vbi0
[4295108.442000] saa7134[0]: registered device radio0
[4295108.484000] saa7134[0]: registered device dsp1
[4295108.536000] saa7134[0]: registered device mixer1
[4295110.747000] saa7134[0]/audio: audio carrier scan failed, using 5.500 MHz [default]

 I have tried all the advice I can find  eg

1)	changing settings in alsamixer

2)	modprobe tda9887 qss=0 (with/without port2=1) etc


When tuned into a channel in tvtime a new message
> [4297044.247000] tda9885/6/7: i2c i/o error: rc == -5 (should be 4)
appears in dmesg.



I have also tried setting up DVB-T with this card. I find this confusing so I may be doing the wrong things - 

1) modprobe saa7134-dvb

2) modprobe tda1004x 

3) scan -v uk-BlackHill
	>scanning uk-BlackHill
	>using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
	>initial transponder 634167000 0 2 0 3 0 0 0
	>>> tune to: 634167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
	>>> tuning status == 0x1f
	>WARNING: filter timeout pid 0x0011
	>WARNING: filter timeout pid 0x0000
	>WARNING: filter timeout pid 0x0010
	>dumping lists (0 services)
	>Done.
4)dmesg
	[4295625.140000] DVB: registering new adapter (saa7134[0]).
	[4295625.140000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
	[4295668.566000] tda1004x: waiting for firmware upload (dvb-fe-tda10046.fw)...
	[4295668.619000] tda1004x: using firmware v20
	[4295672.222000] tda1004x: firmware upload complete
	[4295672.225000] tda1004x: firmware upload failed


Ahhhhhhh - I'm pulling my hair out. [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

Any help/advice much appreciated or if anyone with the same card has got it working please let me know.

Cheers

---

### Post by xymox12 on 2005-11-01
To add to my own post -

Got sound to work in analogue-tv using
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
from [http://tvtime.sourceforge.net/help.html#audioconnect](http://tvtime.sourceforge.net/help.html#audioconnect).

Not the best solution (sound seams a little delayed and very hissy) so still looking. But it does show the card sound is working :smile:

---

### Post by xymox12 on 2005-11-02
And again (hope this helps anyone with the same setup in the future) -
Finally got sound and picture on analogu tv using VLC (actually one of my staple MM players in windows) Yaaaaa:D 
Took looking at DScaler in windows for the frequency of a channel that gave a good picture and plugging it into the capture settings in VLC. I had to change the chroma settings to YUY2 or YV12 to get an image - the standard IV40 gave an error message - (plus some other standard settings for my PAL image).

Good old VLC - now onto DVB-T......

---

### Post by fragmental on 2005-11-03
video capture technology can be a pain in linux.

You can sign up for the video4linux mailing list.  that might help.   They will probably expect you to get the v4l2 cvs version though, which might not be a bad idea when it comes down to it.

Are you sure that the tuner really is 38 and isn't just getting recognized incorrectly? It's possible that the tuner isn't exactly supported but has an API compliant with tuner 22.

If you don't have a little audio patch cable to send it to audio, you might have to manually assign audio things.  I'd give a link to that but I need to go to sleep.  If you've got it working now, then maybe it doesn't need it anyway.

I didn't know vlc could show tv.  vlc is awesome.

I have an saa7140 based card and it seems to have some newer tuner that's not totally supported but it works with the alps tuners and new-tapc tuners.  I can't get fm radio to work though, and one of my channels has weird green and blue and purple lines.

good luck.

---

### Post by xymox12 on 2005-11-03
Cheers Fragmental,

Didn't mention that I had built/installed the latest  v4l cvs - but when I tried to modprobe the new saa7134 driver it error'd out saying something about not the same version as snd_pcm_new and other 'snd_ '- I built the latest alsa drivers and installed them but it didn't help, -googled around but without luck.
 Being quite new at linux I couldn't figure a way of reverting back to the original v4l (tried synaptic but it didn't help). In the end I had to do a full reinstall. But hey thats lifux.

I would like to try the new vl4 cvs again but am put off by the same thing happening. No doubt I will though.

---

### Post by fragmental on 2005-11-04
[https://www.redhat.com/mailman/listinfo/video4linux-list](https://www.redhat.com/mailman/listinfo/video4linux-list) is the address for the list info, if you haven't signed up for it already.  Those guys should know more about it than anyone.

and [http://linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS](http://linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS) is instructions for building CVS, if you haven't seen that either.

the wiki [http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page) is pretty helpful, if you don't have that bookmarked.

I haven't been brave enough yet to take the plunge into v4l cvs.  I have everything except radio, and a single broadcast channel working(tuner isn't exactly supported on the kernel's v4l), so I'm not in that big of a hurry.  My card is just a cheap analog flyvideo oem card anyway.  I'm more interested in getting Mythtv setup, but I've just been too lazy.  It's a lot more fun to watch tv than to go to great pains to record it.

---

### Post by xymox12 on 2005-11-04
Howdy

Well I went for the V4L cvs yesterday - and ouch! was that a fight - but finally got it to work and now have the new sa7134 driver modprobed.

And guess what - it correctly identifies my card as 12 and tuner as 63 (Hybrid phillips MK3). Analogue tv tuning is now rock solid with all the channels tuned(used to be hit and miss with tuner=22).

Loading the new saa7134-dvb module fixes the firmware problem and the dvb software seems to be doing something now but havn't had time to play around with it yet. Looks like it should work though.

One worrying thing is that I can't get sound apart from some screeching noises in VLC anymore -  but its early days yet. The new saa7134 mod has an alsa register now as well as the old oss register - so not quite sure what that implies. Seems like some messing around to be had....

Cheers

---

### Post by daller on 2005-12-16
Hi There,

I have the same card:

```

0000:00:0d.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
        Subsystem: Creatix Polymedia GmbH: Unknown device 0003
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at d8001000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>


```

I also have a sound problem...

I'm using tvtime!

Everytime I change channel, I get a scrambled sound (like when no signal) for about 5-6 seconds  (The video works instantly)

Any ideas?

---

### Post by daller on 2005-12-16
This was due to a faulty choice of audio default (PAL-DK) - I now use PAL-BG and it works perfectly!

---

