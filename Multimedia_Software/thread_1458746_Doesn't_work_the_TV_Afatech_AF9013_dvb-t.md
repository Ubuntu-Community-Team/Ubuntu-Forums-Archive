---
title: "Doesn't work the TV Afatech AF9013 dvb-t"
date: 2010-04-20
forum: Multimedia Software
---

### Post by Dark_Jack on 2010-04-20
Hello to all!

I bought a **Conceptronic USB DVB-T Digital TV Receiver** but I can not get to work on my **Ubuntu 9.10 [COLOR=Red]64 bits[/COLOR]**

Apparently, my ubuntu is detected:

```
antonio@antonio-desktop:~$ dmesg | grep -i dvb
[   11.738849] usbcore: registered new interface driver dvb_usb_af9015
``````
antonio@antonio-desktop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 1b80:d393 Afatech** 
Bus 001 Device 002: ID 0951:1624 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
antonio@antonio-desktop:~$ dmesg|tail
[   13.592518] hda-intel: Codec #3 probe error; disabling it...
[   13.746597] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   13.746879] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   14.254537] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   14.254540] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   14.254960] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.540788] usplash:381 freeing invalid memtype ffffffffcf000000-ffffffffcfe00000
[   24.590007] eth0: no IPv6 routers present
[   62.010018] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   62.171204] usb 1-2: configuration #1 chosen from 1 choice
```I have installed the "**linux-firmware-nonfree**" and "**dvb-usb-af9015.fw**"

[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/")

The TDT is **Conceptronic** brand and product code is **CTVDIGRCU**

**Errores:**
 [URL="http://img408.imageshack.us/img408/6602/pantallazojy.png"]
[/URL]
[http://img408.imageshack.us/img408/6602/pantallazojy.png](http://img408.imageshack.us/img408/6602/pantallazojy.png)
 [http://img408.imageshack.us/img408/7796/pantallazo4ud.png](http://img408.imageshack.us/img408/7796/pantallazo4ud.png)

**PD:** Obviously, the device is connected even though the pictures say otherwise ...

```
antonio@antonio-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetadp              6528  0 
vboxnetflt             14288  0 
vboxdrv              1778380  2 vboxnetadp,vboxnetflt
snd_hda_codec_realtek   277860  1 
dvb_usb_af9015         32964  0 
dvb_usb                19276  1 dvb_usb_af9015
dvb_core              104528  1 dvb_usb
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     11908  0 
iptable_filter          3872  0 
parport                40528  2 ppdev,lp
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
nvidia              10316904  36 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
usb_storage            66304  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
e1000e                138544  0 
intel_agp              33040  0 
antonio@antonio-desktop:~$
```Anybody can help me, please? :(

---

### Post by Dark_Jack on 2010-04-20
nothing? :(

---

### Post by Jared Norris on 2010-06-15
I guess this is a bit of a *BUMP* because I have the exact same issue but with a differently branded USB Tv Tuner.

I googled the lsusb device ID and found this post and was all excited I could have my problems solved and then realised you were just experiencing the same issues.

Has anyone come across this and found a solution?

---

### Post by Vide on 2010-06-28
Did you try to wait a little and to make sure you have good signal?
I mean, I have an Afatech AF9013 DVB-T (branded as AverMedia AVerTV Volar Black HD (A850)) and I came here cause it was no working with similiar error. But suddenly after waiting some minutes the blue led of my USB receiver blinked and then the scan in Kaffeine started to work

---

### Post by Jared Norris on 2010-06-28
Vide,

Thanks for the response. I actually found out that the tv tuner I had was a realtek chip reporting as an afatech chip (no idea how?) and so as soon as I installed the right firmware it worked as it should.

Dark Jack,

I had to check with the manufacturer what chipset was being used to find out it wasn't the one reported. If you aren't sure it's an afatech maybe just shoot them an email to ask.

---

### Post by Dark_Jack on 2010-08-28
My **DVB-T** is the:

[http://www.conceptronic.net/site/DesktopDefault.aspx?tabindex=1&tabid=242&Cid=40&gid=4050&Pid=CTVDIGDUAL](http://www.conceptronic.net/site/DesktopDefault.aspx?tabindex=1&tabid=242&Cid=40&gid=4050&Pid=CTVDIGDUAL)

---

### Post by Jose Catre-Vandis on 2010-08-28
Check out this thread, might help you?

[http://ubuntuforums.org/showthread.php?t=606487](http://ubuntuforums.org/showthread.php?t=606487)

If it helps I have what appears to be a very similar card which works OK (sorry), however my Device Id is slightly different to yours:
```
YOURS: Bus 001 Device 003: ID 1b80:d393 Afatech 
MINE: Bus 001 Device 002: ID 1b80:e395 Afatech
```

---

### Post by Dark_Jack on 2010-08-30
Does this prove?

[http://ubuntuforums.org/showpost.php?p=9712937&postcount=126](http://ubuntuforums.org/showpost.php?p=9712937&postcount=126)

:confused:

---

### Post by jmore9 on 2010-08-30
Here is a great site with a lot of info on linuxtv :

[http://www.linuxtv.org/](http://www.linuxtv.org/)

Go there find out if your hardware is supported and see what it says about it.

Here is list of supported devices :

[http://www.linuxtv.org/wiki/index.php/ATSC_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_Devices)

---

