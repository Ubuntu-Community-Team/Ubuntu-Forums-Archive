---
title: "Wireless issues"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by Teethdude on 2013-04-30
A few days ago, I updated to kubuntu 13.04. Everything was good and fine at first. Then, my wireless stopped working suddenly.I am duel booting it with Win7 and wireless works fine for it, but Kubuntu has issues.It will connect to a wireless access point. looks fine and all, but when trying to use the connection (web browser, minecraft, really anything.) it just doesn't work.thanks in advance.

---

### Post by Frankaz on 2013-05-01
> **Teethdude said:**
> A few days ago, I updated to kubuntu 13.04. Everything was good and fine at first. Then, my wireless stopped working suddenly.I am duel booting it with Win7 and wireless works fine for it, but Kubuntu has issues.It will connect to a wireless access point. looks fine and all, but when trying to use the connection (web browser, minecraft, really anything.) it just doesn't work.thanks in advance.

I too have a problem with wireless, it won't connect at all. Says configuring interface for ages but then gives up. This only happened since upgrading to 13.04, Win7 still working fine. Chipset for wireless is ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. A1) [Ralink RT3072]

---

### Post by Teethdude on 2013-05-01
Well, it seems that my wireless tends to be choosey. At home very occasionally i'll disable and enable the wireless to get it to work. At school, it will connect but i have no access at all to the network. No internet or anything.

Driver issues? Broadcom 4313 (i think)

---

### Post by Teethdude on 2013-05-01
Recently i noticed errors happening in the background (Ctrl+Alt+f1) on the Command Line Interface. Here is a snapshot attached.

[ATTACH=CONFIG]242046[/ATTACH]

---

### Post by Hadaka on 2013-05-01
Hi, lets see what your wireless card is.
please do..
```
lspci -nn | grep 0280
```
thanks.

---

### Post by Teethdude on 2013-05-01
The output was as followed:
```
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

---

### Post by Hadaka on 2013-05-01
Hi read post #6 and #8

[http://ubuntuforums.org/showthread.php?t=2140263](http://ubuntuforums.org/showthread.php?t=2140263)

if you have problems, post back.
thanks.

---

### Post by Teethdude on 2013-05-01
The thing is, my connection is working just fine now (because I'm at home). But at school, it will connect to the wireless internet, I'll "login" to have access, then that is where i lose the ability to do anything. Web pages will sit and load for long periodes of time then say it something like: "Webpage not available".

If I boot into Windows7, it will work at school. Is it possible my school is blocking access for anything that isn't windows based? Macs and Android devices tend to have problems as well.

---

### Post by Hadaka on 2013-05-01
ok, by this..
  "A few days ago, I updated to kubuntu 13.04. Everything was good and fine at first. Then, my wireless stopped working suddenly"
one would think your wifi was not working at all.
please post the results of..
```
lsmod
modinfo wl
```
thanks.

---

### Post by Teethdude on 2013-05-01
Sorry about the miswording of my post. Mistakes happen. But here is the output of the code:
```
mike@mike-Kubuntu:~$ lsmodModule                  Size  Used by
btusb                  22474  0 
snd_hrtimer            12744  1 
pci_stub               12622  1 
vboxpci                23194  0 
parport_pc             28152  0 
vboxnetadp             25670  0 
ppdev                  17073  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 42641  12 
bnep                   18036  2 
bluetooth             228619  22 bnep,btusb,rfcomm
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
joydev                 17377  0 
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
microcode              22881  0 
snd_hda_codec_realtek    78399  1 
lib80211_crypt_tkip    17379  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
wl                   3074449  0 
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
psmouse                95870  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211               14352  2 wl,lib80211_crypt_tkip
mac_hid                13205  0 
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
serio_raw              13215  0 
rtsx_pci_ms            13011  0 
k10temp                13126  0 
cfg80211              510937  1 wl
memstick               16554  1 rtsx_pci_ms
fglrx                5201161  381 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
amd_iommu_v2           19068  1 fglrx
sp5100_tco             13735  0 
i2c_piix4              13266  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
vesafb                 13828  1 
rtsx_pci_sdmmc         17475  0 
r8169                  67446  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
wmi                    19070  1 hp_wmi
video                  19390  0 
ahci                   25731  1 
libahci                31364  1 ahci
mike@mike-Kubuntu:~$ modinfo wl
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string
mike@mike-Kubuntu:~$ clear
mike@mike-Kubuntu:~$ lsmod
Module                  Size  Used by
btusb                  22474  0 
snd_hrtimer            12744  1 
pci_stub               12622  1 
vboxpci                23194  0 
parport_pc             28152  0 
vboxnetadp             25670  0 
ppdev                  17073  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 42641  12 
bnep                   18036  2 
bluetooth             228619  22 bnep,btusb,rfcomm
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
joydev                 17377  0 
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
microcode              22881  0 
snd_hda_codec_realtek    78399  1 
lib80211_crypt_tkip    17379  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
wl                   3074449  0 
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
psmouse                95870  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211               14352  2 wl,lib80211_crypt_tkip
mac_hid                13205  0 
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
serio_raw              13215  0 
rtsx_pci_ms            13011  0 
k10temp                13126  0 
cfg80211              510937  1 wl
memstick               16554  1 rtsx_pci_ms
fglrx                5201161  381 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
amd_iommu_v2           19068  1 fglrx
sp5100_tco             13735  0 
i2c_piix4              13266  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
vesafb                 13828  1 
rtsx_pci_sdmmc         17475  0 
r8169                  67446  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
wmi                    19070  1 hp_wmi
video                  19390  0 
ahci                   25731  1 
libahci                31364  1 ahci
mike@mike-Kubuntu:~$ modinfo wl
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string
mike@mike-Kubuntu:~$ 



```

Thanks for being patient with me and helping me.

---

### Post by Hadaka on 2013-05-01
Nothing jumping out, with the exception of alot
of trouble reports with that card and 13.04.
lets try the Varunendra fix and see if that helps.
please post the output of..
```

apt-cache show bcmwl-kernel-source | grep -i version 
```
and we'll go from there..
thanks.

---

### Post by Teethdude on 2013-05-01
I put the command in. here is the output of the command:
```
mike@mike-Kubuntu:~$ apt-cache show bcmwl-kernel-source | grep -i version
Version: 6.20.155.1+bdcom-0ubuntu6
mike@mike-Kubuntu:~$ 



```

---

### Post by Hadaka on 2013-05-01
Hi, it looks like you have the new 13.04 problem
driver..go to this link and do all the commands in post #8
report back and then we will do the varunendra fix.
[http://ubuntuforums.org/showthread.php?t=2140263](http://ubuntuforums.org/showthread.php?t=2140263)
thanks.

---

### Post by Teethdude on 2013-05-01
Ok, i did those commands. here is the new output for the final one:
```
mike@mike-Kubuntu:~$ apt-cache show bcmwl-kernel-source | grep -i version
Version: 6.20.155.1+bdcom-0ubuntu6
Version: 5.100.82.38+bdcom-0ubuntu6

```

---

### Post by Hadaka on 2013-05-01
Good job, please do..
*from a WIRED connection *
```
sudo apt-get remove --purge bcmwl-kernel-source 
```
then
```
 sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6

```
and lastly..
```

dpkg -s bcmwl-kernel-source | grep -i version 
```

---

### Post by Teethdude on 2013-05-01
Well here are the results. I did see an error come up and the command "fill in" did nothing. 
```
mike@mike-Kubuntu:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,279 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119717 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
mike@mike-Kubuntu:~$ sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,151 kB of archives.
After this operation, 3,514 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/restricted bcmwl-kernel-source amd64 5.100.82.38+bdcom-0ubuntu6 [1,151 kB]
Fetched 1,151 kB in 11s (104 kB/s)                                                           
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 119650 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-19-generic
Building for architecture x86_64
Building initial module for 3.8.0-19-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.0-19-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
mike@mike-Kubuntu:~$ fill in
No command 'fill' found, did you mean:
 Command 'kill' from package 'procps' (main)
 Command 'file' from package 'file' (main)
 Command 'sfill' from package 'secure-delete' (universe)
fill: command not found
mike@mike-Kubuntu:~$ 



```

---

### Post by Hadaka on 2013-05-01
that "fill in" was a place holder while i went to 
copy and paste the command..please see the
corrected command from the last post.
CODE IS:

dpkg -s bcmwl-kernel-source | grep -i version
thanks.

---

### Post by Teethdude on 2013-05-01
ok, it says:
```
mike@mike-Kubuntu:~$ dpkg -s bcmwl-kernel-source | grep -i version
Version: 5.100.82.38+bdcom-0ubuntu6
mike@mike-Kubuntu:~$ 

```

---

### Post by Hadaka on 2013-05-01
please boot and check to make sure the wireless
is working...re reding varunendra;s fix..we should have
done post #8 first..then post #6 but it looks like you do
have the older stable driver now.
so..boot, try the wireless and report back please
thanks.

---

### Post by Teethdude on 2013-05-01
Well, now i have a different problem. 

It claims I have the driver, I can see my wireless connection, but it cannot connect at all. It will attempt, get stuck at "setting address" then quit.
I plugged in a LAN cable right now.

---

### Post by Hadaka on 2013-05-01
ok, stay wired and reload the dirver
first lets remove it...please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then go here [http://ubuntuforums.org/showthread.php?t=2140263](http://ubuntuforums.org/showthread.php?t=2140263)
and do post #8 then post #6
after you finish loading the driver please do
```
sudo modprobe -rfv wl
sudo modprobe wl
```
boot and check the wireless.

---

### Post by Teethdude on 2013-05-01
Well, i didn't reboot yet, but this was the output of the commands: ```
mike@mike-Kubuntu:~$ sudo modprobe -rfv wlFATAL: Module wl not found.
mike@mike-Kubuntu:~$ sudo modprobe wl
FATAL: Module wl not found.
mike@mike-Kubuntu:~$ 

```
I'll reboot now just in case.

EDIT:
I rebooted, and it doesn't work. Still gets stuck like stated before. LAN cable is back in.

---

### Post by Hadaka on 2013-05-01
ok, did you do the commands in post 8 and 6 of that
link? and did the load of the driver go without error?
please post the output of..
```
lsmod
```
thanks

---

### Post by Teethdude on 2013-05-01
Yea, i did the commands and i didn't see any errors either. here is the output of lsmod:
```
mike@mike-Kubuntu:~$ lsmodModule                  Size  Used by
btusb                  22474  0 
nls_iso8859_1          12713  1 
snd_hrtimer            12744  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  11 bnep,btusb,rfcomm
arc4                   12615  2 
brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
joydev                 17377  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  5 
snd_hda_codec         136453  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
microcode              22881  0 
snd_pcm                97451  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
snd                    68876  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
fglrx                5201161  92 
psmouse                95870  0 
serio_raw              13215  0 
mac_hid                13205  0 
k10temp                13126  0 
rtsx_pci_ms            13011  0 
bcma                   41051  1 brcmsmac
sp5100_tco             13735  0 
memstick               16554  1 rtsx_pci_ms
amd_iommu_v2           19068  1 fglrx
i2c_piix4              13266  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
vesafb                 13828  1 
mmc_block              27090  2 
rtsx_pci_sdmmc         17475  0 
r8169                  67446  0 
wmi                    19070  1 hp_wmi
video                  19390  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25731  1 
libahci                31364  1 ahci

```

---

### Post by Hadaka on 2013-05-01
ahh..should have looked at this before..
please do..
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
then at the bottom of the file add this one line
```
blacklist brcmsmac 
```
save and close gedit.
then do..
```
sudo modprobe -rfv brcmsmac
```
report back how that goes.
thanks

---

### Post by Teethdude on 2013-05-01
here's what it says:
```
mike@mike-Kubuntu:~$ sudo modprobe -rfv brcmsmac
rmmod brcmsmac
rmmod mac80211
rmmod cfg80211
rmmod bcma
rmmod brcmutil
rmmod cordic

```

---

### Post by varunendra on 2013-05-01
These don't look good to me -
> **Teethdude said:**
> ```
....
....
Building initial module for 3.8.0-19-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
**[COLOR="#FF0000"]Error! Bad return status for module build on kernel: 3.8.0-19-generic (x86_64)[/COLOR]**
Consult **[COLOR="#FF0000"]/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log[/COLOR]** for more information.

