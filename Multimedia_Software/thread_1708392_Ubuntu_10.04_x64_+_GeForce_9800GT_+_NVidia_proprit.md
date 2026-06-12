---
title: "Ubuntu 10.04 x64 + GeForce 9800GT + NVidia propritary driver = black screen of death"
date: 2011-03-16
forum: Multimedia Software
---

### Post by HolgerB on 2011-03-16
Hi all,

prior filing a bug in launchpad I wanted to hear you expertise on my issue. After pluging in a newly bought NVidia GeForce 9800GT from Ebay into my system I decided to reinstall my system using the latest LTS version of Ubuntu (10.04.1 x64). After some starting issues (I needed to use nomodeset as boot parameter in order to get X from the install DVD) everything went fine. Then I upgraded the whole system and install nvidia-current via the standard propritary driver tool from Ubuntu. Everything went fine until I started nvidia-xconfig to generate a basic xorg.conf which loads the NVidia driver. After reboot my screen went black (short message from the monitor "no signal") and the whole system locked up. No chance to switch to any of the cosole. The system was not even reachable via ssh from my other Ubuntu box. I tried a few times to restart the system via hard reboot and the system rarely is even capable writing an Xorg.0.log. The one time it did everything looked fine to me (see Xorg.0.log). 

The last line in the Xorg.log was
(EE) Mar 13 21:48:14 NVIDIA(0): WAIT: (E, 0, 0x827d, 0)

Seems to me that the video driver seems to wait but for what ? :)

I spent some time googling for this error and found tips on using the nopat boot parameter but this didn´t help either. I tried various combinations of older / newer NVidia drivers but none of them fixed this issue. Many postings in the www were mentioning error within the messages file but I didn´t find them either. The postings here in the forum I find when searching for nvidia, black screen were mostly related to either notebooks and other GeForce cards.

After deleting my xorg.conf the system boots up fine which is no surprise since I guess that the open source nv driver is loaded. 

I can confirm that the graphic adapter itself works flawlessly since I run WinXP in dual boot on this system. I also tried some live gaming DVDs (e.g. Linux X-Gamer Live DVD, Sabayon Linux 5.5 Gaming Edition x86) and the card worked fine with newer versions of the NVidia propritary driver (260.19.36 / 260.19.29). What was really interesting in this test: All three 32 bit version I tried worked fine **but** the 64 bit version of the Sabayon Gaming Edition DVD showed similar behaviour during booting up: X is starting, monitor goes to standby and *bang* system locks up.
 
This are my current system specs:
 - Ubuntu 10.04.1 x64 
- AMD Athlon 64 X2 5200+ 
- 6 GB DDR2 RAM (2x2GB+2x1GB)
- ALiveXFire-eSATA2 Mainboard 
- Galaxy nVidia Geforce 9800 GT 512 MB 

Any ideas on this issues ? I am out of any approach for further investigation. I would have uploaded my messages file but it is really big because of all my experiments.
Please let me know if any further infomation is required.

TIA,
Holger

---

### Post by BicyclerBoy on 2011-03-17
AFAIK
If nomodeset was needed to allow the nvidia driver to load, this means the nouveau kernel module is not blacklisted.
I thought the later driver install scripts fixed this.

Have you tried installing the (old outdated) ubuntu nivida driver thru' jockey or..
You can get a recent pre-compiled bin driver from 3rd party ppa package managed & avoid the nvidia script..
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
This installs with dkms & dependencies are managed (kernel headers).. no kernel update mess.

I would try removing the mpeg2 encoder card & try again.

---

### Post by HolgerB on 2011-03-17
> **BicyclerBoy said:**
> AFAIK
If nomodeset was needed to allow the nvidia driver to load, this means the nouveau kernel module is not blacklisted. 
For clarification: Nomodeset was only required for my system to boot up the Ubuntu CD in live mode with running X in order to install Ubuntu itself. I am not shure though what causes this behaviour. To my understanding the nouveau driver is the standard one for my card after launching live mode.

> **BicyclerBoy said:**
> 
Have you tried installing the (old outdated) ubuntu nivida driver thru' jockey or..
You can get a recent pre-compiled bin driver from 3rd party ppa package managed & avoid the nvidia script..
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
This installs with dkms & dependencies are managed (kernel headers).. no kernel update mess.

On tip of the german Ubuntu wiki I tried the newest version from the x-org ledger ppa (v270.29). No change. I haven't tried an older version though.

> **BicyclerBoy said:**
> 
I would try removing the mpeg2 encoder card & try again.
What issues whould you expect from a Haupauge PVR150 ? How could it interfere with the 3D card ? :confused:

---

### Post by oldfred on 2011-03-17
What nVidia driver did you install.

With my 9600Gt I have to use nomodeset with liveCD and on first boot by adding to grub menu kernel line. Then I just install the recommended nVidia that pops up.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Sometimes other options may be reaquired:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

---

### Post by HolgerB on 2011-03-17
First I installed the standard nvidia-driver which comes with U10.04.1 out of the box. I am not shure which version this is/was but the corresponding package is called nvidia-current. I needed to run nvidia-xconfig afterwards (as requested by the NVidia system tool) in order to generate a xorg.conf which loads the nvidia driver on next X-restart.

Beside nomodeset I also tried nopat als kernel option. Neither of them helped to solve the issue with the NVidia driver.

---

### Post by BicyclerBoy on 2011-03-18
> What issues whould you expect from a Haupauge PVR150 ? How could it interfere with the 3D card ?
Just grasping at straws really & that it appears in the Xorg.0.log..

