---
title: "2 Problems: Linksys WUSB600n and audio over HDMI"
date: 2010-12-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by go4linux on 2010-12-13
I tried to install the alpha to solve a problem I have with my computer connected to the tv, and now I have an extra problem.

**New problem:**

I have a Linksys WUSB600N. With 10.10 I managed to get it working, but with the alpha I didn't. To install the driver I have to change a couple of files and compile, so it's possible that I made a mistake, but I checked a couple of times, and everything seems to go well. Except that it doesn't work.
This is the relevant part of my messages file, which I get when I plug in the adapter:
> Dec 13 14:28:59 tvpc kernel: [ 1949.800047] usb 1-2: new high speed USB device using ehci_hcd and address 11
Dec 13 14:28:59 tvpc kernel: [ 1949.983494] ------------[ cut here ]------------
Dec 13 14:28:59 tvpc kernel: [ 1949.983511] WARNING: at include/linux/netdevice.h:1557 RtmpPhyNetDevInit+0xeb/0x100 [rt3572sta]()
Dec 13 14:28:59 tvpc kernel: [ 1949.983514] Hardware name: System Product Name
Dec 13 14:28:59 tvpc kernel: [ 1949.983516] Modules linked in: rt3572sta nls_iso8859_1 nls_cp437 vfat fat usb_storage uas binfmt_misc parport_pc ppdev snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_usb_audio snd_pcm snd_hwdep snd_usbmidi_lib snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq i915 snd_timer snd_seq_device arc4 snd crc_ccitt rt2x00lib mac80211 cfg80211 snd_page_alloc drm_kms_helper drm joydev i2c_algo_bit video output usbhid psmouse hid soundcore uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 shpchp asus_atk0110 serio_raw lp parport r8169 [last unloaded: rt2x00usb]
Dec 13 14:28:59 tvpc kernel: [ 1949.983562] Pid: 29, comm: khubd Tainted: G        W   2.6.37-7-generic #19-Ubuntu
Dec 13 14:28:59 tvpc kernel: [ 1949.983564] Call Trace:
Dec 13 14:28:59 tvpc kernel: [ 1949.983572]  [<ffffffff8106621f>] warn_slowpath_common+0x7f/0xc0
Dec 13 14:28:59 tvpc kernel: [ 1949.983575]  [<ffffffff8106627a>] warn_slowpath_null+0x1a/0x20
Dec 13 14:28:59 tvpc kernel: [ 1949.983587]  [<ffffffffa03c21eb>] RtmpPhyNetDevInit+0xeb/0x100 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983597]  [<ffffffffa03d2ce3>] rt2870_probe.clone.5+0x1c3/0x3d0 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983609]  [<ffffffffa03c2000>] ? MainVirtualIF_open+0x0/0x100 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983621]  [<ffffffffa03c1bc0>] ? MainVirtualIF_close+0x0/0x360 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983633]  [<ffffffffa03c2290>] ? rt28xx_send_packets+0x0/0x50 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983644]  [<ffffffffa03c1980>] ? rt28xx_ioctl+0x0/0x20 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983656]  [<ffffffffa03c1830>] ? RT28xx_get_ether_stats+0x0/0x150 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983666]  [<ffffffffa03d2f2a>] rtusb_probe+0x3a/0x60 [rt3572sta]
Dec 13 14:28:59 tvpc kernel: [ 1949.983671]  [<ffffffff81434e49>] usb_probe_interface+0x109/0x200
Dec 13 14:28:59 tvpc kernel: [ 1949.983675]  [<ffffffff813afba8>] really_probe+0x68/0x190
Dec 13 14:28:59 tvpc kernel: [ 1949.983679]  [<ffffffff813afea5>] driver_probe_device+0x45/0x70
Dec 13 14:28:59 tvpc kernel: [ 1949.983682]  [<ffffffff813affd3>] __device_attach+0x53/0x60
Dec 13 14:28:59 tvpc kernel: [ 1949.983685]  [<ffffffff813aff80>] ? __device_attach+0x0/0x60
Dec 13 14:28:59 tvpc kernel: [ 1949.983688]  [<ffffffff813ae8d4>] bus_for_each_drv+0x64/0x90
Dec 13 14:28:59 tvpc kernel: [ 1949.983691]  [<ffffffff813afd8f>] device_attach+0x8f/0xb0
Dec 13 14:28:59 tvpc kernel: [ 1949.983694]  [<ffffffff813af36d>] bus_probe_device+0x2d/0x50
Dec 13 14:28:59 tvpc kernel: [ 1949.983697]  [<ffffffff813acf57>] device_add+0x307/0x410
Dec 13 14:28:59 tvpc kernel: [ 1949.983701]  [<ffffffff81433029>] usb_set_configuration+0x679/0x760
Dec 13 14:28:59 tvpc kernel: [ 1949.983705]  [<ffffffff8143c8e4>] generic_probe+0x44/0xa0
Dec 13 14:28:59 tvpc kernel: [ 1949.983709]  [<ffffffff81434f70>] usb_probe_device+0x30/0x60
Dec 13 14:28:59 tvpc kernel: [ 1949.983712]  [<ffffffff813afba8>] really_probe+0x68/0x190
Dec 13 14:28:59 tvpc kernel: [ 1949.983715]  [<ffffffff813afea5>] driver_probe_device+0x45/0x70
Dec 13 14:28:59 tvpc kernel: [ 1949.983718]  [<ffffffff813affd3>] __device_attach+0x53/0x60
Dec 13 14:28:59 tvpc kernel: [ 1949.983721]  [<ffffffff813aff80>] ? __device_attach+0x0/0x60
Dec 13 14:28:59 tvpc kernel: [ 1949.983724]  [<ffffffff813ae8d4>] bus_for_each_drv+0x64/0x90
Dec 13 14:28:59 tvpc kernel: [ 1949.983727]  [<ffffffff813afd8f>] device_attach+0x8f/0xb0
Dec 13 14:28:59 tvpc kernel: [ 1949.983731]  [<ffffffff813af36d>] bus_probe_device+0x2d/0x50
Dec 13 14:28:59 tvpc kernel: [ 1949.983734]  [<ffffffff813acf57>] device_add+0x307/0x410
Dec 13 14:28:59 tvpc kernel: [ 1949.983737]  [<ffffffff8142b7dd>] usb_new_device+0x7d/0x100
Dec 13 14:28:59 tvpc kernel: [ 1949.983740]  [<ffffffff8142c4b0>] hub_port_connect_change+0x5c0/0x980
Dec 13 14:28:59 tvpc kernel: [ 1949.983744]  [<ffffffff8142cbb0>] hub_events+0x340/0x4d0
Dec 13 14:28:59 tvpc kernel: [ 1949.983747]  [<ffffffff8142cd75>] hub_thread+0x35/0x180
Dec 13 14:28:59 tvpc kernel: [ 1949.983751]  [<ffffffff81088390>] ? autoremove_wake_function+0x0/0x40
Dec 13 14:28:59 tvpc kernel: [ 1949.983754]  [<ffffffff8142cd40>] ? hub_thread+0x0/0x180
Dec 13 14:28:59 tvpc kernel: [ 1949.983757]  [<ffffffff81087c66>] kthread+0x96/0xa0
Dec 13 14:28:59 tvpc kernel: [ 1949.983761]  [<ffffffff8100cf24>] kernel_thread_helper+0x4/0x10
Dec 13 14:28:59 tvpc kernel: [ 1949.983765]  [<ffffffff81087bd0>] ? kthread+0x0/0xa0
Dec 13 14:28:59 tvpc kernel: [ 1949.983768]  [<ffffffff8100cf20>] ? kernel_thread_helper+0x0/0x10
Dec 13 14:28:59 tvpc kernel: [ 1949.983770] ---[ end trace 3c024082c235d59e ]---I was hoping that maybe someone could help me with that.

 **Original problem:**

]the computer has an Intel G41 chipset. Audio works fine with earphones, and on the tv when using Windows, but not on the tv when using Linux. The tv is connected with a HDMI cable.
I was thinking that I probably have the problem described in this post:

