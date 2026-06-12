---
title: "ATi HDTV Wonder"
date: 2008-09-18
forum: Mythbuntu
---

### Post by jlp_engineer on 2008-09-18
Hello,

I just obtained an ATi HDTV Wonder PCI card and I have installed it along side a PVR-150 tuner.  The PVR-150 works and I can get it to detect channels on my cable TV service just great.  The problem for the ATi HDTV Wonder seems to be that it is not setup correctly, as far as I can see.  This is probably something stupid on my part :confused:, and might be easy for someone to spot what I am doing wrong.  Mythbuntu 8.10 seems to detect the card under the V4L category...not the DVB, which some of the posts seem to indicate.  When I have it scan for channels, I get no channels detected, and there does not seem to be any digital frequency band selections available on the page in setup where you can scan for channels.  ](*,)

1 - Do I need to install the nxt-2004 firmware?  I have seen some posts indicating that you need to do this, but I have also seen some posts indicating that the support for this card should be built into the Mythbuntu 8.10 kernel.

2 - Does this card need to have a separate listing source to "see" the digital channels?

3 - Under what category should the card be detected?  Is it V4L for the analog tuner and DVB for the digital part?

Ideas?

---

### Post by blackoper on 2008-09-18
see my thread about it here:

[http://ubuntuforums.org/showthread.php?t=756800&highlight=ati+hdtv]("http://ubuntuforums.org/showthread.php?t=756800&highlight=ati+hdtv")

once you install the dvb-fe-nxt2004.fw file then follow the mythtv wiki entry here to get things up and running. You need to load the firmware at boot
[http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder]("http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder")

after you get the firmware moved to the kernel in /lib/firmware/"kernel whatever" you then need to go into /etc/modules.d/ and create a file call it whatever you want. I called mine ati_hdtv_wonder and then you need to add: saa7134-dvb  as the only line in there. After that is done edit /etc/modules file and add saa7134-dvb as a line and then reboot and you are golden

---

### Post by jlp_engineer on 2008-09-22
Well,

I am off into the world of Linux source code and firmware loading...

I just tried launching the "get_dvb_firmware" script to obtain the nxt2004 firmware file and I am getting the following error:

This firmware requires the unzip command - see [ftp://ftp.info-zip.org/pub/infozip/UnZip.html](ftp://ftp.info-zip.org/pub/infozip/UnZip.html)

Can anyone help me over this hurdle?

TIA!

---

### Post by paulg on 2008-09-26
If you haven't figured it out, you need to install a package for it.

```
aptitude install unzip
```

Actually, the package might be just plain ol' zip.

---

### Post by jlp_engineer on 2008-09-30
OK,

Thanks for the package "solution" to this problem.  I figured that out for myself after looking at the script that grabbed the firmware files I needed.  I used the Synaptic Package Manager to install Unzip, and everything works now as it was intended to.

I have a new problem.  I cannot seem to tune any channels with the ATi HDTV Wonder - at all.  I have followed the instructions on the MythTV Wiki for the HDTV Wonder, to no avail.  I am hoping that I have simply missed something, but to tell the truth, the instructions are just vague enough, that simple errors could have come in.  

Blackoper - you said to go into /etc/modules.d/ and create a file, but I have no directory called /etc/modules.d/.  I only have one called /etc/modprobe.d/.  Are you referring to the file in the /etc/ folder called "modules"?  If so, I have modified this file to load the cx88-dvb module and the dvb-pll module and rebooted the system.  I have checked the dmesg output and the modules and firmware files seem to be loading and the card is being recognized and a tuner is being registered. 

I have gone through Myth setup and have selected the card type as "DVB DTV Capture card (v3.x)", exactly as the Wiki entry suggested, although the Frontend ID and Subtype do not indicate the HDTV Wonder.  In the Video sources section, I have setup my cable providers channel selection, including all the digital channels.  I am not sure how important this is in the actual operation of the card - I suspect it is only for the listings.  If my selections on Schedules Direct shows normal cable channels, or normal channels plus digital, I assume I have to pick the one with normal plus digital, and only that one.  For example, SD will allow me to have the standard cable channel lineup AND the lineup that includes the standard and digital channels.  Which is correct?

OK, for the input selection, I have DVB:0 (Television) pointing to my Schedules Direct CableONE channels, but when I tell Myth to "Scan for channels" on the "Connect source to input" setup screen, I get only a blank screen.  The screen I get when I scan for channels on the PVR-150 source setup screen shows a progress bar, signal strength, etc.  I get nothing with the ATi card, so I cannot tell if it is even working.  ](*,)

I noticed during the capture card setup, that the ATi card shows up under a "Card Type" of Analog V4L capture card selection with a probed info of "ATI HDTV Wonder [cx8800]".  Is this the analog tuner portion of the card?  Do I need to set this up if I want it to tune analog channels?  Should this be setup as a separate tuner in order for the digital tuner to work?  ](*,):???:

