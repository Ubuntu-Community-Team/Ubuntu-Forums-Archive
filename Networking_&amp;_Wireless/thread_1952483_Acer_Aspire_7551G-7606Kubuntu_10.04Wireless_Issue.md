---
title: "Acer Aspire 7551G-7606/Kubuntu 10.04/Wireless Issue"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by ricomoss on 2012-04-04
I am having trouble enabling the wireless network card.  Per the instructions on how to submit this type of problem I have entered in all the relevant information below.

**1) Machine Brand and Model**
```

Acer Aspire 7551G-7606 Laptop

```

**2) Wireless Brand, Model and Wireless Chipset**
```

06:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e034
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

**3) Check Interface**
```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

**Check for modules:**  (Sorry about the long output here but I don't know what to look for on this one.)
```

Module                  Size  Used by
ppdev                   6375  0 
joydev                 11104  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279104  1 
arc4                    1473  2 
snd_hda_intel          25805  2 
snd_pcm_oss            41394  0 
snd_hda_codec          85791  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  1 snd_hda_codec
snd_pcm                87946  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 329085  0 
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              238928  1 ath9k
ath                     9723  1 ath9k
uvcvideo               62915  0 
videodev               40614  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
soundcore               8052  1 snd
psmouse                65040  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
acer_wmi               15829  0 
cfg80211              148725  3 ath9k,mac80211,ath
led_class               3764  2 ath9k,acer_wmi
edac_core              45423  0 
serio_raw               4918  0 
i2c_piix4               9639  0 
edac_mce_amd            9278  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38350  3 
tg3                   122382  0

```

**5) Kernel Boot Messages**
Couldn't find any information on wlan or wireless.  If you can tell me what to look for I'll put it here but this list was entirely too long.

**Network Configuration**
```

  *-network DISABLED
       description: Wireless interface
       product: AR9287 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:90:e0:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0200000-d020ffff

```

**7) Scan For Networks:**
```

wlan0     Failed to read scan data : Network is down

```

**8) Ubuntu Version:**
```

Description:    Ubuntu 10.04.4 LTS

```

**9) Kernel/Architecture:**
```

2.6.32-40-generic x86_64

```

**Restarting The Network:**
```

 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
                                                                                             [ OK ]

```


Below are some additional commands.
```

ricomoss@keaton:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        EC:55:F9:90:E0:21

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

and...

```

ricomoss@keaton:~$ sudo rfkill list
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

It appears to be *blocked*.

Any suggestions?

---

### Post by chili555 on 2012-04-04
Please try:```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
```Did your wireless spring to life? If so, let's blacklist acer-wmi:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```If not, post back and we'll dig deeper.

---

### Post by ricomoss on 2012-04-04
I ran both those commands.  What am I looking for now?

There doesn't seem to be a listing for wireless anymore.

*ifconfig* returns no wireless info.

Now there is only the phy0.
```

ricomoss@keaton:~$ sudo rfkill list
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

I have not yet run the blacklist command.  Should I?

---

### Post by chili555 on 2012-04-04
> Hard blocked: yesThat suggests the switch or key combination is switched to off. Can you toggle it back on?

Let's not run the blacklist yet until we are confident it's either the switch or the acer-wmi module...or both.

Off to lunch with Mrs. Chili. See you a bit later.

---

### Post by ricomoss on 2012-04-04
> **chili555 said:**
> That suggests the switch or key combination is switched to off. Can you toggle it back on?

Let's not run the blacklist yet until we are confident it's either the switch or the acer-wmi module...or both.

Off to lunch with Mrs. Chili. See you a bit later.

Actually, I went ahead with the blacklist before I read this post.  After a restart or two it worked!

Thank you soooo much!!!

---

