---
title: "Acer Aspire 5310 WiFi ''switch'' BCM4311"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by poccio on 2013-07-17
Hello, I'm completely new to Ubuntu (installed 2 days ago). I have installed Ubuntu 12.04 LTS from a Usb key. When I was using the Usb key before installing it downloaded the STA Broadcom driver and activated it so I thought that it might be already inside Ubuntu that I then installed. The wifi didn't work so after going around the forum I downloaded the b43 driver which should automtically install the firmware but my wifi still won't work, also the Additional drivers app in System settings tells me there are no proprietary drivers in use. 
Let me explain better, its more like I don't have Wifi capabilty at all. There is a wifi "switch" but it's really an independent key on the top of the keyboard (please note this is not my computer but a pic from the internet, my keyboard is an italian one) and I suspect if I could get that to work my wireless would too. Please note also that I have read the sticky about BCM4311 in this section but didn't understand everything and what little I understand seeme not applicable to my problem. Please help and please give me detailed instructions as I don't really know my way around Ubuntu yet!!     
[IMG]http://images02.olx.be/ui/4/19/87/65791287_2-Acer-Aspire-5310-Charleroi.jpg[/IMG]

---

### Post by praseodym on 2013-07-17
Hi,

please download this file and save it in "Downloads"

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Install it via terminal (CTRL+ALT+T)
```

sudo dpkg -i ~/Downloads/*.deb
sudo modprobe -v b43
```
After that please show the outputs of
```

lsmod
iwconfig
dmesg | grep b43
rfkill list
```

---

### Post by poccio on 2013-07-17
ok  did the irst part, but after i put in 
> 
sudo modprobe -v b43

this comes out
> 
insmod /lib/modules/3.5.0-36-generic/kernel/drivers/bcma/bcma.ko
insmod /lib/modules/3.5.0-36-generic/kernel/drivers/ssb/ssb.ko
nd then it just stops but if i try to close the terminal it tells me there is a process running...what's happening?

---

### Post by praseodym on 2013-07-17
Exit it and reboot. After that check the outputs.

---

### Post by poccio on 2013-07-17
```

davide@davide-Aspire-5310:~$ lsmod
Module                  Size  Used by
wl                   3032548  1 
rfcomm                 38104  0 
bnep                   17791  2 
snd_hda_codec_realtek    64959  1 
bluetooth             189585  10 rfcomm,bnep
snd_hda_intel          32983  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
i915                  479235  3 
joydev                 17394  0 
parport_pc             32115  0 
coretemp               13362  0 
ppdev                  12850  0 
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
acer_wmi               27975  0 
sparse_keymap          13659  1 acer_wmi
drm_kms_helper         47459  1 i915
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
microcode              18396  0 
drm                   240443  4 i915,drm_kms_helper
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13317  1 i915
lpc_ich                16993  0 
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              181041  1 wl
psmouse                91381  0 
mac_hid                13078  0 
video                  19117  2 i915,acer_wmi
wmi                    18745  1 acer_wmi
lib80211               14041  1 wl
serio_raw              13032  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
ahci                   25621  2 
libahci                26166  1 ahci
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
tg3                   141761  0 
davide@davide-Aspire-5310:~$ iwconfig
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
davide@davide-Aspire-5310:~$ dmesg | grep b43
davide@davide-Aspire-5310:~$ rfkill list
0: acer-wireless: Wireless LAN
         Soft blocked: no
         Hard blocked: no
davide@davide-Aspire-5310:~$

```

---