Oh yeah, I have also read in the Myth Wiki for the ATi card that I need to modify or setup the kernel.  Do I still need to do that in order for the card to work?  I am running Mythbuntu 8.10, so perhaps this step is no longer necessary, as the wiki shows what to do for 7.10 or earlier.  Perhaps I will update them when and if I solve this problem I have.:cry:

Help!

---

### Post by pierreski on 2008-10-10
Hi all,

I've just installed a fresh copy of Ubuntu 8.04 on my media box equipped with a ATI HDTV Wonder pci card. I've followed all the instructions (except customizing kernel configuration) in the mythtv wiki ([http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)). I made sure to copy the dvb-fe-nxt2004.fw file to the proper /lib/firmware/[my kernel version] directory.

"dmesg|grep nxt" gives the following output:
```

[   69.522581] nxt200x: NXT2004 Detected
[ 1544.866155] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[ 1544.918999] nxt2004: Waiting for firmware upload(2)...
[ 1546.380348] nxt2004: Firmware upload complete

```

but when I run the "scan atsc/us-Cable-Standard-center-frequencies-QAM256" command from the /usr/share/doc/dvb-utils/examples/scan directory, I get the following output:

```

scanning atsc/us-Cable-Standard-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 57000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!

...(several tuning attempts all fail)...

>>> tune to: 69000000:QAM_256
ERROR: interrupted by SIGINT, dumping partial result...
dumping lists (0 services)
Done.

```

Anyone have any suggestions for fixing this? Do I need to modify the kernel as mentioned in the wiki? Do I need to add a module at startup? If so, how would I do that? Thanks in advance!

---

### Post by newlinux on 2008-10-10
@pierriski:

Are you sure unencrypted QAM channels are available in your area?

@jlp_engineer?

So you get a blank screen when you go the screen to select your scan settings or after you have setup your scan settings (setup the frequency type, range of scan, etc.) and initiate the scan? What does the terminal output from mythtv-setup say when you do this?  And you are configuring the DVB card, not the V4L side of it right?

the v4L is the analog side, but you don't have to set it up to get the digital side to scan to work.

What kernels are you running? The wiki says:

Warning: Kernel's 2.6.20 to 2.6.20.3 (tested) are broken. Kernel 2.6.21.x and above are fixed.

---

### Post by pierreski on 2008-10-10
I spoke a little too early. Apparently, the errors I got while scanning were completely normal!

I let the scan finish completely and found all my local channels. I added "> channels.conf" to my scan command so the channels found would be saved. I then found the latest version Me-TV and enjoyed some great HDTV :popcorn:

---

### Post by angryswede on 2008-10-12
I am trying to get the analog portion of this tuner working using v4l.  I am running the cable through a motorola STB box.  The channel scan will pick up channels 3 and 4; however, when I tune to them all I get is a blank screen.  Anyone had any success with this or any links to instructions to get this working?

---

### Post by pierreski on 2008-11-03
:KS Quick update for ATI HDTV Wonder Users:

*In (K,X,Myth) Ubuntu 8.10 (Intrepid), the ATI HDTV Wonder card is installed using instructions from this site: [http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder) . No kernel changes are necessary

*In order to create the channels configuration file needed for almost every DVB application, use the following command (Note that several errors like "transponder failed to tune to channel" will occur during this process):
```
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > channels.conf
```

*Install mplayer or xine. Copy the channels.conf file to the .mplayer or .xine folder in your home directory, and try watching DVB on either program. Enjoy the HDTV!

---

### Post by Grandma_DOG on 2008-12-21
That all sounds great, but your scan code doesn't work out of the box.  Is it a package of some kind?  How to run "scan xxx..."?

> **pierreski said:**
> :KS Quick update for ATI HDTV Wonder Users:

*In (K,X,Myth) Ubuntu 8.10 (Intrepid), the ATI HDTV Wonder card is installed using instructions from this site: [http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder) . No kernel changes are necessary

