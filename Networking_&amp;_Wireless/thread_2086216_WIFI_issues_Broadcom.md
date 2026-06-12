---
title: "WIFI issues Broadcom"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by tyatyi on 2012-11-20
Hello dear All,

I am absolutely lost and I would like to ask advise. After upgrading to Ubuntu 12.04 my Broadcom WIFI driver stopped working.
I tried ndiswrapper with a windows driver, I also tried activating the driver as in previous comments, I tried also different distributions, but the driver is not active and wifi is not working. My expert friend also blacklisted the driver and reactivated, but no change.

These are the details:
 Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

It shows : wireless disabled by hardware switch. However I triple checked and the physical switch in ON. I switched ON/OFF not working. On some distros  it is not even showing this, it just not showing any wireless options.
Else : networking works  fine from ethernet cable and 3G stick.

Does anybody have any idea?? 
THANK YOU IN ADVANCE.

---

### Post by Bucky Ball on 2012-11-20
Uninstall ndiswrapper as it will prevent anything else working and is pretty much superseded by b43.

Did you do an update with the ethernet cable in? If not, uninstall ndiswrapper and do that, then check Additional Drivers.

If there's nothing there, try installing b43-fwcutter and firmware-b43-installer.

You may need to log out or restart to get the changes to happen.

---

### Post by NikTh on 2012-11-20
> **tyatyi said:**
> 
I tried ndiswrapper with a windows driver, I also tried activating the driver as in previous comments, I tried also different distributions, but the driver is not active and wifi is not working. My expert friend also blacklisted the driver and reactivated, but no change.

These are the details:
 Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller **[14e4:4727] **(rev 01)

Hi , 
the wireless card you have is supposed to work out of the box in 12.04 . You not need any restricted drivers and especially you don't need this ndiswrapper. 

Please follow bellow commands to remove completely this ndiswrapper thing

```
sudo modprobe -rf ndiswrapper 
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk sudo rm /etc/modprobe.d/ndiswrapper.conf 
sudo rm -r /etc/ndiswrapper/*  
sudo depmod -a
``` 