```
That was in the first attempt ^^

In the next attempt, we don't have wl module at all! -
> **Teethdude said:**
> ```
mike@mike-Kubuntu:~$ sudo modprobe wl
FATAL: **[COLOR="#FF0000"]Module wl not found[/COLOR]**.
```

> **Teethdude said:**
> ...here is the output of lsmod:
```
mike@mike-Kubuntu:~$ lsmodModule                  Size  Used by
...
brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
...
```
Can't see 'wl' there. Instead, there is brcmsmac, which is loaded when indeed the wl driver is not available.

Please post again :
```
dpkg -s bcmwl-kernel-source | grep -i version
```
And..
```
cat /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log
```

**PS:**
I am worried about the error message in post #16. May have to do some research if it re-occurs.

---

### Post by Teethdude on 2013-05-01
Just to clarify incase anyon edidn't see the post's tag, i am running Kubuntu 13.04

here's the code:
```
mike@mike-Kubuntu:~$ dpkg -s bcmwl-kernel-source | grep -i version
Version: 5.100.82.38+bdcom-0ubuntu6
mike@mike-Kubuntu:~$ cat /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log
DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.8.0-19-generic (x86_64)
Wed May  1 21:10:54 ADT 2013
make: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  LD      /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'

```

I must get to bed now, I have school tomorrow morning.
I'll check back tomorrow morning around 630-7 (Atlantic Canada GMT -4)

---

### Post by varunendra on 2013-05-01
Yes, I noticed that you are using Kubuntu. But the repositories and drivers are all the same as far as I know, so it shouldn't make any difference in our approach.

> **Teethdude said:**
> ```

/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: **[COLOR="#FF0000"]fatal error: asm/system.h: No such file or directory[/COLOR]**
compilation terminated.
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'

```

Almost the same error^^ that I encountered when I tried to compile the source downloaded directly from [broadcom's site]("http://www.broadcom.com/support/802.11/linux_sta.php"). Couldn't get around it, so took the path of using old repository, which was successful in my test as well as for at least one user in the thread we are referring to.

But looks like I must finally face the challenge of understanding the error and solving it after all.

At this point, you have two options with your card -
1) Please stand by and try whatever we (or someone better) may come up with. Or,
2) Wait until the default driver in the latest kernel is patched up to fix the bug.

Here's the bug report page that you may wish to keep an eye on : [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281)

---

### Post by Teethdude on 2013-05-02
Thanks. I'll just install the updated driver for now seeing it works when I'm at home. At school, I should be able to hold off for now.

---

### Post by varunendra on 2013-05-02
#############################################
[SIZE=3][COLOR="#FF0000"]**UPDATE :** Broadcom has updated the driver version on their site which does not need the tweaks below. So THIS FIX DOES NOT APPLY ANYMORE![/COLOR][/SIZE]
Also, the Ubuntu repositories also offer updated packages now, so there should be no need to download - compile the official driver from broadcom's site.

Source to updated Ubuntu packages (6.30.. is recommended) : [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)

If someone still has problems, feel free to post here or pm me.
#############################################
[COLOR="#000080"][I]EDIT 5 : Users of 13.04 and later should first try the native brcmsmac driver as suggested in post #83 : [http://ubuntuforums.org/showthread.php?t=2140640&p=12736821#post12736821](http://ubuntuforums.org/showthread.php?t=2140640&p=12736821#post12736821)
If that does not work well, or doesn't work at all, you may try this one.[/I][/COLOR]

[FONT=Arial][I][SIZE=3][COLOR="#800000"]**[Information Part]**[/SIZE]
Did some research with the "asm/system.h" error and as per comment #3 at [this]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506") (unrelated) bug report page, asm/system.h seems to have been intentionally dropped in kernel 3.4-rc1~54 and later : [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0195c002](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0195c002)

As a result, any package that tries to 'include' it during build process will fail in the newer kernels. Workaround is to get rid of all "#include asm/system.h" lines in the files containing it.
Accordingly, there is a patch suggested at [fedora forums]("http://forums.fedoraforum.org/showpost.php?p=1583224&postcount=7") that worked here at my 13.04 64-bit test VM.
[SIZE=3]**[End of Information Part]**[/COLOR][/SIZE][/I][/FONT]

[SIZE=3]**_The Workaround_ (only for BCM4313 [14e4:4727]) :**[/SIZE]

[LIST=1]
[*]Download the driver suitable to your architecture (32/64 bit) from here : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) [COLOR="#000080"]*(EDIT 2: use 'arch' command to find what architecture you are using. "x86_64" means 64-bit, "i386" or "i686" mean 32-bit)*[/COLOR]
[*]Copy the downloaded file to your desktop > Right-click > "Extract Here".
[*]Open the **src/wl/sys/wl_linux.c** file in the extracted directory.
[*]Delete the line that says "**#include <asm/system.h>**" (line no. 43 in current version)
[*]Search for another line that says "**.ndo_set_multicast_list**" (line no. 388 in current version) and change it to "**.ndo_set_rx_mode**". The line should now read - > .ndo_set_rx_mode = wl_set_multicast_list Proofread, save and close the file.
[*]Now open a terminal and go into the extracted folder - ```
cd ~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112
```(assuming **"hybrid-portsrc_x86_64-v5_100_82_112"** is the name of the extracted directory)
[*]Once in, compile and build the driver with make command : ```
make
```
[*]If successful, you should see "wl.ko" file in the extracted directory. If it is there, ONLY THEN proceed as follows (in the same terminal, same directory) -
[/LIST]
[COLOR="#000080"][I]EDIT : Just to be clear, enter one command at a time > let it finish > enter next command

EDIT3 : The second command below may return error if the other version of "wl" driver is not already present and loaded. So if you get error like "FATAL: Module wl not found" at the second command, it is nothing to worry about. Proceed with the next steps.[/I][/COLOR]
```
sudo su
modprobe -rfv wl
apt-get purge bcmwl-kernel-source
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
depmod -a
modprobe -v wl
update-initramfs -u
exit
```
Watch out for errors and report back if any occur (except what mentioned in *[COLOR="#000080"]EDIT3[/COLOR]* above). The main part is building of the wl.ko driver. Rest are just its placement and automation.

[COLOR="#000080"]EDIT4 :[/COLOR]
To revert the changes we have made in this post and related posts elsewhere, please follow the instructions in post #81 : [http://ubuntuforums.org/showthread.php?t=2140640&p=12698987#post12698987](http://ubuntuforums.org/showthread.php?t=2140640&p=12698987#post12698987)

---

### Post by apochry on 2013-05-15
Hello varunendra,

I have the same issue with the BCM4313 card so I tried the suggested in post #31. When I compile the driver I get the following output:
```

izzo@StupiDell:~$ cd ~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112
izzo@StupiDell:~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/built-in.o
  CC [M]  /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/shared/linux_osl.o
  CC [M]  /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o
  CC [M]  /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_iw.o
  CC [M]  /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_cfg80211.o
  LD [M]  /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.o
  Building modules, stage 2.
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  MODPOST 1 modules
[COLOR=#ff0000]WARNING: modpost: missing MODULE_LICENSE() in /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.o
see include/linux/module.h for more information
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'[/COLOR]
  CC      /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.mod.o
  LD [M]  /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
izzo@StupiDell:~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112$ 

```

Two WARNINGs... Is that alright?
The "wl.ko" was crated, so I went ahead.

The thing seems to be stable now and I hope it will stay like that.

One more question for my (and others') understanding:
**Does the driver of version 5_100_82_112 need to be installed prior tho the whole procedure, or one can start with the 6.20.155.1 in place? The last is in the 13.04 and 5.100.82.112 has to be installed manually.**

Thank you very much!

- Izzo

---

### Post by Hadaka on 2013-05-15
@apochry
  Glad it worked for you, I'm not sure exactly what
your configuration was prior to loading the modified
fix,so its hard to say just why you had to load the driver.
I'll send varunendra a note and have him take a look at this.
If you have any more problems wih this, please start a new
thread and refer or link to this one. We are trying to keep track
of each case where the modified files were used in order to make
any improvements or verify the workaround is stable.
thanks.

---

### Post by varunendra on 2013-05-15
Hello Izzo,
> **apochry said:**
> I have the same issue with the BCM4313 card so I tried the suggested in post #31. When I compile the driver I get the following output:
```
[COLOR=#ff0000]WARNING: modpost: missing MODULE_LICENSE() in /home/izzo/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.o
see include/linux/module.h for more information
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'[/COLOR]

```

Two WARNINGs... Is that alright?
Those are perfectly normal.
Usually you will see many warnings while compiling any source. They are just notifications and can be safely ignored as long as they don't turn into **Errors**. Only in that case we take a close look at the warnings to find the reasons for the errors.

> One more question for my (and others') understanding:
**Does the driver of version 5_100_82_112 need to be installed prior tho the whole procedure, or one can start with the 6.20.155.1 in place? The last is in the 13.04 and 5.100.82.112 has to be installed manually.**
'**Any**' driver installed prior to the procedure will be completely removed from the system by the two commands - 'modprobe -rfv wl' and 'apt-get purge bcmwl-kernel-source' in step #8 of the procedure.

If no driver is installed, these two commands will do nothing.

So, with the inclusion of those two commands, the procedure covers all 'usual' cases and makes sure the further procedure gets a clean slate to write on.

To precisely answer your last question, yes, we are aware that 6.20.155.1 is the default version for 13.04 (by the way, it is not a part of the kernel, and is installed separately when *user* chooses to accept the *suggestion* by the OS). That version is somehow broken, and that's why the older, working version has to be installed manually - with some patching to make it compatible with the latest kernel. Hence the procedure in post #31.

I am eagerly waiting for the release of a fixed version of the wl driver. Meanwhile, we must repeat the above building and installation process after each kernel upgrade (unless a better suggestion is found somewhere) :(

Like Hadaka said, we'd appreciate your feedback on the performance of the driver and any further problems regarding the fix.
Users like you are our only resources to verify and possibly make improvements to the fix, if needed.

Thanks for asking, and welcome to the list of my *victims* :)

---

### Post by apochry on 2013-05-16
Hello guys,

thank you for the work you are doing!

Sorry for the dump question above. I didn't read the commands carefully while copying them (I know, lame of me...).

I am going to disappoint you about the driver...
I don't know why and how it managed to be fast and stable the first two hours after the manual install, but now it behaves totally different:
[LIST]
[*]It takes for ever to connect. The first three times it took btw. 8 and 13 minutes.
[*]If it connects it stays connected for differently long. Sometimes connection brakes in several seconds and It can connect again. Other times stays stays for some minutes, or even an hour or two. At the end end will disconnect unable to connect again within the borders of patience.
[*]Even if it stays for some time that it's awfully slow. It is so slow, that even browsing is impossible (a page like ubuntu.com or ebay.com will load in more than a minute to load)
[/LIST]
I am testing for two hous now, so this is what the written above is based on.

I did another thing as well...
On the same box I still have my previous installation 12.04LTS 32bit so I booted it. There I had issues with the driver as well and "solved" the problem by switching to the open source "brcmsmac".
This driver never performed to good but was satisfactory. Things were still the same in the old ubuntu. Stable (on my home wifi, on the university's "WPA2 Enterprise" secured network disconnects once every 10 to 30 mins), fairly fast, takes a while to connect.
This driver (brcmsmac) seems to be totally useless on 13.04 64bit (my current).

So that's for now from me. I hope my feedback will help somehow.
I would really like to see this thing solved and get rid of the cable once again! So if you want me test something else, I'll be more than happy to do it! 

Thank you!
 - Izzo

---

### Post by varunendra on 2013-05-16
> **apochry said:**
> I am going to disappoint you about the driver...

Not necessarily.
Since you had similar (if not same) problems in 12.04 with that driver, and still have some (even though different) with the brcmsmac, the problem may well be external. Although it being the driver's fault is equally possible.

Please download the "Wireless Script" following the link in my signature, and keep it handy on the desktop. Whenever it disconnects itself and fails to reconnect, run the script and post back the contents of "netinfo.txt" file it generates. It *may* possibly give us some hints about the problem.

Also, when you are struggling with the speed (but are still connected), run and post outputs of -
```
ifconfig
iwconfig
nm-tool
ping -c4 google.com
```

For encryption type in router, WPA2-PSK is recommended (whereas WPA/WPA2 mixed mode is strongly discouraged).

Whatever the reason is, I'm glad you are interested in digging more (not many users show this interest, which is understandable).

One more thing - I am just a learner like you, therefore any conclusions or suggestions I may come up with may be flawed. So keep looking for better alternatives than what I may suggest here (although it seems you already are, which is good for us). :)

---

### Post by apochry on 2013-05-17
Hello,

I did some further testing and here are the results:

First thing I did was to change the router from mixed b/g mode back to only g. With this setting the "brcmsmac" driver can connect, stays connected and and the speed is satisfactory. It behaves as in 12.04. I think, I've changed the router setting to b/g when I was first unable to connect with the "wl" driver in order to test. Than I forgot that and came to the wrong conclusion, that the "brcmsmac" is useless in 13.04. It's not, just don't use mixed b/g mode. I don't know about n - my router does not support it, so I can not test.

Than I changed the WPA/WPA2 mixed mode that I was using to WPA2-PSK as recommended and loaded the "wl" to test further.
I think, it is now somewhat more stable and connects easier, usually from the second time after about a minute (statement based on three attempts). The speed stay the same - it really sucks  making browsing impossible.

Here the requested outputs:
```

izzo@StupiDell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 84:8f:69:cd:XX:XX  
          inet6 addr: fe80::868f:69ff:fecd:94f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72424 (72.4 KB)  TX bytes:43166 (43.1 KB)

eth1      Link encap:Ethernet  HWaddr 64:27:37:de:XX:XX  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:fede:a5f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:631 errors:0 dropped:0 overruns:0 frame:11963
          TX packets:573 errors:20 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:689892 (689.8 KB)  TX bytes:66062 (66.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:892719 (892.7 KB)  TX bytes:892719 (892.7 KB)

izzo@StupiDell:~$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:217  Noise level:164
          Rx invalid nwid:0  invalid crypt:8  invalid misc:0

lo        no wireless extensions.

```

```

izzo@StupiDell:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [BGWG] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        64:27:37:DE:XX:XX

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    EasyBox-600108:  Infra, 1C:C6:3C:60:01:XX, Freq 2417 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    sensitive name: Infra, 00:26:4D:E2:32:XX, Freq 2447 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    The Dark Knight: Infra, 00:15:0C:5D:2C:XX, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA
    Geb_14_03:       Infra, 1C:C6:3C:68:C9:XX, Freq 2422 MHz, Rate 54 Mb/s, Strength 62 WPA2
    WLAN-NHJ:        Infra, 7C:4F:B5:94:5A:XX, Freq 2427 MHz, Rate 54 Mb/s, Strength 64 WPA2
    ALICE-WLAN60:    Infra, 00:1C:28:68:E0:XX, Freq 2457 MHz, Rate 54 Mb/s, Strength 74 WPA2
    *BGWG:           Infra, 00:21:04:1F:XX:XX, Freq 2432 MHz, Rate 0 Mb/s, Strength 100 WPA2
    WLAN:            Infra, 00:12:BF:4B:F0:XX, Freq 2462 MHz, Rate 0 Mb/s, Strength 64 WPA2
    Geb.16 App 2.5:  Infra, 50:7E:5D:1B:2C:XX, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WPA2

  IPv4 Settings:
    Address:         192.168.2.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        84:8F:69:CD:XX:XX

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

```

```

izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.129) 56(84) bytes of data.
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=1 ttl=50 time=46.5 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=2 ttl=51 time=796 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=3 ttl=50 time=332 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3130ms
rtt min/avg/max/mdev = 46.504/391.904/796.498/309.031 ms


izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.137) 56(84) bytes of data.
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=1 ttl=50 time=1283 ms
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=2 ttl=50 time=284 ms
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=3 ttl=50 time=54.1 ms
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=4 ttl=51 time=538 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3009ms
rtt min/avg/max/mdev = 54.161/540.307/1283.876/462.279 ms, pipe 2


izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.129) 56(84) bytes of data.
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=1 ttl=50 time=51.0 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=2 ttl=50 time=736 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=3 ttl=50 time=44.3 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=4 ttl=50 time=55.0 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3706ms
rtt min/avg/max/mdev = 44.330/221.759/736.589/297.262 ms
izzo@StupiDell:~$

