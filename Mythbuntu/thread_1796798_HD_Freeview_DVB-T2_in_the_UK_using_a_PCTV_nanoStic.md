---
title: "HD Freeview DVB-T2 in the UK using a PCTV nanoStick T2"
date: 2011-07-04
forum: Mythbuntu
---

### Post by Slate8 on 2011-07-04
As there was only one old thread about this card, I thought I would post about my success in getting Freeview (over an aerial) HD tv working in MythTV using the PCTV nanoStick T2.

Before you bother/invest money make sure your nearest transmitter is broadcasting DVB-T2 :)

So, the hardware: [http://www.pctvsystems.com/Products/ProductsEuropeAsia/Digitalproducts/PCTVnanoStickT2/tabid/248/language/en-GB/Default.aspx](http://www.pctvsystems.com/Products/ProductsEuropeAsia/Digitalproducts/PCTVnanoStickT2/tabid/248/language/en-GB/Default.aspx)

The PCTV nanoStick T2 290e is the first PC TV tuner that supports DVB-T2. DVB-T2 is needed to receive HD channels via Freeview in the UK.

Next, The drivers. The Linux drivers for this device can be found via [http://stevekerrison.com/290e/index.html](http://stevekerrison.com/290e/index.html) 
I would like to thank Steve Kerrison for writing these drivers and getting the 290e talking to Linux. Great work!

The drivers can be installed using the LinuxTV projects V4L-DVB framework. Relevant links are [http://linuxtv.org/](http://linuxtv.org/) and the wiki at [http://linuxtv.org/wiki/](http://linuxtv.org/wiki/)

So, to get this this working with Myth just follow the install instructions at [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I ran through the "Basic" Approach, rebooted and the 290e was recorgnised. From there it was just a case of running the Myth-backend setup and adding the video source & rescanning etc. As well as the usual Freeview channels I now get BBC One HD, ITV1 HD, Channel4 HD and BBC HD. The quality is stunning.

That's all there is to it. So, if you are looking to watch HD content over Freeview this is one way to do it that works.

---

### Post by tobiz on 2011-07-04
> **Slate8 said:**
> As there was only one old thread about this card, I thought I would post about my success in getting Freeview (over an aerial) HD tv working in MythTV using the PCTV nanoStick T2.

Before you bother/invest money make sure your nearest transmitter is broadcasting DVB-T2 :)

So, the hardware: [http://www.pctvsystems.com/Products/ProductsEuropeAsia/Digitalproducts/PCTVnanoStickT2/tabid/248/language/en-GB/Default.aspx](http://www.pctvsystems.com/Products/ProductsEuropeAsia/Digitalproducts/PCTVnanoStickT2/tabid/248/language/en-GB/Default.aspx)

The PCTV nanoStick T2 290e is the first PC TV tuner that supports DVB-T2. DVB-T2 is needed to receive HD channels via Freeview in the UK.

Next, The drivers. The Linux drivers for this device can be found via [http://stevekerrison.com/290e/index.html](http://stevekerrison.com/290e/index.html) 
I would like to thank Steve Kerrison for writing these drivers and getting the 290e talking to Linux. Great work!

The drivers can be installed using the LinuxTV projects V4L-DVB framework. Relevant links are [http://linuxtv.org/](http://linuxtv.org/) and the wiki at [http://linuxtv.org/wiki/](http://linuxtv.org/wiki/)

So, to get this this working with Myth just follow the install instructions at [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I ran through the "Basic" Approach, rebooted and the 290e was recorgnised. From there it was just a case of running the Myth-backend setup and adding the video source & rescanning etc. As well as the usual Freeview channels I now get BBC One HD, ITV1 HD, Channel4 HD and BBC HD. The quality is stunning.

That's all there is to it. So, if you are looking to watch HD content over Freeview this is one way to do it that works.
This sounds very encouraging as I'd prefer this route rather than a satellite antenna.  A couple of questions: 1) does this give 1080i video & 5.1 audio (my HDMI connected AV amp gives me 7.1 audio)? 2) is the chip the same as used in the Blackgold BGT3620 PCI card, has anyone tried the Blackgold card?

---

### Post by Slate8 on 2011-07-05
I checked last night and the stream is 1080i. I heard rumours that the BBC were going to start broadcasting in 1080p but looks like this hasn't happened yet, or at least isn't happening on my transmitter.

The audio on my setup is downmixed to stereo so I haven't tried 5.1. As far as I know both the broadcast and driver support 5.1 audio.

I think the chipset is different. Details of the 290e chipset here [http://linuxtv.org/wiki/index.php/DVB-T2_USB_Devices](http://linuxtv.org/wiki/index.php/DVB-T2_USB_Devices)

As far as I know the Blackgold hardware is PCIe rather than USB and not supported by the Linux TV project yet.

---

### Post by tobiz on 2011-07-05
Slate8, I checked with the BBC Technical website and it says they broadcast in 1080i. Thanks for your info, most useful. I'll go ahead and buy a PCTV nanoStick T2 and install it in my 'production' Mythbuntu 8.10 system, and see what happens.  I've checked that the transmitter I use does broadcast the HD channels. For info the Blackgold web site says they will be releasing a Linux driver for the BGT3620, in June, but it's not clear if this is only available to OEMs (for some reason). They also say they will be releasing a BGT3630 which seems to be the same as the 3620 but without analogue, which given the direction of TV broadcasting in the UK seems sensible.

---

### Post by tobiz on 2011-07-06
Ok so I've ordered a nanoStick and on my none production system (Ubuntu 10.04) have tried building from git with success.  One question before trying this on my production system, just so as to be safe: can I save the contents of /lib/modules/[your kernel version]/kernel/drivers/media, run sudo make install and if things don't seem to be ok just restore back the saved modules?

---

### Post by Slate8 on 2011-07-07
I believe you can, see [http://www.gossamer-threads.com/lists/mythtv/users/481140](http://www.gossamer-threads.com/lists/mythtv/users/481140)

---

### Post by tobiz on 2011-07-08
> **Slate8 said:**
> I believe you can, see [http://www.gossamer-threads.com/lists/mythtv/users/481140](http://www.gossamer-threads.com/lists/mythtv/users/481140)
I think I'm trying to do the impossible here but just in case I'm doing something wrong: I've tried to build the CR2820r driver on my 2.6.27 kernel (production mythbuntu 8.10) system. I used the make menuconfig option to remove everything but the CR2820r DVB driver and then ran make.  The result I got was:
pjr@hms:~/media_build$ make
make -C /home/pjr/media_build/v4l 
make[1]: Entering directory `/home/pjr/media_build/v4l'
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/pjr/media_build/v4l'
make[1]: Entering directory `/home/pjr/media_build/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.27-8-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/pjr/media_build/v4l/firmware'
make[2]: Leaving directory `/home/pjr/media_build/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/pjr/media_build/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/pjr/media_build/v4l/firmware'
Kernel build directory is /lib/modules/2.6.27-8-generic/build
make -C ../linux apply_patches
make[2]: Entering directory `/home/pjr/media_build/linux'
Patches for v2.6.27 already applied.
make[2]: Leaving directory `/home/pjr/media_build/linux'
make -C /lib/modules/2.6.27-8-generic/build SUBDIRS=/home/pjr/media_build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-8-generic'
  CC [M]  /home/pjr/media_build/v4l/cxd2820r_core.o
In file included from <command-line>:0:
/home/pjr/media_build/v4l/compat.h:713:28: error: linux/firewire.h: No such file or directory
In file included from <command-line>:0:
/home/pjr/media_build/v4l/compat.h: In function 'fw_csr_string':
/home/pjr/media_build/v4l/compat.h:718: error: storage size of 'ci' isn't known
/home/pjr/media_build/v4l/compat.h:723: error: implicit declaration of function 'fw_csr_iterator_init'
/home/pjr/media_build/v4l/compat.h:724: error: implicit declaration of function 'fw_csr_iterator_next'
/home/pjr/media_build/v4l/compat.h:726: error: 'CSR_DESCRIPTOR' undeclared (first use in this function)
/home/pjr/media_build/v4l/compat.h:726: error: (Each undeclared identifier is reported only once
/home/pjr/media_build/v4l/compat.h:726: error: for each function it appears in.)
/home/pjr/media_build/v4l/compat.h:726: error: 'CSR_LEAF' undeclared (first use in this function)
/home/pjr/media_build/v4l/compat.h:718: warning: unused variable 'ci'
make[3]: *** [/home/pjr/media_build/v4l/cxd2820r_core.o] Error 1
make[2]: *** [_module_/home/pjr/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/pjr/media_build/v4l'
make: *** [all] Error 2


Of course it could just be that the build shouldn't work for such an old kernel but just in case, anyone know what the problem is?

---

### Post by tobiz on 2011-07-14
I have to report a failure, reason as yet unknown. On my Intel Atom 510 (64 bit) ubuntu 10.04 system (which is up to date with all fixes running 2.6.32-32-generic). I ran git clone, sudo make install, reboot. 
Results
1) I saw cxd2820r being built
2) lsusb gives:
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0471:0330 Philips SPC 710NC PC Camera
Bus 002 Device 002: ID 0c16:0001 Gyration, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 2013:024f  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ID 2013:024f is the nanoStick

3) lsmod doesn't show cxd2820r being loaded
4) vlc, unsurprisingly doesn't work
5) cxd2820r.ko is in ....../frontends
6) syslog shows
usb 1-7: new high speed USB device using ehci_hcd and address 10
Jul 14 13:15:28 aleutia-desktop kernel: [ 4315.503748] usb 1-7: configuration #1 chosen from 1 choice 

Whereas on 11.04 syslog it says, eventually:
 DVB: registering new adapter (em28xx #0)
: [   31.601680] DVB: registering adapter 0 frontend 0 (Sony CXD2820R (DVB-T/T2))...
 [   31.601826] DVB: registering adapter 0 frontend 1 (Sony CXD2820R (DVB-C))...
 [   31.602478] em28xx #0: Successfully loaded em28xx-dvb
[   31.602485] Em28xx: Initialized (Em28xx dvb Extension) extension

Which looks ok

I built a ubuntu 11.04 system on an old Intel (32 bit) system and did the same thing. 
Results
1) lsusb gives similar results but for ID 2103:024f says Unknown (Pinnacle?)
2) lsmod gives (lots of other stuff which includes)
cxd2820r               28464  1 em28xx_dvb
dvb_core               90106  2 em28xx_dvb,cxd2820r
Looks ok
3) running scan finds the device but for logistic reasons I have no outdoor aerial connection so doesn't find any channels.

Conclusion:
Seems to work on 32-bit 11.04 systems but not 64-bit 10.04 and if I had to guess the problem is on the usb detection side.  Any other thoughts and help welcome.  BTW I need to run the nanostick with the 10.04 system as it has an outdoor aerial connection.

---

### Post by stevekerrison on 2011-07-14
I'm not sure why it wouldn't work on 32-bit 10.04 - I compiled it successfully on there.

From what you've said it may be that the dvb-usb module doesn't contain the entry for the 290e (the data that produces the output of lsusb is dealt with elsewhere, however).

I'm not sure what to suggest to fix it as there shouldn't really be any difference, and you're using make install so the updated modules should **all** get copied in.

Perhaps check the timestamps on the module files, particularly dvb-usb and the em28xx collection to be sure they've all been installed properly.

---

### Post by tobiz on 2011-07-14
Ok, I'm not suggesting it is a 32-bit vs 64-bit issue just one of the difference factors between where it works and were it doesn't work, it maybe and is probably not relevant.

As to the timestamps of the various directories:

/lib/modules/2.6.32-32-generic/kernel/drivers/media/video/em28xx$ ls -l
total 248
-rw-r--r-- 1 root root  25240 2011-07-14 14:43 em28xx-alsa.ko
-rw-r--r-- 1 root root  33248 2011-07-14 14:43 em28xx-dvb.ko
-rw-r--r-- 1 root root 187616 2011-07-14 14:43 em28xx.ko

/lib/modules/2.6.32-32-generic/kernel/drivers/media/dvb/dvb-usb$ ls -l
total 1140
-rw-r--r-- 1 root root  14432 2011-07-14 14:43 dvb-usb-a800.ko
-rw-r--r-- 1 root root  62528 2011-07-14 14:43 dvb-usb-af9005.ko
-rw-r--r-- 1 root root   7624 2011-07-14 14:43 dvb-usb-af9005-remote.ko
-rw-r--r-- 1 root root  56912 2011-07-14 14:43 dvb-usb-af9015.ko
-rw-r--r-- 1 root root  29952 2011-07-14 14:43 dvb-usb-anysee.ko
-rw-r--r-- 1 root root  15944 2011-07-14 14:43 dvb-usb-au6610.ko
-rw-r--r-- 1 root root  32512 2011-07-14 14:43 dvb-usb-az6027.ko
-rw-r--r-- 1 root root  18504 2011-07-14 14:43 dvb-usb-ce6230.ko
-rw-r--r-- 1 root root  19064 2011-07-14 14:43 dvb-usb-cinergyT2.ko
-rw-r--r-- 1 root root  88776 2011-07-14 14:43 dvb-usb-cxusb.ko
-rw-r--r-- 1 root root 185600 2011-07-14 14:43 dvb-usb-dib0700.ko
-rw-r--r-- 1 root root  17832 2011-07-14 14:43 dvb-usb-dibusb-common.ko
-rw-r--r-- 1 root root  31760 2011-07-14 14:43 dvb-usb-dibusb-mb.ko
-rw-r--r-- 1 root root  14696 2011-07-14 14:43 dvb-usb-dibusb-mc.ko
-rw-r--r-- 1 root root  17680 2011-07-14 14:43 dvb-usb-digitv.ko
-rw-r--r-- 1 root root  34232 2011-07-14 14:43 dvb-usb-dtt200u.ko
-rw-r--r-- 1 root root  14960 2011-07-14 14:43 dvb-usb-dtv5100.ko
-rw-r--r-- 1 root root  71800 2011-07-14 14:43 dvb-usb-dw2102.ko
-rw-r--r-- 1 root root  21960 2011-07-14 14:43 dvb-usb-ec168.ko
-rw-r--r-- 1 root root  26384 2011-07-14 14:43 dvb-usb-friio.ko
-rw-r--r-- 1 root root  15408 2011-07-14 14:43 dvb-usb-gl861.ko
-rw-r--r-- 1 root root  27104 2011-07-14 14:43 dvb-usb-gp8psk.ko
-rw-r--r-- 1 root root  43160 2011-07-14 14:43 dvb-usb.ko
-rw-r--r-- 1 root root  44352 2011-07-14 14:43 dvb-usb-lmedm04.ko
-rw-r--r-- 1 root root  47904 2011-07-14 14:43 dvb-usb-m920x.ko
-rw-r--r-- 1 root root  14240 2011-07-14 14:43 dvb-usb-nova-t-usb2.ko
-rw-r--r-- 1 root root  21568 2011-07-14 14:43 dvb-usb-opera.ko
-rw-r--r-- 1 root root  23880 2011-07-14 14:43 dvb-usb-technisat-usb2.ko
-rw-r--r-- 1 root root  27960 2011-07-14 14:43 dvb-usb-ttusb2.ko
-rw-r--r-- 1 root root  14384 2011-07-14 14:43 dvb-usb-umt-010.ko
-rw-r--r-- 1 root root  27672 2011-07-14 14:43 dvb-usb-vp702x.ko
-rw-r--r-- 1 root root  22152 2011-07-14 14:43 dvb-usb-vp7045.ko

So as expected they all have the same timestamp.
It does look like a usb problem but I have no idea why it's not (I assume) detected correctly or how to fix it.

Some more info:
usb-devices returns
T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#= 12 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2013 ProdID=024f Rev=01.00
S:  Manufacturer=PCTV Systems
S:  Product=PCTV 290e
S:  SerialNumber=00000006W4P0
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

So something knows about the 2013:024f device but the Driver=(none) looks like the problem

---

### Post by tobiz on 2011-07-15
Result!! (Well nearly)
I've just installed the latest 10.04 LTS upgrade which includes the 2.6.32-33-generic kernel.  I've repeated the git, build.sh, make install, reboot and the 290e now works with vlc - great.

BUT No HD channels!
Running scan /usr/share/dvb/dvb-t/uk-EmleyMoor -o zap | tee ~/channels.conf doesn't return any HD channels.
It may be to do with the data used by scan.  The Emley Moor transmitter does broadcast HD, see [http://www.ukfree.tv/txdetail.php?a=SE222128]("http://www.ukfree.tv/txdetail.php?a=SE222128"). I'll investigate this.  I'm using an aerial amp so signal is good.

---

### Post by tobiz on 2011-07-15
Success!!
It was the scan data. If anyone's interested I added this line to the file used by scan for the Emley Moor transmitter:

T 618000000 8MHz 4/5 NONE QAM256 32k 1/128 NONE

Field #2 is the transmitter frequency, change for your tx, the other fields should be ok as is, but I don't guarantee that!

Fields #4,7,8 were taken from [http://www.dvb.org/technology/fact_sheets/index.xml]("http://www.dvb.org/technology/fact_sheets/index.xml"), see, "DVB-T2 - 2nd Generation Terrestrial Broadcasting".

One slight problem I may have discovered is that after unplugging and plugging in the 290e it stops working - may need looking at, it is after all experimental.

---

### Post by burrluk on 2011-08-04
Hi Tobiz,
 
You sound like a man that can help me.
 
I have tried to modify the /usr/share/dvb/dvb-t/uk-EmleyMoor file with the details you provided but no luck.  scan (and scandvb) both throw errors on 32k and 1/128 options.
 
what version of scan are you using?

---

### Post by tobiz on 2011-08-04
> **burrluk said:**
> Hi Tobiz,
 
You sound like a man that can help me.
 
I have tried to modify the /usr/share/dvb/dvb-t/uk-EmleyMoor file with the details you provided but no luck.  scan (and scandvb) both throw errors on 32k and 1/128 options.
 
what version of scan are you using?
Good question! I'm using the latest available from the ubuntu 10.04 repository ie 1.1.1+rev1273-1ubuntu1, it's a component of dvb-apps.  I've attached the channels.conf file it produces if that helps.  I've also added my updated version of the uk-EmleyMoor data with the HD channels data included on the end.  What errors are you getting?  Do you get the same errors using the data attached?  I took the information from here: [http://www.dvb.org/technology/fact_sheets/DVB-T2_Factsheet.pdf]("http://www.dvb.org/technology/fact_sheets/DVB-T2_Factsheet.pdf").
BTW I've been told the unplugging issue is not the 290e (cxd2820r) driver itself but a known problem with a module it uses.  There's a workaround but I've not tried it yet.

---

### Post by rankincj on 2011-08-15
> **tobiz said:**
> I've also added my updated version of the uk-EmleyMoor data with the HD channels data included on the end.

Hi,

I'm also trying to tune my 290e adapter into my local transmitter, and I have discovered this site:

[http://www.ukfree.tv/txdetail.php?a=SE222128](http://www.ukfree.tv/txdetail.php?a=SE222128)

So the best parameters for the Emley Moor transmitter's HD MUX are (apparently):

[B]T 618000000 8MHz 2/3 AUTO QAM256 AUTO AUTO AUTO
[/B] 
The scandvb application doesn't seem to support all DVB-T2 parameters yet, but the 290e has an auto-tuning algorithm. In fact, it has been suggested that as little as:

**T 618000000 8MHz AUTO AUTO AUTO AUTO AUTO AUTO**

is enough for scandvb, provided the signal strength where you are is high enough.

---

### Post by deadite66 on 2011-08-28
Compiling from git tree seems to be a pain, random between compile errors and compiling correctly but only doing a few modules.

hopefully i'll download something workable before my dongle arrives.

---

### Post by rulet on 2011-09-17
Does Linux Kernel 3.0 has the driver for this tuner already included?

---

### Post by deadite66 on 2011-09-17
> **rulet said:**
> Does Linux Kernel 3.0 has the driver for this tuner already included?

yes it does.
i've happily run both the oneiric kernel on maverick and now running oneiric full time on my mediapc (with regular backups in case of upgrade breakages).

---

### Post by rulet on 2011-09-17
What program for watching do you use, what connection to audio system and is there any problems with audio?

---

### Post by deadite66 on 2011-09-17
we don't have HD transmissions yet in our region so i can't speak for compatibility.

i don't need live tv so use xbmc as it looks much better than mythtv-frontend, i've been making meaningful file names with mythlink.pl

```
/usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl --dest /home/sharedfiles/movies/TV-readable/ --format '%T %S -- %d-%m-%y %H:%i'
```

and use mythtv-backend for recording and mythweb for admin'ing via the browser which makes it very handy to set recordings if your away from the house.

audio is via standard stereo patch cable as i only have DVI, haven't noticed any audio problems yet.

---

### Post by rulet on 2011-09-18
I see -- you just using mythtv for recording and xbmc for watching recorded. Is that line which you put somewhere in xbmc config and when you start xbmc you can see what mythtv has recorded?

---

### Post by deadite66 on 2011-09-18
no i make it a cron job that runs every 15 minutes.

---

### Post by Cuppa-Chino on 2011-12-20
Hi has anyone got the remote control working for this device? If so how do I set it up for Mythtv?

my google-fu only turned up this chat on [patchwork]("http://patchwork.linuxtv.org/patch/7102/") 

thanks

---

### Post by bilboubu on 2012-02-18
I have this card and am trying out mythtv, I am new to Linux and need some help.

I have installed mythtv on xbmcbuntu 11.10 but have no idea how to set the back end up. I dont think I need to do any manual driver install as I can see the usb stick as an option in card setup. 

I was hoping for some sort of dummies guide for this particular card on the setup screens.
What should the card type be? it defaults to analog v4l capture card
Video source? i think i want transmitted guide only for now
Input connections? no idea

I am lost and cant seem to get it to work, any help would be appreciated.

---

### Post by deadite66 on 2012-02-18
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by bilboubu on 2012-02-18
thanks for this, but I cannot seem to get any channels, is this what worked for you?

---

### Post by deadite66 on 2012-02-19
yes it worked for me, do you have a strong signal? i found the 290e to be deafer than any other dvb hardware i have.

---

### Post by bilboubu on 2012-02-19
I have managed to scan now and has picked up the channels. I needed to select the sony device which was confusing.

Next issue however, when in the front end and I go to live tv I get a blank screen and it says channel change failed. Come across that?

---

### Post by deadite66 on 2012-02-19
i haven't had that problem but then i only record on mythtv.

this is my setup.

[IMG]http://dl.dropbox.com/u/7618572/mythtv/mythtv-setup-1.jpg[/IMG] 
[IMG]http://dl.dropbox.com/u/7618572/mythtv/mythtv-setup-2.jpg[/IMG]
[IMG]http://dl.dropbox.com/u/7618572/mythtv/mythtv-setup-3.jpg[/IMG]

---

### Post by bilboubu on 2012-02-19
Thank you, I have got it working now.

How quickly do your channels change, mine seems to take a few seconds, is this down to myth tv, is there a way to speed it up?

---

### Post by nickrout on 2012-02-19
Channel change takes significantly longer than a STB or TV set. 

Then again myth's primary goal is not LiveTV.

---

### Post by Cuppa-Chino on 2012-04-10
just wanted to bump my question on the remote.

I have upgraded to kernel 3.2 and have most of keys working, except channel up, down and ok ---> which would be useful to have as they form the only kind of arrow area !



I have seen that there was a patch in discussion as early as august in some of the upstream mailing lists but am still stuck...

also any idea how I can find out if the device can do more scan codes and use a universal remote to operate it with more codes?

> **deadite66 said:**
> i haven't had that problem but then i only record on mythtv.

this is my setup.



what do you use as frontend?

---

### Post by deadite66 on 2012-04-10
> **Cuppa-Chino said:**
> 
what do you use as frontend?

mostly XBMC but due to BBC changing audio rates midstream on HD channels i've been using the [libcmyth version]("http://forum.xbmc.org/showthread.php?tid=110694") (it's a self compile though) he added extras that mythtv included to fix the audio problem.

i haven't been using its PVR addon though just the built-in myth:// protocol.

---

### Post by tez1982 on 2012-05-22
> **Cuppa-Chino said:**
> just wanted to bump my question on the remote.


Can I ask how you got this working at all. I'm running mythbuntu 12.04 and can't get the remote to work at all?

---

### Post by tez1982 on 2012-05-25
> **tez1982 said:**
> Can I ask how you got this working at all. I'm running mythbuntu 12.04 and can't get the remote to work at all?

Figured it out, the v4l drivers don't seem to support the IR interface. 

In case anyone else is pulling their hair out over getting the PCTv nanostick 290e remote here is my LIRC config.

#/etc/lirc/hardware.conf
REMOTE="pctvusb"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event8"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""


#~/.lircrc
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa

#~/.mythtv/lircrc
begin
    remote = pctvusb
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_ESC
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_FASTFORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = pctvusb
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

#/etc/lirc/lircd.conf
begin remote

  name  pctvusb
  bits           56
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x0
  gap          251812
  toggle_bit_mask 0x0

      begin codes
          BTN_0                    0x04000400000727 0x01000B00000001
          BTN_1                    0x0400040000070F 0x01000200000001
          BTN_2                    0x04000400000715 0x01000300000001
          BTN_3                    0x04000400000710 0x01000400000001
          BTN_4                    0x04000400000718 0x01000500000001
          BTN_5                    0x0400040000071B 0x01000600000001
          BTN_6                    0x0400040000071E 0x01000700000001
          BTN_7                    0x04000400000711 0x01000800000001
          BTN_8                    0x04000400000721 0x01000900000001
          BTN_9                    0x04000400000712 0x01000A00000001
          KEY_MUTE                 0x04000400000700 0x01007100000001
          KEY_MENU                 0x04000400000701 0x01008B00000001
          KEY_POWER                0x04000400000739 0x01007400000001
          KEY_UP                   0x04000400000706 0x01019200000001
          KEY_DOWN                 0x0400040000070C 0x01019300000001
          KEY_LEFT                 0x04000400000709 0x01007200000001
          KEY_RIGHT                0x04000400000703 0x01007300000001
          KEY_OK                   0x04000400000705 0x01016000000001
          KEY_ESC                  0x0400040000073C 0x01008000000001
          KEY_EPG                  0x0400040000073F 0x01008A00000001
          KEY_RECORD               0x04000400000736 0x0100A700000001
          KEY_PLAY                 0x04000400000730 0x0100A400000001
          KEY_FASTFORWARD          0x04000400000733 0x0100D000000001
          KEY_REWIND               0x0400040000072D 0x0100A800000001
      end codes

end remote

---

### Post by deadite66 on 2012-09-04
tried out the 290e in 12.10 alpha3 and it's much better.
scans faster and locks on a mux without having to use an attenuator.

---

### Post by jksj on 2012-09-17
High thanks for the info on getting the remote to work  **tez1982. **However I am still having limited success. Most keys on the remote work out the box without any configuration ie without using the Mythbuntu Control Centre to install lirc etc.. The remote is being seen as a keyboard on /dev/input/event6. The numeric keys, the volume and exit all work but not ok, up, down, ff,rw or play.   
Installing lirc and implementing your file changes, has no effect - any suggestions?

---

### Post by tsh on 2012-09-18
I just got one of these, and it is only showing HD channels (from Sandy tx, I think). I get 5 channels, but none of the SD channels that my Nova-T picks up. Trying a scan with the windows software to check its not a hardware problem, but any tips for making Myth find the channels?

---

### Post by deadite66 on 2012-09-18
it's a problem with the kernel, something is enabled with dvb-t2 signals but not with dvb-t.
i have to use an attenuator to lower the signal strength then it will pick the SD channels up.

this is fixed in the quantal kernels and hopefully will be backported to precise when quantal is released.

---

### Post by tsh on 2012-09-18
Far more sensitive than the Nova-T. I get a passable HD signal using the comedy stick antenna included in the box. Taking the amp out of the circuit fixes it (so the amp was probably introducing imd too)

---

### Post by deadite66 on 2012-09-29
3.5.0 kernel up on the edgers ppa for the daring.

can scan all channels without an attenuator now, fingers crossed recording is more stable.

---

### Post by dansang on 2013-04-14
Has anyone got the remote to work? i tried the suggestions in this thread! none have worked!! please anyone help??

---

### Post by jksj on 2013-04-16
No It did not work for me either.
Happily using a [http://www.amazon.co.uk/Rii-2-4GHz-Wireless-Keyboard-Touchpad/dp/B004FSFYG8/ref=sr_1_1?s=computers&ie=UTF8&qid=1366109331&sr=1-1&keywords=miniature+wireless+keyboard](http://www.amazon.co.uk/Rii-2-4GHz-Wireless-Keyboard-Touchpad/dp/B004FSFYG8/ref=sr_1_1?s=computers&ie=UTF8&qid=1366109331&sr=1-1&keywords=miniature+wireless+keyboard) which works out of the box.

---

### Post by tobiz on 2013-10-09
> **jksj said:**
> No It did not work for me either.
Happily using a [http://www.amazon.co.uk/Rii-2-4GHz-Wireless-Keyboard-Touchpad/dp/B004FSFYG8/ref=sr_1_1?s=computers&ie=UTF8&qid=1366109331&sr=1-1&keywords=miniature+wireless+keyboard](http://www.amazon.co.uk/Rii-2-4GHz-Wireless-Keyboard-Touchpad/dp/B004FSFYG8/ref=sr_1_1?s=computers&ie=UTF8&qid=1366109331&sr=1-1&keywords=miniature+wireless+keyboard) which works out of the box.
I've upgraded to mythtv 0.25 (from ubuntu repo) on ubuntu 12.04 using the usb pctv 290e.  Myth backend refuses to recognise this device, reporting an error.  If I run the scan command for adapter0 and the uk-EmleyMoor config file it returns the full set of channels (including the HD ones after adding this to uk-EmelyMoor file).  So the device is recognised by the system, can be used to scan for channels but mythbackend fails when it is selected.  Any ideas as to why this happens or how to fix it or whether it's fixed in a later version.

---