*In order to create the channels configuration file needed for almost every DVB application, use the following command (Note that several errors like "transponder failed to tune to channel" will occur during this process):
```
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > channels.conf
```

*Install mplayer or xine. Copy the channels.conf file to the .mplayer or .xine folder in your home directory, and try watching DVB on either program. Enjoy the HDTV!

---

### Post by newlinux on 2008-12-21
I think you have to install the dvb-utils package
```

sudo apt-get install dvb-utils

```

---

### Post by xmrkite on 2009-01-12
I recently tried the get the same card working under ubuntu 8.10 (intrepid ibex), however it did not work. It would not scan the digital channels properly.

I then followed these instructions and it now works:

> 

Excerpt from this page: [http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)

The digital portion of the card will appear to be working by default upon booting (without loading any drivers/firmware), however channel scanning will not work. Though the digital channels will lock you will receive "timeout errors" and "no tables" errors from within mythtv. You must download and install the firmware as stated below under the "Loading the Firmware" section for Ubuntu 7.04. After that you can either reboot or run the following commands:

sudo modprobe -r cx88-dvb   #This will unload the drivers module
sudo modprobe cx88-dvb      #This will reload the drivers module but this time using the new firmware


I hope this helps anyone else out there who is having problems. My card works great and get's great hdtv reception.

---

### Post by mjklam on 2009-02-03
I am completely new to Ubuntu and Linux. I have a ATI HDTV wonder tuner card. I have been trying to make this work with my Mythbuntu and also my Ubuntu desktop. I am stuck on this step "Go to this site and copy the script and paste it into a file named "get_dvb_firmware" I pasted the script in the file and where should I put this file in. I have tried putting it in cd /usr/share/doc/dvb. It would not let me. I need a better instructions since my knowledge is not that advanced. Should I give up and try to find a turner card that does not require this complex process.

---

### Post by xmrkite on 2009-02-03
To be honest with you, the page with that script is a little cumbersome. So go to this url: [http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmware](http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmware) and click on the link at the very top right that says "hide line numbers".

Then copy all the text in that gray area and save it to a file called get_dvb_firmware in the /usr/share/doc/dvb directory. You may need to create that directory if it doesnt already exist on your system.

The get the firmware by running these commands:
cd /usr/share/doc/dvb
sudo chmod +x ./get_dvb_firmware
sudo ./get_dvb_firmware nxt2004
sudo cp ./dvb-fe-nxt2004.fw /lib/firmware

Then reboot, and run these two commands:

sudo modprobe -r cx88-dvb
sudo modprobe cx88-dvb

Try rebooting again just to be safe, then you should be able to scan for channels. I was actually surprised how quickly i got this working because I usually run into every problem in the book with linux. Let me know if it works or not.

---

### Post by mjklam on 2009-02-03
> **xmrkite said:**
> To be honest with you, the page with that script is a little cumbersome. So go to this url: [http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmware](http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmware) and click on the link at the very top right that says "hide line numbers".

Then copy all the text in that gray area and save it to a file called get_dvb_firmware in the /usr/share/doc/dvb directory. You may need to create that directory if it doesnt already exist on your system.

The get the firmware by running these commands:
cd /usr/share/doc/dvb
sudo chmod +x ./get_dvb_firmware
sudo ./get_dvb_firmware nxt2004
sudo cp ./dvb-fe-nxt2004.fw /lib/firmware

Then reboot, and run these two commands:

sudo modprobe -r cx88-dvb
sudo modprobe cx88-dvb

Try rebooting again just to be safe, then you should be able to scan for channels. I was actually surprised how quickly i got this working because I usually run into every problem in the book with linux. Let me know if it works or not.


Thanks, I'm hoping to solve this soon.

I already created the directory /usr/share/doc/dvb using the terminal program. 

I did the first part with hiding the numbers. I paste the script in the Text Editor. I tried saving the text file directly to that directory from the Text Editor which didn't work.  I saved this file on my desktop. I set it to allow executing file as program. I tried moving it to /usr/share/doc/dvb that I created. I was not able to. It says error while moving "get_dvb_firmware. Error moving file:permission denied. 

 I am not sure if I am doing it right.

---

### Post by newlinux on 2009-02-03
You can get the firmware directly from the ubuntu repos. Try the following:

```

sudo apt-get install linux-source
cd /usr/src
sudo tar xvjf linux-source-[INSERT YOUR KERNEL VERSION HERE].tar.bz2
cd linux-source-[INSERT KERNEL VERSION]/Documentation/dvb
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/

```