```

I will be using the "brcmsmac" driver for now.
I would however try anything you guys suggest.

I really think the problem is driver related. I used the laptop only several hours on Windows when it arrived an year ago, bur I didn't notice any wifi misbehavior whatsoever. I than purged Win, so I can't test it now. My flatmate is fine with his Centrino card and Windows. Another two older Linux laptops and various Android devices working just fine. 

Thank you!
 - Izzo

---

### Post by apochry on 2013-05-17
... and just as a reference a pink with the "**brcmsmac**" driver in use:

```

izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.142) 56(84) bytes of data.
64 bytes from muc03s01-in-f14.1e100.net (173.194.35.142): icmp_req=1 ttl=51 time=174 ms
64 bytes from muc03s01-in-f14.1e100.net (173.194.35.142): icmp_req=2 ttl=50 time=207 ms
64 bytes from muc03s01-in-f14.1e100.net (173.194.35.142): icmp_req=3 ttl=50 time=210 ms
64 bytes from muc03s01-in-f14.1e100.net (173.194.35.142): icmp_req=4 ttl=50 time=305 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 174.704/224.491/305.342/48.738 ms


izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.131) 56(84) bytes of data.
64 bytes from muc03s01-in-f3.1e100.net (173.194.35.131): icmp_req=1 ttl=50 time=280 ms
64 bytes from muc03s01-in-f3.1e100.net (173.194.35.131): icmp_req=2 ttl=51 time=156 ms
64 bytes from muc03s01-in-f3.1e100.net (173.194.35.131): icmp_req=4 ttl=50 time=249 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3008ms
rtt min/avg/max/mdev = 156.657/228.922/280.405/52.613 ms


izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.133) 56(84) bytes of data.
64 bytes from muc03s01-in-f5.1e100.net (173.194.35.133): icmp_req=1 ttl=50 time=140 ms
64 bytes from muc03s01-in-f5.1e100.net (173.194.35.133): icmp_req=2 ttl=50 time=226 ms
64 bytes from muc03s01-in-f5.1e100.net (173.194.35.133): icmp_req=3 ttl=50 time=243 ms
64 bytes from muc03s01-in-f5.1e100.net (173.194.35.133): icmp_req=4 ttl=51 time=132 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 132.181/185.765/243.867/49.962 ms

```

---

### Post by varunendra on 2013-05-18
> **apochry said:**
> 
```

izzo@StupiDell:~$ ifconfig
....
....

eth1      Link encap:Ethernet  HWaddr 64:27:37:de:XX:XX  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:fede:a5f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:631 errors:0 dropped:0 overruns:0 **[COLOR="#FF0000"]frame:11963[/COLOR]**
          TX packets:573 **[COLOR="#FF0000"]errors:20[/COLOR]** dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:689892 (689.8 KB)  TX bytes:66062 (66.0 KB)
          Interrupt:16 
```
What a mess!! I've no idea what may be causing this, but it certainly ain't good!
If you are still testing, please try changing the "MTU" in your wireless connection settings from "automatic" to "1492" (restore it back if it makes no difference). Connect, use for a while and see if the "frame" errors still occur. In a wired connection, they usually occur due to a bad cable or bad contact. But can't even guess about wireless, especially when the other driver is working fine.

Now this -
> ```
izzo@StupiDell:~$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: **[COLOR="#FF0000"]Not-Associated[/COLOR]**   
          **Link Quality:[COLOR="#FF0000"]5[/COLOR]**  Signal level:217  **Noise level:164**
          Rx invalid nwid:0  invalid crypt:8  invalid misc:0
```
..is the second time I am seeing this weird output. Are you sure it was connected when you got this output? Although sounds a stupid question to myself, especially given the nm-tool output below, but I am.. :confused:

> ```
izzo@StupiDell:~$ nm-tool
NetworkManager Tool

State: connected (global)

- Device: eth1  [BGWG] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  **State:             [COLOR="#0000CD"]connected[/COLOR]**
  Default:           yes
  HW Address:        64:27:37:DE:XX:XX

  Capabilities:
    **Speed:           54 Mb/s**

 (blah-blah-blah...)
```

And finally -
> ```
izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.129) 56(84) bytes of data.
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=1 ttl=50 time=46.5 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=2 ttl=51 time=**[COLOR="#FF0000"]796 ms[/COLOR]**
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=3 ttl=50 time=332 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, **25% packet loss**, time 3130ms
rtt min/avg/max/mdev = 46.504/391.904/796.498/309.031 ms


izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.137) 56(84) bytes of data.
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=1 ttl=50 time=**[COLOR="#FF0000"]1283 ms[/COLOR]**
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=2 ttl=50 time=284 ms
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=3 ttl=50 time=54.1 ms
64 bytes from muc03s01-in-f9.1e100.net (173.194.35.137): icmp_req=4 ttl=51 time=**538 ms**

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3009ms
rtt min/avg/max/mdev = 54.161/540.307/1283.876/462.279 ms, pipe 2


izzo@StupiDell:~$ ping -c4 google.com
PING google.com (173.194.35.129) 56(84) bytes of data.
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=1 ttl=50 time=51.0 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=2 ttl=50 time=**[COLOR="#FF0000"]736 ms[/COLOR]**
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=3 ttl=50 time=44.3 ms
64 bytes from muc03s01-in-f1.1e100.net (173.194.35.129): icmp_req=4 ttl=50 time=55.0 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3706ms
rtt min/avg/max/mdev = 44.330/221.759/736.589/297.262 ms
izzo@StupiDell:~$
```

Whatever be the reason, given that weirdness, I think -
> I will be using the "brcmsmac" driver for now.
..is a good idea.
What I suggested (changing MTU; can't think of anything else right now) is just for sake of testing, if you are interested. And yes, me too now think it is a driver issue. Although you are the only one (of the four people so far) who has reported this problem. I guess others might be just lucky or didn't care that much.

One more thing, I recommend, since you are directly affected, you should register on launchpad and add yourself to the list of "affected" users to this bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281)

..and post a comment with the description of the problem and this "workaround", and that it is proving to be inefficient as of now. Do mention that you are using 13.04 (you might be redirected to another more recent bug due to this).

As the brcmsmac seems relatively stable, do you think its performance is good enough to keep people happy?

---

### Post by alvio on 2013-05-30
> **varunendra said:**
> [SIZE=4][COLOR=#800000]**[Information Part]**[/COLOR][/SIZE]
Did some research with the "asm/system.h" error and as per comment #3 at [this]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506") (unrelated) bug report page, asm/system.h seems to have been intentionally dropped in kernel 3.4-rc1~54 and later : [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0195c002](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0195c002)

As a result, any package that tries to 'include' it during build process will fail in the newer kernels. Workaround is to get rid of all "#include asm/system.h" lines in the files containing it.

Accordingly, there is a patch suggested at [fedora forums]("http://forums.fedoraforum.org/showpost.php?p=1583224&postcount=7") that worked here at my 13.04 64-bit test VM.
[SIZE=4][COLOR=#800000]**[End of Information Part]**[/COLOR][/SIZE]

So here is what 'should' work for you too -
[LIST=1]
[*]Download the driver suitable to your architecture (32/64 bit) from here : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) [COLOR=#000080]*(EDIT 2: use 'arch' command to find what architecture you are using. "x86_64" means 64-bit, "i386" or "i686" mean 32-bit)*[/COLOR] 
[*]Copy the downloaded file to your desktop > Right-click > "Extract Here". 
[*]Open the **src/wl/sys/wl_linux.c** file in the extracted directory. 
[*]Delete the line that says "**#include <asm/system.h>**" (line no. 43 in current version) 
[*]Search for another line that says "**.ndo_set_multicast_list**" (line no. 388 in current version) and change it to "**.ndo_set_rx_mode**". The line should now read -  Proofread, save and close the file. 
[*]Now open a terminal and go into the extracted folder - ```
cd ~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112
```(assuming **"hybrid-portsrc_x86_64-v5_100_82_112"** is the name of the extracted directory) 
[*]Once in, compile and build the driver with make command : ```
make
``` 
[*]If successful, you should see "wl.ko" file in the extracted directory. If it is there, ONLY THEN proceed as follows (in the same terminal, same directory) - 
[/LIST]
[COLOR=#800000]EDIT : Just to be clear, enter one command at a time > let it finish > enter next command[/COLOR]
```
sudo su
modprobe -rfv wl
apt-get purge bcmwl-kernel-source
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
depmod -a
modprobe -v wl
update-initramfs -u
exit
```
Watch out for errors and report back if any occur. The main part is building of the wl.ko driver. Rest are just its placement and automation.

Let's hope you won't have to compromise with OS switching after this finishes.


This worked perfect... thanks a lot:KS

---

### Post by varunendra on 2013-05-31
> **alvio said:**
> This worked perfect... thanks a lot:KS

Wow! Looks like your first post, so.... Welcome to the forums alvio!! :)

And that's a great feedback to have, thanks for the confirmation.
It would be even better if you could provide some information about the version of ubuntu you are using -
```
lsb_release -a
uname -mr
```

And if there are any issues related to the fix, now or later, please let us know.

Cheers!:KS

---

### Post by digi007 on 2013-05-31
> **varunendra said:**
> Wow! Looks like your first post, so.... Welcome to the forums alvio!! :)

And that's a great feedback to have, thanks for the confirmation.
It would be even better if you could provide some information about the version of ubuntu you are using -
```
lsb_release -a
uname -mr
```

And if there are any issues related to the fix, now or later, please let us know.

Cheers!:KS

Hi, Varunendra

This is my first post and is a question and reporting of a problem. 

I am still kind of a newbe to the linux world and I keep experimenting. I dont like windows musch (except for official purpose, no choice) and due to my interest in PC world, I keep trying these distors like ubuntu and linux mint etc. 

Currently I am using ubuntu 12.04 (on my wife's lappy) and did a fresh install of Linux Mint 15 today. I had no issues as such with my wifi previously with older versions of both of these distros. But, wireless on my Dell Vostro 3350 doesnt seem to work. I tried everyhting you have said, few times but no result. 

Initially I got the wireless network detected but just could not connect. After few attempts, not wifi is on but it doesnt detect any network. 

I am clueless and dont know what to do. Have spent at least 4 hours online searching for solutions and tried probably everything but no result. 

Can you please help?

Thanks

Digi

---

### Post by varunendra on 2013-05-31
Hello Digi!
> **digi007 said:**
> This is my first post..
Then let me first have the privilege to welcome you to the forums! So.. Welcome aboard Digi !! :)

> Currently I am using ubuntu 12.04 (on my wife's lappy) and did a fresh install of Linux Mint 15 today. I had no issues as such with my wifi previously with older versions of both of these distros. But, wireless on my Dell Vostro 3350 doesnt seem to work. I tried everyhting you have said, few times but no result.
Please show us outputs of -
```
lspci -nnk | grep -iA2 net
uname -mr
lsb_release -d
lsmod
```
You may just copy-paste the above commands in terminal, enter one at a time (shortcut key to open terminal on Ubuntu is 'Ctrl + Alt + T').

While posting the outputs, click on **#** button above the edit box, and paste the output in-between the 'Code' tags generated by the button.

---

### Post by digi007 on 2013-06-01
```
digi@digi-Vostro-3350 ~ $ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Vostro 3350 [1028:04b2]
    Kernel driver in use: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: wl