[http://www.phoronix.com/forums/showpost.php?p=151471&postcount=12](http://www.phoronix.com/forums/showpost.php?p=151471&postcount=12)

The post belongs to a thread that gives as a solution the patch described in this article:

[http://www.phoronix.com/scan.php?page=news_item&px=ODYyMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODYyMQ)

That patch is the reason for me to try the alpha. I was thinking that 2 months were enough for that patch to find its way to the kernel, but maybe I was wrong: I still get no audio.
Because of the previous problem it's a bit difficult for me to run an update, as I have no connection, so I'm basically stuck. I wanted to ask:

1) is that patch delivered with Ubuntu?[
2) if not, when will it be?

TIA

---

### Post by cariboo on 2010-12-13
According to the article you linked to, the patch should appear in the kernel were are using now, the only thing I can suggest is to check the changelogs, to see if support has been added.

---

### Post by go4linux on 2010-12-14
> **cariboo907 said:**
> According to the article you linked to, the patch should appear in the kernel were are using now, the only thing I can suggest is to check the changelogs, to see if support has been added.
I couldn't find a changelog with enough information, but at the end I thought I don't really need an internet connection on my machine to check it: I can download the source package from another machine.
Indeed the patch seems to be there. Now I have to figure out why I don't have audio. Could be a parameter in a module, or something else.

Maybe I'll stay with windows. What a terrible thought.

Thanks

---

### Post by ibizatunes on 2010-12-14
> Maybe I'll stay with windows. What a terrible thought.Are you using 11.04 as a production machine? as this is only alpha software!

---

### Post by go4linux on 2010-12-14
> **ibizatunes said:**
> Are you using 11.04 as a production machine? as this is only alpha software!
not really, it's just a multimedia computer connected to a tv. No special purposes besides movies and videos.
I know it's alpha, and it was not really my intention to use it, but I figured it was the only way to solve my audio problem. Apparently I was wrong

---

### Post by Reiger on 2010-12-14
The kernel oops/panic you get is a regression in the rt28* driver. Some older (Lucid, Maverick, early Natty) kernels do not exhibit the bug.

I think this is what GnomeUser ran into as well, I know I have (with a Linksys PCI card) but I do not have time to investigate it further. So your best bet is to grab an older kernel from some PPA or other repository and cross fingers.

---

### Post by go4linux on 2010-12-14
> **Reiger said:**
> The kernel oops/panic you get is a regression in the rt28* driver. Some older (Lucid, Maverick, early Natty) kernels do not exhibit the bug.

I think this is what GnomeUser ran into as well, I know I have (with a Linksys PCI card) but I do not have time to investigate it further. So your best bet is to grab an older kernel from some PPA or other repository and cross fingers.
Good to know, thanks. I guess it's one more reason to not use the alpha. Hopefully it will get better.

---

