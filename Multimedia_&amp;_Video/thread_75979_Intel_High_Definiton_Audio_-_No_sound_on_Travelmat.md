---
title: "Intel High Definiton Audio - No sound on Travelmate 3000"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by Muffe on 2005-10-14
Has anyone got the Intel High Definition Audio controller to work on Breezy? I have an Acer Travelmate 3000 running Ubuntu 5.10 Breezy, and I cannot get any sound. Her is some relevant debugging information:

lspci | grep Audio
```
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
```

lsmod | grep snd
```
snd_hda_intel          15872  0
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
```

dmesg | grep intel-hda
```
[   46.132105] hda-intel: unable to grab IRQ 0
```

It seems that the card is detected and the drivers loaded, but not finding he card. It might be something with that dmesg output... I dont actually know.

Can anyone help me? Thanks.

---

### Post by shenki on 2005-10-14
That dmsg output seems to be different to others I've seen (from my extensive googling and forum reading, in efforts to get my own intel HD audio equipped laptop working)

Here are some bugs relating to the Intel HD Audio driver, which it seems wasn't quite up to scratch in the kernel that breezy decided to go with:

[15465](http://bugzilla.ubuntu.com/show_bug.cgi?id=15465) Hotplug hangs on boot trying to load snd-hda-intel
[15031](http://bugzilla.ubuntu.com/show_bug.cgi?id=15031) ALC880 + Intel 915GM - ICH6 results in Kernel panic

The second bug has some promising links to patches for the kernel, and also a kernel .deb that has the patch itegrated. Didn't work for me, but give it a go.

---

### Post by LeTon on 2005-10-31
Hi, there
I'm also fighting over a sound issue with this sound card:(
All outputs are the same except I get nothing on dmesg | grep intel-hda!
I quite like ubuntu...with help of multiple how-tos got streaming videos and dvds working and all....
...and I am just stuck on the sound:(((( I have tried many how- tos, all the settings seem to be right....what else
If anyone out there would have at least some sort of idea?Please
It would so suck not to be able use this beautiful laptop up to its fullest:(
Asus Z33A-V
[http://usa.asus.com/products4.aspx?l1=5&l2=64&l3=0&model=606&modelmenu=1]("http://usa.asus.com/products4.aspx?l1=5&l2=64&l3=0&model=606&modelmenu=1")
P4-1.86
768 MB DDR2-400SDRAM
80GB Ultra DMA HDD 5400rpm


Thank you in advance

---

### Post by namru on 2005-11-01
Got no sound either on TM3004 WTMi.
I was wondering if a kernel update could be of any help? I read about the newly released 2.6.14. At least it has better support for ipw2200...

There was lots of sound fixes and a couple regarding Intel HDA but I'm not sure it is fully functional yet.

Here's the link to the changelog:
[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14)

---

### Post by namru on 2005-11-01
I (kind of) managed to get the sound working!

Both Intel HDA(alsa) and SigmaTel SCAT9200(oss mixer) are recognised, but there is  something wrong with the sound. At the login screen, a sort of jungle-drum starts and repeats endlessly. Anyway, the first sound I've heard on ubuntu on this laptop.

Also, batterystatus works, CPU scaling works, (it scaled down to 800Mhz) But now no network connection is possible! Also my usb-mouse is really slow now. weird.

I did this:
-downloaded and installed the intel compiler.
-downloaded and compiled ACER-Travelmate_3002_WTMi-3C18-custom.asl.gz
-copied the compiled DSDT.aml to /etc/mkinitramfs/
-booted with noapic nolapic instead of acpi=off

any suggestions on how to get sound and acpi and network running on same boot parameters?

---

