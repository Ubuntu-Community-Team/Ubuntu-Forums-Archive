---
title: "Cannot access Wired settings"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by thatkiwiguy on 2013-05-18
Just installed dual boot ubuntu, but cannot get any access to the internet (Using a Ethernet cable). When I launch into windows internet it's fine (I'm writing this post off it so I guess that's proof it works), but cannot get any access in Linux.

Now I've searched a little for solutions and when I go into network in settings and try turn wired on, it will automatically turn itself off if I quit the settings all while not letting me access the settings.

Something I did find was this post [http://ubuntuforums.org/showthread.php?t=1956423](http://ubuntuforums.org/showthread.php?t=1956423), where it says;

 I suspect your /etc/network/interfaces reads this:
 	Code:
 	
auto lo iface lo inet loopback
Append this to the file and reboot:

 	Code:
 	
auto eth0 iface eth0 inet dhcp

I ran this and got the result auto lo, but don't know how to change it to auto eth0.

If anyone could give me any help on how to fix the code and why I can't turn wired on that would be great.

---

### Post by praseodym on 2013-05-18
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net     [COLOR="#FF0000"]#this is one line[/COLOR]
lsmod
```

---

### Post by thatkiwiguy on 2013-05-18
Here's the text, wasn't sure how to copy it out so formatting isn't great but hopefully it's usable.
```
M@ubuntu:~$ lspci -nnk | grep -A2 net 
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10) 
    Subsystem: Giga-byte Technology Device [1458:e000] 
07:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller [1b4b:9172] (rev 11) 
```

```
m@ubuntu:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12714  1 
nls_utf8               12558  1 
isofs                  40307  1 
bnep                   18240  2 
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  0 
bluetooth             211812  10 bnep,rfcomm 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp 
snd_hda_codec_hdmi     32476  1 
coretemp               13642  0 
snd_hda_codec_via      47558  1 
kvm                   422160  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel 
aes_x86_64             17256  1 aesni_intel 
microcode              23030  0 
psmouse               102075  0 
serio_raw              13216  0 
lpc_ich                17145  0 
joydev                 17694  0 
snd_hda_intel          34117  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel 
snd_hwdep              17765  1 snd_hda_codec 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi 
snd_seq_midi_event     14900  1 snd_seq_midi 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              29990  2 snd_pcm,snd_seq 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq 
mac_hid                13254  0 
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15092  1 snd 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm 
mei                    41410  0 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid 
uas                    18073  0 
usb_storage            49288  2 
nouveau               924024  2 
ttm                    88495  1 nouveau 
drm_kms_helper         49259  1 nouveau 
drm                   290344  4 nouveau,ttm,drm_kms_helper 
i2c_algo_bit           13565  1 nouveau 
mxm_wmi                13022  1 nouveau 
wmi                    19257  2 nouveau,mxm_wmi 
video                  19598  1 nouveau
```

---

### Post by cortman on 2013-05-18
Not to interrupt praseodym's line of inquiry, but I'm interested in what would be listed from the command

```

ifconfig

