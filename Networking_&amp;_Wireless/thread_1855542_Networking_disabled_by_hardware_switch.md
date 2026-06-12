---
title: "Networking disabled by hardware switch"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by geekman2 on 2011-10-06
I am running Ubuntu 11.04 on a acer aspire one zg5 netbook and for the past two weeks my wireless networking has worked flawlessly. But after i disabled wireless to save battery power it would no longer let me re-enable wireless saying "wireless is disabled by hardware switch" Please help

---

### Post by jaj123 on 2011-10-06
try to paste this in terminal and post the result

rfkill list

---

### Post by jaj123 on 2011-10-06
And try this in terminal too and see if it works

rfkill unblock all

---

### Post by wildmanne39 on 2011-10-06
Hi, welcome to the forum! Please try this if it works we will need to make it permanent.
```
sudo rmmod -f acer-wmi
```
Thank you

---

### Post by dostumai on 2011-10-06
I've got the same problem, none of my networking functions work - wireless or mobile broadband - and the enable wireless button is grayed out.

---

### Post by geekman2 on 2011-10-06
> **wildmanne39 said:**
> Hi, welcome to the forum! Please try this if it works we will need to make it permanent.
```
sudo rmmod -f acer-wmi
```Thank you
 
I tried that, it returns "no such file or directory"

---

### Post by geekman2 on 2011-10-06
I already tried rfkill list and rfkill unblock all both do nothing

---

### Post by jaj123 on 2011-10-06
Go to /etc/modprobe.d  and see if you can find anything about your wifi card or drivers in any of the files.
If you can, delete it (back up the file first).

---

### Post by geekman2 on 2011-10-06
Through nautilus or terminal if through terminal how?

---

### Post by jaj123 on 2011-10-06
Through nautilus.
You will need root access to edit anything so in terminal:

gksudo nautilus

---

### Post by geekman2 on 2011-10-06
why am i deleting the driver?

---

### Post by wildmanne39 on 2011-10-06
Hi, we need to approach this systematically, I will need to see the results of the commands I post and please do not delete or mess with any config files.
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by geekman2 on 2011-10-06
the result of the first command:
bash: cat/etc/lsb-release: No such file or directory
Linux Unbuti 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux

of the second:
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:015b]
    Kernel driver in use: r8169
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e008]
    Kernel driver in use: ath5k

of the third:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr off   Fragment thro
          Power Management off

Fourth:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

And finally:

Module                  Size  Used by
ndiswrapper           192828  0 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
i915                  451033  3 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
drm_kms_helper         40745  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ath5k                 144534  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
acerhdf                14217  0 
uvcvideo               66851  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                73312  0 
serio_raw              12990  0 
drm                   184164  4 i915,drm_kms_helper
cfg80211              156212  3 ath5k,ath,mac80211
jmb38x_ms              17364  0 
memstick               15816  1 jmb38x_ms
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
r8169                  42534  0 


Thanks for your help by the way!

---

### Post by jaj123 on 2011-10-06
The files in modprobe.d blocks drivers and stuff.
tex if you try to install a newer version the old one will be blocked,
Even if you uninstall the newer version the old driver might still be blocked

---

### Post by geekman2 on 2011-10-06
> **jaj123 said:**
> The files in modprobe.d blocks drivers and stuff.
tex if you try to install a newer version the old one will be blocked,
Even if you uninstall the newer version the old driver might still be blocked

I got into modprobe.d what am i looking for?

---

### Post by jaj123 on 2011-10-06
Do you use Windows wireless drivers (ndiswrapper)?

Did you use it when your connection was working?

---

### Post by geekman2 on 2011-10-06
I think so,  the only thing i know about my drivers is that up until last night my wireless worked perfectly but nothing changed between when it worked and when it didnt. Windows xp was previously installed if that helps

---

### Post by jaj123 on 2011-10-06
Did your wifi card worked out of the box when you installed ubuntu?

Do you see a file in modprobe.d called ndiswrapper or somthing similar?

---

### Post by wildmanne39 on 2011-10-06
Hi, your drivers are installed and so is ndiswrapper  so we need to remove it, also your hardware is off.

Run this command for ndiswrapper please:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Run those commands one at a time and see if you can turn your wireless on.

If not make sure something did not happen to turn it off in the bios.
Thank you

---

### Post by geekman2 on 2011-10-06
> **jaj123 said:**
> Did your wifi card worked out of the box when you installed ubuntu?

Do you see a file in modprobe.d called ndiswrapper or somthing similar?
  yes to both of your questions, it worked out of the box and there is a file called ndiswrapper

---

### Post by geekman2 on 2011-10-06
> **wildmanne39 said:**
> Hi, your drivers are installed and so is ndiswrapper  so we need to remove it, also your hardware is off.

Run this command for ndiswrapper please:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```Run those commands one at a time and see if you can turn your wireless on.

If not make sure something did not happen to turn it off in the bios.
Thank you

Shouldn't  I check BIOS first?

---

### Post by wildmanne39 on 2011-10-06
Hi, no ndiswrapper needs to be removed so why not get rid of it.
Thank you

---

### Post by jaj123 on 2011-10-06
Then you need to uninstall ndiswrapper either with the commands wildmanne posted or with ubuntu software center and make sure the file in modprobe.d is deleted.

---

### Post by wildmanne39 on 2011-10-06
Hi, the command will do a better job of getting rid of it and it will get rid of the config files as well.
Thank you

---

### Post by geekman2 on 2011-10-06
OK I did that, what now

---

### Post by jaj123 on 2011-10-06
Restart your computer.

---

### Post by geekman2 on 2011-10-06
That worked! thanks for your help both of you! I posted this via wireless

---

### Post by wildmanne39 on 2011-10-06
Hi, did you check your wireless lan in bios?

Please do this:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0 without sudo:
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

### Post by wildmanne39 on 2011-10-06
Hi, if you have any more problems with hard block do what I mentioned in post 28.

If I have been helpful would you please click on the red link in my signature and show your support for me becoming an ubuntu member? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

