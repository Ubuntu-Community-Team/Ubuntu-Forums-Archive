---
title: "Realtek ALC892 sound drivers - so many options"
date: 2010-05-25
forum: Multimedia Software
---

### Post by OdinOrion on 2010-05-25
First, I must state I am a total Linux noob.  I can see why Linux is not mainstream with all the difficulties in setup, but I am sticking with it.  I installed Ubuntu 10.04 on the machine I recently built because I was not willing to shell out $$$$ for Windows 7.  XP is installed in dual boot.

Anyway, back to the subject.  The system I built uses the Gigabyte 890GPA -UD3H.  Great board!  I chose it for my particular needs.  USB3, Sata 3.0, good on board graphics (I play old games, really old games!), and lastly Realtek ALC892 sound with Dolby Theater.  Original plan was to continue with Windows XP, so Linux was not a consideration...fast forward a week.

Gigabyte does not offer any Linux support, and refers Linux users to vendor proprietary drivers or 3rd party sources.  So I went looking for support for the ALC892 codec.  The ALC892 is fairly new to the scene.  What I have found is fairly confusing.

I do have sound at this point, but don't have the full feature set. There is mention here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573378) that the Ubuntu 10.04 default kernel ( 2.6.32) does not support ALC892 and that a back port to kernel 2.6.33.xx will allow for full function.  So this seems promising