e.g. I'm running kernel 2.6.24 in hardy, so for kernel 2.6.24

```

sudo apt-get install linux-source
cd /usr/src
sudo tar xvjf linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/Documentation/dvb
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/
```

Then reboot and load the module as indicated above
```

sudo modprobe cx88-dvb
```

---

### Post by mjklam on 2009-02-03
after typing in uname -r

it shows that I have Kernel 2.6.27 -11-generic

I am going to try this tomorrow after work which is another long day with windows XP! It is exciting trying a new OS software like Ubuntu. If I get this to work, it would be neat to build Mythtvbuntu PVR!

---

### Post by newlinux on 2009-02-04
Good luck.. also, as mentioned above, instead of rebooting after running those commands you could just:
```

sudo modprobe -r cx88-dvb
sudo modprobe cx88-dvb

```

Let us know how it goes.

if you have problems after this run the following commands and paste the results:
```

dmesg | grep nxt2004
dmesg | grep adapter

```

---

### Post by mjklam on 2009-02-05
Thanks, the commands you gave me worked perfectly. It picked up the firmware and the channel scanner functions as it is supposed to! I was able to pick up several DTV channels through antenna. I don't have cable so I couldn't try the the analog cable part. 

The TV playback is not steady. It is some hardware problem. I think this card does not have on board encoding. The encoding is done in the computer resulting not steady playback. I noticed it is steady when I land on a SD channel. I am running on Athlon XP 2600 processor. It could be the constant writing in HD to the harddrive causing not steady playback. It is neat that I could rewind any time.  I am using an older hard drive. I didn't want to write over the computer's primary hard drive.   

It is time to look for bargains on newer hardware for this computer.

---

### Post by newlinux on 2009-02-05
I'm glad you got it working. Digital signals are already encoded and are just captured by the tuner so they don't need encoding. The problem you are having is that your CPU/video card don't have enough beef to properly decode an HD signal. I had a p4 2.6Ghz/Geforce MX440 that just barely was able to do it (1080i/720p mpeg-2). Anything less than that will probably struggle and require other processes running concurrently to be at a minimum. I think your XP 2600 may be just a little too weak on its own.


What kind of video card do you have? If you have a nvidia card, XvMC (which allows for your video card to help out much more with mpeg-2 recordings) has a good chance of allowing your system to playback HD mpeg-2 content. Otherwise, you probably will need new hardware. 

