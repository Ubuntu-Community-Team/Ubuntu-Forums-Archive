---
title: "Using modprobe"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by kammce on 2010-01-31
[SIZE=3]I have been using 'modprobe' a while now (at least a half a year now) to insert 'ndiswrapper' into my computer's kernel. I figured out how to get it to work 95% of the time (use root besides sudo. Root reacts faster making the insertion go faster and smoother). I have even figured out how to save my computer from crashing if 'ndiswrapper' quits out (remove 'ndiswrapper' from the kernel and it will either restart or kill the process. Killing it will make you have to restart your computer to get 'ndiswrapper' to work again... Oh yeah, if you did not know, ndiswrapper will crash your computer if dies. For some reason, my computer does something different once 'ndiswrapper' dies). But I have never been able to remove or re-insert 'ndiswrapper' from the kernel after it was **killed** the first time I tried inserting it into the kernel. I am wondering if anyone has been able to do so. It is not an emergency but it gets annoying having to reboot my computer to get the wifi to work when my computer does not feel the need to do what I want it to do. (Its a good thing I don't have windows or I would have to wait a pretty long time.)[/SIZE]

---

### Post by kammce on 2010-02-04
stilled need a reply

---

### Post by adam814 on 2010-02-05
Out of curiosity what wifi card are you using?  If you can get it working at all with a native driver it'll solve that problem and it'll be more stable (and probably faster).

---

### Post by kammce on 2010-02-05
[FONT=Lucida Console][SIZE=3]I am using the Netgear WG311v3 PCI wifi card. I can not seem to find any native drivers for it on the web. I find is how to use ndiswrapper to run it. This is less about my wifi card but more about being able to remove a module when it inserts itself then it kills over. When I use "lsmod", ndiswrapper gets a used by number of 1 besides it's normal 0. I can't remove it because it is in use. I have tried 'modprobe -r ndiswrapper' and 'rmmod ndiswrapper' and neither work. They just stall out or tell me that ndiswrapper is in use. I have tried forcing them out but that does not work. But I recently took a really close look at my kernal log and saw something strange. it said:

[/SIZE][/FONT][FONT=Lucida Console][SIZE=3]```

Feb  4 17:18:48 KhalilServer kernel: [  126.557435] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Feb  4 17:18:48 KhalilServer kernel: [  126.602929] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
Feb  4 17:18:48 KhalilServer kernel: [  126.604152] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
Feb  4 17:18:48 KhalilServer kernel: [  126.605032] ndiswrapper: using IRQ 16
Feb  4 17:18:48 KhalilServer kernel: [  126.678033] Modules linked in: ndiswrapper binfmt_misc rfcomm l2cap bluetooth ppdev vmnet vmblock i915 drm vsock vmci vmmon ipv6 acpi_cpufreq cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table cpufreq_userspace cpufreq_powersave container dock sbs sbshc video output battery iptable_filter ip_tables x_tables aes_x86_64 dm_crypt dm_mod ac visor usbserial lp loop snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event psmouse snd_seq snd_timer snd_seq_device serio_raw parport_pc parport button snd iTCO_wdt iTCO_vendor_support pcspkr shpchp pci_hotplug intel_agp evdev soundcore ext3 jbd mbcache sg sd_mod sr_mod cdrom ata_generic pata_acpi ata_piix libata scsi_mod ehci_hcd r8169 uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse

```

The part where it states "Modules linked in:" is the wierd part. From this i assume that ndiswrapper made a link to every kernel module in the kernel when it was killed, keeping me from removing it. Normally it only depends on 'Usbcore', and if it is not killed then it is only linked to 'usbcore' but i would still be able to remove it if it killes over after a while. 

Basically, what I have come up with, is that you have to kill every module in the kernel inorder to get another chance to re-insert it.

I am hoping that someone more experieced can verife this or maybe give me a solution.
[/SIZE][/FONT]

---

### Post by amsterdamharu on 2010-02-05
It says on help pages that no native driver is available:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

> WifiDocs/Device/Netgear_WG311_v3  (last edited 2009-06-06 16:22:29 by [Gavesh]("https://launchpad.net/%7Eygavesh"))

I guess you can try to see if that page contains any tips you haven't tried yet

---

### Post by adam814 on 2010-02-05
I don't think that necessarily means ndiswrapper links to every module on the system.  I get pretty similar output on my system and I can pull the "iwlagn" driver (my wifi driver) without any problems.

---

### Post by kammce on 2010-02-05
You might be right. I just upgraded from ndiswrapper 1.9 (One of the oldest versions out there) and went to 1.55. I have not tried (purposely) to remove ndiswrapper after it has been killed. Provided that I still get the killed message from ndiswrapper 1.55.

---

### Post by kammce on 2010-02-12
Alright. I still have this problem... Sometimes. I figured out the real issue. Ndiswrapper stops responding when I insert it into the kernel. I have tried forcing it to upload it's self and it ends up not responding on upload. The problem is ndiswrapper trying to run my wifi drivers. Without my card in my computer, ndiswrapper inserts itself into my kernel 99.999999% of the time, and uploads completely everytime!

 I am really just looking for a way to remove ndiswrapper from my kernel when it stops responding.

---

