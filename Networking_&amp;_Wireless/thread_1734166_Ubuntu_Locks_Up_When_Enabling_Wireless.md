---
title: "Ubuntu Locks Up When Enabling Wireless"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by vitae_drinker on 2011-04-19
Hey, I've been having an issue for the last day or so. I have an HP Pavilion dv8000 running 10.10. Whenever I boot with the Wireless activated, it will lock about 3-4 seconds into the log-in screen (I'm guessing when it connects to my router). If I have the wireless deactivated (like now), I am able to use the ethernet connection, or (like now) use my phone to tether internet. But, as soon as I click the wireless to active, locks up. The wireless activity light flashes, but that's all.

I'm pretty good about updating whenever I use my laptop, but I think something in the most recent update may have broken my wireless connection. If someone more knowledgeable than me would like to help, I would greatly appreciate it.

---

### Post by MooPi on 2011-04-20
You'll need to give us more details. Your wireless device for starts. From terminal...
```
lsmod
iwconfig
```
That should give us a place to start.

---

### Post by vitae_drinker on 2011-04-20
lsmod generated:

```
Module                  Size  Used by
rndis_host              6248  0 
cdc_ether               4052  1 rndis_host
usbnet                 17376  2 rndis_host,cdc_ether
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
nvidia               9329739  55 
snd_hda_codec_conexant    30003  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8767  0 
arc4                    1165  2 
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  0 
pcmcia                 35973  0 
nls_cp437               4931  1 
intel_agp              26566  0 
iwl3945                85550  0 
agpgart                32011  2 nvidia,intel_agp
psmouse                59033  0 
tifm_7xx1               3766  0 
output                  1883  1 video
lp                      7342  0 
serio_raw               4022  0 
tifm_core               6089  1 tifm_7xx1
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
iwlcore               127415  1 iwl3945
cifs                  241548  2 
mac80211              231959  2 iwl3945,iwlcore
cfg80211              144694  3 iwl3945,iwlcore,mac80211
soundcore                880  1 snd
hp_wmi                  5223  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40204  0 
sdhci_pci               6633  0 
ahci                   19198  3 
firewire_ohci          21234  0 
e100                   30356  0 
firewire_core          46643  1 firewire_ohci
sdhci                  15922  1 sdhci_pci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  2 usbnet,e100
libahci                21728  1 ahci

```


iwconfig generated:


```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
usb0      no wireless extensions.

```

Hope this helps.

---

### Post by vitae_drinker on 2011-04-20
Okay, I deleted my remembered wireless networks, restarted my wireless router, and was able to reconnect to it, briefly. But, as soon as my laptop hibernated, and brought it back up, it locked up again.

Now, I can restart my wireless as long as I don't try to connect my home network. I was able to hook up to my Nexus One when it was USB tethered, and when acting as a Wireless hub.

---

### Post by vitae_drinker on 2011-04-22
No help?

---

### Post by mark.0 on 2011-05-01
I have the same problem. I just upgraded to ubutnu 11 last night and have experienced this since. Works fine until I enable wireless, then the everything freezes.  I can't post my lsmod because, well, I have no internet access from that machine now to post it :(

Running a HP Mini 210, which requires restricted drivers for the wireless card, which I presume has something to do with my problem... 

I've also experienced several other possibly related problems since the upgrade. Ubuntu was freezing at the splash screen on boot. changing grub to xforcevesa nomodeset acpi=off without quiet splash allowed me to finally boot. I then received a prompt from ubuntu telling me that I didn't have the proper components to load unity or something and told me "classic" would be loaded. The old 10.4-like interface loaded. At this point I was suspicious that my card was the problem with booting, so I disabled wireless here and rebooted. Upon boot, it allowed the new ubuntu 11 interface to load this time, so I guess the wireless was the problem. But now, when I try to enable wireless, everything freezes.

O yeah, and now if I try to edit grub during boot and ctrl-x to boot with changes, I get "magic alloc is broken". WTF. I'm getting pretty frustrated here and with I'd waited to upgrade. Can anyone help????


EDIT: BTW, the restricted driver for the wireless card in question is "Broadcom STA wireless driver". I decided to try going to System Settings > Additional drivers and disable the driver and see what happens when I re-enable wireless: same symptoms. I then re-enabled the restricted driver, which appeared to re-install it, so I tried to try again: same symptoms.

EDIT AGAIN: My problem is resolved, however, I unfortunately cannot accurately say what fixed the problem. I retried enabling and re-enabling the restricted driver with a clean reboot. At some point, my "enable wireless" became disabled from the networks menu. So then, I looked at my BIOS and enabled the "enable internal network yadayada something at boot". I'm not sure if this got changed, or if it had always been disabled. Regardless, when I booted next time, "Enable Wireless" was finally available, so I crossed my fingers and enabled it. Thankfully nothing froze up and I can not finally use my wireless.... Sorry I don't have a clearer description of what I did and wasn't more methodical here, but I was getting frustrated :) .

---

