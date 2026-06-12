---
title: "[SOLVED] Adding lirc_pvr150 module = system hard lock"
date: 2007-10-23
forum: Mythbuntu
---

### Post by Akriss on 2007-10-23
**[COLOR="Red"]OK its been solved![/COLOR]**

Follow the quotes :)

> **superm1 said:**
> Akriss,

Okay I've got the patch built on a PPA.

Add this deb line into Applications->System->Software Sources->Third Party Sources (or to your /etc/apt/sources.list).

```
deb     http://ppa.launchpad.net/superm1/ubuntu gutsy main restricted universe multiverse
```Update your package lists and a new linux-ubuntu-modules should be available.

> **Akriss said:**
> Done. . Works well now. 

Added the module update. . Then added lirc from packet manager.  Added ONLY &#8220;lirc_pvr150&#8221; to &#8220;MODULES&#8221; line in hardware.conf, added my blaster code set to &#8220;lircd.conf&#8221; and moved &#8220;haup-ir-blaster.bin&#8221; to &#8220;/lib/firmware/

Receives and send ir as intended.
[COLOR="Red"]________End of Fix_______[/COLOR]

I &#8216;am trying to get my pvr-150 blaster to work in Gusty and/or Mythbuntu but it&#8217;s giving me grief. 

I have installed the &#8220;lirc&#8221; and &#8220;lirc-modules-source&#8221; from the package manager. And Choose the Hauppauge tv card when asked. Then I opened &#8220;/etc/lirc/hardware.conf&#8221; and Modify the &#8220;MODULES&#8221; line from &#8220; MODULES="lirc_dev lirc_i2c" &#8220; to &#8220;MODULES="lirc_dev lirc_pvr150 lirc_i2c" &#8220; adding the prv150 to be loaded. Then I download the firmware &#8220;haup-ir-blaster.bin&#8221; and move it to &#8220;/lib/firmware/&#8221; and confirm its there. 

Now here is where the fun begins. If I reboot or &#8220;sudo /etc/init.d/lirc restart&#8221; the system hard locks. The only way I can boot the system to normal mode is to rename &#8220;/etc/lirc/lircd.conf&#8221; (--OR--) to edit &#8220;/etc/lirc/hardware.conf&#8221; and remove &#8220;lirc_pvr150&#8221; from the &#8220;MODULES&#8221; line. 

I have tried editing &#8220;/etc/lirc/hardware.conf&#8221; and the &#8220;MODULES&#8221; line to just &#8220;MODULES="lirc_pvr150" &#8220; and it still hard locks.

This is all from a fresh install of Gusty or Mythbuntu RC.

