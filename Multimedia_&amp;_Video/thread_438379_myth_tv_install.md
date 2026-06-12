---
title: "myth tv install"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by Bashed on 2007-05-09
I'm looking to install MythTV on Feisty here as a replacement for Media Center (Vista)

Problem is:

- I do not know which to install: frontend? backend? both?
- what do I input for mysql database info?

I'm installing this on my Ubuntu Feisty desktop, so its not a dedicated, separated box for Mythtv.

I'm using this link
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

I ran  mythtv-setup and have no idea how to do this. What should the capture card be?

I use an eternal USB by PinnacleSys, model HD-Pro Stick 800e.

Thanks in advance.

---

### Post by tgm4883 on 2007-05-09
Do you already have your tuner working in linux?

---

### Post by Bashed on 2007-05-09
No. This is my whole purpose here, to get it working.  It works fine in Vista, but I have no idea how to properly use it (any software) in linux.

Hopefully you know how ;)

---

### Post by emperor on 2007-05-09
The first requirement for a MythTV backend is a compatible hardware tuner. It does not appear that your USB tuner is supported:

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)

After you pray for wisdom, I recommend that you read the documentation on this site:
[http://www.mythtv.org/](http://www.mythtv.org/)

If you are going to get a remote control working for the frontend, it will be easier with Fedora Core. On Ubuntu, you will have to compile a lirc kernel module.

---

### Post by Bashed on 2007-05-09
> **emperor said:**
> The first requirement for a MythTV backend is a compatible hardware tuner. It does not appear that your USB tuner is supported:

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)