For new hardware, if you are on a budget, you could look into a VDPAU compatible video card from nvidia. One of those would allow you playback HD (mpeg-2, VC-1, h.264) content back. You would need to use a patched version of myth for myth to take advantage of it (binary packages for this are available, so you wouldn't need to install your own), and a patched version of mplayer - but that would be the cheapest option if XvMC doesn't do it for you.

For more info:

XVMC: [http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

VDPAU: [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)


IF you need help implementing XvMC or VDPAU just let us know.

---

### Post by molder on 2009-02-19
> **newlinux said:**
> Good luck.. also, as mentioned above, instead of rebooting after running those commands you could just:
```

sudo modprobe -r cx88-dvb
sudo modprobe cx88-dvb

```

Let us know how it goes.

if you have problems after this run the following commands and paste the results:
```

dmesg | grep nxt2004
dmesg | grep adapter

```

I am still having problems.  I have no idea what to do next.  I have recompiled my kernel.  Updated my firmware.  Still no luck.
  
```
andrew@MythTV-Molder:~$ sudo modprobe -r cx88-dvb
[sudo] password for andrew: 
andrew@MythTV-Molder:~$ sudo modprobe cx88-dvb
andrew@MythTV-Molder:~$ dmesg | grep nxt2004
[  408.539442] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[  408.539468] firmware: requesting dvb-fe-nxt2004.fw
[  408.598213] nxt2004: Waiting for firmware upload(2)...
[  410.019527] nxt2004: Firmware upload complete
andrew@MythTV-Molder:~$ dmesg | grep adapter
[   16.395029] DVB: registering new adapter (cx88[0])
[  788.667137] DVB: registering new adapter (cx88[0])
andrew@MythTV-Molder:~$ 

```

---

### Post by newlinux on 2009-02-19
> **molder said:**
> I am still having problems.  I have no idea what to do next.  I have recompiled my kernel.  Updated my firmware.  Still no luck.
  
```
andrew@MythTV-Molder:~$ sudo modprobe -r cx88-dvb
[sudo] password for andrew: 
andrew@MythTV-Molder:~$ sudo modprobe cx88-dvb
andrew@MythTV-Molder:~$ dmesg | grep nxt2004
[  408.539442] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[  408.539468] firmware: requesting dvb-fe-nxt2004.fw
[  408.598213] nxt2004: Waiting for firmware upload(2)...
[  410.019527] nxt2004: Firmware upload complete
andrew@MythTV-Molder:~$ dmesg | grep adapter
[   16.395029] DVB: registering new adapter (cx88[0])
[  788.667137] DVB: registering new adapter (cx88[0])
andrew@MythTV-Molder:~$ 

```

It would help if you told us what problems you are having, and how you have configured myth...

---

### Post by molder on 2009-02-23
I seam to have MythTV finally configured, ALSA updated, and the newest ATI Catalyst drivers installed.  I can not get sound through my HDMI port connected to a Panasonic plasma TV.  Also if and when I do get a signal lock with my tuner, there are two videos stacked on top of each other and static.  Also, is it possible to access other DLNA servers on the network through MythTV?> **newlinux said:**
> It would help if you told us what problems you are having, and how you have configured myth...

---

### Post by Astrogeek on 2009-02-23
Hello All.

I'm struggling with this card as well. Right now I'm running Intrepid with kernel 2.6.27. I had myth installed but had no luck getting the card to respond to channel scans. Eventually I unistalled myth and have been trying to get it to work with movie player and xine. So far no luck. Here are my dmesg results:

Code:

```
eric@greatblue:~$ dmesg | grep nxt2004
[   33.461075] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   33.461082] firmware: requesting dvb-fe-nxt2004.fw
[   33.581171] nxt2004: Waiting for firmware upload(2)...
[   34.619194] nxt2004: Firmware upload complete
eric@greatblue:~$ dmesg | grep adapter
[   16.698409] DVB: registering new adapter (cx88[0])


```

Also, when I sudo modprobe -r cx88-dvb I get this:


```
eric@greatblue:~$ sudo modprobe -r cx88-dvb
FATAL: Module cx88_dvb is in use.


```

Which I believe means that I already have the driver running. Is that correct?

When I try to scan for channels I get this:


```
eric@greatblue:~$ scan atsc/usscan /usr/share/doc/dvb-utils/examples/scan/atsc  /us-ATSC-center-frequencies-8VSB > channels.conf
scanning atsc/usscan
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or   resource busy


```

Xine tells me that there's no dvb device found, and movie player says that it can't find the channels.conf file. Myth wasn't able to pick up anything other than the occassional blank screen. 

Any tips would be great!

Thanks.

Eric

---

### Post by newlinux on 2009-02-24
> **molder said:**
> I seam to have MythTV finally configured, ALSA updated, and the newest ATI Catalyst drivers installed.  I can not get sound through my HDMI port connected to a Panasonic plasma TV.  Also if and when I do get a signal lock with my tuner, there are two videos stacked on top of each other and static.  Also, is it possible to access other DLNA servers on the network through MythTV?


It sounds like your problems are more playback issues. You might (if you haven't already) want to start a thread  around your double image problem. ATI graphics is known to be problematic in Linux, and even more so in Linux.

As for your signal locks, have you tried scanning outside of myth using the scan utility? Also double check your RF connections. some cards and scanning software are more fickle than others.

Mythfrontend does not act as a generic UPnP client, so it won't pick up other DLNA servers...

---

### Post by newlinux on 2009-02-24
> **Astrogeek said:**
> Hello All.

I'm struggling with this card as well. Right now I'm running Intrepid with kernel 2.6.27. I had myth installed but had no luck getting the card to respond to channel scans. Eventually I unistalled myth and have been trying to get it to work with movie player and xine. So far no luck. Here are my dmesg results:

Code:

```
eric@greatblue:~$ dmesg | grep nxt2004
[   33.461075] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   33.461082] firmware: requesting dvb-fe-nxt2004.fw
[   33.581171] nxt2004: Waiting for firmware upload(2)...
[   34.619194] nxt2004: Firmware upload complete
eric@greatblue:~$ dmesg | grep adapter
[   16.698409] DVB: registering new adapter (cx88[0])


```

Also, when I sudo modprobe -r cx88-dvb I get this:


```
eric@greatblue:~$ sudo modprobe -r cx88-dvb
FATAL: Module cx88_dvb is in use.


```

Which I believe means that I already have the driver running. Is that correct?

When I try to scan for channels I get this:


```
eric@greatblue:~$ scan atsc/usscan /usr/share/doc/dvb-utils/examples/scan/atsc  /us-ATSC-center-frequencies-8VSB > channels.conf
scanning atsc/usscan
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or   resource busy


```

Xine tells me that there's no dvb device found, and movie player says that it can't find the channels.conf file. Myth wasn't able to pick up anything other than the occassional blank screen. 

Any tips would be great!

Thanks.

Eric

Looks like everything is installed fine, but you are having some module problems. Reboot, and check to see if the module is loaded. IF it isn't load it. Your unloading of the module looks like it partially failed, probably leaving your DVB device in a weird state. IF after you reboot 

```
dmesg | grep adapter
```

gives you an initiliazed cx88 dvb device, that module is loaded. (you can also do ```
lsmod | grep cx88
```)


Your scan command has too many spaces in it. It looks like it truncated the filename with the values to scan. If you are scanning for OTA ATSC channels the command should be:
```

scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf
```

if you want to use mplayer to step through the channels. After that scan has completed (it will take a while)

You can do ```
mplayer dvb://
```

and use the h and k keys to step up and down through the stations the scan found. It will close and open mplayer after each step.

---

### Post by Astrogeek on 2009-02-24
> IF after you reboot 

```
dmesg | grep adapter
```

gives you an initiliazed cx88 dvb device, ...


So what I'm seeing here is this 
```
 eric@greatblue:~$ dmesg | grep adapter
[   17.540244] DVB: registering new adapter (cx88[0])

```

I'm not sure that this tells me that it's initialized or not. "Registering" to me looks like it's initializing it when I run the command. Is that the case? 

Just for grins I ran the scan code you posted as well. It still gave me the "FATAL" error:
```
eric@greatblue:~$ scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
eric@greatblue:~$ 

```

I'm kinda stuck at this point. If it's not initializing correctly, how do I fix that? 

Thanks for the input newlinux, I appreciate it!

eric

---

### Post by newlinux on 2009-02-25
dmesg just reports what is happening, it doesn't actually do anything, so I believe you card is at least trying to be initialized, but some resource is conflicting with it. It should get registered and initialized when the module is loaded which dmesg (which is really just a log) tells us is happening. What does:

```

ls /dev/dvb/adapter*

```
return? I'm pretty sure you device is initialized because the error you are getting indicates it's there but something else is using it.

You said you uninstalled myth. Are you sure it is completely uninstalled? You will want to make sure mythbackend isn't running... when you do the scan.

just to be sure mythbackend isn't running, what does:

```

ps aux | grep myth

```
return? If mythbackend is running - that's probably what's causing the conflict if it is a conflict problem.

---

### Post by newlinux on 2009-02-25
I should add, if mythbackend is running you don't need to uninstall it, just stop it:

```

sudo /etc/init.d/mythtv-backend stop

```

---

### Post by Astrogeek on 2009-02-26
Hi again.



>  What does:

```

ls /dev/dvb/adapter*

```
return? 

```
eric@greatblue:~$ ls /dev/dvb/adapter*
demux0  dvr0  frontend0  net0

```



>  what does:

```

ps aux | grep myth

```
return? 

```

eric@greatblue:~$ ps aux | grep myth
mythtv    5682  0.0  1.0 133136 21760 ?        Ssl  17:39   0:00 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
eric      7285  0.0  0.0   3240   800 pts/0    S+   18:06   0:00 grep myth

```

looks like myth is still running afterall.

I'm running the scan now, which seems to be actually working! I'll report in later with results.

Eric

---

### Post by molder on 2009-04-24
I am not able to tune analog channels now.

---

### Post by molder on 2009-05-04
Bump.  

Digital channels are great but my analog channels will not tune.  When I scan I get no channels detected.  If I Fetch the channels from Schedules Direct and tune an analog channel, just static.

---

### Post by xmrkite on 2009-05-05
I have the same issue. Digital works great, but no analog.

---

### Post by jaketrunk on 2009-05-27
I'm getting stuck trying to unzip the firmware.  I followed Newlinux's instructions on post #17, but keep getting the following error when I run the "sudo perl get_dvb_firmware nxt2004" command:

unzip failed - unable to extract firmware at get_dvb_firmware line 421.

I'm running Mythbuntu 9.04.  Any help would be greatly appreciated.

---

