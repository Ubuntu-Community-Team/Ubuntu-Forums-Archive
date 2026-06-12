---
title: "wireless is disabled by hardware switch"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by sairam2000 on 2011-05-21
i hate to start a new thread that is already discussed in many places. But after hours and hours of digging, i am thinking there might be a 5 minute solution. But only if i know that... :frown:

I own a lenovo ideapad y450. my networking controllers are...
> Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
[B]The problem is i cannot access wifi. The network manager says the wireless is disabled by hardware switch.

[/B]My hardware switch for wireless (on the laptop) is infact ON.

when i try rfkill list all, the result is...
> 0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
when i try Fn+f5 (thatz the key to activate wireless), the result for rfkill list all is...
> 0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
from here there is no progress till now. i have checked my bios setting to see wlan is enabled (yes, it is.) I have restarted the system after rfkill unblock all. No result. i have also tried rfkill unblock wifi. i logged in ubuntu classic. wired and mobile broadband are working in all settings.

the result for dmesg | grep iwl

> sai@sai-laptop:~$ dmesg | grep iwl
[   10.124427] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.124431] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.124614] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.124662] iwlagn 0000:06:00.0: setting latency timer to 64
[   10.124721] iwlagn 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.158159] iwlagn 0000:06:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   10.158162] iwlagn 0000:06:00.0: Device SKU: 0Xb
[   10.199460] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.199620] iwlagn 0000:06:00.0: irq 49 for MSI/MSI-X
[   10.291057] iwlagn 0000:06:00.0: loaded firmware version 8.83.5.1 build 33692
[   10.383765] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
sai@sai-laptop:~$ ^C
sai@sai-laptop:~$ 


During natty installation (it was a fresh one) i had ticked for third party installations but had no internet running at that time. now the additional drivers under hardware in system settings shows nothing. just blank. NO MATTER WHAT I DID I HAVE COME TO THE FIRST STEP AGAIN. MY WIRELESS IS DISABLED BY HARDWARE SWITCH. _where is this switch_ & how do i switch it on (if thatz so easy.)

sorry guys for repeat topic. but all the solutions given in other thread were specific to some system or condition and mine somehow did not match.

This forum has solved many of my nightmares just like a cakewalk. I am thankful.

---

