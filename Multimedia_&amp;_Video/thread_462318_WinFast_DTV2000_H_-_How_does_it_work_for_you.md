---
title: "WinFast DTV2000 H - How does it work for you ?"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by Z42 on 2007-06-02
Hi,

I have not seen that many posts about this card.

I managed to make DVB work on Feisty (pretty easy using Kaffeine) but there are number of things that still fail:
- Analog TV: how do I select the input (Antenna/Cable) ? I checked with most of the TV apps and none display the option. Sometimes (randomly when, for some reason, the right input is enabled on the card), I can see analog channels in, say, TVtime.
- CVBS/Composite signal input: this totally fails. I tried many options but never managed to capture the video input.

Capture should be there:
[FONT="Courier New"]$ v4l2-ctl  --all
Driver info:
        Driver name   : cx8800
        Card type     : WinFast DTV2000 H
        Bus info      : PCI:0000:00:0b.0
        Driver version: 6
        Capabilities  : 0x05010011
                Video Capture
                VBI Capture
                Tuner
                Read/Write
                Streaming[/FONT]

I checked the code for cx88 I saw the specific section (cx88-cards.c):
[FONT="Courier New"][CX88_BOARD_WINFAST_DTV2000H] = {
		/* video inputs and radio still in testing */
		.name           = "WinFast DTV2000 H",
		.tuner_type     = TUNER_PHILIPS_FMD1216ME_MK3,
		.radio_type     = UNSET,
		.tuner_addr     = ADDR_UNSET,
		.radio_addr     = ADDR_UNSET,
		.tda9887_conf   = TDA9887_PRESENT,
		.input          = {{
			.type   = CX88_VMUX_TELEVISION,
			.vmux   = 0,
			.gpio0  = 0x00017304,
			.gpio1  = 0x00008203,
			.gpio2  = 0x00017304,
			.gpio3  = 0x02000000,
		}},
		.mpeg           = CX88_MPEG_DVB,
},[/FONT]

Maybe someone can tell me from his experience or from the code above 
- if there is a way to solve my issues 
- or if I should just forget about it (and switch to a better card?)

Note that this is a good surprise DVB works(and fails on a commercial OS on which it is supposed to be officially supported). Could not get any kind of help from Leadtek.

Thank you for any hint,
Z

---

### Post by Z42 on 2007-06-05
Ok, video capture works now. Try at your own risk...
Sorry if this is not the right way to do it... I started on Ubuntu only a few weeks ago (great stuff!!!)

Here is the section of the cx88-cards.c I modified:
	```
{
		/* video inputs and radio still in testing */
		.name           = "WinFast DTV2000 H",
		.tuner_type     = TUNER_PHILIPS_FMD1216ME_MK3,
		.radio_type     = UNSET,
		.tuner_addr     = ADDR_UNSET,
		.radio_addr     = ADDR_UNSET,
		.tda9887_conf   = TDA9887_PRESENT,
		.input          = {
			{
				.type   = CX88_VMUX_TELEVISION,
				.vmux   = 0,
				.gpio0  = 0x00017304,
				.gpio1  = 0x00008203,
				.gpio2  = 0x00017304,
				.gpio3  = 0x02000000,
			},
			{
				.type   = CX88_VMUX_COMPOSITE1,
				.vmux   = 1,
				.gpio3  = 0x02000000,
			},
		},
		.mpeg           = CX88_MPEG_DVB,
	},
```

I used the great information from Alain there (sorry this is in french): [http://alainperrot.perso.cegetel.net/]("http://alainperrot.perso.cegetel.net/")
(don't forget to reboot after you replaced the .ko files)

I am using the following command to display the WII output on my Linux desktop:
```
mplayer tv:// -tv driver=v4l2:device=/dev/video0:norm=pal-bg:input=1:outfmt=uyvy
```

:D

---

### Post by grege on 2007-06-08
Under Feisty

I had to add a few lines to /etc/modules
ir-common
dvb-core
cx88-dvb

and fired up kaffeine and the TV works fine and I can record and playback, the remote has some functionality - change channels with the numbers and adjust volume.

However try as I might I cannot get the system to recognise the FM tuner and create a /dev/radio0

I have loaded every module that seems relevant, but nothing. Any ideas?

I may have to wait for the 2.6.22 kernel, or chuck it and get a Winfast 2000 expert

:(

---

### Post by rominet7777 on 2007-07-07
Hi,

I just had a *very* hard time to make the beast work in analogic mode with mplayer, but I did it (I did not try the module recompilation to enable composite yet...)

OK, so I'm in France, and I had to figure out a lot of things like : 
- the sound is stereo, and you **must** use amode=1
- because of the video size (?) you have to use a big buffer
- sometimes the sound is just crap, you have to restart mplayer anyway
- you have to define an input config file to remap^some keys (defaults of h and k for channel tunning is not good on my keyboard...)
- do **NOT** use secam nor pal, look at mplayer output to see what modes are supported
- the audio indeed is 48000 Hz

OK, here is my big command line :

```

mplayer -input conf=tvinput.conf -autosync 30 tv:// -tv driver=v4l2:device=/dev/video1:width=768:height=576:norm=secam-l:chanlist=europe-west:alsa:adevice=hw.1,0:volume=90:audiorate=48000:immediatemode=0:amode=1:buffersize=64:channels=49-tf1,52-France_2,62-France_3,65-Canal,59-Arte,42-M6:fps=30 -vf pp=ci

```

Hope this will help some people...

Cheers

---

### Post by monkeytech on 2007-11-23
Thanks to the Posts above i can get RCA input working using the settings outlined in 2nd post...

thanks heaps... now if i could just work out the best way to stream video/enbed in website (as i have my dv cam hooked up thought it.

---

### Post by monkeytech on 2007-11-23
> **Z42 said:**
> 
I am using the following command to display the WII output on my Linux desktop:
```
mplayer tv:// -tv driver=v4l2:device=/dev/video0:norm=pal-bg:input=1:outfmt=uyvy
```

:D

any ideas how to make this work thought VLC ? so i can setup streaming? i am a little lost and have tried a few diff settings


cheers

---

### Post by monkeytech on 2007-11-24
> **monkeytech said:**
> any ideas how to make this work thought VLC ? so i can setup streaming? i am a little lost and have tried a few diff settings


cheers

Answering my own question here.. for those with this card and above hack.. u can use this v4l line in vlc to access the video inputs 

 v4l:// :v4l-vdev="/dev/video0" :v4l-adev="/dev/dsp" :v4l-norm=3 :v4l-channel=1 :v4l-tuner=-1 :v4l-audio=-1 :no-v4l-mjpeg


works for me will play around some more


regards

---

