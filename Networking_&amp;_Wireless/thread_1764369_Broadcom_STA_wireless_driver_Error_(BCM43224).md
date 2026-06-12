---
title: "Broadcom STA wireless driver Error (BCM43224)"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by alapoo on 2011-05-21
I just installed Ubuntu on my computer yesterday (with no prior exposure to Unix systems) as a dual OS.  I've been having trouble trying to get my wireless internet to work.

I have been able to activate the Broadcom STA wireless driver suggested under Additional Drivers, however at the bottom it states: This driver is activated but not currently in use.



I'm not sure what this all means but maybe it helps:

*lsmod*
```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
uvcvideo               66851  0 
psmouse                59039  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
fglrx                2434640  161 
serio_raw              12990  0 
videodev               75143  1 uvcvideo
i7core_edac            23248  0 
edac_core              42881  3 i7core_edac
video                  18951  0 
ssb                    45942  0 
lib80211               14570  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
ahci                   21591  2 
e1000e                138627  0 
libahci                25548  1 ahci
crc_itu_t              12627  1 firewire_core

```

*lsusb*
```

Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

```

*lspci | grep Network*
```

06:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)

```

**Update**

I solved this issue by following the few steps here: [http://ubuntuforums.org/showthread.php?t=1745437](http://ubuntuforums.org/showthread.php?t=1745437)
Which removed the device from being blacklisted.

---

### Post by alapoo on 2011-05-21
In the Synaptic Package Manager bcmwl-kernal-source is a broken package. When I try to reinstall or remove it, it fails because it needs the internet to perform both of those operations.

---

### Post by alapoo on 2011-05-21
I downloaded both of the .deb files that the Package Manager was trying to access through the internet.  I transfered them over, but I'm not quite sure what to do now.

---

### Post by alapoo on 2011-05-21
As an additional hurdle I keep getting an error when I try to install or uninstall anything that says:
 
*Items cannot be installed or removed until the package catalog is repaired.  Do you want to repair it now?*
*Once Update Manager has finished the repairs, you can close it and return to the store.*
 
When I hit repair it says:
 
*Failed to download package files*
*Check your Internet connection*
 
Of course, again, I dont have the internet because that's the issue at hand.

---

### Post by meloade on 2011-05-21
Do you not have an Ethernet connection you can use? The wireless drivers should not be stopping you from using these. On a different note... Why didn't you just use the recommended drivers in (System>Admin>Additional Drivers) ?

---

### Post by alapoo on 2011-05-21
haha I can't believe I didn't think too hook up an ethernet connection. #-o
 
I have been trying to use the recommended drivers from Additional Drivers.  When I click activate it gives me the first error I described and references the jockey.log

---

### Post by meloade on 2011-05-21
[QUOTE=alapoo;10846617]haha I can't believe I didn't think too hook up an ethernet connection. #-o
 
I had a good laugh there. Have you tried reinstalling the drivers you have now that you have an internet connection?

---

### Post by alapoo on 2011-05-21
I was able to activate the Broadcom STA wireless driver via Additional drivers with my ethernet connection.  However, I tried disconnecting the ethernet cable and testing to see if I could pickup any wireless signals and I couldn't.  Under additional drivers it now says:

*This driver is activated but not currently in use.*

I'm going to try the wireless again and see what that does.

---

### Post by meloade on 2011-05-21
> **alapoo said:**
> I was able to activate the Broadcom STA wireless driver via Additional drivers with my ethernet connection.  However, I tried disconnecting the ethernet cable and testing to see if I could pickup any wireless signals and I couldn't.  Under additional drivers it now says:

*This driver is activated but not currently in use.*

I'm going to try the wireless again and see what that does.

Try restarting the computer.

---

### Post by alapoo on 2011-05-21
I did.  A few times.  Still nothing.

---

### Post by alapoo on 2011-05-21
I'm getting these errors a lot:

*firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1*

---

### Post by alapoo on 2011-05-22
I have no idea how to fix this.  Any help would be appreciated.  

I was able to activate the Broadcom STA wireless driver suggested under Additional Drivers.  It has a green light next to it, but it now says:

*This driver is activated but not currently in use.*

How do I put the driver to use?

---

### Post by MKdx on 2011-05-22
Please post the output of this command:```
lsmod
```

---

### Post by alapoo on 2011-05-22
```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
uvcvideo               66851  0 
psmouse                59039  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
fglrx                2434640  102 
serio_raw              12990  0 
videodev               75143  1 uvcvideo
i7core_edac            23248  0 
edac_core              42881  3 i7core_edac
video                  18951  0 
ssb                    45942  0 
lib80211               14570  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
ahci                   21591  2 
e1000e                138627  0 
libahci                25548  1 ahci
crc_itu_t              12627  1 firewire_core

```

---

### Post by alapoo on 2011-05-22
Are there any other commands that might help?  Sorry, I'm new to Unix systems.

---

### Post by alapoo on 2011-05-22
I solved this issue by following the few steps here: [http://ubuntuforums.org/showthread.php?t=1745437](http://ubuntuforums.org/showthread.php?t=1745437)
Which removed the device from being blacklisted.

---