### Post by chili555 on 2011-05-21
Please raise your right hand and solemnly swear on my copy of C/C++ Programmer's Bible, autographed by Linus Torvalds, that switch #5 here is in the 'On' position. If so, please post:```
lsmod
```Thanks.

---

### Post by sairam2000 on 2011-05-22
thanks chili555 for the reply and ur effort to get that image of laptop! yes that 5th switch is ON. when it is off,
> sai@sai-laptop:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


and when it is on (with fn+f5), the old status returns
> sai@sai-laptop:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


the result for ur query is[FONT=monospace]

[/FONT]> sai@sai-laptop:~$ lsmod
Module                  Size  Used by
sha256_generic         20911  2 
binfmt_misc            13213  1 
cryptd                 19801  0 
aes_i586               16956  331 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255896  1 
snd_hda_intel          24140  2 
arc4                   12473  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
iwlagn                284601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               66851  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
iwlcore               148965  1 iwlagn
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              257001  2 iwlagn,iwlcore
psmouse                59039  0 
jmb38x_ms              17364  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 iwlagn,iwlcore,mac80211
memstick               15816  1 jmb38x_ms
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ideapad_laptop         13262  0 
sparse_keymap          13666  1 ideapad_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  446547  3 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
tg3                   131476  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
drm_kms_helper         40745  1 i915
acpi_igd_opregion      13574  1 i915
drm                   184133  5 i915,drm_kms_helper,acpi_igd_opregion
i2c_algo_bit           13184  1 i915
ahci                   21591  3 
libahci                25548  1 ahci
video                  18951  1 i915
sai@sai-laptop:~$ 


---

### Post by MKdx on 2011-05-22
try this after startup
```
sudo modprobe lib80211
sudo modprobe lib80211_crypt_tkip
sudo modprobe wl
sudo modprobe acer_wmi
rfkill unblock all
sudo rmmod acer_wmi
```

---

### Post by sairam2000 on 2011-05-22
hello MKdx, thx for ur reply. i did ur codes. the results were

> sai@sai-laptop:~$ sudo modprobe lib80211
[sudo] password for sai: 
sai@sai-laptop:~$ sudo modprobe lib80211_crypt_tkip
sai@sai-laptop:~$ sudo modprobe wl
FATAL: Module wl not found.
sai@sai-laptop:~$ sudo modprobe acer_wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.38-9-generic-pae/kernel/drivers/platform/x86/acer-wmi.ko): No such device
sai@sai-laptop:~$ rfkill unblock all
sai@sai-laptop:~$ sudo rmmod acer_wmi
ERROR: Module acer_wmi does not exist in /proc/modules
sai@sai-laptop:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


Is it something about damage to the card or will it recover if i go for complete OS reinstallation?

---

### Post by chili555 on 2011-05-22
> **MKdx said:**
> try this after startup
```
sudo modprobe lib80211
sudo modprobe lib80211_crypt_tkip
sudo modprobe wl
sudo modprobe acer_wmi
rfkill unblock all
sudo rmmod acer_wmi
```Do you see acer_wmi in his lsmod? Do you see wl? What the heck good is wl going to do for an Intel wireless card? I really want to understand.

---

### Post by chili555 on 2011-05-22
> Is it something about damage to the card or will it recover if i go for complete OS reinstallation?We haven't seen any sign of damage to the card yet, let's hold off for now.

Please try:```
sudo rmmod -f ideapad-laptop
sudo rfkill unblock all
rfkill list all
```Any improvement?

---

### Post by sairam2000 on 2011-05-22
hi chili555, thx for ur consistent support. i am seeing u r active in other threads too giving solutions or trying passionately. Great job.

After ur code, the usual first two lines (result of rfkill list all) were gone.
> sai@sai-laptop:~$ sudo rmmod -f ideapad-laptop
[sudo] password for sai: 
sai@sai-laptop:~$ sudo rfkill unblock all
sai@sai-laptop:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
i tried enabling/disabling fn+f5, the result is same. and tried hardware slider switch on and off, the result remains the same.

---

### Post by chili555 on 2011-05-22
Are you certain that the wireless is enabled in the BIOS? I am out of ideas.

---

### Post by nbrebol on 2011-05-22
Hi, i have (i think) the exact same problem. I have a Lenovo y560 and i used to run windows 7 until my hard drive died. i had an old one that i plugged in and decided to run ubuntu since i didn't want to buy Windows again. long story short, my physical hardware switch is turned to "on" yet according to the network manager, my wireless is disabled. i get the same results as you did when i do "rfkill list all" with the physical switch turned on and off.

Also, i had tried reinstalling the OS but to no avail. My only thought is that i read somewhere either on the forums or another support page that some network drivers had to be turned on using Windows OS. In other words, if you dual-boot you have to boot Windows, make sure the wireless is enabled, then boot Ubuntu. I am not sure if this is true or not but i have no way to tell since i can't boot windows...

Thank you chili555 for your help so far. One question i have is how do i tell if wireless is enabled in the BIOS?



Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

---

### Post by chili555 on 2011-05-22
> One question i have is how do i tell if wireless is enabled in the BIOS?As the computer is booting, in the first few seconds, you will see an option to press Del or Esc or F1 or some such to enter the setup menu. That's the BIOS. Look around for any options to enable or disable wireless. One of my laptops has the diabolical option to enable or disable bluetooth; which also disables wireless!

---

### Post by nbrebol on 2011-05-23
> **chili555 said:**
> As the computer is booting, in the first few seconds, you will see an option to press Del or Esc or F1 or some such to enter the setup menu. That's the BIOS. Look around for any options to enable or disable wireless. One of my laptops has the diabolical option to enable or disable bluetooth; which also disables wireless!

ok thanks i checked that and it says it is enabled.

---

### Post by sairam2000 on 2011-05-23
> **chili555 said:**
> Are you certain that the wireless is enabled in the BIOS? I am out of ideas.
Ya, wireless is enabled in BIOS. i thought of reinstalling OS, then i saw this
> **nbrebol said:**
> Hi, i have (i think) the exact same problem...

...Also, i had tried reinstalling the OS but to no avail.
So i have to wait.

---

### Post by MKdx on 2011-05-24
My bad didn't notice the different model, saw the lenovo and lsmod output which was similar to my machine'. Had few modules not loading at startup at one point after switching between property drivers, ndswrapper and oss one while trying to get wireless to work, acer_wmi, wl and lib80211 ones :)

> **chili555 said:**
> Do you see acer_wmi in his lsmod? Do you see wl? What the heck good is wl going to do for an Intel wireless card? I really want to understand.

---

### Post by lvyaojia on 2012-04-08
I specially registered an account to replay your question!

cause I also have the same problem for few months.

so suffering!

but I solved!

press F2 when start up your pc,
jump to the last BIOS setting, load the default BIOS setting, and save.

all done. then the wifi works again! 
good luck.

---

### Post by dylan07 on 2012-04-08
> **lvyaojia said:**
> I specially registered an account to replay your question!

cause I also have the same problem for few months.

so suffering!

but I solved!

press F2 when start up your pc,
jump to the last BIOS setting, load the default BIOS setting, and save.

all done. then the wifi works again! 
good luck.

And if that doesnt work. Check to make sure that the driver is installed and activated. Look in "Additional Drivers" or "proprietary".

---

### Post by sairam2000 on 2012-04-08
> **lvyaojia said:**
> I specially registered an account to replay your question!

cause I also have the same problem for few months.

so suffering!

but I solved!

press F2 when start up your pc,
jump to the last BIOS setting, load the default BIOS setting, and save.

all done. then the wifi works again! 
good luck.
Thanks a lot lvyaojia. My two year wait has been finally over with lot of painful patience. Now i sit anywhere typing or browsing while my laptop feeds from home wifi. Thanks a lot.

---

### Post by jsiret on 2012-06-16
So I'm having the same problem except I close my lid, or disable the network/wireless, or I roll a 6 and the wireless hardware switch turns it's self off, then I must reboot and reset the bios.

Is there anyway around this?

---

### Post by qazam on 2012-12-15
> **lvyaojia said:**
> I specially registered an account to replay your question!

I specially registered an account to say THANKS to you!

---

### Post by xjq314 on 2013-02-15
> **lvyaojia said:**
> I specially registered an account to replay your question!

cause I also have the same problem for few months.

so suffering!

but I solved!

press F2 when start up your pc,
jump to the last BIOS setting, load the default BIOS setting, and save.

all done. then the wifi works again! 
good luck.

I specially register to say thank you. I have been search for the solutions for the whole day until I read your answers. Thank you so much.

---