digi@digi-Vostro-3350 ~ $ uname -mr
3.8.0-19-generic x86_64
digi@digi-Vostro-3350 ~ $ lsb_release -d
Description:    Linux Mint 15 Olivia

digi@digi-Vostro-3350 ~ $ lsmod
Module                  Size  Used by
ppp_deflate            12950  0 
bsd_comp               12921  0 
ppp_async              17413  1 
crc_ccitt              12707  1 ppp_async
option                 34090  1 
usb_wwan               15334  1 option
usbserial              36911  5 option,usb_wwan
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
lib80211_crypt_tkip    17379  0 
wl                   3074449  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17377  0 
snd_rawmidi            30180  1 snd_seq_midi
dell_wmi               12681  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
sparse_keymap          13890  1 dell_wmi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_timer              29425  2 snd_pcm,snd_seq
videobuf2_core         40513  1 uvcvideo
mac_hid                13205  0 
cfg80211              510937  1 wl
psmouse                95870  0 
videodev              129260  2 uvcvideo,videobuf2_core
mei                    41158  0 
btusb                  22474  0 
dell_laptop            17369  0 
dcdbas                 14397  1 dell_laptop
microcode              22881  0 
dm_multipath           22843  0 
scsi_dh                14843  1 dm_multipath
lpc_ich                17061  0 
bluetooth             228619  22 bnep,btusb,rfcomm
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
serio_raw              13215  0 
btrfs                 785967  0 
zlib_deflate           26885  2 btrfs,ppp_deflate
libcrc32c              12615  1 btrfs
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
ums_realtek            17949  0 
usb_storage            57204  1 ums_realtek
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
i915                  600351  3 
wmi                    19070  1 dell_wmi
video                  19390  1 i915
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0
```

---

### Post by digi007 on 2013-06-01
Hi Varun, 

Thank you so much for your warm welcome and quick reponse. :) 

I wanted to inform you that in continuation with my experiments I have reinstalled the driver version 6 from synaptic package manager. 

I can see my wifi network (which is WPA2 Enterprise from Tikona) but cant connect. It keeps asking for username and password but nothing happens. 

Similar was the case after following your detailed guide few times. 

I am not sure whats happening or if I am making any mistake. And I hope the driver will be fixed officially. 

Thanks for your help. 

Cheers, 

Digi

---

### Post by varunendra on 2013-06-01
> **digi007 said:**
> I wanted to inform you that in continuation with my experiments I have reinstalled the driver version 6 from synaptic package manager. 

I can see my wifi network (which is WPA2 Enterprise from Tikona) but cant connect. It keeps asking for username and password but nothing happens.
Sounds like a different problem than the driver compatibility issue we have been addressing here.

But since you have the same kernel version as originally discussed in this thread, I'd suggest to once more try the alternate version of the driver as I suggested in post #31. At least we will be sure that the known issues with this card and the default driver combination are ruled out. Once that one is installed, follow the "Wireless Script" link in my signature, do what the linked post suggests there and post back the contents (or pastebin link) of the "wireless-info.txt" file generated by the script.

Along with that, please also post -
```
modinfo wl
```
..to confirm that we indeed have the intended version of the driver in use.


**PS:**
Alternatively, you may try the relatively easier solution of using updated firmware with the native brcmsmac driver, as suggested by praseodym, and reportedly working fine : [http://ubuntuforums.org/showthread.php?t=2148444&p=12663032#post12663032](http://ubuntuforums.org/showthread.php?t=2148444&p=12663032#post12663032)
This solution requires you to remove the wl driver and use the native brcmsmac instead. Please let us know if you try this and it works better. Although I suspect you may have an additional problem than the driver alone.

---

### Post by digi007 on 2013-06-01
output of modinfo wl after the process again

[HTML]digi@digi-Vostro-3350 ~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112 $ modinfo wlfilename:       /lib/modules/3.8.0-19-generic/updates/wl.ko
srcversion:     49E2D90EE4D6877632DEDB0
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string

[/HTML]

result of wireless script

```
*************** info trace ***************

***** uname -a *****

Linux digi-Vostro-3350 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    LinuxMint
Description:    Linux Mint 15 Olivia
Release:    15
Codename:    olivia

***** lspci *****

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
    Subsystem: Dell Vostro 3350 [1028:04b2]
    Kernel driver in use: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 003 Device 008: ID 19d2:fff1 ZTE WCDMA Technologies MSM 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 004: ID 0c45:642c Microdia 
Bus 002 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 / Wintech CM-5098 Optical Mouse
Bus 002 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 002 Device 005: ID 0bda:0138 Realtek Semiconductor Corp. Card reader

***** iwconfig *****

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

wl                   2573614  0 
lib80211               14352  2 wl,lib80211_crypt_tkip

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    tikonawifi:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 0 Mb/s, Strength 67 WPA2 Enterprise


- Device: ttyUSB0  [Reliance connection] ---------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         115.240.107.173
    Prefix:          32 (255.255.255.255)
    Gateway:         220.224.141.129

    DNS:             220.226.100.40
    DNS:             220.226.6.104


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"tikonawifi"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-57 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Encryption key:eek:n
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


***** resolv.conf *****

nameserver 127.0.1.1

nameserver 208.67.222.222
nameserver 208.67.220.220

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist brcmsmac
blacklist bcma

***** dmesg *****

[12255.662790] wlc_lcnphy_rx_gain_tbl_free_entry = 5
[12362.772394] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112

****************** done ******************
```

---

### Post by varunendra on 2013-06-01
> **digi007 said:**
> filename:       /lib/modules/3.8.0-19-generic**[COLOR="#FF0000"]/updates/wl.ko[/COLOR]**
srcversion:     49E2D90EE4D6877632DEDB0
Hmm.. the driver version is same, but the location of the driver suggests you may have followed a slightly different way to install it, although that shouldn't affect its performance. So.. did you follow another 'similar' method or mix up this one with it? Because as per my post, this driver should have been located in /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless directory.

While the location shouldn't affect its performance, I am suspecting that the other method (if you followed one) may have other stuff that may interfere with the connectivity. Or may be something else you tried. For example, I'm not sure yet what is module lib80211_crypt_tkip required for, which is present in your lsmod.

Also -
```
  Wireless Access Points 
    tikonawifi:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 0 Mb/s, Strength 67 **WPA2 Enterprise**
```

Are you using WPA2 Enterprise encryption type? Try changing it to WPA2 Personal in network manager and pure WPA2-PSK (AES) in the access point.


**PS:**
Oh, and please wrap the output in your post within 'Code' tags as you have done in post #44 above. It looks scary at the moment :D

---

### Post by digi007 on 2013-06-01
Hi, 

First of all apologies for these late replies, i do want to solve this problem ASAP. Actually, the OS is completely set us now and only thing not working is wifi, which is the key for me. 

For trying the different methods, yes, I have tried few, including downloading and installing version 5 of the driver and blacklist etc. I think I have messed up. Any way back? can I start from zero? meaning like a new installation. 

For Tikona, its their network and router which does not allow any other method, only signal is WPA2 Enterprise. And I have used till yesterday mint 14 from the last 4 months and it worked so flawlessly that I didnt log in to windows for weeks. But, after mint 15, wifi is the biggest and only problem. Please help me get it work :(

And sorry for that code thing, it was my bad :)

Thanks, 

Digi

---

### Post by varunendra on 2013-06-01
You can still edit your post to wrap the output in code tags. I can request a mod to do that for you but I think of it as a good practice to ask the poster to do it as a practice. :)

Also, a support forum like this is a place to post and have patience while someone knowledgeable and/or interested enough sees it and has time to reply. So quick replies, while a good thing, aren't to be much expected here. I wasn't expecting that from you, you shouldn't expect that from me :)

Onto the problem -

Trying different methods isn't necessarily a bad thing (well.., it often does confuse things, but they can be dealt with), and a fresh installation isn't a guaranteed fix. So I think we can proceed with what we have at the moment. Accordingly, assuming you haven't tried yet another solution since your last post :P, please try -
```
sudo modprobe -rfv lib80211_crypt_tkip
sudo modprobe -rfv wl
sudo modprobe -v wl
```
Try to connect and see if things improved. If not, do a restart and post outputs of -
```
lsmod
dmesg | grep -E 'wl|eth|brcm|bcm|lib80211'
cat /var/log/syslog | grep -iE 'wl|eth|brcm|bcm|network|lib80211'
```

---

### Post by digi007 on 2013-06-02
> **varunendra said:**
> You can still edit your post to wrap the output in code tags. I can request a mod to do that for you but I think of it as a good practice to ask the poster to do it as a practice. 

I agree and I will edit it :) 

> Also, a support forum like this is a place to post and have patience while someone knowledgeable and/or interested enough sees it and has time to reply. So quick replies, while a good thing, aren't to be much expected here. I wasn't expecting that from you, you shouldn't expect that from me 


It must be the communication problem, what I meant was, I am being late in responding to post results and replies. I understand your point I never expected quick responses on forums :) so no worries 

Onto the problem -

> Trying different methods isn't necessarily a bad thing (well.., it often does confuse things, but they can be dealt with), and a fresh installation isn't a guaranteed fix. So I think we can proceed with what we have at the moment. Accordingly, assuming you haven't tried yet another solution since your last post , please try -
```
sudo modprobe -rfv lib80211_crypt_tkip
sudo modprobe -rfv wl
sudo modprobe -v wl
```

Try to connect and see if things improved. If not, do a restart and post outputs of -


I have applied above commands and tried, same problem, then restarted, same problem, after a while it didnt even detect the network while I am sitting next to router :( So, it sometimes doesnt detect the network and if it does then doesnt connect. 


```
lsmod
dmesg | grep -E 'wl|eth|brcm|bcm|lib80211'
cat /var/log/syslog | grep -iE 'wl|eth|brcm|bcm|network|lib80211'
```


The results of above commands as below, 

```
digi@digi-Vostro-3350 ~ $ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
joydev                 17377  0 
lib80211_crypt_tkip    17379  0 
wl                   2573614  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            17369  0 
dcdbas                 14397  1 dell_laptop
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
psmouse                95870  0 
microcode              22881  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
dm_multipath           22843  0 
scsi_dh                14843  1 dm_multipath
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
lib80211               14352  2 wl,lib80211_crypt_tkip
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
serio_raw              13215  0 
btusb                  22474  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
bluetooth             228619  22 bnep,btusb,rfcomm
lpc_ich                17061  0 
soundcore              12680  1 snd
mei                    41158  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
ums_realtek            17949  0 
usb_storage            57204  1 ums_realtek
wmi                    19070  1 dell_wmi
i915                  600351  3 
ahci                   25731  2 
libahci                31364  1 ahci
video                  19390  1 i915
i2c_algo_bit           13413  1 i915
r8169                  67446  0 
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper


```

```
digi@digi-Vostro-3350 ~ $ dmesg | grep -E 'wl|eth|brcm|bcm|lib80211'
[    1.065163] r8169 0000:05:00.0 eth0: RTL8168e/8111e at 0xffffc9000065c000, 18:03:73:a3:9a:c1, XID 0c200000 IRQ 46
[    1.065167] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   16.379868] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.501722] lib80211: common routines for IEEE802.11 drivers
[   16.501726] lib80211_crypt: registered algorithm 'NULL'
[   17.168549] wl: module license 'unspecified' taints kernel.
[   17.214720] lib80211_crypt: registered algorithm 'TKIP'
[   17.282068] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112
[   20.106809] r8169 0000:05:00.0 eth0: link down
[   20.106841] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.107174] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  351.906632] r8169 0000:05:00.0 eth0: link up
[  351.906653] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


