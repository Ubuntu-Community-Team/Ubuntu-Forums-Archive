---
title: "Problem :: VIA XvMC / MythTV 0.21 / Upgrade to Ubuntu 8.04"
date: 2008-05-07
forum: Mythbuntu
---

### Post by little_sam on 2008-05-07
I have recently done a dist upgrade to Ubuntu 8.04 and since this I have been having problems with MythTV.

Previously I had no problems using the internal myth viewer to play back using the VIA XvMC extension, but it appears that this no longer works, and hence myth is reverting to a different decode method, which my CPU can't cope with. (get prebuffering pauses and audio buffer underruns).

I have tried /etc/X11/XvMCConfig being:
/usr/lib/libXvMC.so.1
/usr/lib/libviaXvMC.so.1
libXvMC.so.1
with no luck on any of them.


System Details:
EPIA SP13000 with VIA CN400 decoder chip
Myth Version: 0.21.0+fixes17145-0ubuntu0+mythbuntu2



MythFrontend Log:
```
2008-05-07 23:21:23.059 TV: Attempting to change from None to WatchingPreRecorded
2008-05-07 23:21:23.192 DPMS Deactivated
ViaXvMC: Could not allocate timestamp blit area.
2008-05-07 23:21:25.624 VideoOutputXv Error: Unable to create XvMC Context, status(11): BadAlloc
2008-05-07 23:21:25.627 VideoOutputXv Error: Could not open XvMC port...

                        You may wish to verify that your DISPLAY
                        environment variable does not use an external
                        network connection.

                        You may also wish to verify that
                        /etc/X11/XvMCConfig contains the correct
                        vendor's XvMC library.

2008-05-07 23:21:25.630 AFD: Opened codec 0x90dde90, id(MPEG2VIDEO) type(Video)
2008-05-07 23:21:25.632 AFD: codec MP3 has 2 channels
2008-05-07 23:21:25.634 AFD: Opened codec 0x90de210, id(MP3) type(Audio)
2008-05-07 23:21:25.635 AFD: codec MP3 has 1 channels
2008-05-07 23:21:25.637 AFD: Opened codec 0x90de590, id(MP3) type(Audio)
2008-05-07 23:21:25.637 AFD: Opened codec 0x90de910, id(DVB_SUBTITLE) type(Subtitle)
2008-05-07 23:21:25.712 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-07 23:21:25.716 Opening ALSA audio device 'default'.
2008-05-07 23:21:26.866 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-05-07 23:21:26.894 VideoOutputXv: XVideo Adaptor Name: 'XV_SWOV'
2008-05-07 23:21:27.392 OSD Theme Dimensions W: 640 H: 480
2008-05-07 23:21:31.567 TV: Changing from None to WatchingPreRecorded
2008-05-07 23:21:31.599 Realtime priority would require SUID as root.
2008-05-07 23:21:31.616 FilterManager: failed to load filter 'none', no such filter exists
2008-05-07 23:21:31.617 Couldn't load deinterlace filter none
2008-05-07 23:21:31.980 Video timing method: DRM
2008-05-07 23:21:34.834 NVP: prebuffering pause
2008-05-07 23:21:40.548 NVP: prebuffering pause
2008-05-07 23:21:42.064 NVP: prebuffering pause

```

Xorg.0.log:
```
[snip]
(II) VIA(0): [Xv] Using PCI DMA for Xv image transfer.
(II) VIA(0): Benchmarking video copy. Less is better.
(--) VIA(0): Timed   libc YUV420 copy... 2905414. Throughput: 108.9 MiB/s.
(--) VIA(0): Timed kernel YUV420 copy... 2868473. Throughput: 110.3 MiB/s.
(--) VIA(0): Timed    SSE YUV420 copy... 1859647. Throughput: 170.2 MiB/s.
(--) VIA(0): Timed    MMX YUV420 copy... 3166870. Throughput: 99.9 MiB/s.
(--) VIA(0): Ditch 3DNow! YUV420 copy... Not supported by CPU.
(--) VIA(0): Timed   MMX2 YUV420 copy... 2224402. Throughput: 142.3 MiB/s.
(--) VIA(0): Using SSE YUV42X copy for video.
(II) VIA(0): [XvMC] Registering viaXvMCPro.
(II) VIA(0): [XvMC] Initialized XvMC extension.
(WW) VIA(0): Option "XvmcUsesTextures" is not used
(WW) VIA(0): Option "NvAGP" is not used
[/snip]

```

