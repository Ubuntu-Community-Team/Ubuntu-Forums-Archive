---
title: "Help with: Terratec Cinergy S2 USB HD (rev2): s2-liplianin"
date: 2011-11-14
forum: Mythbuntu
---

### Post by Jim_101 on 2011-11-14
Hi,
I'm a bit of a noob with linux and I'm struggling to get this working.

I'm using mythbuntu 11.10 kernel 3.0.0-12-generic.

To get it installed I need s2-liplianin.

I've downloaded both files from the terratec website [here]("http://linux.terratec.de/tv_en.html").

Firmware copied to /lib/firmware
Patch applied
Then when I try to make I get this:

```

make -C /usr/src/s2-liplianin-7ea7cc0eaa40/v4l 
make[1]: Entering directory `/usr/src/s2-liplianin-7ea7cc0eaa40/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/firmware'
make[2]: Leaving directory `/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/firmware'
make -C firmware
make[2]: Entering directory `/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/firmware'
Kernel build directory is /lib/modules/3.0.0-12-generic/build
make -C /lib/modules/3.0.0-12-generic/build SUBDIRS=/usr/src/s2-liplianin-7ea7cc0eaa40/v4l CFLAGS="-I../linux/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /usr/src/s2-liplianin-7ea7cc0eaa40/v4l/tuner-xc2028.o
/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/tuner-xc2028.c: In function 'xc2028_set_params':
/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/tuner-xc2028.c:1178:5: error: 'T_DIGITAL_TV' undeclared (first use in this function)
/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/tuner-xc2028.c:1178:5: note: each undeclared identifier is reported only once for each function it appears in
/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/tuner-xc2028.c:1179:1: warning: control reaches end of non-void function [-Wreturn-type]
make[3]: *** [/usr/src/s2-liplianin-7ea7cc0eaa40/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/usr/src/s2-liplianin-7ea7cc0eaa40/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/s2-liplianin-7ea7cc0eaa40/v4l'
make: *** [all] Error 2

```

Can anyone help?

Thanks,
Jim

---

### Post by nemanaldin on 2011-11-15
hi,
i have this problem too
my dvb is technotrend s2-3200
please help

---

### Post by slarty2000 on 2011-11-15
I'm getting something very similar to that too with my Technisat skystar usb HD
when i run lsusb i get
Bus 001 Device 002: ID 14f7:0500 TechniSat Digital GmbH DVB-PC TV Star HD

I've tried to down load a firmware file and add to the lib\firmware
I installed mercurial
i tried to follow this wiki [http://linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD](http://linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD)

but I get the same problem as you with the make

I'm a novice to linux so I could be doing something wrong or maybe this process no longer works with ubuntu 11:10?

any help would be great

---

### Post by Jim_101 on 2011-11-16
I finally went back to 10.04 and managed to get s2-liplianin to build fine.

I followed the steps in the readme file of the patch archive on the Terratec Linux website:

1. get s2-liplianin repository:
hg clone [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin)

2. copy firmware:
-copy "dvb-fe-ds3000.fw" to "/lib/firmware"


3. copy patch and apply it:
-copy "cinergy_s2_usb_r2.patch" to "s2-liplianin"
(cd into s2-liplianin folder)
patch -p1 -i cinergy_s2_usb_r2.patch
(in case of sucess just the following message appears:
"patching file linux/drivers/media/dvb/dvb-usb/dw2102.c")


4. make (still within "s2-liplianin" folder)


4a. (only if error with module FIREDTV):
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
make


5. sudo make install


6. connect "CINERGY S2 USB Rev.2" and enjoy!

Also a lot of info here:
[http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI)

If anyone does know how to get this to build in Oneric I'd love to know.

Jim

---

### Post by Jim_101 on 2011-11-17
This caused a whole host of other problems, making this not an option for me; my nvidia card HDMI output isn't recognized in the sound settings in MythTV, my cheapo DVB-T usb stick isn't recognized either.

I found this problem with s2-liplianin documented here,
[http://linuxtv.org/wiki/index.php/S2-liplianin](http://linuxtv.org/wiki/index.php/S2-liplianin)
but as current it seems there's no solution to it.

Theres some foreign posts that I'm trying to make sense of.

---

### Post by nickrout on 2011-11-18
For heaven's sake people, just buy supported cards.

Do not buy a card based on a manufacturer's drivers. Buy one with drivers in the mainstream kernel.

---

### Post by alien878 on 2011-11-23
The ironic thing is, the drivers have been in the kernel since 2.6.39 according to [http://linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD](http://linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD)

I have not been able to get a card with the same chipset to work on these included drivers and am also stuck on 10.04.  I can't complain... it all works, so I just lock the kernel version and leave it alone.

Note:  I had more luck with the older mantis drivers from jusst.de than the s2-liplainin.  See here for details on both (different card, same drivers):

[http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C)

---

### Post by Whiskey-Jack on 2011-11-29
I have a similar problem with a different card (TechniSat Skystar HD). Since I also only just took my first steps in LinuxTV land I'm a bit lost. What I would like to understand is why I should compile and install liplianin when there are drivers included in the kernel? 

My card is working, but only with scan and normal channels. I can't get HD channels so I tried scan-s2. But in order to compile that it seems to need liplianin which in turn won't compile (same problem as mentioned earlier). I don't mind compiling, but there seem to be so many dirvers,  branches and packages/apps (scan that works for me, dvbscan that doesn't, scan-s2 that you need to compile yourself) that it is all just a bit confusing. So if anyone can shed some light on this it would be greatly appreciated  ;)

---

### Post by alien878 on 2011-11-30
Hi WJ.  I really can't say why the kernel drivers didn't work for me.  I've tried both 10.10 and 11.04 without success.  There were some comments that a buggy version was imported, but that should have been fixed by now.

If you have SD and not HD, you might check signal strength, connectors, etc.  I find hat HD is much more sensitive to poor signal strength.  You might also check dmesg and lsusb to see if the device was detected as an S2.

---

### Post by Whiskey-Jack on 2011-12-06
Thanks for your reply. I did play around a bit and it seems the drivers with kernel 3.0 are working fine for me. I just couldn't get scan-s2 to work, but as it turns out w_scan works perfectly. I had tried with a bunch of different older kernels with s2-liplianin and although one worked, most did not even detect the card. No matter as the latest one is working fine without the need to install additional drivers.

---

### Post by Loki555 on 2012-01-03
@Whiskey-Jack
I have a Terratec Cinergy S2 USB HD rev2 and want to use it on Ubuntu 11.10 can you please post your solution?

Greetings
Loki

---

### Post by Whiskey-Jack on 2012-01-03
I just used the stock kernel with the latest Ubuntu release. The drivers in there work fine for me, however, I'm not using a usb solution. My actual problem turned out to be scan-s2 which wouldn't work with HD channels. However, with w_scan scanning HD channels did work. Hope it helps.

---

### Post by kamolt on 2012-03-11
> **nickrout said:**
> For heaven's sake people, just buy supported cards.

Do not buy a card based on a manufacturer's drivers. Buy one with drivers in the mainstream kernel.

I did not yet find any S2 card with CI that works properly under Linux. I have a tt-s2-3200 that usually works ok for S2 channels but mostly fails for S channels. For example it is unable lock the French Mezzo channel. To receive Mezzo i have to switch to an old TT-S1500 - CI dvb pci card. A few kernels ago before 2.6 I think tt-S2-3200 worked much better. 
So for all I know there is NO dvb-s2 + CI card that works 100% with the so called drivers in the mainstream kernel. I am a very long term mythtv user and I like Ubuntu a lot but if consider all the hours I hav spent to get things working then I must ackowledge that W7 is a very cheap OS. Everything works out of the box....

---