```

Thw last one, for some reson the terminal didnt show the complete result, this whatever I could get

```
Jun  2 11:44:38 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:44:38 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:44:38 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:44:38 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:44:38 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:44:38 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:44:39 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Jun  2 11:44:41 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Authentication with 04:4f:aa:5d:1e:c8 timed out.
Jun  2 11:44:41 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:44:41 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:44:42 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 11:44:43 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Trying to associate with ac:67:06:b6:ab:99 (SSID='tikonawifi' freq=2422 MHz)
Jun  2 11:44:43 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Association request to the driver failed
Jun  2 11:44:43 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 11:44:43 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Associated with 04:4f:aa:5d:1e:c8
Jun  2 11:44:43 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-STARTED EAP authentication started
Jun  2 11:44:43 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:44:43 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:44:44 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:44:44 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:44:44 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:44:44 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:44:45 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Jun  2 11:44:47 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Authentication with 04:4f:aa:5d:1e:c8 timed out.
Jun  2 11:44:47 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:44:47 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:44:48 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 11:44:48 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Trying to associate with 04:4f:aa:5d:1e:c8 (SSID='tikonawifi' freq=2442 MHz)
Jun  2 11:44:48 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Association request to the driver failed
Jun  2 11:44:48 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 11:44:49 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Associated with 04:4f:aa:5d:1e:c8
Jun  2 11:44:49 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-STARTED EAP authentication started
Jun  2 11:44:49 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:44:49 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:44:49 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:44:49 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:44:49 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:44:49 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:44:50 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Jun  2 11:44:52 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Authentication with 04:4f:aa:5d:1e:c8 timed out.
Jun  2 11:44:52 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:44:52 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:44:52 digi-Vostro-3350 NetworkManager[1049]: <warn> Activation (eth1/wireless): association took too long.
Jun  2 11:44:52 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 11:44:52 digi-Vostro-3350 NetworkManager[1049]: <warn> Activation (eth1/wireless): asking for new secrets
Jun  2 11:44:53 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: disconnected -> inactive
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth1/wireless): connection 'tikonawifi' has security, and secrets exist.  No new secrets needed.
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'ssid' value 'tikonawifi'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'scan_ssid' value '1'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'auth_alg' value 'OPEN'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'password' value '<omitted>'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'eap' value 'TTLS'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'fragment_size' value '1300'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'ca_path' value '/etc/ssl/certs'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'ca_path2' value '/etc/ssl/certs'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'identity' value '1100658063'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'bgscan' value 'simple:30:-45:300'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: added 'proactive_key_caching' value '1'
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> Config: set interface ap_scan to 1
Jun  2 11:45:15 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: inactive -> scanning
Jun  2 11:45:16 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Trying to associate with ac:67:06:b6:ab:99 (SSID='tikonawifi' freq=2422 MHz)
Jun  2 11:45:16 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Association request to the driver failed
Jun  2 11:45:16 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 11:45:16 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Associated with 04:4f:aa:5d:1e:c8
Jun  2 11:45:16 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-STARTED EAP authentication started
Jun  2 11:45:16 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:45:19 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:45:19 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:45:19 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:45:19 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:45:19 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:45:20 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Jun  2 11:45:22 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Authentication with 04:4f:aa:5d:1e:c8 timed out.
Jun  2 11:45:22 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:45:22 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:45:23 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 11:45:24 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Trying to associate with 04:4f:aa:5d:1e:c8 (SSID='tikonawifi' freq=2442 MHz)
Jun  2 11:45:24 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Association request to the driver failed
Jun  2 11:45:24 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 11:45:24 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Associated with 04:4f:aa:5d:1e:c8
Jun  2 11:45:24 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-STARTED EAP authentication started
Jun  2 11:45:24 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:45:24 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:45:24 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:45:24 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:45:25 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:45:25 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:45:26 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Jun  2 11:45:28 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Authentication with 04:4f:aa:5d:1e:c8 timed out.
Jun  2 11:45:28 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:45:28 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:45:29 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 11:45:29 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Trying to associate with ac:67:06:b6:ab:99 (SSID='tikonawifi' freq=2422 MHz)
Jun  2 11:45:29 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Association request to the driver failed
Jun  2 11:45:29 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 11:45:29 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Associated with 04:4f:aa:5d:1e:c8
Jun  2 11:45:29 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-STARTED EAP authentication started
Jun  2 11:45:29 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:45:29 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:45:29 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:45:29 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:45:30 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:45:30 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:45:31 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Jun  2 11:45:33 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Authentication with 04:4f:aa:5d:1e:c8 timed out.
Jun  2 11:45:33 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:45:33 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:45:34 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 11:45:34 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Trying to associate with 04:4f:aa:5d:1e:c8 (SSID='tikonawifi' freq=2442 MHz)
Jun  2 11:45:34 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Association request to the driver failed
Jun  2 11:45:34 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 11:45:35 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Associated with 04:4f:aa:5d:1e:c8
Jun  2 11:45:35 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-STARTED EAP authentication started
Jun  2 11:45:35 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:45:35 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:45:35 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:45:35 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:45:35 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:45:35 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:45:36 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Jun  2 11:45:38 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Authentication with 04:4f:aa:5d:1e:c8 timed out.
Jun  2 11:45:38 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:45:38 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:45:39 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jun  2 11:45:39 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Trying to associate with ac:67:06:b6:ab:99 (SSID='tikonawifi' freq=2422 MHz)
Jun  2 11:45:39 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Association request to the driver failed
Jun  2 11:45:39 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: scanning -> associating
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: eth1: Associated with 04:4f:aa:5d:1e:c8
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-STARTED EAP authentication started
Jun  2 11:45:40 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associating -> associated
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25 -> NAK
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=21
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate'
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=1 depth=1 subject='/C=IN/ST=MUMBAI/L=BHANDUP/O=TIKONA DIGITAL NETWORKS/emailAddress=admin@tikona.com/CN=802.1x CA Certificate' err='self signed certificate in certificate chain'
Jun  2 11:45:40 digi-Vostro-3350 NetworkManager[1049]: <warn> Activation (eth1/wireless): association took too long.
Jun  2 11:45:40 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 11:45:40 digi-Vostro-3350 NetworkManager[1049]: <warn> Activation (eth1/wireless): asking for new secrets
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: eth1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  2 11:45:40 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: associated -> disconnected
Jun  2 11:45:40 digi-Vostro-3350 NetworkManager[1049]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  2 11:45:43 digi-Vostro-3350 NetworkManager[1049]: <warn> No agents were available for this request.
Jun  2 11:45:43 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jun  2 11:45:43 digi-Vostro-3350 NetworkManager[1049]: <info> Marking connection 'tikonawifi' invalid.
Jun  2 11:45:43 digi-Vostro-3350 NetworkManager[1049]: <warn> Activation (eth1) failed for connection 'tikonawifi'
Jun  2 11:45:43 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  2 11:45:43 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): deactivating device (reason 'none') [0]
Jun  2 11:46:10 digi-Vostro-3350 NetworkManager[1049]: <info> Saved default wired connection 'Wired connection 1' to persistent storage
Jun  2 11:46:11 digi-Vostro-3350 NetworkManager[1049]:    Ifupdown: get unmanaged devices count: 0
Jun  2 11:46:11 digi-Vostro-3350 NetworkManager[1049]:    Ifupdown: get unmanaged devices count: 0
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): carrier now ON (device state 20)
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun  2 11:46:31 digi-Vostro-3350 kernel: [  351.906632] r8169 0000:05:00.0 eth0: link up
Jun  2 11:46:31 digi-Vostro-3350 kernel: [  351.906653] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Auto-activating connection 'Wired connection 1'.
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  2 11:46:31 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> dhclient started with pid 2270
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  2 11:46:32 digi-Vostro-3350 dhclient: Listening on LPF/eth0/18:03:73:a3:9a:c1
Jun  2 11:46:32 digi-Vostro-3350 dhclient: Sending on   LPF/eth0/18:03:73:a3:9a:c1
Jun  2 11:46:32 digi-Vostro-3350 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xf436d8c)
Jun  2 11:46:32 digi-Vostro-3350 dhclient: DHCPREQUEST of 10.25.235.112 on eth0 to 255.255.255.255 port 67 (xid=0xf436d8c)
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info>   address 10.25.235.112
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info>   prefix 18 (255.255.192.0)
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info>   gateway 10.25.192.1
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info>   nameserver '113.193.1.60'
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info>   nameserver '113.193.0.148'
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  2 11:46:32 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun  2 11:46:32 digi-Vostro-3350 avahi-daemon[1002]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.25.235.112.
Jun  2 11:46:32 digi-Vostro-3350 avahi-daemon[1002]: New relevant interface eth0.IPv4 for mDNS.
Jun  2 11:46:32 digi-Vostro-3350 avahi-daemon[1002]: Registering new address record for 10.25.235.112 on eth0.IPv4.
Jun  2 11:46:33 digi-Vostro-3350 avahi-daemon[1002]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::1a03:73ff:fea3:9ac1.
Jun  2 11:46:33 digi-Vostro-3350 avahi-daemon[1002]: New relevant interface eth0.IPv6 for mDNS.
Jun  2 11:46:33 digi-Vostro-3350 avahi-daemon[1002]: Registering new address record for fe80::1a03:73ff:fea3:9ac1 on eth0.*.
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <info> DNS: starting dnsmasq...
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <warn> dnsmasq not available on the bus, can't update servers.
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <error> [1370153793.863408] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <warn> DNS: plugin dnsmasq update failed
Jun  2 11:46:33 digi-Vostro-3350 NetworkManager[1049]: <info> Writing DNS information to /sbin/resolvconf
Jun  2 11:46:34 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) successful, device activated.
Jun  2 11:46:34 digi-Vostro-3350 NetworkManager[1049]: <warn> dnsmasq appeared on DBus: :1.48
Jun  2 11:46:34 digi-Vostro-3350 NetworkManager[1049]: <info> Writing DNS information to /sbin/resolvconf
Jun  2 11:46:52 digi-Vostro-3350 NetworkManager[1049]: <info> (eth0): IP6 addrconf timed out or failed.
Jun  2 11:46:52 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  2 11:46:52 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  2 11:46:52 digi-Vostro-3350 NetworkManager[1049]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  2 11:48:33 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jun  2 11:48:33 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): deactivating device (reason 'none') [0]
Jun  2 11:48:33 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): taking down device.
Jun  2 11:48:33 digi-Vostro-3350 avahi-daemon[1002]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  2 11:48:33 digi-Vostro-3350 avahi-daemon[1002]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e6d5:3dff:fee7:5459.
Jun  2 11:48:33 digi-Vostro-3350 avahi-daemon[1002]: Withdrawing address record for fe80::e6d5:3dff:fee7:5459 on eth1.
Jun  2 11:48:33 digi-Vostro-3350 NetworkManager[1049]: <info> WiFi hardware radio set disabled
Jun  2 11:48:33 digi-Vostro-3350 NetworkManager[1049]: <info> WiFi now disabled by radio killswitch
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): bringing up device.
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> WiFi hardware radio set enabled
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> WiFi now enabled by radio killswitch
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1) supports 1 scan SSIDs
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <warn> Trying to remove a non-existant call id.
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: starting -> ready
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1): supplicant interface state: ready -> inactive
Jun  2 11:48:35 digi-Vostro-3350 NetworkManager[1049]: <info> (eth1) supports 1 scan SSIDs
Jun  2 11:48:37 digi-Vostro-3350 avahi-daemon[1002]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e6d5:3dff:fee7:5459.
Jun  2 11:48:37 digi-Vostro-3350 avahi-daemon[1002]: New relevant interface eth1.IPv6 for mDNS.
Jun  2 11:48:37 digi-Vostro-3350 avahi-daemon[1002]: Registering new address record for fe80::e6d5:3dff:fee7:5459 on eth1.*.
```

So, lets see if we can find solution to this, this has become challanging and itresting now. 

Digi

PS
in syterm info the process info says Intel Core i5-2430M CPU @ 2.40 GHz x 2 (it should be 4, its quad core processor) is this problem connected to wifi one?

---

### Post by varunendra on 2013-06-02
> **digi007 said:**
> It must be the communication problem, what I meant was, I am being late in responding to post results and replies. I understand your point I never expected quick responses on forums :) so no worries
Indeed a communication problem! Because what I meant was that you don't need to apologize for delays.

Oh, and except in some very specific (rare) cases, you almost always need only two kind of tags (BB codes) -
'Quote' for quoting something that someone has said,
'Code' for posting terminal commands and their outputs.

You have been using 'Html' tags so far, which is not bad, but it is meant for posting html codes only.

Back to the issue -

For some reason, the "lib80211_crypt_tkip" driver is still loading -
> ```
digi@digi-Vostro-3350 ~ $ lsmod
Module                  Size  Used by
......
**lib80211_crypt_tkip**    17379  0
.....
lib80211               14352  2 wl,**[COLOR="#FF0000"]lib80211_crypt_tkip[/COLOR]**
.....

