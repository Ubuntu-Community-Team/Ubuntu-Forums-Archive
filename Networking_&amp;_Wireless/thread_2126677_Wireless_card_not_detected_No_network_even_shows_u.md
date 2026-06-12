---
title: "Wireless card not detected? No network even shows up! Help!"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by KamonB on 2013-03-17
First time Ubuntu user, but I hope I catch on quickly

However I'm having a problem... I can't find out how to install my wireless card drivers onto my laptop.

I updated all of Ubuntu and I tried to use NDISWrapper.. but to no avail.
I believe I have an 802.11 b/g/n wireless card adapter.

Can you guys give me any help?




Also: How can I get my music I have on my windows partition to be accessible while I'm on Ubuntu?

---

### Post by Hadaka on 2013-03-17
Hi, please do..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the results
thanks.

---

### Post by KamonB on 2013-03-17
> **Hadaka said:**
> Hi, please do..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the results
thanks.


```
phillip@ubuntu:~$ lspci -nn | egrep '0200|0280'03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)

```

```
phillip@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            17501  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_via      46676  1 
joydev                 17458  0 
snd_hda_intel          33492  5 
bnep                   18141  2 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
rfcomm                 46620  0 
snd_hwdep              17699  1 snd_hda_codec
parport_pc             32689  0 
nouveau               896008  0 
coretemp               13401  0 
ppdev                  17074  0 
bluetooth             209249  10 bnep,rfcomm
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lp                     17760  0 
kvm_intel             132760  0 
snd_seq_midi           13325  0 
i915                  520615  3 
parport                46346  3 parport_pc,ppdev,lp
kvm                   414071  1 kvm_intel
snd_rawmidi            30513  1 snd_seq_midi
ttm                    83596  1 nouveau
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         49113  2 nouveau,i915
ghash_clmulni_intel    13221  0 
drm                   288721  6 nouveau,i915,ttm,drm_kms_helper
aesni_intel            51038  0 
snd_timer              29426  2 snd_pcm,snd_seq
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13414  2 nouveau,i915
rtsx_pci_ms            13012  0 
snd                    78921  19 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                95595  0 
aes_x86_64             17256  1 aesni_intel
mxm_wmi                13022  1 nouveau
lpc_ich                17062  0 
mei                    40691  0 
memstick               16555  1 rtsx_pci_ms
soundcore              15048  1 snd
wmi                    19071  2 nouveau,mxm_wmi
video                  19391  2 nouveau,i915
serio_raw              13216  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
microcode              22804  0 
mac_hid                13206  0 
rtsx_pci_sdmmc         17476  0 
rtsx_pci               28325  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  61651  0 

```