This is from my /var/log/messages, with the lirc_pvr150 in the modules line of hardware.conf and no lircd.conf file:
```
 Oct 22 22:57:30 ubuntu kernel: [   46.516840] ivtv:  ==================== START INIT IVTV ====================
Oct 22 22:57:30 ubuntu kernel: [   46.516845] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
Oct 22 22:57:30 ubuntu kernel: [   46.516971] ivtv0: Autodetected Hauppauge card (cx23416 based)
Oct 22 22:57:30 ubuntu kernel: [   46.517215] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Oct 22 22:57:30 ubuntu kernel: [   46.517225] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 21
Oct 22 22:57:30 ubuntu kernel: [   46.517238] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Oct 22 22:57:30 ubuntu kernel: [   46.578274] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
Oct 22 22:57:30 ubuntu kernel: [   46.578280] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 (level, high) -> IRQ 18
Oct 22 22:57:30 ubuntu kernel: [   46.900604] intel8x0_measure_ac97_clock: measured 52793 usecs
Oct 22 22:57:30 ubuntu kernel: [   46.900610] intel8x0: clocking to 48000
Oct 22 22:57:30 ubuntu kernel: [   47.208450] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4158612376 bytes)
Oct 22 22:57:30 ubuntu kernel: [   47.424328] ivtv0: Encoder revision: 0x02050032
Oct 22 22:57:30 ubuntu kernel: [   47.424332] ivtv0: Recommended firmware version is 0x02060039.
Oct 22 22:57:30 ubuntu kernel: [   47.484674] tveeprom 2-0050: Hauppauge model 26032, rev C199, serial# 8359175
Oct 22 22:57:30 ubuntu- kernel: [   47.484680] tveeprom 2-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
Oct 22 22:57:30 ubuntu kernel: [   47.484683] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
Oct 22 22:57:30 ubuntu kernel: [   47.484686] tveeprom 2-0050: audio processor is CX25841 (idx 35)
Oct 22 22:57:30 ubuntu kernel: [   47.484689] tveeprom 2-0050: decoder processor is CX25841 (idx 28)
Oct 22 22:57:30 ubuntu kernel: [   47.484692] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
Oct 22 22:57:30 ubuntu kernel: [   47.484695] ivtv0: Autodetected Hauppauge WinTV PVR-150
Oct 22 22:57:30 ubuntu kernel: [   47.484698] ivtv0: reopen i2c bus for IR-blaster support
Oct 22 22:57:30 ubuntu kernel: [   47.576126] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Oct 22 22:57:30 ubuntu kernel: [   47.791103] cx25840 2-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
Oct 22 22:57:30 ubuntu kernel: [   52.102889] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Oct 22 22:57:30 ubuntu kernel: [   52.218192] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
Oct 22 22:57:30 ubuntu kernel: [   52.275914] tuner 2-0061: type set to 50 (TCL 2002N)
Oct 22 22:57:30 ubuntu kernel: [   52.611960] ivtv0: Registered device video0 for encoder MPEG (4 MB)
Oct 22 22:57:30 ubuntu kernel: [   52.612254] ivtv0: Registered device video32 for encoder YUV (2 MB)
Oct 22 22:57:30 ubuntu kernel: [   52.612547] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
Oct 22 22:57:30 ubuntu kernel: [   52.612752] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
Oct 22 22:57:30 ubuntu kernel: [   52.640505] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
Oct 22 22:57:30 ubuntu kernel: [   52.640646] ivtv:  ====================  END INIT IVTV  ====================
 
```

If any of that info helps.

I am stuck at this point need some advise please.:confused:

---

### Post by superm1 on 2007-10-23
Rather than both lirc_i2c and lirc_pvr150:

can you try with just lirc_pvr150 in the MODULES= line?

---

### Post by Akriss on 2007-10-23
Yes I have tryed that as well. 

from above :)
> I have tried editing &#8220;/etc/lirc/hardware.conf&#8221; and the &#8220;MODULES&#8221; line to just &#8220;MODULES="lirc_pvr150" &#8220; and it still hard locks. 

and tryed again just now to be sure :p

---

### Post by superm1 on 2007-10-23
Well that's not good.  I'm wondering if perhaps the lirc_pvr150 author hasn't made this module compatible with 2.6.22.  You may very well be the first person actually testing it on Gutsy (which would be rather unfortunate).  Lets see if you can narrow this down a little further.

rmmod all lirc modules.  

Hit ctrl alt f1 to switch to virtual terminal 1.

login here.

From here modprobe lirc_pvr150.

See if you get some kernel backtrace here about what is happening.

---

### Post by Akriss on 2007-10-23
$modprobe lirc_pvr150
```
 WARNING Error inserting lirc_dev (/lib/modules/2/6/22-14-generic/ubuntu/media/lirc/lirc_dev/lirc_dev.ko) Operation not permitted
WARNING Error inserting lirc_pvr150 (/lib/modules/2/6/22-14-generic/ubuntu/media/lirc/lirc_pvr150/lirc_pvr150.ko) Operation not permitted
```

And a $sudo modprobe lirc_pvr150, hard locks.
And that with just lirc_pvr150 in the module line.
:confused:

---

### Post by superm1 on 2007-10-23
Sorry should have been more specific

```
sudo modprobe lirc_pvr150
```

---

### Post by Akriss on 2007-10-23
LOL 
I edited my post as you posted.

I tryed it hard locked. =/

---

### Post by Akriss on 2007-10-23
After Google'n around for a few hours looking for tips, I came upon the answer on "Mark's Braindump" page.

