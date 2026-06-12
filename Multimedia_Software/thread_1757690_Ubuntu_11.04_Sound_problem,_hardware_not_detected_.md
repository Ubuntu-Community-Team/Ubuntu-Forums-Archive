---
title: "Ubuntu 11.04 Sound problem, hardware not detected (Intel sound card)"
date: 2011-05-13
forum: Multimedia Software
---

### Post by saurabh_02 on 2011-05-13
I previously had Ubuntu 10.10 installed, and one day after updating I lost audio. In the hope of resolving  this problem, I then updated to Ubuntu 11, but the problem persists. 

The output of the command:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 
is here: [http://www.alsa-project.org/db/?f=fe658796655756fe87f97e4dee238af95b51ff1d](http://www.alsa-project.org/db/?f=fe658796655756fe87f97e4dee238af95b51ff1d)


Also, I  followed the steps on sound troubleshooting ([https://help.ubuntu.com/community/So...%20Compilation]("https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation")) after realizing that I may not have the sound driver installed.

But after reaching the step where I try to configure alsa using :

sudo dpkg-reconfigure alsa-source

I faced the following error (for hda-intel soundcard)

Done!
unpack 
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.38-8-generic  KSRC=/usr/src/linux-headers-2.6.38-8-generic KDREV=2.6.38-8.42  kdist_image
saurabh02@arroyavelab2:~$ tail -F /var/cache/modass/alsa-source.buildlog.$(uname -r).*
==> /var/cache/modass/alsa-source.buildlog.2.6.38-8-generic.1303687971 <==
compilation terminated.
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2

==> /var/cache/modass/alsa-source.buildlog.2.6.38-8-generic.1303688035 <==
compilation terminated.
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2




Any help is greatly appreciated....

---

### Post by lidex on 2011-05-14
OK. Your alsa install is borked, but that's alright, we can re-install it.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by saurabh_02 on 2011-05-16
Lidex: Thanks for your reply. I ran the command, and rebooted. But, still there is no sound hardware detected, and of course no sound. Below was the full output of the command:


Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.38-9-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.38-9-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.38-9-generic linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 4 not upgraded.
Need to get 0 B/37.4 MB of archives. After unpacking 0 B will be used.
Preconfiguring packages ...              
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60183 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60184 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60208 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60209 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 62462 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 62484 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
(Reading database ... 600362 files and directories currently installed.)
Preparing to replace linux-image-2.6.38-9-generic 2.6.38-9.43 (using .../linux-image-2.6.38-9-generic_2.6.38-9.43_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.38-9-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-9-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found kernel: /boot/vmlinuz-2.6.35-28-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.27-15-generic
Found kernel: /boot/vmlinuz-2.6.24-25-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60183 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60184 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60208 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60209 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-9-generic /boot/vmlinuz-2.6.38-9-generic
Preparing to replace alsa-base 1.0.24+dfsg-0ubuntu1 (using .../alsa-base_1.0.24+dfsg-0ubuntu1_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.24.2-0ubuntu6 (using .../alsa-utils_1.0.24.2-0ubuntu6_i386.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2 1.0.24.1-0ubuntu5 (using .../libasound2_1.0.24.1-0ubuntu5_i386.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.24+dfsg-0ubuntu1 (using .../linux-sound-base_1.0.24+dfsg-0ubuntu1_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60187 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60188 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60212 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60213 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
Setting up linux-image-2.6.38-9-generic (2.6.38-9.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-9-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-9.43 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-9.43 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-9-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found kernel: /boot/vmlinuz-2.6.35-28-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.27-15-generic
Found kernel: /boot/vmlinuz-2.6.24-25-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60187 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60188 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60212 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 60213 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-9-generic /boot/vmlinuz-2.6.38-9-generic
 * dkms: running auto installation service for kernel 2.6.38-9-generic                                                                                       
 *       vboxhost (4.0.4)...                                                                                                                          [ OK ] 
 *       nvidia-current (270.41.06)...                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-9-generic /boot/vmlinuz-2.6.38-9-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-9-generic /boot/vmlinuz-2.6.38-9-generic
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60187 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60188 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60212 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60213 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_hardy': invalid character in revision number
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-9-generic /boot/vmlinuz-2.6.38-9-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-9-generic /boot/vmlinuz-2.6.38-9-generic
Setting up libasound2 (1.0.24.1-0ubuntu5) ...
Setting up linux-sound-base (1.0.24+dfsg-0ubuntu1) ...
Setting up alsa-base (1.0.24+dfsg-0ubuntu1) ...
Setting up alsa-utils (1.0.24.2-0ubuntu6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by lidex on 2011-05-16
I think you updated to the wrong version:
```
Ubuntu natty (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu Natty (development branch)"
```
Also, what's with the multitude of kernels? I would remove all but these two:
```
Found kernel: /boot/vmlinuz-2.6.38-9-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
```
What kernel are you in right now:
```
uname -a
```

---

### Post by saurabh_02 on 2011-05-17
Hi Lidex: the output of

uname -a

is,

Linux [hostname] 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686 i686 i386 GNU/Linux

so as you advised, i moved all other kernel version, except 38-9 and 38-8, from the /boot/ folder. I again ran the command you gave me before for re-installation of several modules and rebooted, but still no luck. :(

---

### Post by lidex on 2011-05-17
> **saurabh_02 said:**
> Hi Lidex: the output of

uname -a

is,

Linux [hostname] 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686 i686 i386 GNU/Linux

so as you advised, i moved all other kernel version, except 38-9 and 38-8, from the /boot/ folder. I again ran the command you gave me before for re-installation of several modules and rebooted, but still no luck. :(

The more I look at this, the more I believe you should re-install natty - a clean install. Backup to another drive, wipe this one, and download the release version to install:
[http://cdimage.ubuntu.com/releases/natty/release/](http://cdimage.ubuntu.com/releases/natty/release/)

---

### Post by saurabh_02 on 2011-05-23
lidex: Is there any way I could re-install without erasing my current applications?

---

### Post by lidex on 2011-05-24
Probably not, but you can backup your program configurations and import them back in as needed. Some of them may be the culprit which is why you want a clean install.

---

