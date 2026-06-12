---
title: "Help with Pixart usb webcam"
date: 2006-05-05
forum: Multimedia &amp; Video
---

### Post by poul33 on 2006-05-05
Hello.  I am new to this.  My friend Elliot has introduced me and is trying to help me out.  I am not a technician, so I was wondering if anyone could help me finish setting up my USB webcam.

We installed easycam and it successfully detected and installed the correct driver.  However, when we run camorama to test it, an error appears:

Could not connect to video device (/dev/video0).  Please check connection.

So it looks like the driver installed, but camorama (and other programs like gnomemeeting) do not know where to look for the camora.

Here is lsusb:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 093a:2468 Pixart Imaging, Inc.
Bus 001 Device 001: ID 0000:0000

lsmod:
Module                  Size  Used by
ipv6                  217408  6
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
spca5xx               610224  0
videodev                9344  1 spca5xx
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
i2c_sis96x              5252  0
i2c_core               19728  2 i2c_acpi_ec,i2c_sis96x
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
sis_agp                 8452  1
agpgart                32328  1 sis_agp
tsdev                   7616  0
evdev                   9088  0
piix                    9476  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sis900                 19456  0
mii                     5248  1 sis900
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  4 spca5xx,ehci_hcd,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
sis5513                14472  1
ide_core              125268  5 piix,ide_cd,ide_disk,ide_generic,sis5513
unix                   24624  637
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon



Any help is very appreciated!  Thanks in advance.

Poul

---

### Post by louis_nichols on 2006-05-05
[this thread]("http://ubuntuforums.org/showthread.php?t=75284") might be what you need.

The problem is slightly different from the one most encounter, but the solution could be the same. Your lsmod does show spca5xx loaded, so the probability of this is high, I'd say.

---

### Post by poul33 on 2006-05-07
Thanks, Louis.  We had already seen Arnieboy's post, but still no luck.  The driver is already installed, it's just that the programs do not know where to look for the camera.

Just for fun, uname reveals the following:
2.6.12-10-386

There appears to be no /dev/video entries or anything similar under /dev/.

Is there any other info we can provide to help solve this problem?

Thanks,
Poul

---

### Post by louis_nichols on 2006-05-07
Take a look at [spca5xx's home page]("http://mxhaard.free.fr/spca5xx.html") see if your exact model is in the compatibility list. Otherwise, perhaps we should look for another driver. I think this is where we should start.

---

### Post by jamespi on 2006-05-08
how did you install the drivers in the first place? I tried to find this easycam thing  on the web and in synaptic but to no avail. 

I did sudo modprobe spca5xx to get the module to load, presumably you guys did something else. The light on the top of my webcam has not come on. I have a Q-Tec Webcam100 which is listed as compatible on the chart for spca5xx.

The light on top of my cam is not on, and i get the same error from camorama as you do.

---

### Post by poul33 on 2006-05-08
Here's the easycam site:
[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

We came accross this: [thread]("http://www.ubuntuforums.org/archive/index.php/t-76863.html") that said the driver was faulty "in Breezy" and pointed back to Arnieboy's [post]("http://www.ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx") with step-by-step instructions to install the driver.

We're going to try Arnieboy's way and see if that works.

Good luck!

---

### Post by louis_nichols on 2006-05-09
[QUOTE=poul33]Here's the easycam site:
[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

We came accross this: [thread]("http://www.ubuntuforums.org/archive/index.php/t-76863.html") that said the driver was faulty "in Breezy" and pointed back to Arnieboy's [post]("http://www.ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx") with step-by-step instructions to install the driver.

We're going to try Arnieboy's way and see if that works.

Good luck![/QUOTE]

Did you manage to get it working? Is it in the list at spca5xx's site?

EDIT: typo

---

### Post by poul33 on 2006-05-11
Arnieboy's instructions worked!  Anyone who tried easycam with no results should give it a try.

Good luck and thanks!

---

