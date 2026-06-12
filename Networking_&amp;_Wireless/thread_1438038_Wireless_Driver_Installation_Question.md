---
title: "Wireless Driver Installation Question"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by billiusmaximus on 2010-03-24
I recently moved into a new apartment in which internet service is provided for the tenants and the wireless router is located in another apartment somewhere.

My concern is that once I begin fresh installing the newer releases of Ubuntu, how am I going to be able to get the appropriate wireless drivers? Previously, I could hardwire into the router temporarily to set up the wireless drivers.

So my question is: How can I install a wireless driver without the ability to hardwire into the router? Can I download a package and install the driver manually? Where can I go to get these packages?

Any assistance is much appreciated. Thank you.
Billy

---

### Post by chili555 on 2010-03-24
It depends entirely on the wireless card. I suggest you find out what you have and download anything you need and burn it to a CD so you will have it in any event.

Different cards use different drivers, downloadable, native and ndiswrapper.

---

### Post by billiusmaximus on 2010-03-24
Alright, but what "sorts of things" do I need? My Dell laptop has a Broadcom BCM4311, how can I get the firmware for this to put on another machine manually?

---

### Post by seenthelite on 2010-03-24
This may help

[Broadcom.com - 802.11 Linux STA driver]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by chili555 on 2010-03-25
> **billiusmaximus said:**
> Alright, but what "sorts of things" do I need? My Dell laptop has a Broadcom BCM4311, how can I get the firmware for this to put on another machine manually?The firmware, if you have installed it and your Broadcom is working correctly, is located in /lib/firmware/b43 or maybe some nearby places. Simply open a terminal and create a folder in your home directory:```
mkdir b43
```Now copy over everything in the /lib/firmware/b43 directory:```
sudo cp /lib/firmware/b43/* b43
```Now you can burn it to a CD and keep it forever. 

In a new computer, you can:```
mkdir b43
```Then drag and drop the firmware to the new folder named b43. Next copy it all over:```
sudo cp b43/* /lib/firmware/b43
```Make sure the copied over firmware is readable and writable as needed and owned by root:```
sudo chmod 644 /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43/*
```You can check which firmware is needed with:```
dmesg | grep b43
```Once you have this on a CD, you can repeat the process endlessly. It should only be needed in case of a reinstall.

---

### Post by dnd980 on 2010-03-25
I have a similar problem to this except i dont have a computer with a  working wifi driver is it possible to install the driver provided by  broadcom I have a similar broadcom card (the 432)

---

### Post by chili555 on 2010-03-25
Probably. Run the dmesg command and see what is missing. If you have the firmware on the other computer, just move it over; be sure to put it in the right directory and fix its owner and permissions. We will be interested in your report.

Your card may, or may not use the b43 driver.

---

### Post by dnd980 on 2010-03-25
> **chili555 said:**
> Probably. Run the dmesg command and see what is missing. If you have the firmware on the other computer, just move it over; be sure to put it in the right directory and fix its owner and permissions. We will be interested in your report.

Your card may, or may not use the b43 driver.
is there a trick to have it just show the networking information since I got about 23 pages of stuff and thats with it cropping the first part

---

### Post by chili555 on 2010-03-25
I was referring to this:> You can check which firmware is needed with:
```
dmesg | grep b43

```
Sorry if you misunderstood.

---

### Post by dnd980 on 2010-03-25
> **chili555 said:**
> I was referring to this:Sorry if you misunderstood.
sorry about that 
i just get this which doesnt mean much to me 
       1.016265] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  [    1.016276] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64

---