```

---

### Post by thatkiwiguy on 2013-05-19
Here you go,

> m@ubuntu:~$ ifconfig 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1312 (1.3 KB)  TX bytes:1312 (1.3 KB)

---

### Post by praseodym on 2013-05-19
Please check if these packages are installed:
```
dpkg -l dkms
dpkg -l linux-headers-$(uname -r)
dpkg -l build-essential
```
If yes, you can download this package

[http://media.cdn.ubuntu-de.org/forum/attachments/55/19/4987097-alx_dkms-cw20121003.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/55/19/4987097-alx_dkms-cw20121003.tar.gz)

Save it in your /home directory, open a new terminal and install according to this

[http://forum.ubuntuusers.de/topic/lan-wlan-probleme-mit-lenovo-g580/2/#post-4987097](http://forum.ubuntuusers.de/topic/lan-wlan-probleme-mit-lenovo-g580/2/#post-4987097)

Starting point is "Installation über DKMS¶"

---

### Post by thatkiwiguy on 2013-05-20
Downloaded package, copied to /home both the file and then the contents. Got these messages 

> m@ubuntu:~$ dpkg -l dkms 
No packages found matching dkms. 
m@ubuntu:~$ dpkg -l linux-headers-$(uname -r) 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name           Version        Description 
+++-==============-==============-============================================ 
ii  linux-headers- 3.5.0-23.35~pr Linux kernel headers for version 3.5.0 on 64 
m@ubuntu:~$ dpkg -l build -essential 
dpkg-query: error: package name in specifier '-essential' is illegal: must start with an alphanumeric character 

Would still like some help on how to change auto lo to auto eth0, and that's an error I know is wrong but don't know how to fix it.

---

### Post by steeldriver on 2013-05-20
Unless you are using the Server edition of Ubuntu then there is nothing wrong with your /etc/network/interfaces file - the Desktop editions get their ethernet / wlan settings from NetworkManager. Leave that file alone and concentrate on following praseodym's instructions for the driver - check your typing carefully for example it should be **build-essential** (no space) not **build -essential** (with a space)

---

### Post by praseodym on 2013-05-20
[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3.1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3.1_all.deb)

Here is the dkms package. Alternatively, the driver can be compiled without dkms, see the link above. But first check

```
dpkg -l build-essential
```

---

### Post by thatkiwiguy on 2013-05-20
Re typed command correctly, couldn't find package.

Attached a pic for you to see if I have the right files in home directory.

---

### Post by praseodym on 2013-05-20
Save the linked "dkms" .deb package in Downloads and let any package packed in the "tar.gz" file also in "Downloads". 

```
cd ~/Downloads/
sudo dpkg -i *.deb

```
Then continue with the installation instruction with the line "sudo tar"

---

### Post by thatkiwiguy on 2013-05-21
Tried again, got this; 

> m@ubuntu:~$ sudo dpkg -i *.deb 
[sudo] password for m: 
dpkg: error processing *.deb (--install): 
 cannot access archive: No such file or directory 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic 
Warning: No support for locale: en_US.utf8 
Errors were encountered while processing: 
 *.deb 
m@ubuntu:~$ 

Attached pic of downloads to make sure all files are there. But I still would like help on how to change auto lo to auto eth0.

---

### Post by praseodym on 2013-05-21
Did you change the directory before?

---

### Post by Hadaka on 2013-05-21
Hi, the link you refered to in your post..
[http://ubuntuforums.org/showthread.php?t=1956423](http://ubuntuforums.org/showthread.php?t=1956423)
is for Ubuntu 11.10...which is no longer supported. 
your computer (because it's newer) requires the ALX
dirver. The version of Ubuntu you loaded does not have that driver.
also..your /etc/network/interfaces is suppose to look like this..
```
auto lo
iface lo inet loopback

```
nothing more..

please follow praseodym,s guide

or you may also get the needed ALX driver
by doing..
```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx

```
the reason your wired is not working is only because you dont have the correct driver
not the /etc/network/interfaces file.
good luck.

---

### Post by thatkiwiguy on 2013-05-21
> **praseodym said:**
> Did you change the directory before?

I don't think I did, but when I go through the partition I installed it on I can't find any of the document/download folders. Although I didn't turn hidden files on, but you would think you could find them. Where is the downloads folder supposed to be?

---

### Post by praseodym on 2013-05-21
The download folder is located directly in your /home directory.

---

### Post by thatkiwiguy on 2013-05-22
When I'm in Linux, I can browse the /home and /downloads and have the packages placed in there but then when I try run commands it doesn't recognize as the folder existing. Which I thought was weird so when I'm booted into Windows, I went into the HD Ubuntu is installed in and I can't find any of the folders (Haven't checked if they're hidden though) - compared to C:Users/public/m/downloads. I might try reinstalling to make sure it's installed correctly to the right place, should I stay on 12.04 or install 13.04?

---

### Post by steeldriver on 2013-05-22
You realize that Linux terminal is case-sensitive, right? so for example

```
cd downloads
```

is not the same as

```
cd Downloads
```

Generally Windows can't read Linux filesystems - so don't put too much faith in what you see on the HD when booted in Windows

---

### Post by thatkiwiguy on 2013-05-22
> **steeldriver said:**
> You realize that Linux terminal is case-sensitive, right? so for example

```
cd downloads
```

is not the same as

```
cd Downloads
```

Generally Windows can't read Linux filesystems - so don't put too much faith in what you see on the HD when booted in Windows

Thanks for that, got one step further. Still can't get the code to work but the package seems to install now.

> m@ubuntu:~$ cd ~/Downloads/
m@ubuntu:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for m:
(Reading database ... 138792 files and directories currently installed.)
Preparing to replace dkms 2.2.0.3-1ubuntu3.1 (using dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Unpacking replacement dkms ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
Processing triggers for man-db ...
m@ubuntu:~/Downloads$ sudo tar xvf 4987097-alx_dkms-cw20121003.tar.gz -C /usr/src
tar: 4987097-alx_dkms-cw20121003.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
m@ubuntu:~/Downloads$ sudo dkms add alx_dkms -v cw20121003
Error! Could not find module source directory.
Directory: /usr/src/alx_dkms-cw20121003 does not exist.
m@ubuntu:~/Downloads$


---

### Post by praseodym on 2013-05-22
Please copy the downloaded tar.gz archive also to "Downloads" and try again

---

### Post by thatkiwiguy on 2013-05-22
Well, managed to get the code to run. 

This was the end section as the whole thing was to big to copy;

> DKMS: install completed.
m@ubuntu:~/Downloads$ sudo depmod -a && sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
Warning: No support for locale: en_US.utf8
m@ubuntu:~/Downloads$ 


There's still no internet, did I miss some of the code? Because I entered everything from the german page from the sudo tar line correctly.

---

### Post by praseodym on 2013-05-22
Did you reboot

---

### Post by thatkiwiguy on 2013-05-22
Yes, still nothing.

---

### Post by praseodym on 2013-05-22
Check now:
```

uname -a
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
modinfo alx | grep file
dmesg | grep alx
```

---

### Post by thatkiwiguy on 2013-05-23
> **praseodym said:**
> Check now:
```

uname -a
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
modinfo alx | grep file
dmesg | grep alx
```

Ran it, restarted, still doesn't seem to work.

```
m@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
m@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8               12558  1
nls_iso8859_1          12714  1
isofs                  40307  1
nouveau               924024  2
bnep                   18240  2
ttm                    88495  1 nouveau
parport_pc             32867  0
ppdev                  17114  0
lp                     17800  0
parport                46563  3 parport_pc,ppdev,lp
rfcomm                 47562  0
bluetooth             211812  10 bnep,rfcomm
drm_kms_helper         49259  1 nouveau
drm                   290344  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13565  1 nouveau
mxm_wmi                13022  1 nouveau
wmi                    19257  2 nouveau,mxm_wmi
video                  19598  1 nouveau
snd_hda_codec_hdmi     32476  1
snd_hda_codec_via      47558  1
coretemp               13642  0
kvm                   422160  0
ghash_clmulni_intel    13221  0
aesni_intel            51134  0
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
joydev                 17694  0
microcode              23030  0
psmouse               102075  0
serio_raw              13216  0
mac_hid                13254  0
mei                    41410  0
snd_hda_intel          34117  5
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_seq_midi           13325  0
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lpc_ich                17145  0
hid_generic            12541  0
usbhid                 47259  0
hid                   100815  2 hid_generic,usbhid
uas                    18073  0
usb_storage            49288  2
m@ubuntu:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3936 (3.9 KB)  TX bytes:3936 (3.9 KB)
 
m@ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
m@ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
m@ubuntu:~$ modinfo alx | grep file
filename:       /lib/modules/3.5.0-23-generic/updates/dkms/alx.ko
m@ubuntu:~$ dmesg | grep alx
[   30.446758] alx: Unknown symbol compat_dependency_symbol (err 0)
m@ubuntu:~$
```

---

### Post by praseodym on 2013-05-23
Load the driver by hand:
```