Then take a look here => [http://ubuntuforums.org/showthread.php?t=1985698](http://ubuntuforums.org/showthread.php?t=1985698)

Thanks

---

### Post by tyatyi on 2012-11-20
hello!! thank you.

ndiswrapper is removed as I am currently on a brand new installation of Mint.

I tried the code what suggested on the attached link:, and this was returned

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

What exactly is Hard blocked: yes means? Can it mean that my physical switch might be faulty? It is switched on for sure..

---

### Post by NikTh on 2012-11-20
Hard blocked means that wireless is of , but maybe we have a conflict here. (like the other thread I gave you). 

Let us see some extra info. 

Please open a terminal (CTRL+ALT+T) and execute bellow commands with order. (_Active Internet connection required_)

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo
sudo ./wirelessinfo
```The last command will produce a file named **netinfo.txt** inside your /home folder.
Click on **"New Reply"** and attach the file. [See here on how to attach a file]("http://i.stack.imgur.com/0E6qS.png") 

_Above is a script for debugging proposes. All your sensitive-personal data are hidden for security reasons. _

Thanks

---

### Post by tyatyi on 2012-11-20
Thank you I attached the file. I appreciate your help

---

### Post by NikTh on 2012-11-20
You have this wl driver installed and enabled. This is the additional driver . Try to remove it.

```
sudo apt-get remove --purge bcmwl-kernel-source
``` 
Then reboot and check the wireless again. 

If not working , give the results of 
```
lspci -nnk | grep -iA2 net 
lsmod
dmesg | grep -ie net -ie firm -ie b43 -ie wlan -ie eth
``` 

Thanks

---

### Post by tyatyi on 2012-11-20
Hello, 
after removal and reboot, the wireless is still disabled, no reaction on anything.
This is the results of the code: 

tyatyi@tyatyi-Lenovo ~ $ lspci -nnk | grep -iA2 net 
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Lenovo Device [17aa:3926]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: brcmsmac
tyatyi@tyatyi-Lenovo ~ $ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
bcma                   25651  0 
arc4                   12473  2 
snd_hda_codec_realtek   174055  1 
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
joydev                 17393  0 
psmouse                87140  0 
brcmutil               14675  1 brcmsmac
bnep                   17830  2 
parport_pc             32114  0 
snd_hda_intel          32765  3 
ppdev                  12849  0 
bluetooth             158438  7 bnep
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
serio_raw              13027  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 brcmsmac,mac80211
binfmt_misc            17292  1 
crc8                   12781  1 brcmsmac
ideapad_laptop         17890  0 
snd_timer              28931  2 snd_pcm,snd_seq
cordic                 12487  1 brcmsmac
sparse_keymap          13658  1 ideapad_laptop
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414568  2 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
wmi                    18744  0 
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
ums_realtek            17920  0 
hid                    77367  1 usbhid
uas                    17699  0 
r8169                  56321  0 
usb_storage            39646  2 ums_realtek
tyatyi@tyatyi-Lenovo ~ $ dmesg | grep -ie net -ie firm -ie b43 -ie wlan -ie eth
[    0.000000]   Transmeta GenuineTMx86
[    0.172640] NET: Registered protocol family 16
[    0.767295] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f44240d8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.767323] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.773993] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.782108] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f44240d8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.782373] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f44240d8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.797149] i2c-core: driver [aat2870] using legacy suspend method
[    0.797157] i2c-core: driver [aat2870] using legacy resume method
[    0.799477] NetLabel: Initializing
[    0.799484] NetLabel:  domain hash size = 128
[    0.799489] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.799524] NetLabel:  unlabeled traffic allowed by default
[    0.885683] NET: Registered protocol family 2
[    0.887918] NET: Registered protocol family 1
[    0.889208] audit: initializing netlink socket (disabled)
[    1.641282] NET: Registered protocol family 10
[    1.642835] NET: Registered protocol family 17
[    2.756140] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.758176] r8169 0000:05:00.0: eth0: RTL8102e at 0xf803a000, 00:26:9e:fb:71:2a, XID 04e00000 IRQ 43
[   15.382347] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.345148] NET: Registered protocol family 31
[   16.368354] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.967385] r8169 0000:05:00.0: eth0: link down
[   17.968372] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.969801] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.572754] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  109.973911] r8169 0000:05:00.0: eth0: link up
[  109.974627] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  120.664068] eth0: no IPv6 routers present

---

### Post by NikTh on 2012-11-20
Hi , 
try this 
```
sudo modprobe -rvf bcma
sudo modprobe -rvf brcmsmac
``` 

Then do 
```
sudo modprobe brcmsmac
```

See if wireless works. If yes we have to make it permanent because above is for one session only. 

Thanks

---

### Post by tyatyi on 2012-11-21
Hello, thank you, I tried the code, unfortunately WIFI still shows unavailable/disabled.

tyatyi@tyatyi-Lenovo ~ $ sudo modprobe -rvf bcma
[sudo] password for tyatyi: 
Sorry, try again.
[sudo] password for tyatyi: 
rmmod /lib/modules/3.2.0-23-generic/kernel/drivers/bcma/bcma.ko
tyatyi@tyatyi-Lenovo ~ $ sudo modprobe -rvf brcmsmac
rmmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
rmmod /lib/modules/3.2.0-23-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
rmmod /lib/modules/3.2.0-23-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/3.2.0-23-generic/kernel/lib/crc8.ko
rmmod /lib/modules/3.2.0-23-generic/kernel/lib/cordic.ko
tyatyi@tyatyi-Lenovo ~ $ sudo modprobe brcmsmac
tyatyi@tyatyi-Lenovo ~ $ ^C
tyatyi@tyatyi-Lenovo ~ $

---

### Post by Hadaka on 2012-11-21
Hi, Lenovo Fn/F5 keys toggle wireless card on and off.  Enter code...

```
rfkill list all
```*IF wireless shows hardblocked Yes, press Fn/F5  only one time and  repeat code...

```
rfkill list all
``` to see if it unblocked.

please also post..

```
grep -i blacklist /etc/modprobe.d/blacklist.conf
```then look at this thread...post #8
[http://ubuntuforums.org/showthread.php?t=2081537](http://ubuntuforums.org/showthread.php?t=2081537)


thanks

---

### Post by NikTh on 2012-11-22
Hi , 
this is weird , because bcma driver seems to support your wireless card 

> alias:          pci:v0000**14E4**d0000**4727**sv*sd*bc*sc*i*

but try what @Hadaka suggested . 
First install **linux-headers-generic** and the install **bcmwl-kernel-source** , @chilli555 is one of the wireless masters here :) 
Thanks

---

### Post by tyatyi on 2012-11-22
Hi , 

the fn/F5 combination just influenced the 'soft blocked' part and did not change the 'hard blocked'

tyatyi@tyatyi-Lenovo ~ $ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tyatyi@tyatyi-Lenovo ~ $ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
tyatyi@tyatyi-Lenovo ~ $ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tyatyi@tyatyi-Lenovo ~ $ grep -i blacklist /etc/modprobe.d/blacklist.conf
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
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
blacklist amd76x_edac

I tried also the suggestion on the different thread, I installed the headers and the driver according to the codes. But no change, after reboot it still shows, that wireless disabled by hardware switch... although the physical switch is clearly ON

sudo apt-get install linux-headers-generic sudo apt-get install --reinstall bcmwl-kernel-source sudo modprobe wl iwconfig

---

### Post by wildmanne39 on 2012-11-22
Hi, delete the wireless infotext file in your home folder then copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by chili555 on 2012-11-22
Just as a temporary experiment, please try:```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
sudo rfkill list all
```Now have we cured this?> 0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]Thanks.

There are several Broadcom devices that are covered by multiple drivers, brcmsmac, b43, wl, etc. The key is determining which works best. In this case, I believe bcmwl-kernel-source is optimal for 14e4:4727. Its installation handily blacklists everything else.

---

### Post by tyatyi on 2012-11-22
Hi 

attached is the file requested.

the commands did not change the 'hard locked' part:

tyatyi@tyatyi-Lenovo ~ $ sudo modprobe -r ideapad-laptop
tyatyi@tyatyi-Lenovo ~ $ sudo rfkill unblock all
tyatyi@tyatyi-Lenovo ~ $ sudo rfkill list all
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Thank you for trying to help

---

### Post by chili555 on 2012-11-22
Sticky little problem you have there! You might check here: [http://glonek.co.uk/linux-mint/wireless-disabled-stuck-in-phy0-hard-blocked/](http://glonek.co.uk/linux-mint/wireless-disabled-stuck-in-phy0-hard-blocked/)> If I reboot the machine and press the WiFi button on the laptop ONCE sometime before linux boots (took me 3 tries to get the timing right – needs to be somewhere between the BIOS and OS boot… hard to say) – then the phy0 hard block will go off! I can use my laptop WiFi again!You might also reset the BIOS to default. We have seen a few cases where this helps.

---

### Post by Hadaka on 2012-11-22
Hi, here is yet another link with a like hardblocked on a Lenovo
looks like a bios reset and a blacklist add.

[http://askubuntu.com/questions/143782/wireless-is-disabled-by-hardware-switch-lenovo-b460](http://askubuntu.com/questions/143782/wireless-is-disabled-by-hardware-switch-lenovo-b460)

hope this helps.

---

### Post by tyatyi on 2012-11-22
Hi,

it seems I am hopeless. I did all steps, I reset BIOS, I checked there under settings: Wireless is enabled. I tried the FN/F5 game as well during boot. Nothing.
I really think that the hardware switch might be faulty and not switching back correctly...
Unfortunately wireless still shows as disabled...
  
However now this results shows the following , two times wireless and one is yes, yes

0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by NikTh on 2012-11-22
Hi , 
please try this 
```
sudo modprobe -rvf ideapad-laptop
``` 
now try again the wireless switch (Fn+F5) . 
Working ? 
Thanks

---

### Post by Hadaka on 2012-11-22
@NikTH  all the fixes for hardblocked Lenovo i am finding seem to blacklist
acer-wmi...then bios reset. The info  Wildman requested showed wmi
in the lsmod list. So blacklisting just wmi might be worth a try. and possibly
a total power down including battery.

---

### Post by tyatyi on 2012-11-23
Hello ,

the previous code did not help. I pushed than FN/F5 and that only soft locked theWIFI but did not remove hard lock.
 
$ rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


"So blacklisting just wmi might be worth a try." 
How do I do this?

Thank you

---

### Post by NikTh on 2012-11-23
> **Hadaka said:**
> @NikTH  all the fixes for hardblocked Lenovo i am finding seem to blacklist
acer-wmi...then bios reset. The info  Wildman requested showed wmi
in the lsmod list. So blacklisting just wmi might be worth a try. and possibly
a total power down including battery.

I didn't read the answer #15 (@chili555 answer) , oh!! blind guy here :P . 
He already suggested the idepad-laptop rmmod. 

@tyatyi you can try to remove-unload  wmi and see if that helps 
```
sudo modprobe -rvf wmi
``` 
```
rfkill list all
```

---

### Post by tyatyi on 2012-11-23
Hi,

nothing really changed with the code:
After the first rfkill list I pressed FN/F5 and so the siflock was removed. But you can see the hardblock is still there.
However if you see the 'ideapad WLAN: Wireless LAN is showing hardblocked no.. How can this be? Why is it ?  THANK YOU AGAIN for trying to help.

tyatyi@tyatyi-Lenovo ~ $ sudo modprobe -rvf wmi
[sudo] password for tyatyi: 
rmmod /lib/modules/3.2.0-23-generic/kernel/drivers/platform/x86/wmi.ko
tyatyi@tyatyi-Lenovo ~ $ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
tyatyi@tyatyi-Lenovo ~ $ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by tyatyi on 2012-11-23
Hello
in addition what I have just realized that when I boot my laptop, the wireless indicator on the front of the keyboard is lit up, means active and at the moment Linux is starting than the indicator goes out. So it really seems that the OS is screwing it up.. No?

thanks again

---

### Post by Hadaka on 2012-11-23
Hi, as an experiment, try this..

turn off the wireless switch
turn off wireless in bios
turn off the computer
boot back up
reset the bios to wireless on
set the wireless switch to on

any changes?

---

### Post by tyatyi on 2012-11-23
Hi , no changes unfortunately, after doing all the steps you suggested-
Thanks again.

---

### Post by NikTh on 2012-11-23
Can you try to reset the BIOS to default settings and try again ? 
Thanks

---

### Post by chili555 on 2012-11-23
> tyatyi@tyatyi-Lenovo ~ $ rfkill list all
[COLOR="Red"]0: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: yes[/COLOR]
1: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
2: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: noOle Chili doesn't like this one bit! That is, I suspect, the Broadcom driver provided by bcmwl-kernel-source. Let's try:```
sudo modprobe -rf wl
sudo rfkill unblock all
rfkill list all
```What does it say now?

I wonder if we need to compile a later Broadcom STA driver...

---

### Post by ainu92 on 2012-11-23
Hi wireless is not working in ubuntu wubi in hpmini no networks are displayed plzz help

---

### Post by NikTh on 2012-11-23
> **ainu92 said:**
> Hi wireless is not working in ubuntu wubi in hpmini no networks are displayed plzz help

Hi, 
please open a new Thread (your thread) at [Networking & Wireless](http://ubuntuforums.org/forumdisplay.php?f=336) section. 
Thanks

---

### Post by tyatyi on 2012-11-23
It shows:

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

Still no wireless. Only the wired is shown on the panel.

---

### Post by chili555 on 2012-11-23
> 0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: noIt is *NOT* hard blocked!!! So it seems it certainly is related to the Broadcom driver. Now do:```
sudo modprobe wl
rfkill list all
```Now what is the report?

---

### Post by tyatyi on 2012-11-23
This is the report now :-)


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by chili555 on 2012-11-23
It is pretty clearly an issue with the bcmwl-kernel-source driver. Without it, you are not blocked; with it, you are. Let's see what version you have:```
sudo dpkg -s bcmwl-kernel-source | grep -i version
```In 12.10, I have 5.100.82.112, the same as the latest on Broadcom's site. According to the README:> ISSUES FIXED AND WHAT'S NEW IN RECENT RELEASES
-------------------------------------------
+ Supports monitor mode
+ Supports cfg80211
+ Supports hidden networks
+ [COLOR="Red"]Supports rfkill[/COLOR]We might try compiling the newest version.

---

### Post by tyatyi on 2012-12-04
Hello, thank you for all your help, and sorry for not getting back earlier but the laptop was at service.
It was a physical fault of the motherboard, and that had to be fixed.
Thanks for all you tries and help. 
Very good community and help forum++++ !!!

---

