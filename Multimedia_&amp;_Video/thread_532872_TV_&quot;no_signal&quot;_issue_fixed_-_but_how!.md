---
title: "TV &quot;no signal&quot; issue fixed - but how?!"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by Meurglys on 2007-08-23
Hello. I'm posting this, even though I solved it already. Hope it helps someone. :)

What happened?

One night I watched TV as usual with my old Hauppauge WinTV PCI card that I've been using on various Linux Systems for years without any problems, ever. Currently I'm on Feisty 64 bit.

I left the computer on, went to bed, got up in the morning, fired up tvtime to watch the news - nothing. Only a blue screen and a "no signal" message. A channel scan didn't bring up anything.

So I started looking into the problem.

All hardware firmly in its place.

Permissions ok, and I'm member of "video" too.

```
meurglys@ubuntu:~ $ ls -l /dev/video*
crw-rw---- 1 root video 81, 0 2007-08-21 20:40 /dev/video0

meurglys@ubuntu:~ $ sudo adduser meurglys video
The user `meurglys' is already a member of `video'.
```

Card and driver are there:

```
meurglys@ubuntu:~ $ dmesg | grep bttv
[   40.103127] bttv: driver version 0.9.16 loaded
[   40.103132] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   40.103174] bttv: Bt8xx card found (0).
[   40.103573] bttv0: Bt878 (rev 17) at 0000:01:07.0, irq: 18, latency: 132, mmio: 0xd3000000
[   40.103582] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   40.103584] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   40.103613] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   40.106117] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   40.134053] bttv0: Hauppauge eeprom indicates model#44354
[   40.134056] bttv0: using tuner=28
[   40.134115] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   40.181935] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   40.182622] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   40.305529] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   40.331197] bttv0: registered device video0
[   40.331223] bttv0: registered device vbi0
[   40.331247] bttv0: registered device radio0
[   40.341458] bttv0: PLL: 28636363 => 35468950 .. ok
```

No errors on the terminal either:

```
meurglys@ubuntu:~ $ tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/meurglys/.tvtime/tvtime.xml
cpuinfo: CPU Dual-Core AMD Opteron(tm) Processor 1214, family 15, model 3, stepping 2.
cpuinfo: CPU measured at 1000.052MHz.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 70200000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 2.
xfullscreen: Head 0 at 0,0 with size 1280x1024.
xfullscreen: Head 1 at 1280,0 with size 1280x1024.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Metacity and is EWMH compliant.
xcommon: You are using metacity.  Disabling aspect ratio hints
xcommon: since most deployed versions of metacity are still broken.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 500: NV05 Video Blitter.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/meurglys/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'bttv', card 'BT878 video (Hauppauge (bt878))' (bus PCI:0000:01:07.0).
videoinput: Version is 2320, capabilities 5010015.
videoinput: Maximum input width: 924 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (72).
```

And it's not a problem with tvtime, happens with scantv on the command line too:

```
meurglys@ubuntu:~ $ scantv -c /dev/video0 -C /dev/vbi0

scanning channel list europe-west...
E2   ( 48.25 MHz): no station
E3   ( 55.25 MHz): no station
E4   ( 62.25 MHz): no station
S01  ( 69.25 MHz): no station
S02  ( 76.25 MHz): no station
S03  ( 83.25 MHz): no station
...
```

... and so on. You get the point.

I found many people  in this forum with similar issues, but no real solution.

I tried modprobing card=10 and tuner=28, as suggested.
I completely removed all tv apps including config files, logged off and on, yes rebooted even, reinstalled - nothing.

And so on.

Now, what did the trick was this:

Completely remove all tv applications including all config files. (--> Synaptic)
Shut down.
Remove the TV card!
Boot up.
Shut down.
Pop the card back into its slot.
Boot up.
Reinstall TV app, e.g. tvtime.
Scan for channels.
Watch Simpsons!

:popcorn:

Now I'm curious to find out what has happened here. IRQ confusion? Voodoo? System hiccup? Bad dreams manifesting in computer issues? :confused:

Even though it's working now I'm not really happy cause I don't know WHY it happened in the first place.

Does anyone have an idea?

Thanks in advance. :)

---