[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

He has a patched lirc for the  hauppauge pvr 150 blaster and kernel's >2.6.16.

Works like a champ.

---

### Post by superm1 on 2007-10-24
> **Akriss said:**
> After Google'n around for a few hours looking for tips, I came upon the answer on "Mark's Braindump" page.

[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

He has a patched lirc for the  hauppauge pvr 150 blaster and kernel's >2.6.16.

Works like a champ.
I checked with the kernel team.  Considering the severity of this crash, they'll be willing to accept a stable release update for this kernel module.  

So if I attempt to prepare a diff between the latest posted on Mark's site and our current kernel module, and post a deb, would you be willing to revert your changes temporarily to test it so that we can fix this for everyone?

Thanks

---

### Post by Akriss on 2007-10-24
Yes I am willing to help out. 

I have been doing the installs on a spare HD till I get all the kinks sorted out and then will move it to the production HD when all is working well.

---

### Post by superm1 on 2007-10-24
Akriss,

Okay I've got the patch built on a PPA.

Add this deb line into Applications->System->Software Sources->Third Party Sources (or to your /etc/apt/sources.list).

```
deb     http://ppa.launchpad.net/superm1/ubuntu gutsy main restricted universe multiverse
```Update your package lists and a new linux-ubuntu-modules should be available.

---

### Post by Akriss on 2007-10-24
Done. . Works well now. 

Added the module update. . Then added lirc from packet manager.  Added ONLY &#8220;lirc_pvr150&#8221; to &#8220;MODULES&#8221; line in hardware.conf, added my blaster code set to &#8220;lircd.conf&#8221; and moved &#8220;haup-ir-blaster.bin&#8221; to &#8220;/lib/firmware/

Receives and send ir as intended.

---

### Post by BatPenguin on 2007-10-27
> **Akriss said:**
> Done. . Works well now. 

Added the module update. . Then added lirc from packet manager.  Added ONLY “lirc_pvr150” to “MODULES” line in hardware.conf, added my blaster code set to “lircd.conf” and moved “haup-ir-blaster.bin” to “/lib/firmware/

Receives and send ir as intended.

Great to see I'm not the only one with the PVR-150. I had the IR blaster in it going nicely in Edgy but now I'm having problems with this in Gutsy.

I don't have lock-ups but it seems like nothing happens when I "sudo modprobe lirc_pvr150". No messages in syslog or /var/log/messages, kooks like the module loads and...does nothing.  My channel change scripts don't work. .before I start posting more detailed logs etc. here, could you please clarify whether you used the patched LIRC from the Mark's Braindump or just the basic gutsy packages? From the above post I gather that you just installed the module update and then Synaptic -> Lirc and that's it. Is this correct? No custom Lirc from that page?

I added the module update repo line but for some reason I still see the update even after I install it. Strange...but I presume it's installed, I don't know if this could be the problem for me.

---

### Post by BatPenguin on 2007-10-27
OK, looks like I got it. Removed everything, reinstalled the  Mark's Braindump version, and it works now after a reboot.

---

### Post by superm1 on 2007-10-28
> **BatPenguin said:**
> OK, looks like I got it. Removed everything, reinstalled the  Mark's Braindump version, and it works now after a reboot.
This is disconcerting.  Did the updated package from my PPA not work? (That is what should be pushed out to stable release updates in the near future)

---

### Post by BatPenguin on 2007-10-29
Oh, OK -- well, in that case, I'd be happy to remove it all and try again later tonight - I'll get back to you. I think I might've omitted a reboot at some point, so lemme try this again. I'll reboot after removing the current version and after installing the new one before trying, that should probably be the safest way to make sure everything is OK and the modules loaded properly. That might've had something to do with my previous failure.

I'll let you know how it goes this time. Since I'm the only one reporting problems, I'd be inclined to believe it's a case of me messing up but we'll see. I'll report back hopefully already today.

---

### Post by yfaykya on 2007-10-29
Just to say it works for me with a BSkyB STB using only the firmware from Marks page (mythbuntu lirc) . Is there anyway of getting the f/w bundled as well so there would be one less step?

---

### Post by superm1 on 2007-10-29
> **yfaykya said:**
> Just to say it works for me with a BSkyB STB using only the firmware from Marks page (mythbuntu lirc) . Is there anyway of getting the f/w bundled as well so there would be one less step?
licensing is the issue on that firmware.  There is none listed.

---

### Post by OffAxis on 2007-10-29
same here; I can't get the channel changing script to work at all.
I've added the ppa line to my sources.list file, it recognizes the new package and I confirm installation, but it doesn't seem to take.
 
Here's my apt-get upgrade:

```
The following packages will be upgraded:
  linux-ubuntu-modules-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3873kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  linux-ubuntu-modules-2.6.22-14-generic
Install these packages without verification [y/N]? y
(Reading database ... 60551 files and directories currently installed.)
Preparing to replace linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.40~ppa1 (using .../linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40~ppa1_amd64.deb) ...
Unpacking replacement linux-ubuntu-modules-2.6.22-14-generic ...
Setting up linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.40~ppa1) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

```

This is an AMD 64-bit system with a PVR-150 w/integrated receiver/blaster, on a mythbuntu iso.

I've followed Akriss' earlier synopsis...only I've never installed the module from mark's braindump, just the haup-ir-blaster.bin to /lib/firmware/.

---

### Post by superm1 on 2007-10-29
> **OffAxis said:**
> same here; I can't get the channel changing script to work at all.
I've added the ppa line to my sources.list file, it recognizes the new package and I confirm installation, but it doesn't seem to take.
 
Here's my apt-get upgrade:

```
The following packages will be upgraded:
  linux-ubuntu-modules-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3873kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  linux-ubuntu-modules-2.6.22-14-generic
Install these packages without verification [y/N]? y
(Reading database ... 60551 files and directories currently installed.)
Preparing to replace linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.40~ppa1 (using .../linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40~ppa1_amd64.deb) ...
Unpacking replacement linux-ubuntu-modules-2.6.22-14-generic ...
Setting up linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.40~ppa1) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

```This is an AMD 64-bit system with a PVR-150 w/integrated receiver/blaster, on a mythbuntu iso.

I've followed Akriss' earlier synopsis...only I've never installed the module from mark's braindump, just the haup-ir-blaster.bin to /lib/firmware/.
The only thing that my fixed package will do is fix the kernel module preventing a freeze.  Does this happen for you?

You still need the firmware and such.

---

### Post by BatPenguin on 2007-10-29
OK, looks like the new module version works for me as well. Must've been my bad previously.

Now I installed that module version and then intalled LIRC from Synaptic,  and this seems to be working fine. Maybe it was something about not rebooting before, I don't know, but looks good now. I never had the lockups anyway, just problems getting it working.

In any case, there's a strange behavior that wasn't there before - now I see the Update Manager notificiation for updates constantly, and it keeps showing this module update even though it's installed. If I click to install it again, it does, but the notification remains. It says:

linux-ubuntu-modules-2.6.22-14-generic
From version 2.6.22-14.40~ppa1 to 2.6.22-14.40~ppa1 

so from and to versions are the same...and still the notification remains. Any ideas why?

---

### Post by OffAxis on 2007-10-29
ah. I thought the update was required to get the module working properly.
I never had lockups, but having added the line, it now constantly shows as an update.

---

### Post by superm1 on 2007-10-29
I've seen that happen in the past with packages, but no idea why.  You can just disable the PPA for now, the package will remain until the new version from the SRU.

---

### Post by OffAxis on 2007-10-29
can do.
Thanks for the clarification.

---

### Post by ptipton on 2007-10-30
I am also having problems with getting the pvr150 blaster to work. I upgraded to mythbuntu gutsy from a fully working feisty mythtv setup. Everything went fine in the upgrade except the blaster no longer works. Now mythtvbackend log gives a "irsend  could not connect to socket  irsend :no such file or directory" errors when I try and change channels.
I a little confused as to whether I need to have  " module="lirc_pvr150" in hardware.conf or not. Tried with and without and doesn't seem to make any difference. Am also wondering whether I should be using the modified lirc from Marks Braindump or whether the lirc in Gutsy is ok?
Any help much appreciated.

---

### Post by Akriss on 2007-10-30
ptipton,

If you follow post 11 & 12 in this thead you should be golden. :)

---

### Post by superm1 on 2007-10-30
> **Akriss said:**
> ptipton,

If you follow post 11 & 12 in this thead you should be golden. :)
Would you mind updating your first post to reflect the proper procedure to follow?

