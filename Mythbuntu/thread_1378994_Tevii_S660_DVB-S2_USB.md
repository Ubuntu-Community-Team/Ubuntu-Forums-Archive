---
title: "Tevii S660 DVB-S2 USB"
date: 2010-01-12
forum: Mythbuntu
---

### Post by dumbo79 on 2010-01-12
Hi,

I have problem to get my Tevii S660 to work with Mythbuntu. I have downloaded the linux driver from tevii's support site. I think I have installed them correct (I'm a newbiw on linux). I copy the .fw files to /lib/firmware and the I run make && make install

When I run mythtv-setup I can't se my tuner under "Capture cards"

Anyone who has get this work with S660? Any idea of what I'm doing wrong?

BR,
Micke

---

### Post by srandrews on 2010-01-13
Hi Mickie,

I managed to install this OK the other day with MythBuntu, the only thing that almost tripped me up was I needed to run the make commands as root, this failed as the second command isn't run as root:

```
sudo make && make install
```

I ran it as two separate lines like this which worked:

```
sudo make
sudo make install
```

HTH
Simon

---

### Post by fuzzydunlop on 2010-01-28
I did this and it all compiled and installed correctly I think.

No /dev/dvb* and dmesg reports:

```
[  107.540029] usb 1-2: new high speed USB device using ehci_hcd and address 1
[  107.672963] usb 1-2: configuration #1 chosen from 1 choice
[  107.673312] dvb-usb: found a 'TEVII S660 DVBS2 USB2.0' in cold state, will y to load a firmware
[  107.673326] usb 1-2: firmware: requesting dvb-usb-teviis660.fw
[  107.695867] dvb-usb: downloading firmware from file 'dvb-usb-teviis660.fw'
[  107.695881] usb 1-2: firmware: requesting dvb-usb-teviis660.fw
[  107.732673] teviis660: start downloading TEVIIS660 firmware
[  107.832233] teviis660: error while transferring firmware
[  107.832244] teviis660: could not restart the USB controller CPU.
[  107.832249] teviis660: could not restart the USB controller CPU.
[  107.937710] usb 1-2: USB disconnect, address 113

```

---

### Post by fuzzydunlop on 2010-01-29
Looking at syslog and it seems to be some problem with loading firmware and vmap and vmalloc.

Can anybody help with this?

```
Jan 29 08:50:59 AOK-mythtv kernel: [52241.668035] usb 1-2: new high speed USB device using ehci_hcd and address 55
Jan 29 08:50:59 AOK-mythtv kernel: [52241.804401] usb 1-2: configuration #1 chosen from 1 choice
Jan 29 08:50:59 AOK-mythtv kernel: [52241.805268] dvb-usb: found a 'TEVII S660 DVBS2 USB2.0' in cold state, will try to load a firmware
Jan 29 08:50:59 AOK-mythtv kernel: [52241.805282] usb 1-2: firmware: requesting dvb-usb-teviis660.fw
Jan 29 08:50:59 AOK-mythtv kernel: [52241.832918] dvb-usb: downloading firmware from file 'dvb-usb-teviis660.fw'
Jan 29 08:50:59 AOK-mythtv kernel: [52241.832932] usb 1-2: firmware: requesting dvb-usb-teviis660.fw
Jan 29 08:50:59 AOK-mythtv kernel: [52241.873490] vmap allocation for size 12288 failed: use vmalloc=<size> to increase size.
Jan 29 08:50:59 AOK-mythtv kernel: [52241.873507] firmware 1-2: firmware_loading_store: vmap() failed
Jan 29 08:50:59 AOK-mythtv kernel: [52241.874244] teviis660: did not find the firmware file. (dvb-usb-teviis660.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems.
Jan 29 08:50:59 AOK-mythtv kernel: [52242.323270] usb 1-2: USB disconnect, address 55

```

---

### Post by Neon Dusk on 2010-01-29
> **fuzzydunlop said:**
> Looking at syslog and it seems to be some problem with loading firmware and vmap and vmalloc.


Jan 29 08:50:59 AOK-mythtv kernel: [52241.874244] teviis660: did not find the firmware file. (dvb-usb-teviis660.fw)

Do you have the firmware file 'dvb-usb-teviis660.fw' in /lib/firmware

Looking at [http://de.gentoo-wiki.com/wiki/TeVii_S660_DVB-S2_USB](http://de.gentoo-wiki.com/wiki/TeVii_S660_DVB-S2_USB) the card needs two firmware files that can installed using

```

wget http://www.tevii.com/linux_tevii_ds3000.rar 
unrar e linux_tevii_ds3000.rar
sudo cp -p dvb-usb-teviis660.fw /lib/firmware
sudo cp -p dvb-fe-ds3000.fw /lib/firmware

```

(from your log it looks like 'dvb-usb-teviis660.fw' is being requested so I've modified the instructions not to change the name to 'dvb-usb-s630.fw')

---

### Post by fuzzydunlop on 2010-01-29
Yes. I copied the two fw files you mentioned to /lib/firmware.

I've just checked and reinstalled but still getting the same errors.

---

### Post by Neon Dusk on 2010-01-29
This might be a long shot but there's another two files in the rar archive
dvb-fe-cx24116.fw
dvb-usb-s630.fw

Have these been copied to /lib/firmware as well? For the dvb-fe-cx24116.fw if it already exists overwrite with the one in the archive (the version in the Ubuntu packages is corrupt)

---

### Post by fuzzydunlop on 2010-01-29
Yup...they are there.

Copied them in again just now, reinstalled the tevii drivers and still the same. 

So now I have installed the tevii and the v4l sources and neither one is working for me. This is driving me nuts.:sad:

I wonder if it is related to 'Module ehci_hcd not found'. When i lsmod | grep hcd there is nothing.

---

### Post by fuzzydunlop on 2010-02-02
Has nobody else have a problem with this device?

---

### Post by Neon Dusk on 2010-02-02
> **fuzzydunlop said:**
> ...

I wonder if it is related to 'Module ehci_hcd not found'. When i lsmod | grep hcd there is nothing.

That suggests that USB 2.0 isn't working which may cause the problems that you're seeing.

---

### Post by fuzzydunlop on 2010-02-02
I don't know. Been reading so much on anything it could possibly be that I'm confused but I think I saw a thread somewhere saying that this was brought into kernel. So maybe that would explain the lack of a module?

lsusb gives
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:c058 Logitech, Inc.
Bus 002 Device 003: ID 04f2:0402 Chicony Electronics Co., Ltd
Bus 002 Device 002: ID 1784:0001 TopSeed Technology Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```It seems to partially start up. I'm seeing this in the dmesg
```

[ 3954.416039] usb 1-6: new high speed USB device using ehci_hcd and address 89
[ 3954.548757] usb 1-6: configuration #1 chosen from 1 choice
[ 3954.549635] dvb-usb: found a 'TEVII S660 DVBS2 USB2.0' in cold state, will tr
y to load a firmware
[ 3954.549651] usb 1-6: firmware: requesting dvb-usb-teviis660.fw
[ 3954.562172] dvb-usb: downloading firmware from file 'dvb-usb-teviis660.fw'
[ 3954.562186] usb 1-6: firmware: requesting dvb-usb-teviis660.fw
[ 3954.579926] teviis660: start downloading TEVIIS660 firmware
[ 3954.709614] dvb-usb: found a 'TEVII S660 DVBS2 USB2.0' in warm state.
[ 3954.709747] dvb-usb: will pass the complete MPEG2 transport stream to the sof
tware demuxer.
[ 3954.740416] DVB: registering new adapter (TEVII S660 DVBS2 USB2.0)
[ 3954.804346] teviis660: read eeprom failed
[ 3954.804358] dvb-usb: MAC address reading failed.
[ 3954.891450] Invalid probe, probably not a DS3000 device
[ 3954.891770] dvb-usb: no frontend was attached by 'TEVII S660 DVBS2 USB2.0'
[ 3954.956794] input: IR-receiver inside an USB DVB receiver as /devices/pci0000
:00/0000:00:04.1/usb1/1-6/input/input1248
[ 3954.956911] dvb-usb: schedule remote query interval to 150 msecs.
[ 3954.956922] dvb-usb: TEVII S660 DVBS2 USB2.0 successfully initialized and con
nected.
[ 3954.957030] usb 1-6: USB disconnect, address 89
[ 3955.001046] dvb-usb: TEVII S660 DVBS2 USB2.0 successfully deinitialized and d
isconnected.

```

syslog extract
```

Feb  2 17:58:35 AOK-mythtv kernel: [ 7329.832031] usb 1-6: new high speed USB device using ehci_hcd and address 127
Feb  2 17:58:35 AOK-mythtv kernel: [ 7329.965473] usb 1-6: configuration #1 chosen from 1 choice
Feb  2 17:58:35 AOK-mythtv kernel: [ 7329.966258] dvb-usb: found a 'TEVII S660 DVBS2 USB2.0' in cold state, will try to load a firmware
Feb  2 17:58:35 AOK-mythtv kernel: [ 7329.966273] usb 1-6: firmware: requesting dvb-usb-teviis660.fw
Feb  2 17:58:35 AOK-mythtv kernel: [ 7329.979865] dvb-usb: downloading firmware from file 'dvb-usb-teviis660.fw'
Feb  2 17:58:35 AOK-mythtv kernel: [ 7329.979878] usb 1-6: firmware: requesting dvb-usb-teviis660.fw
Feb  2 17:58:35 AOK-mythtv kernel: [ 7329.993630] teviis660: start downloading TEVIIS660 firmware
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.124272] dvb-usb: found a 'TEVII S660 DVBS2 USB2.0' in warm state.
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.124377] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.156611] DVB: registering new adapter (TEVII S660 DVBS2 USB2.0)
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.220067] teviis660: read eeprom failed
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.220078] dvb-usb: MAC address reading failed.
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.304043] Invalid probe, probably not a DS3000 device
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.304270] dvb-usb: no frontend was attached by 'TEVII S660 DVBS2 USB2.0'
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.369301] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-6/input/input1410
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.369428] dvb-usb: schedule remote query interval to 150 msecs.
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.369439] dvb-usb: TEVII S660 DVBS2 USB2.0 successfully initialized and connected.
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.369544] usb 1-6: USB disconnect, address 127
Feb  2 17:58:35 AOK-mythtv kernel: [ 7330.405021] dvb-usb: TEVII S660 DVBS2 USB2.0 successfully deinitialized and disconnected.