**rfkill list all** listed nothing :(

Do you mind explaining to me what I'm looking for? So I can learn this for my other systems I'll be converting to Linux.


edit: Attempted **rfkill list *** and the terminal said it was a bogus command.

---

### Post by Hadaka on 2013-03-17
Hi, i am not seeing anything in your
lsmod file that relates to a wifi card,
as in 80211 xxx and there is missing
data in the lspci 0280 output, did you just
load ubuntu? and more importantly did you do..
```
sudo apt-get update
sudo apt-get upgrade
```
after you loaded? Try that if you have not
and repeat the last commands. The rfkill list all
is just that..all   not wildcard *
thanks.

---

### Post by KamonB on 2013-03-17
> **Hadaka said:**
> Hi, i am not seeing anything in your
lsmod file that relates to a wifi card,
as in 80211 xxx and there is missing
data in the lspci 0280 output, did you just
load ubuntu? and more importantly did you do..
```
sudo apt-get update
sudo apt-get upgrade
```
after you loaded? Try that if you have not
and repeat the last commands. The rfkill list all
is just that..all   not wildcard *
thanks.

Yes, I just got Ubuntu 12.10
I updated everything right after I installed Ubuntu. 

I tried to use 
```
rfkill list all
```
But it didn't work, I'll run all the commands again.



**All 3 codes were run**
```
phillip@ubuntu:~$ rfkill list allphillip@ubuntu:~$ sudo apt-get update
[sudo] password for phillip: 
Hit http://archive.ubuntu.com quantal Release.gpg
Hit http://security.ubuntu.com quantal-security Release.gpg
Hit http://archive.ubuntu.com quantal-updates Release.gpg
Hit http://security.ubuntu.com quantal-security Release
Hit http://archive.ubuntu.com quantal Release   
Hit http://security.ubuntu.com quantal-security/main amd64 Packages
Hit http://archive.ubuntu.com quantal-updates Release
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal/main amd64 Packages
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal/universe amd64 Packages
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages
Hit http://security.ubuntu.com quantal-security/main Translation-en
Hit http://archive.ubuntu.com quantal/main Translation-en
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://archive.ubuntu.com quantal/multiverse Translation-en
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://archive.ubuntu.com quantal/restricted Translation-en
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Hit http://archive.ubuntu.com quantal/universe Translation-en
Hit http://archive.ubuntu.com quantal-updates/main amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/main Translation-en
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://archive.ubuntu.com quantal/main Translation-en_US
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US
Reading package lists... Done
phillip@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phillip@ubuntu:~$ 

```

[http://i.imgur.com/u3yEL6y.png](http://i.imgur.com/u3yEL6y.png)

---

### Post by Hadaka on 2013-03-17
Hi, I'm not much if a realtec guy but lets
take a look at one more thing ,,please do.

```
lsusb
```

also you stated you attempted to load ndiswrapper
i see no traces of it anywhere in your lsmod report
thanks.

---

### Post by Hadaka on 2013-03-17
Hi, I found a link for you that should help.

[http://ubuntuforums.org/archive/index.php/t-2017622.html](http://ubuntuforums.org/archive/index.php/t-2017622.html)

if you have any difficulty with loading the file,report back
and i will try to get the realtek expert on it for you.
thanks.

---

### Post by KamonB on 2013-03-17
> **Hadaka said:**
> Hi, I'm not much if a realtec guy but lets
take a look at one more thing ,,please do.

```
lsusb
```

also you stated you attempted to load ndiswrapper
i see no traces of it anywhere in your lsmod report
thanks.

Well let me clear that up, I tried to install NDISWrapper, but I kept getting errors left and right, it wouldn't create a directory for the files for installation

```
phillip@ubuntu:~$ lsusbBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 147e:1002 Upek 
phillip@ubuntu:~$ 

```

---

### Post by Hadaka on 2013-03-17
Hi, I think we posted at the same time, refer to the post above your 
last post.
here is the link again..
 [http://ubuntuforums.org/archive/index.php/t-2017622.html](http://ubuntuforums.org/archive/index.php/t-2017622.html)
thanks.

---

### Post by KamonB on 2013-03-17
Yeah, sorry I posted that before I refreshed again..

I took that as far as I could and followed this link:
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)


And I got until step 3 then I got errors in the terminal:
```
phillip@ubuntu:~$ sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`[sudo] password for phillip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.5.0-25-generic is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phillip@ubuntu:~$ wget -O- http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz | tar -xz
--2013-03-17 23:34:18--  http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
Resolving dl.dropbox.com (dl.dropbox.com)... 54.235.162.150
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.162.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8997390 (8.6M) [application/x-tar]
Saving to: `STDOUT'


100%[======================================>] 8,997,390   4.66M/s   in 1.8s    


2013-03-17 23:34:21 (4.66 MB/s) - written to stdout [8997390/8997390]


phillip@ubuntu:~$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
phillip@ubuntu:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ make
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make: *** [all] Error 2
phillip@ubuntu:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ sudo make install
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/phillip/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make: *** [all] Error 2
phillip@ubuntu:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ 

```




I tried Step 5: the Modprobe just for the heck of it and got this:

```
phillip@ubuntu:~$ sudo modprobe rtl8723e[sudo] password for phillip: 
FATAL: Module rtl8723e not found.
phillip@ubuntu:~$ ^C
phillip@ubuntu:~$ 

```


It'll download the drivers and everything, however it won't install them it looks like :(

I downloaded the drivers manually via the Dropbox link and put them in a folder in my desktop just in case that can be used for me
The path is: [B]/home/phillip/Desktop/Wireless/Rtl1/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012




Also: I got NDISWrapper to work, however I don't know which *inf* file to select :(
[/B][http://i.imgur.com/boVkq3A.jpg](http://i.imgur.com/boVkq3A.jpg)

---

### Post by Hadaka on 2013-03-17
Hi,i would download the dropbox file from here..
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)
and then follow the instructions from chili555 on the first link i sent...including the sudo su
command.
give that a try and see how it goes.
thanks.

---

### Post by KamonB on 2013-03-18
> **Hadaka said:**
> Hi,i would download the dropbox file from here..
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)
and then follow the instructions from chili555 on the first link i sent...including the sudo su
command.
give that a try and see how it goes.
thanks.


That's what I just did... I'm getting errors on the very last few lines


```
phillip@ubuntu:~$ cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012bash: cd: Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012: No such file or directory
phillip@ubuntu:~$ cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
bash: cd: Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012: No such file or directory
phillip@ubuntu:~$ cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ sudo su
[sudo] password for phillip: 
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make: *** [all] Error 2
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# 

```


Then I did the installation as mentioned in post #6:
```
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo apt-get install --reinstall build-essentialReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/5,814 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 177574 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu3 (using .../build-essential_11.5ubuntu3_amd64.deb) ...
Unpacking replacement build-essential ...
Setting up build-essential (11.5ubuntu3) ...
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo apt-get install --reinstall linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/2,438 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 177574 files and directories currently installed.)
Preparing to replace linux-headers-generic 3.5.0.25.31 (using .../linux-headers-generic_3.5.0.25.31_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-headers-generic (3.5.0.25.31) ...
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo apt-get install --reinstall linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/967 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 177574 files and directories currently installed.)
Preparing to replace linux-headers-3.5.0-25-generic 3.5.0-25.39 (using .../linux-headers-3.5.0-25-generic_3.5.0-25.39_amd64.deb) ...
Unpacking replacement linux-headers-3.5.0-25-generic ...
Setting up linux-headers-3.5.0-25-generic (3.5.0-25.39) ...
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# 



```

---

### Post by Hadaka on 2013-03-18
its saying no directory,,,do.,,
```
cd Desktop
ls
```
see if the file is there...if not do..
```
cd Downloads
```
if its in Downloads...drag it to Desktop
its also upper case "D" in Downloads and Desktop
thanks.


bash: cd: Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012: No such file or directory

---

### Post by KamonB on 2013-03-18
> **Hadaka said:**
> its saying no directory,,,do.,,
```
cd Desktop
ls
```
see if the file is there...if not do..
```
cd Downloads
```
if its in Downloads...drag it to Desktop
its also upper case "D" in Downloads and Desktop
thanks.


bash: cd: Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012: No such file or directory


I got this: 

```
phillip@ubuntu:~$ cd desktopbash: cd: desktop: No such file or directory
phillip@ubuntu:~$ ls
Desktop           Public
Documents         rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
Downloads         shared
examples.desktop  Templates
Music             Ubuntu One
Pictures          Videos
phillip@ubuntu:~$ cd Desktop
phillip@ubuntu:~/Desktop$ ls
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012  Wireless

```

```
phillip@ubuntu:~$ cd Downloadsphillip@ubuntu:~/Downloads$ ls
ndiswrapper-1.58.tar.gz
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 (1).tar.gz
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz
phillip@ubuntu:~/Downloads$ 



```

---

### Post by Hadaka on 2013-03-18
ok, it looks like your file is in Documents


Documents         rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
drag it to Desktop and try again.

its also in Downloads

phillip@ubuntu:~$ cd Downloadsphillip@ubuntu:~/Downloads$ ls ndiswrapper-1.58.tar.gz rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 (1).tar.gz rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz phillip@ubuntu:~/Downloads$

---

### Post by KamonB on 2013-03-18
It's not, it's on my desktop, I moved it here and tried every command over and over again and still nothing :(

[http://i.imgur.com/Ts2TAGa.jpg](http://i.imgur.com/Ts2TAGa.jpg)


```
phillip@ubuntu:~$ cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ sudo su
[sudo] password for phillip: 
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make: *** [all] Error 2
root@ubuntu:/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# 



```

---

### Post by Hadaka on 2013-03-18
Hi, ok do this ...in this order,
go to Desktop and remove the file.
then.  click home...drag and drop


rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz

from Downloads to Desktop

then do..
```
cd Desktop
```
locate your file ... 
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
right click it and chose "extract here"
then try to load again.
thanks.

---

### Post by KamonB on 2013-03-18
Insane... 
I even have it right there.. deleted everything and did it again...

[http://i.imgur.com/lfE8Apw.jpg](http://i.imgur.com/lfE8Apw.jpg)



edit:

WOOOO Finally it worked!
I got tired of everything and just went to properties and copy pasted the name of the folder, for some reason it likes that more than copy pasting it from online!

[http://i.imgur.com/Etmonv2.jpg](http://i.imgur.com/Etmonv2.jpg)

It's installing it this time!

```
phillip@ubuntu:~$ cd Desktopphillip@ubuntu:~/Desktop$ rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514 .2012.tar.gz
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514: command not found
phillip@ubuntu:~/Desktop$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
bash: cd: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012: No such file or directory
phillip@ubuntu:~/Desktop$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.8909.2012
bash: cd: rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.8909.2012: No such file or directory
phillip@ubuntu:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
phillip@ubuntu:~/Desktop$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ make
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/base.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rc.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rc.c:284:2: warning: initialization from incompatible pointer type [enabled by default]
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rc.c:284:2: warning: (near initialization for &#8216;rtl_rate_ops.rate_update&#8217;) [enabled by default]
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/debug.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/regd.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/efuse.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/cam.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/ps.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/core.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/stats.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/pci.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.mod.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/hw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/table.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/sw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/trx.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/led.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.c: In function &#8216;rtl92c_download_fw&#8217;:
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.c:239:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/phy.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rf.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/dm.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/hw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/table.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/sw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/trx.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/led.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/fw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/phy.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rf.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/dm.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/hw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/table.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/sw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/trx.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/led.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/fw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.c: In function &#8216;rtl92d_phy_reset_iqk_result&#8217;:
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.c:3002:2: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rf.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/dm.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/table.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/sw.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/trx.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/led.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.c: In function &#8216;rtl8723e_download_fw&#8217;:
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.c:204:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/phy.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rf.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/dm.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/pwrseq.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/pwrseqcmd.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hal_btc.o
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hal_bt_coexist.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.mod.o
  LD [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ sudo make install
[sudo] password for phillip: 
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make[1]: Entering directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
make -C /lib/modules/3.5.0-25-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
find /lib/modules/3.5.0-25-generic -name "r8192se_*.ko" -exec rm {} \;
find /lib/modules/3.5.0-25-generic -name "r8192ce_*.ko" -exec rm {} \;
find /lib/modules/3.5.0-25-generic -name "r8723e_*.ko" -exec rm {} \;
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ ^C
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ 

```


2nd edit:

I did the modprobe command just to make sure
Got this:

```
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ ^Cphillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ sudo modprobe rtl8723e
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012$ 

```

Does this mean it fully went through?

---

### Post by Hadaka on 2013-03-18
Hi, ok do this ...in this order,
go to Desktop and remove the file.
then.  click home...drag and drop


rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz

from Downloads to Desktop

then do..
```
cd Desktop
```
locate your file ... 
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
right click it and chose "extract here"
then try to load again.
thanks.

---

### Post by KamonB on 2013-03-18
Must not have refreshed :guitar:

I got it going when I copy pasted from the properties name, even though its exactly the same... The terminal likes that more.


Posted code above ^ does that mean it works now? Haha



edit:

IT WORKS!
[http://i.imgur.com/lNT55DR.jpg](http://i.imgur.com/lNT55DR.jpg)


Thank you so much brother, I wish I could give + Reputation or a +1 cause you deserve it man!


Hopefully I'll get better at Ubuntu over time and be able to help people like you did for me. I can't thank you enough.

---

### Post by Hadaka on 2013-03-18
WOW,,,thats awesome ! this was brand new territory for me
and i want to thank you for adding to my knowledge base.
glad its working !!

please use thread tools and mark this solved.
or edit the title and mark it [SOLVED]  if the
regular tools way is not working...
it was fun..thanks

just now spotted this.. [B]Also: I got NDISWrapper to work, however I don't know which *inf* file to select
delete that
thats a last resort driver and wont work for you anyway.
[/B]

---

### Post by KamonB on 2013-03-18
Oh my god.. 

I turned on my computer just now to find that again the driver is gone and although I've read and redone everything in this thread and I used the copy paste from file properties it's giving me errors on that now!


Does anyone know why this error keeps popping up relentlessly?!

```
phillip@ubuntu:~$ cd Desktopphillip@ubuntu:~/Desktop$ ls
bleachbit.desktop
Django-1.5
geany.desktop
gedit.desktop
Humble.Indie.Bundle.7
Python3
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
steam.desktop
the-basement-collection.desktop
phillip@ubuntu:~/Desktop$ 

```

I clearly have it on my desktop....
Yet I keep getting this error CONSTANTLY:

```
phillip@ubuntu:~$ cd Desktop
phillip@ubuntu:~/Desktop$ ls
bleachbit.desktop
Django-1.5
geany.desktop
gedit.desktop
Humble.Indie.Bundle.7
Python3
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
steam.desktop
the-basement-collection.desktop
phillip@ubuntu:~/Desktop$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ make
make -C /lib/modules/3.5.0-26-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make: *** [all] Error 2
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ 



```


After Step 2:
```
phillip@ubuntu:~$ sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`[sudo] password for phillip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.5.0-26-generic is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  gconf-editor linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phillip@ubuntu:~$ 

```


Step 3:
```
phillip@ubuntu:~$ sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`[sudo] password for phillip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.5.0-26-generic is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  gconf-editor linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ wget -O- http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz | tar -xz
--2013-03-18 22:52:01--  http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
Resolving dl.dropbox.com (dl.dropbox.com)... 107.22.254.1
Connecting to dl.dropbox.com (dl.dropbox.com)|107.22.254.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8997390 (8.6M) [application/x-tar]
Saving to: `STDOUT'


100%[======================================>] 8,997,390   4.91M/s   in 1.7s    


2013-03-18 22:52:04 (4.91 MB/s) - written to stdout [8997390/8997390]


phillip@ubuntu:~$ 

```


Step 4: I took the folder and moved it to the Desktop, I copied the name and everything,
Why am I getting an error on the *make* command? [http://i.imgur.com/aNNiMv9.jpg](http://i.imgur.com/aNNiMv9.jpg)
```
phillip@ubuntu:~$ sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`[sudo] password for phillip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.5.0-26-generic is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  gconf-editor linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ wget -O- http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz | tar -xz
--2013-03-18 22:52:01--  http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
Resolving dl.dropbox.com (dl.dropbox.com)... 107.22.254.1
Connecting to dl.dropbox.com (dl.dropbox.com)|107.22.254.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8997390 (8.6M) [application/x-tar]
Saving to: `STDOUT'


100%[======================================>] 8,997,390   4.91M/s   in 1.7s    


2013-03-18 22:52:04 (4.91 MB/s) - written to stdout [8997390/8997390]


phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ 
phillip@ubuntu:~$ cd Desktop
phillip@ubuntu:~/Desktop$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ make
make -C /lib/modules/3.5.0-26-generic/build M=/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/phillip/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make: *** [all] Error 2
phillip@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ 

```

---

### Post by KamonB on 2013-03-27
bump, nobody?

---

