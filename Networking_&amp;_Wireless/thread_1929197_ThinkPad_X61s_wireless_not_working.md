---
title: "ThinkPad X61s wireless not working"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by 4muumia on 2012-02-21
Tried searching for a solution but found none:
- ThinkPad X61s /w Intel PRO 4965 AG on board
 - also tried /w:
   - D-Link DWL-G122, RALink 802.11 bg, also couple of A-Link and Gigabyte usb adapts.
 Favourite distro would be ubuntu 11.10, have also tried 10.04 lts and Fedora 16, with the same result on all:
- System doesnt recognize onboard wlan at all. If i insert a usb adapter, system finds both but says they are unavailable. Wired connection obviously works ok. I've installed drivers for the usb adapters (on all aforementioned distros) but the result is the same as described above.

Ideas? Im willing to dow&#324;grade to earlier versions or switch distros. The machine was shipped with Vista that was still there as i got it. After the initial boot-up that lasted whopping 12 minutes (:D) i decided that i'd rather install os2 or xenix from floppys than stick with vista...

-Jukka

---

### Post by praseodym on 2012-02-21
Tried to reset the BIOS? Check also:

```
lsmod
rfkill list
iwconfig
lsusb #for the stick
```

---

### Post by 4muumia on 2012-02-22
Tried reset, no luck.

>>

maija@maija-ThinkPad-X61s:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_analog    75090  1 
arc4                   12473  2 
ppdev                  12849  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
pcmcia                 39822  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
psmouse                73673  0 
thinkpad_acpi          73942  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvram                  14029  1 thinkpad_acpi
i915                  509519  3 
iwl4965               121795  0 
iwl_legacy             71499  1 iwl4965
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
mac80211              393421  2 iwl4965,iwl_legacy
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32114  1 
tpm_tis                14002  0 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
cfg80211              172427  3 iwl4965,iwl_legacy,mac80211
snd                    55902  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
mei                    36466  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   21634  2 
libahci                25727  1 ahci
e1000e                139814  0 
maija@maija-ThinkPad-X61s:~$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
maija@maija-ThinkPad-X61s:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
maija@maija-ThinkPad-X61s:~$ lsusb #for the stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 17ef:1000 Lenovo 
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

---

### Post by praseodym on 2012-02-22
The card is off. Button/switch/keys/key combination? Also try

> sudo rfkill unblock all

---

### Post by 4muumia on 2012-02-23
keys do nothing, i also disabled wireless from bios > enabled it again > nothing. rfkill does also nothing.

whats weird is that on networking wireless isnt even available without an external wlan card/usb. if card/usb is present, networking shows the types but they are grayed out so > its not possible to turn them on.

hardware broken?

---

### Post by kurt18947 on 2012-02-23
I have an X61 tablet convertible and the Intel 4965 works perfectly upon install or from a live session.  There are two slide switches on the front.  One is pretty obvious, it unlocks the screen.  The second one is not obvious at all;  I had to turn the machine over to see it.  That's the wireless switch.  The command 'rfkill list' may indicate the switch state.  It appears on my machine that <Fn>+F5 also enables/disables wireless.

---

### Post by praseodym on 2012-02-23
Check the key combinations Fn+F2, Fn+F5 (as kurt18947 mentioned) and Fn+F9. Also try to press the button permanently or repeatedly during boot-up

---

### Post by 4muumia on 2012-02-24
oh boy, i feel like i qualify for an apple... :KS
this switch on bottom did it. i had the machine sitting on a dock all the time.
fn keys dont work but hey...

thanks!!!

---

### Post by kurt18947 on 2012-02-24
> **4muumia said:**
> oh boy, i feel like i qualify for an apple... :KS
this switch on bottom did it. i had the machine sitting on a dock all the time.
fn keys dont work but hey...

thanks!!!

I'm glad it works.  That little thing is **not** obvious, especially sitting in a dock.

---

