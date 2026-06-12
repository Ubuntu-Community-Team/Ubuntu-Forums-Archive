---
title: "DVBSky DVB-S/S2 and T/T2 PCIe Card - can not install"
date: 2014-07-06
forum: Multimedia Software
---

### Post by Jonners59 on 2014-07-06
I have installed a SkyDVB Tv/Satelite PCI card and am having trouble getting it to work.  The instructions and drivers that come with the card do not work, and neither do those on the Sky website.

I have found some commands to install the drivers at the [LinuxTv website]("http://www.linuxtv.org/wiki/index.php/DVBSky")  , but I get stuck part way through.  I am not sure how to interperate the instructions.  I did make the card work, but unfortunatly I am not sure what I did and the PC crashed within hours and I have only just rebuilt it.  The instructions are:

   

 # Start terminal (or press Strg+Alt+F1, back to Desktop: Strg+Alt+F7)
 # Login as root and update your system  
 ```
 sudo su

  apt-get update
  apt-get upgrade

``` 

 # Install required build tools
 ```
 apt-get install kernel-package linux-headers-`uname -r`


``` 

 # Download DVBSky Media build package (see: [http://www.dvbsky.net/Support.html](http://www.dvbsky.net/Support.html))
 ```
 cd /usr/src

  wget http://www.dvbsky.net/download/linux/media_build-bst-140128.tar.gz
  tar xf media_build-bst-140128.tar.gz

```  

 # Enter package
 ```
 cd media_build-bst


``` 

 # Run `uname -a` to determine if 32 or 64-bit (x86_64/amd64/ia64) is required.
 ```
 uname -a


``` 
***This is where I get lost.  I know I want ```
 ./v4l/build_x64.sh
``` but how do I type this instruction?***


 # `build_x86.sh` for any 32-bit system with DVB-S/S2/T/T2  =	 ./v4l/build_x86.sh
 # OR
 # `build_dvbc_x86.sh` for DVB-S/S2/C driver  =			./v4l/build_dvbc_x86.sh
 # OR
 # `build_x64.sh` for any 64-bit system with DVB-S/S2/T/T2  =	./v4l/build_x64.sh

 # OR
 # `build_dvbc_x64.sh` for DVB-S/S2/C driver  =			./v4l/build_dvbc_x64.sh
 

 ```
 make && make install


``` 

 # Download and install firmware
 ```
 cd /usr/src

  wget http://www.dvbsky.net/download/dvbsky-firmware.zip
  unzip dvbsky-firmware.zip
  sh ./bst-firmware.sh

``` 

 # Reboot and check DVB devices
 ```
 reboot

  ls /dev/dvb
  dmesg | grep -i dvb

``` 

 

 Anyone help, please?

---

### Post by Bashing-om on 2014-07-06
Jonners59; Wow,

