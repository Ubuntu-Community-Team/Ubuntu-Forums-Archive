---
title: "Webcam support- Options that are permanent."
date: 2009-01-22
forum: Multimedia Software
---

### Post by Maximo7274 on 2009-01-22
I have a HP mini 1000, and it has Ubuntu on it. Unfourtunatly, its webcam is VERY dark, but I did some research and I figured out that all I have to do is get windows movie maker and change the settings for the webcam so that it is much brighter.

Is there a way to get windows movie maker working with wine?  Or does anyone know of a program that would make the webcam brighter for all the applications that use it??

Thanks,

---

### Post by spiderbatdad on 2009-01-22
you might be able to edit /etc/modprobe.d/options appropriately for the driver your webcam uses. an example with the gspca driver here: 
[http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)

---

### Post by Maximo7274 on 2009-01-23
That seems like it would do the trick, except I have no idea how to do it, as I have only had Ubuntu on my laptop for a month....  So any help on exactly what to do would be helpful!, thanks

---

### Post by spiderbatdad on 2009-01-23
Open terminal. Enter command: lsmod  (that's a small L)
copy/paste the output back here. Paste between code tags by clicking the # symbol of the editor at the top of this window.

---

### Post by Maximo7274 on 2009-01-23
```
byron@byron-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
michael_mic            10496  4 
arc4                    9984  4 
ecb                    10880  4 
crypto_blkcipher       25476  1 ecb
af_packet              25728  4 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
container              11520  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
evdev                  17696  12 
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_seq_dummy          10884  0 
serio_raw              13444  0 
psmouse                45200  0 
video                  25104  0 
output                 11008  1 video
battery                18436  0 
ac                     12292  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ieee80211_crypt_tkip    17024  0 
wmi                    14504  0 
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  1 
libusual               27156  1 usb_storage
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24580  2 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_generic            12932  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
ehci_hcd               43276  0 
uhci_hcd               30736  0 
scsi_mod              155212  4 usb_storage,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  7 uvcvideo,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

Thats what it gave me, what exactly does it mean???

THanks

---

### Post by spiderbatdad on 2009-01-23
This is a list of modules that are in use on your system...similar to "drivers."
I have just tried the following, and honestly noticed no difference, but I do not have the issue you have, so this may work for you. You may have to experiment with the values if you see some improvement, but not just what you want.
In my case, after editing the file, I unplug and re-plug my cam. I don't believe you have that option...you're cam is built-in?
So I believe you can unload and reload the module...and it will find your cam...we can test this...if it doesn't you will need to reboot. Ok here we go. Everything in code tags, you will enter into your terminal.

Edit the file /etc/modprobe.d/options.
```
sudo nano /etc/modprobe.d/options
```
Use arrow key and go to end of file. At the end of the file type in or paste the following block of text.
```
options v4l2 gamma=4
options v4l2 GRed=290
options v4l2 GGreen=310
options v4l2 GBlue=315

```
Hit ctrl+o to save, and then hit enter to confirm writing to the file. Then ctrl+x to exit.
Now unload and reload the module...first one command, then the second.
```
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo
```

Now look at the end of the dmesg log to see if you cam was redetected:
```
dmesg | tail
```

Launch your webcam application and look for improvement. Good luck.

---

### Post by Maximo7274 on 2009-01-23
I think it got a tiny bit better....   I am not possitive, but it seems like it, as I can see the outlines of my face now :-D.  I will try to make it brighter by changing the gamma....

I will see if it actually is doing something, once I test out making the gamma 6.

[Edit] DOes this mean it detects my webcam-
byron@byron-laptop:~$ dmesg | tail
[ 1014.768146] usb 2-2: new low speed USB device using uhci_hcd and address 3
[ 1014.949896] usb 2-2: configuration #1 chosen from 1 choice
[ 1014.974512] input: Microsoft Microsoft 3-Button Mouse with IntelliEye? as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input12
[ 1015.017744] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye?] on usb-0000:00:1d.0-2
[ 1237.074989] usbcore: deregistering interface driver uvcvideo
[ 1245.386342] Linux video capture interface: v2.00
[ 1245.420842] uvcvideo: Found UVC 1.00 device Webcam-101 (10f1:1a08)
[ 1245.439423] input: Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input13
[ 1245.448713] usbcore: registered new interface driver uvcvideo
[ 1245.448763] USB Video Class driver (v0.1.0)


I think it does, but I have no idea :-P

---

### Post by spiderbatdad on 2009-01-23
yup.
```
[ 1245.420842] uvcvideo: Found UVC 1.00 device Webcam-101 (10f1:1a0
[ 1245.439423] input: Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input13
```

---

### Post by Maximo7274 on 2009-01-24
I think it is working, but I am not positive, so I have a couple of questions.
1.) what is the highest I can put the gamma setting to?
2.) how would I amp up the contrast, so that it is at max?

Thanks so much for helping me so far :-D

[Edit] YES!!! I amped up the gamma to 50, and guess what?  I CAN SEE MYSELF!!!  You rule!  Thanks so much for all the help- this is awesome!!!!

---