sudo modprobe -v alx
```
and check "cat /etc/resolv.conf" again. There should be nameserver(s) listed. If not, add them by hand:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by thatkiwiguy on 2013-05-24
Am I missing a package because the driver didn't load.
> m@ubuntu:~$ sudo modprobe -v alx

  [sudo] password for m:

  insmod /lib/modules/3.5.0-23-generic/updates/dkms/alx.ko

  FATAL: Error inserting alx (/lib/modules/3.5.0-23-generic/updates/dkms/alx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

  m@ubuntu:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf

  nameserver 8.8.8.8

  nameserver 8.8.4.4

  m@ubuntu:~$ sudo service network-manager restart

  network-manager stop/waiting

  network-manager start/running, process 2162

  m@ubuntu:~$



---

### Post by praseodym on 2013-05-24
>  FATAL: Error inserting alx (/lib/modules/3.5.0-23-generic/updates/dkms/alx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Check:
```

dmesg | grep alx
```

---

### Post by thatkiwiguy on 2013-05-24
1char

> m@ubuntu:~$ dmesg | grep alx
[   30.452613] alx: Unknown symbol compat_dependency_symbol (err 0)
m@ubuntu:~$

---

### Post by praseodym on 2013-05-24
Ok, obviously, the driver does not work with kernel 3.5. Is it Ubuntu 12.04? Please show:

```
dpkg -l linux-image-3*
```

---

### Post by thatkiwiguy on 2013-05-24
> **praseodym said:**
> Ok, obviously, the driver does not work with kernel 3.5. Is it Ubuntu 12.04? Please show:

```
dpkg -l linux-image-3*
```

I'm 12.04,
```

m@ubuntu:~$ dpkg -l linux-image-3*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-image-3. 3.5.0-23.35~pr Linux kernel image for version 3.5.0 on 64 b
m@ubuntu:~$
```

---

### Post by praseodym on 2013-05-24
Please download the following packages:

[http://ubuntu.secsup.org//pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb](http://ubuntu.secsup.org//pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb)

[http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb](http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb)

[http://ubuntu.arcticnetwork.ca//pool/main/l/linux/linux-headers-3.2.0-40-generic_3.2.0-40.64_amd64.deb](http://ubuntu.arcticnetwork.ca//pool/main/l/linux/linux-headers-3.2.0-40-generic_3.2.0-40.64_amd64.deb)

[http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb](http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb)

[http://ubuntu.mirrors.tds.net/pub/ubuntu//pool/main/l/linux-meta/linux-backports-modules-cw-3.4-precise-generic_3.2.0.40.48_amd64.deb](http://ubuntu.mirrors.tds.net/pub/ubuntu//pool/main/l/linux-meta/linux-backports-modules-cw-3.4-precise-generic_3.2.0.40.48_amd64.deb)

[http://ubuntu.mirror.iweb.ca//pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.4-3.2.0-40-generic_3.2.0-40.27_amd64.deb](http://ubuntu.mirror.iweb.ca//pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.4-3.2.0-40-generic_3.2.0-40.27_amd64.deb)

Save them in "Downloads" after removing all other .deb files there. Installation via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot and hold the SHIFT-button during boot-up. In the GRUB-menu choose "previous ubuntu versions" and choose kernel 3.2.0-40. LAN should work.

---

### Post by thatkiwiguy on 2013-05-24
> **praseodym said:**
> Please download the following packages:

[http://ubuntu.secsup.org//pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb](http://ubuntu.secsup.org//pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb)

[http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb](http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb)

[http://ubuntu.arcticnetwork.ca//pool/main/l/linux/linux-headers-3.2.0-40-generic_3.2.0-40.64_amd64.deb](http://ubuntu.arcticnetwork.ca//pool/main/l/linux/linux-headers-3.2.0-40-generic_3.2.0-40.64_amd64.deb)

[http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb](http://ubuntu.media.mit.edu/ubuntu//pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb)

[http://ubuntu.mirrors.tds.net/pub/ubuntu//pool/main/l/linux-meta/linux-backports-modules-cw-3.4-precise-generic_3.2.0.40.48_amd64.deb](http://ubuntu.mirrors.tds.net/pub/ubuntu//pool/main/l/linux-meta/linux-backports-modules-cw-3.4-precise-generic_3.2.0.40.48_amd64.deb)

[http://ubuntu.mirror.iweb.ca//pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.4-3.2.0-40-generic_3.2.0-40.27_amd64.deb](http://ubuntu.mirror.iweb.ca//pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.4-3.2.0-40-generic_3.2.0-40.27_amd64.deb)

Save them in "Downloads" after removing all other .deb files there. Installation via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot and hold the SHIFT-button during boot-up. In the GRUB-menu choose "previous ubuntu versions" and choose kernel 3.2.0-40. LAN should work.

Links 1, 2 and 4 don't work.

---

### Post by praseodym on 2013-05-24
[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb)

Here they are.

---

### Post by thatkiwiguy on 2013-05-24
> **praseodym said:**
> [http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.40.48_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-40-generic_3.2.0-40.64_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-40_3.2.0-40.64_all.deb)

Here they are.

For some reason I still can't download the first link

---

### Post by praseodym on 2013-05-24
You are right, it is not on the server anymore. But anyway, this is only a metapackage. Try to go on with the others.

---

### Post by thatkiwiguy on 2013-05-24
That worked, thanks so much for helping through all my mistakes. Will have I have to do this each time on launch to get internet?

---

### Post by praseodym on 2013-05-24
Normally, kernel 3.5 will be booted automatically. Try grub-customizer:
```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```
Choose kernel 3.2.0-40 as default boot kernel there. We will clean up your system later (its 2:46 in Berlin ;) )

---

### Post by praseodym on 2013-05-25
So, here we go ;)

Be sure you booted into 3.2.0-40 kernel

```
uname -r
```

and show
```