But then I found [http://bstdownload.com/reviews/realtek-hd-audio/](http://bstdownload.com/reviews/realtek-hd-audio/) which was last updated May 24, 2010.  The screen shots below seem to show a control panel very similar to the one distributed with the Gigabyte motherboard when running under Windows.  So this looks good too.

Then there is this [http://www.userdrivers.com/Sound-Card/Realtek-HD-Audio-Codec-Driver-5-14rc5-for-Linux/](http://www.userdrivers.com/Sound-Card/Realtek-HD-Audio-Codec-Driver-5-14rc5-for-Linux/).  The interesting thing here is that it states: The source code copy from [www.alsa-project.org]("http://www.alsa-project.org"). ver:5.14 Linux Source  Code for ALC audio codec.  

Then there is this from Realtek website (at the very bottom of the page of course). [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&G](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&G)  Which seems to be an very recent update of the previous link.

And finally this [http://rapid-downloads.com/servers.asp?PID=04ac522b-8dc2-4ef2-8918-03cc648ffd98&jstyle=1&lbd=1&lang=EN&ts=5/23/20](http://rapid-downloads.com/servers.asp?PID=04ac522b-8dc2-4ef2-8918-03cc648ffd98&jstyle=1&lbd=1&lang=EN&ts=5/23/20)  which gives no details, so I am very wary of trying it.

Which one should I try?  I would think the driver listed on the Realtek website should be the best.  But should I just back port instead?  Or should I back port *and *install the driver from the Realtek website?

Looking for suggestions thanks!

BTW, my first download from the Ubuntu software center was Rosegarden.

---

### Post by OdinOrion on 2010-05-25
I think I will back port and then use the drivers from the Realtek website.  I am not sure I really need to do both, but I would rather update the kernel now.  

I assume I will have to remove the default drivers no matter if I back port or not.  Otherwise the new drivers won't work.

Anybody know how to remove the default drivers?

*Update:*  It appears that the lucid back port link is broken!  Sent an email to notify.

---

### Post by OdinOrion on 2010-05-31
Ok, now that I am officially talking to myself.

I still need to remove the default drivers.  I assume I can't install the ALC892 drivers on top of the default drivers, right?

I really need some help with this,

Thanks

---

### Post by grege on 2010-06-04
As I said in the other thread, I was thinking of buying this board. Now I have.

Running Ubuntu 10.04 with a 2.6.34 kernel stereo analog sound burst forth from the speakers without any configuration or outside drivers. I cannot test it with 5.1 as this computer only has stereo connections.

However clicking on the speaker icon, then sound preferences, then Hardware, then Internal Audio, then Settings for the selected device I get all the expected options up to 5.1 Analog (no 6.1 or 7.1) plus digital stereo out and digital stereo duplex (two way). I would be confident that if I connected the spdif out to an amp and selected AC3 passthrough in VLC that DVDs would play in 5.1.

Stereo music, video and flash all play as expected.

cheers

ps

you can install drivers over the installed ones, in fact it is quite difficult to remove the installed ones. To remove them you would have to dig around in /lib to find them then rename them to disable them. There is no simple unistall of individual drivers. Linux is not like Windows, generally the built in drivers are the best, with the exception of Nvidia and ATI video drivers. Then there is the issue of an update blithely overwriting your hard work with the default drivers. Anyway the supplied Linux kernel drivers work for me.

---

### Post by Yellow Pasque on 2010-06-04
Personally, I would grab kernel and headers packages from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/) , install them, boot into the new kernel and run ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by OdinOrion on 2010-06-04
> **Temüjin said:**
> Personally, I would grab kernel and headers packages from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/") , install them, boot into the new kernel and run ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

This is exactly what I did.  I back ported the Lucid kernel to 2.6.34.

I did not mention it here, but I did do the back port previously and it caused some issues with the proprietary ATI Catalyst drivers.  The back port knocked out the driver and I couldn't seem to get it to function again even by trying to install the latest 10.5 catalyst.

Since I don't have anything valuable on the computer right now (new build) I did a fresh 10.04 install and started over.  This time however, I did the back port first.  Right now the open source drivers are in use for graphics, but I hope to get the proprietary drivers working soon.  

But for now at least I have increased audio function with the back port.  I still do not have full function.  Like no option for 7.1 (I doubt I will use it anyway).  And i am not sure if I will be able to have the ability to change the input/output configuration of the analog like I can under windows.

I also have not had the ability to test any digital output yet.  The analog stereo seems to work well.  

I have an old Cambridge Soundworks 5.1 system that I have used for ~12 years.  It does not have optical, but does have coax AC-3 input.  The standard output for the Gigabyte 890GPA -UD3H only has optical and analog in/out.  But a coax header can be plugged into the mobo.  I will most likely make a header from spare bits.  So, I hope to test the 5.1 digital function soon. 

I hope down the road to provide comparison of feature under Linux and under Windows to see which features are not available in Linux. 

Do you know if the upgrade script changes anything?

---

### Post by grege on 2010-06-04
Odinorion

The ATI driver issue is simply that ATI ties each update to kernel releases and they are always behind. Ubuntu have to get a special version for each release because ATI never have one ready. Nvidia are always up to date with the latest and greatest. For you the only solution is to wait. When Ubuntu 10.10 is released it will have everything you need. If you continue to use 2.6.34 then you will be tied to the open source video driver, which is always going to work irrespective of the kernel. There are experimental PPAs for the latest open source stuff but they might be more work than is sensible, and are mainly aimed at older ATI chipsets.

The good news is that the open source driver will soon be using Gallium 3d drivers and you will be then able to forget ATI drivers forever. By soon I mean 6 - 12 months. If you are not using Linux to play high end 3d games then the open source driver is better anyway as it updates happily and just works for normal desktop and video work.

I also have an older Gigabyte board with onboard HD3200 graphics chip driving a 46" 1920x1080 LCD TV and it plays full screen avis and DVDs without effort using the current standard Ubuntu 10.04 supplied open source driver. 

So unless you are a gamer I would not stress about the ATI drivers.

---

### Post by grege on 2010-06-05
Out of curiosity I rebooted into a stock 2.6.32 Ubuntu 10.04 and the sound from the ALC892 worked, but only a very basic stereo duplex mode as the only option. By installing a 2.6.34 kernel all the other options for Surround and digital connections appeared. The options go up to 5.1, but not 7.1. It may be possible to manually configure 7.1, but I have no use for it so I am happy as it stands.

Hopefully this will help those searching on this chip.

---

### Post by Yellow Pasque on 2010-06-05
> Out of curiosity I rebooted into a stock 2.6.32 Ubuntu 10.04 and the sound from the ALC892 worked, but only a very basic stereo duplex mode as the only option.
You can try running the ALSA script while you're booted into this kernel. Maybe replacing the 2.6.32 ALSA kernel modules with fresh ones built from ALSA 1.0.23 will do the trick without having to use a 2.6.34 kernel.

---

### Post by grege on 2010-06-05
> **Temüjin said:**
> You can try running the ALSA script while you're booted into this kernel. Maybe replacing the 2.6.32 ALSA kernel modules with fresh ones built from ALSA 1.0.23 will do the trick without having to use a 2.6.34 kernel.

I have no doubt that installing ALSA 1.0.23 would do the trick and allow OdinOrion to use fglrx with a 2.6.32 kernel. He would have to keep the install in a folder to re-run in the event a routine update killed the ALSA overwrite, unless he wanted to play with apt pinning.

For me, I will be staying with 2.6.34, I am happy with the performance of the open source radeon driver and very happy with my new Gigabyte 890GPA-UD3H motherboard, complete with USB 3 and SATA 3.

fglrx has been a pain for years, the sooner we have Gallium 3d and open source drivers the better.

---

### Post by OdinOrion on 2010-06-05
> **grege said:**
> Odinorion

The ATI driver issue is simply that ATI ties each update to kernel releases and they are always behind. Ubuntu have to get a special version for each release because ATI never have one ready.

The good news is that the open source driver will soon be using Gallium 3d drivers and you will be then able to forget ATI drivers forever. By soon I mean 6 - 12 months. If you are not using Linux to play high end 3d games then the open source driver is better anyway as it updates happily and just works for normal desktop and video work.

So unless you are a gamer I would not stress about the ATI drivers.

Ok, I kinda get it now.  Well, I guess my issue is that I don't want to nerf any functional potential of the board.  I am not a huge gamer, and I have dual boot set up with XP anyway.  So if I want to game, I can just boot to XP.  The real issue, is that I don't know exactly what I will do in the Linux world, but I want to explore its full range. 

One example, is that have installed Cairo-Dock.  I like it because it is functional, but there is the eye candy aspect.  When you install the Cairo-Dock, there is two versions.  One with Open GL and one without Open GL.  Guess what, the Open GL version does not function without fglrx. 

I don't know how many boards are out there with some combination of ALC892 and ATI graphics, either with integrated graphics or separate card,  but it may be quite a few.

---

### Post by OdinOrion on 2010-06-05
Sheesh!


Tried the ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) alone on original Lucid 10.04 kernel.  First part of compilation worked.

***************************************************************************
*  Alsa packages sucessfully downloaded - run compilation -c next
***************************************************************************
So i did as instructed:  andrew@andrew-desktop:~/Downloads$ sudo ./AlsaUpgrade-1.0.23-2.sh -c

It did a bunch of crap and then got this:

cp ../../alsa-kernel/include/ac97_codec.h .
patch -p0 -i ac97_codec.patch ac97_codec.h
make[4]: patch: Command not found
make[4]: *** [ac97_codec.h] Error 127
make[4]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
make[3]: *** [prepare] Error 2
make[3]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23'
make: *** [include/sndversions.h] Error 2

***************************************************************************
*  alsa-driver-1.0.23 make failed
***************************************************************************

Awesome!!!  I looked through most of the 80+ pages of the ALSA upgrade script thread and found many references to others having various errors which resulted in *  alsa-driver-1.0.23 make failed.  Very few people got any response to their particular issue.  Which makes finding a solution difficult. 

It seems every solution I try ends up creating more problems!!

---

### Post by Yellow Pasque on 2010-06-05
As I posted in the other thread, it is a problem with the script: [http://ubuntuforums.org/showpost.php?p=9416125&postcount=864](http://ubuntuforums.org/showpost.php?p=9416125&postcount=864)

---

### Post by OdinOrion on 2010-06-07
> **Temüjin said:**
> As I posted in the other thread, it is a problem with the script: [http://ubuntuforums.org/showpost.php?p=9416125&postcount=864](http://ubuntuforums.org/showpost.php?p=9416125&postcount=864)

Ok, well did as you suggested and did the upgrade, and then re-ran the script.

Everything seemed to work, and I did not get any errors this time.  Under the Alsa Mixer I now have additional features such as surround, center, LFE volume control.  The Alsa Mixer top panel reads: HDA ATI SB : Realtek ALC892. This is good!

However, nothing has changed under the Sound Preferences tab.  With the back port, under the Sound Preferences tab, I was able to select from various output types, analog, analog duplex, analog 5.1, digital, ect.  

Something still has not worked.  I do have sound because I have analog cables running to the Desktop Theater 5.1.  But this does not enable 5.1.  I made digital output AC-3 header bracket from some spare bits and plugged it into the motherboard.  I know that this homemade  header works, because it operates under Windows XP.  

So, in the end, I am not sure the upgrade script really did anything other than what I see under the Alsa Mixer.

It looks like I am back to the original solutions. 1) back port 2) trying the LinuxPkg-5.15rc1.tar.bz2 I downloaded direct from the Realtek support page.

---

### Post by OdinOrion on 2010-06-07
I just did a manual install of the driver offered on the Realtek support page.  Now under the Sound preferences and then the Hardware tab I have the following choices: 1)Bt878 Audio Capture, 1 input, Analog Stereo Input. 2)Internal Audio, 1 Output, Analog Stereo Output 3) RS880 Audio Device [Radeon HD 4200], 1 Output, Digital Stereo (HDMI) Output.

