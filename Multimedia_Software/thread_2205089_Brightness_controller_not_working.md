---
title: "Brightness controller not working"
date: 2014-02-11
forum: Multimedia Software
---

### Post by tankarakesh.38 on 2014-02-11
Hello All,
     I am new to ubuntu. Recently installed 13.10 in my laptop(LenovoG510-I3 4th Gen-4GBRAM-500GBHDD-2GB graphics Radeon).I unable to control brightness of my laptop. I tried adding "[FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX="acpi_backlight=vendor[/FONT]" and "[FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX"acpi_osi=linux[/FONT]". I am able to see the brightness slider but it has no effect the same while changing the slider. I also added "backlist ideapad" in "/sys/class/backlight/../". For additional info. the backlight for my laptop is IDEAPAD.
Please help me.

---

### Post by Toz on 2014-02-12
Lets have a closer look at some of the settings. Open a terminal window, type in the following commands, and post back the results within **[noparse]```
 
```[/noparse]** tags:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```

3. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

4. A listing of your loaded kernel modules:
```
lsmod
```

5. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by tankarakesh.38 on 2014-02-12
Hi, here are the links that are generated. kindly solve it asap.

**1**. cat /proc/cmdline=```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=bf6e98ef-3739-4153-8345-8a8834f7147a ro acpi_backlight=vendor nomodeset
```
**2**. lspci -k | grep -iA2 VGA
```
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
	Subsystem: Lenovo Device 3801
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
```
**3.** for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
/sys/class/backlight/ideapad
3
16
3
```
**4.** lsmod
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
vesafb                 13828  1 
joydev                 17377  0 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm                   431720  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20359  1 ghash_clmulni_intel
rts5139               331166  0 
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
lib80211_crypt_tkip    17619  0 
microcode              23576  0 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_conexant    56990  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                97655  0 
wl                   4207760  0 
snd_hda_intel          48171  5 
serio_raw              13413  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
cfg80211              480503  1 wl
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21080  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
i915                  661261  2 
snd                    69141  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ideapad_laptop         18342  0 
drm_kms_helper         52710  1 i915
sparse_keymap          13948  1 ideapad_laptop
drm                   297056  2 i915,drm_kms_helper
video                  19318  1 i915
mei_me                 18421  0 
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
mei                    77782  1 mei_me
lp                     17759  0 
soundcore              12680  1 snd
parport                42299  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
usbhid                 53014  0 
hid                   105858  3 usbhid,hid_logitech_dj
ahci                   25819  2 
alx                    32452  0 
libahci                31928  1 ahci
mdio                   13807  1 alx
```
**5**. pastebinit /var/log/Xorg.0.log
```
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>
```

---

### Post by Toz on 2014-02-12
> my laptop(LenovoG510-I3 4th Gen-4GBRAM-500GBHDD-2GB graphics Radeon
A radeon graphics chip is not showing up in the lscpi or lsmod listings. Are you sure there is a radeon graphics chip in this system? 
Can you try again:
```
lspci -k | grep -A2 VGA
```



Can you remove the "acpi_backlight=vendor" kernel parameter, reboot your computer, and post back again:
```
cat /proc/cmdline
```
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```



And finally, can you please install pastebinit (its a small program and it is really helpful for troubleshooting because it posts your log file online for easy viewing):
```
sudo apt-get install pastebinit
```
...then run again:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated?

---

### Post by tankarakesh.38 on 2014-02-12
1.  [COLOR=#000000][FONT=Ubuntu Mono]pastebinit /var/log/Xorg.0.log[/FONT][/COLOR]<code>[http://paste.ubuntu.com/6920162/](http://paste.ubuntu.com/6920162/)
</code>
2.[COLOR=#000000][FONT=Ubuntu Mono]for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
<code>
[/FONT][/COLOR]

 /sys/class/backlight/ideapad
1
16
1


[COLOR=#000000][FONT=Ubuntu Mono]</code>
3.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lspci -k | grep -A2 VGA
<code>
[/FONT][/COLOR]00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
	Subsystem: Lenovo Device 3801
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)


[COLOR=#000000][FONT=Ubuntu Mono]</code>
4. [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cmdline-unable to change acpi_backlight=vendor
<code>
[/FONT][/COLOR]BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=bf6e98ef-3739-4153-8345-8a8834f7147a ro acpi_backlight=vendor nomodeset


[COLOR=#000000][FONT=Ubuntu Mono]
</code>[/FONT][/COLOR]

---

### Post by tankarakesh.38 on 2014-02-12
It a RADEON graphics

---

### Post by Toz on 2014-02-12
> **tankarakesh.38 said:**
> It a RADEON graphics

I see no evidence of radeon graphics in these log files. Can I see your dmesg log file?
```
pastebinit /var/log/dmesg
```
...and paste back the link that is generated.

According to your Xorg.0.log file, you are running in VESA mode (_not_ using the intel video driver). This is probably because you have "nomodeset" on your kernel boot line. Can you let us know why you are using that parameter? It may be why the backlight is not working.

---

### Post by tankarakesh.38 on 2014-02-12
Initially while booting Ubuntu I used to get black screen. To avoid it there was this parameter nomodeset . So I used. I checked with Windows its showing radeon graphic present in my system

---

### Post by Toz on 2014-02-12
Can I see your dmesg log file?
```

pastebinit /var/log/dmesg
```
...and paste back the link that is generated.




Also, can you follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions at the [KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") wiki and remove the **nomodeset** parameter and add the:
```
acpi_osi='!Windows 2012'
```
...kernel parameter to the boot line? When you've booted into the system, post back:
```
cat /proc/cmdline
```
If you get the black screen again and the brightness function keys don't work, simply reboot your computer to reset it back to nomodeset.

---

### Post by tankarakesh.38 on 2014-02-12
After removing nomodeset parameter from kernel, I am unable to see the UI of ubuntu. The system is showing only black screen after asking log in credentials.

---

### Post by tankarakesh.38 on 2014-02-12
Why doesn't ubuntu detect my Radeon graphics in my laptop ?

---

### Post by Toz on 2014-02-13
> **tankarakesh.38 said:**
> After removing nomodeset parameter from kernel, I am unable to see the UI of ubuntu. The system is showing only black screen after asking log in credentials.

So you do see the login prompt?

Can you Ctrl+Alt+F1, log in to the text console, run this command:
```
cat /proc/cmdline
```
...and post back the results?

---

### Post by Toz on 2014-02-13
> **tankarakesh.38 said:**
> Why doesn't ubuntu detect my Radeon graphics in my laptop ?

Perhaps if I could get a look at your dmesg log file.....

---

### Post by tankarakesh.38 on 2014-02-13
Hi TOZ,
   I am shifting to Win8 temporarily. Currently avoiding ubuntu and will be back soon. Anyway thanks for your support in replying to my issue.

---

### Post by tankarakesh.38 on 2014-02-25
Hi toz, today I installed Ubuntu 14.04. In this version I am able to adjust the brightness but I am unable to find out wifi to connect. I am able to connect through ethernet .

---

### Post by Toz on 2014-02-25
> **tankarakesh.38 said:**
> Hi toz, today I installed Ubuntu 14.04. In this version I am able to adjust the brightness but I am unable to find out wifi to connect. I am able to connect through ethernet .

You should create a new thread in the Networking subforum - someone will be able to provide assistance there.

---

