---
title: "How to install a Gadmei Utv330+ Usb Video Capture/Tv Tuner"
date: 2008-07-25
forum: Multimedia Software
---

### Post by michaelAust on 2008-07-25
This device is quite inexpensive (AUD$52 delivered, on ebay), and can be used to capture composite video and sound, eg. from vhs videotapes. It also has an analogue Tv tuner which I have not tried yet. I have been able to watch videotapes using xawtv, tvtime, zapping, etc. and record them using mencoder, both with quite decent quality. There is plenty of info on the web about the Gadmei utv330 and 310 but not about the 330+.I bought it after I found a page detailing a succesful installation
[http://hadiariawan.web.id/2008/01/12/patch-driver-tv-tuner-gadmei-330/](http://hadiariawan.web.id/2008/01/12/patch-driver-tv-tuner-gadmei-330/)
This page is in indonesian but it was not too hard to work out with the help of a web translation tool
[http://www.toggletext.com/](http://www.toggletext.com/)
The instructions from there did not work for me but adding a few bits and pieces from other places did the trick. It apparently contains an em2861 chip which is supported by the em28xx driver. I am using Kubuntu 8.04 Hardy.

Here is the result of lsusb showing the manufacturer/product id.

```
michael@AsusKubuntu:~$ lsusb
Bus 004 Device 005: ID eb1a:50a6 eMPIA Technology, Inc.
```

My process to install this device was as follows.

I used Adept (Can use Synaptic or sudo apt-get install PackageName on the command line.)
install the package mercurial
install the package linux-headers-$(uname -r) (May need the terminal for this one)
I have linux-source but I don't think I needed it.
install the package build-essential
install the package gcc
I think these packages are all you need.

Open a terminal so you can download the Video4Linux source to build the em28xx module and type

```
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-kernel/
```

I ended up with a folder called /home/michael/v4l-dvb-kernel (117 MB) containing all the source code.

In the indonesian page above he says do

```
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
```

But when I did this, if my dvb card was connected and I did "modprobe em28xx" I got errors. This doesn't happen with non experimental.

Within the v4l-dvb-kernel folder edit the file "linux/drivers/media/video/em28xx/em28xx.h" using kate or gedit etc.
Below the line

```
#define EM2882_BOARD_KWORLD_VS_DVBT		  61
```

add a new line

```
#define EM2861_BOARD_GADMEI_UTV330		  62

```
Now edit the file "linux/drivers/media/video/em28xx/em28xx-cards.c"

Search for "EM2860_BOARD_GADMEI_UTV330"

Copy the block starting from

```
	[EM2860_BOARD_GADMEI_UTV330] = {
```

up to the line before

```
	[EM2820_BOARD_GADMEI_UTV310] = {
```

and paste it where the block started so there are now two blocks the same.
Edit the second block as follows,
On the first line of the block replace

```
EM2860_BOARD_GADMEI_UTV330
```

with

```
EM2861_BOARD_GADMEI_UTV330
```

On the second line of the block add a plus sign to the end of the .name string to make

```
		.name         = "Gadmei UTV330+",
```

Now search for "0xa316", and after the line

```
	{ USB_DEVICE(0xeb1a, 0xa316), .driver_info = EM2883_BOARD_KWORLD_HYBRID_A316 },
```

add a new line

```
	{ USB_DEVICE(0xeb1a, 0x50a6), .driver_info = EM2861_BOARD_GADMEI_UTV330 },
```

This will cause the em28xx driver to be loaded when you plug it in (if it has a different lsusb id then put it in the above line). In the indonesian page above he says create the file /etc/modprobe.conf with "options em28xx card=62" in it but this was not necessary for me.

Now search for "EM2860_BOARD_GADMEI_UTV330" again, and below the line

```
		case EM2860_BOARD_GADMEI_UTV330:
```

add a new line

```
		case EM2861_BOARD_GADMEI_UTV330:
```

This is the code to turn on IR for the remote, which I have not tested.
Now search for "EM2860_BOARD_GADMEI_UTV330" again, and below the line

```
		case EM2860_BOARD_GADMEI_UTV330:
```

add a new line

```
		case EM2861_BOARD_GADMEI_UTV330:

```
This is the code to turn off IR for the remote, which I have not tested.

The next step is to compile and install. Open a terminal, cd to the folder v4l-dvb-kernel and type the commands as follows

```
cd v4l-dvb-kernel
make
sudo make install
```

There will be lots of output and it takes a while, I had some warnings but no errors.

You can now try

```
sudo modprobe em28xx
```

And hopefully get no errors

The next step is to restart and plug the Gadmei into a usb port, then try

```
dmesg

```
which should give something like

```
[  211.616025] usb 4-4: new high speed USB device using ehci_hcd and address 5
[  211.671736] usb 4-4: configuration #1 chosen from 1 choice
[  212.191972] Linux video capture interface: v2.00
[  212.239990] em28xx v4l2 driver version 0.0.1 loaded
[  212.240042] em28xx new video device (eb1a:50a6): interface 0, class 255
[  212.240049] em28xx: device is attached to a USB 2.0 bus
[  212.240053] em28xx: you're using the experimental/unstable tree from mcentral.de
[  212.240058] em28xx: there's also a stable tree available but which is limited to
[  212.240062] em28xx: linux <=2.6.19.2
[  212.240065] em28xx: it's fine to use this driver but keep in mind that it will move
[  212.240071] em28xx: to http://mcentral.de/hg/~mrec/v4l-dvb-kernel as soon as it's
[  212.240075] em28xx: proved to be stable
```

I'm not sure why it says "you're using the experimental/unstable tree" when I used
[http://mcentral.de/hg/~mrec/v4l-dvb-kernel/](http://mcentral.de/hg/~mrec/v4l-dvb-kernel/) and not [http://mcentral.de/hg/~mrec/v4l-dvb-experimental/](http://mcentral.de/hg/~mrec/v4l-dvb-experimental/)
But it works. It creates /dev/video0 for video input (or video1 etc. if video0 is used I think).

I can connect my vcr to the composite and audio inputs of the Gadmei and watch videos using TVtime, xawtv, and motv but I need to plug the cable from the line out on the Gadmei to the microphone input (line in did not work) of my soundcard as these programs cannot connect to the digital sound inputs (Apparently a later version of TVtime can). I had to turn on the microphone input and adjust the sound levels using kmix to get sound and no distortion. I was not able to record to the hard disc using any of these programs so I used mencoder as follows

```
mencoder -tv driver=v4l2:width=720:height=576:input=1:norm=PAL-DK:fps=25:adevice=/dev/audio1 tv:// -o OutputFile.avi -ovc lavc -oac mp3lame
```

This command gets the audio from dev/audio1 (can use /dev/dsp1 too) and you don't need the soundcard cable. Mencoder has a vast array of sometimes confusing options but once you find the command line that works you can just use the up arrow in the terminal and edit your last command.

Useful hints:
You can find out the settings of the device using v4lctl (part of xawtv) as follows:

```
michael@AsusKubuntu:~$ v4lctl -c /dev/video0 list
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | NTSC    | NTSC    | NTSC PAL-DK
input      | choice | Televis | Televis | Television Composite1 S-Video
audio mode | choice | mono    | mono    | mono stereo lang1 lang2
bright     | int    |       0 |       0 | range is -128 => 127
contrast   | int    |      16 |      16 | range is 0 => 31
color      | int    |      16 |      16 | range is 0 => 31
volume     | int    |      31 |      31 | range is 0 => 31
mute       | bool   | on      | on      |
Red chroma | int    |       0 |       0 | range is -128 => 127
Blue chrom | int    |       0 |       0 | range is -128 => 127
Gamma      | int    |      32 |      32 | range is 0 => 63

```
Also v4l2ucp is a useful graphical utility for setting volume, colour, etc. Tvtime, mencoder, and all the others mentioned seem to change some of these values when they start but you can still adjust just after you start a capture for example. The deb linked to from the v4l2ucp page did not install properly but I extracted the executable using ark and ran it in the home directory.

Many em28xx related posts that I found suggest installing a >2.6.24 patch, but you don't need to, it is in the v4l-dvb-kernel code already.

Good Luck.

---

### Post by SohailB on 2008-08-09
Thank you very much for the great guide.

> **michaelAust said:**
> 
In the indonesian page above he says create the file /etc/modprobe.conf with "options em28xx card=62" in it but this was not necessary for me.


 I needed that. It gave me the following error without that:
```

[   32.088632] em28xx #0: Your board has no eeprom inside it and thus can't
[   32.088634] em28xx #0: be autodetected.  Please pass card=<n> insmod option to
[   32.088635] em28xx #0: workaround that.  Redirect complaints to the vendor of
[   32.088636] em28xx #0: the TV card. Generic type will be used.
[   32.088637] em28xx #0: Best regards,
[   32.088638] em28xx #0:         -- tux
[   32.088640] em28xx #0: em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
[   32.088643] em28xx #0:     card=0 -> Generic EM2800 video grabber
[   32.088645] em28xx #0:     card=1 -> Generic EM2820 video grabber
[   32.088646] em28xx #0:     card=2 -> Generic EM2821 video grabber

...

[   32.088750] em28xx #0:     card=62 -> Gadmei UTV330+

```


Could it be because of the difference I have in the numbers lsusb gives me? It says:

```

Bus 002 Device 008: ID eb1a:2861 eMPIA Technology, Inc. 

```

---

### Post by michaelAust on 2008-08-13
No worries, 

did you put

```
	{ USB_DEVICE(0xeb1a, 0x2861), .driver_info = EM2861_BOARD_GADMEI_UTV330 },

```
instead of
```
	{ USB_DEVICE(0xeb1a, 0x50a6), .driver_info = EM2861_BOARD_GADMEI_UTV330 },
```

Mine has stopped being recognised, maybe a kernel upgrade or something ? I tried a new make and sudo make install but with no luck.

---

### Post by michaelAust on 2008-08-16
As I said above, it stopped being recognised, which meant that /dev/video0 was not created, therefore capture did not work.

I thought maybe the em28xx driver had been overwritten during a software upgrade so I did

```
apt-file search em28xx

```
and the relevant packages for my current kernel, containing em28xx.ko seemed to be linux-image-2.6.24-19-386, which was not installed, or linux-image-2.6.24-19-generic, which was installed.

The path where this file was installed was
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/em28xx/em28xx.ko

so I had a look there..

```
michael@AsusKubuntu:/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/em28xx$ ls -l
-rw-r--r-- 1 root root 61992 2008-07-12 15:32 em28xx.ko

```
and in the drectory /home/michael/v4l-dvb-kernel/v4l/ I found em28xx.ko, as follows

```
michael@AsusKubuntu:~/v4l-dvb-kernel/v4l$ ls -l em28xx.ko
-rw-r--r-- 1 michael michael 123852 2008-08-13 15:16 em28xx.ko

```
So the installed version was older and smaller than the version there (created by make above).

I tried running make again, and saw that it was entering the directory /lib/modules/2.6.24-18-generic/ instead of /lib/modules/2.6.24-19-generic/. When I ran sudo make install it put em28xx.ko in the 2.6.24-18-generic directory. So to use it I would have had to boot with the old kernel. I searched in /home/michael/v4l-dvb-kernel/v4l/ for files containing the string 2.6.24-18 and found the file /v4l/.version containing the string KERNELRELEASE:=2.6.24-18-generic. I had kept a copy of the unmodified v4l-dvb-kernel/ directory so I looked in there, and there was no /v4l/.version file.

So the first time I ran make it must have written the kernel version at that time in the /v4l/.version file, and when the kernel got upgraded make did not change it but kept using the old version number.

So the way to fix it was to make a new copy of the unmodified v4l-dvb-kernel/ directory and copy my modified em28xx-cards.c and em28xx.h into the v4l-dvb-kernel/linux/drivers/media/video/em28xx directory, overwriting the fles there. Then I ran make and sudo make install.

Voila ! It works again !

---

### Post by lihsus on 2008-09-22
thats a gr8 way making UTv330+ work in linux,
worked fine in mine too.. except one problem

i am having problem with audio,.. there is a separate line-out in my tv-card which shud me kept in mic-input of my laptop, but the tv card is not giving out any sound.. 

i have checked TV card in vista and it works fine, and mic in linux is also working fine

so basically the problem is .. no sound while watching TV in linux (kubuntu hardy)

i wud be thankful if u cud help

i already tried playing TV thru xawtv, tvtime and VLC..

---

### Post by lihsus on 2008-09-26
nevermind, i had been playing around with v4l2 source code little more... and found the solution for my audio problem.

here is what i did to make audio work:

in file em28xx-core.c
find "case EM2860_BOARD_GADMEI_UTV330:"
and add "case EM2861_BOARD_GADMEI_UTV330:" after above line.

again in file em28xx-video.c
find "case EM2860_BOARD_GADMEI_UTV330:"
and add "case EM2861_BOARD_GADMEI_UTV330:" after the line.

find "case EM2860_BOARD_GENERIC:"
and after the case block, paste this code.

```

case EM2861_BOARD_GENERIC:// block we are going to add
			{
				struct drequest_t gadmei_utv_330[]={
					{0x03,0x42,"\x00",0x10,1,0},
					{0x03,0x4a,"\x00",0x00,1,0},
					{0x03,0x60,"\x00",0x10,1,0},
					{0x03,0x66,"\x00",0x10,1,0},
					{0x03,0x68,"\x00",0x10,1,0},
					{0x03,0x86,"\x00",0x10,1,0},
					{0x03,0xa0,"\x00",0x00,1,0},
					{0x03,0xa2,"\x00",0x10,1,0},
					{0x03,0xc0,"\x00",0x00,1,0},
					{0x03,0xc2,"\x00",0x10,1,0},
				};
				struct drequest_t netgmbh_cam[]={
					//{0x02,0x48,"\x00",0x00,1,0},
					{0x03,0x5a,"\x00",0x00,1,0},
				};

				struct drequest_t typhoon_dvdmaker[]={
					{0x03,0x4a,"\x00",0x00,1,0},
				};

				for(i=0,rv=0;i<ARRAY_SIZE(gadmei_utv_330);i++){
					sendbuf=kmalloc(gadmei_utv_330[i].blen,GFP_KERNEL);
					memcpy(sendbuf, gadmei_utv_330[i].buffer, gadmei_utv_330[i].blen);
					ret = usb_control_msg(udev, usb_sndctrlpipe(udev, 0), gadmei_utv_330[i].brequest,
							USB_DIR_OUT | USB_TYPE_VENDOR | USB_RECIP_DEVICE,
							0x0000, gadmei_utv_330[i].index,sendbuf,gadmei_utv_330[i].blen,HZ);
					kfree(sendbuf);
					if(gadmei_utv_330[i].msecs)
						msleep(gadmei_utv_330[i].msecs);
					ret = usb_control_msg(udev, usb_rcvctrlpipe(udev, 0), 0x00,
							USB_DIR_IN | USB_TYPE_VENDOR | USB_RECIP_DEVICE,
							0x0000, 0x05, &buffer, 1, HZ);
					if(buffer!=gadmei_utv_330[i].retval){
						rv=1;
						break;
					}
				}
				if(rv==0){
					(*model)=EM2861_BOARD_GADMEI_UTV330; // only this line is changed
					return 0;
				}
				for(i=0,rv=0;i<ARRAY_SIZE(netgmbh_cam);i++){
					sendbuf=kmalloc(netgmbh_cam[i].blen,GFP_KERNEL);
					memcpy(sendbuf, netgmbh_cam[i].buffer, netgmbh_cam[i].blen);
					ret = usb_control_msg(udev, usb_sndctrlpipe(udev, 0), netgmbh_cam[i].brequest,
							USB_DIR_OUT | USB_TYPE_VENDOR | USB_RECIP_DEVICE,
							0x0000, netgmbh_cam[i].index,sendbuf,netgmbh_cam[i].blen,HZ);
					kfree(sendbuf);
					if(netgmbh_cam[i].msecs)
						msleep(netgmbh_cam[i].msecs);
					ret = usb_control_msg(udev, usb_rcvctrlpipe(udev, 0), 0x00,
							USB_DIR_IN | USB_TYPE_VENDOR | USB_RECIP_DEVICE,
							0x0000, 0x05, &buffer, 1, HZ);
					if(buffer!=netgmbh_cam[i].retval){
						rv=1;
						break;
					}
				}
				if(rv==0){
					(*model)=EM2860_BOARD_NETGMBH_CAM;
					return 0;
				}


				for(i=0,rv=0;i<ARRAY_SIZE(typhoon_dvdmaker);i++){
					sendbuf=kmalloc(typhoon_dvdmaker[i].blen,GFP_KERNEL);
					memcpy(sendbuf, typhoon_dvdmaker[i].buffer, typhoon_dvdmaker[i].blen);
					ret = usb_control_msg(udev, usb_sndctrlpipe(udev, 0), typhoon_dvdmaker[i].brequest,
							USB_DIR_OUT | USB_TYPE_VENDOR | USB_RECIP_DEVICE,
							0x0000, typhoon_dvdmaker[i].index,sendbuf,typhoon_dvdmaker[i].blen,HZ);
					kfree(sendbuf);
					if(typhoon_dvdmaker[i].msecs)
						msleep(typhoon_dvdmaker[i].msecs);
					ret = usb_control_msg(udev, usb_rcvctrlpipe(udev, 0), 0x00,
							USB_DIR_IN | USB_TYPE_VENDOR | USB_RECIP_DEVICE,
							0x0000, 0x05, &buffer, 1, HZ);
					if(buffer!=typhoon_dvdmaker[i].retval){
						rv=1;
						break;
					}
				}
				if(rv==0){
					(*model)=EM2860_BOARD_TYPHOON_DVD_MAKER;
					return 0;
				}
			}
			break;

```

then recompile
"make"
"sudo make install"
"sudo modprobe em28xx"
and restart
then u are ready to go :)

---

### Post by budi_indira on 2009-02-24
Hey all,
I've bought this Tuner about a week ago. But 'till now, I can't installing the driver on my Ubuntu Intrepid, with kernel 2.6.27-9.
I've followed the instruction above, but the error still comes.. T,T

When I run command :
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel/](http://mcentral.de/hg/~mrec/v4l-dvb-kernel/)
it's done with no error, but the directory were only 4.3 MB (not 117MB)


I've download the v4l-dvb-experimental.tar.bz2 from [here]("http://www.makomk.com/%7Eaidan/v4l-dvb-experimental.tar.bz2"), then edit the config file (em28xx.c, etc).
When I run the 'make' command, here the result :

make -C /home/budi/app_temp/gadmei/v4l-dvb-experimental /v4l 
make: *** /home/budi/app_temp/gadmei/v4l-dvb-experimental: No such file or directory.  Stop.
make: *** [all] Error 2

--------------------------------------------------------------------------
Then, if I Patch it with [this]("http://mcentral.de/pipermail/em28xx/attachments/20080402/b43e9afe/v4l-dvb-kernel-Makefile-2.6.24.obj") Patch file and then re-run the 'make' command, it gives this :

make -C /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l 
make[1]: Entering directory `/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l'
creating symbolic links...
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.o
In file included from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-common.h:29,
                 from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttvp.h:37,
                 from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:41:
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h:365: error: field 'class_dev' has incomplete type
In file included from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-common.h:29,
                 from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttvp.h:37,
                 from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:41:
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h:394: warning: 'struct class_device_attribute' declared inside parameter list
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h:394: warning: its scope is only this definition or declaration, which is probably not what you want
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h: In function 'video_device_create_file':
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h:396: error: implicit declaration of function 'class_device_create_file'
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h: At top level:
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h:403: warning: 'struct class_device_attribute' declared inside parameter list
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h: In function 'video_device_remove_file':
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/../linux/include/media/v4l2-dev.h:405: error: implicit declaration of function 'class_device_remove_file'
In file included from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:41:
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:32:
include/linux/kernel.h:376:1: warning: this is the location of the previous definition
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c: In function 'show_card':
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:172: warning: type defaults to 'int' in declaration of '__mptr'
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:172: warning: initialization from incompatible pointer type
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c: At top level:
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:176: error: expected ')' before '(' token
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c: In function 'bttv_register_video':
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:4637: error: 'class_device_attr_card' undeclared (first use in this function)
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:4637: error: (Each undeclared identifier is reported only once
/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.c:4637: error: for each function it appears in.)
make[3]: *** [/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/budi/app_temp/gadmei/v4l-dvb-experimental2/v4l'
make: *** [all] Error 2
-------------------------------------------------------------------------

I don't know what exactly happens :cry:
Someone Help Me PLISSS !!:cry:

Thx before.

---

### Post by michaelAust on 2009-03-12
> Hey all,
I've bought this Tuner about a week ago. But 'till now, I can't installing the driver on my Ubuntu Intrepid, with kernel 2.6.27-9.
I've followed the instruction above, but the error still comes.. T,T

I haven't tried it in Intrepid, only Hardy.
> When I run command :
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel/](http://mcentral.de/hg/~mrec/v4l-dvb-kernel/)
it's done with no error, but the directory were only 4.3 MB (not 117MB)

My mistake I think, 117MB was probably the size after the make, it got much larger.
> When I run the 'make' command, here the result :

make -C /home/budi/app_temp/gadmei/v4l-dvb-experimental /v4l
make: *** /home/budi/app_temp/gadmei/v4l-dvb-experimental: No such file or directory. Stop.
make: *** [all] Error 2

There is a space between "...experimental" and "/v4l". Maybe that is a problem, but I presume the directory /home/budi/app_temp/gadmei/v4l-dvb-experimental does exist if the directory v4l is in it so the error message is hard to understand.

As I said, experimental caused problems but I think make ran ok. You ran make differently but I don't know enough about it to know if that matters. I suppose the mcentral.de code may have changed, I haven't done it for a while.

Sorry I couldn't be more helpful,
Hope you can sort it out.

---

### Post by baucha_linux on 2009-11-10
Has anyone been able to make it work in Kubuntu Karmic??

---

### Post by triastanto on 2010-05-23
> **baucha_linux said:**
> Has anyone been able to make it work in Kubuntu Karmic??

I did it on Ubuntu Karmic.
Here some tutorial I've found:
[HTML]http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+9.10
[/HTML][HTML]http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers
[/HTML]if needed use this firmware:
[HTML]http://konstantin.filtschew.de/v4l-firmware/[/HTML]
While building, error may occur, use this tutorial:
[HTML]http://ubuntuforums.org/showthread.php?t=1305228[/HTML]

---