1) This is my old TV/FM tuner card that I haven't even begun to think about
2) What I am trying to get to work
3)HDMI output, not even going there

Under item 2) profile drop down box, I get the following options (NOTE: these options were *NOT *available after running the Alsa Script!)


The only two options for anything digital are near the bottom of the list.  Both have IEC958 in the description.

---

### Post by OdinOrion on 2010-06-07
Here is the Alsa Mixer.  Should there be sliders under the IEC958?

---

### Post by OdinOrion on 2010-06-08
Still not working.  I am just flogging around with this now.  I don't know what to do next.  I still think there should be sliders under the IEC958, but maybe not.

I feel like plugging an oil leak at 5000 feet below sea level would be easier.

---

### Post by lidex on 2010-06-09
Not familiar with gamix, but in gnome-alsamixer you go to the 'Edit>Soundcard Properties' menu to enable the spdif output, then on the soundcard tab unmute/select spdif/iec958. They are muted by default.

---

### Post by OdinOrion on 2010-06-10
> **lidex said:**
> Not familiar with gamix, but in gnome-alsamixer you go to the 'Edit>Soundcard Properties' menu to enable the spdif output, then on the soundcard tab unmute/select spdif/iec958. They are muted by default.

Gamix may actually be the problem.  It doesn't seem to give me any real control over iec958 settings.