```

Any ideas?

---

### Post by Purple8 on 2010-02-09
mine was working fine. And now does not with latest kernal. Booting into old one at mo

---

### Post by fuzzydunlop on 2010-02-10
Just an update...I'm returning this device for replacement as I think it may be faulty in my case. When I get the new one I will see if things are still the same.

@Purple8 - please let us know how you get on with an alternative kernel version.

---

### Post by Purple8 on 2010-02-16
dont seem to want to install on the latest 9.04. so still booting into th -17 kernel

---

### Post by utar on 2010-02-17
This may not be any help but I have the S650.  I'm not sure if there is any difference between the two from Tevii's website other then a different case as the specs are the same.

The S650 worked for me out of the box on 9.10 once I had copied the correct fw files.  I did note that an fw update broke it again by overwriting the fw files with incorrect ones.

You may just want to double check that you are using the correct fw files, and in particular overwrite any existing ones using the ones from Tevii's website.



Utar

---

### Post by fuzzydunlop on 2010-04-28
UPDATE: For anyone that was having this problem I hope this helps.

Since using the latest drivers from Tevii site (April 2010) I'm now picking up an adapter and am scanning channels.

---

### Post by SnoopFogg on 2010-06-20
Hi, I'm having some problems setting up Freesat using a Tevii s660 USB stick on a REVO with Ubuntu 10.4.  I've followed the instructions on this post and downloaded the latest drivers from the Tevii site but I'm not able to scan for channels.  

To scan for free channels I enter in the terminal: 
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf

In response I get: 
WARNING: frontend type (OFDM) is not compatible with requested tuning type (QPSK)
ERROR: initial tuning failed
dumping lists (0 services)
Done.

"grep -i dvb /var/log/messages" shows:
Jun 19 20:39:59 russ-revo kernel: [ 3423.963677] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
Jun 19 20:39:59 russ-revo kernel: [ 3423.963688] usb 1-4: firmware: requesting dvb-usb-teviis660.fw
Jun 19 20:39:59 russ-revo kernel: [ 3423.968740] dvb-usb: downloading firmware from file 'dvb-usb-teviis660.fw'
Jun 19 20:39:59 russ-revo kernel: [ 3424.100050] dvb-usb: found a 'TeVii S660 USB' in warm state.
Jun 19 20:39:59 russ-revo kernel: [ 3424.100171] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun 19 20:39:59 russ-revo kernel: [ 3424.132135] DVB: registering new adapter (TeVii S660 USB)
Jun 19 20:40:25 russ-revo kernel: [ 3449.731290] dvb-usb: MAC address: 00:00:00:00:00:00
Jun 19 20:40:25 russ-revo kernel: [ 3450.415460] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/input/input7
Jun 19 20:40:25 russ-revo kernel: [ 3450.415712] dvb-usb: schedule remote query interval to 150 msecs.
Jun 19 20:40:25 russ-revo kernel: [ 3450.415725] dvb-usb: TeVii S660 USB successfully initialized and connected.
Jun 19 20:40:25 russ-revo kernel: [ 3450.482262] dvb-usb: TeVii S660 USB successfully deinitialized and disconnected.

Not sure what the last line is about and why it goes disconnected.

I already use a Hauppauge Nova-TD Stick for Freeview which works fine. "grep -i dvb /var/log/messages" shows:

Jun 20 09:58:12 russ-revo kernel: [   20.374807] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in warm state.
Jun 20 09:58:12 russ-revo kernel: [   20.375895] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun 20 09:58:12 russ-revo kernel: [   20.376675] DVB: registering new adapter (Hauppauge Nova-TD Stick (52009))
Jun 20 09:58:12 russ-revo kernel: [   20.842793] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
Jun 20 09:58:12 russ-revo kernel: [   21.067529] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun 20 09:58:12 russ-revo kernel: [   21.067799] DVB: registering new adapter (Hauppauge Nova-TD Stick (52009))
Jun 20 09:58:12 russ-revo kernel: [   21.236779] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
Jun 20 09:58:12 russ-revo kernel: [   21.479735] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-1/input/input3
Jun 20 09:58:12 russ-revo kernel: [   21.479854] dvb-usb: schedule remote query interval to 50 msecs.
Jun 20 09:58:12 russ-revo kernel: [   21.479863] dvb-usb: Hauppauge Nova-TD Stick (52009) successfully initialized and connected.
Jun 20 09:58:12 russ-revo kernel: [   21.482341] usbcore: registered new interface driver dvb_usb_dib0700
 
Any help much appreciated to fix the Tevii s660 problem.

---

### Post by SnoopFogg on 2010-06-22
UPDATE: For anyone that was having this problem: 

"TeVii S660 USB successfully deinitialized and disconnected" 

I removed the other USB I had plugged in (DVB-T) and I can now pick up an adaptor and scan channels.

---

### Post by SnoopFogg on 2010-07-01
I was able to scan initially and could see the channels being scanned. Now I'm not able to scan. Error message:

WARNING: frontend type (OFDM) is not compatible with requested tuning type (QPSK)
ERROR: initial tuning failed.

This is after I tried to reinstall the drivers from the tevii support site.  Although I downloaded them I'm not sure that reinstalled the drivers as the file that downloaded looks very different from the one I downloaded the first time and the instructions don't work anymore.  I'm not sure how to copy the firmware files as the readme instruction suggest (cp *.fw /lib/firmware).

It's strange because it looks like it should be working - grep -i dvb /var/log/messages shows:
 
Jul  1 20:58:50 russ-revo kernel: [   29.081559] dvb-usb: TeVii S660 USB successfully initialized and connected.

Can anyone tell me how to install the new drivers? Or suggest some other way to get this working?

---

### Post by SnoopFogg on 2010-07-04
Hi, can anyone give me an idiots guide to installing the new Linux drivers from the Tevii site for the S660? ([http://www.tevii.com/Support.asp](http://www.tevii.com/Support.asp)  5th one down on the list)

It used to be reasonably straight forward:
# cp *.fw /lib/firmware
# tar xjvf linux-tevii-ds3000.tar.bz2
# cd linux-tevii-ds3000
# make && make install

The files have now changed and these instructions no longer apply.  Has anyone tried these new drivers on Ubuntu 10.4 and got the S660 to work?

---

### Post by SOME1 on 2010-07-05
I bought tevii s660 yesterday and I installed it on 10.04 with the same instructions you mention and its seems to install ok. I haven't test it yet but if you can explain what is the problem with the installation maybe I can help.

---

### Post by SnoopFogg on 2010-07-07
BUMP - Seeking advice on how to install the new drivers for Tevii S660.  Looking at the rest of this thread and having seen this device scan before, I am sure it can work.  Otherwise any suggestions gratefully received.

---

### Post by SnoopFogg on 2010-07-07
Sorry, I missed response from SOME1!  I have seen the device scan before, though it didn't complete.  When I tried again I get an error message:

WARNING: frontend type (OFDM) is not compatible with requested tuning type (QPSK)
ERROR: initial tuning failed.

Were you able to download the drivers from the Tevii site and use the instructions to install?  The file in the drivers on the site appear different from the ones I used previously so don't know what to do with them.  The device is recognised and says it has installed - I just can't scan now.  Let me know what other information would be useful.

---

### Post by SOME1 on 2010-07-07
Strange error, I didn't get that when I installed it. 
I suggest you try to connect the tevii to a different USB port, see if it change something. 

just to make sure you did what I did to install it: (on Ubuntu 10.04)
you download the [this file]("http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar"), extract it to your home page (make sure the directory name you extract the files to it has only english letters!). 
next you run on terminal 
```
sudo apt-get install linux-headers-`uname -r` build-essential
```
that will install everything you need to compile the installation. 

next in terminal you cd to the directory you extract the installion file on it and run
```
sudo cp *.fw /lib/firmware
```
```
sudo tar xjvf linux-tevii-ds3000.tar.bz2
```
```
sudo cd linux-tevii-ds3000
```
```
sudo make
```
```
sudo make install
```

and you got somewhere the error you wrote?

---

### Post by EllamsR on 2010-07-08
Jumping in on this thread...  I also have a Revo R3610 running Ubuntu 10.04 (love it :)) and am looking for a USB2 DVB-S2 tuner with Disequ 1.2 support.  This box had caught my eye. Can anyone report that they have this Tevii working to view/record UK Freesat channels (including BBC HD)?   Are there any _known working_ alternatives?

---

### Post by SOME1 on 2010-07-12
For everyone who try to install\use tevii s660 on ubuntu 10.04 unsuccessfully - 

I send an email to tevii support and this is what they wrote me back: 

> Dear Sir, 

Thanks for using TeVii product,

We are making driver for Ubuntu10.04 now, give us more time please.

Meanwhile, your can try to searching driver on linux website [www.linuxtv.org](www.linuxtv.org) 

Thanks!!
TeVii Support

hope this will help for who trying to use it on 10.04.

---

### Post by SnoopFogg on 2010-07-13
Many thanks SOME1 for the very clear instructions.  I used them and was able to scan for channels.  The process took 6.5 hrs (vs. the 20 minutes I was expecting from instructions on the Parker1 site).  Finally I got a channels.conf file with something in it, but still unable to view any channels. Plus I keep having to unplug the usb back in for the device to be recongised.

At least I know I'm not going mad now.  Guess I can install 9.10 and have more luck, this being the main reason for running it on a Revo attached to the main TV.

---

### Post by fuzzydunlop on 2010-07-15
> **EllamsR said:**
> Jumping in on this thread...  I also have a Revo R3610 running Ubuntu 10.04 (love it :)) and am looking for a USB2 DVB-S2 tuner with Disequ 1.2 support.  This box had caught my eye. Can anyone report that they have this Tevii working to view/record UK Freesat channels (including BBC HD)?   Are there any _known working_ alternatives?

This device works ok with current drivers on 10.04. However, I am still having problems with reliable Diseqc on it. I'm hoping the flaky diseqc will be addressed in updated drivers.

---

### Post by charlie0440 on 2010-08-13
[COLOR=Black]Hi,

I used to use my Tevii s660 with Ubuntu - I did run into problems, so I switched to yaVDR as the OS, for anyone that wants a PVR - it worked out the box once the OS was installed - highly recommended easy to set up.

Anyway off memory this is how I installed mine on Ubuntu for anyone having problems:

[/COLOR]    [COLOR=Black]1) Download  drivers from Tevii website
2) Unzip the download[/COLOR][COLOR=Black]
3) Open Readme and follow instructions  -> copy firmware to lib/firmware folder, unzip tar, etc etc
[/COLOR]
    [COLOR=Black]4) sudo make[/COLOR]
[COLOR=Black]5) sudo make install[/COLOR]
[COLOR=Black]
If it does not work I remember I had to do this:

In a terminal type:
[/COLOR][COLOR=Black]dmesg | grep dvb

This gave me a message like, found a tevii .. in cold state
looking for firmware [/COLOR][COLOR=Black]usb-dvb-s660.fw[/COLOR][COLOR=Black]  file not found

So I did step 6
[/COLOR][COLOR=Black]
6) backup the relevant driver [/COLOR][COLOR=Black]- teviis660.fw[/COLOR][COLOR=Black] (cp [/COLOR][COLOR=Black]teviis660.fw[/COLOR][COLOR=Black] [/COLOR][COLOR=Black]teviis660backup.fw[/COLOR][COLOR=Black]) [/COLOR][COLOR=Black] 
then rename (mv)  the driver to the name it is looking for in dmesg | grep dvb ie:

[/COLOR]
    [COLOR=Black]mv teviis660.fw  usb-dvb-s660.fw[/COLOR]
[COLOR=Black]
I believe that fixed my problem last time. I have to reinstall Ubuntu in the next few days so I will be trying it out later - If i run into problems / success I will post back (sorry about the blue boxes - pasted from my email)
[/COLOR]

---

### Post by charlie0440 on 2010-08-13
> **SnoopFogg said:**
> 

To scan for free channels I enter in the terminal: 
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf



Sorry haven't read the whole thread to see if any1 replied

I did my scan via:

sudo sh -c "scan -o vdr /usr/share/dvb/dvb-s/Astra-19.2E >  /var/lib/vdr/channels.conf"

Also a good scanning guide is here: [http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php)

You can download channel lists from here: [http://www.vdr-settings.com/download/channels/](http://www.vdr-settings.com/download/channels/)

Hope this helps

---

### Post by SOME1 on 2010-09-29
every one here with tevii s660 card & ubuntu 10.10 - 
I think I have a solution about how to enable tevii s660 on ubuntu 10.10 until tevii came out with official driver. I am testing it now. I will write about it soon.

---

### Post by SOME1 on 2010-10-05
So as I wrote, Tevii sent me a new beta driver. this beta driver does not work for me in ubuntu 10.10 beta. 
in ubuntu 10.10 rc, ubuntu said that he found restricted driver for my tevii s660 but the s660 does not work for me after installing the restricted driver from ubuntu. 
so I take the beta driver from tevii, and I used the v4l cvs version and modified it until I got the tevii s660 to work on ubuntu 10.10. 

I attaching this post a link to download my modified driver, after tevii approved it to me. 
please notice: 
1. this is NOT an official tevii driver. if tevii will come out with an update driver for ubuntu 10.10 you should use their driver. 
2. I DO NOT TAKE ANY RESPONSIBILITY about anything that may happens using this driver. if you decided to try it - you take all the responsibility on yourself.
3. please read the readme file to install it properly. it's a little different from the official tevii driver.

If you want to use my modified driver, you can download it [from here]("http://rapidshare.com/files/423271267/S660_10.10.zip"). [Edit: mirror download [from here]("http://d01.megashares.com/dl/2df7a5e/S660_10.10.zip")]

after installation: 
1. please reboot after the installation. 
2. to check out if your installation work, please check the directory /dev: if you have there a folder named dvb (/dev/dvb) your installation was successful. 
3. if you can't see /dev/dvb directory after reboot, try to plugout the power source from your s660 card and then plug it in. wait about 30 seconds and check /dev/dvb again.

I will be happy to read your response about it.
thanks.

Edit - Notice for kernel upragdes
1. If you have a kernel upgrade (via system upgrade in ubuntu), like in the official Tevii driver, the driver stop to work. 
2. In order to make it work again you need to reinstall the driver. please do the follow before reinstall the driver: 
- in terminal run the command "sudo unlink /lib/modules/2.6.29.4-167.fc11.i686.PAE". 
3. DO NOT USE a previous unpack driver. you must extract it again and install it again.

---

### Post by SnoopFogg on 2010-10-21
Ok, was watching BBC HD after successfully installing with no problems last night.  However it stopped working today.  Followed the instructions above (sudo unlink /lib/modules/2.6.29.4-167.fc11.i686.PAE) and reinstalled.  Now get:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

And:

russ@revo:~$ dmesg | grep dvb
[   10.773574] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
[   11.110448] dvb-usb: downloading firmware from file 'dvb-usb-s660.fw'
[   11.232050] dvb-usb: found a 'TeVii S660 USB' in warm state.
[   11.232185] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.368031] dvb-usb: MAC address: ff:ff:ff:ff:ff:ff
[   15.532855] dvb-usb: no frontend was attached by 'TeVii S660 USB'
[   15.533259] dvb-usb: schedule remote query interval to 150 msecs.
[   15.533272] dvb-usb: TeVii S660 USB successfully initialized and connected.
[   15.553605] dvb-usb: TeVii S660 USB successfully deinitialized and disconnected.
[   15.925954] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
[   15.941019] dvb-usb: downloading firmware from file 'dvb-usb-s660.fw'
[   20.585367] dvb-usb: found a 'TeVii S660 USB' in warm state.
[   20.585544] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   24.704025] dvb-usb: MAC address: 00:18:bd:5c:46:58
[   24.753756] dvb-usb: schedule remote query interval to 150 msecs.
[   24.753769] dvb-usb: TeVii S660 USB successfully initialized and connected.
[  600.492202]  [<f825a7f5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
[  600.492256]  [<f82cd1aa>] dvb_usb_adapter_frontend_exit+0x1a/0x30 [dvb_usb]
[  600.492271]  [<f82cc4fa>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
[  600.492289]  [<f82cc5e2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]
[  720.492148]  [<f825a7f5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
[  720.492189]  [<f82cd1aa>] dvb_usb_adapter_frontend_exit+0x1a/0x30 [dvb_usb]
[  720.492200]  [<f82cc4fa>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
[  720.492213]  [<f82cc5e2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]
[  840.492150]  [<f825a7f5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
[  840.492192]  [<f82cd1aa>] dvb_usb_adapter_frontend_exit+0x1a/0x30 [dvb_usb]
[  840.492202]  [<f82cc4fa>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
[  840.492215]  [<f82cc5e2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]
[  960.492145]  [<f825a7f5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
[  960.492187]  [<f82cd1aa>] dvb_usb_adapter_frontend_exit+0x1a/0x30 [dvb_usb]
[  960.492198]  [<f82cc4fa>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
[  960.492211]  [<f82cc5e2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]
[ 1080.492197]  [<f825a7f5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
[ 1080.492258]  [<f82cd1aa>] dvb_usb_adapter_frontend_exit+0x1a/0x30 [dvb_usb]
[ 1080.492280]  [<f82cc4fa>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
[ 1080.492307]  [<f82cc5e2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]
[ 1200.492148]  [<f825a7f5>] dvb_unregister_frontend+0xa5/0xf0 [dvb_core]
[ 1200.492190]  [<f82cd1aa>] dvb_usb_adapter_frontend_exit+0x1a/0x30 [dvb_usb]
[ 1200.492201]  [<f82cc4fa>] dvb_usb_exit+0x4a/0xf0 [dvb_usb]
[ 1200.492214]  [<f82cc5e2>] dvb_usb_device_exit+0x42/0x60 [dvb_usb]

Any ideas why was working, but not now?

---

### Post by SOME1 on 2010-11-01
did you try to plug off the power source from your tevii s660, wait 30 seconds and plug it to the power source again? 

btw, if you edit existing message I cant see it. you must post new reply so I can get an email on a new reply to help you on time. thanks.

---

### Post by reevery on 2010-11-06
In trying to install the S2* drivers from tevii's website, and trying to reinstall the drivers as per the instructions again, I've discovered my ubuntu doesn't have 2.6.29.4-167.fc11.i686.PAE.

I've just done a kernel update so I think the reason why my device has now disappeared is because I need to do the unlink, but the file isn't there. What am I missing?

---

### Post by SOME1 on 2010-11-06
you didn't write what is the version of mythbuntu you are running. 
if you run 10.04 or older you should use tevii driver. 
if you run 10.10 tevii driver probably won't work. you should use the driver I published here. 

about the error, please try the following on your terminal: 

sudo ln -s /lib/modules/$(uname -r) /lib/modules/2.6.29.4-167.fc11.i686.PAE

and recompile again. if you are getting an error about firedtv, please do not use "sudo make", use 
sudo make CONFIG_DVB_FIREDTV:=n 
instead.

---

### Post by reevery on 2010-11-10
Well, actually it's just Ubuntu 10.4 and the standard Myth installation from there, which may explain some of the issues, this is the closest active discussion I've found about the S660.

Suffice to say, your suggestion worked and the device exists again. Thank you.

I still have some work to do as I can't get the full list of channels (Freesat in the UK). There are a few things I need to try out though, but none of the scans apparently pick up any channels on the transports.

---

### Post by SOME1 on 2010-11-11
I know tevii have 2 different s660 models - old one and new one. 
The difference between old S660 & new S660 is the LNB control through GPIO. I don't think you can know if you have the old one or the new one, but please report if you have problems in switching DiSEqC. 
The driver should support the old & the new s660, but I make one more check for this subject in the following days. 

also, please try to use kaffeine to see if you can scan channels. 
if you use vdr, please try to use scan instead w_scan. 

I will report here after I'll dig to the code again. 

thanks.

---

### Post by reevery on 2010-11-12
Ok sorry for the delay in replying. I've managed to get the device back so that's a start.

Scan is not a problem - that gives me a list of channels. But, I can't tune them (using mplayer). When doing a full scan (as per parker1.co.uk instructions) in myth it doesn't find anything at all. It does find channels when importing the channels.conf file I created from scan, but then I can't get any EIT data.

Am I doing something wrong?

---

### Post by SOME1 on 2010-11-13
in order to know if this is a software problem or a driver problem, please install kaffeine by

sudo apt-get install kaffeine

and scan and try to watch with it. if it's not working its probably a driver problem. if its working its probably a software problem. 
please report about the results. 

thanks.

---

### Post by mutant_matt on 2011-03-13
I have a brand new S660 USB, and the problem I've having is, the kernel recognises the device being plugged in, but does nothing further.  It sees the device, but doesn't give it a "name", so I am guessing that it doesn't know what to do with the device ID of 9022:d660.  sudo lsusb provides:

Bus 002 Device 002: ID 0d3d:0001 Tangtop Technology Co., Ltd HID Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 9022:d660  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I am using the latest version of the s2_liplianin source, as pointed to and recommended by Tevii support.  The make and make install seemed to go ok, I used the make command: sudo make CONFIG_DVB_FIREDTV:=n

If I do a search: find . -exec grep -H 9022pD6 {} \;

the only files that match, are:

~/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dvb-usb-dw2102.mod.o
~/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dvb-usb-dw2102.mod.ko
~/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dvb-usb-dw2102.mod.c

I presume that the ultimate module gets built from these files?

If I cat:

~/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dvb-usb-dw2102.mod.c

it shows that the device ID should be known and recognised (extra lines added to highlight entry):

MODULE_ALIAS("usb:v04B4p2102d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v04B4p2101d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v04B4p2104d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v9022pD650d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v0CCDp0064d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v9022pD651d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v04B4p3101d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v9022pD630d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v3011pB012d*dc*dsc*dp*ic*isc*ip*");

MODULE_ALIAS("usb:v9022pD660d*dc*dsc*dp*ic*isc*ip*");  (**HERE**)

MODULE_ALIAS("usb:v3034p7500d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v1F4Dp3000d*dc*dsc*dp*ic*isc*ip*");
MODULE_ALIAS("usb:v0CCDp00A8d*dc*dsc*dp*ic*isc*ip*");


If I do a: sudo modinfo dvb-usb-dw2102 I get:

filename:       /lib/modules/2.6.32-29-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dw2102.ko
license:        GPL
version:        0.1
description:    Driver for DVBWorld DVB-S 2101, 2102, DVB-S2 2104, DVB-C 3101 USB2.0, TeVii S600, S630, S650 USB2.0 devices
author:         Igor M. Liplianin (c) [email]liplianin@me.by[/email]
srcversion:     4D151F7D8E22B91F8C883FC
alias:          usb:v9022pD630d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CCDp0064d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD650d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2102d*dc*dsc*dp*ic*isc*ip*
depends:        dvb-usb
vermagic:       2.6.32-29-generic SMP mod_unload modversions 586 
parm:           debug:set debugging level (1=info 2=xfer 4=rc(or-able)). (debugging is not enabled) (int)
parm:           keymap:set keymap 0=default 1=dvbworld 2=tevii 3=tbs  ... (int)
parm:           adapter_nr:DVB adapter numbers (array of short)


Because the S660 is not listed, I backed up:

/lib/modules/2.6.32-29-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dw2102.ko

and

/lib/modules/2.6.32-29-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb.ko

and copied in the versions that were built from:

~/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/

After a reboot, sudo modinfo dvb-usb-dw2102 now shows it's in the list:

filename:       /lib/modules/2.6.32-29-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dw2102.ko
license:        GPL
version:        0.1
description:    Driver for DVBWorld DVB-S 2101, 2102, DVB-S2 2104, DVB-C 3101 USB2.0, TeVii S600, S630, S650, S660 USB2.0, Prof 1100, 7500 USB2.0, Geniatech SU3000 devices
author:         Igor M. Liplianin (c) [email]liplianin@me.by[/email]
srcversion:     CEE6B5D0D310192A608E275
alias:          usb:v0CCDp00A8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1F4Dp3000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3034p7500d*dc*dsc*dp*ic*isc*ip*

alias:          usb:v9022pD660d*dc*dsc*dp*ic*isc*ip* (**HERE**)

alias:          usb:v3011pB012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD630d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD651d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CCDp0064d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD650d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2102d*dc*dsc*dp*ic*isc*ip*
depends:        dvb-usb
vermagic:       2.6.32-29-generic SMP mod_unload modversions 586 
parm:           debug:set debugging level (1=info 2=xfer 4=rc(or-able)). (int)
parm:           keymap:set keymap 0=default 1=dvbworld 2=tevii 3=tbs  ... 256=none (int)
parm:           demod:demod to probe (1=cx24116 2=stv0903+stv6110 4=stv0903+stb6100(or-able)). (int)
parm:           adapter_nr:DVB adapter numbers (array of short)


but, the output from kern.log and lsusb, haven't changed.  It still doesn't appear to recognise the USB device ID or know what to do with it.  I am at this point, stumped!  

Should I have had to copy the two kernel modules at all?  Not doing so, makes the 660 not listed in the loaded module, so I presumed this had to be done?  Perhaps this would indicate a build issue after all? 

I'm running 10.04LTS, Kernel 2.6.32-29-generic #58-Ubuntu SMP (32bit)

Any Help, very gratefully received!! :)  (I need to get this working, 'cos I was planning on buying the S480 next, to have 3 S2 tuners in my myth box :( )

Cheers,

Matt.

---

### Post by SOME1 on 2011-03-13
your post is very confusing. 
If I get it right, You are running ubuntu 10.04 and you compiled the driver from tevii website. 

I attached this post a zip file. open it and copy the 2 files in this zip to /lib/firmware directory. 

then _redownload and repack_ the driver from tevii website to a new directory. cd to that directory and run

> sudo make CONFIG_DVB_FIREDTV:=n 

if it finished ok (and didn't returned an error) run after it this command
> sudo make install

**and reboot. **
 
to check out if your installation work, please check the directory /dev: if you have there a folder named dvb (/dev/dvb) your installation was successful. 

you can also try to install kaffeine 

> sudo apt-get install kaffeine

and try to scan for channels with it. 

please write here the results.

---

### Post by mutant_matt on 2011-03-13
I appreciate your help! :)

I re-downloaded the Linux driver from the Tevii website (Tevii_s2_liplianin_1.tar), which when un-tared, contains a folder called tevii_s2_liplianin-eb8a914cd499.  I cd'd into that, unzipped your file, copied the firmware files into /lib/firmware.

There were no errors or anything that looked out of place from the sudo make CONFIG_DVB_FIREDTV:=n command, but itself (I logged that to file), but the console did have the following error output:


/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/va1j5jf8007s.c:596: warning: initialization from incompatible pointer type
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/va1j5jf8007t.c:445: warning: initialization from incompatible pointer type
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/jpeg.h:152: warning: 'jpeg_set_qual' defined but not used
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/ir-raw-event.c: In function 'ir_raw_event_register':
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/ir-raw-event.c:192: warning: 'rc' may be used uninitialized in this function
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/v4l2-dev.c:371: warning: initialization from incompatible pointer type
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/cu1216.c:395: warning: 'cu1216_read_quality' defined but not used
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dst.c:1771: warning: initialization from incompatible pointer type
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dst.c:1797: warning: initialization from incompatible pointer type
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dst.c:1831: warning: initialization from incompatible pointer type
/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/dst.c:1854: warning: initialization from incompatible pointer type
WARNING: "snd_aci_get_aci" [/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/radio-miropcm20.ko] undefined!
WARNING: "snd_aci_cmd" [/home/matt/tevii/tevii_s2_liplianin-eb8a914cd499/v4l/radio-miropcm20.ko] undefined!


The make install looks ok and had no problems, so I did reboot, and now, at least, when I plug the 660 in, I get the following in the kern.log/dmesg/syslog:


[   66.520049] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   66.653826] usb 1-2: configuration #1 chosen from 1 choice
[   66.898338] dvb_usb: disagrees about version of symbol dvb_dmxdev_init
[   66.898351] dvb_usb: Unknown symbol dvb_dmxdev_init
[   66.899936] dvb_usb: disagrees about version of symbol dvb_register_adapter
[   66.899947] dvb_usb: Unknown symbol dvb_register_adapter
[   66.901761] dvb_usb: disagrees about version of symbol dvb_dmx_swfilter_204
[   66.901769] dvb_usb: Unknown symbol dvb_dmx_swfilter_204
[   66.902097] dvb_usb: disagrees about version of symbol dvb_dmx_release
[   66.902104] dvb_usb: Unknown symbol dvb_dmx_release
[   66.902828] dvb_usb: disagrees about version of symbol dvb_net_init
[   66.902835] dvb_usb: Unknown symbol dvb_net_init
[   66.903162] dvb_usb: disagrees about version of symbol dvb_dmx_swfilter
[   66.903169] dvb_usb: Unknown symbol dvb_dmx_swfilter
[   66.903558] dvb_usb: disagrees about version of symbol dvb_dmxdev_release
[   66.903565] dvb_usb: Unknown symbol dvb_dmxdev_release
[   66.904136] dvb_usb: disagrees about version of symbol dvb_frontend_detach
[   66.904145] dvb_usb: Unknown symbol dvb_frontend_detach
[   66.904626] dvb_usb: disagrees about version of symbol dvb_net_release
[   66.904634] dvb_usb: Unknown symbol dvb_net_release
[   66.905091] dvb_usb: disagrees about version of symbol dvb_unregister_frontend
[   66.905103] dvb_usb: Unknown symbol dvb_unregister_frontend
[   66.906060] dvb_usb: disagrees about version of symbol dvb_register_frontend
[   66.906069] dvb_usb: Unknown symbol dvb_register_frontend
[   66.906521] dvb_usb: disagrees about version of symbol dvb_unregister_adapter
[   66.906532] dvb_usb: Unknown symbol dvb_unregister_adapter
[   66.906849] dvb_usb: disagrees about version of symbol dvb_dmx_init
[   66.906857] dvb_usb: Unknown symbol dvb_dmx_init


This is an improvement of sorts, but it looks like I have a build problem?

(due to the above, I wasn't expecting, and didn't get, any /dev/dvb folder created).

Any ideas?  I have seen a couple of posts when googling around, suggesting that there might be problems with the S660 drivers on kernel 2.6.32, which is what I am currently running!?

Out of interest, what is the output of your lsusb?  Do you have an identifier string against your device ID?  Mine is still blank, just:

Bus 001 Device 003: ID 9022:d660

Many Thanks again,

Matt.

---

### Post by SOME1 on 2011-03-13
Hi Matt, 

please try [this driver]("http://rapidshare.com/files/452401614/Tevii_S660_cd499.zip") - this is a modified driver that I have changed in the past to make the driver work on Ubuntu 10.04. 
I don't know if it works after the last ubuntu updates, but it's worth trying. 

I can't attached it to this post since there is a max limit for files sizes (1MB) here. 

Please write the results here again. 

thanks.

---

### Post by mutant_matt on 2011-03-13
Thanks for that.  Unfortunately, the same build errors, and the same errors in the kern.log/dmesg/syslog.  What is it about that version that differs from the cd499 that seems to be the current source project version?

Does anybody have it working on kernel 2.6.32 (and/or 10.04 and if so, which kernel).  Perhaps the beta driver for (Ubuntu) 10.10 might be worth a go, as that was built with kernel => 2.6.35 (Ubuntu 10.10) in mind?

I might build a test box on 10.10 and give it try there.

Any other ideas at this point, would be very welcome! ;) :)

Cheers,

Matt.

---

### Post by SOME1 on 2011-03-14
Hi Matt, 

Did you tried to use the official previous drivers? 
The previous drivers made for 10.04. there is 2 versions of it: 
[this is the the first one]("http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar") from Tevii website and [This is the second]("http://www.tevii.com/s2-liplianin_tevii_20100820.tgz").

I will try to install 10.04 on a virtual machine to check your problem if it does not work too.

---

### Post by mutant_matt on 2011-03-14
OK, so I've tried both of those as well, and pretty much get the same set of make errors, and exactly the same set of errors in the dmesg/kern.log/syslog on startup (or when I plug the S660 into the USB).

Perhaps I broke something on the first attempt and every subsequent build is affected by that somehow?

How do I "uninstall" the stuff I built, and revert to the standard Ubuntu repository version of v4l? (I presume that is what I need to do to get back to "standard"?)

If I can get back to "clean", perhaps I can then try the one most people seem to have got working, the Tevii_100315_Beta_linux_tevii_ds3000.rar version.

I do wonder though, if the problem is that the kernel version at that time, worked with this stuff, but it doesn't work with the current kernel version now for 10.04 (2.6.32)?

Thoughts?

Cheers,

Matt.

---

### Post by SOME1 on 2011-03-14
ok, I will install 10.04 on a virtual machine and try to see whats the problem there. 

If you solved it meanwhile, please write here. 

thanks.

---

### Post by mutant_matt on 2011-03-16
Interestingly, I built a 10.10 VM tonight, and out of the box, the 660 is recognised (with the cannot find firmware messages).  So I copied the firmware files in, and it's close.  I now get:

[  949.380265] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  949.541397] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
[  949.580221] dvb-usb: downloading firmware from file 'dvb-usb-s630.fw'
[  949.580289] dw2102: start downloading DW210X firmware
[  950.476230] dvb-usb: found a 'TeVii S660 USB' in warm state.
[  950.481188] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  950.485944] DVB: registering new adapter (TeVii S660 USB)
[  956.648256] dvb-usb: MAC address: 00:00:00:00:00:00
[  956.772167] Only Zarlink VP310/MT312/ZL10313 are supported chips.
[  957.072148] Invalid probe, probably not a DS3000
[  957.072857] dvb-usb: no frontend was attached by 'TeVii S660 USB'
[  957.085775] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/input/input4
[  957.086624] dvb-usb: schedule remote query interval to 150 msecs.
[  957.086699] dvb-usb: TeVii S660 USB successfully initialized and connected.
[  957.086931] usb 1-1: USB disconnect, address 3
[  957.099350] dvb-usb: TeVii S660 USB successfully deinitialized and disconnected.

After this, lsusb shows no device, so it's as if it sees it, doesn't complete the setup, and disconnects it from the bus, even though it's still physically connected.  I've tried a few reboots/power cycles etc, but this is consistently like this.

At this point, do I need to make/make install from the current project/one of the projects on the Tevii website?

I was going to use 10.04LTS as the base for the box, but if it's more straight forward to get this working in 10.10, as I've got to build the new box anyway, I'm not that fussed.

Thoughts/suggestions?

Cheers,

Matt :)

---

### Post by SOME1 on 2011-03-18
I am installing now 10.04 as I promised. I will write here again after I finish the tevii install too. 
I just want to say that I did a system upgrade for 10.10 today with a kernel update and the tevii device stopped to work and refuse to work after the driver reinstall too. I solved it very simply - I removed the power source from the tevii s660 wait and few seconds and plug it in again and it's worked. please make sure it's not your problem.

I will write here again after I check it on 10.04.

---

### Post by mutant_matt on 2011-03-18
Depriving it of power is definately not the fix for me.  I've tried lots of combinations of power off/on, reboots, different USB ports, and various combinations of this.

When you say the "Tevii install", can you give me a quick step by step? (mainly, which copy of the source you use on 10.10?).

Appreciate your continuing help! :)

Cheers,

Matt.

---

### Post by SOME1 on 2011-03-19
ok, I think I found your problem. it's a problem for those who use unstable ubuntu tree in 10.10 too. 
looks like there is some kind of a conflict between the ubuntu driver and dvb DW210X driver in the kernel. (if you enter to system->administration->restricted drivers manager - do you see a driver for dvb? if yes and it's active, please stop using it).
The driver stopped work on my pc too now, so I'll have to find a solution. 
I will dig into the tevii drivers code and try to figure it out. 

thanks for writing about it.

---

### Post by mutant_matt on 2011-03-19
Thanks for looking into it! (I'm out of my depth here! ;) :) )

I don't have any DVB driver in the Restricted Drivers Manager on either my 10.04 or my 10.10 VM.  On 10.10, I have no drivers in there, on 10.04, only my Nvidia graphics driver.

It sounds like though, from what you say, using standard 10.10 out of the box (presumably 10.10 "unstable" is some more bleeding edge build?), with the ds3000.rar set of source files, *that* combination, the make/make install should work (with no errors), and after a power cycle/reboot, the 660 should start working?

If that's correct, I'll give that a go in my 10.10 VM...

Let me know,

Cheers,

Matt :)

---

### Post by SOME1 on 2011-03-19
ok, please try the following: 

1. download and extract [this file]("http://rapidshare.com/files/453360132/s2-liplianin-7e47ba1d4ae8.zip"). 
2. run in your terminal the following commands: 
3. enter the directory you extracted. first remove the previous installs by running
```
sudo make rminstall
```
4. now install the driver by running
```
sudo make CONFIG_DVB_FIREDTV:=n
```

and then
```
sudo make install
```
5. now power off the tevii s660 (plug it out from the power source) and then reboot your computer. 
6. plug the power to your tevii s660 and start your computer again. 
7. check if you have the directory /dev/dvb. if you have it - it works.
8. if it's not working, go to system->administration->system log. choose in the new window the file syslog and scroll to the buttom. plug the tevii s660 out from your usb and plug it in again. write here the bold output. 
do it again for the messages file.

thanks.

---

### Post by mutant_matt on 2011-03-23
SOME1,

Many Thanks for the response, and appologies for the delay.  My "real" 10.04 still seems to be broken, I can't get it back to the point before I started fiddling, where the 660 just wasn't recognised, and I still get nasty build/kernel/driver looking errors when I plug it in.  I guess on this box, I need to somehow "reinstall" the standard dvb stuff, so it's back to how it should be on a "standard" install.  Any ideas on that one? (dpkg reconfigure or similar?).

On my 10.10 VM, I get the same as before compiling the new drivers, I get all the usual stuff in dmesg/kern.log/syslog, and the device gets "disconnected", doesn't show in lsusb, and not surprisingly, isn't created in /dev/dvb.

I will have another bash at this as soon as I can, to get you the logs you requested, and I'll post them up here.

Did you have any success with your 10.04 VM? (and I presume, you've got it working in 10.10?)

Cheers,

Matt.

---

### Post by SOME1 on 2011-03-23
Hi Matt, 

The driver I posted (the last one) installed successfully on 10.04 VM and on 10.10. 
please post here this:

go to system->administration->system log. choose in the new window the file syslog and scroll to the buttom. plug the tevii s660 out from your usb and plug it in again. write here the bold output.
do it again for the messages file.

---

### Post by mutant_matt on 2011-03-23
OK, on the 10.10 VM, when I plug it in, I get the following (I get no entries in syslog or messages, when I unplug):

syslog:

Mar 23 20:54:31 ulx-VirtualBox10-10 kernel: [  168.052325] usb 1-1: new high speed USB device using ehci_hcd and address 2
Mar 23 20:54:31 ulx-VirtualBox10-10 kernel: [  168.369480] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
Mar 23 20:54:31 ulx-VirtualBox10-10 kernel: [  168.435616] dvb-usb: downloading firmware from file 'dvb-usb-s660.fw'
Mar 23 20:54:31 ulx-VirtualBox10-10 kernel: [  168.435705] dw2102: start downloading DW210X firmware
Mar 23 20:54:32 ulx-VirtualBox10-10 kernel: [  169.348443] dvb-usb: found a 'TeVii S660 USB' in warm state.
Mar 23 20:54:32 ulx-VirtualBox10-10 kernel: [  169.352214] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Mar 23 20:54:32 ulx-VirtualBox10-10 kernel: [  169.356333] DVB: registering new adapter (TeVii S660 USB)
Mar 23 20:54:32 ulx-VirtualBox10-10 kernel: [  169.395927] usb 1-1: USB disconnect, address 2
Mar 23 20:54:32 ulx-VirtualBox10-10 kernel: [  169.398068] dvb-usb: MAC address: 01:01:01:01:01:01
Mar 23 20:54:33 ulx-VirtualBox10-10 kernel: [  169.514436] Invalid probe, probably not a DS3000
Mar 23 20:54:33 ulx-VirtualBox10-10 kernel: [  169.514648] dvb-usb: no frontend was attached by 'TeVii S660 USB'
Mar 23 20:54:33 ulx-VirtualBox10-10 kernel: [  169.519747] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/input/input4
Mar 23 20:54:33 ulx-VirtualBox10-10 kernel: [  169.520424] dvb-usb: schedule remote query interval to 150 msecs.
Mar 23 20:54:33 ulx-VirtualBox10-10 kernel: [  169.520494] dvb-usb: TeVii S660 USB successfully initialized and connected.
Mar 23 20:54:33 ulx-VirtualBox10-10 kernel: [  169.521403] dvb-usb: TeVii S660 USB successfully deinitialized and disconnected.
Mar 23 20:54:33 ulx-VirtualBox10-10 kernel: [  169.534836] usbcore: registered new interface driver dw2102


Messages:

Mar 23 20:57:11 ulx-VirtualBox10-10 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="509" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 23 20:58:01 ulx-VirtualBox10-10 kernel: [  377.780249] usb 1-1: new high speed USB device using ehci_hcd and address 3
Mar 23 20:58:01 ulx-VirtualBox10-10 kernel: [  377.939054] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
Mar 23 20:58:01 ulx-VirtualBox10-10 kernel: [  377.982471] dvb-usb: downloading firmware from file 'dvb-usb-s660.fw'
Mar 23 20:58:01 ulx-VirtualBox10-10 kernel: [  377.982575] dw2102: start downloading DW210X firmware
Mar 23 20:58:02 ulx-VirtualBox10-10 kernel: [  378.880284] dvb-usb: found a 'TeVii S660 USB' in warm state.
Mar 23 20:58:02 ulx-VirtualBox10-10 kernel: [  378.880472] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Mar 23 20:58:02 ulx-VirtualBox10-10 kernel: [  378.884885] DVB: registering new adapter (TeVii S660 USB)
Mar 23 20:58:05 ulx-VirtualBox10-10 kernel: [  382.002671] dvb-usb: MAC address: 01:01:01:01:01:01
Mar 23 20:58:05 ulx-VirtualBox10-10 kernel: [  382.034364] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/input/input5
Mar 23 20:58:05 ulx-VirtualBox10-10 kernel: [  382.034534] dvb-usb: schedule remote query interval to 150 msecs.
Mar 23 20:58:05 ulx-VirtualBox10-10 kernel: [  382.034575] dvb-usb: TeVii S660 USB successfully initialized and connected.
Mar 23 20:58:05 ulx-VirtualBox10-10 kernel: [  382.034741] usb 1-1: USB disconnect, address 3
Mar 23 20:58:05 ulx-VirtualBox10-10 kernel: [  382.035274] dvb-usb: TeVii S660 USB successfully deinitialized and disconnected.

I have all the firmware files in /lib/firmware.

Note that, again, I get the following errors, from the make:

/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/dvb-usb-remote.c: In function 'dvb_usb_remote_init':
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/dvb-usb-remote.c:195: warning: assignment from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/dvb-usb-remote.c:196: warning: assignment from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/va1j5jf8007s.c:596: warning: initialization from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/va1j5jf8007t.c:445: warning: initialization from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/jpeg.h:152: warning: 'jpeg_set_qual' defined but not used
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/ir-keytable.c: In function '__ir_input_register':
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/ir-keytable.c:452: warning: assignment from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/ir-keytable.c:453: warning: assignment from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/cu1216.c:395: warning: 'cu1216_read_quality' defined but not used
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/dst.c:1771: warning: initialization from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/dst.c:1797: warning: initialization from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/dst.c:1831: warning: initialization from incompatible pointer type
/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/dst.c:1854: warning: initialization from incompatible pointer type


The make install looks ok though (I think):

make -C /home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l install
make[1]: Entering directory `/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l'
-e
Removing obsolete files from /lib/modules/2.6.35-27-generic/kernel/drivers/media/video:

-e
Removing obsolete files from /lib/modules/2.6.35-27-generic/kernel/drivers/media/dvb/cinergyT2:

-e
Removing obsolete files from /lib/modules/2.6.35-27-generic/kernel/drivers/media/common:

-e
Removing obsolete files from /lib/modules/2.6.35-27-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.35-27-generic/kernel/drivers/media/:
        video/gspca/m5602/: gspca_m5602.ko
        dvb/dvb-usb/: dvb-usb-opera.ko dvb-usb-vp7045.ko dvb-usb-ttusb2.ko
                dvb-usb-af9015.ko dvb-usb-az6027.ko dvb-usb-gp8psk.ko
                dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko dvb-usb-cinergyT2.ko
                dvb-usb-umt-010.ko dvb-usb-anysee.ko dvb-usb-gl861.ko
                dvb-usb-ec168.ko dvb-usb-dtv5100.ko dvb-usb-cxusb.ko
                dvb-usb-af9005-remote.ko dvb-usb-dib0700.ko dvb-usb-a800.ko
                dvb-usb-dibusb-common.ko dvb-usb-pctv452e.ko dvb-usb-au6610.ko
                dvb-usb-dibusb-mc.ko dvb-usb.ko dvb-usb-digitv.ko
                dvb-usb-ce6230.ko dvb-usb-friio.ko dvb-usb-lme2510.ko
                dvb-usb-dtt200u.ko dvb-usb-vp702x.ko dvb-usb-dibusb-mb.ko
                dvb-usb-dw2102.ko dvb-usb-m920x.ko
        video/saa7164/: saa7164.ko
        video/zoran/: videocodec.ko zr36050.ko zr36016.ko
                zr36060.ko zr36067.ko
        video/cx18/: cx18.ko cx18-alsa.ko
        video/cpia2/: cpia2.ko
        IR/keymaps/: rc-tevii-nec.ko rc-adstech-dvb-t-pci.ko rc-hauppauge-new.ko
                rc-pctv-sedna.ko rc-proteus-2309.ko rc-msi-tvanywhere.ko
                rc-avermedia-dvbt.ko rc-pixelview.ko rc-dm1105-nec.ko
                rc-encore-enltv-fm53.ko rc-imon-mce.ko rc-evga-indtube.ko
                rc-em-terratec.ko rc-gadmei-rm008z.ko rc-avermedia-m733a-rm-k6.ko
                rc-dntv-live-dvb-t.ko rc-kworld-plus-tv-analog.ko rc-behold.ko
                rc-norwood.ko rc-rc5-tv.ko rc-vp1027.ko
                rc-vp1041.ko rc-pinnacle-color.ko rc-cinergy-1400.ko
                rc-avertv-303.ko rc-cinergy.ko rc-manli.ko
                rc-eztv.ko rc-kworld-315u.ko rc-avermedia-a16d.ko
                rc-tt-1500.ko rc-videomate-tv-pvr.ko rc-apac-viewcomp.ko
                rc-tt-3200.ko rc-terratec-cinergy-xs.ko rc-nebula.ko
                rc-msi-tvanywhere-plus.ko rc-npgtech.ko rc-ati-tv-wonder-hd-600.ko
                rc-pinnacle-pctv-hd.ko rc-iodata-bctv7e.ko rc-budget-ci-old.ko
                rc-avermedia.ko rc-imon-pad.ko rc-nec-terratec-cinergy-xs.ko
                rc-winfast-usbii-deluxe.ko rc-flydvb.ko rc-videomate-s350.ko
                rc-pv951.ko rc-vp2040.ko rc-pixelview-mk12.ko
                rc-winfast.ko rc-lirc.ko rc-encore-enltv2.ko
                rc-pixelview-new.ko rc-purpletv.ko rc-vp2033.ko
                rc-fusionhdtv-mce.ko rc-empty.ko rc-gotview7135.ko
                rc-kaiomy.ko rc-pinnacle-grey.ko rc-powercolor-real-angel.ko
                rc-avermedia-m135a.ko rc-rc5-hauppauge-new.ko rc-flyvideo.ko
                rc-encore-enltv.ko rc-behold-columbus.ko rc-tbs-nec.ko
                rc-avermedia-cardbus.ko rc-genius-tvgo-a11mce.ko rc-real-audio-220-32-keys.ko
                rc-rc6-mce.ko rc-dntv-live-dvbt-pro.ko rc-asus-pc39.ko
        dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko
        video/ivtv/: ivtvfb.ko ivtv.ko
        dvb/mantis/: mantis.ko
        video/hdpvr/: hdpvr.ko
        common/tuners/: tuner-xc2028.ko mt2060.ko tda9887.ko
                mt2131.ko mc44s803.ko qt1010.ko
                max2165.ko mt20xx.ko tda827x.ko
                tda18271.ko xc5000.ko mxl5007t.ko
                tea5761.ko tuner-types.ko tda8290.ko
                tuner-simple.ko mt2266.ko tea5767.ko
                mxl5005s.ko
        video/sn9c102/: sn9c102.ko
        dvb/dvb-core/: dvb-core.ko
        video/: videobuf-dma-contig.ko vpx3220.ko videobuf-dma-sg.ko
                pms.ko bt856.ko v4l2-mem2mem.ko
                upd64083.ko stradis.ko videobuf-core.ko
                ths7303.ko tda9840.ko saa7191.ko
                cx2341x.ko wm8775.ko meye.ko
                adv7180.ko rj54n1cb0c.ko saa7185.ko
                tuner.ko mt9t031.ko zr364xx.ko
                ks0127.ko videobuf-dvb.ko tvaudio.ko
                tea6420.ko bt866.ko cafe_ccic.ko
                mt9v011.ko saa5246a.ko msp3400.ko
                tvp514x.ko mem2mem_testdev.ko tcm825x.ko
                soc_camera.ko wm8739.ko stkwebcam.ko
                saa5249.ko cpia_pp.ko soc_mediabus.ko
                tda7432.ko w9966.ko ir-kbd-i2c.ko
                mt9m001.ko upd64031a.ko tea6415c.ko
                dabusb.ko bt819.ko cpia_usb.ko
                videodev.ko mxb.ko tda9875.ko
                adv7175.ko soc_camera_platform.ko adv7343.ko
                cs53l32a.ko s2255drv.ko btcx-risc.ko
                se401.ko saa7110.ko saa7115.ko
                saa6588.ko ak881x.ko tvp7002.ko
                v4l2-common.ko hexium_gemini.ko hexium_orion.ko
                tw9910.ko tvp5150.ko mt9m111.ko
                vp27smpx.ko adv7170.ko ov772x.ko
                ov7670.ko saa7127.ko m52790.ko
                ov9640.ko mt9v022.ko v4l1-compat.ko
                videobuf-vmalloc.ko v4l2-int-device.ko c-qcam.ko
                tveeprom.ko cs5345.ko saa717x.ko
                cpia.ko tlv320aic23b.ko bw-qcam.ko
                mt9t112.ko
        video/cx23885/: cx23885.ko
        dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko
                dst.ko
        dvb/siano/: smssdio.ko smsdvb.ko smsusb.ko
                smsmdtv.ko
        video/cx25840/: cx25840.ko
        dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko
        dvb/ngene/: ngene.ko
        dvb/dm1105/: dm1105.ko
        video/cx231xx/: cx231xx.ko cx231xx-dvb.ko cx231xx-alsa.ko
        video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-alsa.ko
                saa7134-dvb.ko saa7134.ko
        dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko
                budget-av.ko budget.ko budget-core.ko
                budget-ci.ko
        video/et61x251/: et61x251.ko
        video/gspca/gl860/: gspca_gl860.ko
        IR/: ir-rc6-decoder.ko ir-sony-decoder.ko ir-jvc-decoder.ko
                ir-core.ko ir-common.ko ir-nec-decoder.ko
                ir-rc5-decoder.ko
        radio/si470x/: radio-usb-si470x.ko
        dvb/frontends/: nxt6000.ko dib7000m.ko dib0090.ko
                drx397xD.ko s5h1411.ko tda665x.ko
                dib8000.ko nxt200x.ko s921.ko
                lnbp22.ko s5h1409.ko cu1216.ko
                atbm8830.ko dib3000mb.ko ec100.ko
                lgs8gl5.ko dib3000mc.ko stv0900.ko
                sp8870.ko tda8083.ko stv0297.ko
                tda10086.ko zl10353.ko mb86a16.ko
                lgs8gxx.ko stv0299.ko dvb-pll.ko
                cx22702.ko lgdt3304.ko tda8261.ko
                tua6100.ko bcm3510.ko stb0899.ko
                or51211.ko cx24113.ko tda826x.ko
                af9013.ko si21xx.ko au8522.ko
                s5h1420.ko stv090x.ko stv0288.ko
                mt352.ko zl10039.ko isl6405.ko
                sp887x.ko dibx000_common.ko isl6421.ko
                mt312.ko or51132.ko tda1004x.ko
                stv6110.ko itd1000.ko stv6110x.ko
                zl10036.ko lgdt3305.ko dib7000p.ko
                l64781.ko ves1x93.ko stb6100.ko
                ves1820.ko dib0070.ko cx22700.ko
                cx24110.ko dvb_dummy_fe.ko lgdt330x.ko
                cx24123.ko lnbp21.ko stb6000.ko
                isl6423.ko tda10023.ko cx24116.ko
                tda10021.ko tda10048.ko ds3000.ko
        video/bt8xx/: bttv.ko
        video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko
                cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko
                cx88-dvb.ko
        video/gspca/: gspca_stk014.ko gspca_spca501.ko gspca_spca500.ko
                gspca_mars.ko gspca_spca1528.ko gspca_stv0680.ko
                gspca_sunplus.ko gspca_vc032x.ko gspca_benq.ko
                gspca_spca505.ko gspca_sn9c20x.ko gspca_zc3xx.ko
                gspca_sq930x.ko gspca_sq905c.ko gspca_sonixb.ko
                gspca_etoms.ko gspca_pac7302.ko gspca_pac207.ko
                gspca_ov534_9.ko gspca_spca508.ko gspca_sq905.ko
                gspca_sn9c2028.ko gspca_t613.ko gspca_spca561.ko
                gspca_ov534.ko gspca_tv8532.ko gspca_jeilinj.ko
                gspca_spca506.ko gspca_sonixj.ko gspca_main.ko
                gspca_cpia1.ko gspca_conex.ko gspca_mr97310a.ko
                gspca_pac7311.ko gspca_ov519.ko gspca_finepix.ko
        dvb/pluto2/: pluto2.ko
        video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko
                ultracam.ko konicawc.ko
        dvb/smi2032/: smi2032.ko
        video/usbvision/: usbvision.ko
        common/: saa7146_vv.ko saa7146.ko
        video/gspca/stv06xx/: gspca_stv06xx.ko
        video/em28xx/: em28xx-dvb.ko em28xx-alsa.ko em28xx.ko
        radio/: dsbr100.ko radio-maestro.ko si4713-i2c.ko
                radio-zoltrix.ko radio-miropcm20.ko radio-terratec.ko
                tef6862.ko radio-aimslab.ko radio-maxiradio.ko
                radio-gemtek.ko radio-trust.ko radio-sf16fmr2.ko
                saa7706h.ko radio-tea5764.ko radio-si4713.ko
                radio-typhoon.ko radio-cadet.ko radio-aztech.ko
                radio-sf16fmi.ko radio-rtrack2.ko radio-gemtek-pci.ko
                radio-timb.ko radio-mr800.ko
        video/pvrusb2/: pvrusb2.ko
        dvb/pt1/: earth-pt1.ko
        video/tlg2300/: poseidon.ko
        video/uvc/: uvcvideo.ko
        dvb/ttusb-budget/: dvb-ttusb-budget.ko
        video/pwc/: pwc.ko
        video/zc0301/: zc0301.ko
        video/au0828/: au0828.ko
