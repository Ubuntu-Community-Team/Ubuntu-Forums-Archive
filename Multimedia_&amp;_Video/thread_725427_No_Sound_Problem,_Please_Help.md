---
title: "No Sound Problem, Please Help"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by perito on 2008-03-15
My sound card is 
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

I tried [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but when I compile I get tons of errors telling me 
```

cp: cannot stat `snd-hpet.o': No such file or directory
cp: cannot stat `snd-page-alloc.o': No such file or directory
cp: cannot stat `snd-pcm.o': No such file or directory
cp: cannot stat `snd-timer.o': No such file or directory
cp: cannot stat `snd.o': No such file or directory

```
and so on...

is there another way to get the driver to my sound card?
Please, please help me... I really to make the sound thing work...

---

### Post by perito on 2008-03-15
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
Im trying method A, which is 
sudo module-assistant update
but Im getting 
sudo: module-assistant: command not found

what does that mean? what should I do?

---

### Post by fenian on 2008-03-15
Install module assistant ...

> sudo apt-get install module-assistant

---

### Post by perito on 2008-03-15
the code is 
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa

what should I install? only sudo apt-get install module-assistant???

---

### Post by fenian on 2008-03-15
First you have to install module-assistant with...

> sudo apt-get install module-assistant

then continue with the instructions you were following.

---

### Post by perito on 2008-03-15
im getting building failed and this is in the log
```

 &#9474; make[6]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1          &#9618; 
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618; 
 &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618; 
 &#9474; make[3]: *** [modules] Error 2                                             &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'      &#9618; 
 &#9474; make[2]: *** [compile] Error 2                                             &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646; 
 &#9474; make: *** [kdist_image] Error 2   

```

what should i do?

---

### Post by fenian on 2008-03-15
Try this method instead  (this will install the latest version of the Alsa sound driver).In a terminal enter....

> wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
tar xvpjf alsa-driver-1.0.16.tar.bz2
cd alsa-driver-1.0.16.tar.bz2
./configure --with-cards=hda-intel
make
sudo make install
modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss snd-seq-

reboot your computer.

---

### Post by perito on 2008-03-15
when i tar xvpjf i get a HUGE Error that ends like this:
```

alsa-driver-1.0.16/utils/buildrpm
tar: alsa-driver-1.0.16/utils/buildrpm: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/link-modules
tar: alsa-driver-1.0.16/utils/link-modules: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/insert
tar: alsa-driver-1.0.16/utils/insert: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/convert_isapnp_ids
tar: alsa-driver-1.0.16/utils/convert_isapnp_ids: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/
tar: alsa-driver-1.0.16/utils/patches: Cannot mkdir: No such file or directory
alsa-driver-1.0.16/utils/patches/patch.Makefile.top.2.4.0-test10
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.top.2.4.0-test10: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.15-01.diff
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.15-01.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.22-01.diff
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.22-01.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.1
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.1: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/rtc-2.4.16.patch
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.16.patch: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/rtc-2.2.16.dif
tar: alsa-driver-1.0.16/utils/patches/rtc-2.2.16.dif: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/soundcore.2.4.patch
tar: alsa-driver-1.0.16/utils/patches/soundcore.2.4.patch: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.21-02.diff
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.21-02.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.19-01.diff
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.19-01.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.14-01.diff
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.14-01.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/rtc-2.4.20.patch
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.20.patch: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/patch.mem.c.2.3.34
tar: alsa-driver-1.0.16/utils/patches/patch.mem.c.2.3.34: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/byteswap.h
tar: alsa-driver-1.0.16/utils/patches/byteswap.h: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.17-03.diff
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.17-03.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pnp-suspend-2.6.15-rc1.diff
tar: alsa-driver-1.0.16/utils/patches/pnp-suspend-2.6.15-rc1.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/rtc-2.4.9.dif
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.9.dif: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/patch.Makefile.top.2.4.1
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.top.2.4.1: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.0-test10
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.0-test10: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/rtc-2.4.23.patch
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.23.patch: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.2
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.2: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/soundcore.2.4.20.patch
tar: alsa-driver-1.0.16/utils/patches/soundcore.2.4.20.patch: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.18-01.diff
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.18-01.diff: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/rtc-2.4.25.patch
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.25.patch: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/patches/rtc-suse-7.0-2.2.16.dif
tar: alsa-driver-1.0.16/utils/patches/rtc-suse-7.0-2.2.16.dif: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/Makefile
tar: alsa-driver-1.0.16/utils/Makefile: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/buildrpm.in
tar: alsa-driver-1.0.16/utils/buildrpm.in: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/alsasound
tar: alsa-driver-1.0.16/utils/alsasound: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/old/
tar: alsa-driver-1.0.16/utils/old: Cannot mkdir: No such file or directory
alsa-driver-1.0.16/utils/old/export-symbols.in
tar: alsa-driver-1.0.16/utils/old/export-symbols.in: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/old/export-symbols.perl
tar: alsa-driver-1.0.16/utils/old/export-symbols.perl: Cannot open: No such file or directory
tar: Skipping to next header
alsa-driver-1.0.16/utils/mod-deps
tar: alsa-driver-1.0.16/utils/mod-deps: Cannot open: No such file or directory
tar: Skipping to next header
tar: Error exit delayed from previous errors


```

---

### Post by perito on 2008-03-15
is there a problem in the file itself?

---

### Post by fenian on 2008-03-15
Sorry there were some typos in my post .For the first command after 

> wget ftp://

finish the line with...

> ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2

it should then download alsa-driver-1.0.16.tar.bz to your home directory,check to see if its there ,right click the file and choose extract here.
Now open the terminal and enter...
> 
cd alsa-driver-1.0.16
./configure --with-cards=hda-intel
make
sudo make install
modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss 

reboot

---

### Post by perito on 2008-03-16
man it all worked except the last step
```
modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss

```

```
ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-hwdep.ko): Operation not permitted
ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ sudo modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ 

