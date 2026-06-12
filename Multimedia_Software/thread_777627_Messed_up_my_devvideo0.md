---
title: "Messed up my /dev/video0"
date: 2008-05-01
forum: Multimedia Software
---

### Post by NarsilAnduril on 2008-05-01
Hi,

Situation :
I'm running an Ubuntu 8.04 with a PVR-500.

No problem with the hardware nor with the driver :

```
03:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (1st unit)
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2

03:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (2nd unit)
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dc000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2

``` 

I used to be able to see both streams /dev/video0 and /dev/video1 in MPayer .

Problem :
I installed the mythbuntu metapackage and set up everything. The only thing that didn't work was the LiveTV and recording (quiet annoying ...;-)).

I thought it was (and still think it is) a right access problem on /dev/video0 and /dev/video1, so I checked the rights and both devices where owned by "root" and grouped under "video". My MythTV installed user is called "media", I tried to add the group "video" to user "media", but "video" didn't appear in the "users and groups" GUI of Ubuntu, so I added it and joined "media" to it.

From this point, I was unable to see the streams in MPlayer (nor in MythTV of course).

Running a dmesg|grep ivtv, a get a strange overflow problem :

```
[17064.340162] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[17064.340168] ivtv0: Cause: the application is not reading fast enough.
(.. many times)

```

Opening /dev/video0 in MPlayer returns a popup "seek failed" and /dev/video1 an "untuned" image (snow).

Could somebody help me with this ? My media box's WAF is dropping everyday :-((

Thanks

Diego

---

### Post by NarsilAnduril on 2008-05-02
Up ?

No way ?

---

### Post by jnygaard on 2008-05-24
Hi! Did you figure this one out? I think I have the same problem, though not using your set of applications, maybe.

I'm running 8.04, the card works, and I actually get a picture on the screen. I can do mplayer /dev/video0, and then tune in to different channels.

*However*... if I quit mplayer, I cannot start it again. It seems that something is hogging the device, and it's not mplayer or a zombie left by mplayer.

This manifests itself this way, for example:

cat /dev/video0 > z.z
cat: /dev/video0: Device or resource busy

I suspect that some "automagical" tool/daemon is sitting around, and then notices video0 after it is being used, and then grabs it (during or) after mplayer has used it, and then this prevents mplayer or my cat-command from ever again acessing the video device.

Does this make sense? Can somebody help me with resolving this? I have the definite feeling that this probably is some trivial setting, or removal of a program, or something... But I simply cannot see what is *actually* going on below the surface here... :-(

Jay

---