```
I'm still not sure if it is required at all. Instead, it is perhaps just conflicting with the 'wl' driver over lib80211 module. So let's try to prevent it from loading. Please do -
```
echo "blacklist lib80211_crypt_tkip" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv wl
sudo modprobe -rfv lib80211
sudo modprobe -v wl
```

Plus, this seems to be a known problem in 13.04 -
> 
```
Jun  2 11:45:40 digi-Vostro-3350 wpa_supplicant[1085]: **TLS: Certificate verification failed**, error 19 (self signed certificate in certificate chain) depth 1 for ......
```
Assuming your wireless network connection name is "tikonawifi" (or else, change it to whatever it is), please do -
```
sudo sed -i 's:system-ca-certs=true:system-ca-certs=false:' /etc/NetworkManager/system-connections/tikonawifi
```
This will change the line "system-ca-certs=**true**" to "system-ca-certs=**false**" in the above keyfile.

Now do -
```
sudo service network-manager restart
```
or simply reboot. Try to connect and see if you can. If not, check if the "lib80211_crypt_tkip" module is loaded again -
```
lsmod | grep lib80211
```

If the problem still exists, post back -
```

lsmod | grep -E 'wl|lib80'
cat /etc/modprobe.d/blacklist.conf | tail -4
dmesg | grep -E 'wl|eth|brcm|bcm|lib80211'
cat /var/log/syslog | grep -iE 'wl|eth|brcm|bcm|network|lib80211' | tail -40
sudo cat /etc/NetworkManager/tikonawifi

```
**[COLOR="#FF0000"]Caution !![/COLOR] The last command output may contain your wifi password if you have saved it. So check that and remove *(password, mac id)* before posting here !**

---

### Post by kellyhenry on 2013-06-02
I just installed Ubuntu on my hp mini110, and since then my wireless adapter won't just work. Please help me as I really need this to work. Thanks. You guys are doing a great job.

---

### Post by varunendra on 2013-06-02
> **kellyhenry said:**
> I just installed Ubuntu on my hp mini110, and since then my wireless adapter won't just work. Please help me as I really need this to work. Thanks. You guys are doing a great job.

Welcome to the Ubuntu Forums kh! :)

Please show us the outputs of (open a terminal with Ctrl+Alt+T, and type or copy-paste these commands one by one in it) -
```
uname -mr
lsb_release -d
lspci -nnk | grep -iA2 net
```

While posting the outputs, please wrap them in 'Code' tags by clicking at '**#**' button above the edit box, then copy-pasting the outputs in-between the tags generated by the button (follow the example link in my signature if you need a detailed example).

---

### Post by digi007 on 2013-06-02
Hi, 

thanks for remedy steps. 

I did follow them and restarted the system, but for some reason that lib80211 did not get removed. so I re-did and re-did and re-did. but it wont go. 

```
digi@digi-Vostro-3350 ~ $ lsmod | grep lib80211
lib80211_crypt_tkip    17379  0 
lib80211               14352  2 wl,lib80211_crypt_tkip


```

However, my wifi seem to have started working but i need to load the wl.ko driver manually on each start, which is not really comfortable but I can live with it as long as it works. 

but, this is confusing, which driver is working? will it create any problem in future? I am happy for now as it is working for now. 

Thanks a lot for your help, I also believe your fix in post #31 woeks :)

You have been awesome :)

Digi

---

### Post by varunendra on 2013-06-02
> **digi007 said:**
> You have been awesome :)
&#2350;&#2379;&#2327;&#2375;&#2350;&#2381;&#2348;&#2379; &#2326;&#2364;&#2369;&#2358; &#2361;&#2369;&#2310; ! :D


> I did follow them and restarted the system, but for some reason that lib80211 did not get removed. so I re-did and re-did and re-did. but it wont go. 
....
....
However, my wifi seem to have started working but i need to load the wl.ko driver manually on each start, which is not really comfortable but I can live with it as long as it works. 

but, this is confusing, which driver is working?

If it works only when you load the wl module manually, then it is clearly the wl and lib80211 modules that are working (lib80211 is a dependency of wl, while lib80211_crypt_tkip is not).

I believe it was the ca_certificate authentication that was the major issue. Now that you can connect using wl driver, please try again -
```
sudo modprobe -rfv lib80211_crypt_tkip
sudo modprobe -rfv wl
sudo modprobe -v wl
```
This *should* remove the lib80211_crypt_tkip driver and reload both wl and lib80211. Do not restart after this, just try to connect and see if it is working. If it is, we can try either the gentleman way to prevent "lib80211_crypt_tkip" from loading, or can go straightaway to the crude, cruel way to remove it through rc.local file.

Just try the above three commands again and check '**lsmod | grep lib80211**' to see if the "lib80211_crypt_tkip" module actually stays unloaded and the wireless works without it. Let me know the status of lsmod and connectivity, and if it happens to be what I'm expecting, we'll automate this all.

---

### Post by digi007 on 2013-06-02
Hi, 

So, I tried those 3 commands and the wifi is still working hurreyyyyyyyy :) 

But I still have to load the driver manually and dont think that crypt tkip is gone yet. 

the result of lsmod | grep lib80211

```
digi@digi-Vostro-3350 ~ $ lsmod | grep lib80211
lib80211_crypt_tkip    17379  0 
lib80211               14352  2 wl,lib80211_crypt_tkip


```

So, I guess we are just one step away. let's kill it:)

Cheers, 

Digi

---

### Post by varunendra on 2013-06-02
> **digi007 said:**
> Hi, 

So, I tried those 3 commands and the wifi is still working hurreyyyyyyyy :) Yeah, add some extra length in "hurreyyyyyyyy" for me too..

> But I still have to load the driver manually and dont think that crypt tkip is gone yet. 

the result of lsmod | grep lib80211

```
digi@digi-Vostro-3350 ~ $ lsmod | grep lib80211
lib80211_crypt_tkip    17379  0 
lib80211               14352  2 wl,lib80211_crypt_tkip

```
Loading the wl driver automatically should be easier (although it should have been automated after loading it, and then updating initramfs). Just do -
```
echo "wl" | sudo tee -a /etc/modules
```
Reboot and it should be loaded already.

However, the loading of lib80211_crypt_tkip is mysterious to me. Did it really get unloaded after the first modprobe command? It should have been removed after the first command, and shouldn't have got loaded again unless some other driver called it back. If it is not required, then its presence may cause conflicts, creating connection problems.

Just to show me what is happening with these, please run the three commands again and post back all the activity from the terminal.

---

### Post by digi007 on 2013-06-02
> =varunendra;12674267]Yeah, add some extra length in "hurreyyyyyyyy" for me too..

here you go hurrrreeeeeeyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy :) also because the friver is now loading on its own :) 

some results 

```
digi@digi-Vostro-3350 ~ $ lsmod | grep lib80211
lib80211_crypt_tkip    17379  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
digi@digi-Vostro-3350 ~ $ sudo modprobe -rfv lib80211_crypt_tkip
[sudo] password for digi: 
rmmod lib80211_crypt_tkip
digi@digi-Vostro-3350 ~ $ lsmod | grep lib80211
lib80211               14352  1 wl


```

so, now I am not sure whats happening, feel like leaving it as it is because after your continues help from last 2 days and some effort, its finally working and am not feeling like making any mistake :)

however, if the tkip thing can be a problem, lets kill it

Cheers and thank you so much (have learned many things and it has made me even bigger fan of Linux :))

Digi

---

### Post by varunendra on 2013-06-02
> **digi007 said:**
> however, if the tkip thing can be a problem, lets kill it
For that, I need to see if it gets unloaded and remains unloaded after the three modprobe commands. From the last outputs you posted, it seems it does (and that's what I was expecting). However, I asked for outputs of the modprobe commands themselves to see exactly what was going on. Call me paranoid if you wish, I want to make extra sure. :)

So, please do a reboot, run these and post back outputs of all of these -
```
lsmod | grep lib80211
sudo modprobe -rfv lib80211_crypt_tkip
sudo modprobe -rfv wl
sudo modprobe -v wl
lsmod | grep lib80211
cat /etc/modprobe.d/blacklist.conf | tail -4
```
The first command will show the original status after rebooting.
Second one should unload the 'tkip' driver (but I need to see the output of the command, it should be something like "rmmod /lib/modules......" type)
Third one should unload both wl and lib80211 (two lines of output, I need to see them to be sure)
Fourth one should load them back (ONLY wl and lib80211 - again only two lines, that's where I'm doubtful, so need to see the output lines)
Fifth and sixth are just sanity check to make sure everything is like we want.

Seventh step - try to connect and confirm that you can, and the connection is fine.

Given your last outputs, the above shouldn't be required, but again, I'm just paranoid ;)

Assuming in advance that all the above outputs will be what I'm expecting, the nice way to keep it from loading (assuming nothing really needs it) is to run (when the 'tkip' driver is unloaded and is no more present in lsmod) -
```
sudo update-initramfs -u
```
After it finishes successfully, reboot and see if we got rid of it (check the lsmod again).

I'd like to clarify that I'm just 'suspecting' that it may create problems, not sure of it. What I'm 'almost' sure of is - it is not needed, so shouldn't be there.

---

### Post by digi007 on 2013-06-03
Hi, 

This morning, after reboot, the tkip was not loaded, to my pleasant surprise :) So I did not follow your other commands and yes the wifi is working just fine too. 

So, I will do some checks during the day and come back to you with results and my experience by day end today. 

For now, I would like to thank you from the bottom of my heart, you have definitely saved my day as I am little impatient and would have installed the older version of mint. 

Cheers, 

Digi

---

### Post by varunendra on 2013-06-03
No problem at all !
As it was an 'experimental fix', it makes me happier than you that it is working nicely and you find it so satisfactory. :)

Feel free to ping me anytime you need help with it.


**PS:**
The fact that it did not load this time indicates that it was probably the failure of loading a more suitable driver (wl) that the kernel was defaulting to the next available alternative. I think it would have been included in kernel driver tree during some previous attempts with other drivers. Now that we have forced wl to load at startup, maybe kernel doesn't need the 'tkip' one anymore, so didn't load it. But still, there can be 'race conditions' (who loads first!) which won't be good.
But as long as it's working, who cares! :D

---

### Post by digi007 on 2013-06-04
Hi Varun, 

I have tried and tested the wireless driver by rebooting, diconneting-reconnecting etc for the whole day yesterday. 

After the first incident in the morning yesterday, the tkip driver kept getting reloaded. So, i tried to kill it permanently by that update code. But, to my surprise, the wifi stopped working. no wifi no network. 

So, i re-applied those 3 magic commands, wifi was back and working flawlessly, so I checked lsmode, and guess what? tkip was back. wow!!!

hence, after doing all those experiments etc, I have come to a conclusion that tkip driver is indeed a must and being called by the wl driver. I might be wrong. 

But, by internet works just fine on wifi without any problems so I am not making any changes to present configurations. 

Let me know your thoughts. 

Cheers, 

Digi

---

### Post by varunendra on 2013-06-04
Well, some research on it suggests that only one of lib80211 or lib80211_crypt_tkip is required. Based on that it was my 'assumption' that it may conflict with lib80211 which is explicitly required by the wl driver version we compiled (and not lib80211_crypt_tkip, as can be confirmed by "modinfo wl" command).

But while searching for its details I also found a post by someone on archlinux forums (can't find the link again) mentioning that he also needed to load both of them. Now given your experience, it looks like indeed both may be required in some cases (even though [wiki.archlinux]("https://wiki.archlinux.org/index.php/Broadcom_wireless#broadcom-wl") clearly says only one of the two should be loaded).

So yes, as long as you don't experience any problems, let it be the way it is.

---

### Post by Chet Hardin on 2013-06-10
Hey. Thanks for the help. I followed your directions, and my card started working. However, the connection is extremely slow.

Got any suggestions?

Thanks!

---

### Post by varunendra on 2013-06-11
> **Chet Hardin said:**
> Hey. Thanks for the help. I followed your directions, and my card started working. However, the connection is extremely slow.

Got any suggestions?

Thanks!

Please follow the "Wireless Script" link in my signature, follow the instructions there to run the script and post back the contents of the result file it creates.

Thanks.

---

### Post by digi007 on 2013-06-11
Hi Varun, 

I am back, unfortunately with a problem again. 

This time the same problem but on Ubuntu 12,04 LTS. Some info might be helpful,

```
digi@digi-Vostro-3350:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
digi@digi-Vostro-3350:~$ uname -mr
3.5.0-32-generic x86_64
digi@digi-Vostro-3350:~$ 