/sbin/depmod -a 2.6.35-27-generic
make -C firmware install
make[2]: Entering directory `/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin
make[2]: Leaving directory `/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l/firmware'
make[1]: Leaving directory `/home/matt/tevii/s2-liplianin-7e47ba1d4ae8/v4l'


Any ideas?

Cheers,

Matt.

---

### Post by SOME1 on 2011-03-23
> found a 'TeVii S660 USB' in cold state
that's exactly what I thought you have. 

Are you using a USB Hub or an Usb extension cable? 
if yes, please connect the s660 to your usb in your computer directly. 
if not, please try a diffrent USB port. 

I prefer you write here the output from the 10.04 (without a VM becouse some of the problems is becouse of the VM).

Matt, if it's not working yet, I'll continuing investigate your case. Just write here again you still have a problem. We will fix it eventually.

---

### Post by mutant_matt on 2011-03-23
You are a superstar! ;)

You know what, even though it's going through a hub, and into a VM, you made me double check everything, and, even though it was seeing it in the VM, the VM wasn't set to "have" the USB device exclusively.  Now that I've set it that way, it's seeing it, it's loading the drivers and /dev/dvb/adaptor0 now exists.

So, now, I need to make an f-connector sat extension cable up, to connect it to the dish/lnb, so I can test the channel scan and watch some test streams.  Many thanks again!

The next step, if you're still feeling helpful, ;) :

1. Do you know how to get my 10.04 install back to original state, without the errors I previously mentioned? (I obviously broke something along the way).  I did a make rminstall in root directory of all the various different versions of the sources I've tried, but dvb is still broken :(

2. What did you change on the latest version of the source, to get it working in the latest 10.04 and 10.10 builds?  Is there a danger that newer kernels, will break something again? (I think I plan, once I've built my myth box, to a state working how I want it, is to do zero updates from there on in!)

3. Is it possible, and would it be worth, only building the parts needed for the 660, and leaving the rest of the drivers as they come "out of the box", from Ubuntu, or doesn't it work like that?

Once I've proved this a bit more, I plan to buy a twin S2 Tevii PCI card, and an ASRock ION 330 board, and add this 660 USB and a Hauppauge NOTA-T USB stick, and hopefully have more tuners than I'll ever need! :)

Many Thanks for your help once again, hopefully, someone else will at some point find these ramblings useful (as this seems to be one of the only threads on the web that help get the 660 working on Linux!).

Cheers,

Matt :)

---

### Post by SOME1 on 2011-03-23
Hi Matt, 

I'm glad I could help. 
From my experience, This card does not work well with some of (usually cheap) usb hub so that's why I asked you to try to remove it (usually the cold status is a hint). 

the errors you mentioned was in my install too (if I remember correctly) but it's not causing usually problems. if you find problem with your card, please write it here and we try to find out what cause it. 

about the last version I posted here, before I started to change the files, I checked on the [Tevii driver developer site]("http://mercurial.intuxication.org/hg/s2-liplianin/") and he already fix the problems I found so I didn't need to do anything, just upload the last driver from his site to here. this driver should work on both 10.04 & 10.10 (I checked it on both machines).

I talked to Sales Director of TeVii Technology before (I helped them with their driver support for 10.10) and I recommended them to insert their driver to the kernel. They promise to work on it and if they do, we won't need to install drivers anymore for this to work - it will work out of the box with any new linux version. 

I hope I answered to all your questions. :)

---

### Post by henz103 on 2011-03-29
I'm having problem installing the driver, getting error in "sudo make" step

Tevii S464 DVB-S2 PCI
Driver: [http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar](http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar)
OS: Ubuntu 10.10

Terminal log:

```
hany@hany-desktop:~/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000$ sudo make
make -C /home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l 
make[1]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
No version yet, using 2.6.35-28-generic
make[1]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
make[1]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.35

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
make[1]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.35-28-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
make[2]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-28-generic/build
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.o
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:252: error: implicit declaration of function 'kfree'
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:314: error: implicit declaration of function 'kzalloc'
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:314: warning: assignment makes pointer from integer without a cast
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:365: warning: assignment makes pointer from integer without a cast
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.c:1269: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/hany/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000/v4l'
make: *** [all] Error 2
hany@hany-desktop:~/Downloads/Chrome/100315_Beta_linux_tevii_ds3000/linux-tevii-ds3000$
```


Any ideas?

Thanks

---

### Post by SOME1 on 2011-04-01
sorry for the late reply. 
please try the following: 

open your terminal and type
sudo apt-get install build-essential linux-headers-$(uname -r)

then download the driver again, extract to a new folder and run in your terminal

sudo make CONFIG_DVB_FIREDTV:=n 
sudo make install

if it finished ok, and it's not working, try to plug the s660 from it's power source and plug it in again and reboot your computer. 

please write here if you have problems.

---

### Post by henz103 on 2011-04-02
> **SOME1 said:**
> sorry for the late reply. 
please try the following: 

open your terminal and type
sudo apt-get install build-essential linux-headers-$(uname -r)

then download the driver again, extract to a new folder and run in your terminal

sudo make CONFIG_DVB_FIREDTV:=n 
sudo make install

if it finished ok, and it's not working, try to plug the s660 from it's power source and plug it in again and reboot your computer. 

please write here if you have problems.


Thanks SOME1 for replying, I followed your steps and it failed with the same error i posted above.


STEP1: sudo apt-get install build-essential linux-headers-$(uname -r)

```
hany@hany-desktop:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.35-28-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

STEP2: then download the driver again, extract to a new folder and run in your terminal

[IMG]http://img25.imageshack.us/img25/7040/tevii.jpg[/IMG]

STEP3: sudo cp *.fw /lib/firmware/

STEP4: tar xjvf linux-tevii-ds3000.tar.bz2

STEP5: cd linux-tevii-ds3000

STEP6: sudo make CONFIG_DVB_FIREDTV:=n

```
hany@hany-desktop:~/Downloads/teviidriver/linux-tevii-ds3000$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l 
make[1]: Entering directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l'
No version yet, using 2.6.35-28-generic
make[1]: Leaving directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l'
make[1]: Entering directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.35

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l'
make[1]: Entering directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.35-28-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/firmware'
make[2]: Leaving directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-28-generic/build
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.o
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c:252: error: implicit declaration of function 'kfree'
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c:314: error: implicit declaration of function 'kzalloc'
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c:314: warning: assignment makes pointer from integer without a cast
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c:365: warning: assignment makes pointer from integer without a cast
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.c:1269: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/hany/Downloads/teviidriver/linux-tevii-ds3000/v4l'
make: *** [all] Error 2
hany@hany-desktop:~/Downloads/teviidriver/linux-tevii-ds3000$ 
```

---

### Post by SOME1 on 2011-04-02
please try [this driver]("http://rapidshare.com/files/453360132/s2-liplianin-7e47ba1d4ae8.zip") and write here the results.
thanks.

---

### Post by henz103 on 2011-04-02
> **SOME1 said:**
> please try [this driver]("http://rapidshare.com/files/453360132/s2-liplianin-7e47ba1d4ae8.zip") and write here the results.
thanks.

Before I try it, Are you aware that I have Tevii S464 not S660, its internal PCI card not external USB device, they use the same driver tho

Thanks


EDIT: Wohoooooooo It worked. I tested it with ME TV and finally I can watch DVB-S channels on Ubuntu, I can't switch channels tho (maybe a bug in ME TV)

Thank you so much SOME1, I appreciate your help.


[IMG]http://img848.imageshack.us/img848/6897/metv.jpg[/IMG]

---

### Post by SOME1 on 2011-04-03
I am glad I could help. I thought is was the driver because I saw some code changing about your card. have fun. :D

---

### Post by SOME1 on 2011-05-13
I have got a messege from a linux mint 11 user (based on UBUNTU 11.04) that pointed out 2 problems while compiling the driver. 

if you have problems when compiling, please try to use [this driver]("https://rapidshare.com/files/3433601396/tevii-140511.tar.gz"). 

thanks.

---

### Post by SOME1 on 2011-05-20
> **SOME1 said:**
> I have got a messege from a linux mint 11 user (based on UBUNTU 11.04) that pointed out 2 problems while compiling the driver. 

if you have problems when compiling, please try to use [this driver]("https://rapidshare.com/files/3433601396/tevii-140511.tar.gz"). 

thanks.

if you get in syslog error about dvb-fe-ds3000.fw file please extract the attachment in this post and put the file dvb-fe-ds3000.fw in your /lib/firmware directory.

---

### Post by dilbert2k on 2011-05-21
Hello,
 
I am also having problems with the Tevii S660. I am a relatively new user of ubuntu (any form of linux!) but have managed to get Myth running on Ubuntu 10.10 on a Revo 3610 using a Kworld 399U dual dvb-t tuner. I am now looking to add the S660 tuner.
 
