---
title: "Web cam set up"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by adwallum on 2008-04-17
Hi

I've had a look at the posts. I have tried EasyCam2, Camorama, Skype and Camera Monitor

EasyCam2 tells me I have the following:-
> Bus 003 Device 005: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
but throws an error in French when I proceed.

Camorama throws an error message:-
> Could not connect to video device (/dev/video0) Please check connection.

lsusb says:
> Bus 003 Device 005: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
 
so I know the web cam is connected to the system, hardware wise.

When I try to test video in Skype, I get mush for video but it does recognise a device in video setup similar to that reported .

Camera Monitor used to come on and off with starting/stopping Skype, since trying EasyCam2 it no longer responds however.

Camera works fine in XP.

Can anybody offer specific help please?  I have trawled a lot through the threads already.

---

### Post by sisco311 on 2008-04-17
post the output of the
```
lsmod
```and
```
ls -al /dev/video*
```and
```
cat /etc/issue
```commands

---

### Post by abhay2101 on 2008-04-17
try in kopete or if  it throws error like

QPixmap::convertFromImage: Cannot convert a null image
QPixmap::convertFromImage: Cannot convert a null image
QPixmap::convertFromImage: Cannot convert a null image
QPixmap::convertFromImage: Cannot convert a null image


in command line then you can upgrade the kernel to 2.6.24-15 in that it will work fine.

your kernel is lacking some drivers....

latest one is having good support..

---

### Post by adwallum on 2008-04-17
lsmod gives:
> Module                  Size  Used by
ipv6                  267780  8 
i915                   32512  2 
drm                    82580  3 i915
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
gspca                 643920  0 
zc0301                 52356  0 
evdev                  13056  3 
compat_ioctl32          2304  1 zc0301
videodev               29440  2 gspca,zc0301
v4l1_compat            15492  1 videodev
v4l2_common            18304  2 zc0301,videodev
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
usbhid                 31872  0 
hid                    38784  1 usbhid
usblp                  15872  0 
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
serio_raw               7940  0 
snd_seq_dummy           4868  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
psmouse                40336  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_i810                5636  0 
i2c_algo_bit            7300  1 i2c_i810
i2c_core               24832  2 i2c_i810,i2c_algo_bit
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usb_storage            73664  0 
libusual               19108  1 usb_storage
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
ata_piix               19588  2 
floppy                 59588  0 
pata_acpi               8320  0 
e100                   37388  0 
mii                     6400  1 e100
libata                159344  3 ata_generic,ata_piix,pata_acpi
ehci_hcd               37900  0 
uhci_hcd               27024  0 
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
usbcore               146028  9 gspca,zc0301,usbhid,usblp,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

ls -al /dev/video* gives:
> lrwxrwxrwx 1 root root     11 2008-04-17 11:15 /dev/video -> /dev/video0
crw-rw-rw- 1 root video 81, 0 2008-04-17 10:25 /dev/video0
crw-r--r-- 1 root root  81, 1 2008-04-17 11:15 /dev/video1

cat /etc/issue gives:
> Ubuntu 8.04 \n \l


Thanks for the quick response

---

### Post by sisco311 on 2008-04-17
unplug the web cam, then:
```
sudo modprobe -r zc0301
sudo modprobe -r gspca
sudo modprobe gspca
```plug in the cam and test it with camorama.

---

### Post by adwallum on 2008-04-17
Camorama got a little further

[IMG]file:///home/denise/Desktop/Webcamsetup01.png[/IMG]
then hung. When trying to close it down I received an error message.
[IMG]file:///home/denise/Desktop/webcam02.png[/IMG]

Camera Monitor is now working. Test in Skype now presents an uniform black screen (was multicoloured mush before)

I am trying to send screenshots but not sure if I have added them properly.

---

### Post by adwallum on 2008-04-17
screenshots added...hopefully

---

### Post by adwallum on 2008-04-20
I have downloaded gspcav1-20071224 from [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html).

Is this the latest driver? Is it already incorporated in Ubuntu's gspca package?

Any further help would be welcome. I'm still stuck with a non functioning web cam (i.e. does not work in Ubuntu due to not finding driver or even determine if one exists - functions in XP with XP drivers).

I solved the problem by buying a cheap Chinese web cam that was driverless off eBay. Just plugged it in. Brilliant! Cheese and Skype can see it, Camorama can't so not the perfect solution for everybody I guess.

---