### Post by praseodym on 2013-07-17
The wrong driver is still installed:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo modprobe -v b43
```

---

### Post by poccio on 2013-07-17
it's asking me a password but i haven't got any, so I went to the user settings to put on in and it asks me for a password there as well (authentication) itried the old one but it won't work? is there like a standard one?

---

### Post by praseodym on 2013-07-17
If you are the user which was set up during the installation, you are the "sudo" user. Type in your PW (no ****** are shown, you have to type 'blind')

---

### Post by poccio on 2013-07-17
right, but my accoun doesn't have a password so i just pressed enter but it says > sorry incorrect
so i'm trying to put a password in through my account manager but it asks me for another password which i don't have ?????

---

### Post by praseodym on 2013-07-17
Who installed your system? This person should know the PW of the sudo user

---

### Post by poccio on 2013-07-17
i did, since i don't have anything on the computer yet, i've decided to reinstall ubuntu to reset up the password, if you can bear with me for a bit i'll let you know how it goes. anyhow i really appreciate you helping me.:KS

---

### Post by praseodym on 2013-07-17
I also recommend not to automatically login. The commands and the installation of the firmware file are the same as above.

---

### Post by poccio on 2013-07-17
ok thanks, so I put a password on there and now it's installing. so if i've understood you correcty, i can just start where i left off (that sudo command line) or should i start from the beginning (downloading the firmware and showing you the outputs)?

---

### Post by praseodym on 2013-07-17
Start with the firmware

---

### Post by poccio on 2013-07-17
ok so i reinstalled and put in the firware, here are the outputs```

davide@davide-Aspire-5310:~$ lsmod
Module                  Size  Used by
bnep                   17791  2 
rfcomm                 38104  0 
bluetooth             189585  10 bnep,rfcomm
parport_pc             32115  0 
ppdev                  12850  0 
snd_hda_codec_realtek    64959  1 
snd_hda_intel          32983  3 
i915                  479235  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
coretemp               13362  0 
joydev                 17394  0 
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
acer_wmi               27975  0 
drm_kms_helper         47459  1 i915
snd_seq_midi           13133  0 
drm                   240443  4 i915,drm_kms_helper
psmouse                91381  0 
sparse_keymap          13659  1 acer_wmi
serio_raw              13032  0 
snd_rawmidi            25426  1 snd_seq_midi
microcode              18396  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
wmi                    18745  1 acer_wmi
snd_timer              28932  2 snd_pcm,snd_seq
wl                   3032548  1 
i2c_algo_bit           13317  1 i915
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              181041  1 wl
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14041  1 wl
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lpc_ich                16993  0 
mac_hid                13078  0 
video                  19117  2 i915,acer_wmi
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
ahci                   25621  2 
libahci                26166  1 ahci
tg3                   141761  0 
davide@davide-Aspire-5310:~$ iwconfig
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
davide@davide-Aspire-5310:~$ dmesg | grep b43
davide@davide-Aspire-5310:~$ rfkill list
0: acer-wireless: Wireless LAN
         Soft blocked: no
         Hard blocked: no
davide@davide-Aspire-5310:~$

```

can i go ahead with the rest of the instructions?

---

### Post by praseodym on 2013-07-17
Yes

---

### Post by poccio on 2013-07-17
so i put in the first line of code and then the password (finally no probls here) but then it did what it did before, basically nohing, no line like ```

davide@davide-Aspire-5310:~$
```
so i kept writing the lines of code but nothing yet, and if i try to close the terminal it says a process is still running, what now?

---

### Post by praseodym on 2013-07-17
This is Ok, the commands are finished. Alternatively, open the file manager via

```
gksudo nautilus
```
and removwe the respective files in /etc/modprobe.d/

Reboot after that and check the outputs

---

### Post by poccio on 2013-07-17
ok. there's a dkms.conf file (not broadcom-sta-dkms.conf) shold i delete that as well?

---

### Post by praseodym on 2013-07-17
No, only the three ones named above. You can try to add the new line

```
blacklist wl
```

to **blacklist.conf**. Save and reboot then

---

### Post by poccio on 2013-07-17
OMG!! thank a million man! it works!! the led thing doesn't keep blinking but only blinks once when you stroke the key, but that is all good!! man you are a genius, i really couldn't have done it without you guiding me every step of the way! i'll change the thread to solved!! again a million thanks! is there anything i can do for you (is there like reputation or positive feedback on this forum?)

---

### Post by praseodym on 2013-07-17
Errr, I dont think so ;)

Now try to uninstall the unnecessary driver (if its working):

```
sudo apt-get remove --purge bcmwl-kernel-source
```
I also recommend installing the following:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
```
and dont forget to update your system :)

---

### Post by poccio on 2013-07-17
hey i started the thread but under thread tools i don't have the option to mark it as solved (maybe because i'm a newbie?) can you do it?
also i thought my system was up to date, what should I do to update it?

---

### Post by praseodym on 2013-07-18
Start the update-manager.

For marking it solved edit the first post and the header.

---

