---
title: "Ubuntu on Vostro 1700 Wireless Driver"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Webnet on 2013-02-19
Yesterday I installed Ubuntu Desktop (didn't see a laptop version) on my Dell Vostro 1700 and everything's running smooth except the wireless.  **iwconfig** shows no wireless device.  I only found [this wiki page]("https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700") on Google and followed the wireless section to no avail.

I've checked Dell's web site and they don't have linux drivers.

Does anyone have any ideas on how to get this up and running?

---

### Post by Hadaka on 2013-02-19
Hi, please post the output of...

```
arch
lspci -nn | egrep '0200|0280'
lsmod 
```
thanks.

---

### Post by Webnet on 2013-02-19
Thanks for your willingness to help...

> ben@ben-Vostro-1700:~$ arch
i686
ben@ben-Vostro-1700:~$ lspci -nn | egrep '0200|0280'
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
ben@ben-Vostro-1700:~$ lsmod
Module                  Size  Used by
bnep                   17708  2 
parport_pc             31969  0 
ppdev                  12818  0 
rfcomm                 37277  12 
coretemp               13169  0 
kvm                   357807  0 
gpio_ich               13160  0 
dell_wmi               12602  0 
sparse_keymap          13659  1 dell_wmi
nouveau               823896  4 
ttm                    75535  1 nouveau
drm_kms_helper         47304  1 nouveau
drm                   238811  6 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13198  1 nouveau
mxm_wmi                12894  1 nouveau
psmouse                84878  0 
dell_laptop            17162  0 
dcdbas                 14055  1 dell_laptop
microcode              18210  0 
snd_hda_codec_idt      59762  1 
serio_raw              13032  0 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
r592                   17708  0 
r852                   17906  0 
sm_common              16773  1 r852
nand                   49497  2 r852,sm_common
nand_ids                8548  1 nand
videodev               95842  2 uvcvideo,videobuf2_core
mtd                    38603  2 sm_common,nand
nand_bch               13004  1 nand
bch                    17227  1 nand_bch
videobuf2_vmalloc      12757  1 uvcvideo
nand_ecc               13106  1 nand
videobuf2_memops       13213  1 videobuf2_vmalloc
memstick               15843  1 r592
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
joydev                 17162  0 
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
lpc_ich                16926  0 
snd_seq_midi           13133  0 
btusb                  17987  0 
bluetooth             183270  22 bnep,rfcomm,btusb
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ssb_hcd                12750  0 
b43                   347311  0 
bcma                   34484  1 b43
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
mac_hid                13038  0 
video                  18848  1 nouveau
wmi                    18591  3 dell_wmi,nouveau,mxm_wmi
iwl3945                63696  0 
iwlegacy               87773  1 iwl3945
mac80211              461203  3 b43,iwl3945,iwlegacy
cfg80211              175574  4 b43,iwl3945,iwlegacy,mac80211
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
hid_logitech_dj        18173  0 
usbhid                 41734  1 hid_logitech_dj
hid                    82179  3 hid_generic,hid_logitech_dj,usbhid
b44                    31327  0 
firewire_ohci          35522  0 
firewire_core          57493  1 firewire_ohci
sdhci_pci              18156  0 
sdhci                  27831  1 sdhci_pci
crc_itu_t              12628  1 firewire_core
ssb                    50088  3 ssb_hcd,b43,b44

---

### Post by ahallubuntu on 2013-02-19
Yep - you have a Broadcom BCM4321 wireless card (rebranded as a Dell card - with Broadcom chipset).  They commonly have issues in Ubuntu, though some of them work automatically (I booted Ubuntu on newer Latitude the other day and the Broadcom card worked automatically).  You can search the forums or just Google for the right recipe to make it work - it's a very common issue.  I try to pop out my Broadcom wireless cards and replace them with Intel wireless cards whenever I acquire a Dell laptop to refurbish, because Intel cards generally work right out of the box.  (At least they do for me!)

Maybe someone else can give you more specific help for your card if you can't figure it out from here.  It's a matter probably of installing or updating something in the terminal.

---

### Post by chili555 on 2013-02-19
What explains this?> iwl3945 63696 0
iwlegacy 87773 1 iwl3945
mac80211 461203 3 b43,iwl3945,iwlegacy
cfg80211 175574 4 b43,iwl3945,iwlegacy,mac80211And this?> ssb_hcd 12750 0
b43 347311 0
bcma 34484 1 b43May we see:```
cat /etc/modules
```Before we fix it properly, we may need to un-fix a few conflicting things.

Do you have a temporary working ethernet connection?

---

### Post by westie457 on 2013-02-19
This link tells us that your wireless chip uses the Broadcom STA driver [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

We will try that one first.

Plug an ethernet cable in. This is to make things easier.
Open Software Sources and go to the Ubuntu Software tab. In here make sure the top for boxes are checked. Close out.

Open a terminal (click on the logo top-left and start typing terminal and hit Enter).

In the terminal run these commands one at a time ```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source

sudo modprobe wl
```
Before running the last command wait a couple of minutes and click on the Network icon (top-right of the screen) and see if there is any available networks. If there is, the third command is not necessary. If nothing, run the last command and check after a short wait.

If still nothing, unplug the cable and reboot the computer. It should now work.


Let us know what happens.

Thank you.

Edit.... chili555 noticed something I missed. Go with what chili555 asks you to do.

---

### Post by chili555 on 2013-02-19
bcmwl-kernel-source blacklists *ssb* which is needed by his ethernet. If you un-blacklist *ssb*, then *b43* loads and conflicts with *wl*. How would you suggest we handle that?

---

### Post by westie457 on 2013-02-19
@ chili555

You got in while I was still composing my reply to the OP. I have already added an edit to my post and am graciously withdrawing from this thread.
I will however be looking on with interest on how the conflicts you spotted are cleared up.
I will learn something from this and might actually remember to look properly one day.

PS. No hard feelings from me.

---

### Post by chili555 on 2013-02-19
> **westie457 said:**
> @ chili555

You got in while I was still composing my reply to the OP. I have already added an edit to my post and am graciously withdrawing from this thread.
I will however be looking on with interest on how the conflicts you spotted are cleared up.
I will learn something from this and might actually remember to look properly one day.

PS. No hard feelings from me.No worries my friend. I am not exactly sure what to do myself and I hoped you had a trick you could help us with. My question, how would you suggest we handle that, was asked because I am not quite sure myself! I hoped you knew!

I suppose we could un-blacklist *ssb* and rename  /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/b43/b43.ko into b43.xx so it doesn't load. What would you, ahallubuntu and Hadaka think about it? 

Of course, all would be solved if the original poster never needs his ethernet after today.

---

### Post by westie457 on 2013-02-19
@ webnet

To help chili555 and any others interested could you follow the suggestion in this post please. [http://ubuntuforums.org/showpost.php?p=12322392&postcount=4](http://ubuntuforums.org/showpost.php?p=12322392&postcount=4)

---

### Post by Hadaka on 2013-02-19
Hi, i vote for first cleaning out all the mystery drivers
and perhaps loading linux-firmware-nonfee. But I think
i too shall sit back with mr westie and observe the master
dr chili555 pull the rabbit out of the hat ;)

---

### Post by Webnet on 2013-02-19
I'm shocked there was so much activity this thread.  Thank you guys for the help.  It really gives me confidence in using Ubuntu as my primary OS with such a good community! 

> ben@ben-Vostro-1700:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
iwl3945

I'm a web developer so command line is familiar territory for me.  Just wanted to save you guys some explinations :)

I did not install bcmwl-kernal-source

I do have a working ethernet connection.

---

### Post by Hadaka on 2013-02-19
Hi, i "may" have found a work around, please post the directory
contents of
```
 /etc/modprobe.d
```im looking for a file the sta driver creates.
thanks

p.s
did you add "loop" to /etc/modules ?
*IF NOT then please ..gedit /etc/modules
and delete....loop and iwl3945
thanks again

---

### Post by Webnet on 2013-02-19
Sure thing, here you go!

> ben@ben-Vostro-1700:~$ ll /etc/modprobe.d
total 60
drwxr-xr-x   2 root root  4096 Feb 18 07:46 ./
drwxr-xr-x 137 root root 12288 Feb 19 21:28 ../
-rw-r--r--   1 root root  2507 Oct  7 21:34 alsa-base.conf
-rw-r--r--   1 root root   325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Mar 18  2011 blacklist.conf
-rw-r--r--   1 root root   210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r--   1 root root   677 Oct  1 09:26 blacklist-framebuffer.conf
-rw-r--r--   1 root root    18 Feb 18 07:46 blacklist-ipw3945.conf
-rw-r--r--   1 root root   156 Oct  7 21:34 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Feb 18 07:33 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Mar 18  2011 blacklist-watchdog.conf
-rw-r--r--   1 root root   347 Oct  1 09:26 iwlwifi.conf
-rw-r--r--   1 root root    30 Aug  2  2012 vmwgfx-fbdev.conf

---

### Post by Hadaka on 2013-02-19
Hi, this was in the /etc/modprobe.d directory

Feb 18 07:46 blacklist-ipw3945.conf

it looks like it was loaded yesterday, its for an intel wireless card?
do you have a secondary wireless card in your machine??

---

### Post by Webnet on 2013-02-19
I just installed Ubuntu yesterday.  There's only 1 wireless card.

---

### Post by chili555 on 2013-02-19
Please check on iwlwifi.conf, also, Hadaka. I suspect these are random attempts at fixes after reading too many forum posts.

---

### Post by Webnet on 2013-02-19
I did try one solution from the get-go, which was this one: [https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700#WIRELESS](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700#WIRELESS)

> ben@ben-Vostro-1700:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

---

### Post by Hadaka on 2013-02-19
Well, we'll just have to randomly unfix,:p
did you delete the 2 lines from /etc/modules....post #13
and did you do the updates/upgrade after you loaded the os?
*IF NOT please do..
```
sudo apt-get update
sudo apt-get upgrade
```and..my error...what os did you load ubuntu 12.04...12.10 ??
sorrry i forgot to ask.

---

### Post by chili555 on 2013-02-19
The iwlwifi.conf is harmless; iwl3945.conf probably needs to go, although it probably won't hurt anything.

---

### Post by Webnet on 2013-02-19
I had installed 12.10, so i did not think to run apt-get upgrade.  I've done that, rebooted and nothing fixed itself :-\

I also removed the 2 lines from /etc/modules prior to reboot.  I had missed that, thanks for pointing it out again.

If I need to remove the iwl file I can.

---

### Post by chili555 on 2013-02-19
Please do:```
sudo apt-get install bcmwl-kernel-source
```After it is done, your wireless should be working. Be sure you make the suggested amendments to /etc/modules.

---

### Post by Webnet on 2013-02-19
I don't even have time to reboot if that's needed after this... built while running that command I saw a few errors and a FATAL...

> Building for architecture i686
Building initial module for 3.5.0-23-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-23-generic/updates/dkms/

depmod........

DKMS: install completed.
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb is in use by ssb_hcd,b44
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
FATAL: Module ssb is in use.
update-initramfs: deferring update (trigger activated)
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic

---

### Post by Hadaka on 2013-02-19
Hi, that usually happens if you are NOT connected to the internet

---

### Post by Hadaka on 2013-02-19
Hi, that usually happens if you are NOT connected to the internet
or you have a flakey download location...try again

---

### Post by Hadaka on 2013-02-19
On second thought...that driver broadcom-kernel-source isnt going to load.
it is trying to blacklist the ssb module and the b44 dirver, which is what your
wired connection is currently using,so the wired connection would drop before
the wireless driver even finished loading.Hence the FATAL error...ssb in use
message. lets sleep on this one and start fresh tomorrow.

---

### Post by Hadaka on 2013-02-20
Hi, just for grins see if the non-free driver will load and work.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe43 
```without booting after it loads,remove the ethernet cable
and see if it works.
*If not, i would suggest deleting the 12.10 os and loading 12.04LTS
(12.04 is supported untill 2017..12.10 has about another year of support)
I would also pm Ahallubuntu for a suggestion on an intel wireless card,
or locate a linux supported usb stick. If anyone else has a suggestion on
this, please feel free to chime in.
If you decide to reload the os, if it asks to load a driver...say NO

---

### Post by chili555 on 2013-02-20
I'm very sorry to disagree with my good friend Hadaka, but I believe bcmwl-kernel-source is correct. The module built as expected. The build process didn't unload *ssb* because it was in use by the ethernet as we discussed above. I think all Webnet needs to do is detach the ethernet and reboot. I think the wireless will be working. If not, let's troubleshoot from there.

I most certainly would not recommend re-installing. Sorry.

---

### Post by Webnet on 2013-02-20
I am please to be writing to you from my laptop using my wifi :)

Thank you so much for the help!  Unplugging the ethernet resolved it!

---

### Post by chili555 on 2013-02-20
Awesome! Your ethernet is probably disabled and my pal Hadaka will walk you through the remedy.

Glad it's working!

---

### Post by Hadaka on 2013-02-20
Awesome !, once again i am amazed by chilli555. this work around
may or may not work for you, but if you care to give it a try, we can
perhaps get your wired connection going. please post the file contents
of /etc/modprobe.d
```
ls /etc/modprobe.d
```
thanks

---

### Post by Webnet on 2013-02-20
All I had to do was unplug the ethernet - which I'll never use anyways since I've got wifi.  I'm good now.  Thank you VERY much!!

---

### Post by chili555 on 2013-02-20
Never say never. If you do need to use it, you can get it to work temporarily with:```
sudo modprobe b44
sudo modprobe ssb
```It will go away on reboot. Hadaka and I suggest you retain this tip in case 'never' ever occurs.

---