I will go after the gnome-alsa mixer and get rid of gamix.  I should have done that anyway just to be thorough.

---

### Post by OdinOrion on 2010-06-12
Blah!!!!!!

Removed the Gamix interface and installed Gnome-alsamixer.  Same deal, no sound.  It won't even let me change the volume sliders for iec958.

I think I will go and back port again on top of another fresh install (I swear this must be my 7th or 8th install), just to see if I can get it work at all with native support.  If I can't get it to work with the backport, then I think something  must be seriously amiss.  Of course I will not use the updated kernel in the end because it messes up the ATI graphics drivers, but I just want to see if the digital out will work under any circumstance.

Again, everything works fine under Windows XP.

---

### Post by Guydin on 2010-07-24
I have the same motherboard as OdinOrion.  I have been using MS operating systems since DOS (though I was a kid with little understanding of DOS beyond how to get a few programs running).  I want to switch to Ubuntu because I want to develop and customize my computer experience, and hopefully contribute to the software that I use.  I use an nVidia gfx card which seems to work fine, but I am having trouble with sound.

I would like to be able to use the on-board sound as well as my USB headphones (Logitech G35).  Unfortunately, I am a complete Linux noob, and the only way I know to install programs is to run a install program.  I am looking forward to learning the Linux way of doing things though.

I do not understand what you guys doing in this thread, but I would like to.  Is there somewhere I can go to get a better understanding?  I don't know how to mess with the kernel or anything else.  Linux does not seem to be detecting my sound card at all (I ran something that a stickied thread recommended from the terminal, and nothing showed up for sound).

---