You could try commenting out the "UseEdidDpi" line(s) in the xorg.conf file.
Try one monitor only..

---

### Post by HolgerB on 2011-03-24
Ok, thanks for all replies !

I've found a "solution". My mainboard is (somehow) causing the issues ! Since I only had 4GB in my machine and only a 32 bit WinXP, I never experienced any issues in adressing more than 4 GB of RAM. After pluging in another 2 GB, the problems started. A test installation with 32 bit Ubuntu 10.04.2 (PAE-Kernel) gave me a somewhat working system:
- Full 6GB were shown
- 3D acceleration worked
- Native Linux games with 3D worked (e.g. Word of Padman, Open Arena)

The fun started when I played around with WINE. I got tons of errors plus strange stack traces. After removing 50% RAM (= 3GB RAM only) everything worked fine. 
A cross check with the 64 bit Sabayon Live gaming DVD confirmed now nicely working 3D.

After this I re-installed Ubuntu 10.04.02 in x64-flavour and everything worked. Even the nomodeset parameter was not neccessary anymore. I got a working Gnome Live mode desktop without any issues.

Unfortunately I have no 64 Windows. So I am not able to confirm wether my mainboard has a general problem to address more than 4 GB of memory, or if my issues is solely related to x64 Linux in combination with hardware.

---

### Post by BicyclerBoy on 2011-03-28
32bit win (or any 32bit OS) can only directly address 4GB RAM space but..

PCIe requires shared/mapped memory space, that is visible by CPU/MMU, for transfer so you can lose 500MB (more) leaving you with closer to 3GB..

AFAIK The pae kernel does some magic to address more RAM.
The physical/electrical arrangements of the RAM modules/slots in the mobo may have a big effect.  

I think it is more reliable to just use the 64bit OS.
I think there are very significant differences (32- 64 kernel/OS) in the boot process but I don't have the understanding to make worthy comment..

---

### Post by giusedia on 2011-04-05
Using a 64bit system did not help in my case.
I have a similar setup
1) Asrock Alivexfire Esata2 3.0 latest bios (3.90)
2) nVidia Corporation G98 GeForce 8400 GS
3) ii  nvidia-current    260.19.06-0ubuntu1  
4) 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 
5) Mem:          3270 mb   (but actually4gb, 2gb 2x, enabling memory hole remap locks enables the bios to see 4096mb but locks everything)
and experience the same issues as you.
I suspect memory and the Nvidia card are the source of the issue, but so far I have been unable to get a pattern. 
The monitor gets blank as you describe.
Disabling cool and quiet and getting less memory brings less problems, but sometimes it gets locked everyway.
When it boots, it works flawlessy and runs every coincevable benchmark with no issues.
Memory is fine with memtest86 but you should not use the 'probe' option to map the real memory.
This motherboard sucks, I had AM2NF6G-VSTA and I worked flawlessly. I suspect it's an ATI chipset+ Nvidia proprietary driver issue.
I use CUDA so I need them enabled.
If you find a fix, please keep  us  posted.
ADD: I first tried booting with 2x2gb and 2x1gb (6gb) and it would not boot at all, never. Installed memory used to work flawlessly in dual-channel in previous mobo.

---

### Post by HolgerB on 2011-04-05
giusedia,

I share your pain.

Just two quick ideas: 
- Try to limit the memory the kernel can access by using the mem=XXX parameter during boot-up. You can easily access the kernel boot parameters by editing your grub configuration (pressing e I guess when the boot menu shows up).

- Simply physically remove enough RAM until you only have 2 GB left and re-try.

> 
I suspect it's an ATI chipset+ Nvidia proprietary driver issue.  
Well, I can not speak for your hardware combination by for me a ATI 4670HD (in the same system) showed similar issues. I was unable to either use the radeon open source drivers as well as the fglrx driver. I was going completely nuts without any ideas. Right now my guess is that the 4670 HD would work now without any issues with only 3 GB in my system.

So, no, I do not think that the issue is related to mainboard, RAM and NVidia cards. I guess it's "just" related to mobo and the amount of memory used. Strangely enough I have seen a bug report over at launchpad where someone had similar issues and the same mobo.

Unfortunately I have no 64 bit version of window. So I can not confirm wether the mainboard has general issues with more than 4GB RAM or if this is solely related to 64 Bit Linux.

Regards,
Holger

---

### Post by giusedia on 2011-04-05
I forgot to say that with some distro (especially [stresslinux_64bit_11.3.x86_64-0.6.108.iso.bz2]("http://www.stresslinux.org/sl/downloads/43") from CD it never fails a boot from the CD with 4GB, while Ubuntu amd64, from my mdadm raid array (very often) or from the usb key (made with startup disk creator, fails rarely) does.
You could put back on 4gb and see if stresslinux fails to start: if it never does, it could be a good point to start to assert if the problem can be mitigated.

---

### Post by HolgerB on 2011-04-06
Thanks for the hint ! 

I didn't know stresslinux at all. Unfortunately I doubt that this will help since I crosstested different Debian flavours (aptosid, Mintlinux, etc) with similar results. Even the 64 bit sabayon live gaming DVD failed with more than 4GB while it worked flawlessly with 3 GB. My issues only start to show up if I install the propritary blob from NVidia (or the corresponding ATI part).

Honestly after hours of investigation and testing I do not feel any like plugging back and forth any hardware.
I am fine with 3GB although 6GB would have been nice for running multiple KVM machine.

---