```

My wifi card is BCM4313. some more info

```
digi@digi-Vostro-3350:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Vostro 3350 [1028:04b2]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: bcma-pci-bridge
digi@digi-Vostro-3350:~$ lsmod
Module                  Size  Used by
wl                   2573608  0 
lib80211               14382  1 wl
b43                   383133  0 
ssb                    52834  1 b43
ppp_deflate            13039  0 
zlib_deflate           27140  1 ppp_deflate
bsd_comp               12995  0 
ppp_async              17540  0 
crc_ccitt              12708  1 ppp_async
option                 30135  0 
usb_wwan               20180  1 option
usbserial              42630  2 option,usb_wwan
usb_storage            49288  0 
brcmsmac              541775  0 
mac80211              555272  2 b43,brcmsmac
brcmutil               14756  1 brcmsmac
cfg80211              208382  3 b43,brcmsmac,mac80211
cordic                 12575  1 brcmsmac
bnep                   18240  2 
rfcomm                 47562  0 
parport_pc             32867  0 
ppdev                  17114  0 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_idt      70774  1 
snd_hda_intel          34063  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
snd_seq_midi           13325  0 
ghash_clmulni_intel    13221  0 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
snd_rawmidi            30750  1 snd_seq_midi
wmi                    19257  1 dell_wmi
snd_seq_midi_event     14900  1 snd_seq_midi
aes_x86_64             17256  1 aesni_intel
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
bcma                   35762  2 b43,brcmsmac
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
psmouse               102506  0 
microcode              23030  0 
serio_raw              13216  0 
btusb                  22432  0 
joydev                 17694  0 
mac_hid                13254  0 
mei                    41410  0 
i915                  535128  3 
lpc_ich                17145  0 
soundcore              15092  1 snd
bluetooth             211812  14 bnep,rfcomm,btusb
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
drm_kms_helper         49259  1 i915
drm                   290344  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
video                  19653  1 i915
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
r8169                  62766  0 
ahci                   25869  4 
libahci                27338  1 ahci


```

Please note that this is after I have tried few fixes, including the one mentioned in your post 31 here. 

First I downgraded the driver from version 6.20 to 5.100. then I blacklisted few entries, then i tried manually laoding the latest firmware for brcmsmac and what not. 

the links I used are, 

[http://askubuntu.com/questions/177100/bcm4313-wireless-card-not-detected-unless-i-boot-with-an-ethernet-connection](http://askubuntu.com/questions/177100/bcm4313-wireless-card-not-detected-unless-i-boot-with-an-ethernet-connection)
[http://askubuntu.com/questions/94021/how-do-i-get-the-broadcom-bcm4313-wireless-working-on-an-asus-1015px](http://askubuntu.com/questions/94021/how-do-i-get-the-broadcom-bcm4313-wireless-working-on-an-asus-1015px) 
[http://askubuntu.com/questions/247993/cant-connect-to-any-wireless-connection-after-updating?lq=1](http://askubuntu.com/questions/247993/cant-connect-to-any-wireless-connection-after-updating?lq=1)

The content of blacklist file

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist mac80211
blacklist brcm80211
blacklist cfg80211
blacklist wl
blacklist lib80211_crypt_tkip
blacklist lib80211
blacklist b43
```

Now I am at the stage where I cant even see my wifi, as per my system, there is no wifi card on this comp. The wired network and CDMA modem works just fine. 

Also, the problem started after the first update and reboot which was that the wifi network did not get connected though detected. later it got connected but slow and fluctuating network and then, no wifi :(

mayday, mayday please help :(

let me know if you can help. It will be great. 

Thanks in avance.

Cheers, 

Digi
```

```

---

### Post by Hadaka on 2013-06-11
Hi Digi007, the reason your wireless is not working is because you
somehow amazingly managed to load 3 different drivers.
1.WL
2.B43
3.BRCMSMAC
Which leads to some serious conflict, not to mention doing varun's mod to the file.
Rather than spend the energy and time to attempt to undo all this, You would really
be better off just to reload 12.04. Once you have a solid wired connection then do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
if you have any problems, post back
thanks.

---

### Post by varunendra on 2013-06-11
> **Hadaka said:**
> Hi Digi007, the reason your wireless is not working is because you
somehow amazingly managed to load 3 different drivers.

:lolflag:

---

### Post by digi007 on 2013-06-11
wow, that is amzing, I cant believe it. 

My bad, sorry, any workaround? it will be good to have this working, everything else seems to be great as far as the OS is concerend. 

Sorry to bother you with my stupid mistakes, I really didnt realise what I was doing

Cheers, 

digi

---

### Post by Hadaka on 2013-06-11
Hi, we are laughing with you,,,not at you, we have all
done like things...this is how we learn. I honestly wouldnt
bother with some kind of work around or undoing what has been
done...you really are better off to reload 12.04...I know its a pain
but its really the best way to fix this.

---

### Post by digi007 on 2013-06-11
Hi, I know what you mean. I am trying to learn. 

But, with the reinstallation of OS, i know that the problem is going to come back, after the first update, my wifi will not connect, again. then, I am at step 0 again. 

There has to be a solution to this problem, I tried many fix, nothing works. This way, I can never use ubuntu, which I dont want to do, I really love it and spending lot of time resolving the issue. 

Please help. 

digi

---

### Post by Hadaka on 2013-06-11
Hi, 12.04 is different than 13.04 in the way it works with
your wifi card...[14e4:4727] so there is no need to compile
any drivers.Witch means on a kernel update it will remain the same.
also..when you load 12.04 and if offers you a proprietary driver...say
NO. ... after you do the reload you will have no wireless. Then from a 
WIRED connection do..
```
sudo apt-get update
sudo apt-get upgrade
```
then do..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
and your driver should be loaded and working.
if not...post back
thanks.

---

### Post by varunendra on 2013-06-11
> **digi007 said:**
> Hi, I know what you mean. I am trying to learn. 

But, with the reinstallation of OS, i know that the problem is going to come back, after the first update, my wifi will not connect, again. then, I am at step 0 again.
Hi digi,

I'd +1 to the idea of doing a fresh install since (I assume) you don't anything to save on it yet.

Even if we get back to step 0 again, that would still be a better situation since won't have to deal with three wrong drivers and related configurations at once. The fact that you have both b43 and wl loaded simultaneously suggests that you must have done quite some manual tweaking to make that happen. So it is easier and better to start fresh.

However, if you are inclined to 'learn', we can try with what you have now, but that may drag the thread unnecessarily long and there will always be a doubt on 'manual' stuff you have done.

In short, currently you need to 'undo' everything you have done manually > double-check that everything is clean > re-install the wl driver > revert to version 5.100.82.38 if the latest one has issues.

On a fresh install, only the last one (or two) step(s) will be needed and it will be much quicker.

I'd be happy to help with whatever you prefer. :)

---

### Post by digi007 on 2013-06-11
Hi Hadaka, 

Thanks for the resolution steps after the fresh install. I will try and follow them. However, can I request more details steps? the reason being, as I have stated earlier, intially, it is going to work just fine, it will start create problems only after the first update, which has to be done. However, the driver is version 6 since the begining ( I think as it is 12.04.2). And that means even if I dont update, I will face a problem after some usage. 

Hi Varun, 

Thanks for your help even in the scenario of current installation. I think I remember things that I have done but of course not everything. So, the i dea of fresh installation seems to be good. 

However, this brings to me another question, as long as I am doing the fresh installation, should I go for 12.04, 13.04 or mint 14 or mint 15? (I know it sounds like a stupid question) 

I have had error problems with 13.04 and mint 15 (cinnamon crash) which I didnt like. So decided to go for LTS which is supposed to be more stable. 

Cheers, 

digi

PS: I am really not liking the fact that I need to do reinstall because I set up my system perfectly. Have installed and configured all the software neeeded etc. Will have to do everything again and plus the most annoying is update of 300 plus MB for my 512 kbps internet connection. I wish I didnt mess up. but cant do much I guess :(

---

### Post by varunendra on 2013-06-11
> **digi007 said:**
> However, this brings to me another question, as long as I am doing the fresh installation, should I go for 12.04, 13.04 or mint 14 or mint 15?
Being an LTS, 12.04 looks like a good option to me. As per your short description, it also seems to suite you best. As far as driver support is concerned, you can always choose to manually install the latest kernel or backported drivers on it. So I'd suggest 12.04, or the one that suits you best.

> PS: I am really not liking the fact that I need to do reinstall because I set up my system perfectly. Have installed and configured all the software neeeded etc. Will have to do everything again and plus the most annoying is update of 300 plus MB for my 512 kbps internet connection. I wish I didnt mess up. but cant do much I guess :(

That sounds like a good enough reason to give it a shot. If you wish, try these -

Remove the wl package -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Then make sure the /etc/modules file doesn't have any custom entries of these drivers (wl, b43, brcmsmac), if you have any other manual tweaks, revert/remove them as well.

Then with a wired connection, do -
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install bcmwl-kernel-source
```
Yes I know this will install a version you are afraid of. But who knows if the problems have been fixed? If it indeed misbehaves, it is not difficult to replace it with an older version.

After this is done, reboot and post back -
```
iwconfig
nm-tool
lsmod
```

**PS:**
You should take a look at AptOnCD to avoid downloading same packages again in case of a fresh reinstall of the same version of Ubuntu.

---

### Post by digi007 on 2013-06-11
Hi Guys, 

So finally, I decided to go ahead for fresh installation and complete the basic software installation etc during the night. Completed majority of the updates as well. 

When the installation finished etc, wifi worked fine. After the first restart too, it was working fine. but, it installed the propritory drivers on itself. So I removed it. 

Even after removing the driver and restart, the wifi was working really smooth. Hence, I completed the installation, update etc. (some updates still needs to installed). But, the next day morning, it started misbehaving. it will keep trying to connect but won't connect, after several attempts it will say, wifi networks disconnected. After few restarts, it did get connected but no interenet connectivity and then again the same problem. 

below is the lsmod output

```
digi@digi-Vostro-3350:~$ lsmod
Module                  Size  Used by
ppp_deflate            13039  0 
zlib_deflate           27140  1 ppp_deflate
bsd_comp               12995  0 
ppp_async              17540  1 
crc_ccitt              12708  1 ppp_async
option                 30089  1 
usb_wwan               20180  1 option
usbserial              42594  5 option,usb_wwan
rfcomm                 47562  0 
bnep                   18240  2 
parport_pc             32867  0 
ppdev                  17114  0 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_idt      70774  1 
arc4                   12530  2 
brcmsmac              541775  0 
mac80211              555198  1 brcmsmac
brcmutil               14756  1 brcmsmac
cfg80211              208382  2 brcmsmac,mac80211
cordic                 12575  1 brcmsmac
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
microcode              23030  0 
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17694  0 
psmouse               102075  0 
uvcvideo               78117  0 
snd_seq_midi           13325  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
btusb                  22432  0 
bluetooth             211812  14 rfcomm,bnep,btusb
snd_rawmidi            30750  1 snd_seq_midi
serio_raw              13216  0 
snd_seq_midi_event     14900  1 snd_seq_midi
lpc_ich                17145  0 
wmi                    19257  1 dell_wmi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  530857  3 
mac_hid                13254  0 
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         49259  1 i915
drm                   290344  4 i915,drm_kms_helper
mei                    41410  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13565  1 i915
video                  19598  1 i915
bcma                   35762  1 brcmsmac
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ums_realtek            18257  0 
uas                    18073  0 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
r8169                  62766  0 
usb_storage            49288  1 ums_realtek


```

Now, I am going to do what Hadaka suggested but that is going to take some time.

below is the output of iwconfig and nm-tool just in case it helps and may be there is something needed to be done before I follow Hadaka's steps.

```
digi@digi-Vostro-3350:~$ iwconfig
ppp0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
digi@digi-Vostro-3350:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: ttyUSB0  [Reliance connection] ---------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         115.241.189.8
    Prefix:          32 (255.255.255.255)
    Gateway:         220.224.141.129

    DNS:             220.226.100.40
    DNS:             220.226.6.104


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        E4:D5:3D:E7:54:59

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    tikonawifi:      Infra, 04:4F:AA:5D:1E:C8, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2 Enterprise


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        18:03:73:A3:9A:C1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by varunendra on 2013-06-12
> **digi007 said:**
> Now, I am going to do what Hadaka suggested but that is going to take some time.

Go ahead and post back how it performs. If having problems, post back lsmod again.

---

### Post by ndefontenay on 2013-06-20
Yay! That totally worked for me.
The modprobe command at line 2 didn't work. No wonder I could not have any wireless!

Thanks a lot.

---

### Post by varunendra on 2013-06-20
> **ndefontenay said:**
> Yay! That totally worked for me.
The modprobe command at line 2 didn't work. No wonder I could not have any wireless!

Thanks a lot.
Welcome to the refugee camp! :P

The **Edit3** above the [commands set]("http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619") in **step #8** addresses the possible error people may get on the command #2. If the error was something else, I would love to look into it.

Also, since people have asked many times now, and is an important part of the workaround, I'm going to make a post on reverting the changes in case it doesn't work. You may wish to keep the link to it handy when created (probably in a few hours from now).

---

### Post by varunendra on 2013-06-20
**_[SIZE=4]How to Un-Install the "wl" driver installed manually as per [Post #31]("http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619") in this thread[/SIZE]_**

**1)** Unload the module if it is loaded :
```
sudo modprobe -rfv wl
```

**2)** Delete it from where we copied it to :
```
sudo rm /lib/modules/`uname -r`/kernel/drivers/net/wireless/wl.ko
```

**3)** Clean up the dependency tree :
```
sudo depmod -a
```

**4)** Update initramfs so that the kernel doesn't keep looking for it :
```
sudo update-initramfs -u
```

That's all to revert all that is done in Post #31 alone.


However, throughout this thread and in some other places while suggesting this workaround, we have also blacklisted the native drivers and added the 'wl' module to /etc/modules file. To revert those changes -

**_[SIZE=4]Reverting Additional Changes[/SIZE]_**

**5) Un-Blacklist any native drivers we may have blacklisted :** Open the /etc/modprobe.d/blacklist.conf file as root -
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
*(replace **gedit** with whatever text editor you have)*