### Post by lidex on 2010-07-24
> **Guydin said:**
> I have the same motherboard as OdinOrion.  I have been using MS operating systems since DOS (though I was a kid with little understanding of DOS beyond how to get a few programs running).  I want to switch to Ubuntu because I want to develop and customize my computer experience, and hopefully contribute to the software that I use.  I use an nVidia gfx card which seems to work fine, but I am having trouble with sound.

I would like to be able to use the on-board sound as well as my USB headphones (Logitech G35).  Unfortunately, I am a complete Linux noob, and the only way I know to install programs is to run a install program.  I am looking forward to learning the Linux way of doing things though.

I do not understand what you guys doing in this thread, but I would like to.  Is there somewhere I can go to get a better understanding?  I don't know how to mess with the kernel or anything else.  Linux does not seem to be detecting my sound card at all (I ran something that a stickied thread recommended from the terminal, and nothing showed up for sound).
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Guydin on 2010-07-24
> uname -a
Linux Hoth 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux


> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


> dpkg -1 | grep "alsa"
dpkg: unknown option -1

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


> head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ID 892

I guess it is detecting it.  I am using a custom built desktop.

Motherboard: GIGABYTE GA-890GPA-UD3H
CPU: AMD Athlon II X4 635 Propus 2.9GHz Socket AM3
Video: BFG Tech BFGEGTX275896OCE
Power: Thermaltake W0319RU 850W ATX 12V 2.2
HDD: Western Digital Caviar Black WD1002FAEX 1TB
RAM: OCZ Platinum 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory Model OCZ3P1333LV4GK

I can gather any other information you need if you let me know how.

---

### Post by lidex on 2010-07-25
Try this one again using lower case L, not number 1:
```
dpkg -l | grep "alsa"

```

---

### Post by Guydin on 2010-07-25
> dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA


.

---

### Post by lidex on 2010-07-25
Best hope for this codec is with latest alsa. Use the alsa-upgrade link in my sig.

---

### Post by Maconi on 2010-08-03
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug  2 2010 for kernel 2.6.31-22-generic-pae  (SMP).
``````
aplay: version 1.0.23 by Jaroslav Kysela  <perex@perex.cz>
``````
**** List of PLAYBACK Hardware  Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
 HDA Intel, ALC892 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI 0
    HDMI Audio Output
``````
Codec: Intel G45 DEVIBX
Address: 3
Function Id: 0x1
Vendor Id: 0x80862804
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:      
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="INTEL HDMI 0", type="HDMI", device=3
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="INTEL HDMI 1", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3
  Power: setting=D0, actual=D0