```

and when i dmesg
```
[  938.440000] snd_hwdep: disagrees about version of symbol snd_info_register
[  938.440000] snd_hwdep: Unknown symbol snd_info_register
[  938.440000] snd_hwdep: disagrees about version of symbol snd_info_create_module_entry
[  938.440000] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  938.440000] snd_hwdep: disagrees about version of symbol snd_info_free_entry
[  938.440000] snd_hwdep: Unknown symbol snd_info_free_entry
[  938.440000] snd_hwdep: disagrees about version of symbol snd_unregister_oss_device
[  938.440000] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  938.440000] snd_hwdep: Unknown symbol snd_verbose_printk
[  938.440000] snd_hwdep: disagrees about version of symbol snd_register_oss_device
[  938.440000] snd_hwdep: Unknown symbol snd_register_oss_device
[  938.440000] snd_hwdep: disagrees about version of symbol snd_ctl_register_ioctl
[  938.440000] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  938.440000] snd_hwdep: disagrees about version of symbol snd_unregister_device
[  938.440000] snd_hwdep: Unknown symbol snd_unregister_device
[  938.440000] snd_hwdep: disagrees about version of symbol snd_device_new
[  938.440000] snd_hwdep: Unknown symbol snd_device_new
[  938.440000] snd_hwdep: disagrees about version of symbol snd_ctl_unregister_ioctl
[  938.440000] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  938.440000] snd_hwdep: Unknown symbol snd_register_device_for_dev


```

---

### Post by xeth_delta on 2008-03-16
I suggest you try running alsaconf:
```
sudo alsaconf
```
Follow the instructions on the screen.

---

### Post by perito on 2008-03-16
```
ubuntu@ubuntu-laptop:~$ sudo alsaconf
sudo: alsaconf: command not found
ubuntu@ubuntu-laptop:~$ 

```

????

---

### Post by perito on 2008-03-16
IT WORKED without 
modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss

I cant believe I hear SOUND out of my PC
I LOVE YOU
thx ALOT

---

### Post by xeth_delta on 2008-03-16
> **perito said:**
> ```
ubuntu@ubuntu-laptop:~$ sudo alsaconf
sudo: alsaconf: command not found
ubuntu@ubuntu-laptop:~$ 

```

????

Ah, you don't have it installed. Follow the instructions in [http://ubuntuforums.org/showthread.php?t=672290](http://ubuntuforums.org/showthread.php?t=672290) post #18.

---

### Post by perito on 2008-03-16
> **fenian said:**
> Sorry there were some typos in my post .For the first command after 



finish the line with...



it should then download alsa-driver-1.0.16.tar.bz to your home directory,check to see if its there ,right click the file and choose extract here.
Now open the terminal and enter...


reboot

im trying to do that agian on gusty but im getting this error
```
ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Operation not permitted
ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ sudo modprobe snd-hda-intel snd-pcm-oss snd-mixer-oss
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ 

```
and this
```
[   51.608000] ieee80211_crypt: registered algorithm 'TKIP'
[  320.232000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  320.232000] snd_hda_intel: Unknown symbol snd_ctl_add
[  320.232000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  320.232000] snd_hda_intel: Unknown symbol snd_pcm_new
[  320.232000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  320.232000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  320.232000] snd_hda_intel: disagrees about version of symbol snd_card_register
[  320.232000] snd_hda_intel: Unknown symbol snd_card_register
[  320.232000] snd_hda_intel: disagrees about version of symbol snd_card_free
[  320.232000] snd_hda_intel: Unknown symbol snd_card_free
[  320.236000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  320.236000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  320.236000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  320.236000] snd_hda_intel: Unknown symbol snd_card_proc_new
[  320.236000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  320.236000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  320.240000] snd_hda_intel: Unknown symbol snd_ctl_new1
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_component_add
[  320.240000] snd_hda_intel: Unknown symbol snd_component_add
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_card_new
[  320.240000] snd_hda_intel: Unknown symbol snd_card_new
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  320.240000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  320.240000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_device_new
[  320.240000] snd_hda_intel: Unknown symbol snd_device_new
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  320.240000] snd_hda_intel: Unknown symbol snd_card_disconnect
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  320.240000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  320.240000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
ubuntu@ubuntu-laptop:~$ 

```

what should i do?

---

### Post by fenian on 2008-03-16
Try this in the terminal,enter each line seperately...
> 
sudo modprobe snd-hda-intel 
sudo modprobe snd-pcm-oss 
sudo modprobe snd-mixer-oss

---

### Post by perito on 2008-03-16
i removed gusty and installed feisty... its working now
i hope hardy would work... donno why gusty didnt :S
I tried everything (I installed Gusty TWICE today)

---