dpkg -l linux-* | grep ii
```

---

### Post by thatkiwiguy on 2013-05-27
> **praseodym said:**
> So, here we go ;)

Be sure you booted into 3.2.0-40 kernel

```
uname -r
```

and show
```

dpkg -l linux-* | grep ii
```

```
m@ubuntu:~$ uname -r
3.2.0-40-generic
m@ubuntu:~$ dpkg -l linux-* | grep ii
ii  linux-backports-modules-cw-3.4-3.2.0-40-generic 3.2.0-40.27                                      compat-wireless Linux modules for version 3.2.0 on x86/x86_64
ii  linux-firmware                                  1.79.1                                           Firmware for Linux kernel drivers
ii  linux-generic-lts-quantal                       3.5.0.23.30                                      Generic Linux kernel image and headers
ii  linux-headers-3.2.0-40                          3.2.0-40.64                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic                  3.2.0-40.64                                      Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.5.0-23                          3.5.0-23.35~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-23-generic                  3.5.0-23.35~precise1                             Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-quantal               3.5.0.23.30                                      Generic Linux kernel headers
ii  linux-image-3.2.0-40-generic                    3.2.0-40.64                                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-23-generic                    3.5.0-23.35~precise1                             Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-quantal                 3.5.0.23.30                                      Generic Linux kernel image
ii  linux-libc-dev                                  3.2.0-37.58                                      Linux Kernel Headers for development
ii  linux-signed-generic-lts-quantal                3.5.0.23.30                                      Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.5.0-23-generic             3.5.0-23.35~precise1                             Signed kernel image generic
ii  linux-signed-image-generic-lts-quantal          3.5.0.23.30                                      Signed Generic Linux kernel image
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu1                             base package for ALSA and OSS sound systems
m@ubuntu:~$ 
```

---

### Post by praseodym on 2013-05-27
So, lets start ;) I strongly recommend copy/paste of the following lines:

First we install all the metapackages for the 3.2 kernel, its headers, compiling tools, the respective drivers, etc:
```

sudo apt-get install --reinstall linux-image-generic linux-headers-generic linux-generic build-essential dkms linux-backports-modules-cw-3.4-precise-generic linux-tools linux-tools-common
```
Then we are uninstalling the "wrong" kernel and other stuff:
```

sudo apt-get remove --purge linux-generic-lts-quantal linux-headers-3.5* linux-headers-generic-lts-quantal linux-image-3.5* linux-image-generic-lts-quantal linux-signed*
```

Then we check the dependencies:
```

sudo apt-get -f install
sudo dpkg --configure -a
```

Then we clean up:
```

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```
After that you can change the default boot-kernel in the grub-customizer to "entry 1" without any kernel number. After rebooting kernel 3.2.0-44-generic should be loaded and your network should (still) work.

If not, press SHIFT during boot-up again and choose 3.2.0-40 again in "previous ubuntu versions".

---

