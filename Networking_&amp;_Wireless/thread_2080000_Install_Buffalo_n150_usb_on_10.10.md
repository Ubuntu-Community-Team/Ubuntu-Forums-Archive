---
title: "Install Buffalo n150 usb on 10.10"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by Patonb on 2012-11-02
So I've been trying to install my buffalo n150 micro usb wifi on Ubuntu 10.10.
 
I've found the rt chipset should be rt8070
[http://www.wikidevi.com/wiki/Buffalo_WLI-UC-GNM](http://www.wikidevi.com/wiki/Buffalo_WLI-UC-GNM)
 
 
I d/l the drivers from: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
 
And following [http://ubuntuforums.org/showpost.php?p=11831414&postcount=18](http://ubuntuforums.org/showpost.php?p=11831414&postcount=18)
 
I get the rt5370 showing up in lsmod
```
brent@WOOHOO:~/Downloads/5073$ lsmod
Module Size Used by
crc_ccitt 1699 0
rt5370sta 801281 0
binfmt_misc 7984 1
parport_pc 30086 0
ppdev 6804 0
snd_hda_codec_realtek 300109 1
coretemp 6442 0
nouveau 569328 2
ttm 68212 1 nouveau
drm_kms_helper 32836 1 nouveau
f71882fg 30700 0
drm 206198 4 nouveau,ttm,drm_kms_helper
snd_hda_intel 26147 2
adt7475 26161 0
snd_hda_codec 100919 2 snd_hda_codec_realtek,snd_hda_intel
hwmon_vid 3154 1 adt7475
psmouse 62080 0
snd_hwdep 6660 1 snd_hda_codec
snd_pcm 89104 2 snd_hda_intel,snd_hda_codec
i2c_algo_bit 6208 1 nouveau
snd_seq_midi 5932 0
shpchp 34910 0
snd_rawmidi 22207 1 snd_seq_midi
snd_seq_midi_event 7291 1 snd_seq_midi
snd_seq 57512 2 snd_seq_midi,snd_seq_midi_event
snd_timer 23850 2 snd_pcm,snd_seq
snd_seq_device 6912 3 snd_seq_midi,snd_rawmidi,snd_seq
i7core_edac 18122 0
lp 10201 0
parport 37032 3 parport_pc,ppdev,lp
snd 64277 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 1240 1 snd
edac_core 46822 4 i7core_edac
serio_raw 4910 0
xhci_hcd 62016 0
snd_page_alloc 8588 2 snd_hda_intel,snd_pcm
joydev 11395 0
usbhid 42030 0
hid 84710 1 usbhid
pata_jmicron 2771 0
ahci 22370 2
sky2 53371 0
libahci 26148 1 ahci

```
but iwconfig doesn't show any devices:
 
So, can anyone help?

---

### Post by chili555 on 2012-11-03
Please post:```
lsusb
modinfo rt5370sta
```Afterwards, we'll re-compile.

---

### Post by Patonb on 2012-11-03
I can't get you the lsusb right now, its not plugged in and I'm not physically able to do it myself, but I assure you it comes up as 
 
0411:01a2 Melco Inc
 
As I've run lsusb many times. I will get the result later though
 
here['s modinfo rt53370sta
```

[EMAIL="brent@WOOHOO:~$"]brent@WOOHOO:~$[/EMAIL] modinfo rt5370sta
filename:       /lib/modules/2.6.35-30-generic-ck/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <[EMAIL="paul_lin@ralinktech.com"]paul_lin@ralinktech.com[/EMAIL]>
srcversion:     B5F68EDB8F10C7E19E04080
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:
vermagic:       2.6.35-30-generic-ck SMP mod_unload modversions
parm:           mac:rt28xx: wireless mac addr (charp)
[EMAIL="brent@WOOHOO:~$"]brent@WOOHOO:~$[/EMAIL]

```

---

### Post by chili555 on 2012-11-03
> [COLOR="Red"]0411:01a2[/COLOR] Melco IncAs we suspected, knew, actually, your device vendor and product ID are not listed. We can perform some surgery on the package you compiled and then re-compile, but what convinces you it's an rt5370sta device? Google doesn't convince me.

---

### Post by Patonb on 2012-11-03
I gathered it as it the ralink driver file (linked 1st post) is what I understood as the "all in one" driver for it.
 
I read on here that despite trying to install one chipset number, you actually see a different one in lsmod.
 
So basically I ASSuMEd it.
 
I have tried installing the rt2870 usb driver, as the wikidev page said it'll work in "compibility mode" but get a make error.
 
I went through the forum prior to asking, so I'm certain you have it runnimng in your head already.

---

### Post by chili555 on 2012-11-03
Upon further research, I am as convinced as we're going to get: somewhat, since this is a fairly new device. Please go to the folder you extracted and open common > rtusb_dev_id.c with a text editor. Add your device as I've highlighted here.> /* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT3070
	{USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
        [COLOR="Red"]{USB_DEVICE(0x0411,0x01A2)}, /* Melco 8070 */[/COLOR]
	{USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
	{USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
	{USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
	{USB_DEVICE(0x0DB0,0x871C)}, /* Ralink 3070 */
	{USB_DEVICE(0x0DB0,0x822C)}, /* Ralink 3070 */
	{USB_DEVICE(0x0DB0,0x871B)}, /* Ralink 3070 */
	{USB_DEVICE(0x0DB0,0x822B)}, /* Ralink 3070 */
	{USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
	{USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
	{USB_DEVICE(0x0DF6,0x0048)}, /* Sitecom 3070 */Everything before and after is unchanged. Spacing, brackets, indentation, etc. is crucial. Proofread carefully, save and close the text editor. Now back to the terminal:```
cd Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/  [COLOR="Red"]<--or wherever you extracted it[/COLOR]
sudo su
modprobe -r rt5370sta
make clean
make
make install
modprobe rt5370sta
exit
```Any improvement?

---

### Post by Patonb on 2012-11-03
Well no errors gettiung it installed.
 
I have to now wait till a working set of fingers come so I can get it plugged into my computer. 
 
Once I get it plugged in, I'll report back.
 
So it seems, that while the ralink driver is to "work" for it, the device id tag just isn't in the device list?

---

### Post by chili555 on 2012-11-03
>  the device id tag just isn't in the device list?Exactly.> while the ralink driver is to "work" for itWe don't know that for sure until it actually 'works.' As you can see by googling, it's a pretty new chipset and the success stories are few to non-existant. 

To put it more simply, we'll know it works when you tell us it works!

---

### Post by Patonb on 2012-11-03
Congrats you've created a success, And a satisfied customer.
 
Plugged it in and I know have ra0 and it now works as far as I can tell properly.
 
Thanks a bunch

---

### Post by chili555 on 2012-11-03
Awesome! Glad it's working. Have fun.

When you compile a package from a tar.gz or similar, it is compiled against your running kernel version only. When Update manager installs a later kernel version, also known as linux-image, you will need to re-compile against the new version:
```
cd Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/  [COLOR="Red"]<--or wherever you extracted it[/COLOR]
sudo su
make clean
make
make install
modprobe rt5370sta
exit
```Please retain your file and these instructions for that time.

---

### Post by Patonb on 2012-11-03
Thanks again

---