I followed the instructions here.....
[http://ubuntuforums.org/showpost.php?p=9927773&postcount=32](http://ubuntuforums.org/showpost.php?p=9927773&postcount=32)
 
I've found some of the posts in this thread difficult to follow due to my lack of linux experience, but I have checked a number of the things suggested.
 
I have a dev/dvb folder. It contains adapter0 and adapter1. Although I am not sure if these both relate to my dual dvb-t tuner.....?
 
dmesg shows the following:
```
[   18.762461] dvb-usb: found a 'KWorld PlusTV Dual DVB-T Stick (DVB-T 399U)' in cold state, will try to load a firmware
[   20.351282] hda_codec: ALC662 rev1: BIOS auto-probing.
[   20.536212] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
[   20.582315] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.606654] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   20.618365] dvb-usb: downloading firmware from file 'dvb-usb-s630.fw'
[   20.618376] dw2102: start downloading DW210X firmware
[   20.636699] usb 1-2: USB disconnect, address 2
[   20.678156] dvb-usb: found a 'KWorld PlusTV Dual DVB-T Stick (DVB-T 399U)' in warm state.
[   20.678690] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.679508] DVB: registering new adapter (KWorld PlusTV Dual DVB-T Stick (DVB-T 399U))
[   20.693514] af9013: firmware version:4.95.0
[   20.698282] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   20.705235] MXL5005S: Attached at address 0xc6
[   20.705246] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.706373] DVB: registering new adapter (KWorld PlusTV Dual DVB-T Stick (DVB-T 399U))
[   20.750095] dvb-usb: found a 'TeVii S660 USB' in warm state.
[   20.750258] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.750317] DVB: registering new adapter (TeVii S660 USB)
[   21.123345] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 21
[   21.123366] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 21 (level, low) -> IRQ 21
[   21.125031] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   21.125052] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   21.125080] nvidia 0000:03:00.0: setting latency timer to 64
[   21.125095] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.125722] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   21.451059] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   21.453682] af9013: firmware version:4.95.0
[   21.464687] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   21.465287] MXL5005S: Attached at address 0xc6
[   21.465523] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/input/input5
[   21.465771] dvb-usb: schedule remote query interval to 150 msecs.
[   21.465789] dvb-usb: KWorld PlusTV Dual DVB-T Stick (DVB-T 399U) successfully initialized and connected.
[   21.592418] usbcore: registered new interface driver dvb_usb_af9015
[   22.207631] type=1400 audit(1305886575.326:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=917 comm="apparmor_parser"
[   22.213294] type=1400 audit(1305886575.336:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=918 comm="apparmor_parser"
[   22.214856] type=1400 audit(1305886575.336:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=918 comm="apparmor_parser"
[   22.215347] type=1400 audit(1305886575.336:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=918 comm="apparmor_parser"
[   22.236655] type=1400 audit(1305886575.356:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=922 comm="apparmor_parser"
[   22.237752] type=1400 audit(1305886575.356:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=922 comm="apparmor_parser"
[   22.316160] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.695271] audit_printk_skb: 18 callbacks suppressed
[   22.695281] type=1400 audit(1305886575.816:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1074 comm="apparmor_parser"
[   25.016444] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.011329] dvb-usb: MAC address: 00:00:00:00:00:00
[   31.070046] Only Zarlink VP310/MT312/ZL10313 are supported chips.
[   31.470037] Invalid probe, probably not a DS3000
[   31.470354] dvb-usb: no frontend was attached by 'TeVii S660 USB'
[   31.470623] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-2/input/input6
[   31.470854] dvb-usb: schedule remote query interval to 150 msecs.
[   31.470869] dvb-usb: TeVii S660 USB successfully initialized and connected.
[   31.470964] usbcore: registered new interface driver dw2102
[   31.531172] dvb-usb: TeVii S660 USB successfully deinitialized and disconnected.
[   31.536934] type=1400 audit(1305886584.656:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1503 comm="apparmor_parser"
[   31.538091] type=1400 audit(1305886584.656:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1503 comm="apparmor_parser"
[   31.591415] ppdev: user-space parallel port driver
[   31.812627] usb 1-2: new high speed USB device using ehci_hcd and address 6
[   32.840024] eth0: no IPv6 routers present
[   37.304505] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   46.930038] usb 1-2: device descriptor read/64, error -110
[   62.160063] usb 1-2: device descriptor read/64, error -110
[   62.390042] usb 1-2: new high speed USB device using ehci_hcd and address 7
[   77.510047] usb 1-2: device descriptor read/64, error -110
[   92.740037] usb 1-2: device descriptor read/64, error -110
[   92.970045] usb 1-2: new high speed USB device using ehci_hcd and address 8
[   98.000152] usb 1-2: device descriptor read/8, error -110
[  103.130089] usb 1-2: device descriptor read/8, error -110
[  103.360061] usb 1-2: new high speed USB device using ehci_hcd and address 9
[  108.390134] usb 1-2: device descriptor read/8, error -110
[  113.520186] usb 1-2: device descriptor read/8, error -110
[  113.630076] hub 1-0:1.0: unable to enumerate USB device on port 2
[  114.170059] usb 2-2: new full speed USB device using ohci_hcd and address 4
[  129.350043] usb 2-2: device descriptor read/64, error -110
[  144.640037] usb 2-2: device descriptor read/64, error -110
[  144.930038] usb 2-2: new full speed USB device using ohci_hcd and address 5
[  160.141287] usb 2-2: device descriptor read/64, error -110
[  175.420038] usb 2-2: device descriptor read/64, error -110
[  175.710035] usb 2-2: new full speed USB device using ohci_hcd and address 6
[  180.740174] usb 2-2: device descriptor read/8, error -110
[  185.870504] usb 2-2: device descriptor read/8, error -110
[  186.160035] usb 2-2: new full speed USB device using ohci_hcd and address 7
[  191.194744] usb 2-2: device descriptor read/8, error -110
[  196.321076] usb 2-2: device descriptor read/8, error -110
[  196.430066] hub 2-0:1.0: unable to enumerate USB device on port 2
[68914.046803] type=1400 audit(1305955467.168:21): apparmor="DENIED" operation="open" parent=19058 profile="/usr/sbin/cupsd" name="/dev/ttyUSB0" pid=19072 comm="serial" requested_mask="w" denied_mask="w" fsuid=0 ouid=0

```
 
The S660 does not show up in lsusb:
```
Bus 002 Device 003: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1b80:e399 Afatech 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
 
Can anyone (SOME1?) help me here please? Is there any other info I need to provide?
 
Thanks in advance!
D2K

---

### Post by SOME1 on 2011-05-21
Hi, 

Welcome to linux. :) 
it will be easier if you can disconnect the dvb that already work so we can understand that the output you are getting is only about the s660. 

you tried to install an old driver and it's look like that's the source for your problem. 

this is what I suggest you try: 

1. download the file I attached in the end of this post. 
2. open your terminal (applications -> accessories -> terminal) and cd to the directory you downloaded the file (for example, if you downloaded the to the downloads directory, type in the terminal 
```
cd ~/Downloads/
``` and press Enter. 
3. extract the file content to the /lib/firmware direcory by typing 
```
sudo unzip -o ./660.zip -d /lib/firmware/
```
(note: if you have message that unzip in not install you need to install it with the command 
```
sudo apt-get install unzip
``` and then use the unzip command above. )
4. download [this driver]("https://rapidshare.com/files/3433601396/tevii-140511.tar.gz"). this is the last driver with all the bug fixes. I haven't test it in 10.10, only in 11.04. if you want something that tested ok in 10.10 you can use [this driver]("http://rapidshare.com/files/453360132/s2-liplianin-7e47ba1d4ae8.zip"). 
5. extract the file you have download and cd to it. (in the graphic system, double click the file, and drag the content to some place, like your desktop or anywhere  else. )
6. cd to the directory you extracted (if its the first file its TEVII directory, if it's the second it's s2-liplianin-7e47ba1d4ae8 directory). 
7. before you can install the driver you need to make sure you have everything you need install. so type in the terminal
```
sudo apt-get install linux-headers-`uname -r` build-essential
```
8. now let's install :) - type this
```
sudo make CONFIG_DVB_FIREDTV:=n 
```
this step take some time. 
9. if it's look like the previous step finished ok(the last lines should be something like 438 (or something like that) modules build) then type 
```
sudo make install 
```
10. after it's done, plug your tevii s660 out from it's power source and plug it in again and restart your computer. it's should work now. 

If there problems write them here and I will try to help. 

Good luck!

---

### Post by dilbert2k on 2011-05-21
Hi 
 
Many thanks for your speedy reply!
 
Using the first driver (11.04) I got as far as step 8, but this failed:
```
mark@mgt01p-myth:~/Downloads/TEVII$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/mark/Downloads/TEVII/v4l 
make[1]: Entering directory `/home/mark/Downloads/TEVII/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.38
File not found: /lib/modules/2.6.38-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/home/mark/Downloads/TEVII/v4l'
make[1]: Entering directory `/home/mark/Downloads/TEVII/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.38
File not found: /lib/modules/2.6.38-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'. Stop.
make[1]: Leaving directory `/home/mark/Downloads/TEVII/v4l'
make: *** [all] Error 2

```
 
I repeated Step 7 just in case:
 
```
mark@mgt01p-myth:~/Downloads/TEVII$ sudo apt-get install linux-headers-`uname -r` build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.35-28-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
 
 
The missing file is **2.6.38-8**-generic, whereas step 7 reports "linux-headers-**2.6.35-28**-generic is already the newest version". Is this because I used the 11.04 driver?
 
I then tried the second diver and I got much further :-)
 
lsusb shows:
```
Bus 002 Device 003: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 9022:d660  
Bus 001 Device 004: ID 1b80:e399 Afatech 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
 
The S660 is appearing as d660 but with no name. Does that inidcate a problem?
 
/dev/dvb now contains adapter0, 1 and 2.
 
I am now trying to add the tuner to MythTV :-)
 
Many Thanks
D2K

---

### Post by SOME1 on 2011-05-21
the first driver is for 11.04... the changes in the kernel version that comes with ubuntu 11.04 seems to be essential for this driver to work. 
so you need to use the driver for 10.10 (it's a good driver, you probably won't notice changes). 

if you have now in the dvb folder a new adapter folder it's a good sign. 
I'll be happy if you write here the results after you'll done configuration for mythtv. 

another way to check if the dvb is working ok is to install kaffeine (in terminal run 
```
sudo apt-get install kaffeine
```
- very friendly software for watching tv and configure it -  but that will install all the kde stuff and if you want to keep your linux clean from things you don't need in the future, try to avoid it. 

good luck.

---

### Post by dilbert2k on 2011-05-23
I am still struggling with the S660, but this time with Myth....
 
So far I am resisting installing kaffeine as I am keen to keep the install as clean as possible.
 
I managed to get the S660 to scan channels in Myth and it found a load, but so far I've been unable to get any EPG data for them (using EIT) and I can't 'Watch TV'. My existing DVB-T tuners continue to work fine.
 
So, I have now disabled the DVB-T tuners to concentrate on getting the S660 working in Myth.
 
But now, I am unable to get Scan Channels to find any at all!
 
Any further pointers would be most welcome.
 
Cheers
D2K

---

### Post by dilbert2k on 2011-05-23
OK - I found out why I could not scan channels. For some reason the Capture Card config had lost the 'LNB' config.
 
Now that I have restored that, and connected it to a EIT video source, I have scanned and found dozens of channels.
 
Unfortunately "Watch TV" displays "Please wait...." and then drops back to the main menu. And I have no EPG data.
 
Any ideas folks?
 
Cheers
D2K

---

### Post by dilbert2k on 2011-05-23
MythTV configuration resolved now - final problem turned out to be a dodgy cable!
 
Thanks for help SOME1!
 
Cheers
D2K

---

### Post by _whitehawk_ on 2011-06-08
Hi,

This may or may not be of any help... but I'm running an up-to-date 11.04 it actually just works out of the box!

I downloaded the [Linux driver]("http://www.tevii.com/s2_liplianin_1.tar") from [TeVii's support page]("http://www.tevii.com/Support.asp"), un-tar'd it, copied the *.fw from ./tevii_s2_liplianin-eb8a914cd499/linux/firmware/ to /lib/firmware, renamed dvb-usb-s660.fw to dvb-usb-s630.fw after I saw in /var/log/kern.log that was the file it was looking for.

I then followed [this guide]("http://parker1.co.uk/mythtv_freesat.php") (although setting FEC to 5/6 as suggested did nothing apart from say no channels found, so I just left it on auto).

I now have satellite on my [MythTV server]("http://www.gavsworld.net/?page=The%20Server") :-)

---

### Post by SOME1 on 2011-06-08
Tevii is updating their driver every now and then but sometimes it's takes time until they post new driver for new linux version so I post here a working driver sometimes before Tevii post it's official in their website. 
anyway, if the driver in Tevii website working for you as expected, you should use their driver. 

thanks.

---

### Post by _whitehawk_ on 2011-06-09
I didn't actually use their driver... only the firmware within their driver package.

I did start playing with compiling drivers, but the DKMS one referenced on the [LinuxTV]("http://www.linuxtv.org/wiki/index.php/S2-liplianin") website didn't compile (can't recall what it failed on). The one from TeVii's website also failed (again, can't recall on what), but the one that you posted ran through fine, however I didn't install it as when I changed FEC to auto (as your driver was compiling), MythTV suddenly started to find channels.

So, bottom line is that I'm using the driver bundled with Ubuntu.

My initial play around last night was streaming the satellite channels to the front ends which was literally when I posted.

I don't appear to see BBC HD, BBC1 HD or Channel 4 HD yet, but I'm sure that's just a case of mucking around with MythTV... at 23:30 I thought is was time for bed since my alarm goes of at 05:30 :-(

Briefly, what is the difference between what's bundled with Ubuntu 11.04 and the driver that you posted?

---

### Post by SOME1 on 2011-06-11
The firmware is the same firware. 
I modified the driver so it should compile without problems. my driver is a cvs based so it should be better since it include bug fixes and sometimes it support new cards.

---

### Post by jlazkano on 2011-06-14
Hello, thanks for this interesting post. I am look info about the Tevvi for my Debian based MythTV. Here is lot of information.

It would be great to collect all driver and firmware version and put it on the linuxtv wiki: [http://linuxtv.org/wiki/index.php/TeVii_S660](http://linuxtv.org/wiki/index.php/TeVii_S660)

Thanks and best regards.

---

### Post by SOME1 on 2011-06-17
> **jlazkano said:**
> Hello, thanks for this interesting post. I am look info about the Tevvi for my Debian based MythTV. Here is lot of information.

It would be great to collect all driver and firmware version and put it on the linuxtv wiki: [http://linuxtv.org/wiki/index.php/TeVii_S660](http://linuxtv.org/wiki/index.php/TeVii_S660)

Thanks and best regards.
I give link to this thread in the page you mention. to collect all drivers and put them there and update every time there is a new driver will be a waste of time. this tread has all the information most users needs and they can post here any errors they have and get help. 

thanks :)

---

### Post by cedo_n on 2011-07-02
> **SOME1 said:**
> I have got a messege from a linux mint 11 user (based on UBUNTU 11.04) that pointed out 2 problems while compiling the driver. 

if you have problems when compiling, please try to use [this driver]("https://rapidshare.com/files/3433601396/tevii-140511.tar.gz"). 

thanks.

This driver is obvious from s2liplianin tree, but this tree has a bug with transponders that have symbol-rate of 30.000 and fec 3/4 . Driver from tevii webpage [http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar](http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar) works with all transponders, but is not compiling on newer kernels. I've tried to patch the tevii driver for 2.6.38 kernels without success, maybe because I'm not a programmer :)
So if anyone have a suggestion would be nice.