After you pray for wisdom, I recommend that you read the documentation on this site:
[http://www.mythtv.org/](http://www.mythtv.org/)

If you are going to get a remote control working for the frontend, it will be easier with Fedora Core. On Ubuntu, you will have to compile a lirc kernel module.

What a shame, you edited your post just to add this sarcastic line?

"After you pray for wisdom"

What for is that comment?  The automatic thread notification sent me this prior to your edit:

"  I read the documentation on this site first!
  [http://www.mythtv.org/](http://www.mythtv.org/)
  "

If you cannot reply without being rude and making comments related to my username, don't reply at all.

---

### Post by KiwiNZ on 2007-05-09
Please keep the personal stuff out of here .
If it continues I will close this thread.

---

### Post by newlinux on 2007-05-09
The list of tuners posted earlier is not comprehensive. Do a search around or read through some of myth Wiki info to find out if it is truly incompatible (although, I've never heard of that one being compatible, and there aren't too many USB models that are). Also, LIRC is not that difficult in ubuntu and there is a good guide for doing so.

---

### Post by Erlander on 2007-05-09
Your tuner is listed here:

[http://www.linuxtv.org/wiki/index.php/DVB_USB#Pinnacle_PCTV_HD_Pro_Stick](http://www.linuxtv.org/wiki/index.php/DVB_USB#Pinnacle_PCTV_HD_Pro_Stick)

as  Unspecified/Unknown/Unsupported devices

Rob

---

### Post by Bashed on 2007-05-09
I also have the Hauppuage HVR-950, which according to this link works.  For me, I tried it again (same directions) and got the SAME error when I ran "make".  What to do?

[http://lunapark6.com/?p=2682&cp=3#comment-57895](http://lunapark6.com/?p=2682&cp=3#comment-57895)

---

### Post by tgm4883 on 2007-05-09
What error?

---

### Post by newlinux on 2007-05-09
Those are instructions for edgy, and feisty has a lot more built in support for cards. Are you running Feisty? What SAME error are you referring to (I don't see you talk about make earlier in this post)? If you are running feisty--Shot in the dark--try modprobing the em28xx module:

```

sudo modprobe em28xx

```

After you have untarred the firmware in the proper location and rebooted.

---

### Post by newlinux on 2007-05-09
> **tgm4883 said:**
> What error?

I think he is referring to the error the Feisty user in the link he posted received when trying to run make, but I'm not sure...

---

### Post by Bashed on 2007-05-10
Sorry, forgot to post the error:

[EMAIL="root@Secured:/lib/firmware/v4l-dvb-kernel-history#"]root@Secured:/lib/firmware/v4l-dvb-kernel-history#[/EMAIL] make
make -C /lib/firmware/v4l-dvb-kernel-history/v4l
make[1]: Entering directory `/lib/firmware/v4l-dvb-kernel-history/v4l’
scripts/make_makefile.pl
No version yet.
Updating/Creating .config
Preparing to compile for kernel version 2.6.20
 ***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.
 If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.
 Vanilla kernels are available at [http://kernel.org.]("http://kernel.org./")
On most distros, this will compile a newly downloaded kernel:
 cp /boot/config-`uname -r` /.config
cd
make all modules_install install
 Please see your distro’s web site for instructions to build a new kernel.
 VIDEO_PLANB: Requires at least kernel 2.6.99
VIDEO_ZR36120: Requires at least kernel 2.6.99
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/lib/firmware/v4l-dvb-kernel-history/v4l’
make[1]: Entering directory `/lib/firmware/v4l-dvb-kernel-history/v4l’
creating symbolic links…
ln -sf . oss
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/lib/firmware/v4l-dvb-kernel-history/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic’
  CC [M]  /lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.o
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function ‘flexcop_pci_irq_check_work’:
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c:119: warning: passing argument 1 of ’schedule_delayed_work’ from incompatible pointer type
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function ‘flexcop_pci_stream_control’:
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c:226: warning: passing argument 1 of ’schedule_delayed_work’ from incompatible pointer type
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c:229: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378:71: error: macro “INIT_WORK” passed 3 arguments, but takes just 2
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function ‘flexcop_pci_probe’:
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: ‘INIT_WORK’ undeclared (first use in this function)
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: (Each undeclared identifier is reported only once
/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: for each function it appears in.)
make[3]: *** [/lib/firmware/v4l-dvb-kernel-history/v4l/flexcop-pci.o] Error 1
make[2]: *** [_module_/lib/firmware/v4l-dvb-kernel-history/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic’
make[1]: *** [default] Error 2
make[1]: Leaving directory `/lib/firmware/v4l-dvb-kernel-history/v4l’
make: *** [all] Error 2



Now, I do have the Hauppauge HVR-950 (usb) but every "HVR" is listed in the compatibility link except my 950 :D  ...yet this person got his 950 working (but I got the above errors)




[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html)

---

### Post by newlinux on 2007-05-10
did you try my suggestion?

---

### Post by Bashed on 2007-05-10
I will try and get back to you.

Anyone know at least when LinuxMCE will be available for Feisty Fawn? Their site and forum show no details, but someone in the mailing list said "I heard in a couple of weeks". Just curious. It would be an easier route and nicer interface to have linuxmce.

---

### Post by newlinux on 2007-05-10
From what I've heard from others *trying* installing it, I doubt it will be an easier route.

---

### Post by tgm4883 on 2007-05-10
> **TalkJesus said:**
> I will try and get back to you.

Anyone know at least when LinuxMCE will be available for Feisty Fawn? Their site and forum show no details, but someone in the mailing list said "I heard in a couple of weeks". Just curious. It would be an easier route and nicer interface to have linuxmce.

Wrong, it will be (at the least) as difficult (if not more) to setup since linuxmce uses mythtv for its media center

---

### Post by Bashed on 2007-05-11
I ran 

sudo modprobe em28xx

I also ran the myth backend setup, populated database.

Now when I attempt to go to frontend to watch tv, it tells me "myth is already using all available inputs for the channel you selected..."

Why? 

In the backend, the capture card I selected for my Hauppage PVR-950 was 

MPEG-2 encoder card  (PVRx50, PVR-500). 


In "input connections" setup area it says

capture device: mpeg " could not open to probe its inputs"


Myth tv is way to complex to setup. 

MCE is the easiest thing to use.

---

### Post by newlinux on 2007-05-11
I don't thank that card is an mpeg-2 encoder card. Try setting it up as a DVB card (as is done in the instructions of the link you posted earlier). Before trying to watch it, you have to define a video source and assign it to an input. That's why you are getting that message, you haven't set the card up properly yet. Note that when you set the card Type as DVB it won't exactly identify the name of the card.

Yes, myth is can be complex and isn't for everybody, but It can do a lot of things MCE can't do and it is free... You can make myth a lot easier with hardware selection. If you took any old random computer with hardware that isn't well supported with MCE and tried to install it you'd have a lot of problems too. If you bought a computer preinstalled with hardware to work with MCE and a computer preinstalled with hardware to work with myth the difference in difficulty to setup would not be nearly as pronounced.

---

### Post by Bashed on 2007-05-11
I installed mythtv via synaptic on my ubuntu feisty fawn laptop.

I'm looking to use MythTV on Feisty here as a replacement for Media Center (Vista)
 
It is not detecting my Hauppauge HVR-950 USB tv tuner card.
 
I'm using this link
 [https://help.ubuntu.com/community/My...tend_Desktop_O]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O")
 
I tried mpeg-2 and DVR, both give the same error shown in screenshot.
 
[http://www.imagehost.ro/viewer.php?img=112131024644b6668131b](http://www.imagehost.ro/viewer.php?img=112131024644b6668131b)

Please assist.

Also, would I be able to use my Microsoft Media Center remote? If so, how would I program it?

---

### Post by newlinux on 2007-05-11
Did you:[LIST=1]
[*]Set the card type as DVB
[*]Define an video source (using a zap2it you already setup)
[*]Assign the video source you defined to the DVB card
[*]Scan for channels (QAM-256/cable-us or 8-VSB/Broadcast, depending on whether you are using cable or OTA ATSC with an antenna)
[/LIST]

What do you mean by "It is not detecting my Hauppauge HVR-950 USB tv tuner card"
What does setup screen where you are defining the cardtype look?

Make sure you follow the setup instructions in detail.
What type of channels are you trying to pick up? QAM? ATSC? NTSC?

Yes, you can use your MCE remote. I use a harmony universal emulating an MCE remote
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

---