Delete (or comment out by adding '**#**' in the beginning) these lines if they are in the file :
> blacklist brcmsmac
blacklist bcma
blacklist b43
blacklist ssb
Proofread, save and close the file.
*(**_Note_:** We have never recommended to blacklist **b43** or **ssb** for this chip (BCM4313 [14e4:4727]) as it is absolutely not needed, but some users seem to be doing it themselves due to confusing articles/posts here and there. So I've also mentioned them in case you have blacklisted them too).*

**6) Remove "wl" from /etc/modules file :** Open the file as root -
```
gksu gedit /etc/modules
```
(again, replace gedit with whatever text editor you have)

..then delete the line -
> wl
from the file if it is in there. Proofread, save and close the file.

After doing all this, your system will be back to defaults again, ready to start fresh with the wireless (of course unless you have made some extra changes which you will need to revert as well).

Please let me know if you have some suggestions/corrections regarding these two posts ([post #31]("http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619") and this one). Thank you !

---

### Post by joneberger on 2013-07-18
The solution presented in this thread worked like a champ.  Thank you!

---

### Post by varunendra on 2013-07-18
> **joneberger said:**
> The solution presented in this thread worked like a champ.  Thank you!

Thank you for the feedback joneberger, it's good to know it still works. :)

However, just so you and others coming to this thread know, more and more people are reporting that the native **brcmsmac** driver on 13.04 is working pretty well for this card. So anyone having 13.04 or later and having problem with this card, should try that one first.

**[COLOR="#800000"]Possible reason for BCM4313 card not working (at present) :[/COLOR]** The default proprietary driver "wl" got installed by user's choice (accepting the "Additional Drivers" program's offer), or automatically during installation of Ubuntu (if "Download Updates while install" and "install third party software" were checked). To verify if the "wl" driver is installed, you can use command "nm-tool" or -
```
lsmod | grep wl
```
If it returns "**wl**" as output, the case is indeed as explained above.

**[COLOR="#800000"]First thing to try :[/COLOR]** Purge the proprietary driver and try the native one -
```
sudo apt-get purge bcmwl-kernel-source
```
..then reboot. The native one should be automatically loaded. You can check it with either the command "nm-tool", or -
```
lsmod | grep brcm
```
If it returns "**brcmsmac**", in the output lines, then it is correctly loaded. Check if it works for you. If not, you may try the other workaround presented in this thread ([post #31]("http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619"))

Good Luck everyone! :)

---

### Post by boia01 on 2013-08-20
Patching the wl driver worked for me too.   This is my hardware:

eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)

and I'm running Ubuntu 13.04.

I tried using the brcmsmac driver and it worked to some extent but I was having intermittent stalls, low signal, and not-so-good throughput, hence why I reverted to the proprietary driver.

varunendra: thanks for providing the patch + instructions!

---

### Post by varunendra on 2013-08-20
> **boia01 said:**
> Patching the wl driver worked for me too.   This is my hardware:

eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)

and I'm running Ubuntu 13.04.

I tried using the brcmsmac driver and it worked to some extent but I was having intermittent stalls, low signal, and not-so-good throughput, hence why I reverted to the proprietary driver.

varunendra: thanks for providing the patch + instructions!

..and Thank you so much for the precious feedback and confirmation boia01 !

It would have been hard for me to believe this issue could persist so long and the patched driver can still perform better than the brcmsmac in any case. So your feedback is a definite confidence booster and I hope its performance remains good and persistent for you.

And a very warm welcome to the Ubuntu Forums boia01 !! :)

---

### Post by cz6Mp83 on 2013-08-21
Hi. I'm a little bit like the monky that sees and then do, so I don't quite understand everything that's happening here and I have this problem, when I run command:

cp wl.ko /lib/modules/myname -r/kernel/drivers/net/wireless

I got this message (in Spanish, so in English it should read something like this):

cp: wrong option --<</>>
Try <<cp --help>> for more information.

---

### Post by varunendra on 2013-08-21
First off, Welcome to the forums cz6Mp83 !

There is a minor error in your command -
> **cz6Mp83 said:**
> cp wl.ko /lib/modules/**[COLOR="#FF0000"]myname -r[/COLOR]**/kernel/drivers/net/wireless
That is not "myname" or anything else than exactly **[COLOR="#0000CD"]`uname -r`[/COLOR]**. That (uname -r) is a command itself that has to be typed exactly the same way [COLOR="#696969"](that is, with the "back-quotes" (``) around it)[/COLOR] as given in the post you are following (post #31).

Just copy-paste the command in the terminal using your mouse pointer -
```
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
```

Let me know if you face anymore errors.

Good luck ! :)

---

### Post by DGINSD on 2014-03-30
I have a bcm4313 thats in a HP G6 laptop, the device works with both the proprietary driver and the open source. The open source is un-useable due to signal strength, the proprietary is better but not how it's supposed to be strength wise, in the past I fixed issue by performing the fix in post 31 but now I cant get the wl.ko module to build. I've tried to get it to build before and after making the listed edits to wl_linux.c both seem to give the same errors and I don't know enough about this to work through them. Here are is the output of make, first without the edits made and then with.

```
david@HP-G6:~/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141$ makeKBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-18-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/built-in.o
  CC [M]  /home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/shared/linux_osl.o
  CC [M]  /home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.o
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_printstats&#8217;:
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3246:7: warning: passing argument 1 of &#8216;wl->tkipmodops->print_stats&#8217; from incompatible pointer type [enabled by default]
       wl->tkip_bcast_data[idx]);
       ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3246:7: note: expected &#8216;struct seq_file *&#8217; but argument is of type &#8216;char *&#8217;
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3249:4: warning: passing argument 1 of &#8216;wl->tkipmodops->print_stats&#8217; from incompatible pointer type [enabled by default]
    wl->tkipmodops->print_stats(debug_buf, wl->tkip_ucast_data);
    ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3249:4: note: expected &#8216;struct seq_file *&#8217; but argument is of type &#8216;char *&#8217;
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c: In function &#8216;wl_reg_proc_entry&#8217;:
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3470:2: error: implicit declaration of function &#8216;create_proc_entry&#8217; [-Werror=implicit-function-declaration]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
  ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3470:22: warning: assignment makes pointer from integer without a cast [enabled by default]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
                      ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3475:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->read_proc = wl_proc_read;
                ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3476:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->write_proc = wl_proc_write;
                ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3477:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->data = wl;
                ^
cc1: some warnings being treated as errors
make[2]: *** [/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'
make: *** [all] Error 2
david@HP-G6:~/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141
```

```
david@HP-G6:~/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141$ makeKBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-18-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  CC [M]  /home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.o
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_printstats&#8217;:
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3246:7: warning: passing argument 1 of &#8216;wl->tkipmodops->print_stats&#8217; from incompatible pointer type [enabled by default]
       wl->tkip_bcast_data[idx]);
       ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3246:7: note: expected &#8216;struct seq_file *&#8217; but argument is of type &#8216;char *&#8217;
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3249:4: warning: passing argument 1 of &#8216;wl->tkipmodops->print_stats&#8217; from incompatible pointer type [enabled by default]
    wl->tkipmodops->print_stats(debug_buf, wl->tkip_ucast_data);
    ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3249:4: note: expected &#8216;struct seq_file *&#8217; but argument is of type &#8216;char *&#8217;
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c: In function &#8216;wl_reg_proc_entry&#8217;:
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3470:2: error: implicit declaration of function &#8216;create_proc_entry&#8217; [-Werror=implicit-function-declaration]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
  ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3470:22: warning: assignment makes pointer from integer without a cast [enabled by default]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
                      ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3475:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->read_proc = wl_proc_read;
                ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3476:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->write_proc = wl_proc_write;
                ^
/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.c:3477:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->data = wl;
                ^
cc1: some warnings being treated as errors
make[2]: *** [/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/david/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'

make: *** [all] Error 2
david@HP-G6:~/Downloads/wireless/hybrid-v35_64-nodebug-pcoem-6_30_223_141$ 
```

---

### Post by varunendra on 2014-03-30
@ DGINSD,

The latest version of the sta driver that you are using (6.30..) is already available in the default repositories. As far as I know, it is the same driver that will be build from the source code downloaded from Broadcom's website. Check if it is available for you or not by -
```
apt-cache show bcmwl-kernel-source | grep Version
```

If it shows 6.30.., all you have to do is to install it like any normal Ubuntu package -
```
sudo apt-get install bcmwl-kernel-source
```

If it does not show up (perhaps if you are using an older kernel), you may try to manually download its .deb package suitable to your architecture (32 or 64 bit, from **[here]("http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/")**) and install it with a simple double-click, or -
```
sudo dpkg -i *[COLOR="#0000CD"]<downloaded package name with path>[/COLOR]*
```

Either way, you shouldn't need to bother with compiling it now.

We know that many driver sources don't compile successfully on the latest kernels. Unfortunately, so far at least *I* haven't found a common patch to make them work. 

There does exist at least one patched driver, but that was for a Ralink (or Realtek, I don't remember correctly) card and I couldn't find enough time since then to test if the same or similar changes can make others work too.

So.. if the normal sta driver doesn't work well, nor does the brcmsmac, I suggest you post a new thread with a description of the problem, what all you have tried so far, plus the report generated by "wireless_script" which you can find in the "Wireless Script" link in my signature below. I'd be very happy to assist if I could get time to, unfortunately, I don't get much time these days. But still, please let me know (by posting here or via PM) if you do post a new thread.

---

### Post by DGINSD on 2014-03-30
Thank you for the response, I have the latest from Ubuntu repos installed and with that installed it works well enough, the indicator on the panel just shows 3 of the 4 bars (even when right next to the wireless AP). I remember trying your fix a version or two of Ubuntu back and that minor issue was solved, just wanted to see if it would solve it again. 

How are they building the official packages if they wont compile? I was more concerned it was a problem with my machine or install, but if what your saying about compilation is correct, working through fixing those issues is way above my pay grade and skills, and would likely only end in frustration. Again thank you for your efforts.

---

### Post by varunendra on 2014-04-01
> **DGINSD said:**
> How are they building the official packages if they wont compile?

The source code we are talking about here is developed by the card manufacturers, while the kernel is being developed by the open source community. Without proper mutual cooperation and understanding, it is difficult for both to maintain consistency in the code.

For the manufacturers, it is difficult because they don't have much time and resources to invest (or, probably 'waste' from their point-of-view) on maintaining compatibility with Linux, because its return would be very small compared to other areas where their limited development team remains busy.

For Linux kernel developers, it is difficult because they have to take care of a mountain of issues all the time, and they can't afford to pay too much attention to a few particular device drivers. On the Open Source developers' part, it is the job of the Open Source driver developers to maintain the compatibility, and they do that as nicely and quickly as possible without knowing the 'Internals' of a card and/or the binary blobs supplied by the manufacturers.

But we are talking about the STA driver, which is proprietary, not the Open Source one. The Open Source community has already done what they could do with it - they have changed the compilation code, and turned it into a .deb package which is now available in the default repositories as you found out yourself. What they can't change is the binary blob that this compiled driver uses, that's entirely the job of the manufacturer unless they are willing to make it open source.

The source code on Broadcom's site is in their control and so it's upto their developers when they find time to fix it. But if the version installed from the repos isn't working, the one on their website won't work either until the binary firmware is fixed as well. So for the time being, the open source version (brcmsmac) is the best option and except for a very few exceptional cases, it has been consistently reported to work really well for the BCM4313 card on newer kernels.

This is why I think if you are still having problems, it may help to post a new thread and post the detailed wireless_script report there so we can see if something needs to be done to improve performance.

---

