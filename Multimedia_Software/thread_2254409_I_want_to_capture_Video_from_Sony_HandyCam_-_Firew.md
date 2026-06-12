---
title: "I want to capture Video from Sony HandyCam - Firewire - need new Kernel?"
date: 2014-11-27
forum: Multimedia Software
---

### Post by troy7 on 2014-11-27
Hello,

I have Xubuntu 12.04.  I have been trying for quite some time to capture video from my Sony HandyCam via Firewire.  

Looks like my firewire card is recognized during boot - lspci | grep 1394 shows 05:05.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller.  

I am using kino - and it says 'No AV/C compliant cam connected or not switched on'.  

From reading I've been doing on the web, I've read the Xubuntu kernel doesn't have 1394 support compiled in.  So, I thought I'd take a crack at making a new kernel.  I haven't done this since version 1.xxx, so I'm seeing quite a few new things.  I believe I have the linux-3.2.0 source downloaded and extracted; however, when I navigate the menus and get to drivers, I was expecting to see something like '1394 video' or the like - then I was planning on enabling it and making a kernel - didn't see that.  I got the source code with the command apt-get source linux-image-$(uname -r)  Perhaps this kernel source code doesn't contain the 1394 driver?

I see I can also get kernel source code from [https://www.kernel.org/](https://www.kernel.org/) - I haven't gone down this path yet.

Looking for some guidance:  Am I on the right path?  Do I need to get my kernal source code from the kernel.org web page for 1394 support?  Thanks.

---

### Post by carl4926 on 2014-11-27
Might be worth just checking with VLC Capture that your device is not visible

---

### Post by troy7 on 2014-11-27
VLC has same problems.

Also checked into kernal - no difference in module availability between what I got and the latest.

I am looking at a tail of dmesg - see this (from a fresh plugin of my video camera):

[  361.172104] Call Trace:
[  361.172118]  [<ffffffff8166266f>] schedule+0x3f/0x60
[  361.172125]  [<ffffffff81662cad>] schedule_timeout+0x29d/0x310
[  361.172137]  [<ffffffffa0c1d583>] ? at_context_queue_packet+0x203/0x370 [firewire_ohci]
[  361.172147]  [<ffffffff816624af>] wait_for_common+0xdf/0x180
[  361.172156]  [<ffffffff81060aa0>] ? try_to_wake_up+0x200/0x200
[  361.172163]  [<ffffffff8166262d>] wait_for_completion+0x1d/0x20
[  361.172175]  [<ffffffffa0c88e0a>] fw_run_transaction+0xea/0x120 [firewire_core]
[  361.172186]  [<ffffffffa0c88b60>] ? transmit_phy_packet_callback+0x20/0x20 [firewire_core]
[  361.172196]  [<ffffffff81068d00>] ? console_unlock+0x80/0x180
[  361.172206]  [<ffffffffa0c882f0>] ? fw_core_add_address_handler+0x160/0x160 [firewire_core]
[  361.172217]  [<ffffffffa0c88e40>] ? fw_run_transaction+0x120/0x120 [firewire_core]
[  361.172227]  [<ffffffffa0c88b60>] ? transmit_phy_packet_callback+0x20/0x20 [firewire_core]
[  361.172238]  [<ffffffffa0c85698>] read_rom+0x68/0xa0 [firewire_core]
[  361.172248]  [<ffffffffa0c8579d>] read_config_rom+0xcd/0x4d0 [firewire_core]
[  361.172259]  [<ffffffffa0c86585>] fw_device_init+0x35/0x350 [firewire_core]
[  361.172268]  [<ffffffff81085fcc>] process_one_work+0x12c/0x470
[  361.172276]  [<ffffffff810870e4>] worker_thread+0x164/0x370
[  361.172284]  [<ffffffff81086f80>] ? manage_workers.isra.31+0x130/0x130
[  361.172291]  [<ffffffff8108b95c>] kthread+0x8c/0xa0
[  361.172300]  [<ffffffff8166ee34>] kernel_thread_helper+0x4/0x10
[  361.172308]  [<ffffffff8108b8d0>] ? flush_kthread_worker+0xa0/0xa0
[  361.172315]  [<ffffffff8166ee30>] ? gs_change+0x13/0x13
[  453.096231] firewire_core: skipped bus generations, destroying all nodes
[  453.596030] firewire_core: rediscovered device fw0
[  456.104070] firewire_core: giving up on config rom for node id ffc0
[  458.250028] firewire_ohci: node ID not valid, new bus reset in progress
[  458.359626] firewire_core: skipped bus generations, destroying all nodes
[  458.856077] firewire_core: rediscovered device fw0
[  458.856112] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  458.856199] firewire_ohci: node ID not valid, new bus reset in progress
[~]>

Has stopped - that is, no more messages after what I posted.

---

### Post by carl4926 on 2014-11-27
> [COLOR=#000000]From reading I've been doing on the web, I've read the Xubuntu kernel doesn't have 1394 support compiled in[/COLOR]
I can't confirm if that is correct
But what you say is a bit vague - I mean you didn't provide a ref
Did your reading lead you to a solution?
If it's in the kernel, what if you boot the latest 14.10 live - is that any different?

---

### Post by troy7 on 2014-11-27
I should of been more clear - doesn't have 1394video 'built in'.

I can't remember the source, but what I was working on when reading that is looking at /etc/modprobe.d/blacklist-firewire.conf

# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2

So, what I got from this and reading on the web is there is a 'old' and 'new' set of 1394 drivers (modules).  I had two references conflicting - but from experimenting, you can't have both modules enabled in that only one will be functional and you're not guarenteed which one it will be.  Also, if you remove the #'s from the beginning of the bottom two - you then add #'s to the top four.  There's then a modprobe command to enable - or you can just reboot.  I tried both, but never got an /etc/raw1394 driver (automatically) made.  I have a fair amount of confidence of the influence of the change since the newer drivers disappeared.

My hunch is the lack of the old drivers appearing is due to the kernal modules availabe for drivers/1394 when the kernel is built.

The oldest Ubuntu I could find is version 10-something.  I was going to try a live boot from the CD and see what drivers become available.

I don't think I will find anything changed going newer.

---

### Post by troy7 on 2014-12-31
I solved my issue by making my system a dual boot:  Win7 and Ubuntu 14.04.  One note is I had to install an older version of MovieMaker - see [http://dungeonworks.blogspot.com/2012/10/sorry-movie-maker-cant-start-problem.html](http://dungeonworks.blogspot.com/2012/10/sorry-movie-maker-cant-start-problem.html).  After capture I use VDub to break it up (still a windows program), but then use ffmpeg (not called aconv) with a graphical WinFF front end to compress into something reasonable to backup on DVD and a spare hard disk.

---