and here are discussions on other forum
[http://www.vdr-portal.de/board16-video-disk-recorder/board5-vdr-konfiguration/p737007-probleme-mit-breitbandigen-dvb-s2-muxen/?highlight=30000#post737007](http://www.vdr-portal.de/board16-video-disk-recorder/board5-vdr-konfiguration/p737007-probleme-mit-breitbandigen-dvb-s2-muxen/?highlight=30000#post737007)
[http://linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_S2-3650_CI](http://linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_S2-3650_CI)

thanx,
cedo

PS: here are channels on thor in VDR format that are constantly loosing lock (the bug that I've talked about)
HBO HD;UPC Direct:11843:VC34M5O35S1:S1.0W:30000:301=27:0;310=hun@106,312=eng@106:0:1815,D02,D97:31005:1536:710:0
BBC HD;Telenor:12015:HC34M5O25S1:S1.0W:30000:516=27:0;656=eng@106,657=pol@106:0:B00:4104:70:41:0
Discovery HD;Telenor:12015:HC34M5O25S1:S1.0W:30000:513+8189=27:0;644=eng@106:0:B00,1815,D02,D97:4102:70:41:0
History Chnl HD;Telenor:12015:HC34M5O25S1:S1.0W:30000:514+8187=27:648=eng@3,649=pol@4,650=hun@4,651=cze@4:0:B00,1815,D02,D97:4202:70:41:0
Nat Geo HD;Telenor:11785:HC34M5O25S1:S1.0W:30000:512=27:640=eng@4;641=eng@106:0:B00,1815,D02,D97:3806:70:38:0
Nat Geo Wild HD;Telenor:11785:HC34M5O25S1:S1.0W:30000:513=27:644=eng@4:0:B00,1815,D02,D97:4805:70:38:0
Animal Planet HD;Telenor:12015:HC34M5O25S1:S1.0W:30000:512+8188=27:0;640=eng@106:0:B00:4203:70:41:0
MTVN HD;Telenor:11785:HC34M5O25S1:S1.0W:30000:514=27:0;648=eng@106:0:B00:4606:70:38:0
ESPN America HD;Telenor:11785:HC34M5O25S1:S1.0W:30000:515=27:652=eng@4:0:B00,1815,D02,D97:2935:70:38:0
Eurosport HD;Telenor:12015:HC34M5O25S1:S1.0W:30000:512=27:0;641=sve@106,640=nor@106,642=dan@106,643=fin@106:0:B00:4105:70:41:0
NOVA Sport HD;UPC Direct:11842:VC34M5O35S1:S1.0W:30000:251=27:261=cze@4,262=eng@4:0:1815,D02,D97:31004:1536:710:0
Also there are a lot of channels with SR 30000 on 16E

---

### Post by SOME1 on 2011-07-02
Hi, 

This is a known bug. 
please try to use [this driver]("http://d01.megashares.com/dl/2df7a5e/S660_10.10.zip") and see if it helps you. this is a tevii driver that I modified to work with 10.10 and report the results. 

thanks.

---

### Post by cedo_n on 2011-07-02
> **SOME1 said:**
> Hi, 

This is a known bug. 
please try to use [this driver]("http://d01.megashares.com/dl/2df7a5e/S660_10.10.zip") and see if it helps you. this is a tevii driver that I modified to work with 10.10 and report the results. 

thanks.

I've tried and did not compile on 2.6.38.... :(
I'll install 2.6.35 later and post results

thanks,
cedo

---

### Post by SOME1 on 2011-07-02
please don't install 2.6.35. I want to find a solution for you. 
can you give me link to the driver that worked ok but didn't compile on 2.6.38?

thanks.

---

### Post by cedo_n on 2011-07-03
> **SOME1 said:**
> please don't install 2.6.35. I want to find a solution for you. 
can you give me link to the driver that worked ok but didn't compile on 2.6.38?

thanks.

Here it is, directly from tevii web... [http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar](http://www.tevii.com/100315_Beta_linux_tevii_ds3000.rar)
Not compiling on anything above 2.6.34 due to needed changes in kernel, like #include <linux/slab.h> and lot of others.

thanks again,
cedo

---

### Post by SOME1 on 2011-07-03
yes, I found it. thanks.
I will try to make it work on 10.10 and I will report here. it might take a few days. 

I have 2 questions for you: 
1. Did you try the driver I asked you to? is it have problems? 
2. you are using S660? if not, you need to understand that I can't test it for other cards, but it should work on any card it worked before. 

thanks.

---

### Post by cedo_n on 2011-07-03
Hi again...

The driver, [http://d01.megashares.com/dl/2df7a5e/S660_10.10.zip](http://d01.megashares.com/dl/2df7a5e/S660_10.10.zip) that you send me wich didn't compile on 2.6.38, compile perfectly on 2.6.35, and 30.000 channels works also PERFECTLY.

My card is S464, but this is not important, because in my opinion, the bug is not card specific, it is present in "all" cards from liplianin HG tree. (my friend have 3200 from tehnotrend, wich is also affected) 

If you can find the difference between tevii and liplianin driver, would be wonderful patch for all users of liplianin tree, but it is also a very nice if you can patch S660_10.10.zip to compile on 2.6.38 and of course future 3.0 kernels.

thanks...

---

### Post by cedo_n on 2011-07-03
Coincidence or not, i've found post from today on other forum [http://linuxdvb.org.ru/wbb/index.php?page=Thread&postID=21630#post21630](http://linuxdvb.org.ru/wbb/index.php?page=Thread&postID=21630#post21630)

So I've only use this patch, and 30000 channels are working with all drivers, including latest from liplianin:
```

diff -Naur orig/linux/drivers/media/dvb/frontends/ds3000.c mod/linux/drivers/media/dvb/frontends/ds3000.c  --- orig/linux/drivers/media/dvb/frontends/ds3000.c 2011-03-03 05:45:11.000000000 +0100  +++ mod/linux/drivers/media/dvb/frontends/ds3000.c 2011-05-25 07:26:56.647120018 +0200  @@ -1129,7 +1129,7 @@  ds3000_writereg(state,  ds3000_dvbs2_init_tab[i],  ds3000_dvbs2_init_tab[i + 1]);  - ds3000_writereg(state, 0xfe, 0x98);  + ds3000_writereg(state, 0xfe, 0x54);  break;  default:  return 1;

```But I dont think that this will help friends that have S3200 from tehnotrend thou :(

Regards and thanks to all here,
cedo

PS: patch for NICE signal meter on tevii cards (S464....) would be my last wish for this card now ;) everything else works perfect now.

PPS: whats wrong with wrap [CODE] tags?

---

### Post by SOME1 on 2011-07-04
I am glad you found a solution. I guess you don't need me to change the driver. 

if you have other problems please report here and we will try to help you. 

thanks.

---

### Post by be18 on 2011-07-09
if anyone have the driver for 11.04 would be nice :)

tks

---

### Post by SOME1 on 2011-07-09
you can try the last liplianin driver. 
download it from [here]("http://mercurial.intuxication.org/hg/s2-liplianin/archive/tip.zip"). 
use [this instructions]("http://ubuntuforums.org/showpost.php?p=10844374&postcount=70") to install it and report here for problems.

thanks.

---

### Post by scox_nz on 2011-07-18
I have created a set of files for the Liplianin driver to support kernel version 2.6.39.

It is not a patch sorry, but just copy across the included files over a 2.6.39 kernel tree and make/install.

---

### Post by claytonie on 2011-08-01
> **SOME1 said:**
> you can try the last liplianin driver. 
download it from [here]("http://mercurial.intuxication.org/hg/s2-liplianin/archive/tip.zip"). 
use [this instructions]("http://ubuntuforums.org/showpost.php?p=10844374&postcount=70") to install it and report here for problems.

thanks.

After months of not getting my Tevii S660 working in Ubuntu this did the job perfectly. Thanks for your efforts SOME1!! :)

---

### Post by jlazkano on 2011-08-12
Hello, I have a problem with the Tevii S660. I have on a Debian Squeeze machine with 2.6.32-5-686 kernel. I use Ubuntu on my laptop, but for my HTPC a prefer Debian.

I read the post and it looks very interesting. I know that this is not a Debian forum, but maybe you can help me.

I have a Tevii S470 PCIe working perfect with this method:

```

mkdir /usr/local/src/dvb
cd /usr/local/src/dvb
wget http://tevii.com/100315_Beta_linux_tevii_ds3000.rar
unrar x 100315_Beta_linux_tevii_ds3000.rar
cp *.fw /lib/firmware/
tar xjvf linux-tevii-ds3000.tar.bz2
cd linux-tevii-ds3000
make && make install

```

I just take the wire from the S470 and connect to the S660, I have good kernel message and device initialized on boot: [http://dl.dropbox.com/u/1541853/dmesg](http://dl.dropbox.com/u/1541853/dmesg)

I can not scan any channel:

```

w_scan -fs -s S19E2 -o 7 -t 3 -X -a 6 > astra19.2_s660.conf

```

If I try with MythTV I get this on mythbackend start:

```

2011-08-12 21:43:20.810 DVBChan(56:/dev/dvb/adapter6/frontend0) Warning: Unsupported modulation parameter.

```

And this when go to a sat channel:

```

2011-08-12 21:45:00.081 TVRec(50): Changing from WatchingLiveTV to None
2011-08-12 21:45:00.236 MainServer::ANN Playback
2011-08-12 21:45:00.237 adding: htpc as a client (events: 0)
2011-08-12 21:45:00.241 TVRec(56): Changing from None to WatchingLiveTV
2011-08-12 21:45:00.259 TVRec(56): HW Tuner: 56->56
2011-08-12 21:45:01.656 LoadFromScheduler(): Error, called from backend.
2011-08-12 21:45:01.663 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-08-12 21:45:01.774 DVBChan(56:/dev/dvb/adapter6/frontend0) Warning: Unsupported modulation parameter.
2011-08-12 21:45:02.031 DVBSM(/dev/dvb/adapter6/frontend0), Warning: Cannot count Uncorrected Blocks
			eno: Success (0)

```

I just configured the LNB same as S470 (Universal).

How can I debug the device? Can you help with this?

Thanks and best regards.

---

### Post by jlazkano on 2011-08-13
I got it!!!

The solutions is on the las SOME1 post, thanks!!! I try other firmware and drivers version, this procedure works for me on a Debian Squeeze:

```

apt-get install linux-headers-`uname -r` build-essential
mkdir /usr/local/src/dvb
cd /usr/local/src/dvb
wget http://mercurial.intuxication.org/hg/s2-liplianin/archive/tip.zip
unzip s2-liplianin-0b7d3cc65161.zip 
cd s2-liplianin-0b7d3cc65161
make CONFIG_DVB_FIREDTV:=n
make install

```

The drivers are from here: [http://ubuntuforums.org/showpost.php?p=10844374](http://ubuntuforums.org/showpost.php?p=10844374)

It works perfect, I didn't try HD channels yet.

Can I post the procedure on the linuxtv wiki? Are this firmware Tevii official ones? [http://ubuntuforums.org/attachment.php?attachmentid=192768&d=1305964408](http://ubuntuforums.org/attachment.php?attachmentid=192768&d=1305964408)

Thanks and best regards.

---

### Post by SOME1 on 2011-08-13
Hi, 

I am glad it helped you. 
You can post it everywhere you want. I suggest you linked to this thread in case someone have questions. we usually help here. 

this is NOT official Tevii drivers. there are many drivers in this thread, some of them was modified by me to make it work with kernel changes and some of them are liplianin drivers. anyway, if you found one that works for you - that's the most important thing :)

thanks.

---

### Post by jlazkano on 2011-08-13
> **SOME1 said:**
> Hi, 

I am glad it helped you. 
You can post it everywhere you want. I suggest you linked to this thread in case someone have questions. we usually help here. 

this is NOT official Tevii drivers. there are many drivers in this thread, some of them was modified by me to make it work with kernel changes and some of them are liplianin drivers. anyway, if you found one that works for you - that's the most important thing :)

thanks.

I add it on the wiki: [http://linuxtv.org/wiki/index.php/TeVii_S660#Linux_support](http://linuxtv.org/wiki/index.php/TeVii_S660#Linux_support)

Feel free to modify/add comments, I am not any expert on Linux DVB and my english is not good enough.

Best regards.

---

### Post by AndrewGee on 2011-08-20
Hi,

I'm having problems with the s2-liplianin driver. I just installed the latest tip.zip version of the driver in ubuntu natty.

The s660 is recognised and initialised, as seen from dmesg.

But the problem comes from my additional two DVB-T hauppauge tuners that seem to conflict with this new s2-liplianin driver. I get a stacktrace on dmesg, and then none of the dvb devices operate.

Is there any way I could fix this?

Thanks

(Attached is the relevant dmesg output)

---

### Post by scpetand on 2011-08-21
Hi I followed the #98 instructions and it works.

However using sasc-ng ([http://dolot.kipdola.com/wiki/Install_SASC-NG](http://dolot.kipdola.com/wiki/Install_SASC-NG)) together with Tevii S660 is something I cannot get working.

I run a modified 2.6.38 kernel using the patches found at:
[http://www.vanbest.org/drupal6/content/installing-sasc-ng-linux-2.6.38](http://www.vanbest.org/drupal6/content/installing-sasc-ng-linux-2.6.38)

When running the configure (sasc-ng package) before the compilation I use:
./configure --dvb-dir=<the linux directory in the package I downloaded in #98>
Is that correct?

It compiles and the module get loaded. When recording with mythtv or looking at a sat channel  using Kaffeine using the new virtual adapter the machine console freeze, the kernel logs fills with:
Aug 21 18:29:24 volvo kernel: [11533.040020] ata1: lost interrupt (Status 0x58)
Aug 21 18:29:24 volvo kernel: [11533.050002] ata1: drained 65536 bytes to clear DRQ.
Aug 21 18:29:24 volvo kernel: [11533.112885] ata1.00: limiting speed to UDMA/25:PIO4
Aug 21 18:29:24 volvo kernel: [11533.112890] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Aug 21 18:29:24 volvo kernel: [11533.112896] sr 0:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Aug 21 18:29:24 volvo kernel: [11533.112911] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
Aug 21 18:29:24 volvo kernel: [11533.112912]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 21 18:29:24 volvo kernel: [11533.112915] ata1.00: status: { DRDY }
Aug 21 18:29:24 volvo kernel: [11533.112941] ata1: soft resetting link
Aug 21 18:29:25 volvo kernel: [11533.330174] ata1.00: configured for UDMA/25
Aug 21 18:29:25 volvo kernel: [11533.330738] ata1: EH complete


How do I compile a working sasc-ng with a Tevii S660 DVB-S2 USB card?

Best regards
Peter Andersson

---

### Post by SnoopFogg on 2011-09-05
Hi, I just tried following the instructions in number 98 but doesn't seem to be working:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

I'm using 11.04.  Any suggestions?

---

### Post by SOME1 on 2011-09-05
Hi, 

Please try to disconnect your S660 from the power source, restart your pc and plug it again. 

Thanks.

---

### Post by SnoopFogg on 2011-09-06
Hi, it just seems really temperamental.  After the unit was unplugged and the revo restarted, it successfully scanned for channels.  When I then tried to view one using mplayer it wouldn't play.  So I went to try and scan again and got the same message "failed to open...no such device".  Tried unplugging and rebooting another 3 times but no progress.  

Can you suggest anything else?

Cheers

---

### Post by SnoopFogg on 2011-09-06
Sorry, just realised that it is a different message:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

But I was getting the "Device or resource busy" message earlier too.

---

### Post by jlazkano on 2011-09-06
> **SnoopFogg said:**
> Sorry, just realised that it is a different message:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

But I was getting the "Device or resource busy" message earlier too.

My device is working well, but you can try this: [http://www.gilzad.de/blog/pivot/entry.php?id=7](http://www.gilzad.de/blog/pivot/entry.php?id=7)

Sorry, I can not help you more, no idea.

Regards.

---

### Post by SOME1 on 2011-09-06
> **SnoopFogg said:**
> Sorry, just realised that it is a different message:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

But I was getting the "Device or resource busy" message earlier too.

it's look like you did an upgrade for your kernel packages. 
please try to reinstall & recompile the s660 driver. 

thanks.

---

### Post by SnoopFogg on 2011-09-07
Hi, I tried to reinstall the driver following the instructions in #70.  I think it was successful - these were the final lines after sudo make CONFIG_DVB_FIREDTV:=n

  CC      /home/russ/Desktop/TEVII/v4l/zr364xx.mod.o
  LD [M]  /home/russ/Desktop/TEVII/v4l/zr364xx.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
./scripts/rmmod.pl check
found 442 modules
make[1]: Leaving directory `/home/russ/Desktop/TEVII/v4l'

Following a restart and disconnecting power to the unit I seem to be back where I was:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

Also getting this after disconnecting the power again:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

Thanks for the clear instructions in #70.  The only part I think that potentially could have gone wrong was 

step 6. cd to the directory you extracted (if its the first file its TEVII directory, if it's the second it's s2-liplianin-7e47ba1d4ae8 directory). 

Here I extracted to the desktop and then cd into the TEVII file.  I wasn't sure what you meant by "if it's the second..."  Could that be a problem?

Cheers

---

### Post by SOME1 on 2011-09-08
Hi, 

while you scan for channels you need to stop/disable any software that use your device. you can't use the same device with 2 softwares. 
if you installed vdr (or similar)or you are watching tv, you need to stop this services and then scan for channels. 

please write here what you installed on your system so I can try to guide you how to stop it for the scanning, and restart it after it. 

thanks.

---

### Post by SnoopFogg on 2011-09-08
> **SOME1 said:**
> Hi, 

while you scan for channels you need to stop/disable any software that use your device. you can't use the same device with 2 softwares. 
if you installed vdr (or similar)or you are watching tv, you need to stop this services and then scan for channels. 

please write here what you installed on your system so I can try to guide you how to stop it for the scanning, and restart it after it. 

thanks.

Hi, I can't imagine what might be using the device.  The main things I have installed are: 

Boxee - used often.  starts on startup
VLC - not really used anymore
XBMC - not really used anymore
Myth - this is what I would like to use*
Mplayer - installed following the Parker1 guide in order to test whether the tuner works. Otherwise not used
Miro - used occasionally

* Would the fact I had a freeview dual tuner attached to it before have made a difference?  The freeview tuner has been removed - would the existing channel.conf make a difference? 

Cheers

---

### Post by SOME1 on 2011-09-09
sorry for the late response. 
please open your terminal, and run this commands;

```
sudo so
```
you will need to type your password here. and then run
```
lsof | grep /dev/dvb/adapter0/demux0
```

post the output here. 
this output will tell us why your device is busy.

thanks.

---

### Post by SnoopFogg on 2011-09-10
> **SOME1 said:**
> sorry for the late response. 
please open your terminal, and run this commands;

```
sudo so
```
you will need to type your password here. and then run
```
lsof | grep /dev/dvb/adapter0/demux0
```

post the output here. 
this output will tell us why your device is busy.

thanks.

Hi, see below - something wrong with the first command:

russ@revo:~$ sudo so
sudo: so: command not found
russ@revo:~$ lsof | grep /dev/dvb/adapter0/demux0
russ@revo:~$ 

Also tried:

russ@revo:~$ sudo lsof | grep /dev/dvb/adapter0/demux0
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/russ/.gvfs
      Output information may be incomplete.

Any ideas?  Cheers

---

### Post by SOME1 on 2011-09-10
sorry, it should be

```
sudo su
```

sorry again. thanks.

---

### Post by SnoopFogg on 2011-09-12
> **SOME1 said:**
> sorry, it should be

```
sudo su
```

sorry again. thanks.

Hi, I get an error message:

russ@revo:~$ sudo su
[sudo] password for russ: 
root@revo:/home/russ# lsof | grep /dev/dvb/adapter0/demux0
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/russ/.gvfs
      Output information may be incomplete.

Then there was no output - it hung for a while and went back to russ@revo:~$

---

### Post by SOME1 on 2011-09-17
you are using FUSE file system and not ext so it's looks like this file system works different with permissions issue. 

so, this is my suggestion: you'll probably run vdr or mythtv that use your card. 
so run this commands on terminal to stop them: (one of this commands should work, and the other won't so just try them both)
```
sudo /etc/init.d/vdr stop
```
```
sudo /etc/init.d/mythtv-backend stop
```
and now try to run the channels scan. if it's still not working please run this command

```
ps  -A aux >> ~/process.txt
```

this command will create a file in your home directory named "process.txt" with the running programs on your system, hopefully it will help me understand what using your card. 
attached that file to your post and I try to help. 

please report if something worked for you. 
thanks.

---

### Post by SnoopFogg on 2011-09-18
Hi, so here's what is happening following your instructions above: 

russ@revo:~$ sudo /etc/init.d/vdr stop
[sudo] password for russ: 
sudo: /etc/init.d/vdr: command not found
russ@revo:~$ sudo /etc/init.d/mythtv-backend stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting

After this it seemed to scan successfully.  Then when I went to test a channel I got this but MPlayer did not actually open:

russ@revo:~$ mplayer dvb://"BBC THREE"
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team

Playing dvb://BBC THREE.
dvb_tune Freq: 10773000
TS file format detected.

I then tried to run mythtv setup (incase it was just a problem with mplayer) but that didn't work.  Having restarted the Tevii box, I now get the same old message:

russ@revo:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

Finally did the last command to create the process file:

russ@revo:~$ ps  -A aux >> ~/process.txt

Cheers

---

### Post by SOME1 on 2011-09-18
It's looks like the driver is working ok and the problem is with mplayer and/or mythtv. 
please install an easy software for watching&scanning tv like kaffeine: 

```
sudo apt-get install kaffeine
```

then you should see the program in your menu. 
(after stop the mythtv as before) try to use it to scan your channels and watch them. if it's work then the problem is with mplayer/mythtv. 

if that's the case, please ask in another thread about it. if it's not working with kaffeine, please write here what happend. 

thanks. :)

---

### Post by SnoopFogg on 2011-09-20
Hi, I installed Kaffeine and successfully scanned for channels.  When I go to watch a channel I get an error message from Kaffeine "No available device found".  

If I reboot the computer it lets me scan again, but gives the same error message if I try to watch a channel.

Thanks

---

### Post by SOME1 on 2011-09-21
hi, 

try to uninstall mythtv from your system. you can use this command (that uninstall your personal mythtv settings as well) 

```
sudo apt-get purge mythtv
```

and then try to watch with kaffeine. 
if it's not working yet, please try to unplug you s660 from it's power source, wait a few seconds and plug it in again. restart your computer and try again. 

thanks.

---

### Post by SnoopFogg on 2011-09-22
Hi, I tried the purge command and got this after a re-scan:

russ@revo:~$ mplayer dvb://"BBC THREE"
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team

Playing dvb://BBC THREE.
dvb_tune Freq: 10773000
TS file format detected.
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 1160 bytes
dvb_streaming_read, attempt N. 5 failed with errno 0 when reading 1160 bytes
dvb_streaming_read, attempt N. 4 failed with errno 0 when reading 1160 bytes
dvb_streaming_read, attempt N. 3 failed with errno 0 when reading 1160 bytes
dvb_streaming_read, attempt N. 2 failed with errno 0 when reading 1160 bytes
dvb_streaming_read, attempt N. 1 failed with errno 0 when reading 1160 bytes
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 5 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 4 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 3 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 2 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 1 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, return 0 bytes
TS_PARSE: COULDN'T SYNC
NO VIDEO! NO AUDIO!  NO SUBS (yet)! 
No stream found.
dvb_streaming_read, attempt N. 1 failed with errno 0 when reading 4096 bytes
dvb_streaming_read, return 0 bytes
dvb_tune Freq: 10788000
FE_GET_INFO FAILED
dvb_tune, TUNING FAILED


Exiting... (End of file)


Then realised that the purge had not got rid of everything as mythbackend was still available. So removed all mythtv related parts using synaptic.

But I'm still getting errors after reboot

Kaffeine saying "Cannot find demux plugin for MRL "fifo:/home/russ/.kde/share/apps/kaffeine/dvbpipe.m2t".

and 

russ@revo:~$ mplayer dvb://"BBC THREE"
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team

Playing dvb://BBC THREE.
dvb_tune Freq: 10773000
TS file format detected.


MPlayer interrupted by signal 2 in module: demux_open
dvb_streaming_read, attempt N. 6 failed with errno 4 when reading 244 bytes

 
Thanks again

---

### Post by SOME1 on 2011-09-22
please try to run this

```
sudo apt-get install libxine1-all-plugins
```

and try to scan again with kaffeine. 

thanks

---

### Post by micantox on 2011-09-23
Hi all,

I'm facing a big problem with a slightly different device, the S630. 
I've downloaded the proper drivers from the website, copied the required firmware files in /lib/firmwares, compiled and installed the driver.

At the following reboot the system correctly recognized and
initialized the device. This is the output of the command 'cat
/var/log/messages | grep dvb'.

Sep 23 09:48:05 IDU kernel: [    8.178590] dvb-usb: found a 'TeVii
S630 USB' in cold state, will try to load a firmware
Sep 23 09:48:05 IDU kernel: [    8.178606] usb 1-5: firmware:
requesting dvb-usb-s630.fw
Sep 23 09:48:05 IDU kernel: [    8.479111] dvb-usb: downloading
firmware from file 'dvb-usb-s630.fw'
Sep 23 09:48:05 IDU kernel: [    8.908055] dvbh0: mixed HW and IP
checksum settings.
Sep 23 09:48:05 IDU kernel: [    8.997257] dvb-usb: found a 'TeVii
S630 USB' in warm state.
Sep 23 09:48:05 IDU kernel: [    8.997378] dvb-usb: will pass the
complete MPEG2 transport stream to the software demuxer.
Sep 23 09:48:12 IDU kernel: [   16.412525] dvb-usb: MAC address:
00:18:bd:5b:97:44
Sep 23 09:48:12 IDU kernel: [   16.775333] dvb-usb: schedule remote
query interval to 150 msecs.
Sep 23 09:48:12 IDU kernel: [   16.775347] dvb-usb: TeVii S630 USB
successfully initialized and connected.
Sep 23 09:57:27 IDU kernel: [    7.255661] dvbh0: mixed HW and IP
checksum settings.
Sep 23 09:57:27 IDU kernel: [    7.292012] dvb-usb: found a 'TeVii
S630 USB' in cold state, will try to load a firmware
Sep 23 09:57:27 IDU kernel: [    7.292024] usb 1-5: firmware:
requesting dvb-usb-s630.fw
Sep 23 09:57:27 IDU kernel: [    7.877607] dvb-usb: downloading
firmware from file 'dvb-usb-s630.fw'
Sep 23 09:57:27 IDU kernel: [    7.997036] dvb-usb: found a 'TeVii
S630 USB' in warm state.
Sep 23 09:57:27 IDU kernel: [    7.997164] dvb-usb: will pass the
complete MPEG2 transport stream to the software demuxer.
Sep 23 09:57:32 IDU kernel: [   14.784140] dvb-usb: MAC address:
00:18:bd:5b:97:44
Sep 23 09:57:33 IDU kernel: [   15.632086] dvb-usb: TeVii S630 USB
successfully initialized and connected.

As far as I understood, this should lead to the creation of the
required device nodes in /dev/dvb/adapter0/, namely demux0, dvr0,
frontend0 and net0. None of this happens.

I've even tried to create an on purpose udev rule in
/etc/udev/rules.d/, called 70-persistent-dvb.rules, containing the
following rules.

```
KERNEL=="dvb0.dvr0", SUBSYSTEM=="dvb", MODE="0666"
KERNEL=="dvb0.demux0", SUBSYSTEM=="dvb", MODE="0666"
KERNEL=="dvb0.frontend0", SUBSYSTEM=="dvb", MODE="0666"
KERNEL=="dvb0.net0", SUBSYSTEM=="dvb", MODE="0666"

```
But, still, no device nodes get created.

How to solve this?

Best regards,
M.

---

### Post by SOME1 on 2011-09-23
Hi, 

I can't promise I can help about s630 becouse and I don't have one, but I can try. 

you can try the last liplianin driver. 
download it from [here]("http://mercurial.intuxication.org/hg/s2-liplianin/archive/tip.zip"). 
use [this instructions]("http://ubuntuforums.org/showpost.php?p=10844374&postcount=70") to install it. 
after the installation finished, please plug the power source from your s630 off, restart  your computer and plug it in again. 

report here for the results.

thanks.

---

### Post by micantox on 2011-09-23
> **SOME1 said:**
> 
report here for the results.

thanks.

Hi SOME1,

still nothing. Similar results as before in /var/log/messages

```
Sep 23 13:29:26 IDU kernel: [   10.575454] dvbh0: mixed HW and IP checksum settings.
Sep 23 13:29:26 IDU kernel: [   10.680159] dvb-usb: found a 'TeVii S630 USB' in cold state, will try to load a firmware
Sep 23 13:29:26 IDU kernel: [   10.680179] usb 1-6: firmware: requesting dvb-usb-s630.fw
Sep 23 13:29:26 IDU kernel: [   11.264436] dvb-usb: downloading firmware from file 'dvb-usb-s630.fw'
Sep 23 13:29:26 IDU kernel: [   11.398236] dvb-usb: found a 'TeVii S630 USB' in warm state.
Sep 23 13:29:26 IDU kernel: [   11.398348] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Sep 23 13:29:26 IDU kernel: [   11.398907] dvb-usb: MAC address: 00:00:00:00:00:00
Sep 23 13:29:26 IDU kernel: [   12.135046] dvb-usb: TeVii S630 USB successfully initialized and connected.
Sep 23 13:29:26 IDU kernel: [   12.136185] dvb-usb: TeVii S630 USB successfully deinitialized and disconnected.
Sep 23 13:29:26 IDU kernel: [   13.219300] dvb-usb: found a 'TeVii S630 USB' in cold state, will try to load a firmware
Sep 23 13:29:26 IDU kernel: [   13.219314] usb 1-6: firmware: requesting dvb-usb-s630.fw
Sep 23 13:29:26 IDU kernel: [   21.142654] dvb-usb: downloading firmware from file 'dvb-usb-s630.fw'
Sep 23 13:29:26 IDU kernel: [   21.412092] dvb-usb: found a 'TeVii S630 USB' in warm state.
Sep 23 13:29:26 IDU kernel: [   21.412186] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Sep 23 13:29:26 IDU kernel: [   22.743238] dvb-usb: MAC address: 00:18:bd:5b:97:44
Sep 23 13:29:26 IDU kernel: [   22.926892] dvb-usb: TeVii S630 USB successfully initialized and connected.
```

but still no /dev/dvb/adapter0 created (no /dev/dvb at all, actually).

I've another box (they are Atom-based low powered machines), with the very same hardware configuration and software set-up and that works properly.

Regretfully, I cannot mix hardware in my tries because one of these setups is physically far away from my place, so I cannot exclude hardware problems of the remote one.

Thanks!
M.

---

### Post by SOME1 on 2011-09-23
Do you use USB hub? if yes, please connect it directly to your pc. please try to connect it to a diffrent usb port and check your usb cable too. 

thanks.

---

### Post by micantox on 2011-09-23
> **SOME1 said:**
> Do you use USB hub? if yes, please connect it directly to your pc. please try to connect it to a diffrent usb port and check your usb cable too.

Regretfully I cannot do any more tries until Monday. Anyway, it seems to me that there are different problems, since at system logging level everything seems to be properly working.

The only missing step so far is the device nodes creation. I really can't see why this step is not triggered by the driver.

Thanks a lot!
M.

---

### Post by SOME1 on 2011-09-23
I had a similar problem with my s660 card in the past and I solve it simply by changing the usb port. it's look like on of my usb device wasn't working ok. It's worth a try. 

please write here if there is any change. 
thanks :)

---

### Post by micantox on 2011-09-23
> **SOME1 said:**
> I had a similar problem with my s660 card in the past and I solve it simply by changing the usb port. it's look like on of my usb device wasn't working ok. It's worth a try. 

please write here if there is any change. 
thanks :)

Ok,thanks for sharing your opinions and experience. I'll give it a try for sure on Monday, even if I've already tried on two different USB ports out of four... Hope to be luckier with the other two.

Thanks again!
M.

---

### Post by dilbert2k on 2011-09-24
> **SOME1 said:**
> 7. before you can install the driver you need to make sure you have everything you need install. so type in the terminal
```
sudo apt-get install linux-headers-`uname -r` build-essential
```
8. now let's install :) - type this
```
sudo make CONFIG_DVB_FIREDTV:=n 
```
this step take some time. 

 
 
Hi,
 
I'm trying to get my S660 running on 11.04, kernel 2.6.38-11-generic.
 
Step 7 completes successfully, but step 8 fails with this error:
```
Preparing to compile for kernel version 2.6.38
File not found: /lib/modules/2.6.38-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'. Stop.
make[1]: Leaving directory `/home/mark/S660_Drivers/TEVII/v4l'
make: *** [all] Error 2
```
 
It seems to be looking for the wrong kernel version. Any advice please?
 
Thanks
Mark

---

### Post by SOME1 on 2011-09-24
what version of drivers did you use? 

thanks.

---

### Post by dilbert2k on 2011-09-24
Hi
 
Very prompt reply!
 
I used the divers linked in post #92
 
Thanks
Mark

---

### Post by SOME1 on 2011-09-24
please try [this]("http://mercurial.intuxication.org/hg/s2-liplianin/archive/tip.zip") driver.

thanks.

---

### Post by micantox on 2011-09-29
> **micantox said:**
> Ok,thanks for sharing your opinions and experience. I'll give it a try for sure on Monday, even if I've already tried on two different USB ports out of four... Hope to be luckier with the other two.

Thanks again!
M.

Ok, it was exactly that problem... at the very last port out of four the driver brought up the device node as well.

I guess it is not a hardware problem: it perhaps expects a specific port for the TeVii to be connected on.

Thanks a lot!
M.

---

### Post by _whitehawk_ on 2011-10-22
It's been a while since I've played with this tuner again (I just settled with most of the FreeSat channels, but only ITV1 HD).

Anyway, I've just upgraded my master backend to Ubuntu Server 11.10, which has the new v3 kernel.

Well... I'm not sure what's changed (I assume a newer version of the driver in the main kernel tree and maybe even generic v4l changes), but now my tuner card tunes into everything :-)

Keep up the good work on the driver :-)

Cheers,
Gav.

---

### Post by SOME1 on 2011-10-22
Hi, 

you can try the last liplianin driver. 
download it from [here]("http://mercurial.intuxication.org/hg/s2-liplianin/archive/tip.zip"). 
use [this instructions]("http://ubuntuforums.org/showpost.php?p=10844374&postcount=70") to install it. 
after the installation finished, please plug the power source from your s660 off, restart  your computer and plug it in again. 

report here for the results.
thanks.

---

### Post by mutant_matt on 2011-11-10
SOME1, just a note for you, and for anyone else coming to this thread now or in the future.  After struggling with getting this working with my S660 USB on 10.04 and 10.10 (but we got there in the end, compiling the drivers/modules), I have just revisited this project that I never got beyond "proof of concept", last summer.  I want to get going again on building my myth box so last night I:

1. Downloaded the Mythbuntu 11.10 ISO (currently comes with kernel 3.0.0-12-generic)
2. Booted the ISO in a VM and installed myth to a 4GB USB stick (POC USB stick ;) :D )
3. Booted the USB stick on an Acer Revo (3610/ION1)
4. Copied in the firmware files, connected the S660, boom, everything came right up
5. Scanning and watching via VLC and mplayer worked, myth the same.

So now, in only a few hours, I have a working POC myth system with one S660 USB, OS and myth running off a USB stick (I pointed the recordings area at a hard drive though), where as a test I was able to record BBC HD, BBC 1 HD concurrently, and watch another SD channel.  Now I just need more tuners and to purchase the hardware for the real box.

SOME1, again, thanks for all your help.  I'm guessing now the drivers are now part of the main tree, you should be able to have a rest now! ;) :D

From what I can see on: [http://linuxtv.org/wiki/index.php/TeVii_S480](http://linuxtv.org/wiki/index.php/TeVii_S480), it looks like the 480 is also now supported in the main tree, "out of the box"? (which is probably my next move, in addition to the 660).  As far as you know, they should play nicely together?

Thanks again,

Cheers,

Matt :)

---

### Post by SOME1 on 2011-11-12
Hi Matt, 

thanks for the update. 
as far as I know there is no reason why s480 and s660 wont work together. 

I am glad that no one will need to compile the drivers again. :) 

(at least until tevii next product :) )

glad I could help. 

Dotan.

---

### Post by Tillda on 2011-12-07
Have tried all drivers I think but still not working. Running YAVDR 4.0 please someone help. Rgds Tillda


sovrum@ubuntu:~$ dmesg |grep dvb
[   16.952908] dvb-usb: found a 'TeVii S650 USB2.0' in cold state, will try to load a firmware
[   19.293194] dvb-usb: downloading firmware from file 'dvb-usb-dw2104.fw'
[   20.180113] dvb-usb: found a 'TeVii S650 USB2.0' in warm state.
[   20.180436] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.278161] dvb-usb: MAC address reading failed.
[   20.850333] dvb-usb: no frontend was attached by 'TeVii S650 USB2.0'
[   20.904532] dvb-usb: schedule remote query interval to 150 msecs.
[   20.904551] dvb-usb: TeVii S650 USB2.0 successfully initialized and connected.
[   21.061324] dvb-usb: TeVii S650 USB2.0 successfully deinitialized and disconnected.
[   21.881783] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
[   21.911662] dvb-usb: downloading firmware from file 'dvb-usb-s660.fw'
[   22.040105] dvb-usb: found a 'TeVii S660 USB' in warm state.
[   22.040301] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   22.172570] dvb-usb: MAC address: ff:ff:ff:ff:ff:ff
[   22.181778] dvb-usb: no frontend was attached by 'TeVii S660 USB'
[   22.183486] dvb-usb: schedule remote query interval to 150 msecs.
[   22.183506] dvb-usb: TeVii S660 USB successfully initialized and connected.
sovrum@ubuntu:~$ w_scan -fs -s S0W8
w_scan version 20101001 (compiled for DVB API 5.2)
using settings for 0.8 west Thor 3/5 & Intelsat 10-02
frontend_type DVB-S, channellist 50
output format vdr-1.6
Info: using DVB adapter auto detection.
main:2960: FATAL: ***** NO USEABLE DVB CARD FOUND. *****

---

### Post by Purple8 on 2011-12-11
> **mutant_matt said:**
> SOME1, just a note for you, and for anyone else coming to this thread now or in the future.  After struggling with getting this working with my S660 USB on 10.04 and 10.10 (but we got there in the end, compiling the drivers/modules), I have just revisited this project that I never got beyond "proof of concept", last summer.  I want to get going again on building my myth box so last night I:

1. Downloaded the Mythbuntu 11.10 ISO (currently comes with kernel 3.0.0-12-generic)
2. Booted the ISO in a VM and installed myth to a 4GB USB stick (POC USB stick ;) :D )
3. Booted the USB stick on an Acer Revo (3610/ION1)
4. Copied in the firmware files, connected the S660, boom, everything came right up
5. Scanning and watching via VLC and mplayer worked, myth the same.

So now, in only a few hours, I have a working POC myth system with one S660 USB, OS and myth running off a USB stick (I pointed the recordings area at a hard drive though), where as a test I was able to record BBC HD, BBC 1 HD concurrently, and watch another SD channel.  Now I just need more tuners and to purchase the hardware for the real box.

SOME1, again, thanks for all your help.  I'm guessing now the drivers are now part of the main tree, you should be able to have a rest now! ;) :D

From what I can see on: [http://linuxtv.org/wiki/index.php/TeVii_S480](http://linuxtv.org/wiki/index.php/TeVii_S480), it looks like the 480 is also now supported in the main tree, "out of the box"? (which is probably my next move, in addition to the 660).  As far as you know, they should play nicely together?

Thanks again,

Cheers,

Matt :)
Hi what firmware files did you usethe ones from tevii?? thanks

---

### Post by charlie0440 on 2012-01-03
> **Tillda said:**
> Have tried all drivers I think but still not working. Running YAVDR 4.0 please someone help. Rgds Tillda

I just installed it today using the yavdr PPAs:

1) follow the instructions in post #134
2) Add yavdr PPAs, stable-vdr, stable-xbmc, (main & stable-yavdr -dont know if you need these last two). They are all found [here including instructions on how to install]("https://launchpad.net/~yavdr")

3) Install vdr:
sudo apt-get install vdr vdr-plugin-xineliboutput vdr-plugin-xvdr vdr-plugin-vnsiserver vdr-plugin-eepg

