---
title: "VDPAU no longer working after upgrade to 10.04"
date: 2010-11-23
forum: Multimedia Software
---

### Post by Phil Urich on 2010-11-23
Much of this post is just a re-hash of a similar post I put up on the XBMC forums, since the box in question is mostly used as an XBMC instance.  I haven't gotten a reply there yet, though, and this is at heart a *buntu problem since it's more than just XBMC that is no longer able to use VDPAU

The title is my problem in a nutshell.

**Hardware:**
Pentium III 600 mHz, overclocked to 720mHz ohhh yeahhh! ;)
256MB RAM, man that was kickass back in the day
GeForce 8400GS 512MB PCI (not PCI-E, remember, it's a Pentium III)

**Software:**
Ubuntu 10.04.1 (minimal, no DE installed)
2.6.32-26-generic, i686
XBMC 9.11-lucid3 (from their PPA, I believe), r26018
nvidia-current 195.36.15-0ubuntu2
nvidia-glx-185 195.36.15-0ubuntu2 (kindof a package-misnomer, eh?)
mplayer 2:1.0~rc3+svn20090426-1ubuntu16


```

23:56:11 T:2977164144 M:113225728  NOTICE: Opening video stream: 0 source: 256
23:56:11 T:2977164144 M:113225728  NOTICE: Creating video codec with codec id: 28
23:56:11 T:2977164144 M:113225728  NOTICE: CDVDVideoCodecFFmpeg::Open() Creating VDPAU(1280x720)
23:56:11 T:2977164144 M:113225728  NOTICE: vdp_device = 0x00000000 vdp_st = 0x00000001
23:56:11 T:2977164144 M:113225728   ERROR: (VDPAU) unable to init VDPAU - vdp_st = 0x1.  Falling back.
23:56:11 T:2977164144 M:113225728  NOTICE: CDVDVideoCodecFFmpeg::Open() Failed to get VDPAU device
23:56:11 T:2977164144 M:113225728  NOTICE:  (VDPAU) ~CVDPAU
```

I've tried it with as large of a variety of videos (and codecs therein) as I can, the result is equally unimpressive every time.


I'm totally at a loss.  Tried uninstalling all the NVIDIA drivers and re-installing without any sort of PPAs or even updates enabled (hence the version), still nothing.  But it all worked perfectly fine last week under Karmic, running XBMC 9.11 too.  Yet now VDPAU won't work, sticking me with this CPU running at 720mHz trying desperately to process HD video (and failing quite miserably).  Is it something painfully obvious that I'm missing, or is there something strange and wrong with the main Ubuntu repo version of the NVIDIA drivers/libraries, or my install somehow?

It definitely seems to be a system-wide problem, not just XBMC per se.

mplayer's log (using SMPlayer as the frontend out of lazyness)  gives

```
[vdpau]Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```

vdpauinfo, meanwhile, states:

```
display: :0.0   screen: 0
Error creating VDPAU device: 1
```

I remain at a complete loss as to what to do.

---

### Post by mc4man on 2010-11-23
Honestly didn't use lucid too long, nor use many stock media players or libs.
You need libvdpau1 installed. If still no go then possibly consider using a new mplayer (built-in ffmpeg libs
This ppa is highly recommended and quite trustworthy - updates every 3 days or so though you don't have to update that often

[https://launchpad.net/~motumedia/+archive/mplayer-daily?field.series_filter=lucid](https://launchpad.net/~motumedia/+archive/mplayer-daily?field.series_filter=lucid)

---

### Post by Phil Urich on 2010-11-23
Since this computer just needs to run XBMC and . . . well, play video using XBMC, that's entirely it, I wouldn't really want to follow a potentially unstable PPA.  That's what my other 7 computers are for ;)

I don't blame you for thinking maybe I didn't install libvdpau1, but remember, I had this working before; that was still installed, and I triple-checked so too.

I figured it out, though.  In /usr/lib there were a bunch of symlinks which led to older, seemingly orphaned vdpau lib files:

```
/usr/lib/libvdpau_nvidia.so ->
  /usr/lib/libvdpau_nvidia.so.180.37

/usr/lib/libvdpau.so.1 ->
  /usr/lib/libvdpau.so.180.37

/usr/lib/libvdpau_trace.so ->
  /usr/lib/libvdpau_trace.so.180.37
```

Sitting there all un-linked-to was libvdpau.so.1.0.0, too. Meanwhile nvidia-current seemed to have installed symlinks for libvdpau_nvidia and libvdpau_trace in /usr/lib/vdpau. So I removed all the ones quoted above, made the /usr/lib/libvdpau.so.1 symlink point to /usr/lib/libvdpau.so.1.0.0, and voila!  Strangely enough this seems to have *also* fixed XBMC's ability to start its own xsession upon boot, although that seems unlikely (still, I don't remember doing anything else between reboots).

Anyways, 'tis all fixed.  Thanks for lending the hand, though!

---

### Post by reise.pt on 2011-01-02
I also had the problem with the symbolic links, and when I changed it to the new path all started to work again!
My /usr/lib dir is like this now
```
reise@htpc-linux:/usr/lib$ ls libvdpau* -l
lrwxrwxrwx 1 root root      24 2011-01-02 22:27 libvdpau_nvidia.so -> vdpau/libvdpau_nvidia.so
-rwxr-xr-x 1 root root 1474796 2010-02-08 17:24 libvdpau_nvidia.so.190.42
lrwxrwxrwx 1 root root      17 2010-05-16 18:40 libvdpau.so -> libvdpau.so.1.0.0
lrwxrwxrwx 1 root root      17 2011-01-02 22:39 libvdpau.so.1 -> libvdpau.so.1.0.0
-rw-r--r-- 1 root root    5332 2010-02-13 03:42 libvdpau.so.1.0.0
-rwxr-xr-x 1 root root    3624 2010-02-08 17:24 libvdpau.so.190.42
lrwxrwxrwx 1 root root      23 2011-01-02 22:29 libvdpau_trace.so -> vdpau/libvdpau_trace.so
-rwxr-xr-x 1 root root   50332 2010-02-08 17:24 libvdpau_trace.so.190.42
```

---