### Post by chili555 on 2010-03-25
Is the Broadcom up and running? It's not complaining about missing firmware. What does this tell us?```
ls /lib/firmware/b43
```

---

### Post by dnd980 on 2010-03-25
the first time i did it it just gave me this in green 

/lib/firmware/b43
so i tried it a 2nd time and i got this 

  bash: /lib/firmware/b43: cannot execute binary file

---

### Post by chili555 on 2010-03-25
```
[COLOR="Red"]ls[/COLOR] /lib/firmware/b43
```That *ls *up there means 'list the contents.' Please try again.

---

### Post by dnd980 on 2010-03-25
thats for your help but I copied and pasted it from the post and it was  the same as last time 

    david@dnd:~$ ls /lib/firmware/b43
  /lib/firmware/b43

---

### Post by chili555 on 2010-03-25
So no firmware is in there. So you need to get it. Does it have a working ethernet connection? Can you activate it under System > Administration > Hardware Drivers?

---

### Post by dnd980 on 2010-03-25
no internet other than wifi and there is nothing listed there

---

### Post by chili555 on 2010-03-25
[http://ubuntu.cafuego.net/pool/jaunty-cafuego/broadcom/b43-firmware_1.1-0cafuego1.tar.gz](http://ubuntu.cafuego.net/pool/jaunty-cafuego/broadcom/b43-firmware_1.1-0cafuego1.tar.gz)

Grab that package on a USB key, select Extract Here and move it into /lib/firmware/b43 as shown above.

sudo cp b43-firmware-1.1/firmware/b43/*  /lib/firmware/b43

---

### Post by dnd980 on 2010-03-25
im getting it cant find the directory since it doesnt exist but I made the b43 file Its in the home file so I just want to make sure thats right but i did extract that file there 
if its to messed up its not the biggest deal but thanks for the help

---

### Post by chili555 on 2010-03-25
Sounds correct. What does it look like?```
ls /lib/firmware/b43
```

---

### Post by dnd980 on 2010-03-25
still getting the same thing as before
  /lib/firmware/b43

---

### Post by chili555 on 2010-03-25
Then you didn't move the firmware files there correctly. Can you try again?

---

### Post by dnd980 on 2010-03-25
it may not be right but I copied what I did in the terminal but the firmware is in the b43 file I made in my home directory using the command on the the first page
   david@dave:~$ sudo cp b43-firmware-1.1/firmware/b43/* /lib/firmware/b43
  cp: cannot stat `b43-firmware-1.1/firmware/b43/*': No such file or directory
  david@dave:~$ sudo cp b43/b43-firmware-1.1/firmware/b43/* /lib/firmware/b43
  cp: target `/lib/firmware/b43' is not a directory

---

### Post by chili555 on 2010-03-26
> cp: target `/lib/firmware/b43' is not a directory Let's fix that:```
sudo rm -f /lib/firmware/b43
sudo mkdir /lib/firmware/b43
```

> cp: cannot stat `b43-firmware-1.1/firmware/b43/*': No such file or directoryThen the file you downloaded and extracted must not be in your home directory. Where is it? On your desktop? If so, the command would be:```
cd Desktop
sudo cp b43-firmware-1.1/firmware/b43/* /lib/firmware/b43
```Figure out where the file actually is and change directory to that location and proceed. If it is in a folder you created called 'b43' then do:```
cd b43
sudo cp b43-firmware-1.1/firmware/b43/* /lib/firmware/b43
```

---

### Post by dnd980 on 2010-03-26
I think its going somewhere 
   david@dave:~$ sudo rm -f /lib/firmware/b43
    david@dave:~$ sudo mkdir /lib/firmware/b43
  david@dave:~$ cd b43
  david@dave:~/b43$ sudo cp b43-firmware-1.1/firmware/b43/* /lib/firmware/b43
  david@dave:~/b43$ sudo chmod 644 /lib/firmware/b43/*
  david@dave:~/b43$ sudo chown root:root /lib/firmware/b43/*
  david@dave:~/b43$ dmesg | grep b43
  [    1.020367] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  [    1.020375] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
and still no connection but when I typed this in again I got something back

  
   david@dave:~$ ls /lib/firmware/b43
  a0g0bsinitvals4.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  pcm5.fw
  a0g0bsinitvals5.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  ucode11.fw
  a0g0bsinitvals9.fw   b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode13.fw
  a0g0initvals4.fw     b0g0bsinitvals4.fw   lp0initvals13.fw    ucode14.fw
  a0g0initvals5.fw     b0g0bsinitvals5.fw   lp0initvals14.fw    ucode15.fw
  a0g0initvals9.fw     b0g0bsinitvals9.fw   lp0initvals15.fw    ucode4.fw
  a0g1bsinitvals13.fw  b0g0initvals13.fw    n0absinitvals11.fw  ucode5.fw
  a0g1bsinitvals5.fw   b0g0initvals4.fw     n0bsinitvals11.fw   ucode9.fw
  a0g1bsinitvals9.fw   b0g0initvals5.fw     n0initvals11.fw
  a0g1initvals13.fw    b0g0initvals9.fw     pcm4.fw

just for future reference what does the sudo cd actually do since it looks pretty useful

---

### Post by chili555 on 2010-03-26
Do you mean 'sudo cp?' It means copy and since the file is owned by root and not dave, you need administrative priveleges, or 'sudo.'

Have you rebooted with the ethernet cable detached?

---

### Post by billiusmaximus on 2010-03-26
> **chili555 said:**
> The firmware, if you have installed it and your Broadcom is working correctly, is located in /lib/firmware/b43 or maybe some nearby places. Simply open a terminal and create a folder in your home directory:```
mkdir b43
```Now copy over everything in the /lib/firmware/b43 directory:```
sudo cp /lib/firmware/b43/* b43
```Now you can burn it to a CD and keep it forever. 

In a new computer, you can:```
mkdir b43
```Then drag and drop the firmware to the new folder named b43. Next copy it all over:```
sudo cp b43/* /lib/firmware/b43
```Make sure the copied over firmware is readable and writable as needed and owned by root:```
sudo chmod 644 /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43/*
```You can check which firmware is needed with:```
dmesg | grep b43
```Once you have this on a CD, you can repeat the process endlessly. It should only be needed in case of a reinstall.

Thank you this is very helpful, however, I do not have a b43 directory inside the /lib/firmware directory. I did an ls on the /lib/firmware directory and here are the results:

2.6.28-11-generic                   dvb-usb-wt220u-fc03.fw
2.6.28-17-generic                   dvb-usb-wt220u-zl0353-01.fw
2.6.28-18-generic                   ipw2100-1.3.fw
acx                                 ipw2100-1.3-i.fw
aic94xx-seq.fw                      ipw2100-1.3-p.fw
atmel_at76c502_3com.bin             ipw2200-bss.fw
atmel_at76c502_3com-wpa.bin         ipw2200-ibss.fw
atmel_at76c502.bin                  ipw2200-sniffer.fw
atmel_at76c502d.bin                 isl3877
atmel_at76c502d-wpa.bin             isl3886
atmel_at76c502e.bin                 isl3887usb_bare
atmel_at76c502e-wpa.bin             isl3890
atmel_at76c502-wpa.bin              isl3890usb
atmel_at76c503-i3861.bin            iwlwifi-3945-1.ucode
atmel_at76c503-i3863.bin            iwlwifi-3945-2.ucode
atmel_at76c503-rfmd-0.90.2-140.bin  iwlwifi-4965-1.ucode
atmel_at76c503-rfmd-acc.bin         iwlwifi-4965-2.ucode
atmel_at76c503-rfmd.bin             iwlwifi-5000-1.ucode
atmel_at76c504_2958-wpa.bin         lbtf_usb.bin
atmel_at76c504a_2958-wpa.bin        NPE-B
atmel_at76c504.bin                  NPE-B.01020201
atmel_at76c504c-wpa.bin             NPE-C
atmel_at76c505a-rfmd2958.bin        NPE-C.02020201
atmel_at76c505-rfmd2958.bin         ql2100_fw.bin
atmel_at76c505-rfmd.bin             ql2200_fw.bin
atmel_at76c506.bin                  ql2300_fw.bin
atmel_at76c506-wpa.bin              ql2322_fw.bin
BCM2033-FW.BIN                      ql2400_fw.bin
BCM2033-MD.BIN                      rt2561.bin
dvb-fe-cx24116.fw                   rt2561s.bin
dvb-fe-or51132-qam.fw               rt2661.bin
dvb-fe-or51132-vsb.fw               rt2860.bin
dvb-fe-or51211.fw                   rt2870.bin
dvb-fe-tda10046.fw                  rt73.bin
dvb-ttpci-01.fw                     v4l-cx23418-apu.fw
dvb-usb-af9015.fw                   v4l-cx23418-cpu.fw
dvb-usb-avertv-a800-02.fw           v4l-cx23418-dig.fw
dvb-usb-bluebird-01.fw              v4l-cx2341x-dec.fw
dvb-usb-dib0700-1.10.fw             v4l-cx2341x-enc.fw
dvb-usb-dib0700-1.20.fw             v4l-cx2341x-init.mpg
dvb-usb-dibusb-5.0.0.11.fw          v4l-cx23885-avcore-01.fw
dvb-usb-dibusb-6.0.0.8.fw           v4l-cx23885-enc.fw
dvb-usb-dtt200u-01.fw               v4l-cx25840.fw
dvb-usb-tvwalkert.fw                v4l-pvrusb2-24xxx-01.fw
dvb-usb-umt-010-02.fw               v4l-pvrusb2-29xxx-01.fw
dvb-usb-vp702x-01.fw                zd1201-ap.fw
dvb-usb-vp7045-01.fw                zd1201.fw
dvb-usb-wt220u-02.fw                zd1211

Thanks again,
Billy

---

### Post by chili555 on 2010-03-26
Billy-

Which driver is your Broadcom using? Find out with:```
lsmod | grep -e b43 -e wl
sudo lshw -C network
```

---

### Post by billiusmaximus on 2010-03-26
Here is the output of those two commands. Don't know what most of it means.

billius@billius-laptop:~$ lsmod | grep -e b43 -e wl
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
billius@billius-laptop:~$ sudo lshw -C network
[sudo] password for billius: 
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:85:f7:c1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:d6:b7:e9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:8b:51:93:02:dd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Thanks,
Billy

---

### Post by chili555 on 2010-03-26
Ah! Your wireless uses the module* wl*.> [COLOR="Red"]wl[/COLOR] 1281364 0
ieee80211_crypt 13444 2 ieee80211_crypt_tkip,[COLOR="Red"]wl[/COLOR]It is installed with bcmwl-kernel-source. Let me work out how we might put it and its dependencies on a CD. Back later.

---

### Post by billiusmaximus on 2010-03-29
Thanks, I really appreciate it.

Billy

---

### Post by chili555 on 2010-03-29
Sorry for the delay. You are in luck. The package needed to install the module *wl* is on the install CD. If you have now, or download a fresh copy of the CD, then all you have to do is open System > Administration > Synaptic and drop the CD in the tray. Search for bcmwl-kernel-source and install it.

Then load the needed module:```
sudo modprobe wl
```Your wireless should then be operational.

---

### Post by bkratz on 2010-03-29
Sorry, but don't forget to go to synaptic then settings then repositories and check the box next to " installable from cd rom!" or it won't try there.

---

### Post by billiusmaximus on 2010-03-31
Thank you very much. If you dont mind my asking, how did you find this information out?

One of my roommates is considering loading her netbook with Ubuntu as well as my other roommate is buying a new computer in the next month and he loves using Ubuntu on my laptop.

Thanks, I am trying to learn how to do this diagnosing on my own. :/

Billy

P.S. - I have a bootable USB drive and I don't suppose it is possible to make Synaptic install the drivers from that? I tried it just now and it seems to want a cd rom.

---

### Post by chili555 on 2010-03-31
> If you dont mind my asking, how did you find this information out?Many years of experience, some Googling and on one computer or another around the house has about every downloadable driver  on it that there is. Before I answer a post, I like to know that the procedure is sound because I just executed it on my own machine.> I have a bootable USB drive and I don't suppose it is possible to make Synaptic install the drivers from that? I tried it just now and it seems to want a cd rom. I have never tried, but I doubt it.

---

### Post by billiusmaximus on 2010-04-30
> **chili555 said:**
> The firmware, if you have installed it and your Broadcom is working correctly, is located in /lib/firmware/b43 or maybe some nearby places. Simply open a terminal and create a folder in your home directory:```
mkdir b43
```Now copy over everything in the /lib/firmware/b43 directory:```
sudo cp /lib/firmware/b43/* b43
```Now you can burn it to a CD and keep it forever. 

In a new computer, you can:```
mkdir b43
```Then drag and drop the firmware to the new folder named b43. Next copy it all over:```
sudo cp b43/* /lib/firmware/b43
```Make sure the copied over firmware is readable and writable as needed and owned by root:```
sudo chmod 644 /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43/*
```You can check which firmware is needed with:```
dmesg | grep b43
```Once you have this on a CD, you can repeat the process endlessly. It should only be needed in case of a reinstall.

Hi,

I followed this procedure yesterday and it appears to almost have worked. But when I click the pull down menu at the top right, it says "device not ready" and can't detect any wireless networks.

Can anyone provide some help?

Thanks,
Billius

---

### Post by chili555 on 2010-04-30
Did you reboot? What does this tell us?```
dmesg | grep b43
```

---

### Post by billiusmaximus on 2010-05-01
Here is my output:

billius@billius-desktop:~$ dmesg | grep b43
[    1.022295] b43-pci-bridge 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.757959] b43legacy-phy0: Broadcom 4306 WLAN found
[    8.785049] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[    8.785074] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[    8.809051] b43legacy-phy0 debug: Radio initialized
[    9.393034] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[    9.402211] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[    9.402243] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[    9.754272] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[    9.762421] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[    9.762427] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

Interesting, looks like I should check out the url...

Thanks,
Billius

---

### Post by billiusmaximus on 2010-05-01
Hello again,

I am tagging on to my last post, my firmware is stored in the directory:

/lib/firmware/b43

But looking at this output, it appears to be looking for the firmware in:

/lib/firmware/b43legacy

Maybe I just need to change the directory?

Billius

---

### Post by chili555 on 2010-05-01
> Maybe I just need to change the directory?Sure. Simply do:```
sudo cp /lib/firmware/b43/* /lib/firmware/b43legacy
```

---

### Post by billiusmaximus on 2010-05-01
Hi,

Just did it, and it still didn't change anything. The output of dmesg is still the same.

Billius

---

### Post by chili555 on 2010-05-01
Please try a reboot.

---

### Post by billiusmaximus on 2010-05-01
A reboot didn't work, however I seriously lucked out.

I am running Ubuntu 9.04 on my laptop and so I installed fw-cutter, ran it, and then took the b43 and b43legacy directory from the laptop and put both on the desktop. Made sure the file permissions/ownership was correct, and after I rebooted, wireless is working.

Not sure why it works as I am pretty sure my laptop does not have the exact same wireless adapter.

Thanks,
Billius

---

### Post by ldjinthevillages on 2010-05-02
bcm4311 
Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Very simple once you find it!

---

### Post by fstopharmony on 2010-11-03
Hey! I just installed ubuntu netbook 10.10 onto my Dell Insprion mini 10. Everything went flawless until I went to connect to a wireless network. As others have posted it says "missing firmware". 
 
I found a site that had the "b43" and "b43legacy" folders with files and everything available for download. I have them saved into my home folder however I'm unable to copy them into the /lib/firmware/ folder. 
 
I keep getting a message saying that I do not have permission to perform that action. I'm the only user/administrator on the computer so I'm confused how I don't have permission to do this. 
 
I can see that the original "b43" and "b43legacy" folders have little X's in the corners of them. What does that mean and why am I unable to copy the new ones to that folder?
 
PLEASE HELP!! Thanks!

---

### Post by chili555 on 2010-11-03
Sometimes, only the geeky command line will do the job quickly, easily and without fuss.> I'm the only user/administrator on the computer so I'm confused how I don't have permission to do this. Ubuntu doesn't allow, unless you do some serious hacking, users to log in as root. It's one of Linux' strengths. Passing viruses and malware can't automatically install because they don't have root privileges or permission. We gain permission temporarily with the command *sudo*.

Please open Applications > Accessories > Terminal and we will create the needed directories in /lib/firmware:```
sudo mkdir /lib/firmware/b43
sudo mkdir /lib/firmware/b43legacy
```Now, we will navigate to the folders on your desktop:```
cd Desktop/firmwarefolder/b43
```Substitute the name of the folder you actually have. Now, we will copy the actual firmware files to the directories we created:```
sudo cp * /lib/firmware/b43
```Now we move over to the b43legacy folder and do the same:```
cd ~/Desktop/firmwarefolder/b43legacy
sudo cp * /lib/firmware/b43legacy
```The wildcard * means copy everything. Now we give the firmware files the correct permission (!) and owner:```
sudo chown root:root /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43legacy/*
sudo chmod 644 /lib/firmware/b43/*
sudo chmod 644 /lib/firmware/b43legacy/*
```Now we unload and reload the driver and your wireless should come to life:```
sudo rmmod -f b43
sudo modprobe b43
```If it doesn't goes as smoothly as we hoped, please post back with:```
ls /lib/firmware/b43
```Thanks.

---

