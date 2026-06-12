---
title: "Can't change wireless settings"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by blindmeplease on 2010-09-11
I got this Acer Revo 3610 nettop about a week ago. I got it to use as an htpc, and decide to do an install of xbmc live on it. Now, I'm completely new to linux, so its been a learning experience for me. I have everything set up the way I want it at this point, but I'm stuck on trying to configure the wireless.

I'm not sure where I should start troubleshooting this thing, but something about this seems off to me.

```
xbmc@XBMCLive:~$ sudo -s
root@XBMCLive:~# iwconfig ra0 mode Managed
root@XBMCLive:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:eek:ff   Fragment thr:eek:ff
          Encryption key:eek:ff
          Link Quality=10/100  Signal level:0 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```That command that should let me change the wireless mode doesn't seem to do anything.

```

root@XBMCLive:~# iwconfig ra0 essid "linksys"
root@XBMCLive:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0F:66:0C:45:B3
          Bit Rate=24 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:-43 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```The same goes for setting the essid, but what does stand out to me is that the link quality and signal level both change when I try to set it.

Anyway, here is a bit more information that I am hoping is of use.

```

lshw -C network

  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: ra0
       version: 00
       serial: 70:f1:a1:9f:54:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.3 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:febf0000-febfffff

nm-tool

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        70:F1:A1:9F:54:14

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
    Airport Network: Infra, 90:84:0D:D7:2E:73, Freq 2462 MHz, Rate 0 Mb/s, Strength 89
    linksys:         Infra, 00:0F:66:0C:45:B3, Freq 2437 MHz, Rate 54 Mb/s, Strength 100

```If I can add anything else that would be of help, please let me know.

---

### Post by MaindotC on 2010-09-11
Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  I'm not familiar with xbmc but in Ubuntu there is an icon in the top right that should show an arrow pointing up and an arrow pointing down.  It's an applet that controls the network manager.  Do you have an applet that looks like that?  You can click on it and it should show the wireless networks and let you select them.

---

### Post by blindmeplease on 2010-09-11
The way this xbmc install works is, I do all of my configuration in the terminal. So no nice gui to get me through this.

---

### Post by MaindotC on 2010-09-11
Fantastic because that's exactly how the guide is written!  Looks like you're all set.  Let us know if you can't follow the guide and precisely at what point you are having difficulty.

---

### Post by blindmeplease on 2010-09-11
So after looking things over some more, I'm seeing

driver=RALINK WLAN

in lshw -C network. Now, should that also appear when I run lsmod?

```
Module                  Size  Used by
snd_hda_codec_nvhdmi     4828  1
snd_hda_codec_realtek   203328  1
snd_hda_intel          26920  3
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
psmouse                56500  0
nvidia              10212256  38
dm_crypt               12928  0
serio_raw               5280  0
lp                      8964  0
joydev                 10272  0
i2c_nforce2             6784  0
shpchp                 32272  0
lirc_mceusb            15296  1
parport                35340  1 lp
agpgart                34988  1 nvidia
rt3090sta             812564  1
led_class               4096  0
lirc_dev               10804  3 lirc_mceusb
usbhid                 38208  0
forcedeth              54152  0


```If that is the case, maybe that is the problem I'm having.

EDIT: Looking it over again, rt3090sta is loaded, and that is my network card. But that isn't what is listed as the driver for that adapter in lshw. So am I seeing something that I need to make a change to here, or is RALINK WLAN referring to something in the module rt3090sta? Or should the driver listed be named exactly the same as one of the listed modules?

---

### Post by MaindotC on 2010-09-12
You'll need to research this matter further because I'm having difficulty finding decent documentation to describe precisely which driver you should have installed for which wireless card.  According to your lshw output, you have a RT3090 Wireless 802.11n 1T/1R PCIe.  [This appears to be the support page](http://www.ralinktech.com/support.php?s=2) but I can't seem to find anything that correctly identifies the RT3090 or if you need that firmware file at the bottom of the page.

In any event, adding drivers to your machine usually won't break anything - if you load the improper driver associated with a hardware device it simply will not function properly.  So, I downloaded the source from the ralink site, made/installed it using the following commands (dunno if you're familiar with compiling/installing):```
sudo make
sudo make install
modprobe -l | grep rt3090

```and it successfully returned ```
/lib/modules/2.6.24-28-generic/kernel/drivers/net/wireless/rt3090sta.ko
``` (.ko are driver files). I'm using 8.04 so my kernel version may appear differently than yours.  I also checked the [following google results](http://is.gd/f6BF5) and [these too](http://is.gd/f6BIV).  [This thread](http://www.linuxquestions.org/questions/linux-hardware-18/wireless-network-card-not-detected-by-ubuntu-751100/) talks about removing and blacklisting any conflicting drivers and loading rt3090.  Try and find a support IRC channel for further help with ralink drivers.  I would but I'm going to bed.

---

### Post by blindmeplease on 2010-09-12
Thanks. That got it working, now I'm just trying to figure out how to get the interface to configure and pick up an ip at boot. Right now I can manually configure it each time it boots up and connect to the internet. I'm under the impression that it should be a matter of configuring /etc/network/interfaces. Someone tell me if I'm wrong.

---

### Post by MaindotC on 2010-09-12
If you have NetworkManager installed - the little icon in the top right that lets you select networks - then that will take precedence over your interfaces file.  I had to remove NetworkManager because I had a problem with it and couldn't figure out what it was so I just removed it and then the interfaces file takes over.  I don't have a 10.04 machine that uses wireless but you should look through the NetworkManager settings to see if you can edit properties for each network.  There should be something like "connect to this automatically".

Also check out [these results](http://is.gd/f6Lgr) especially the UF section.

---