4) install xbmc
sudo apt-get install xbmc xbmc-addon-xvdr

5) add your channels to:
nano /etc/vdr/channels.conf

All working fine via VNSI. For some reason XVDR was not available within XBMC

Edit: ^^ on 11.10

---

### Post by scox_nz on 2012-01-10
I have updated the (current) stock ubuntu kernel modules for the S660 to include Igor's changes from s2-liplianin-ahead.

This mostly includes showing a tuned LED on the box (glows blue when the satellite is tuned).

The files changed are:
[LIST]
[*]linux-source-3.0.0/drivers/media/dvb/frontends/ds3000.c
[*]linux-source-3.0.0/drivers/media/dvb/frontends/ds3000.h
[*]linux-source-3.0.0/drivers/media/dvb/dvb-usb/dw2102.c
[/LIST]

This changes the ds3000 module and the dvb_usb_dw2102 modules.

cheers,
S. Cox

---

### Post by art2003 on 2012-01-14
Anybody got the Geniatek HD_STAR to work (with kernel 3.0.8)

I have another card that works fine.
But this one creates adapter0 and gives a lock but vdr shows nothing on the screen with this card 

```

1f4d:3000 G-Tek Electronics Group 

```

```


[   41.950200] dw2102: su3000_power_ctrl: 1, initialized 1
[   41.950208] 
[   41.960522] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   42.012176] ds3000_firmware_ondemand: Waiting for firmware upload(2)...

```

---

### Post by sam667 on 2012-02-05
> **SOME1 said:**
> Hi, 

you can try the last liplianin driver. 
download it from [here]("http://mercurial.intuxication.org/hg/s2-liplianin/archive/tip.zip"). 
use [this instructions]("http://ubuntuforums.org/showpost.php?p=10844374&postcount=70") to install it. 
after the installation finished, please plug the power source from your s660 off, restart  your computer and plug it in again. 

report here for the results.
thanks.

I've got the S480 card and I cant get it to work on a brand new install of Mythbuntu 11.04

> 
uname -r
3.0.0-12-generic


> 
dmesg | grep -i dvb
[   14.075393] dvb-usb: found a 'TeVii S480.1 USB' in cold state, will try to load a firmware
[   14.108170] dvb-usb: did not find the firmware file. (dvb-usb-s660.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   14.108188] dvb-usb: found a 'TeVii S480.2 USB' in cold state, will try to load a firmware
[   14.109125] dvb-usb: did not find the firmware file. (dvb-usb-s660.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)


I have followed the instructions, but on step 8 I get:
> 
make -C /root/TEVII/v4l 
make[1]: Entering directory `/root/TEVII/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.38
File not found: /lib/modules/2.6.38-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/root/TEVII/v4l'
make[1]: Entering directory `/root/TEVII/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.38
File not found: /lib/modules/2.6.38-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/root/TEVII/v4l'
make: *** [all] Error 2


Does anyone have any idea?

---

### Post by SOME1 on 2012-02-05
Sorry I didn't reply here in the past weeks. (personal issue). 
art2003 & sam667 - 
I attached a file to this post. 
please download it and put all the fw files in your /lib/firmware/ directory (you will need root privilege for that). you can do it in your own way or open your terminal, cd to the directory where you save fw.zip file and run 
```
sudo unzip -o ./fw.zip -d /lib/firmware/
```

then restart your linux and check if this works. if not, you need to compile the driver. write here and I'll try to help.

---

### Post by art2003 on 2012-02-05
Same result, lsmod shows ds3000 is loaded and femon shows a lock.
I can even scan for channels but black screen (on FTA channels with good signal)

> **SOME1 said:**
> Sorry I didn't reply here in the past weeks. (personal issue). 
art2003 & sam667 - 
I attached a file to this post. 
please download it and put all the fw files in your /lib/firmware/ directory (you will need root privilege for that). you can do it in your own way or open your terminal, cd to the directory where you save fw.zip file and run 
```
sudo unzip -o ./fw.zip -d /lib/firmware/
```

then restart your linux and check if this works. if not, you need to compile the driver. write here and I'll try to help.

---

### Post by SOME1 on 2012-02-05
this usually happens because of bad usb port or bad usb cable. please try a different usb port and different usb cable. 
also, please make sure it's not a software problem. to make sure, you can install kaffeine (user friendly gui interface for scan and watch). if it's work with kaffeine it's a software problem. 

to install kaffeine run in terminal
```
sudo apt-get install kaffeine
```

---

### Post by string158 on 2012-02-06
Thanks Some1,  I think I have been having similar issues to art2003.  I've been able to scan, but have had issues watching channels, and getting the card hooked up with TVheadend or Mythtv.  I'm going to try the firmware & kaffiene tonight.  


For a while I thought I might have had a hardware issue,  but managed to discount that by installing XP in VM and getting the card to work... 


Just out of interest,  is the Zip you just uploaded any different to the previous firmware in 660.zip which you uploaded previously?

---

### Post by art2003 on 2012-02-06
you can run diff  file_1   file_2

and that will tell you if the 2 files are identical (do that for the firmware files)

In my case I have decided to return it to the seller since in the manual it says it supports only Diseqc 1.0 and explicitly lists diseq 1.2 (rotor) as not supported and I would like to use a rotor in the near future.

> **string158 said:**
> Thanks Some1,  I think I have been having similar issues to art2003.  I've been able to scan, but have had issues watching channels, and getting the card hooked up with TVheadend or Mythtv.  I'm going to try the firmware & kaffiene tonight.  


