---
title: "WinTv HVR 2250 suddenly broken"
date: 2011-07-20
forum: Mythbuntu
---

### Post by peteroschi on 2011-07-20
hi

since updating to mythbuntu 11.04, my wintv hvr2250 is not running anymore

dmesg | grep saa7164 gives:


```
[ 1288.671933] saa7164 0000:02:00.0: PCI INT A disabled
[ 1291.904931] saa7164 driver loaded
[ 1291.905147] saa7164 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 18 (level, low) -> IRQ 18
[ 1291.907571] CORE saa7164[0]: subsystem: 0070:8900, board: Hauppauge WinTV-HVR2200 [card=5,autodetected]
[ 1291.907590] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfa800000
[ 1291.907611] saa7164 0000:02:00.0: setting latency timer to 64
[ 1291.920045] saa7164_downloadfirmware() firmware corrupt
[ 1291.920062] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[ 1291.941363] saa7164_downloadfirmware() firmware read 4019072 bytes.
[ 1291.941373] saa7164_downloadfirmware() firmware loaded.
[ 1291.941405] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[ 1291.941418] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[ 1291.941425] saa7164_downloadfirmware() BSLSize = 0x0
[ 1291.941432] saa7164_downloadfirmware() Reserved = 0x0
[ 1291.941438] saa7164_downloadfirmware() Version = 0x1661c00
[ 1296.450049] saa7164_downloadimage() image corrupt
peter@oschimyth:~$ 

```

i downloaded already again from [http://www.steventoth.net](http://www.steventoth.net)
but it always gives me the failure mentioned above

it ran totally smoothly before the upgrade....
any ideas that could help?

thanks

peter

---

### Post by peteroschi on 2011-08-08
im i the only one with this problem?

any help?

peter

---

### Post by williammanda on 2011-08-12
Have you inquired at linuxtv.org about this?

---

### Post by astrahle on 2011-10-23
Mate, I'm having the same problem too. Mythbuntu 11.10 64 bit. Have tried 32 bit. Have tried compiling my own kernel off of 3.0.4 and using git repository as per below.
 
No good. It just doesn't like the NXP7164-2010-03-10.1.fw any more on ARCH 3.0. 
 
Can anyone help?
 
Ash.
 
 
 
Turns out that "git clone git://kernellabs.com/stoth/saa7164-stable.git" is meant to pull down a whole kernel.

I also discovered that after the above git clone is done, the files that are checked out from the downloaded git repository still didn't include a recent enough version of the saa7164 driver. To get the correct saa7164 source code files, I had to checkout a more recent commit from the downloaded git repository, ie I had to do 
git checkout 87e0c0378bf2068df5d0c43acd66aea9ba71bd89Many thanks to Steven Toth (driver author) for telling me about the "87e0c0378bf2068df5d0c43acd66aea9ba71bd89" commit.

Once I had the correct driver source code, I then installed the source code of my ubuntu kernel and replaced its saa7164 source code files (ie the files under the "src/linux-2.6.35/drivers/media/video/saa7164/" directory) with those from the above git commit and then recompiled the kernel. I found the following instructions at "[[COLOR=#284b72]http://linuxtweaking...buntu-1004.html[/COLOR]]("http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html")" for getting the ubuntu kernel source code and recompiling it most helpfull.

A cold reboot with the new kernel produced dmesg output that showed that the driver did indeed recognise the card :) However it also showed that it was looking for (and couldn't find) a "NXP7164-2010-03-10.1.fw" firmware file. I got it from [[COLOR=#284b72]http://www.steventot...2010-03-10.1.fw[/COLOR]]("http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw") and copied it into /lib/firmware/$(uname -r) and cold rebooted.

After that I just had to add the card's two adapters to Mythtv (via the backend settings gui) and it now seems to be working fine :) (though I have only just started using it, so the next few days might highlight more issues).

---