```I have sound over HDMI, but if the source is anything higher than stereo all I get is static (5.1 doesn't work).

When I went into the .conf file I noticed that...

```
options snd-hda-intel index=-2
```Wasn't even in the file, but...

```
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
```Was. I added "options snd-hda-intel index=-2".

After a reboot I got an "Audio Failed to Initialize" error (it at least worked for stereo before).

Also, after adding "options snd-hda-intel index=-2" I got this error when typing aplay.

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hdmi
aplay: main:654: audio open error: No such file or directory

```After removing the "options snd-hda-intel index=-2" line and rebooting, it worked just like it did before (stereo sources work, surround sources don't, all over HDMI).

Also, ever since adding the "options snd-hda-intel index=-2" line and removing it I get an...

```
aplay: main:654: audio open error: Device or resource  busy
```Error anytime I try to type aplay and I can't run any speaker tests without getting the same error (Device or resource busy).

Any suggestions on any of the above?

---

### Post by jc_75 on 2010-08-13
did you finally resolve your problem ?
I have the same chipset and no sound from my computer !

---

### Post by sorin7486 on 2010-08-26
Has this been solved ? I had the 64 bit version of Ubuntu until earlier today and sound worked just fine. Sadly everything else seemed to be broken. So I decided to switch to the 32 bit version and everything else works but sound. Talking about frustrating !!!

---

### Post by shunte88 on 2010-08-28
Same problem here too; mobo is M488TD-M/USB3

I've upgraded to alsa 1.0.23 can now see S/PDIF but no sound on any of the outputs

Do you have any resolution on your install?

Any help would be much appreciated, I'm loathing the thought of rebuilding my new HTPC with Win 7

** Edit **
I checked alsa version and I was still on 1.0.22 so went through the build and compile again; originally I had a mix of .21 and .22 so I'm assuming thats why I didn't get .23 complete.

after reboot checked alsa with the following

stuart@stue-htpc:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 28 2010 for kernel 2.6.32-24-generic (SMP).

still no sound so manually ran configurator

sudo alsaconf

and that seems to have done the trick

hope this helps someone

---

### Post by cyberdiga on 2010-09-01
Same problem here. 

i installed ubuntu 10.04 with alsa 1.0.23 but no output on spdif optical and coaxial
i also tried different kernel versions

is it possible to enable de spdif output from alc892 at ubuntu 10.04, and if yes how do i do that.

see printscreen of alsamixer.

[IMG]http://www.cyberdiga.nl/forums/alsamixer.png[/IMG]

---

### Post by OdinOrion on 2010-09-19
Well, I abandoned Ubuntu after so many frustrating hours messing with this sound issue.  I never did get the digital sound to work.  In fact, I messed around enough to make the system freeze and got all sorts of errors.

Well now I have downloaded and installed 10.10 beta.  And I don't have digital sound again.  I haven't bothered to pull out the analog cables yet.  Still, I was hoping the issue would be resolved either through the latest version or through Realtek.  But it doesn't seem anything has changed.  Very frustrating to say the least. 

All this '"user friendly" aspect to Ubuntu that is touted seems to be off the mark.  I really just want it to work right. A tweak here or there is OK, but I literally spent hours upon hours trying different approaches.  Most of the time I wasn't really sure what I was doing, so most attempts made me feel like I was flailing about like a mad monkey.

I am sure that some in the Linux world would insist that if I can't handle a little code, than I should just buck up and buy Windows 7 because obviously Linux is not for me. I have sooo many other things that require my time and energy.  I don't have a lifetime to figure this out.  Am I crazy to expect this to work right the first time?

Anyway, I am still hoping someone has come up with a solution.  If not, I guess I will enjoy my XP for another ten years.

---

### Post by b0neski on 2010-10-22
Hi guys.
Asus M4A88TD-M motherboard with realtek ALC892 chipset.
Mythbuntu 10.04.
SPDIF optical was not working!
I followed the instructions here [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) which upgraded me to the ALSA 1.0.23 drivers (from 1.0.21).
Manually ran "sudo alsaconf" then went to mythtv frontend audio settings (Utilities / Setup > Setup > General > Audio systetm), changed Audio output Device to ALSA:spdif and bingo!
Working!
You may need to mess with more settings in this audio section - my amp didn't like myth trying to upconvert stereo to 5.1 and I changed the "Digital output device" to ALSA:iec958. Obviously your settings will differ depending on what amp you have.
 
Thanks shunte88 for mentioning the last step of alsaconf. I knew it had to work because we've got almost the same mobo.

---

### Post by ericwdanielson on 2011-06-03
I have a ASUS M4A89GTD mobo. Was having problems enabling surround sound. mobo has onboard surround ALC892 from realtek. Updated ALSA no luck. What ended up working was when I completely removed pulseaudio. once I did that all speakers are working fine.

---

### Post by mutt|ey on 2011-08-04
I have an integrated audio (Realtek ALC892 Audio Codec) on a Asrock 880GXH.

If i set in phonon:

- "Internal Audio" > "Analog Stereo Duplex" i can only hear audio in passthrought (Dolby Digital and DTS)

- "Internal Audio" > "Digital Stero Duplex " i can hear all "normal" sound but no passthrought (Dolby Digital and DTS)

Ubuntu 11.04 32bit, Kernel 2.6.38-11

---

### Post by jaygo on 2011-10-05
Thanks for that note, muttley. It looks like that setting forces passthrough. Since there's no setting for digital 5.1, that appears to be the easiest way to do it.

---

### Post by glaubersm on 2011-10-20
Does Realtek HD Audio work with pulseaudio sound server on lucid or not?
Does it work only with alsa?

---

### Post by jaygo on 2011-10-23
@glauber
my ALC888 has worked perfectly with pulseaudio for a number of versions, including lucid.

---