I checked, and looks like these people keep their software up to date to support ubuntu and the latest releases too ! (do check again that you have the correct file for trusty's kernel -3.13-)

OK, in response to your question:
> 
This is where I get lost. I know I want
Code:
 ./v4l/build_x64.sh


Wherever you chose to untar the tarball the file 'v4l/build_x64.sh' should exist.
Change Directory (cd) to where it was extracted;
make sure the file is marked as executable:
```

ls -la
sudo chmod +x <file_name>

```
now the leading './' is a path, that says this path right here - so you have to be in the directory that the file is located in. 
execute the file then with just entering the complete command:
```

./v4l/build_x64.sh

```
That should execute, but but, no guarantee as to what results, ain't been there, ain't done that.

Not in the ubuntu repository ->
[INDENT][INDENT]user be wary[/INDENT][/INDENT]

[INDENT][INDENT][INDENT]hey, just my bit to try and help
[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2014-07-06
Cheers Bashin-om
I think I understand what you are saying, so will have another look tomorrow evening and if it makes sense to me will give it another go.

This is the latest and I did get it to work, my fear is that it may have been the cause of the crash too!  I am particularly wary as it is storred in the same location as the kernel.

Fingers crossed.

Good night

---

### Post by Jonners59 on 2014-07-08
So if I have this correct, the .sh file should be in "/v4l/" which if extracted in "/usr/src/media_build-bst" and is marked "Exacutabe" then would this command work?

```
 cd /usr/src/media_build-bst/
``` followed by ```
./v4l/build_x64.sh make && make install
```

or

```
 cd /usr/src/media_build-bst/v4l/
```  followed by ```
build_x64.sh  make && make install
```

or

 ```
 cd /usr/src/media_build-bst/v4l/  &&  build_x64.sh  make && make install
```

---

### Post by Bashing-om on 2014-07-08
Jonners59; It all depends.

What has the programmer/packager done ? Maybe the binary is supplied, thus compilation is not required.

When you extracted the tar ball, SOP is a "readme" file provided by the programmer to be present.

[INDENT][INDENT]what does the author advise for installation in that "readme" ?
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2014-07-08
I'll get back as soon as I can get the wife of the telly, if not too late...  She's watching the worldcup!

From memory, though, the enclosed information was poor and did not work at all.   The one i found on the LinuxTv thread I got to work before the PC crashed, but can not recall how I managed it.

The instuctions/commands are as below
cd /usr/src and download and extract file here...
cd media_build-bst go in to the extracted file
then the bit i do not understand, something to do with ./v4l/build_x64.sh
then
make && make install

---

### Post by Bashing-om on 2014-07-08
Jonners59; Well.

Like this, in the present circumstances we do not know what the author has provided. But, make and make install are to compile from source code and yes, must be in the same directory as the source code for the commands as given to take effect.
Again, there should be included instructions that would be much more to the point than any other directions.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2014-07-09
From the READ file
[PHP]Usage:
Just call the build utility:    $ ./build
Then, install the drivers as root, with:    # make install
[/PHP]

From the install pdf
[PHP]2,2,Compile1)Enter the source code directory, then change the read/write permissions:media_build-bstcd /home/DVBSky//home/DVBSky/media_build-bst2)Check and choose one of the target systems, run ‘uname -a’ to get os informaton../v4l/build_x86.sh if build for 32 bit system os../v4l/build_dvbc_x86.sh if build for 32 bit system os to support DVB-C../v4l/build_x64.sh if build for 64 bit system os../v4l/build_dvb_cx64.sh if build for 64 bit system os to support DVB-C.3)Compile the source code:make4)Install driver, which need super user privilege:sudo make install5)Copy firmware file dvb-fe-ds3000.fw to /Lib/Firmware directory.Firmware file can be downloaded from support web page in www.dvbsky.net. Unzipit then copy.6)Reboot computer.7)Verify the installation is successful or not:ls /dev/dvbIf the adaptor0 is list here so the driver is installed properly[/PHP]

But when I try this ```
ls /dev/dvb
```  it says it does not exist and if I create it and then try again, it deletes the directory I have made, so I get the same answer, does not exist...

```
dmesg | grep -i dvb
``` says nothing......, blank

---

### Post by Bashing-om on 2014-07-09
Jonners59; Humm ..

Where did you download the application to ? One must be in that location as the Present Working Directory to target the files.
So, let's see if we can find where that location is:
```

sudo find / -name media_build-bstcd

```
as that is the 1st step - to change the permissions on the build file -, then find the install files and do the make commands.
Then do a 'ls' there to see that the required files are present to effect the 'make'.

[INDENT]no step for a stepper.
[INDENT][INDENT][INDENT]but, we gotta do the steps
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2014-07-09
Thanks Basshin-om
It should be in /usr/src/ .  when I navigate there I can see it and [FONT=Ubuntu Mono][COLOR=#000000]build_x64.sh is executable according to permissions.  I note it is owned by me and not root, if that is significant... however, running the cmd [/COLOR][/FONT]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo find / -name media_build-bstcd [/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]you sent me yields nothing....[/FONT]

[FONT=Ubuntu Mono]Just realised a typo in what you sent me...  If I type [/FONT][/COLOR]```
sudo find / -name media_build-bst
``` I get the correct location ```
 /usr/src/media_build-bst
```  phew

If I then go in to the directory and run the list cmd you sent before, I get...
```
/usr/src/media_build-bst$ ls -la
total 1108
drwxrwxr-x 7 mediaserver mediaserver   4096 Jan 28 03:06 .
drwxr-xr-x 9 root        root          4096 Jul  9 06:34 ..
drwxrwxr-x 2 mediaserver mediaserver   4096 Jul  9 06:34 backports
-rwxrwxr-x 1 mediaserver mediaserver  15312 Jan 28  2013 build
-rw-rw-r-- 1 mediaserver mediaserver  18011 Jan 28  2013 COPYING
drwxrwxr-x 2 mediaserver mediaserver   4096 Jul  9 06:34 devel_scripts
-rw-rw-r-- 1 mediaserver mediaserver 649441 Sep  5  2011 dvb-firmwares.tar.bz2
drwxrwxr-x 8 mediaserver mediaserver   4096 Jul  9 06:34 .git
-rw-rw-r-- 1 mediaserver mediaserver     13 Jan 28  2013 .gitignore
-rw-rw-r-- 1 mediaserver mediaserver   4243 Jan 28  2013 INSTALL
drwxrwxr-x 6 mediaserver mediaserver   4096 Jul  9 06:34 linux
-rw-rw-r-- 1 mediaserver mediaserver  96162 May 20  2013 Linux_Driver_installation_en.pdf
-rw-rw-r-- 1 mediaserver mediaserver    547 Jan 28  2013 Makefile
-rw-rw-r-- 1 mediaserver mediaserver     41 Feb 14  2013 Notes
-rw-rw-r-- 1 mediaserver mediaserver   1130 Jan 28  2013 README
-rw-rw-r-- 1 mediaserver mediaserver  50682 Jan 28  2013 README.patches
drwxrwxr-x 5 mediaserver mediaserver 241664 Jul  9 06:45 v4l
```

I then made the file owned by root....

cd back and followed the actions below, agin.

Output = 
[HTML]  LD [M]  /usr/src/media_build-bst/v4l/gspca_ov534.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_ov534_9.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_pac207.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_pac7302.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_pac7311.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_se401.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sn9c2028.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sn9c20x.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sonixb.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sonixj.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_spca1528.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_spca500.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_spca501.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_spca505.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_spca506.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_spca508.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_spca561.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sq905.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sq905c.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sq930x.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_stk014.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_stv0680.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_stv06xx.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_sunplus.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_t613.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_topro.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_tv8532.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_vc032x.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_vicam.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_xirlink_cit.ko  LD [M]  /usr/src/media_build-bst/v4l/gspca_zc3xx.ko  LD [M]  /usr/src/media_build-bst/v4l/hdpvr.ko  LD [M]  /usr/src/media_build-bst/v4l/hopper.ko  LD [M]  /usr/src/media_build-bst/v4l/ivtv-alsa.ko  LD [M]  /usr/src/media_build-bst/v4l/ivtv.ko  LD [M]  /usr/src/media_build-bst/v4l/mantis.ko  LD [M]  /usr/src/media_build-bst/v4l/mantis_core.ko  LD [M]  /usr/src/media_build-bst/v4l/msp3400.ko  LD [M]  /usr/src/media_build-bst/v4l/ngene.ko  LD [M]  /usr/src/media_build-bst/v4l/poseidon.ko  LD [M]  /usr/src/media_build-bst/v4l/pvrusb2.ko  LD [M]  /usr/src/media_build-bst/v4l/pwc.ko  LD [M]  /usr/src/media_build-bst/v4l/radio-usb-si470x.ko  LD [M]  /usr/src/media_build-bst/v4l/rc-core.ko  LD [M]  /usr/src/media_build-bst/v4l/saa7134.ko  LD [M]  /usr/src/media_build-bst/v4l/saa7146.ko  LD [M]  /usr/src/media_build-bst/v4l/saa7146_vv.ko  LD [M]  /usr/src/media_build-bst/v4l/saa7164.ko  LD [M]  /usr/src/media_build-bst/v4l/shark2.ko  LD [M]  /usr/src/media_build-bst/v4l/sit2fe.ko  LD [M]  /usr/src/media_build-bst/v4l/smsmdtv.ko  LD [M]  /usr/src/media_build-bst/v4l/sn9c102.ko  LD [M]  /usr/src/media_build-bst/v4l/snd-bt87x.ko  LD [M]  /usr/src/media_build-bst/v4l/stb0899.ko  LD [M]  /usr/src/media_build-bst/v4l/stk1160.ko  LD [M]  /usr/src/media_build-bst/v4l/stkwebcam.ko  LD [M]  /usr/src/media_build-bst/v4l/stv0900.ko  LD [M]  /usr/src/media_build-bst/v4l/tda18271.ko  LD [M]  /usr/src/media_build-bst/v4l/tm6000.ko  LD [M]  /usr/src/media_build-bst/v4l/tuner.ko  LD [M]  /usr/src/media_build-bst/v4l/usbvision.ko  LD [M]  /usr/src/media_build-bst/v4l/uvcvideo.ko  LD [M]  /usr/src/media_build-bst/v4l/videodev.ko  LD [M]  /usr/src/media_build-bst/v4l/zr36067.komake[2]: Leaving directory `/usr/src/linux-headers-3.13.0-30-generic'./scripts/rmmod.pl checkmake[1]: Leaving directory `/usr/src/media_build-bst/v4l'make -C /usr/src/media_build-bst/v4l installmake[1]: Entering directory `/usr/src/media_build-bst/v4l'
Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/saa7134:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/marvell-ccic:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ttusb-budget:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/dm1105:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/pt1:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/frontends:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/tlg2300:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/uvc:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/siano:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/mantis:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ddbridge:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx231xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/zoran:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ngene:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/firewire:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/bt8xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/pluto2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/bt8xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/dvb-core:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx18:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/hdpvr:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca/stv06xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/usbvision:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca/m5602:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/common/tuners:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ttpci:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/common:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/tm6000:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx88:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/saa7164:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/dvb-usb:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca/gl860:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx25821:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/b2c2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ttusb-dec:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx25840:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx23885:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/ivtv:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/pvrusb2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/sn9c102:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cpia2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/au0828:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/em28xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/pwc:
Installing kernel modules under /lib/modules/3.13.0-30-generic/kernel/drivers/media/:    usb/cpia2/: cpia2.ko     usb/cx231xx/: cx231xx-alsa.ko cx231xx.ko cx231xx-dvb.ko     i2c/: tveeprom.ko cx2341x.ko bt856.ko         tda7432.ko ak881x.ko tcm825x.ko         ir-kbd-i2c.ko adv7180.ko adv7175.ko         cs5345.ko ths7303.ko adv7183.ko         msp3400.ko adv7343.ko ov7670.ko         vpx3220.ko ks0127.ko upd64031a.ko         tvaudio.ko wm8739.ko tvp514x.ko         saa6588.ko upd64083.ko tvp5150.ko         cs53l32a.ko vs6624.ko saa7191.ko         btcx-risc.ko saa7110.ko adv7393.ko         sr030pc30.ko saa717x.ko adv7170.ko         saa7127.ko aptina-pll.ko tda9840.ko         saa7115.ko tlv320aic23b.ko tvp7002.ko         bt819.ko tea6420.ko saa7185.ko         tea6415c.ko smiapp-pll.ko vp27smpx.ko         bt866.ko mt9v011.ko wm8775.ko         m52790.ko     pci/dm1105/: dm1105.ko     pci/zoran/: zr36016.ko zr36050.ko videocodec.ko         zr36060.ko zr36067.ko     usb/gspca/: gspca_etoms.ko gspca_ov534_9.ko gspca_pac7311.ko         gspca_kinect.ko gspca_benq.ko gspca_sonixb.ko         gspca_sunplus.ko gspca_sonixj.ko gspca_spca561.ko         gspca_sq905c.ko gspca_sn9c2028.ko gspca_stk014.ko         gspca_mr97310a.ko gspca_main.ko gspca_pac207.ko         gspca_mars.ko gspca_topro.ko gspca_se401.ko         gspca_ov519.ko gspca_jl2005bcd.ko gspca_spca506.ko         gspca_sq930x.ko gspca_sn9c20x.ko gspca_finepix.ko         gspca_tv8532.ko gspca_nw80x.ko gspca_konica.ko         gspca_conex.ko gspca_ov534.ko gspca_spca1528.ko         gspca_spca500.ko gspca_spca508.ko gspca_cpia1.ko         gspca_jeilinj.ko gspca_pac7302.ko gspca_spca501.ko         gspca_t613.ko gspca_vicam.ko gspca_sq905.ko         gspca_stv0680.ko gspca_zc3xx.ko gspca_vc032x.ko         gspca_xirlink_cit.ko gspca_spca505.ko     pci/saa7146/: hexium_gemini.ko mxb.ko hexium_orion.ko     pci/ddbridge/: ddbridge.ko     pci/cx25821/: cx25821.ko     pci/ivtv/: ivtv-alsa.ko ivtv.ko ivtvfb.ko     common/siano/: smsdvb.ko smsmdtv.ko     usb/uvc/: uvcvideo.ko     dvb-core/: dvb-core.ko     pci/cx88/: cx88-dvb.ko cx88-blackbird.ko cx88-alsa.ko         cx8800.ko cx88xx.ko cx88-vp3054-i2c.ko         cx8802.ko     pci/ttpci/: ttpci-eeprom.ko budget-av.ko budget-core.ko         dvb-ttpci.ko budget.ko budget-ci.ko         budget-patch.ko     pci/cx23885/: cx23885.ko altera-ci.ko     pci/cx18/: cx18-alsa.ko cx18.ko     parport/: bw-qcam.ko w9966.ko c-qcam.ko     radio/si470x/: radio-usb-si470x.ko     tuners/: tua9001.ko fc0011.ko tda9887.ko         mxl5007t.ko tda18271.ko tuner-types.ko         tea5767.ko fc0012.ko tea5761.ko         tda18218.ko tuner-xc2028.ko mt2063.ko         tuner-simple.ko mt2060.ko mc44s803.ko         mxl5005s.ko tda18212.ko max2165.ko         tda827x.ko xc5000.ko fc0013.ko         fc2580.ko mt2131.ko tda8290.ko         e4000.ko xc4000.ko mt20xx.ko         qt1010.ko mt2266.ko     radio/: shark2.ko saa7706h.ko radio-tea5764.ko         radio-mr800.ko radio-keene.ko radio-timb.ko         radio-maxiradio.ko radio-shark.ko radio-si4713.ko         dsbr100.ko tef6862.ko radio-ma901.ko         si4713-i2c.ko radio-wl1273.ko     pci/pt1/: earth-pt1.ko     usb/au0828/: au0828.ko     usb/stkwebcam/: stkwebcam.ko     common/saa7146/: saa7146_vv.ko saa7146.ko     pci/pluto2/: pluto2.ko     usb/dvb-usb-v2/: dvb-usb-ec168.ko dvb-usb-af9015.ko dvb-usb-az6007.ko         mxl111sf-tuner.ko dvb-usb-it913x.ko dvb_usb_cypress_firmware.ko         dvb-usb-mxl111sf.ko mxl111sf-demod.ko dvb-usb-af9035.ko         dvb-usb-anysee.ko dvb-usb-dvbsky.ko dvb-usb-lmedm04.ko         dvb-usb-ce6230.ko dvb-usb-gl861.ko dvb-usb-au6610.ko         dvb_usb_v2.ko     dvb-frontends/: stv0288.ko zl10353.ko cx24110.ko         zl10039.ko lgs8gxx.ko rtl2830.ko         lgs8gl5.ko au8522_common.ko bcm3510.ko         stv6110x.ko dibx000_common.ko rtl2832.ko         or51211.ko dib0070.ko stv090x.ko         s5h1420.ko tda826x.ko m88rs2000.ko         isl6423.ko stv6110.ko stv0299.ko         dib8000.ko or51132.ko cx24116.ko         mb86a20s.ko cxd2820r.ko cx24123.ko         drxk.ko mb86a16.ko stb0899.ko         isl6421.ko dib7000m.ko lgdt330x.ko         sp887x.ko cx24113.ko dvb_dummy_fe.ko         tda10021.ko tda18271c2dd.ko tda10086.ko         sp8870.ko mt352.ko af9013.ko         lgdt3305.ko nxt6000.ko drxd.ko         tda665x.ko m88dc2800.ko dib0090.ko         hd29l2.ko stv0900.ko tda10048.ko         lg2160.ko atbm8830.ko a8293.ko         tda10023.ko l64781.ko cx22702.ko         s5h1432.ko stb6100.ko ec100.ko         dvb-pll.ko lnbp21.ko ves1820.ko         ves1x93.ko lnbp22.ko cx22700.ko         s5h1411.ko isl6405.ko nxt200x.ko         s5h1409.ko tda1004x.ko ix2505v.ko         it913x-fe.ko stb6000.ko dib7000p.ko         stv0367.ko tua6100.ko sit2fe.ko         dib3000mc.ko itd1000.ko si21xx.ko         tda8261.ko af9033.ko tda8083.ko         au8522_dig.ko dib3000mb.ko m88ds3103.ko         stv0297.ko mt312.ko zl10036.ko         tda10071.ko s921.ko dib9000.ko         ds3000.ko au8522_decoder.ko     usb/stk1160/: stk1160.ko     usb/s2255/: s2255drv.ko     pci/mantis/: mantis_core.ko mantis.ko hopper.ko     pci/ngene/: ngene.ko     usb/dvb-usb/: dvb-usb-technisat-usb2.ko dvb-usb-umt-010.ko dvb-usb-opera.ko         dvb-usb-az6027.ko dvb-usb-dibusb-common.ko dvb-usb-m920x.ko         dvb-usb-digitv.ko dvb-usb-dib0700.ko dvb-usb-dibusb-mb.ko         dvb-usb-vp7045.ko dvb-usb-cxusb.ko dvb-usb.ko         dvb-usb-nova-t-usb2.ko dvb-usb-af9005-remote.ko dvb-usb-gp8psk.ko         dvb-usb-dtt200u.ko dvb-usb-dtv5100.ko dvb-usb-vp702x.ko         dvb-usb-pctv452e.ko dvb-usb-a800.ko dvb-usb-af9005.ko         dvb-usb-cinergyT2.ko dvb-usb-friio.ko dvb-usb-ttusb2.ko         dvb-usb-dw2102.ko dvb-usb-dibusb-mc.ko     ../linux/drivers/misc/altera-stapl/: altera-stapl.ko     pci/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134.ko         saa7134-alsa.ko saa7134-dvb.ko     usb/hdpvr/: hdpvr.ko     usb/em28xx/: em28xx.ko em28xx-dvb.ko em28xx-alsa.ko         em28xx-rc.ko     usb/ttusb-dec/: ttusb_dec.ko ttusbdecfe.ko     common/b2c2/: b2c2-flexcop.ko     usb/siano/: smsusb.ko     firewire/: firedtv.ko     i2c/soc_camera/: mt9t031.ko mt9m001.ko ov5642.ko         ov2640.ko rj54n1cb0c.ko mt9m111.ko         imx074.ko mt9t112.ko ov9740.ko         mt9v022.ko ov6650.ko ov772x.ko         ov9640.ko tw9910.ko     usb/gspca/m5602/: gspca_m5602.ko     pci/bt8xx/: bt878.ko bttv.ko dst.ko         dvb-bt8xx.ko dst_ca.ko     mmc/siano/: smssdio.ko     radio/wl128x/: fm_drv.ko     usb/gspca/stv06xx/: gspca_stv06xx.ko     platform/soc_camera/: soc_mediabus.ko sh_mobile_csi2.ko sh_mobile_ceu_camera.ko         soc_camera_platform.ko soc_camera.ko     usb/tm6000/: tm6000.ko tm6000-alsa.ko tm6000-dvb.ko     pci/b2c2/: b2c2-flexcop-pci.ko     usb/pwc/: pwc.ko     usb/sn9c102/: sn9c102.ko     usb/usbvision/: usbvision.ko     platform/marvell-ccic/: cafe_ccic.ko     pci/saa7164/: saa7164.ko     usb/ttusb-budget/: dvb-ttusb-budget.ko     i2c/cx25840/: cx25840.ko     rc/: ir-nec-decoder.ko ir-sony-decoder.ko ir-sanyo-decoder.ko         rc-loopback.ko ir-rc5-sz-decoder.ko ati_remote.ko         mceusb.ko lirc_dev.ko gpio-ir-recv.ko         ir-mce_kbd-decoder.ko imon.ko fintek-cir.ko         ir-jvc-decoder.ko ir-rc6-decoder.ko ite-cir.ko         ir-rc5-decoder.ko streamzap.ko ttusbir.ko         nuvoton-cir.ko ir-lirc-codec.ko ene_ir.ko         rc-core.ko winbond-cir.ko redrat3.ko         iguanair.ko     usb/zr364xx/: zr364xx.ko     usb/tlg2300/: poseidon.ko     v4l2-core/: videobuf-dvb.ko videobuf2-dma-contig.ko videobuf-core.ko         videobuf2-vmalloc.ko videobuf2-memops.ko tuner.ko         videobuf-dma-contig.ko v4l2-mem2mem.ko videobuf2-dma-sg.ko         v4l2-common.ko videobuf-vmalloc.ko videodev.ko         videobuf-dma-sg.ko videobuf2-core.ko v4l2-int-device.ko     usb/pvrusb2/: pvrusb2.ko     usb/gspca/gl860/: gspca_gl860.ko     rc/keymaps/: rc-terratec-cinergy-xs.ko rc-medion-x10-digitainer.ko rc-dm1105-nec.ko         rc-pixelview.ko rc-tt-1500.ko rc-terratec-slim-2.ko         rc-tivo.ko rc-videomate-tv-pvr.ko rc-asus-pc39.ko         rc-gadmei-rm008z.ko rc-avermedia-m135a.ko rc-imon-pad.ko         rc-flydvb.ko rc-winfast.ko rc-dntv-live-dvb-t.ko         rc-encore-enltv2.ko rc-streamzap.ko rc-it913x-v2.ko         rc-eztv.ko rc-rc6-mce.ko rc-ati-tv-wonder-hd-600.ko         rc-powercolor-real-angel.ko rc-imon-mce.ko rc-leadtek-y04g0051.ko         rc-pixelview-002t.ko rc-avermedia.ko rc-hauppauge.ko         rc-anysee.ko rc-azurewave-ad-tu700.ko rc-ati-x10.ko         rc-genius-tvgo-a11mce.ko rc-pixelview-new.ko rc-lme2510.ko         rc-terratec-slim.ko rc-gotview7135.ko rc-digitalnow-tinytwin.ko         rc-pinnacle-color.ko rc-manli.ko rc-total-media-in-hand.ko         rc-kworld-315u.ko rc-technisat-usb2.ko rc-nec-terratec-cinergy-xs.ko         rc-kworld-pc150u.ko rc-digittrade.ko rc-dib0700-nec.ko         rc-adstech-dvb-t-pci.ko rc-tevii-nec.ko rc-dvbsky.ko         rc-pinnacle-grey.ko rc-cinergy-1400.ko rc-fusionhdtv-mce.ko         rc-npgtech.ko rc-winfast-usbii-deluxe.ko rc-avermedia-a16d.ko         rc-trekstor.ko rc-evga-indtube.ko rc-lirc.ko         rc-avermedia-dvbt.ko rc-medion-x10-or2x.ko rc-pv951.ko         rc-avertv-303.ko rc-snapstream-firefly.ko rc-cinergy.ko         rc-pixelview-mk12.ko rc-behold.ko rc-flyvideo.ko         rc-em-terratec.ko rc-msi-digivox-ii.ko rc-purpletv.ko         rc-twinhan1027.ko rc-videomate-s350.ko rc-kworld-plus-tv-analog.ko         rc-iodata-bctv7e.ko rc-dib0700-rc5.ko rc-nebula.ko         rc-videomate-m1f.ko rc-total-media-in-hand-02.ko rc-msi-tvanywhere-plus.ko         rc-proteus-2309.ko rc-msi-digivox-iii.ko rc-avermedia-rm-ks.ko         rc-budget-ci-old.ko rc-avermedia-cardbus.ko rc-tbs-nec.ko         rc-asus-ps3-100.ko rc-medion-x10.ko rc-alink-dtu-m.ko         rc-it913x-v1.ko rc-norwood.ko rc-apac-viewcomp.ko         rc-pinnacle-pctv-hd.ko rc-real-audio-220-32-keys.ko rc-behold-columbus.ko         rc-dntv-live-dvbt-pro.ko rc-kaiomy.ko rc-pctv-sedna.ko         rc-encore-enltv-fm53.ko rc-avermedia-m733a-rm-k6.ko rc-msi-tvanywhere.ko         rc-encore-enltv.ko     platform/: mem2mem_testdev.ko m2m-deinterlace.ko sh_veu.ko         via-camera.ko vivi.ko timblogiw.ko     usb/b2c2/: b2c2-flexcop-usb.ko     pci/meye/: meye.ko /sbin/depmod -a 3.13.0-30-generic make -C firmware installmake[2]: Entering directory `/usr/src/media_build-bst/v4l/firmware'Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw cp: cannot stat 'dabusb/firmware.fw': No such file or directorydabusb/bitstream.bin cp: cannot stat 'dabusb/bitstream.bin': No such file or directoryttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin dvb-fe-bcm3510-01.fw dvb-fe-or51132-qam.fw dvb-fe-or51132-vsb.fw dvb-fe-or51211.fw dvb-fe-xc5000-1.6.114.fw dvb-ttpci-01.fw-261a dvb-ttpci-01.fw-261b dvb-ttpci-01.fw-261c dvb-ttpci-01.fw-261d dvb-ttpci-01.fw-261f dvb-ttpci-01.fw-2622 dvb-usb-avertv-a800-02.fw dvb-usb-bluebird-01.fw dvb-usb-dib0700-1.20.fw dvb-usb-dibusb-5.0.0.11.fw dvb-usb-dibusb-6.0.0.8.fw dvb-usb-dtt200u-01.fw dvb-usb-terratec-h5-drxk.fw dvb-usb-terratec-h7-az6007.fw dvb-usb-terratec-h7-drxk.fw dvb-usb-umt-010-02.fw dvb-usb-vp702x-01.fw dvb-usb-vp7045-01.fw dvb-usb-wt220u-01.fw dvb-usb-wt220u-02.fw v4l-cx231xx-avcore-01.fw v4l-cx23418-apu.fw v4l-cx23418-cpu.fw v4l-cx23418-dig.fw v4l-cx23885-avcore-01.fw v4l-cx23885-enc.fw v4l-cx25840.fw make[2]: Leaving directory `/usr/src/media_build-bst/v4l/firmware'make[1]: Leaving directory `/usr/src/media_build-bst/v4l'[/HTML]

but after reboot the same thing

```
$ ls /dev/dvb
ls: cannot access /dev/dvb: No such file or directory
mediaserver@mediaserver:~$ dmesg | grep -i dvb
mediaserver@mediaserver:~$ 

```

---

### Post by Bashing-om on 2014-07-09
Jonners59; Well. 

I see :
> 
Installing kernel modules under /lib/modules/3.13.0-30-generic/kernel/drivers/media/:	->>>

Is all good now ?

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2014-07-09
It didn't work, so I removed the tar file and the extracted file and started from scratch.  Only difference I am noew doing make and then make install...

Ah, the make has just stopped after about >5 mins of doing stuff

here is the tail end of the text... there were hundreds of lines like this.

[HTML]  CC      /usr/src/media_build-bst/v4l/rc-alink-dtu-m.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-alink-dtu-m.ko  CC      /usr/src/media_build-bst/v4l/rc-anysee.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-anysee.ko  CC      /usr/src/media_build-bst/v4l/rc-apac-viewcomp.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-apac-viewcomp.ko  CC      /usr/src/media_build-bst/v4l/rc-asus-pc39.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-asus-pc39.ko  CC      /usr/src/media_build-bst/v4l/rc-asus-ps3-100.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-asus-ps3-100.ko  CC      /usr/src/media_build-bst/v4l/rc-ati-tv-wonder-hd-600.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-ati-tv-wonder-hd-600.ko  CC      /usr/src/media_build-bst/v4l/rc-ati-x10.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-ati-x10.ko  CC      /usr/src/media_build-bst/v4l/rc-avermedia-a16d.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avermedia-a16d.ko  CC      /usr/src/media_build-bst/v4l/rc-avermedia-cardbus.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avermedia-cardbus.ko  CC      /usr/src/media_build-bst/v4l/rc-avermedia-dvbt.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avermedia-dvbt.ko  CC      /usr/src/media_build-bst/v4l/rc-avermedia-m135a.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avermedia-m135a.ko  CC      /usr/src/media_build-bst/v4l/rc-avermedia-m733a-rm-k6.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avermedia-m733a-rm-k6.ko  CC      /usr/src/media_build-bst/v4l/rc-avermedia-rm-ks.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avermedia-rm-ks.ko  CC      /usr/src/media_build-bst/v4l/rc-avermedia.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avermedia.ko  CC      /usr/src/media_build-bst/v4l/rc-avertv-303.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-avertv-303.ko  CC      /usr/src/media_build-bst/v4l/rc-azurewave-ad-tu700.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-azurewave-ad-tu700.ko  CC      /usr/src/media_build-bst/v4l/rc-behold-columbus.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-behold-columbus.ko  CC      /usr/src/media_build-bst/v4l/rc-behold.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-behold.ko  CC      /usr/src/media_build-bst/v4l/rc-budget-ci-old.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-budget-ci-old.ko  CC      /usr/src/media_build-bst/v4l/rc-cinergy-1400.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-cinergy-1400.ko  CC      /usr/src/media_build-bst/v4l/rc-cinergy.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-cinergy.ko  CC      /usr/src/media_build-bst/v4l/rc-core.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-core.ko  CC      /usr/src/media_build-bst/v4l/rc-dib0700-nec.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-dib0700-nec.ko  CC      /usr/src/media_build-bst/v4l/rc-dib0700-rc5.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-dib0700-rc5.ko  CC      /usr/src/media_build-bst/v4l/rc-digitalnow-tinytwin.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-digitalnow-tinytwin.ko  CC      /usr/src/media_build-bst/v4l/rc-digittrade.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-digittrade.ko  CC      /usr/src/media_build-bst/v4l/rc-dm1105-nec.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-dm1105-nec.ko  CC      /usr/src/media_build-bst/v4l/rc-dntv-live-dvb-t.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-dntv-live-dvb-t.ko  CC      /usr/src/media_build-bst/v4l/rc-dntv-live-dvbt-pro.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-dntv-live-dvbt-pro.ko  CC      /usr/src/media_build-bst/v4l/rc-dvbsky.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-dvbsky.ko  CC      /usr/src/media_build-bst/v4l/rc-em-terratec.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-em-terratec.ko  CC      /usr/src/media_build-bst/v4l/rc-encore-enltv-fm53.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-encore-enltv-fm53.ko  CC      /usr/src/media_build-bst/v4l/rc-encore-enltv.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-encore-enltv.ko  CC      /usr/src/media_build-bst/v4l/rc-encore-enltv2.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-encore-enltv2.ko  CC      /usr/src/media_build-bst/v4l/rc-evga-indtube.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-evga-indtube.ko  CC      /usr/src/media_build-bst/v4l/rc-eztv.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-eztv.ko  CC      /usr/src/media_build-bst/v4l/rc-flydvb.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-flydvb.ko  CC      /usr/src/media_build-bst/v4l/rc-flyvideo.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-flyvideo.ko  CC      /usr/src/media_build-bst/v4l/rc-fusionhdtv-mce.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-fusionhdtv-mce.ko  CC      /usr/src/media_build-bst/v4l/rc-gadmei-rm008z.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-gadmei-rm008z.ko  CC      /usr/src/media_build-bst/v4l/rc-genius-tvgo-a11mce.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-genius-tvgo-a11mce.ko  CC      /usr/src/media_build-bst/v4l/rc-gotview7135.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-gotview7135.ko  CC      /usr/src/media_build-bst/v4l/rc-hauppauge.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-hauppauge.ko  CC      /usr/src/media_build-bst/v4l/rc-imon-mce.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-imon-mce.ko  CC      /usr/src/media_build-bst/v4l/rc-imon-pad.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-imon-pad.ko  CC      /usr/src/media_build-bst/v4l/rc-iodata-bctv7e.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-iodata-bctv7e.ko  CC      /usr/src/media_build-bst/v4l/rc-it913x-v1.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-it913x-v1.ko  CC      /usr/src/media_build-bst/v4l/rc-it913x-v2.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-it913x-v2.ko  CC      /usr/src/media_build-bst/v4l/rc-kaiomy.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-kaiomy.ko  CC      /usr/src/media_build-bst/v4l/rc-kworld-315u.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-kworld-315u.ko  CC      /usr/src/media_build-bst/v4l/rc-kworld-pc150u.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-kworld-pc150u.ko  CC      /usr/src/media_build-bst/v4l/rc-kworld-plus-tv-analog.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-kworld-plus-tv-analog.ko  CC      /usr/src/media_build-bst/v4l/rc-leadtek-y04g0051.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-leadtek-y04g0051.ko  CC      /usr/src/media_build-bst/v4l/rc-lirc.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-lirc.ko  CC      /usr/src/media_build-bst/v4l/rc-lme2510.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-lme2510.ko  CC      /usr/src/media_build-bst/v4l/rc-loopback.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-loopback.ko  CC      /usr/src/media_build-bst/v4l/rc-manli.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-manli.ko  CC      /usr/src/media_build-bst/v4l/rc-medion-x10-digitainer.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-medion-x10-digitainer.ko  CC      /usr/src/media_build-bst/v4l/rc-medion-x10-or2x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-medion-x10-or2x.ko  CC      /usr/src/media_build-bst/v4l/rc-medion-x10.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-medion-x10.ko  CC      /usr/src/media_build-bst/v4l/rc-msi-digivox-ii.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-msi-digivox-ii.ko  CC      /usr/src/media_build-bst/v4l/rc-msi-digivox-iii.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-msi-digivox-iii.ko  CC      /usr/src/media_build-bst/v4l/rc-msi-tvanywhere-plus.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-msi-tvanywhere-plus.ko  CC      /usr/src/media_build-bst/v4l/rc-msi-tvanywhere.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-msi-tvanywhere.ko  CC      /usr/src/media_build-bst/v4l/rc-nebula.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-nebula.ko  CC      /usr/src/media_build-bst/v4l/rc-nec-terratec-cinergy-xs.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-nec-terratec-cinergy-xs.ko  CC      /usr/src/media_build-bst/v4l/rc-norwood.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-norwood.ko  CC      /usr/src/media_build-bst/v4l/rc-npgtech.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-npgtech.ko  CC      /usr/src/media_build-bst/v4l/rc-pctv-sedna.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pctv-sedna.ko  CC      /usr/src/media_build-bst/v4l/rc-pinnacle-color.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pinnacle-color.ko  CC      /usr/src/media_build-bst/v4l/rc-pinnacle-grey.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pinnacle-grey.ko  CC      /usr/src/media_build-bst/v4l/rc-pinnacle-pctv-hd.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pinnacle-pctv-hd.ko  CC      /usr/src/media_build-bst/v4l/rc-pixelview-002t.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pixelview-002t.ko  CC      /usr/src/media_build-bst/v4l/rc-pixelview-mk12.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pixelview-mk12.ko  CC      /usr/src/media_build-bst/v4l/rc-pixelview-new.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pixelview-new.ko  CC      /usr/src/media_build-bst/v4l/rc-pixelview.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pixelview.ko  CC      /usr/src/media_build-bst/v4l/rc-powercolor-real-angel.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-powercolor-real-angel.ko  CC      /usr/src/media_build-bst/v4l/rc-proteus-2309.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-proteus-2309.ko  CC      /usr/src/media_build-bst/v4l/rc-purpletv.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-purpletv.ko  CC      /usr/src/media_build-bst/v4l/rc-pv951.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-pv951.ko  CC      /usr/src/media_build-bst/v4l/rc-rc6-mce.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-rc6-mce.ko  CC      /usr/src/media_build-bst/v4l/rc-real-audio-220-32-keys.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-real-audio-220-32-keys.ko  CC      /usr/src/media_build-bst/v4l/rc-snapstream-firefly.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-snapstream-firefly.ko  CC      /usr/src/media_build-bst/v4l/rc-streamzap.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-streamzap.ko  CC      /usr/src/media_build-bst/v4l/rc-tbs-nec.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-tbs-nec.ko  CC      /usr/src/media_build-bst/v4l/rc-technisat-usb2.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-technisat-usb2.ko  CC      /usr/src/media_build-bst/v4l/rc-terratec-cinergy-xs.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-terratec-cinergy-xs.ko  CC      /usr/src/media_build-bst/v4l/rc-terratec-slim-2.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-terratec-slim-2.ko  CC      /usr/src/media_build-bst/v4l/rc-terratec-slim.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-terratec-slim.ko  CC      /usr/src/media_build-bst/v4l/rc-tevii-nec.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-tevii-nec.ko  CC      /usr/src/media_build-bst/v4l/rc-tivo.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-tivo.ko  CC      /usr/src/media_build-bst/v4l/rc-total-media-in-hand-02.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-total-media-in-hand-02.ko  CC      /usr/src/media_build-bst/v4l/rc-total-media-in-hand.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-total-media-in-hand.ko  CC      /usr/src/media_build-bst/v4l/rc-trekstor.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-trekstor.ko  CC      /usr/src/media_build-bst/v4l/rc-tt-1500.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-tt-1500.ko  CC      /usr/src/media_build-bst/v4l/rc-twinhan1027.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-twinhan1027.ko  CC      /usr/src/media_build-bst/v4l/rc-videomate-m1f.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-videomate-m1f.ko  CC      /usr/src/media_build-bst/v4l/rc-videomate-s350.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-videomate-s350.ko  CC      /usr/src/media_build-bst/v4l/rc-videomate-tv-pvr.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-videomate-tv-pvr.ko  CC      /usr/src/media_build-bst/v4l/rc-winfast-usbii-deluxe.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-winfast-usbii-deluxe.ko  CC      /usr/src/media_build-bst/v4l/rc-winfast.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rc-winfast.ko  CC      /usr/src/media_build-bst/v4l/redrat3.mod.o  LD [M]  /usr/src/media_build-bst/v4l/redrat3.ko  CC      /usr/src/media_build-bst/v4l/rj54n1cb0c.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rj54n1cb0c.ko  CC      /usr/src/media_build-bst/v4l/rtl2830.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rtl2830.ko  CC      /usr/src/media_build-bst/v4l/rtl2832.mod.o  LD [M]  /usr/src/media_build-bst/v4l/rtl2832.ko  CC      /usr/src/media_build-bst/v4l/s2255drv.mod.o  LD [M]  /usr/src/media_build-bst/v4l/s2255drv.ko  CC      /usr/src/media_build-bst/v4l/s5h1409.mod.o  LD [M]  /usr/src/media_build-bst/v4l/s5h1409.ko  CC      /usr/src/media_build-bst/v4l/s5h1411.mod.o  LD [M]  /usr/src/media_build-bst/v4l/s5h1411.ko  CC      /usr/src/media_build-bst/v4l/s5h1420.mod.o  LD [M]  /usr/src/media_build-bst/v4l/s5h1420.ko  CC      /usr/src/media_build-bst/v4l/s5h1432.mod.o  LD [M]  /usr/src/media_build-bst/v4l/s5h1432.ko  CC      /usr/src/media_build-bst/v4l/s921.mod.o  LD [M]  /usr/src/media_build-bst/v4l/s921.ko  CC      /usr/src/media_build-bst/v4l/saa6588.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa6588.ko  CC      /usr/src/media_build-bst/v4l/saa6752hs.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa6752hs.ko  CC      /usr/src/media_build-bst/v4l/saa7110.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7110.ko  CC      /usr/src/media_build-bst/v4l/saa7115.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7115.ko  CC      /usr/src/media_build-bst/v4l/saa7127.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7127.ko  CC      /usr/src/media_build-bst/v4l/saa7134-alsa.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7134-alsa.ko  CC      /usr/src/media_build-bst/v4l/saa7134-dvb.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7134-dvb.ko  CC      /usr/src/media_build-bst/v4l/saa7134-empress.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7134-empress.ko  CC      /usr/src/media_build-bst/v4l/saa7134.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7134.ko  CC      /usr/src/media_build-bst/v4l/saa7146.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7146.ko  CC      /usr/src/media_build-bst/v4l/saa7146_vv.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7146_vv.ko  CC      /usr/src/media_build-bst/v4l/saa7164.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7164.ko  CC      /usr/src/media_build-bst/v4l/saa717x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa717x.ko  CC      /usr/src/media_build-bst/v4l/saa7185.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7185.ko  CC      /usr/src/media_build-bst/v4l/saa7191.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7191.ko  CC      /usr/src/media_build-bst/v4l/saa7706h.mod.o  LD [M]  /usr/src/media_build-bst/v4l/saa7706h.ko  CC      /usr/src/media_build-bst/v4l/sh_mobile_ceu_camera.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sh_mobile_ceu_camera.ko  CC      /usr/src/media_build-bst/v4l/sh_mobile_csi2.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sh_mobile_csi2.ko  CC      /usr/src/media_build-bst/v4l/sh_veu.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sh_veu.ko  CC      /usr/src/media_build-bst/v4l/shark2.mod.o  LD [M]  /usr/src/media_build-bst/v4l/shark2.ko  CC      /usr/src/media_build-bst/v4l/si21xx.mod.o  LD [M]  /usr/src/media_build-bst/v4l/si21xx.ko  CC      /usr/src/media_build-bst/v4l/si4713-i2c.mod.o  LD [M]  /usr/src/media_build-bst/v4l/si4713-i2c.ko  CC      /usr/src/media_build-bst/v4l/sit2fe.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sit2fe.ko  CC      /usr/src/media_build-bst/v4l/smiapp-pll.mod.o  LD [M]  /usr/src/media_build-bst/v4l/smiapp-pll.ko  CC      /usr/src/media_build-bst/v4l/smsdvb.mod.o  LD [M]  /usr/src/media_build-bst/v4l/smsdvb.ko  CC      /usr/src/media_build-bst/v4l/smsmdtv.mod.o  LD [M]  /usr/src/media_build-bst/v4l/smsmdtv.ko  CC      /usr/src/media_build-bst/v4l/smssdio.mod.o  LD [M]  /usr/src/media_build-bst/v4l/smssdio.ko  CC      /usr/src/media_build-bst/v4l/smsusb.mod.o  LD [M]  /usr/src/media_build-bst/v4l/smsusb.ko  CC      /usr/src/media_build-bst/v4l/sn9c102.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sn9c102.ko  CC      /usr/src/media_build-bst/v4l/snd-bt87x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/snd-bt87x.ko  CC      /usr/src/media_build-bst/v4l/soc_camera.mod.o  LD [M]  /usr/src/media_build-bst/v4l/soc_camera.ko  CC      /usr/src/media_build-bst/v4l/soc_camera_platform.mod.o  LD [M]  /usr/src/media_build-bst/v4l/soc_camera_platform.ko  CC      /usr/src/media_build-bst/v4l/soc_mediabus.mod.o  LD [M]  /usr/src/media_build-bst/v4l/soc_mediabus.ko  CC      /usr/src/media_build-bst/v4l/sp8870.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sp8870.ko  CC      /usr/src/media_build-bst/v4l/sp887x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sp887x.ko  CC      /usr/src/media_build-bst/v4l/sr030pc30.mod.o  LD [M]  /usr/src/media_build-bst/v4l/sr030pc30.ko  CC      /usr/src/media_build-bst/v4l/stb0899.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stb0899.ko  CC      /usr/src/media_build-bst/v4l/stb6000.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stb6000.ko  CC      /usr/src/media_build-bst/v4l/stb6100.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stb6100.ko  CC      /usr/src/media_build-bst/v4l/stk1160.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stk1160.ko  CC      /usr/src/media_build-bst/v4l/stkwebcam.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stkwebcam.ko  CC      /usr/src/media_build-bst/v4l/streamzap.mod.o  LD [M]  /usr/src/media_build-bst/v4l/streamzap.ko  CC      /usr/src/media_build-bst/v4l/stv0288.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv0288.ko  CC      /usr/src/media_build-bst/v4l/stv0297.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv0297.ko  CC      /usr/src/media_build-bst/v4l/stv0299.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv0299.ko  CC      /usr/src/media_build-bst/v4l/stv0367.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv0367.ko  CC      /usr/src/media_build-bst/v4l/stv0900.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv0900.ko  CC      /usr/src/media_build-bst/v4l/stv090x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv090x.ko  CC      /usr/src/media_build-bst/v4l/stv6110.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv6110.ko  CC      /usr/src/media_build-bst/v4l/stv6110x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/stv6110x.ko  CC      /usr/src/media_build-bst/v4l/tcm825x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tcm825x.ko  CC      /usr/src/media_build-bst/v4l/tda10021.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda10021.ko  CC      /usr/src/media_build-bst/v4l/tda10023.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda10023.ko  CC      /usr/src/media_build-bst/v4l/tda10048.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda10048.ko  CC      /usr/src/media_build-bst/v4l/tda1004x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda1004x.ko  CC      /usr/src/media_build-bst/v4l/tda10071.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda10071.ko  CC      /usr/src/media_build-bst/v4l/tda10086.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda10086.ko  CC      /usr/src/media_build-bst/v4l/tda18212.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda18212.ko  CC      /usr/src/media_build-bst/v4l/tda18218.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda18218.ko  CC      /usr/src/media_build-bst/v4l/tda18271.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda18271.ko  CC      /usr/src/media_build-bst/v4l/tda18271c2dd.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda18271c2dd.ko  CC      /usr/src/media_build-bst/v4l/tda665x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda665x.ko  CC      /usr/src/media_build-bst/v4l/tda7432.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda7432.ko  CC      /usr/src/media_build-bst/v4l/tda8083.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda8083.ko  CC      /usr/src/media_build-bst/v4l/tda8261.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda8261.ko  CC      /usr/src/media_build-bst/v4l/tda826x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda826x.ko  CC      /usr/src/media_build-bst/v4l/tda827x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda827x.ko  CC      /usr/src/media_build-bst/v4l/tda8290.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda8290.ko  CC      /usr/src/media_build-bst/v4l/tda9840.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda9840.ko  CC      /usr/src/media_build-bst/v4l/tda9887.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tda9887.ko  CC      /usr/src/media_build-bst/v4l/tea5761.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tea5761.ko  CC      /usr/src/media_build-bst/v4l/tea5767.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tea5767.ko  CC      /usr/src/media_build-bst/v4l/tea6415c.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tea6415c.ko  CC      /usr/src/media_build-bst/v4l/tea6420.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tea6420.ko  CC      /usr/src/media_build-bst/v4l/tef6862.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tef6862.ko  CC      /usr/src/media_build-bst/v4l/ths7303.mod.o  LD [M]  /usr/src/media_build-bst/v4l/ths7303.ko  CC      /usr/src/media_build-bst/v4l/timblogiw.mod.o  LD [M]  /usr/src/media_build-bst/v4l/timblogiw.ko  CC      /usr/src/media_build-bst/v4l/tlv320aic23b.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tlv320aic23b.ko  CC      /usr/src/media_build-bst/v4l/tm6000-alsa.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tm6000-alsa.ko  CC      /usr/src/media_build-bst/v4l/tm6000-dvb.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tm6000-dvb.ko  CC      /usr/src/media_build-bst/v4l/tm6000.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tm6000.ko  CC      /usr/src/media_build-bst/v4l/ttpci-eeprom.mod.o  LD [M]  /usr/src/media_build-bst/v4l/ttpci-eeprom.ko  CC      /usr/src/media_build-bst/v4l/ttusb_dec.mod.o  LD [M]  /usr/src/media_build-bst/v4l/ttusb_dec.ko  CC      /usr/src/media_build-bst/v4l/ttusbdecfe.mod.o  LD [M]  /usr/src/media_build-bst/v4l/ttusbdecfe.ko  CC      /usr/src/media_build-bst/v4l/ttusbir.mod.o  LD [M]  /usr/src/media_build-bst/v4l/ttusbir.ko  CC      /usr/src/media_build-bst/v4l/tua6100.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tua6100.ko  CC      /usr/src/media_build-bst/v4l/tua9001.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tua9001.ko  CC      /usr/src/media_build-bst/v4l/tuner-simple.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tuner-simple.ko  CC      /usr/src/media_build-bst/v4l/tuner-types.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tuner-types.ko  CC      /usr/src/media_build-bst/v4l/tuner-xc2028.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tuner-xc2028.ko  CC      /usr/src/media_build-bst/v4l/tuner.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tuner.ko  CC      /usr/src/media_build-bst/v4l/tvaudio.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tvaudio.ko  CC      /usr/src/media_build-bst/v4l/tveeprom.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tveeprom.ko  CC      /usr/src/media_build-bst/v4l/tvp514x.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tvp514x.ko  CC      /usr/src/media_build-bst/v4l/tvp5150.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tvp5150.ko  CC      /usr/src/media_build-bst/v4l/tvp7002.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tvp7002.ko  CC      /usr/src/media_build-bst/v4l/tw9910.mod.o  LD [M]  /usr/src/media_build-bst/v4l/tw9910.ko  CC      /usr/src/media_build-bst/v4l/upd64031a.mod.o  LD [M]  /usr/src/media_build-bst/v4l/upd64031a.ko  CC      /usr/src/media_build-bst/v4l/upd64083.mod.o  LD [M]  /usr/src/media_build-bst/v4l/upd64083.ko  CC      /usr/src/media_build-bst/v4l/usbvision.mod.o  LD [M]  /usr/src/media_build-bst/v4l/usbvision.ko  CC      /usr/src/media_build-bst/v4l/uvcvideo.mod.o  LD [M]  /usr/src/media_build-bst/v4l/uvcvideo.ko  CC      /usr/src/media_build-bst/v4l/v4l2-common.mod.o  LD [M]  /usr/src/media_build-bst/v4l/v4l2-common.ko  CC      /usr/src/media_build-bst/v4l/v4l2-int-device.mod.o  LD [M]  /usr/src/media_build-bst/v4l/v4l2-int-device.ko  CC      /usr/src/media_build-bst/v4l/v4l2-mem2mem.mod.o  LD [M]  /usr/src/media_build-bst/v4l/v4l2-mem2mem.ko  CC      /usr/src/media_build-bst/v4l/ves1820.mod.o  LD [M]  /usr/src/media_build-bst/v4l/ves1820.ko  CC      /usr/src/media_build-bst/v4l/ves1x93.mod.o  LD [M]  /usr/src/media_build-bst/v4l/ves1x93.ko  CC      /usr/src/media_build-bst/v4l/via-camera.mod.o  LD [M]  /usr/src/media_build-bst/v4l/via-camera.ko  CC      /usr/src/media_build-bst/v4l/videobuf-core.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf-core.ko  CC      /usr/src/media_build-bst/v4l/videobuf-dma-contig.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf-dma-contig.ko  CC      /usr/src/media_build-bst/v4l/videobuf-dma-sg.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf-dma-sg.ko  CC      /usr/src/media_build-bst/v4l/videobuf-dvb.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf-dvb.ko  CC      /usr/src/media_build-bst/v4l/videobuf-vmalloc.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf-vmalloc.ko  CC      /usr/src/media_build-bst/v4l/videobuf2-core.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf2-core.ko  CC      /usr/src/media_build-bst/v4l/videobuf2-dma-contig.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf2-dma-contig.ko  CC      /usr/src/media_build-bst/v4l/videobuf2-dma-sg.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf2-dma-sg.ko  CC      /usr/src/media_build-bst/v4l/videobuf2-memops.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf2-memops.ko  CC      /usr/src/media_build-bst/v4l/videobuf2-vmalloc.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videobuf2-vmalloc.ko  CC      /usr/src/media_build-bst/v4l/videocodec.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videocodec.ko  CC      /usr/src/media_build-bst/v4l/videodev.mod.o  LD [M]  /usr/src/media_build-bst/v4l/videodev.ko  CC      /usr/src/media_build-bst/v4l/vivi.mod.o  LD [M]  /usr/src/media_build-bst/v4l/vivi.ko  CC      /usr/src/media_build-bst/v4l/vp27smpx.mod.o  LD [M]  /usr/src/media_build-bst/v4l/vp27smpx.ko  CC      /usr/src/media_build-bst/v4l/vpx3220.mod.o  LD [M]  /usr/src/media_build-bst/v4l/vpx3220.ko  CC      /usr/src/media_build-bst/v4l/vs6624.mod.o  LD [M]  /usr/src/media_build-bst/v4l/vs6624.ko  CC      /usr/src/media_build-bst/v4l/w9966.mod.o  LD [M]  /usr/src/media_build-bst/v4l/w9966.ko  CC      /usr/src/media_build-bst/v4l/winbond-cir.mod.o  LD [M]  /usr/src/media_build-bst/v4l/winbond-cir.ko  CC      /usr/src/media_build-bst/v4l/wm8739.mod.o  LD [M]  /usr/src/media_build-bst/v4l/wm8739.ko  CC      /usr/src/media_build-bst/v4l/wm8775.mod.o  LD [M]  /usr/src/media_build-bst/v4l/wm8775.ko  CC      /usr/src/media_build-bst/v4l/xc4000.mod.o  LD [M]  /usr/src/media_build-bst/v4l/xc4000.ko  CC      /usr/src/media_build-bst/v4l/xc5000.mod.o  LD [M]  /usr/src/media_build-bst/v4l/xc5000.ko  CC      /usr/src/media_build-bst/v4l/zl10036.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zl10036.ko  CC      /usr/src/media_build-bst/v4l/zl10039.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zl10039.ko  CC      /usr/src/media_build-bst/v4l/zl10353.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zl10353.ko  CC      /usr/src/media_build-bst/v4l/zr36016.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zr36016.ko  CC      /usr/src/media_build-bst/v4l/zr36050.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zr36050.ko  CC      /usr/src/media_build-bst/v4l/zr36060.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zr36060.ko  CC      /usr/src/media_build-bst/v4l/zr36067.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zr36067.ko  CC      /usr/src/media_build-bst/v4l/zr364xx.mod.o  LD [M]  /usr/src/media_build-bst/v4l/zr364xx.komake[2]: Leaving directory `/usr/src/linux-headers-3.13.0-30-generic'./scripts/rmmod.pl checkmake[1]: Leaving directory `/usr/src/media_build-bst/v4l'
[/HTML]
now the make install bit

[HTML] make installmake -C /usr/src/media_build-bst/v4l installmake[1]: Entering directory `/usr/src/media_build-bst/v4l'
Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/firewire:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx231xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/uvc:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/dm1105:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/au0828:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/common/tuners:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/sn9c102:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca/m5602:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/bt8xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ddbridge:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/siano:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx88:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx23885:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ngene:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/marvell-ccic:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/dvb-core:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/dvb-usb:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/pvrusb2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/saa7134:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ttpci:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/mantis:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/pwc:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ttusb-dec:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/common:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/hdpvr:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/tm6000:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/zoran:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/ivtv:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx25821:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/pt1:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx25840:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/usbvision:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/em28xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca/gl860:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cpia2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/bt8xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/gspca/stv06xx:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/saa7164:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/frontends:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/tlg2300:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/b2c2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/pluto2:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/video/cx18:

Removing obsolete files from /lib/modules/3.13.0-30-generic/kernel/drivers/media/dvb/ttusb-budget:
Installing kernel modules under /lib/modules/3.13.0-30-generic/kernel/drivers/media/:	usb/stk1160/: stk1160.ko 	rc/keymaps/: rc-purpletv.ko rc-iodata-bctv7e.ko rc-avermedia.ko 		rc-dntv-live-dvbt-pro.ko rc-encore-enltv.ko rc-it913x-v2.ko 		rc-rc6-mce.ko rc-videomate-s350.ko rc-pinnacle-grey.ko 		rc-real-audio-220-32-keys.ko rc-gotview7135.ko rc-evga-indtube.ko 		rc-dntv-live-dvb-t.ko rc-digitalnow-tinytwin.ko rc-npgtech.ko 		rc-nec-terratec-cinergy-xs.ko rc-tivo.ko rc-kaiomy.ko 		rc-norwood.ko rc-snapstream-firefly.ko rc-apac-viewcomp.ko 		rc-ati-tv-wonder-hd-600.ko rc-budget-ci-old.ko rc-ati-x10.ko 		rc-streamzap.ko rc-nebula.ko rc-avermedia-dvbt.ko 		rc-anysee.ko rc-it913x-v1.ko rc-leadtek-y04g0051.ko 		rc-azurewave-ad-tu700.ko rc-avermedia-a16d.ko rc-cinergy-1400.ko 		rc-kworld-pc150u.ko rc-medion-x10-digitainer.ko rc-em-terratec.ko 		rc-encore-enltv2.ko rc-medion-x10.ko rc-alink-dtu-m.ko 		rc-lme2510.ko rc-lirc.ko rc-behold-columbus.ko 		rc-imon-pad.ko rc-winfast-usbii-deluxe.ko rc-hauppauge.ko 		rc-pixelview-mk12.ko rc-twinhan1027.ko rc-imon-mce.ko 		rc-avermedia-m733a-rm-k6.ko rc-gadmei-rm008z.ko rc-videomate-m1f.ko 		rc-pixelview-002t.ko rc-avermedia-m135a.ko rc-total-media-in-hand.ko 		rc-avermedia-rm-ks.ko rc-msi-tvanywhere-plus.ko rc-adstech-dvb-t-pci.ko 		rc-tbs-nec.ko rc-dm1105-nec.ko rc-asus-ps3-100.ko 		rc-manli.ko rc-videomate-tv-pvr.ko rc-powercolor-real-angel.ko 		rc-dvbsky.ko rc-terratec-slim.ko rc-behold.ko 		rc-dib0700-nec.ko rc-medion-x10-or2x.ko rc-avertv-303.ko 		rc-kworld-315u.ko rc-pixelview-new.ko rc-flyvideo.ko 		rc-kworld-plus-tv-analog.ko rc-technisat-usb2.ko rc-winfast.ko 		rc-pctv-sedna.ko rc-msi-digivox-ii.ko rc-digittrade.ko 		rc-proteus-2309.ko rc-eztv.ko rc-terratec-slim-2.ko 		rc-terratec-cinergy-xs.ko rc-avermedia-cardbus.ko rc-asus-pc39.ko 		rc-tevii-nec.ko rc-pinnacle-color.ko rc-fusionhdtv-mce.ko 		rc-msi-digivox-iii.ko rc-pinnacle-pctv-hd.ko rc-msi-tvanywhere.ko 		rc-pv951.ko rc-encore-enltv-fm53.ko rc-genius-tvgo-a11mce.ko 		rc-trekstor.ko rc-tt-1500.ko rc-flydvb.ko 		rc-total-media-in-hand-02.ko rc-cinergy.ko rc-pixelview.ko 		rc-dib0700-rc5.ko 	usb/uvc/: uvcvideo.ko 	dvb-frontends/: cx24110.ko stb6100.ko lg2160.ko 		stv6110.ko mb86a20s.ko si21xx.ko 		dib7000m.ko isl6423.ko dib3000mc.ko 		dib7000p.ko stv0297.ko zl10039.ko 		hd29l2.ko cx22702.ko dib3000mb.ko 		mt312.ko dib0070.ko s5h1420.ko 		dvb-pll.ko stb0899.ko stv0288.ko 		ves1820.ko stv090x.ko tda1004x.ko 		tda18271c2dd.ko sp887x.ko ds3000.ko 		lgdt3305.ko af9033.ko stb6000.ko 		sp8870.ko atbm8830.ko stv0900.ko 		lnbp22.ko ix2505v.ko m88ds3103.ko 		au8522_dig.ko tda10071.ko s5h1409.ko 		tda826x.ko tda665x.ko zl10036.ko 		lgdt330x.ko dib8000.ko zl10353.ko 		bcm3510.ko m88rs2000.ko s921.ko 		cx24123.ko au8522_common.ko isl6405.ko 		tda10086.ko isl6421.ko mb86a16.ko 		drxk.ko s5h1411.ko rtl2830.ko 		l64781.ko tda8083.ko sit2fe.ko 		dib0090.ko dvb_dummy_fe.ko a8293.ko 		af9013.ko dibx000_common.ko tua6100.ko 		rtl2832.ko or51132.ko s5h1432.ko 		tda10023.ko lgs8gxx.ko stv0299.ko 		tda8261.ko stv6110x.ko ves1x93.ko 		au8522_decoder.ko cxd2820r.ko nxt200x.ko 		itd1000.ko tda10021.ko cx22700.ko 		mt352.ko ec100.ko m88dc2800.ko 		stv0367.ko or51211.ko cx24116.ko 		tda10048.ko lnbp21.ko lgs8gl5.ko 		drxd.ko nxt6000.ko it913x-fe.ko 		dib9000.ko cx24113.ko 	dvb-core/: dvb-core.ko 	../linux/drivers/misc/altera-stapl/: altera-stapl.ko 	pci/cx23885/: cx23885.ko altera-ci.ko 	pci/ddbridge/: ddbridge.ko 	pci/cx88/: cx88-vp3054-i2c.ko cx8802.ko cx8800.ko 		cx88-alsa.ko cx88-blackbird.ko cx88-dvb.ko 		cx88xx.ko 	pci/cx25821/: cx25821.ko 	usb/tlg2300/: poseidon.ko 	i2c/: vpx3220.ko m52790.ko tvp7002.ko 		mt9v011.ko saa6588.ko upd64083.ko 		msp3400.ko saa7185.ko adv7175.ko 		ir-kbd-i2c.ko adv7343.ko ov7670.ko 		cx2341x.ko tea6420.ko adv7183.ko 		adv7393.ko wm8739.ko saa7191.ko 		aptina-pll.ko saa7115.ko bt866.ko 		cs5345.ko tveeprom.ko saa7110.ko 		ak881x.ko adv7170.ko vp27smpx.ko 		tvp514x.ko tvaudio.ko tea6415c.ko 		tda7432.ko smiapp-pll.ko upd64031a.ko 		ths7303.ko bt856.ko bt819.ko 		tcm825x.ko saa7127.ko tda9840.ko 		sr030pc30.ko vs6624.ko btcx-risc.ko 		adv7180.ko tlv320aic23b.ko ks0127.ko 		cs53l32a.ko tvp5150.ko saa717x.ko 		wm8775.ko 	pci/bt8xx/: dvb-bt8xx.ko dst_ca.ko dst.ko 		bttv.ko bt878.ko 	mmc/siano/: smssdio.ko 	pci/ngene/: ngene.ko 	common/saa7146/: saa7146.ko saa7146_vv.ko 	pci/meye/: meye.ko 	usb/gspca/m5602/: gspca_m5602.ko 	radio/: radio-shark.ko radio-ma901.ko tef6862.ko 		radio-maxiradio.ko radio-keene.ko radio-wl1273.ko 		dsbr100.ko radio-mr800.ko si4713-i2c.ko 		radio-tea5764.ko shark2.ko saa7706h.ko 		radio-timb.ko radio-si4713.ko 	usb/cx231xx/: cx231xx-dvb.ko cx231xx-alsa.ko cx231xx.ko 	usb/b2c2/: b2c2-flexcop-usb.ko 	usb/sn9c102/: sn9c102.ko 	firewire/: firedtv.ko 	usb/em28xx/: em28xx-rc.ko em28xx-dvb.ko em28xx.ko 		em28xx-alsa.ko 	usb/tm6000/: tm6000.ko tm6000-dvb.ko tm6000-alsa.ko 	common/siano/: smsmdtv.ko smsdvb.ko 	usb/gspca/gl860/: gspca_gl860.ko 	pci/saa7134/: saa7134-alsa.ko saa7134.ko saa6752hs.ko 		saa7134-dvb.ko saa7134-empress.ko 	pci/zoran/: zr36067.ko zr36050.ko zr36060.ko 		videocodec.ko zr36016.ko 	pci/ivtv/: ivtv.ko ivtv-alsa.ko ivtvfb.ko 	platform/marvell-ccic/: cafe_ccic.ko 	radio/si470x/: radio-usb-si470x.ko 	parport/: w9966.ko c-qcam.ko bw-qcam.ko 	usb/stkwebcam/: stkwebcam.ko 	pci/ttpci/: budget-ci.ko dvb-ttpci.ko budget-core.ko 		budget-patch.ko ttpci-eeprom.ko budget.ko 		budget-av.ko 	usb/dvb-usb-v2/: dvb-usb-gl861.ko dvb-usb-mxl111sf.ko dvb-usb-ce6230.ko 		dvb-usb-af9035.ko dvb-usb-ec168.ko dvb-usb-it913x.ko 		dvb-usb-dvbsky.ko dvb-usb-af9015.ko dvb_usb_cypress_firmware.ko 		dvb-usb-anysee.ko dvb-usb-au6610.ko dvb-usb-az6007.ko 		mxl111sf-tuner.ko mxl111sf-demod.ko dvb_usb_v2.ko 		dvb-usb-lmedm04.ko 	usb/dvb-usb/: dvb-usb-dibusb-common.ko dvb-usb-dib0700.ko dvb-usb-pctv452e.ko 		dvb-usb-opera.ko dvb-usb-vp702x.ko dvb-usb-nova-t-usb2.ko 		dvb-usb-dibusb-mb.ko dvb-usb-dtt200u.ko dvb-usb-ttusb2.ko 		dvb-usb-cxusb.ko dvb-usb-dibusb-mc.ko dvb-usb-dtv5100.ko 		dvb-usb-digitv.ko dvb-usb-af9005-remote.ko dvb-usb-technisat-usb2.ko 		dvb-usb-umt-010.ko dvb-usb.ko dvb-usb-m920x.ko 		dvb-usb-friio.ko dvb-usb-az6027.ko dvb-usb-af9005.ko 		dvb-usb-vp7045.ko dvb-usb-a800.ko dvb-usb-dw2102.ko 		dvb-usb-gp8psk.ko dvb-usb-cinergyT2.ko 	pci/saa7164/: saa7164.ko 	usb/gspca/stv06xx/: gspca_stv06xx.ko 	usb/pvrusb2/: pvrusb2.ko 	pci/pluto2/: pluto2.ko 	usb/ttusb-budget/: dvb-ttusb-budget.ko 	usb/usbvision/: usbvision.ko 	usb/s2255/: s2255drv.ko 	i2c/cx25840/: cx25840.ko 	pci/pt1/: earth-pt1.ko 	usb/ttusb-dec/: ttusb_dec.ko ttusbdecfe.ko 	radio/wl128x/: fm_drv.ko 	pci/mantis/: mantis.ko mantis_core.ko hopper.ko 	usb/gspca/: gspca_ov534.ko gspca_xirlink_cit.ko gspca_conex.ko 		gspca_t613.ko gspca_vicam.ko gspca_jl2005bcd.ko 		gspca_sn9c2028.ko gspca_stk014.ko gspca_kinect.ko 		gspca_spca506.ko gspca_cpia1.ko gspca_konica.ko 		gspca_nw80x.ko gspca_spca501.ko gspca_spca505.ko 		gspca_spca500.ko gspca_ov534_9.ko gspca_mars.ko 		gspca_sunplus.ko gspca_main.ko gspca_finepix.ko 		gspca_vc032x.ko gspca_pac7311.ko gspca_ov519.ko 		gspca_tv8532.ko gspca_sn9c20x.ko gspca_benq.ko 		gspca_sq905c.ko gspca_topro.ko gspca_se401.ko 		gspca_pac207.ko gspca_etoms.ko gspca_spca1528.ko 		gspca_jeilinj.ko gspca_spca508.ko gspca_sonixb.ko 		gspca_sq930x.ko gspca_spca561.ko gspca_pac7302.ko 		gspca_sq905.ko gspca_sonixj.ko gspca_mr97310a.ko 		gspca_stv0680.ko gspca_zc3xx.ko 	usb/au0828/: au0828.ko 	usb/zr364xx/: zr364xx.ko 	usb/pwc/: pwc.ko 	v4l2-core/: videodev.ko videobuf2-core.ko videobuf-vmalloc.ko 		videobuf-dma-sg.ko videobuf2-dma-contig.ko v4l2-mem2mem.ko 		videobuf-dvb.ko videobuf2-memops.ko v4l2-int-device.ko 		videobuf2-vmalloc.ko videobuf-core.ko videobuf2-dma-sg.ko 		v4l2-common.ko videobuf-dma-contig.ko tuner.ko 	platform/: via-camera.ko mem2mem_testdev.ko vivi.ko 		m2m-deinterlace.ko timblogiw.ko sh_veu.ko 	usb/siano/: smsusb.ko 	pci/dm1105/: dm1105.ko 	usb/cpia2/: cpia2.ko 	i2c/soc_camera/: imx074.ko rj54n1cb0c.ko ov772x.ko 		mt9t112.ko ov9740.ko mt9t031.ko 		ov9640.ko ov6650.ko mt9m111.ko 		mt9v022.ko mt9m001.ko tw9910.ko 		ov2640.ko ov5642.ko 	rc/: rc-core.ko mceusb.ko winbond-cir.ko 		ttusbir.ko ir-rc5-decoder.ko nuvoton-cir.ko 		lirc_dev.ko gpio-ir-recv.ko ir-sony-decoder.ko 		streamzap.ko ir-jvc-decoder.ko ir-lirc-codec.ko 		ir-rc5-sz-decoder.ko ir-nec-decoder.ko ir-rc6-decoder.ko 		ene_ir.ko ati_remote.ko ite-cir.ko 		fintek-cir.ko imon.ko ir-sanyo-decoder.ko 		iguanair.ko ir-mce_kbd-decoder.ko redrat3.ko 		rc-loopback.ko 	tuners/: tea5767.ko mt2131.ko xc4000.ko 		mt2063.ko tda18271.ko tda827x.ko 		qt1010.ko max2165.ko tuner-simple.ko 		fc0013.ko fc0011.ko fc2580.ko 		tda18218.ko mt2266.ko mt2060.ko 		e4000.ko mc44s803.ko mxl5005s.ko 		tua9001.ko mt20xx.ko tda8290.ko 		xc5000.ko tuner-xc2028.ko tda18212.ko 		tuner-types.ko tda9887.ko tea5761.ko 		fc0012.ko mxl5007t.ko 	common/b2c2/: b2c2-flexcop.ko 	pci/cx18/: cx18-alsa.ko cx18.ko 	platform/soc_camera/: soc_mediabus.ko sh_mobile_ceu_camera.ko soc_camera_platform.ko 		soc_camera.ko sh_mobile_csi2.ko 	usb/hdpvr/: hdpvr.ko 	pci/saa7146/: hexium_orion.ko mxb.ko hexium_gemini.ko 	pci/b2c2/: b2c2-flexcop-pci.ko /sbin/depmod -a 3.13.0-30-generic make -C firmware installmake[2]: Entering directory `/usr/src/media_build-bst/v4l/firmware'Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw cp: cannot stat 'dabusb/firmware.fw': No such file or directorydabusb/bitstream.bin cp: cannot stat 'dabusb/bitstream.bin': No such file or directoryttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin dvb-fe-bcm3510-01.fw dvb-fe-or51132-qam.fw dvb-fe-or51132-vsb.fw dvb-fe-or51211.fw dvb-fe-xc5000-1.6.114.fw dvb-ttpci-01.fw-261a dvb-ttpci-01.fw-261b dvb-ttpci-01.fw-261c dvb-ttpci-01.fw-261d dvb-ttpci-01.fw-261f dvb-ttpci-01.fw-2622 dvb-usb-avertv-a800-02.fw dvb-usb-bluebird-01.fw dvb-usb-dib0700-1.20.fw dvb-usb-dibusb-5.0.0.11.fw dvb-usb-dibusb-6.0.0.8.fw dvb-usb-dtt200u-01.fw dvb-usb-terratec-h5-drxk.fw dvb-usb-terratec-h7-az6007.fw dvb-usb-terratec-h7-drxk.fw dvb-usb-umt-010-02.fw dvb-usb-vp702x-01.fw dvb-usb-vp7045-01.fw dvb-usb-wt220u-01.fw dvb-usb-wt220u-02.fw v4l-cx231xx-avcore-01.fw v4l-cx23418-apu.fw v4l-cx23418-cpu.fw v4l-cx23418-dig.fw v4l-cx23885-avcore-01.fw v4l-cx23885-enc.fw v4l-cx25840.fw make[2]: Leaving directory `/usr/src/media_build-bst/v4l/firmware'make[1]: Leaving directory `/usr/src/media_build-bst/v4l'[/HTML]

---

### Post by Jonners59 on 2014-07-09
Nope!!!  Did not work

[HTML]$ ls /dev/dvbls: cannot access /dev/dvb: No such file or directorymediaserver@mediaserver:~$ dmesg | grep -i dvbmediaserver@mediaserver:~$ [/HTML]

---

### Post by Jonners59 on 2014-07-10
[COLOR=#000000][FONT=Verdana]SkyDVB sent me new instructions.  More basic then below, but the link downloaded a different set of drivers

[/FONT][/COLOR]
[PHP]Read this document first. http://www.dvbsky.net/download/doc/Linux_driver_installation_Guide
Download dvbsky media tree. http://www.dvbsky.net/download/linux/media_build-bst-14-140621.tar.gz
and install it.[/PHP]

This time I moved the downloaded file to my Home Directory and extracted it there.  Then followed the instructions below, but to the Home Directory.....

It has installed no question, but not able to get any of the clients to work with it.... another problem, so I guess this is now solved.

---