---

### Post by Akriss on 2007-10-30
> **superm1 said:**
> Would you mind updating your first post to reflect the proper procedure to follow?

I did a quickie edit to the firts post ;)

---

### Post by ptipton on 2007-10-31
Akriss, Superm1- worked a treat, many thanks for the fix.

---

### Post by mirak63 on 2007-11-03
thanks for the fix, I experienced this very bad freeze too.

there are to many bugs and regressions in gutsy ...

---

### Post by superm1 on 2007-11-03
This is why we need people with this hardware to test it before the release comes out :)

The kernel guys have been putting off doing an update for linux-ubuntu-modules, but last I spoke, the patch on my PPA will be included.

For hardy, can at least one of you upgrade around beta time on one of your boxes, or at least test a live disk?  We can prevent stuff like this from happening.

---

### Post by Trimble Epic on 2007-11-04
> **superm1 said:**
>   You may very well be the first person actually testing it on Gutsy (which would be rather unfortunate).  

Hey, I was testing this back when the 7.10 iso was first posted, and I asked you about it in the IRC, Sm1.

Glad someone else took the reigns on this, I don't have enough Linux experience yet to have done the testing that Akriss did.  I am thankful.

I'm away from my box for a few weeks, so I'll have to wait before I can dig into this.  I sure wish I saw this thread before I left the house, or I would have finally been able to set it to record stuff off my dish network receiver... :(   good thing most of my shows can be bit-torrented... 

Thanks for solving this, guys!

---

### Post by greg963 on 2007-11-06
I had the same issue and I have gotten the lirc_pvr150 module loaded ok using the ~ppa kernel modules (bty amd64) but I am getting:

greg@gmythtv1:~$ sudo /usr/sbin/lircd -n --device=/dev/lirc/0 --output=/dev/lircd --pidfile=/var/run/lircd0 /etc/lircd.conf
lircd-0.8.2[13144]: error in configfile line 84:
lircd-0.8.2[13144]: "2156396544": must be a valid (lirc_t) number
lircd-0.8.2[13144]: reading of config file failed
lircd-0.8.2[13144]: lircd(userspace) ready
lircd-0.8.2[13144]: caught signal


/etc/lircd.conf
-----snip
begin remote

  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0

  begin raw_codes
    name 0
    2156396544 ------>line 84
    name 1
    2156396545
    name 2
    2156396546
    name 3
    2156396547
    name 4
    2156396548
    name 5
    2156396549
    name 6
    2156396550
    name 7
    2156396551
    name 8
    2156396552
    name 9
    2156396553
    name POWER
    2156396554
    name CH_UP
    2156396559
    name CH_DOWN
    2156396560
    name MUTE
    2156396561
    name VOL_DOWN
    2156396562
    name CH_PREVIOUS
    2156396563
    name VOL_UP
    2156396564
    name DISPLAY
    2156396565
    name EXIT
    2156396568
    name GUIDE
    2156396571
    name SAT
    2156396586
    name MENU
    2156396591
    name MUP
    2156396592
    name MDOWN
    2156396593
    name MLEFT
    2156396594
    name MRIGHT
    2156396595

  end raw_codes

  end remote
greg@gmythtv1:~$ 

I am using the lircd from the repo's lirc package.  I am going to try compiling the version from Mark's Braindump but last time I tried that it made my ati usb remote unable to communicate with liblircclient. I was hoping this would get both working.

Also the lircd.conf works if I recompile lirc_pvr150 and lircd from the Mark's Braindump lirc version.

---

### Post by superm1 on 2007-11-06
Did you save this with some sort of editor that would add windows line endings?

There are *NO* patches to the lirc executable on mark's website.  His patches are just to create the lirc_pvr150 module, which is already provided here by the ppa package.

---

### Post by greg963 on 2007-11-07
no, I used vi and the file has not changed since I upgraded from feisty,  I was able to get it to work (sort of) by completely removing the lirc package and the kernel modules and rebuilding from this source - [http://www.blushingpenguin.com/mark/lmilk/lirc-0.8.3-CVS-pvr150.tar.bz2](http://www.blushingpenguin.com/mark/lmilk/lirc-0.8.3-CVS-pvr150.tar.bz2)  from - [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

Using this source I followed the instructions on the previous link for lirc_pvr150 module and then ran it a second time for the lirc_atiusb module.  This gave me a version of lircd in /usr/local/sbin and the irxxxx commands in /usr/local/bin so I modified the lirc init script accordingly (following the general instructions laid out in lirc how to for multiple devices) and created three instances of lircd to run, one for lirc_atiusb one for each of my two pvr150's.  It now works if I reboot the machine but for some reason the ati remote stops working (irw works but no response in mythtv) when I reload lirc (/etc/init.d/lirc restart).

greg@gmythtv1:~$ ps -ax | grep lirc
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 4302 ?        S      0:00 [lirc_pvr150]
 4346 ?        S      0:00 [lirc_pvr150]
 6090 ?        Ss     0:00 /usr/local/sbin/lircd --device=/dev/lirc/0 --output=/dev/lircd --pidfile=/var/run/lircd0
 6100 ?        Ss     0:03 /usr/local/sbin/lircd --device=/dev/lirc/1 --output=/dev/lircd1 --pidfile=/var/run/lircd1
 6102 ?        Ss     0:02 /usr/local/sbin/lircd --device=/dev/lirc/2 --output=/dev/lircd2 --pidfile=/var/run/lircd2
greg@gmythtv1:~$

also /etc/lircd.conf is linked to /etc/lirc/lircd.conf to use the default location and /dev/lirc/0 is the ati_remote.

At any rate its working on boot now, so I should be able to work things out from there but the lirc kernel modules do seem to have some issues.

---

### Post by mandyfester on 2007-12-06
Hi 

I just tried to follow the instructions and got the remote control working. However the next boot Ubuntu reported that it could not find the lirc_pvr150 module. I removed lirc and now after each boot Ubuntu reports it cannot configure my graphics card and I no longer can get a network connection or much else in fact, usb devices and hardware are disabled. 

Any solutions please before I am forced to do a reinstall?

Thanks

Andy

---

### Post by mandyfester on 2007-12-10
After a fresh reinstall and following the instructions in this thread lirc in working.

---

### Post by rswartze on 2008-01-09
Thread Folk,

Thanks for your help here.  I followed the solution and I'm to what I believe to be an easy problem to solve...except I can't get it.

I used the new module for lirc_pvr150 and don't have any more lockup problems.  I'm running 2 pvr150's but have not configured lirc for both, I'm letting it default to /dev/lirc0.  The one pvr150 I tried did receive commands from the remote...GOOD.

But, I get the message "unknown remote: blaster" when I try to change channels (comand line testing).  I'm using the standard change_channel.pl script.  I have put the 'blaster' remote into /etc/lirc/lircd.conf but it doesn't seem to find it after kill -HUP.  The standard script should use /dev/lircd as the device, so I don't need to explicitly set one right?

I used to have the 'does not support' sending problem, then the lockup problem with lirc_pvr150, but both of those are gone, now it just won't use my lircd.conf.  It's like I'm not editing the right file and it's using some config file from who-knows-where.  lirc_pvr150 is the only module I have in /etc/lirc/hardware.conf.

I've previously had a single pvr150 and the blaster workiing with the change_channel.pl script and this same 'blaster' remote configuration in knoppmyth.  

Here are my questions:
1. What lircd.conf file is used by my lircd?
2. Do I need the lirc_12c module in /etc/lirc/hardware.conf?
3. The default /etc/lirc/hardware.conf had a file 'hauppauge/lirc.conf.hauppage' listed?  Not present in /etc/lirc/.  Where is this??
4. I changed #3 to reference "/etc/lirc/lircd.conf", but it changed nothing.
5. What are the .lircrc files in the home directories and does this have something to do with my problem?
6. Is my problem related to only running one instance of lircd (I don't think so).

Much thanks to anyone who can help here,

---

### Post by superm1 on 2008-01-11
> **rswartze said:**
> Thread Folk,
<snip>
Here are my questions:
1. What lircd.conf file is used by my lircd?

/etc/lirc/lircd.conf
> 
2. Do I need the lirc_12c module in /etc/lirc/hardware.conf?

For lirc_pvr150 module, you do not.need to also list the i2c module (matter of fact it can cause troubles)
> 
3. The default /etc/lirc/hardware.conf had a file 'hauppauge/lirc.conf.hauppage' listed?  Not present in /etc/lirc/.  Where is this??

This is used internally by the maintainer scripts to copy the file to /etc/lirc/lircd.conf.  That should be the same file as /usr/share/lirc/remotes/hauppauge/lirc.conf.hauppauge
> 
4. I changed #3 to reference "/etc/lirc/lircd.conf", but it changed nothing.

This won't affect anything visibly to you until next time lirc is reconfigured (which will likely be hardy).  Things wrg to lirc have changed a LOT in hardy though, so you will have to reconfigure then probably anyway.
> 
5. What are the .lircrc files in the home directories and does this have something to do with my problem?

Start out by making sure irw works properly.  If it doesn't, the lircrc files have nothing to do with it.
They are only used when applications try to do things with lirc. (not the daemon)
> 
6. Is my problem related to only running one instance of lircd (I don't think so).

With the pvr150, you won't want more than one instance running.  Doing more instances will make things quite troublesome (although such things are automated now for Hardy)

---

### Post by rswartze on 2008-01-12
Thanks Super, I made some progress

LIRC is not loading my config file properly.  I get an error when it runs into my first blaster code.

Jan 12 12:50:22 Mythbuntu lircd-0.8.2[5260]: error in configfile line 28:
Jan 12 12:50:22 Mythbuntu lircd-0.8.2[5260]: "2175729664": must be a valid (lirc_t) number
Jan 12 12:50:22 Mythbuntu lircd-0.8.2[5260]: reading of config file failed

I found some information on [http://www.blushingpenguin.com/mark/blog/?p=19&cp=all](http://www.blushingpenguin.com/mark/blog/?p=19&cp=all)

With this post:

Ryan: it&#8217;s a bug in lirc to do with 64-bit support. Try asking the lirc list for help. Somebody had a fix for this and I asked them for it so I could forward it to you, but so far they haven&#8217;t responded. It&#8217;s just something trivial to do with the lirc file parser.

Do you know if this is updated in newer lirc versions, or do I have to follow this fix:

Hi Mark,

Thanks for pointing me in the right direction. Not being much of a programmer, I just went into the code and removed the if-then block that validates lirc_t numbers. After recompiling, I don&#8217;t receive the error message any more, and my IR blaster blinks when I run the send_power_new script!

I know, that&#8217;s hardly a fix, but it got me going. Hopefully I&#8217;ll be able to get that fix someone else came up with, or see the fix in a new version.

---

### Post by TheHilikus on 2008-02-17
i am glad i found this thread. i updated today from feisty and lirc stopped working (i was using the patched version following Mark braindump's blog and it worked fine in feisty). after a while i got lirc back but not the ir blaster. this is where this thread came to play. 1 thing though, my distro upgrade didnt finish successfully because of lirc so i dont know if that made it miss some updates, but it seems that that patch by superm1 is still **not** part of the main repos, which is weird. i wish it had worked just by installing it the first time, instead i had to add superm1's repo to get a good package after hours of fiddleling. whats taking so long? its been like 4 months already, a hard crash of the system due to a module sounds pretty bad to me...

---

### Post by opennomad on 2008-03-02
so the package works really well for me under the generic kernel (linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.40~ppa1).

I just tried using it under the -rt (real time) kernel and there the package (linux-ubuntu-modules-2.6.22-14-rt 2.6.22-14.40~ppa1) and the kernel boots but the remote doesn't work since the modprobe just stops without completing.  In other words modprobe command just sits there.

The last couple of things I see in dmesg are:

```

[  137.835737] eth1: no IPv6 routers present
[  247.710791] lirc_dev: IR Remote Control driver registered, at major 61 
[  247.888982] lirc_pvr150: chip found with RX and TX

```

Has anyone seen this?  does anyone have it working under the -rt kernel?

---

### Post by tshannon on 2008-04-05
The solution in this post got my lirc stuff working great, but after installing the module from the deb source, it broke my wireless connection.  Now I can see the wireless network I want to connect to, but it shows no signal strength (where previosly it was 80 - 90%), and I can't connect to it at all.

Anyone know what happened?

---