Any help would be greatly appreciated - I'm not really sure where to go from here.

cheers

sam

---

### Post by dantheperson on 2008-05-14
I've got exactly the same problem on a SP8000.

one thing i've tried is switching from the via driver to the openchrome driver

Driver          "openchrome"

and

libchromeXvMCPro.so.1

same result

---

### Post by dantheperson on 2008-05-14
Well,

I've got it working using openchrome.  I'm not sure it was the driver change that fixed it though, as i still get the same error as you after a restart with openchrome.

What i have to do is view a movie using xine -V xxmc, then quit xine, then myth will work again.
> 2008-05-15 00:39:28.036 VideoOutputXv: XvMC Adaptor Name: 'XV_SWOV'
Unable to create XvMC Surface.


Althought it says unable to create surface, the "ViaXvMC: Could not allocate timestamp blit area." error is gone and it doesn't fall back to a different renderer, and from the CPU usage i can tell it is working.

---

### Post by dantheperson on 2008-05-15
Well, anothers day usage has shown XvMC to be totally unreliable.  Sometime it works sometimes it doesn't.

Further more getting kernel crashes like > May 15 00:40:01 rebirth kernel: [  819.439293] ------------[ cut here ]------------
May 15 00:40:01 rebirth kernel: [  819.439320] kernel BUG at /build/buildd/linux-2.6.24/mm/vmalloc.c:349!
May 15 00:40:01 rebirth kernel: [  819.439332] invalid opcode: 0000 [#1] SMP 
May 15 00:40:01 rebirth kernel: [  819.439343] Modules linked in: via drm rfcomm l2cap bluetooth apm ppdev cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table cpufreq_userspace cpufreq_powersave iptable_filter ip_tables x_tables jfs nls_iso8859_1 nls_cp437 vfat fat aes_i586 ipv6 dm_crypt dm_mod sbp2 lp snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_dummy evdev snd_seq_oss dvb_pll parport_pc parport snd_seq_midi snd_rawmidi mt352 usbhid snd_seq_midi_event hid snd_seq cx88_dvb cx88_vp3054_i2c videobuf_dvb dvb_core af_packet snd_timer snd_seq_device snd cx8802 cx8800 pcspkr cx88xx ir_common i2c_algo_bit tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common soundcore videobuf_dma_sg videobuf_core btcx_risc i2c_viapro i2c_core shpchp pci_hotplug via_agp agpgart usb_storage ext3 jbd mbcache libusual sr_mod sg cdrom sd_mod ata_generic pata_via sata_via pata_acpi via_rhine mii ehci_hcd uhci_hcd libata ohci1394 scsi_mod usbcore ieee1394 
May 15 00:40:01 rebirth kernel: bcon tileblit font bitblit softcursor fuse
May 15 00:40:01 rebirth kernel: [  819.439599] 
May 15 00:40:01 rebirth kernel: [  819.439611] Pid: 6955, comm: mythbackend Not tainted (2.6.24-16-generic #1)
May 15 00:40:01 rebirth kernel: [  819.439625] EIP: 0060:[__vunmap+0xc7/0xf0] EFLAGS: 00010246 CPU: 0
May 15 00:40:01 rebirth kernel: [  819.439663] EIP is at __vunmap+0xc7/0xf0
May 15 00:40:01 rebirth kernel: [  819.439672] EAX: 00000000 EBX: 00000000 ECX: 00000002 EDX: 00000610
May 15 00:40:01 rebirth kernel: [  819.439685] ESI: cdfa3b60 EDI: 00000001 EBP: daa2e458 ESP: cd8e5f2c
May 15 00:40:01 rebirth kernel: [  819.439697]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May 15 00:40:01 rebirth kernel: [  819.439711] Process mythbackend (pid: 6955, ti=cd8e4000 task=daa245a0 task.ti=cd8e4000)
May 15 00:40:01 rebirth kernel: [  819.439722] Stack: ddae7284 dda83ac7 ddbecb04 daa2e414 ddbecb04 daa2e414 de352000 dda81fa3 
May 15 00:40:01 rebirth kernel: [  819.439749]        00000000 db7ee140 ddbecb78 00000008 db7ee140 db2f1660 db8503d0 c018e2b7 
May 15 00:40:01 rebirth kernel: [  819.439774]        00000000 00000000 db2f1660 da05ef80 db8503d0 db7ee140 ce942480 00000000 
May 15 00:40:01 rebirth kernel: [  819.439798] Call Trace:
May 15 00:40:01 rebirth kernel: [  819.439819]  [<dda83ac7>] dvbdmx_release_ts_feed+0x77/0xa0 [dvb_core]
May 15 00:40:01 rebirth kernel: [  819.439954]  [<dda81fa3>] dvb_demux_release+0x93/0x160 [dvb_core]
May 15 00:40:01 rebirth kernel: [  819.440041]  [__fput+0xa7/0x190] __fput+0xa7/0x190
May 15 00:40:01 rebirth kernel: [  819.440114]  [filp_close+0x49/0x80] filp_close+0x49/0x80
May 15 00:40:01 rebirth kernel: [  819.440171]  [sys_close+0x6e/0xd0] sys_close+0x6e/0xd0
May 15 00:40:01 rebirth kernel: [  819.440205]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 15 00:40:01 rebirth kernel: [  819.440328]  =======================
May 15 00:40:01 rebirth kernel: [  819.440334] Code: c8 3a c0 c7 04 24 ed da 39 c0 e8 95 d7 fa ff 83 c4 10 5b 5e 5f e9 1a 71 f8 ff 8b 46 10 e8 a2 99 00 00 eb aa 83 c4 10 5b 5e 5f c3 <0f> 0b eb fe 89 5c 24 04 c7 04 24 88 c9 3a c0 e8 65 d7 fa ff c7 
May 15 00:40:01 rebirth kernel: [  819.440437] EIP: [__vunmap+0xc7/0xf0] __vunmap+0xc7/0xf0 SS:ESP 0068:cd8e5f2c
May 15 00:40:01 rebirth kernel: [  819.440474] ---[ end trace d027e00f039d5019 ]---

Usually either mythfrontend or mythbackend are the process that experience the failure.  The processes are then unkillable and a reboot is required.

So i went back to the 2.6.20-16-generic kernel that is still on the system from before i upgraded from feisty to hardy.  Still running hardy and myth 0.21 from hardy, but with the feisty kernel.

Now it works 100%, even better than i remember, 7% CPU usage playing back on this 800Mhz ancient CPU.  Excellent.

---

### Post by robho on 2008-05-18
dantheperson,

what driver works for you? Do both via and openchrome work? Do you need /etc/X11/XvMCConfig to get xvmc going?

I'm using the same hardware as little_sam (SP13000, CN400) and can't quite get XVMC to work.

I had xvmc working nicely in another linux distribution, but when I tried mythbuntu it stopped working. I tried using my old configuration with mythbuntu, but it didn't change anything.

---

### Post by dantheperson on 2008-05-22
Both via and openchrome worked unreliably under the 8.04 kernel.

After going back to the feisty kernel it has worked 100% with openchrome.  I haven't tried via since downgrading the kernel.

Mine is the SP8000, no fan, less mhz, otherwise identical

Changing XvMCConfig didn't seem to have any effect, but i haven't exhaustively proven that.  After a couple of weeks of no TV, once it started working, i've left it untouched.

The xvmc library name is different between via and openchrome packages, something like libviaXvMCPro.so.1 vs libchromeXvMcPro.so.1

---

### Post by robho on 2008-06-21
Thanks! I got xvmc going with an older kernel too. I'll see if I can narrow this problem down and file a bug somewhere.

xvmc seems to work both in mythtv and xine with the old kernel so I believe the problem is not with mythtv, but probably with the kernel or something interfacing with the kernel.

---

### Post by little_sam on 2008-06-21
I have also managed to get xvmc working in 2 earlier kernels, but not 2.6.24-16. My problem is that this breaks something else :(

Good luck with the bug finding - if I can do anything let me know

---

### Post by robho on 2008-07-10
Just a little update..

It seems like the commit c153f45f9b7e30289157bba3ff5682291df16caa to the Linux kernel introduces XVMC problems. This is between 2.6.23 and 2.6.24 so all 2.6.23 kernels are OK, but nothing newer.

I still haven't figured out if this is an xorg driver problem triggered by the kernel change or if it's the kernel change that's bad.

I will try to figure that out, but it might take some time.

If someone has some insight into XvMC, the openchrome/via driver and the kernel DRI interface I'd appreciate any input/comments.

---

### Post by theophile on 2008-07-11
Does anyone know if this kernel patch affects nVidia XvMC or only VIA?

---

### Post by andyfromtucson on 2008-11-05
I just recently upgraded a Via Epia SP8000e to Mythbuntu 8.04 and I also cannot get XvMC to work. I think I have configured everything right in Playback Profiles to use XvMC (I created a new profile with just one entry and specified using VIA XvMC as the decoder), and it appears the Mythbuntu 8.04 automatically used the Openchrome driver, but still CPU usage is 70-90% when I watch a recorded program when it should be around 20%.

Has anyone found a solution besides using a kernel earlier than 2.6.24? I have no idea about how to go about switching to an earlier kernel, and I am afraid 8.04 will break if I go back to an earlier kernel.
 
I did a lot of googling on this issue and the only other place I could find where it was discussed in depth is here:

[http://bugs.gentoo.org/show_bug.cgi?id=228473]("http://bugs.gentoo.org/show_bug.cgi?id=228473")

But there is no apparent resolution posted there.

I also tried upgrading to Mythbuntu 8.10 but in one quick test after rebooting XvMC still doesn't appear to be working.

---

### Post by robho on 2008-11-09
I can get xvmc working with recent kernels if I switch from SLUB memory allocator to SLAB. This requires a recompile of the kernel since all kernels (except for the rt-kernel (but it crashes for me)) are using SLUB.

I'd still like to get this sorted out though, but I don't really know where to turn. This is clearly not a ubuntu-only bug since it has been seen in gentoo and slackware too. So filing a bug with the ubuntu guys don't seem quite right.

Right now the gentoo bug mentioned above is probably the best place to discuss the problem. If people with this xvmc problem would submit their configuration and findings to that bug it would probably help to get this issue resolved and give it some attention.

---

### Post by andyfromtucson on 2008-11-10
I finally gave up on trying to get VIA XvMC to work with Mythbuntu 8.04 and 8.10 and found the ISO for Mythbuntu 7.10 and installed it.

VIA XvMC works with Mythbuntu 7.10 for me, but be careful to deselect the backports repository before you do any package updates. The backports repository is enabled by default in Mythbuntu 7.10 and it contains the Gutsy backport of MythTV 0.21 which breaks XvMC.

I filed a comment on the Gentoo bug report as suggested by Robho.

---

### Post by andyfromtucson on 2008-11-28
There is now a patch available to the Openchrome driver that fixes this problem:

[http://bugs.gentoo.org/show_bug.cgi?id=228473]("http://bugs.gentoo.org/show_bug.cgi?id=228473")

Its the one called ioctlfix.patch.  Robho was kind enough to send me instructions on how to apply the patch to Mythbuntu 8.10. I first downloaded the patch file from the bug report to my home directory, and then ran the following commands all in my home directory, and then rebooted.

```
sudo apt-get build-dep xserver-xorg-video-openchrome
sudo apt-get install build-essential
wget http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.903.orig.tar.gz
wget http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.903-0ubuntu3.diff.gz
tar xf xserver-xorg-video-openchrome_0.2.903.orig.tar.gz
zcat xserver-xorg-video-openchrome_0.2.903-0ubuntu3.diff.gz | patch -p0
patch -p0 < ioctlfix.patch
cd xf86-video-openchrome-0.2.903
./configure --prefix=/usr
make
sudo make install
```

After applying this patch and rebooting I was able to successfully play a recording using XvMC on Mythbuntu 8.10 on my Via Epia SP8000e.

---

### Post by little_sam on 2008-12-24
Thank you so much - I have followed the instructions, with a fresh install of MythBuntu 8.10 and I now have a working system again.

Any news when this patch will be applied to to the driver distributed in the kernel?

---

### Post by richard.e.morton on 2009-08-16
I have the same problem... I am running mythbuntu 9.04.

I have tried this patch and couldn't see anything particularly wrong until this line:
> patch -p0 < ioctlfix.patch

I had previously given up on MythBuntu and started using MythDora5 although I now see that this issue also presents itself in MythDora 10.21.

From the reports on this thread this looks like this is the answer and I am surprised that this fix hasn't made it into the drivers in some form.

---

### Post by robho on 2009-09-20
The above patch is included in 9.04 and later ubuntu releases ([ubuntu bug 304119]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/304119")) so there is no longer any need to manually patch openchrome.

For me XvMC works out of the box with 9.04 and a CN400 chipset.

---

### Post by scovel on 2009-09-20
I have a VIA EPIA SP13000, it has the CN400 chipset (nothing but trouble...).  I just reloaded my frontend.  I was running and ancient Gentoo system and XvMC was working well.  I just loaded on Mythbuntu 9.04.  When DRI is enabled, all I get is choppy stuttering video and audio.  Lots of "WriteAudio: buffer underrun" and " NVP: prebuffering pause".  If I disable "glx" in the xorg.conf then XvMC/DRI is effectively disabled and things work better.  CPU is 70%-80% and I get the occasional stutters.  With XvMC under Gentoo the audio/video was perfect and CPU Utilization was around 20%.

I'm using the S-Video connector.

I've done all the usual voodoo to get XvMC going.  I'm stuck.  Any thoughts?

Thanks,

Sean

---

### Post by robho on 2009-09-20
My setup is identical to yours. SP13000, ubuntu 9.04 and S-video output.

XvMC seems to work for me. It's been a while since I installed this machine (think it was a hardy installation initially), but I can't think of any special configuration needed. The problem mentioned above was the only big problem for me.

I guess you have DRI working, but you should see something like this in xorg log:

(II) CHROME(0): direct rendering enabled
...
(II) CHROME(0): [XvMC] Registering chromeXvMCPro.
(II) CHROME(0): [XvMC] Initialized XvMC extension.

And in the log from mythfrontend this seems normal:

VideoOutputXv: XvMC Adaptor Name: 'XV_SWOV'
Unable to create XvMC Surface.

I admin that it doesn't look ok, but I'm quite sure xvmc is used. I get black-white osd (I'm using 16bpp) and the video is much more fluent than when using xv.

My xorg configuration contains only
Option "TVType" "PAL"
Option "TVDeflicker"  "2"
And 720x576@16bpp. All other settings are the default values.

Have you setup your playback profile in mythtv? I have removed all profiles and only use one with these settings:
resolution: > 0x0
decoder: VIA XvMC
max cpus: 1
video renderer: xvmc-blit
osd renderer: chromakey

I think I've had some problems with the mythtv playback profiles so check those (setup->setup->tv setting->playback).

---

### Post by robho on 2009-09-20
Sean..

I just realized that I've had to configure the frequency scaling to avoid audio clicks. The default CPU governor in ubuntu is ondemand which makes the cpu switch frequencies quite often and these frequency hops caused the audio to stutter for me. I changed the governor to conservative so that it makes fewer frequency hops and that works better for me. I think this is specific to SP13000.

You could try this to switch to conservative mode:
> sudo bash
> echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

---

### Post by scovel on 2009-09-21
Out of the box it wasn't wroking. XvMC wasn't activated.  It did install the Openchrome X server and related drivers.  For some reason it was not loading the kernel modules "via" and "dri" so I had to add those in modules.d.

Next, it wasn't using the TV-Out, so I added some stuff in the xorg.conf.  At that point XvMC was enabled (from messages in Xorg.0.log) but the video would start and stop every couple of seconds.

If I disable "glx" in xorg.conf, this effectively disables XvMC, and the video is almost perfect, but CPU utilization is 80%.  Any complex motion on the screen causes dropped video and audio.

I did go into the setup and made a config that only uses VIA XvMC with all the other settings you recommended.  That didn't help.

I tried the scaling_governor as you recommended.  It didn't make a difference.

Did you do a clean install of 9.04 or an upgrade from Hardy?

Sean

---

### Post by robho on 2009-09-21
I upgraded from Hardy.

I'm pretty confused. My drm and via drivers seem to load automatically without any manual configuration. And I don't need any xorg configuration to enable TV output..

What video files are you trying to play using XvMC? Could it be that mythtv records into mpeg4 or something else that isn't accelerated by xvmc? I have a PVR-150 TV card which records into mpeg2 in hardware. Maybe you can check your recording profiles and tweak it into recording into mpeg2?

Have you tried playing a DVD using xvmc? The menu always uses xv, but the movie is mpeg2 and should be accelerated by xvmc.

---

### Post by scovel on 2009-09-22
If you upgraded from Hardy, lots of things were already setup and working.  That's probably why you didn't have to make any changes.

I have a setup very similar to yours.  I have a PVR-250 in the backend for recording.  I'm trying to play MPEG2 files.

I looked at some log files last night.  There is something odd going on with MythTV and my X setup.  I suspect things in the Openchrome driver have changed significantly since I set it up in Gentoo.  I think what I need is a valid xorg.conf, and things might start working.

I'm in NTSC land.  Anyone got a working xorg.conf for a CN400 with VIA XvMC working?

Robho, I know your setup is PAL, but would you mind giving me your xorg.conf?

Here is a section from my xorg log file

```

2009-09-21 20:00:10.795 VideoOutputXv: XvMC Adaptor Name: 'XV_SWOV'
Unable to create XvMC Surface.
2009-09-21 20:00:10.979 OSD Theme Dimensions W: 640 H: 480
2009-09-21 20:00:12.905 TV: Changing from None to WatchingPreRecorded
2009-09-21 20:00:12.907 New DB connection, total: 4
2009-09-21 20:00:12.914 Using realtime priority.
2009-09-21 20:00:12.921 Connected to database 'mythconverg' at host: 10.10.20.20
2009-09-21 20:00:12.922 Video sync method can't support double framerate (refresh rate too low for bob deint)
2009-09-21 20:00:12.925 Failed to approve 'onefield' deinterlacer
2009-09-21 20:00:12.925 Couldn't load deinterlace filter
2009-09-21 20:00:12.941 Video timing method: DRM
2009-09-21 20:00:17.021 NVP: Timed out waiting for free video buffers.
2009-09-21 20:00:17.697 NVP: prebuffering pause
2009-09-21 20:00:17.699 WriteAudio: buffer underrun


```Seems like my refresh rate is too low?  None of the deinterlacers work.  Then the timeouts and pauses begin.

Sean

---

### Post by robho on 2009-09-22
Here's my complete xorg.conf. As I said, not much in there. Actually I think the only reason I have anything at all is because I want PAL (NTSC is default I think) and I want to set a resolution matching a PAL TV.

```

Section "Device"
 Identifier	"Configured Video Device"
 Option "TVType" "PAL"
 Option "TVDeflicker"  "2"
EndSection

Section "Monitor"
 Identifier	"Configured Monitor"
EndSection

Section "Screen"
 Identifier	"Default Screen"
 Monitor	"Configured Monitor"
 Device		"Configured Video Device"
 DefaultDepth	16

 Subsection "Display"
  Depth 16
  Modes "720x576Over"
 EndSubsection
EndSection

```

And for reference, here's a typical mythfrontend log when watching a recording. This is actually MythTV 0.22, SVN 21940 from the daily builds server. I had no problems with 0.21-fixes, but wanted to see what 0.22 was all about (it's pretty buggy so stay with 0.21-fixes for now).

```

2009-09-22 19:56:33.607 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-09-22 19:56:33.685 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2009-09-22 19:56:34.541 AFD: Opened codec 0xa9dd590, id MPEG2VIDEO_XVMC_VLD) type(Video)
2009-09-22 19:56:34.546 AFD: codec MP2 has 2 channels
2009-09-22 19:56:34.551 AFD: Opened codec 0xaa62040, id(MP2) type(Audio)
2009-09-22 19:56:34.583 Opening audio device 'default'. ch 2(2) sr 48000
2009-09-22 19:56:34.587 Opening ALSA audio device 'default'.
2009-09-22 19:56:35.100 VideoOutputXv: XvMC Adaptor Name: 'XV_SWOV'
Unable to create XvMC Surface.
2009-09-22 19:56:35.143 VideoOutputXv: Number of bits per pixel is 16, 
                        but we only support ARGB 32 bbp for ChromaKeyOSD.
2009-09-22 19:56:35.154 NVP(0): Forcing decode extra audio option on (Video method requires it).
2009-09-22 19:56:35.166 OSD Theme Dimensions W: 1280 H: 720
2009-09-22 19:56:35.637 Unknown altfont: infofont in textarea: callsign
2009-09-22 19:56:37.157 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -
- end ok2009-09-22 19:56:37.159 TV: Changing from None to Watching WatchingPreRecorded
2009-09-22 19:56:37.196 ScreenSaverX11Private: DPMS Deactivated 1
2009-09-22 19:56:37.217 Realtime priority would require SUID as root.
2009-09-22 19:56:39.430 NVP(0): Timed out waiting for free video buffers.
2009-09-22 19:56:40.197 Video timing method: USleep with busy wait
2009-09-22 19:56:46.055 TV: Attempting to change from Watching WatchingPreRecorded to None
2009-09-22 19:56:46.074 TV: Changing from Watching WatchingPreRecorded to None
2009-09-22 19:56:46.075 ScreenSaverX11Private: DPMS Reactivated 1

```

I really don't know what else to suggest. Here are some parts from my Xorg.0.log. I don't attach the whole file, because it's pretty huge, but I'll send it to you in a private message if you want the whole 83kb thing.

```

Current Operating System: Linux dumburken 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
...
(--) PCI:*(0@1:0:0) VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] rev 2, Mem @ 0xe0000000/67108864, 0xe8000000/16777216, BIOS @ 0x????????/65536
...
(II) Module openchrome: vendor="http://openchrome.org/"
        compiled for 1.5.99.902, module version = 0.2.903
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
...
(II) CHROME(0): VIAGetRec
(**) CHROME(0): Depth 16, (--) framebuffer bpp 16
(==) CHROME(0): RGB weight 565
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: PM800/PM880/CN400
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options.
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Reading config file...
(**) CHROME(0): Option "TVDeflicker" "2"
(**) CHROME(0): Option "TVType" "PAL"
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): Shadow framebuffer is disabled.
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Using hardware two-color cursors and software full-color cursors
.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
        if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(**) CHROME(0): TV deflicker is set to 2.
(**) CHROME(0): TV Type is PAL.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xe8000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xe8200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(WW) CHROME(0): Manufacturer plainly copied main PCI IDs to subsystem/card IDs.
(--) CHROME(0): Detected VIA VT3118 (PM800).
(II) CHROME(0): Detected MemClk 6
(II) CHROME(0): ViaGetMemoryBandwidth
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:E-EDID segment register" registered at address 0x60.
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaVT162xDetect
(II) CHROME(0): I2C device "I2C bus 3:VT162x" registered at address 0x40.
(--) CHROME(0): Detected VIA Technologies VT1622A/VT1623 TV Encoder
(II) CHROME(0): ViaTVInit
(II) CHROME(0): ViaVT162xInit
(II) CHROME(0): VT162xSave
(II) CHROME(0): VT1622DACSense
(--) CHROME(0): VT162x: S-Video connected.
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x07
(II) CHROME(0): ViaOutputsSelect: CRT.
(II) CHROME(0): ViaOutputsSelect: TV.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.lo to 30.000000
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 47.250000
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 47.500000
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.lo to 29.049999
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.lo to 28.000000
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.lo to 25.000000
(II) CHROME(0): Configured Monitor: Using hsync range of 25.00-47.50 kHz
(II) CHROME(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
... Lots of display mode validation ...
(--) CHROME(0): Virtual size is 720x576 (pitch 720)
(**) CHROME(0): *Default mode "720x576Over": 27.0 MHz (scaled from 0.0 MHz), 31.
2 kHz, 50.0 Hz
(II) CHROME(0): Modeline "720x576Over"x50.0   27.00  720 768 800 864  576 577 57
9 625 -hsync +vsync (31.2 kHz)

```

Btw.. Not all deinterlacers are supported by XvMC. I can't find that setting now, but I think Bob is one of the supported. I think it says in the help for that setting.

---

### Post by scovel on 2009-09-24
Gave up.  I've wasted my last hour getting that Via Chrome video card configured.  They have promised Linux support for years.  I ordered an Nvidia 9400 GT.  Going with VDPAU.

My next frontend won't be an Via Epia.  I'll go with an Nvidia Ion.  They may only have non-free closed binary drivers, but THEY WORK.

I'm not bitter....

;)

Sean

---

### Post by waynemcl on 2009-10-07
Anybody in this thread tried Karmic / 9.10 beta? Does DVD playback or TV playback work ok on VIA epia e.g m10000? (I'm downloading it, will try soon). Cheers, W

---

### Post by richard.e.morton on 2009-10-07
Have a look at this thread regarding xvmc and karmic.  
[http://ubuntuforums.org/showthread.php?p=8032842](http://ubuntuforums.org/showthread.php?p=8032842)

---

### Post by scovel on 2009-10-12
Turns out it wasn't an XvMC issue after all.  See this thread:

[http://ubuntuforums.org/showthread.php?p=8092415#post8092415](http://ubuntuforums.org/showthread.php?p=8092415#post8092415)

---

### Post by dantheperson on 2009-11-01
> **andyfromtucson said:**
> There is now a patch available to the Openchrome driver that fixes this problem:

[http://bugs.gentoo.org/show_bug.cgi?id=228473]("http://bugs.gentoo.org/show_bug.cgi?id=228473")

Its the one called ioctlfix.patch.  Robho was kind enough to send me instructions on how to apply the patch to Mythbuntu 8.10. 
Should this patch work on 8.04, same instructions?  I recently updated my box after being on holiday for a year, and now wireless networking doens't work with the old kernel i am running.  I have to choose from the fiesty kernel with working XvMC or the hardy kernel with working networking...

---

### Post by robho on 2009-11-01
Dan,

the instructions may work for you with 8.04, but since the instructions use the packages from 8.10 you will end up using the openchrome driver from 8.10 in your 8.04 installation. May work, may not..

I checked the 8.04 version of openchrome and the ioctl patch should work with that driver version too. If you want to patch the 8.04 openchrome driver you "only" need to change the links in the patch instructions so that they link to the 8.04 openchrome source code. The proper links can be found here: [http://packages.ubuntu.com/hardy/xserver-xorg-video-openchrome](http://packages.ubuntu.com/hardy/xserver-xorg-video-openchrome)

Here's an attempt to adapt the patch instruction to 8.04. I don't have an 8.04 installation these days so I can't verify it, but I think I got it right.

```

sudo apt-get build-dep xserver-xorg-video-openchrome
sudo apt-get install build-essential
wget http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.901.orig.tar.gz
wget http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.901-0ubuntu4.diff.gz
tar xf xserver-xorg-video-openchrome_0.2.901.orig.tar.gz
cd xserver-xorg-video-openchrome
zcat ../xserver-xorg-video-openchrome_0.2.901-0ubuntu4.diff.gz | patch -p1
patch -p1 < ioctlfix_from_gentoo_bug.patch
./configure --prefix=/usr
make
sudo make install

```

After you have run this you have overwritten your openchrome driver with the patched version. If you ever reinstall the openchrome ubuntu package or update it, the patch will go away.

---