For a while I thought I might have had a hardware issue,  but managed to discount that by installing XP in VM and getting the card to work... 


Just out of interest,  is the Zip you just uploaded any different to the previous firmware in 660.zip which you uploaded previously?

---

### Post by string158 on 2012-02-06
Thanks Art2003, that another command to add to my ever growing list! I'll give it a try when I get home tonight.

---

### Post by sam667 on 2012-02-06
> **SOME1 said:**
> Sorry I didn't reply here in the past weeks. (personal issue). 
art2003 & sam667 - 
I attached a file to this post. 
please download it and put all the fw files in your /lib/firmware/ directory (you will need root privilege for that). you can do it in your own way or open your terminal, cd to the directory where you save fw.zip file and run 
```
sudo unzip -o ./fw.zip -d /lib/firmware/
```

then restart your linux and check if this works. if not, you need to compile the driver. write here and I'll try to help.

Thanks SOME1, I can now see the card(s).
I'm using sasc-ng which has created two "mirrors" of the 2 DVBs but in Kaffeine card 3 + 4 shows up as DVBS rather than DVBS2, any ideas about this?
Also, I cant scan on them.. I've recompiled sasc-ng with the 3.0.0.15 Kernel

Thanks again!!

---

### Post by dumbo79 on 2012-02-07
Hi,

Now I think I should give MythTv a new chance. I have installed the drivers for my Tevii S660 card and if I run dmesg | grep dvb I see the following message:

[   20.926020] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
[   24.602222] dvb-usb: downloading firmware from file 'dvb-usb-s660.fw'
[   24.728498] dvb-usb: found a 'TeVii S660 USB' in warm state.
[   24.728710] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   24.873467] dvb-usb: MAC address: 00:18:bd:5c:5f:e3
[   24.886174] dvb-usb: schedule remote query interval to 150 msecs.
[   24.886189] dvb-usb: TeVii S660 USB successfully initialized and connected.
[   24.886256] dvb-usb: found a 'TeVii S660 USB' in cold state, will try to load a firmware
[   24.900711] dvb-usb: downloading firmware from file 'dvb-usb-s660.fw'
[   25.020141] dvb-usb: found a 'TeVii S660 USB' in warm state.
[   25.020341] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   25.152086] dvb-usb: MAC address: 00:18:bd:5c:5f:cb
[   25.157670] dvb-usb: schedule remote query interval to 150 msecs.
[   25.157685] dvb-usb: TeVii S660 USB successfully initialized and connected.

This seems to be ok (I have 2 S660 cards), but when I try to do a channel scan:

scan /usr/share/dvb/dvb-s/Thor-1.0W > thor_channels.conf

I get the following error:

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

Someone has any idea of what could be wrong?

---

### Post by SOME1 on 2012-03-03
As mention here before, in Ubuntu 12.04 (And maybe in previous version as well) all you need to do is to copy the fw files to /lib/firmware/ and then enable the build in restricted dvb driver in the ubuntu menu. after restarting your computer the tevii should work without compiling the driver manually as needed before.

---

### Post by hoke4040 on 2012-04-21
Hi I have a tevii s480 wich is basicly 2 s660. I get most of HD channals working fine but SD channals very stuttering just like bad reception. But when I try with dedicated receiver I get 100% signal quality and no stutter so my lnb and dish is fine. Why do I get thease stutter? and HD channels on 30000Kb isnt working at all

---

### Post by druggo on 2012-04-24
Hi i am too fiddling with S660 under ubuntu, the case with 30000 SR HD channels can be because their USB chip simply cannot handle the bandwidth needed. 

Someone need to get this confirmed with Tevii though. I'm through talking to them..

Druggo

---

### Post by mikulator on 2012-06-23
SOME1 -> Would what you suggest above be like this:

```

sudo cp dvb-usb-s660.fw /lib/firmware/
sudo cp dvb-fe-ds3000.fw /lib/firmware/

```
To install them permanently I could then do?
```

sudo jockey-text –enable=dvb-usb-s660.fw
sudo jockey-text –enable=dvb-fe-ds3000.fw

```

I am trying to move to 12.04 and it is not going to well with this driver.

Or am I missing something?


Cheers
Mik

---

### Post by SOME1 on 2012-06-23
in ubuntu 12.04 you can try 2 things: 
1. the driver in ubuntu restricted drivers as mentioned before. 
2. if you have issues, you can try compile the new liplianin driver by do this: 

1. copy the fw file as mentioned [here]("http://ubuntuforums.org/showpost.php?p=11666215&postcount=143"). 
2. open your terminal and type: 
```
sudo apt-get install linux-headers-`uname -r` build-essential mercurial
```
3. now you need to download the new driver. to do this type in terminal
```
hg clone http://pikacode.com/liplianin/s2-liplianin-v35
```
4. cd to the directory you just downloaded by typing
```
cd s2-liplianin-v35
```
5. compile the driver
```
sudo make
```
6. install the driver
```
sudo make install
```
7. after it's done, plug your tevii s660 out from it's power source and plug it in again and restart your computer. it's should work now. 

hope it will help you.

---

### Post by mikulator on 2012-06-23
Thanx for the fast reply

I did try to compile the driver but with no succes - using linuxTvWiki.

But I did not try the restricted drives in ubuntu... I misunderstood your post above. I will try that.

Cheers,
mik

---

### Post by mikulator on 2012-06-23
Just had to reply

using the additional drivers in mythbuntu 12.04 LTS in combination with downloaded drivers worked for my S480 PCIe card!

Here is what I did:
```

  Applications > Settings > Additional Drivers
   Activate
        "Firmware for DVB cards"
  
```then from the terminal
```

sudo -s
cd /usr/local/src wget [http://www.tevii.com/s2_liplianin_1.tar](http://www.tevii.com/s2_liplianin_1.tar) 
tar xvf s2_liplianin_1.tar 
cd tevii_s2_liplianin-eb8a914cd499/linux/firmware/ 
cp dvb-usb-s660.fw /lib/firmware/
cp dvb-fe-ds3000.fw /lib/firmware/ 

```leaving out the last one will not make it work

---

### Post by SOME1 on 2012-06-30
> **SOME1 said:**
> in ubuntu 12.04 you can try 2 things: 
1. the driver in ubuntu restricted drivers as mentioned before. 
2. if you have issues, you can try compile the new liplianin driver by do this: 

1. copy the fw file as mentioned [here]("http://ubuntuforums.org/showpost.php?p=11666215&postcount=143"). 
2. open your terminal and type: 
```
sudo apt-get install linux-headers-`uname -r` build-essential mercurial
```
3. now you need to download the new driver. to do this type in terminal
```
hg clone http://pikacode.com/liplianin/s2-liplianin-v35
```
4. cd to the directory you just downloaded by typing
```
cd s2-liplianin-v35
```
5. compile the driver
```
sudo make
```
6. install the driver
```
sudo make install
```
7. after it's done, plug your tevii s660 out from it's power source and plug it in again and restart your computer. it's should work now. 

hope it will help you.

a little fix to this instructions:
1. stage 2 should be
open your terminal and type: 
```
sudo apt-get install linux-headers-`uname -r` build-essential mercurial libproc-processtable-perl
```
2. if you are using amd64 version, please replace stage 5 with 
5. compile the driver
```
sudo make -j2
```

---

### Post by mikulator on 2012-07-02
sorry I am a bit confused.

Do you prefer the drivers from (a) your previous post 

[http://ubuntuforums.org/showpost.php?p=11666215&postcount=143](http://ubuntuforums.org/showpost.php?p=11666215&postcount=143)

(b) the ones I used 

from s2_liplianin_1.tar

or (c) compiled driver?

cheers

---

### Post by SOME1 on 2012-07-02
if you are using ubuntu 12.04 the only working drivers as far as I know is [this one]("http://ubuntuforums.org/showpost.php?p=12065528&postcount=158"). 
If you are using previous version of ubuntu you should try the previous suggestion as posted before.

---

### Post by mikulator on 2012-07-02
sorry I may be a bit thick...](*,)and may have confused you by my previous post

I am running 12.04 on a test system with a the PCIe S480 

I have used the additional drivers i 12.04 which work together with the firmware in s2_liplianin_1.tar file i download. This is however only based on short testing in my test system.

Would you rather suggest using the firmware from your zip file from [here]("http://ubuntuforums.org/showpost.php?p=11666215&postcount=143")?

And is it best to compile the driver than use ubuntus additional driver?

cheers

---

### Post by SOME1 on 2012-07-02
that's probably the same firmware. 
the diffrence is in the driver. 

there is a new firmware on tevii site, so if you have issues with the firmware you can try the new one. 
I found that the old one works better for me. 

the compiled driver is also works better than ubuntu restricted driver for me, but you may found other results on your system.

---

### Post by adamskiteam on 2012-08-25
For every time I make I give the command receives an error, can someone help me. I have ubuntu 12.10.Thx

[PHP]make -C /root/s2-liplianin/v4l
make[1]: Entering directory `/root/s2-liplianin/v4l'
perl scripts/make_config_compat.pl /lib/modules/3.2.0-29-generic-pae/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/root/s2-liplianin/v4l/firmware'
make[2]: Leaving directory `/root/s2-liplianin/v4l/firmware'
make -C firmware
make[2]: Entering directory `/root/s2-liplianin/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/root/s2-liplianin/v4l/firmware'
Kernel build directory is /lib/modules/3.2.0-29-generic-pae/build
make -C /lib/modules/3.2.0-29-generic-pae/build SUBDIRS=/root/s2-liplianin/v4l CFLAGS="-I../linux/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /root/s2-liplianin/v4l/tuner-xc2028.o
/root/s2-liplianin/v4l/tuner-xc2028.c: In function 'xc2028_set_params':
/root/s2-liplianin/v4l/tuner-xc2028.c:1178:5: error: 'T_DIGITAL_TV' undeclared (first use in this function)
/root/s2-liplianin/v4l/tuner-xc2028.c:1178:5: note: each undeclared identifier is reported only once for each function it appears in
/root/s2-liplianin/v4l/tuner-xc2028.c:1179:1: warning: control reaches end of non-void function [-Wreturn-type]
make[3]: *** [/root/s2-liplianin/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/root/s2-liplianin/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/s2-liplianin/v4l'
make: *** [all] Error 2
[/PHP]

---

### Post by mikulator on 2012-08-27
but you should not have to build your own drivers... I got it to work by doing as written in my post from the June 24th, 2012 01:29 AM

---

### Post by jksj on 2012-08-27
High all, thinking about buying one of these for use with Freesat in the UK. It is difficult to tell from such a large set of problem reports whether the device is currently reliable with mythtv.  So based on Mikulator's post "I got it to work by doing as written in my post from the June 24th, 2012 01:29 AM" - does this mean it works for days at a time without losing any recordings?

---

### Post by mikulator on 2012-08-27
I have had very very few problems with recordings and this could (most likely) be related to mythbuntu being a bit buggy.

If you want a recommendation... I can only give it, in comparison to my other S2 dvb cards: technotrend S2-3200.


HD is good
Tuning is good
Install was ok easy - a little special because the system ses them as two usb based cards.





 Cheers

---

### Post by jksj on 2012-08-28
Thanks I will go ahead and buy one.:KS

---

### Post by jksj on 2012-09-04
Bought one .. Works fine in Kaffeine but only when initialized by windows. I am running on a dual boot laptop.If I boot up win7 the blue light on the adaptor flashes once before login - reboot to ubuntu - blue light flashes once then everything fine, note blue light does not light up when tuner working in ubuntu but does in windows.
When I boot directly into Ubuntu after power cycling the receiver, the blue light still flashes but the DS3000 front end fails to initialise.
Running ubuntu 12.04.1 - 3.2.0-29-generic ie 64 bit.
Using the kernel built in driver and have tried the firmware from the Tevii website and from post 143.


```
Sep  4 07:53:27 laptop-Ideapad-Z560 kernel: [   21.543629] DVB: registering new adapter (TeVii S660 USB)
Sep  4 07:53:27 laptop-Ideapad-Z560 kernel: [   21.573010] usb 2-1.4: USB disconnect, device number 4
Sep  4 07:53:27 laptop-Ideapad-Z560 kernel: [   21.573789] dvb-usb: MAC address: 70:70:70:70:70:70
Sep  4 07:53:27 laptop-Ideapad-Z560 kernel: [   21.678253] lirc_dev: IR Remote Control driver registered, major 250 
Sep  4 07:53:27 laptop-Ideapad-Z560 kernel: [   21.687547] IR LIRC bridge handler initialized
Sep  4 07:53:27 laptop-Ideapad-Z560 kernel: [   21.772836] Invalid probe, probably not a DS3000
Sep  4 07:53:27 laptop-Ideapad-Z560 kernel: [   21.772842] dvb-usb: no frontend was attached by 'TeVii S660 USB' 
```

The version of dfvb-fe-ds3000.fw in /lib/firmware is dated 18 May 2012.

---

### Post by jksj on 2012-09-04
Further info on the problem where the receiver works when initialised in windows but not in linux. 
The fault changes when a different usb port is used. The message is

```
Sep  4 10:15:55 laptop-Ideapad-Z560 kernel: [   63.633200] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
Sep  4 10:15:55 laptop-Ideapad-Z560 kernel: [   63.644412] ds3000_firmware_ondemand: Waiting for firmware upload(2)...
```So the issue is definitely related to USB timing, both the usb ports i have tried work perfectly on a warm device so I am stuck.
Any ideas?;)

Attempting to compile the driver fails with :-
```
/home/laptop/s2-liplianin-v35/v4l/saa716x_ff_cmd.c:137:12: warning: 'sti7109_do_raw_osd_cmd' defined but not used [-Wunused-function]
make[3]: *** [/home/laptop/s2-liplianin-v35/v4l/saa716x_ff_cmd.o] Error 1
make[3]: *** Waiting for unfinished jobs....
cc1: some warnings being treated as errors
```

---

### Post by jksj on 2012-09-05
Further update - receiver now working perfectly in Mythtv :) **but **If the power is turned off and on the receiver has to be re-initialised in windows.So presumably I am using either the wrong firmware or the driver built into 12.04 is not good at cold start.

Please post which firmware has been successfully used with the 12.04 driver or how to get the liplinian driver to compile.

---

### Post by nickrout on 2012-09-05
> **jksj said:**
> Further update - receiver now working perfectly in Mythtv :) **but **If the power is turned off and on the receiver has to be re-initialised in windows.So presumably I am using either the wrong firmware or the driver built into 12.04 is not good at cold start.

Please post which firmware has been successfully used with the 12.04 driver or how to get the liplinian driver to compile.

Copy the firmware from the windows partition to the mythbuntu partition.

---

### Post by jksj on 2012-09-05
Thanks - I thought of that but the firmware files are not that obvious, there are a couple of cat files of the right size but they probably need reformatting. I note that there is avtivity on linux-media to address this issue, so I would like to try an updated driver if I can get it to compile.

[http://www.mail-archive.com/linux-media@vger.kernel.org/msg51236.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg51236.html)

---

### Post by WytseTalsma on 2012-11-25
> **jksj said:**
> Further update - receiver now working perfectly in Mythtv :) **but **If the power is turned off and on the receiver has to be re-initialised in windows.So presumably I am using either the wrong firmware or the driver built into 12.04 is not good at cold start.
 
Please post which firmware has been successfully used with the 12.04 driver or how to get the liplinian driver to compile.
 
I have the exact same problem! Have you already found a solution?
I've used various driver versions from v4l and liplinian and on both ubuntu and debian I get this problem. Currently running Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-32-generic x86_64).

---

### Post by jksj on 2012-11-26
No i gave up and bought a TBS 6920 which is rock solid.
I found that there was some work going on to address the problem. Google DS3000 firmware in [http://git.linuxtv.org/media_tree.git](http://git.linuxtv.org/media_tree.git). I tried the patches against the latest V4Linux build from [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) with no success. On my system the card would work reliably (after a cold start in windows) for a couple of days and then kill the USB subsystem to the extent that the machine would not boot until after a full power cycle.  I gave up after about a month of this.

---

### Post by mikulator on 2012-11-27
I have 2 PCIe versions which in reality are the equivalent to 4 USB versions and have had no issues at all - just installed them yesterday on mythbuntu 12.04.1 and they worked great

I don't know if other cards are better...

Cheers

This is basically what I did (note that this is from my install script so not all is valid, but it did work)
```

sudo wget http://www.tevii.com/s2_liplianin_1.tar # these are older but work
sudo tar xvf s2_liplianin_1.tar

cd tevii_*/linux/firmware/

sudo cp dvb-fe-cx24116.fw /lib/firmware/
sudo cp dvb-fe-ds3000.fw /lib/firmware/
sudo cp dvb-usb-s630.fw /lib/firmware/
sudo cp dvb-usb-s660.fw /lib/firmware/
sudo cp dvb-usb-teviis660.fw /lib/firmware/

sudo jockey-text -e firmware:dvb_usb # enable additional driver in mythbuntu for tevii

```

---

### Post by Knasher on 2013-01-07
I'm using my S660 along with its remote in lirc through devinput and I'm having a bit of a problem with it.  When I use it to tune into sat streams, after a while the blue light will flash on the front of the device and the remote will stop working until my next restart.  Nothing appears in any logs I've looked at so I'm unsure where else to start.  

If anyone has seen anything similar or has any idea on how to fix this, any info would be appreciated.

---

### Post by mikulator on 2013-01-08
I use the PCIe versions and do not have any issues.

There have been others that have noted something about power management on USB ports - in the BIOS.

---

### Post by WytseTalsma on 2013-01-13
Today I've performed an kernel update after which I've downloaded, compiled and installed the latest drivers. Now I get something new visible in dmesg, which looks good:
 
```
[   37.976563] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   37.979650] ds3000_firmware_ondemand: Waiting for firmware upload(2)...
[   39.688208] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   39.689358] ds3000_firmware_ondemand: Waiting for firmware upload(2)...
[   40.726444] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   40.727501] ds3000_firmware_ondemand: Waiting for firmware upload(2)...

``` (yes, I have three of them ;))
 
Running kernel 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux 
with the latest v4l drivers and the firmware suggested by mikulator.
I've not yet had a cold reboot, I will let you all know if all is OK after the next power failure or full system maintenance/reboot.

---

### Post by art2003 on 2013-01-14
I have used several PCI DVB-S cards with zero problems, until one day I got an ION motherboard and then needed USB DVB-S cards and ... lots of problems. Even cards reported to be working fine, were so only with Diseqc 1.0 but did not support Diseqc 1.2 (rotor)

If anybody has used a usb dvb-s (or dvb-s2) card under linux with a rotor and working properly, please say so and what card you used.

---

### Post by WytseTalsma on 2013-01-23
After a cold boot the firmware is now loaded correctly :) I have a lot of continuity counter errors and stuttering though.. but that's a different problem.

---

### Post by dilbert2k on 2013-02-13
Hello

After previous bad experiences with this tuner, I've had my Tevii S660 working well for 3 weeks on MythTV 0.25 on Ubuntu 12.10, and was finally becoming quite pleased with it. Until last Sunday when it inexplicably stopped working (0B recordings).

Can anyone pl confirm if they have a reliable S660 and Myth implementation? And the firmware, driver, Ubuntu and myth versions?

Or should I just buy a different tuner?

Thanks!
D2K

---

### Post by art2003 on 2013-02-13
Mine was stable but did not drive a rotor (diseqc 1.2)
Have you used it with a rotor?

---

### Post by dilbert2k on 2013-02-13
No rotor here.

---

### Post by art2003 on 2013-02-13
I would run dmesg |less

and see if there are any relevant errors...

---

