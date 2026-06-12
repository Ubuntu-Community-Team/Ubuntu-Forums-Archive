---
title: "HOWTO: Install the Nvidia driver on Edgy Eft"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by tseliot on 2006-10-21
Hi, I've ported my guide about the Nvidia Drivers to Edgy Eft on the USDF.
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Or on my website:
[Latest Nvidia Edgy]("http://albertomilone.com/latest_nvidia_udsf_edgy.html")

**[COLOR="Red"]The guide works ONLY for driver 8774 or higher (Method 2)[/COLOR]**



--------------------------------------------------------------------
Script to make Method 2 faster

You can also use my Envy script which you can find below (for automating Method 2 and solving problems of driver mismatch)

NOTE: this might be dangerous and buggy

This script will download the Nvidia installer (and all the files the installer needs) and set the driver for you.

Get to the following website:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And follow the instructions you will find there.

The scripts will install the Nvidia driver 9631 and 7184

---

### Post by Nano Geek on 2006-10-21
Thanks for the great guide!   =D> =D> =D>
Edit: When I tried to force the Nvidia beta driver to use the right resolution for my 19 inch widescreen monitor, it left me with only 800x600. Do you know any way to fix this?
Thanks

---

### Post by rplantz on 2006-10-21
I tried twice. Both times it refused to start my x server until I changed "nvidia" to "nv" in my xorg.conf.

I have an nvidia Geforce FX5200 128MB graphic card.

I'm running ```

bob@ubuntu:~$ uname -a
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

```
so I installed linux-generic.

I also note that in the past I tried to install nvidia-settings, but it won't allow both nvidia-glx and nvidia-settings.

I don't know how to determine if I'm using my card to best advantage, but the current Applications->System Tools->NVIDIA-Settings really does not allow me to do anything.

Edit: I got it to work! I used synaptic to completely remove linux-generic, linux-restricted-modules-2.6.17-10-generic, linux-restricted-modules-generic, nvidia-glx, nvidia-kernel-common. Then I followed the howto.

---

### Post by DidRocks on 2006-10-22
Thanks for your post but unfortunatly it doesn't work for me
I tried to install the latest beta nvidia driver (9625) with my toshiba laptop using a GeForce4 420 Go. 

What i must precise is that from Warty, i was using the nvidia driver properly, but, some days before the release of Dapper, this one wasn't working anymore (just getting a black screen) and i had to use the legacy driver + making some tips to no have a black band on the right of my screen.

So, i want again to try with the official driver and install the 9625 because i wan to use Aiglx). I followed your section 7) If you own a GeForce4 420/440 Go or a GeForce4 MX 440 of the PROBLEM SECTION without any luck.
> 
I tried in /etc/modprobe.d/options:
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1

and in xorg.conf :
Option "ExactModeTimingsDVI" "TRUE"
Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"

then
Option "ExactModeTimingsDVI"
Option "UseEdidDpi" "FALSE"
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"

and also :
> In /etc/modprobe.d/options:
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=4

with in xorg.conf :
Option "ExactModeTimingsDVI" "TRUE"
Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"

then
Option "ExactModeTimingsDVI"
Option "UseEdidDpi" "FALSE"
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"

without success ! i'm stuck with a black screen. I can hear me log in. So, the kernel isn't frozen.
I tried the section "16) If you can hear drums (greeting) sound when your Ubuntu boots but there is no output on the monitor:" and add the Option "UseEDID" "False" in the Device section. I tried to add a resolution and a refresh rate working with the nv driver. Without success again. I also tried all the combinaison of this tip with the previous (a great number of tests !!!)

Do you have any idea ? Thanks !

---

### Post by tseliot on 2006-10-22
I don't use the Beta driver (since I need a stable OS) therefore I wouldn't know how to help you.

My guide will be updated when the stable version of that driver is released.

---

### Post by DidRocks on 2006-10-22
So, i tried to install 8774 and i works with the first solution. Thank you very much, i was tired of using the legacy drivers :p !
I'll stay connected as soon as 9625 will be ok for Geforce4 420Go ! (Try to be patient beforce using Aiglx)

---

### Post by The Noble on 2006-10-22
DidRocks, I have the same graphics card as you so you are not alone in this struggle. I have gone through quite a few hoops to get the driver working, but I sadly have nothing good to report. Don't waste your time right now, as nothing is working, the screen is always black. 

If anyone has a similar problem to what Didrocks and I are experiencing please PM us if you got anywhere. I have patched the driver with the official i2c patch, installed the regular drivers (from both Amaranth's repos and the regular .run), and a few other things, so looks like we are forced to wait for now.

---

### Post by interurban on 2006-10-24
> **asjdfwejqrfjcvm msz34rq33 said:**
> 
Edit: When I tried to force the Nvidia beta driver to use the right resolution for my 19 inch widescreen monitor, it left me with only 800x600. Do you know any way to fix this?
Thanks

You need to edit your xorg.conf to change your resolution (I am assuming you already tried System-->Preferences-->Screen Resolution).
```

sudo gedit /etc/X11/xorg.conf
```Then you need to add the resolution(s) you want to the "Display" subsection in the "Screen" section.

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
```Where it says   Modes  "1280x1024" "1024x768" .... simply add the resolution you want in front, making it:

```
SubSection     "Display"
        Depth       1
        Modes      "Your Resolution Here" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
```Repeat for the other subsections.
Hope this helps.

---

### Post by drakin on 2006-10-24
thank you very much 
method 2 worked for me
GeForce FX 5200 
Nvidia driver 9625 beta

---

### Post by Nano Geek on 2006-10-25
> **interurban said:**
> You need to edit your xorg.conf to change your resolution (I am assuming you already tried System-->Preferences-->Screen Resolution).
```

sudo gedit /etc/X11/xorg.conf
```Then you need to add the resolution(s) you want to the "Display" subsection in the "Screen" section.

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
```Where it says   Modes  "1280x1024" "1024x768" .... simply add the resolution you want in front, making it:

```
SubSection     "Display"
        Depth       1
        Modes      "Your Resolution Here" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
```Repeat for the other subsections.
Hope this helps.Thanks, but my problem is that it just won't use the resolutions in my xorg.conf file. My resolutions are already set right. Again, thank you for giving me suggestions.

---

### Post by martijn hoekstra on 2006-10-25
> I tried twice. Both times it refused to start my x server until I changed "nvidia" to "nv" in my xorg.conf.

I had the complete oposite. I had to change "nv" to "nvidia". Thank god I remembered reading this post, because I wouldn't have figured it out myself.

Oh well, I'm still left with a 'press and pray' system: about 50% of the time it makes it trough initial boot. Add to that that when X fails It also gave me about 30% of the time a login promt, and hung (hanged, hing?) the other 70, that gave me about 85/100 reboot with the power plug.

Oh well, it runs now.

---

### Post by BragiRagnarson on 2006-10-26
> **The Noble said:**
> DidRocks, I have the same graphics card as you so you are not alone in this struggle. I have gone through quite a few hoops to get the driver working, but I sadly have nothing good to report. Don't waste your time right now, as nothing is working, the screen is always black.

I have actually managed to start X on my laptop. The problem is that I did it in recovery mode (select recovery mode from GRUB and provide root password).

I think why this works and normal login fails is because of ACPI stuff that is enabled AFTER you log out from recovery console. Also some suggested patches for Gentoo seem to confirm this.

I'll wait for a proper solution and live with "nv" driver for the time being. At least hibernation works :)

---

### Post by DSK on 2006-10-26
I used the script and installed the driver.  Then I downloaded the 9625 driver package and installed with NVIDIA installer.  Next I installed Beryl and everything works great on my 6800GT! 

It would be great if we could enter the driver version that the script uses.

Thanks for the script.

---

### Post by Caseyjp on 2006-10-26
Just a heads up regarding the 7950GT cards.

NVIDIA has released the 9626 driver for "quaddro", and per the nvforums, this is the ONLY driver right now working with the 7950 series.  I installed it and it works like a charm....however the 8x series does NOT see the 7950 as a valid nvidia card.

Here is the link to the nvidia 9626 driver:

[http://www.nvidia.com/object/linux_display_ia32_1.0-9626.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-9626.html")

This is NOT for the 7950 GTX cards, as they are 2 7900GT cores, which isn't the same as the 7950GT KO series.

---

### Post by Xgates on 2006-10-27
Why do we need to use this script, what is wrong with just installing Nvidia with Synaptic?

THANKS

---

### Post by Caseyjp on 2006-10-27
I'm just stabbin' in the dark here, but most of us want current nvidia drivers.  Once the distro is 'released', that is all she wrote for the synaptic "way" until the next release.

This script gets updated with the latest nvidia drivers as nvidia releases them....therefore...a need for the script.  

There is also the 'manual' install method, but this script simplifies the hell out of it for the casual user who doesn't have a clue what a "header file" or "kernel sources" are.  Got it?

---

### Post by tseliot on 2006-10-27
> **Xgates said:**
> Why do we need to use this script, what is wrong with just installing Nvidia with Synaptic?

THANKS

You don't need my script. If you had a problem of driver mismatch or if you used a recompiled kernel my script could come in handy.

Using the driver from the official repos or from my repos is usually a better idea

---

### Post by Magneto on 2006-10-27
> **tseliot said:**
> You don't need my script. If you had a problem ...........
Using the driver from the official repos or from my repos is usually a better idea

If only the new fangled ideas of mangling an upgrade via deletion of all drivers were as trouble free as your script. Thank you worked flawlessly. I upgraded and it looks like all my video drivers were deleted, which is fine by me anyway since I only need one.

---

### Post by tseliot on 2006-10-27
> **Magneto said:**
> If only the new fangled ideas of mangling an upgrade via deletion of all drivers were as trouble free as your script. Thank you worked flawlessly. I upgraded and it looks like all my video drivers were deleted, which is fine by me anyway since I only need one.

That problem will be solved in the next release of Envy but only fo Ubuntu Edgy

---

### Post by budluva04 on 2006-10-27
yup, your script worked like a charm for me....ubuntu edgy 6.10 and nvidia fx5500....

great work, keep it up

---

### Post by MemoryDump on 2006-10-27
I'm about to do a fresh install of Edgy on my P4 3.2 with 2gigs of ram with a NVIDIA GeForce 7800 GS (pci) installed..

after applying all the ubuntu updates (if there are any)..
which method would you recommend I use given my setup?

I'm hoping to get WoW running on this sytem if I'm successfull this time.. haven't had any luck in the past (with WoW.. not the video drivers).. so I've always had to revert back to WindowsXP.

thanks

---

### Post by tseliot on 2006-10-27
> **MemoryDump said:**
> I'm about to do a fresh install of Edgy on my P4 3.2 with 2gigs of ram with a NVIDIA GeForce 7800 GS (pci) installed..

after applying all the ubuntu updates (if there are any)..
which method would you recommend I use given my setup?

I'm hoping to get WoW running on this sytem if I'm successfull this time.. haven't had any luck in the past (with WoW.. not the video drivers).. so I've always had to revert back to WindowsXP.

thanks
Method 1

**and if it doesn't work and the Xserver crashes**:
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

### Post by eutu on 2006-10-27
than you this worked fine i am using xubuntu with an old gforce 3 vidio card

---

### Post by Lord Landis on 2006-10-28
I too am having major pains installing the nvidia drivers.  Now, it's partially my fault, as I had an ATI card in and changed them out.  But aside from that, whenever I try to do 'apt-get install nvidia-glx', I get the following error:

dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Do any of you know of a way to work around this short of re-installing?

Thanks.

---

### Post by tseliot on 2006-10-28
> **Lord Landis said:**
> I too am having major pains installing the nvidia drivers.  Now, it's partially my fault, as I had an ATI card in and changed them out.  But aside from that, whenever I try to do 'apt-get install nvidia-glx', I get the following error:

dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Do any of you know of a way to work around this short of re-installing?

Thanks.

You have to remove the ATI driver before installing the Nvidia one.

Type:
```
sudo aptitude purge xorg-driver-fglrx
```

then
```
sudo aptitude install nvidia-glx
```

---

### Post by sandyeggoboy on 2006-10-28
Hi all, i have been reading these posts for a while now, but have been concentrating on getting other, more important things working first. 

i have a Riva TNT2 card, 32mb ram, and i can't seem to get ANY driver to work. anyone know which driver i need to install>?

---

### Post by Lord Landis on 2006-10-28
> **tseliot said:**
> You have to remove the ATI driver before installing the Nvidia one.

Type:
```
sudo aptitude purge xorg-driver-fglrx
```

then
```
sudo aptitude install nvidia-glx
```

I just tried that, and I got exactly the same error message as before.

---

### Post by tseliot on 2006-10-28
> **sandyeggoboy said:**
> Hi all, i have been reading these posts for a while now, but have been concentrating on getting other, more important things working first. 

i have a Riva TNT2 card, 32mb ram, and i can't seem to get ANY driver to work. anyone know which driver i need to install>?

Try the legacy driver. And if that doesn't work, read my Problems Section (point 4 and point 10)

---

### Post by tseliot on 2006-10-28
> **Lord Landis said:**
> I just tried that, and I got exactly the same error message as before.

Type:
```
sudo rm /var/cache/apt/archives/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb
```

and then do what I suggested before

---

### Post by Lord Landis on 2006-10-28
> **tseliot said:**
> Type:
```
sudo rm /var/cache/apt/archives/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb
```

and then do what I suggested before

Still no luck.  Thanks for the help though.  I think I'll burn the alternate install CD and see if the repair installation fixes things.

--EDIT--

I fixed it!  It turns out that I had to do the following:

```
sudo dpkg-divert --remove /usr/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
```

After that, apt-get installed the drivers just fine!

---

### Post by tseliot on 2006-10-29
**[COLOR="Red"]UPDATE: 2 new releases of Envy are available[/COLOR]**.

Envy DOES NOT remove the restricted modules any more.

read the rest [here]("http://albertomilone.com/wordpress/?p=40")

---

### Post by cyberswat on 2006-10-29
I performed a completely clean installation of Ubuntu 6.10 today and did not touch anything before installing wine and the WoW.  Followed the instructions at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) to add the repository and install Wine.

Installed windows fonts into wines font folder so I could read the WoW installer's directions.

The WTF/Config.wtf had to contain the following lines because anything less created an evil flickering of horizontalish lines:
   SET gxResolution "1280x1024"
   SET gxRefresh "75"
   SET gxColorBits "24"
   SET gxApi "opengl"
   SET SoundOutputSystem "1"
   SET SoundBufferSize "150"
   SET hwDetect "0"

I've tried this a bunch in the past and have always had to compile from source with the nvidia patch ... I did not have to do that this time.  This is the first time everything worked completely and totally like it should.

A complete detail of the steps I took are at [http://www.kevinbridges.org/linuxWoW](http://www.kevinbridges.org/linuxWoW) 

No idea if this the right way to do the installation but I'm to busy playing WoW to worry about it.

---

### Post by Nexxus6 on 2006-10-31
I installed the Nvidia drivers with automatix2 on edgy final and rebooted. Everything appeared fine, Nvidia logo at boot and the desktop looked nice. When I select any of the ubuntu default GL screen savers all I get is a blank screen. I am using an old MSI nvidia geforce 2 pro 64 megs of ram. I tried a fresh install of ubuntu and a manual install the legacy Nvidia drivers but I get the same result? Anyone else having this issue?

---

### Post by Nexxus6 on 2006-10-31
http://www.ubuntuforums.org/showthread.php?t=270014&highlight=gl+screen+saver'
I will try the link above.

---

### Post by tseliot on 2006-10-31
> **Nexxus6 said:**
> I installed the Nvidia drivers with automatix2 on edgy final and rebooted. Everything appeared fine, Nvidia logo at boot and the desktop looked nice. When I select any of the ubuntu default GL screen savers all I get is a blank screen. I am using an old MSI nvidia geforce 2 pro 64 megs of ram. I tried a fresh install of ubuntu and a manual install the legacy Nvidia drivers but I get the same result? Anyone else having this issue?

Try this:
```
sudo aptitude install nvidia-legacy linux-generic nvidia-settings nvidia-xconfig
```

then type:
```
sudo nvidia-xconfig --no-composite
```

---

### Post by pcbroch on 2006-10-31
So i'm having problems with my nvidia card too...  I initally PM'd tseliot, but he suggest I post here instead:

Here's my problem. I have installed ubuntu 6.10 to my Dell laptop (xps m1710) which has an nvidia 7900 go gtx card in it. I am not using the laptop display though, instead I want to use a Dell DFP (2007WFP) connected through DVI to my laptop. The default install is fine and I get video out my dvi to the DFP no problem. But with that much power under the hood, I want to be able to use XGL/Compiz, 3d, etc, which the default 'nv' driver will not give me.

I tried installing nvidia-glx and upon reboot, I can hear the (oh so annoying after 50 reboots) gnome desktop sounds, but I'm left with a blank screen, and my LCD goes into standby, due to lack of signal.

It seems like no matter what I do, Xorg wants to use my built-in laptop display and not my DFP.

I'm sure i'm missing something dumb, but can't for the life of me figure it out.

To this tseliot suggested:

*Try adding this line to the Section Device of your /etc/X11/xorg.conf*
```
Option "UseDisplayDevice" "DFP"
```

I have tried this just now, and I still get a blank screen.  Can anyone help?

---

### Post by Nexxus6 on 2006-10-31
Did a fresh install of edgy then

sudo aptitude install nvidia-legacy linux-generic nvidia-settings nvidia-xconfig

then type:

sudo nvidia-xconfig --no-composite

This caused x to fail. So I did a fresh install of edgy used automatix to install nvidia drivers then did 

sudo nano -w /etc/X11/xorg.conf

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

This worked!

---

### Post by jbtito03 on 2006-11-02
Hi guys..

just switched from fedora to ubuntu. Have to say its quite a piece of a distro.....

Well... everything works fine, just the 3d acc is not working at all.

I am using the legacy drivers, xorg.conf has the "nvidia" driver string and at reboot i see the nvidia logo. But, for example, the screensavers don work at all...

In one forum thread i read something about nvidifb... so i modprobed it.. and now my lsmod says:

Module Size Used by
nvidiafb 58012 0
i2c_algo_bit 9480 1 nvidiafb
nls_utf8 2304 1
nls_cp437 6016 1
vfat 13440 1
fat 54556 1 vfat
binfmt_misc 11784 1
nfsd 231844 13
exportfs 6016 1 nfsd
lockd 65800 2 nfsd
sunrpc 160188 8 nfsd,lockd
cpufreq_userspace 4372 0
cpufreq_stats 5892 0
freq_table 4996 1 cpufreq_stats
cpufreq_powersave 2048 0
cpufreq_ondemand 6944 0
cpufreq_conservative 7200 0
video 16644 0
tc1100_wmi 7428 0
sbs 15776 0
sony_acpi 5516 0
pcc_acpi 13184 0
i2c_ec 5376 1 sbs
hotkey 10660 0
dev_acpi 11140 0
button 7056 0
battery 10756 0
container 4736 0
ac 5892 0
asus_acpi 16792 0
sg 35356 0
sd_mod 21648 2
ipv6 257632 21
dm_mod 60088 4
md_mod 78740 0
lp 11972 0
nvidia 3931148 8
tsdev 8256 0
usb_storage 73408 1
scsi_mod 141320 3 sg,sd_mod,usb_storage
af_packet 21768 2
snd_via82xx 28696 1
gameport 15368 1 snd_via82xx
snd_ac97_codec 96672 1 snd_via82xx
snd_ac97_bus 2432 1 snd_ac97_codec
snd_mpu401_uart 8704 1 snd_via82xx
snd_pcm_oss 46080 0
snd_pcm 80520 3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc 10504 2 snd_via82xx,snd_pcm
snd_mixer_oss 18560 1 snd_pcm_oss
snd_seq_dummy 4100 0
snd_seq_oss 34304 0
snd_seq_midi 9088 0
snd_rawmidi 25600 2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event 7808 2 snd_seq_oss,snd_seq_midi
snd_seq 53360 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 23172 2 snd_pcm,snd_seq
snd_seq_device 8972 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
libusual 15632 1 usb_storage
parport_pc 36132 1
parport 37320 2 lp,parport_pc
i2c_viapro 8980 0
snd 55428 13 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm _oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi ,snd_seq,snd_timer,snd_seq_device
psmouse 40072 0
shpchp 40856 0
pci_hotplug 31284 1 shpchp
usbhid 42464 0
i2c_core 22288 4 nvidiafb,i2c_algo_bit,i2c_ec,i2c_viapro
via_agp 10368 1
agpgart 33456 2 nvidia,via_agp
soundcore 9952 1 snd
rtc 12596 0
serio_raw 7300 0
evdev 10496 1
pcspkr 3072 0
floppy 60676 0
via_rhine 23940 0
mii 6016 1 via_rhine
ext3 138632 2
jbd 55700 1 ext3
ehci_hcd 32520 0
uhci_hcd 23176 0
usbcore 130304 6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic 1536 0
ide_disk 17664 4
ide_cd 32416 1
cdrom 37792 1 ide_cd
via82cxxx 9604 0 [permanent]
generic 4868 0
thermal 14600 0
processor 26028 1 thermal
fan 5124 0
fbcon 40480 0
tileblit 2944 1 fbcon
font 8448 1 fbcon
bitblit 6272 1 fbcon
softcursor 2432 1 bitblit
vesafb 8348 0
capability 5000 0
commoncap 7808 1 capability

but still... no 3d....

can someone help... pleaseee....

Distro... edgy elf 6.10

bye

---

### Post by jbtito03 on 2006-11-02
Okey... one more detail... glxinfo output

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x80 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)

---

### Post by wadeall on 2006-11-02
HELP !

I'm a newbie who foolishly tried to get to clever with Ubuntu and install the latest nvidia drivers in the hope that they would allow me to get the best out of my graphics card.  

I've installed Edgy on my Core2Duo powered computer with a Geforce 7600GS graphics card and a Viewsonic 2025wm monitor.

I had previously had problems with the monitor resolution as this particualr monitor doesnt like being in the default refreshrate of 75Hz in 1680v1050 resolution mode however I had got these fixed.

I attempted your Method 2 and did steps 1-3

I then pressed Control-Alt-F1 and this switched off the graphical interface and took me to a black page with command  text in it (I was in a KDE environmnet i fthis makes a difference - I had expected a simple  command line  box to come up so I could continue rerading the instructions. I then tried to input step 4 but this didnt  work 

So i tried to recover the system and get back to the beginning but I had not created a backup by this  stage.

I themn tried your suggested remedy:
sudo dpkg -reconfigure -phigh xserver-xorg

and it just says:

/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

So what do I  do now????  Apart from rebuild my windows machine.

It's incredibly frustrating for neewbies that Ubuntu still seems to require  alot of  complicatated and error prone coding just to do somethingeally simple like install graphics drivers!

Thanks for any help you can give.

Wade

---

### Post by AceRimmer on 2006-11-03
If I upgraded my 6.06 to 6.10 do I have to redo the video drivers?

---

### Post by wadeall on 2006-11-03
Acerimer  - im  just a newbie  but  it's my understanding that you would need to reinstall the  driveers  when yiu upgrade the  kernal as  with the move to Edgy

---

### Post by tseliot on 2006-11-03
> **AceRimmer said:**
> If I upgraded my 6.06 to 6.10 do I have to redo the video drivers?

How did you install the Nvidia driver?

---

### Post by RockerTux on 2006-11-03
None of the methods work for me. When the driver is installed and activated (after running nvidia-xconfig), X won't run, and its error message says, on Edgy, that the nvidia module type is unknown, or something like that. On previous Ubuntu releases, the error was that the option vt7 was not recognized.
That is, no Ubuntu releases have working 3d accel on my FX5200. Any ideas?

---

### Post by tseliot on 2006-11-04
> **RockerTux said:**
> None of the methods work for me. When the driver is installed and activated (after running nvidia-xconfig), X won't run, and its error message says, on Edgy, that the nvidia module type is unknown, or something like that. On previous Ubuntu releases, the error was that the option vt7 was not recognized.
That is, no Ubuntu releases have working 3d accel on my FX5200. Any ideas?

let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by RockerTux on 2006-11-04
```

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  4 19:11:49 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3188 card 1043,80a3 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,80b0 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0322 card 1682,1351 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfb700000 - 0xfd8fffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe3600000 - 0xf35fffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfc000000/24, 0xe8000000/27, BIOS @ 0xfd800000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdd00000 - 0xfdd000ff (0x100) MX[B]
	[1] -1	0	0xfdf00000 - 0xfdf03fff (0x4000) MX[B]
	[2] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[3] -1	0	0xfd800000 - 0xfd81ffff (0x20000) MX[B](B)
	[4] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[6] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[7] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[8] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[9] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[12] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdd00000 - 0xfdd000ff (0x100) MX[B]
	[1] -1	0	0xfdf00000 - 0xfdf03fff (0x4000) MX[B]
	[2] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[3] -1	0	0xfd800000 - 0xfd81ffff (0x20000) MX[B](B)
	[4] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[6] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[7] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[8] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[9] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[12] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdd00000 - 0xfdd000ff (0x100) MX[B]
	[5] -1	0	0xfdf00000 - 0xfdf03fff (0x4000) MX[B]
	[6] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[7] -1	0	0xfd800000 - 0xfd81ffff (0x20000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce FX 5200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdd00000 - 0xfdd000ff (0x100) MX[B]
	[5] -1	0	0xfdf00000 - 0xfdf03fff (0x4000) MX[B]
	[6] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[7] -1	0	0xfd800000 - 0xfd81ffff (0x20000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdd00000 - 0xfdd000ff (0x100) MX[B]
	[5] -1	0	0xfdf00000 - 0xfdf03fff (0x4000) MX[B]
	[6] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[7] -1	0	0xfd800000 - 0xfd81ffff (0x20000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE8000000
(--) NV(0): MMIO registers at 0xFC000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 30.00-55.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 50.00-150.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(==) NV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfdd00000 - 0xfdd000ff (0x100) MX[B]
	[7] -1	0	0xfdf00000 - 0xfdf03fff (0x4000) MX[B]
	[8] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[9] -1	0	0xfd800000 - 0xfd81ffff (0x20000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe8000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "abnt2"
(**) Generic Keyboard: XkbModel: "abnt2"
(**) Option "XkbLayout" "br"
(**) Generic Keyboard: XkbLayout: "br"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86(abnt2)+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+br+level3(ralt_switch)" };
    xkb_geometry             { include "pc(abnt2)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

With the "nvidia" module enabled and the "dri" option disabled, as the driver documentation says.

And, :rolleyes:, I know using the command line, XD, before Ubuntu, I was at Slackware and Gentoo =P

---

### Post by svzy on 2006-11-04
Whenever I enter```
sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev
```
during method 2 I always get this error```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
so then I tried to run your script. I DL the script and follow the instructions and i get something like "error: envy not found"(I'm not sure what the error is). Can anyone help?

---

### Post by tseliot on 2006-11-05
> **RockerTux said:**
> And, :rolleyes:, I know using the command line, XD, before Ubuntu, I was at Slackware and Gentoo =P

1) Did the Nvidia driver work in Slackware and Gentoo?

2) this is your problem:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

3) can you post the ouput of this command:
```
lspci -n | grep 300
```

---

### Post by tseliot on 2006-11-05
> **svzy said:**
> Whenever I enter```
sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev
```
during method 2 I always get this error```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
so then I tried to run your script. I DL the script and follow the instructions and i get something like "error: envy not found"(I'm not sure what the error is). Can anyone help?

1) What happens if you type:
```
sudo dpkg --configure -a
```

2) Did you install "envy"? Otherwise you shouldn't get that error

---

### Post by AceRimmer on 2006-11-06
> **tseliot said:**
> How did you install the Nvidia driver?

With one of your methods, its been awhile but I installed the Nvidia driver, edited the xorg.conf file and then disabled AGP since it was causing lockups.

---

### Post by uoL on 2006-11-06
Hi i have the same problem of GLX
here's the result of the command

lspci -n | grep 300
01:00.0 0300: 10de:0322 (rev a1)

I have just installed ubuntu 6.10 and I installed nvidia drivers from sinaptyc it didn't work but after modifing xorg.conf 'nv' to 'nvidia' it seems to worked out now but I was trying to run beryl and I get this

uol@tyger:~$ beryl-manager 
uol@tyger:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".



Thanks!

---

### Post by rachii on 2006-11-06
well i had the nvidia driver successfully installed and running great in edgy.  however i was not paying attention today and run updates and got an update for the restricted modules.  so now when x starts i get an error saying the nvidia version doesnt match the kernel version and that no screens were found.

how do i find out what version of the nvidia driver is installed, and how should i get them to work again?  uninstall both and restart? or is there an easier way?

thanks

---

### Post by AceRimmer on 2006-11-07
I went throught the steps of step one on your guide to make sure and it told me I already had the latest driver installed.  

But when I try to run glxgears, which worked perfectly under 6.06, I get this message.
> Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


Also Penguin Racer does't start. 

I am getting higher resolutions and stuff like that, and when I boot I get the nvidia screen before the login screen.

---

### Post by tseliot on 2006-11-07
> **uoL said:**
> Hi i have the same problem of GLX
here's the result of the command

lspci -n | grep 300
01:00.0 0300: 10de:0322 (rev a1)

I have just installed ubuntu 6.10 and I installed nvidia drivers from sinaptyc it didn't work but after modifing xorg.conf 'nv' to 'nvidia' it seems to worked out now but I was trying to run beryl and I get this

uol@tyger:~$ beryl-manager 
uol@tyger:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".



Thanks!

Please, follow every step of method 1 (use the command line instead of Synaptic).

---

### Post by tseliot on 2006-11-07
> **rachii said:**
> well i had the nvidia driver successfully installed and running great in edgy.  however i was not paying attention today and run updates and got an update for the restricted modules.  so now when x starts i get an error saying the nvidia version doesnt match the kernel version and that no screens were found.

how do i find out what version of the nvidia driver is installed, and how should i get them to work again?  uninstall both and restart? or is there an easier way?

thanks

type:
```
sudo aptitude install linux-generic linux-restricted-modules-`uname -r`
```

---

### Post by tseliot on 2006-11-07
> **AceRimmer said:**
> I went throught the steps of step one on your guide to make sure and it told me I already had the latest driver installed.  

But when I try to run glxgears, which worked perfectly under 6.06, I get this message.


Also Penguin Racer does't start. 

I am getting higher resolutions and stuff like that, and when I boot I get the nvidia screen before the login screen.

Did you disable composite in your xorg.conf?

---

### Post by tseliot on 2006-11-07
> **uoL said:**
> Hi i have the same problem of GLX
here's the result of the command

lspci -n | grep 300
01:00.0 0300: 10de:0322 (rev a1)

I have just installed ubuntu 6.10 and I installed nvidia drivers from sinaptyc it didn't work but after modifing xorg.conf 'nv' to 'nvidia' it seems to worked out now but I was trying to run beryl and I get this

uol@tyger:~$ beryl-manager 
uol@tyger:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".



Thanks!

Are you trying to use Composite with driver 8776?

You might need the beta driver to use Beryl and AIGLX

---

### Post by ulriks on 2006-11-07
Having problems with my desktop freezing (apparently from minimising or maximising windows) after an upgrade of the nvidia-glx, I tried to install the driver using envy, which removed my xserver all together...

I am now back to normal, that is a less stable system. 

Any one got any ideas what to do or should I just try a clean install?

Ulrik

---

### Post by d351GuJu on 2006-11-07
Thanks so much for this script, I nearly spent 2 hours trying to solve my widescreen LCD resolution problem after installing nvidia beta drivers.  But envy reinstalled the stable drivers and solved all of my problems in less than 5 minutes!

You are da man!

d351GuJu

---

### Post by christooss on 2006-11-07
I get X crash

It say that nvidia.ko is mising. What can I do? Is a sollution that someone sends me file?

---

### Post by AceRimmer on 2006-11-07
> **tseliot said:**
> Did you disable composite in your xorg.conf?

Here is my file. 

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NvAGP" "0"
    Option         "RenderAccel" "Off"
    Option         "IgnoreDisplayDevices" "DFP,TV"
    Option         "NoRenderExtension" "Off"
    Option         "AllowGLXWithComposite" "Off"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by ulriks on 2006-11-08
I tried one again using the envy-script (this time being pacient), and the NVIDIA driver was installed. My desktop (xserver?) is still as labile as ever and the displayconfig module is not all alright (see attachment). It this because of envy, or something I've done? This also happened when my problems first started, (Saturday, when I upgraded the nvidia-glx).

Anyone with ideas as to why this happens? And what can be done to fix it? Things used to work flawlessly.

I am currently using the nv driver - which it stabile - but make everything seems slow

---

### Post by tseliot on 2006-11-08
> **ulriks said:**
> I tried one again using the envy-script (this time being pacient), and the NVIDIA driver was installed. My desktop (xserver?) is still as labile as ever and the displayconfig module is not all alright (see attachment). It this because of envy, or something I've done? This also happened when my problems first started, (Saturday, when I upgraded the nvidia-glx).
That display config gui is not perfect and IMO you shouldn't use it. It has only caused troubles on my computer.

1) Use the nvidia driver and then post the output of this command:
```
glxinfo | grep direct

```

2) Can you post the output of this command?
```
lspci -n | grep 300
```

---

### Post by RockerTux on 2006-11-08
> **tseliot said:**
> 1) Did the Nvidia driver work in Slackware and Gentoo?

2) this is your problem:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

3) can you post the ouput of this command:
```
lspci -n | grep 300
```
Yes, it did. I could even use XGL on Gentoo and play Doom 3 on Slack =P

I noticed that when I was installing the driver's package, apt-get said that the module was not in the ELF format, something like that. So, maybe that's the problem, isn't it?

And the output of the command you asked me to run:
> arthur@acmasoft:~$ lspci -n | grep 300
01:00.0 0300: 10de:0322 (rev a1)

---

### Post by gumbald on 2006-11-08
> **tseliot said:**
> type:
```
sudo aptitude install linux-generic linux-restricted-modules-`uname -r`
```

I've just had the same problem, that didn't work... Still telling me I got no screen.

---

### Post by gumbald on 2006-11-08
Solved it, for some reason I had booted into the 386 kernel not generic, I'll  edit my Grub settings now...

---

### Post by ulriks on 2006-11-08
glxinfo | grep direct gave:
direct rendering: Yes

lspci -n | grep 300 gave:
01:00.0 0300: 10de:0181 (rev a2)

And this is my xorg.conf (just in case)
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbVariant"	"dk"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Dell E151FPp"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"Dell E151FPp"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

The displayconfig gui may be bad, but why is it gone?

Thanks
Ulrik

---

### Post by tseliot on 2006-11-08
> **ulriks said:**
> glxinfo | grep direct gave:
direct rendering: Yes

lspci -n | grep 300 gave:
01:00.0 0300: 10de:0181 (rev a2)

And this is my xorg.conf (just in case)
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbVariant"	"dk"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Dell E151FPp"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"Dell E151FPp"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

The displayconfig gui may be bad, but why is it gone?

Thanks
Ulrik

I don't know why that gui doesn't work.

Anyway the driver works fine (since direct rendering is enabled)

---

### Post by ulriks on 2006-11-08
> **tseliot said:**
> I don't know why that gui doesn't work.

Anyway the driver works fine (since direct rendering is enabled)

I see... Any ideas why the desktop freezes? and how I can figure out if it really is x that crashes?

---

### Post by tseliot on 2006-11-08
> **ulriks said:**
> I see... Any ideas why the desktop freezes? and how I can figure out if it really is x that crashes?

Try point 4 of the problems Section of my guide.

and see if it fixes the problem

---

### Post by tseliot on 2006-11-08
[COLOR="Red"]**UPDATE: Envy 0.7.1 has been released.**[/COLOR]
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

P.S. it supports driver 9629

---

### Post by christooss on 2006-11-08
Any solutions for my missing .ko file?

---

### Post by RockerTux on 2006-11-08
Any ideas on my problem? =P

---

### Post by AceRimmer on 2006-11-09
I did a upgrade from 6.06 so I wonder if I would be better off doing a completely new install to get it working properly?

---

### Post by tseliot on 2006-11-09
> **AceRimmer said:**
> Here is my file. 


Try this:
```
sudo nvidia-xconfig --no-composite
```

---

### Post by tseliot on 2006-11-09
> **christooss said:**
> I get X crash

It say that nvidia.ko is mising. What can I do? Is a sollution that someone sends me file?

How did you install the driver?

---

### Post by tseliot on 2006-11-09
> **RockerTux said:**
> With the "nvidia" module enabled and the "dri" option disabled, as the driver documentation says.

And, :rolleyes:, I know using the command line, XD, before Ubuntu, I was at Slackware and Gentoo =P

Try this:
```
sudo nvidia-xconfig --no-composite
```

and then restart the Xserver (do not touch anything else)

---

### Post by AceRimmer on 2006-11-09
> **tseliot said:**
> Try this:
```
sudo nvidia-xconfig --no-composite
```

What exactly does that do?  does it cause any performance hits or disable any features?

Thanks for the help!

---

### Post by tseliot on 2006-11-09
> **AceRimmer said:**
> What exactly does that do?  does it cause any performance hits or disable any features?

Thanks for the help!

It disables the Composite extension. It won't decrease the performance of your card. Don't worry.

---

### Post by ulriks on 2006-11-09
> **tseliot said:**
> Try point 4 of the problems Section of my guide.

and see if it fixes the problem

It appears to be working! Thanks!

Why is it that

```
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" "Off"
```

Did the trick?

---

### Post by christooss on 2006-11-09
> **tseliot said:**
> How did you install the driver?

It happened after installing official drivers from Nvidia.com after that I installed drivers through apt-get install nvidia-glx from different repositories and even with Envy script but none fixed the crash

---

### Post by tseliot on 2006-11-09
> **ulriks said:**
> It appears to be working! Thanks!

Why is it that

```
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" "Off"
```

Did the trick?
Maybe the AGP was causing the problem

---

### Post by tseliot on 2006-11-09
> **christooss said:**
> It happened after installing official drivers from Nvidia.com after that I installed drivers through apt-get install nvidia-glx from different repositories and even with Envy script but none fixed the crash

You might have caused a mess.

Do you use a wireless card to connect to the Internet?

---

### Post by christooss on 2006-11-09
nope

---

### Post by RockerTux on 2006-11-09
> **tseliot said:**
> Try this:
```
sudo nvidia-xconfig --no-composite
```

and then restart the Xserver (do not touch anything else)

Not working, again...

```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(EE) /usr/lib/xorg/modules/drivers/nvidia_drv.so is an unrecognized 
module type
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (unknown module type, 6)
```

---

### Post by AceRimmer on 2006-11-09
> **tseliot said:**
> It disables the Composite extension. It won't decrease the performance of your card. Don't worry.

That worked.  You are the man.

Nvidia drivers must be a lot better than ATI.  This computer is an Athlon XP 2200+ @1.8Ghz with a GeForce 6600GT card and it runs the demo faster than my Athlon64 @ 2.25Ghz with an ATI X800GTO modded to 16 pipes.  The ATI machine is significantly faster in Windows.

---

### Post by tseliot on 2006-11-10
> **RockerTux said:**
> Not working, again...

```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(EE) /usr/lib/xorg/modules/drivers/nvidia_drv.so is an unrecognized 
module type
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (unknown module type, 6)
```
Can I see the full output of the error?

---

### Post by tseliot on 2006-11-10
> **christooss said:**
> nope

!) uninstall the driver from Envy
2) uninstall the restricted modules:
```
sudo aptitude purge linux-restricted-modules-`uname -r`
```

3) install the driver by using Envy

---

### Post by RockerTux on 2006-11-10
> **tseliot said:**
> Can I see the full output of the error?

How can I log GDM's error messages? This one was copied char by char =P

---

### Post by tseliot on 2006-11-10
> **RockerTux said:**
> How can I log GDM's error messages? This one was copied char by char =P

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by RockerTux on 2006-11-10
So I can only log startx messages... anyway, it's exactly the same error I posted some pages before.

---

### Post by tseliot on 2006-11-10
> **RockerTux said:**
> So I can only log startx messages... anyway, it's exactly the same error I posted some pages before.

are you sure?

The composite extension should be disabled this time.

---

### Post by brottman on 2006-11-10
If I may ask please, why is your script removing the restricted modules? Is there a reason to remove the restricted modules that I do not fully understand yet?

I install my nvidia drivers by downloading the driver file itself and running the official nvidia install script.

```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo /etc/init.d/gdm start
```

I do not remove my restricted modules (I need em for wireless) and my laptop runs great with the new nvidia drivers.

---

### Post by tseliot on 2006-11-10
> **brottman said:**
> If I may ask please, why is your script removing the restricted modules? Is there a reason to remove the restricted modules that I do not fully understand yet?

I install my nvidia drivers by downloading the driver file itself and running the official nvidia install script.

```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo /etc/init.d/gdm start
```

I do not remove my restricted modules (I need em for wireless) and my laptop runs great with the new nvidia drivers.

Envy 0.7.1 does NOT remove the restricted-modules.

The only package which is removed is nvidia-glx

EDIT: the only 2 versions of Envy which you can download do not remove the restricted modules.

EDIT2: I see what you mean... I have just removed the (useless and out-of-date) warning in the main thread.

---

### Post by brottman on 2006-11-10
Ok, thanks :)

---

### Post by RockerTux on 2006-11-10
> **tseliot said:**
> are you sure?

The composite extension should be disabled this time.

Yeah... module not recognized, and that stuff. I tried using a working xorg.conf from a Gentoo box, same error.

---

### Post by tseliot on 2006-11-10
> **RockerTux said:**
> Yeah... module not recognized, and that stuff. I tried using a working xorg.conf from a Gentoo box, same error.

I can only suggest you to ask for help here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by hotttoddie on 2006-11-12
Having troubles with my Edgy Eft / NVidia installation.  The "NV" driver never seems to work - I just get garbage video on my screen at any resolution.  So installed the Nvidia drivers using the Envy perl script...  That didnt work either...  My system starts up and I can see the Ubuntu loading screen and then the test for a fsck check but then my monitor goes to stanby mode... Ive tried several screen modes at different depths and refresh rates with no success.

Here is my motherboard [http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?DetailID=422](http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?DetailID=422)

I have a FX5200 card 

Here is my [xorg.conf]("http://todd.gatorline.com/xorg.conf.txt")

Here is my verbose level 5 output from the [startx]("http://todd.gatorline.com/startxoutput.txt")

  Any help would be amazing...

-Todd

---

### Post by tseliot on 2006-11-12
> **hotttoddie said:**
> Having troubles with my Edgy Eft / NVidia installation.  The "NV" driver never seems to work - I just get garbage video on my screen at any resolution.  So installed the Nvidia drivers using the Envy perl script...  That didnt work either...  My system starts up and I can see the Ubuntu loading screen and then the test for a fsck check but then my monitor goes to stanby mode... Ive tried several screen modes at different depths and refresh rates with no success.

Here is my motherboard [http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?DetailID=422](http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?DetailID=422)

I have a FX5200 card 

Here is my [xorg.conf]("http://todd.gatorline.com/xorg.conf.txt")

Here is my verbose level 5 output from the [startx]("http://todd.gatorline.com/startxoutput.txt")

  Any help would be amazing...

-Todd

can you post the content of your /etc/X11/xorg.conf ?

---

### Post by xi0nic on 2006-11-12
**tseliot** -  Thank you so much for this script. I just ran it on my fresh Edgy install, 32bit, running a (old-as-dirt) Ti4600. Worked flawlessly.

<3

edit: having glx issues, cannot run glxgears or glxinfo! =X

---

### Post by tseliot on 2006-11-12
> **xi0nic said:**
> **tseliot** -  Thank you so much for this script. I just ran it on my fresh Edgy install, 32bit, running a (old-as-dirt) Ti4600. Worked flawlessly.

<3

edit: having glx issues, cannot run glxgears or glxinfo! =X

It might be a bug of the latest driver (which might cause problems with Geforce 4 cards).

Use the "uninstall" function of Envy and **then** follow Method 1 of my guide (so as to install driver 8776):
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by xi0nic on 2006-11-12
> **tseliot said:**
> It might be a bug of the latest driver (which might cause problems with Geforce 4 cards).

Use the "uninstall" function of Envy and **then** follow Method 1 of my guide (so as to install driver 8776):
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Rgr, will do! Thanks =D

---

### Post by hotttoddie on 2006-11-12
> **tseliot said:**
> can you post the content of your /etc/X11/xorg.conf ?

The xorg.conf and the startx log are hyperlinked in my orginal post...  

Here are my xorg.conf and my startx-verbose5 logs
```

-toddmc@goose:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:47:17 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       35.0 - 60.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth   16
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "640x480_60" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```







***********************

---

### Post by hotttoddie on 2006-11-12
> **tseliot said:**
> can you post the content of your /etc/X11/xorg.conf ?

Following up with my startx verbose log output:

```
toddmc@goose:~$ sudo startx -- -verbose 5 -logverbose 5
xauth:  creating new authority file /home/toddmc/.serverauth.12122

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux goose 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 12 01:47:42 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/TTF/,
        /usr/share/fonts/X11/OTF,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/CID/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.0
        X.Org XInput driver : 0.6
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7


(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0741 card 1019,1b13 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1019,1b13 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:6: chip 1039,7013 card 1019,0c04 rev a0 class 07,03,00 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1019,1b13 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1019,1b13 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1019,1b13 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1019,1b13 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1019,1b13 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1019,1b13 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:09:0: chip 3388,0021 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 01:00:0: chip 10de,0322 card 10de,01b9 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe9000000 - 0xeaffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:9:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xe9000000/24, 0xd8000000/27
(--) PCI: (2:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xe0000000/26
(--) PCI: (2:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xe4000000/26
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [1] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [2] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [3] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [4] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [5] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [6] -1  0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [7] -1  0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [8] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [11] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [12] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [13] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [14] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [15] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [1] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [2] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [3] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [4] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [5] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [6] -1  0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [7] -1  0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [8] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [11] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [12] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [13] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [14] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [15] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [5] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [6] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [7] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [8] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [9] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [10] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [13] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [19] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [20] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [21] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.1.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9629  Wed Nov  1 19:31:54 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) NVIDIA(0): Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [5] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [6] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [7] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [8] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [9] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [10] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [13] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [19] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [20] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [21] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [5] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [6] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [7] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [8] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [9] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [10] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [13] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [14] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [15] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [16] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [20] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [21] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [22] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [23] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [24] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
        [25] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [26] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x83e
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(II) NVIDIA(0): GPU Architecture: 0x30
(II) NVIDIA(0): GPU Implementation: 0x34
(II) NVIDIA(0): GPU Revision: 0xa2
(--) NVIDIA(0): VideoBIOS: 04.34.20.22.bc
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0):
(II) NVIDIA(0): Mode timing constraints for  : GeForce FX 5200
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0):
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0):
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0):
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Samsung 570V TFT (CRT-1)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0):
(--) NVIDIA(0): --- EDID for CRT-0 ---
(--) NVIDIA(0):
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0):
(--) NVIDIA(0): --- End of EDID for CRT-0 ---
(--) NVIDIA(0):
(--) NVIDIA(0): Samsung 570V TFT (CRT-1): 350.0 MHz maximum pixel clock
(--) NVIDIA(0):
(--) NVIDIA(0): --- EDID for Samsung 570V TFT (CRT-1) ---
(--) NVIDIA(0): EDID Version                 : 1.2
(--) NVIDIA(0): Manufacturer                 : SAM
(--) NVIDIA(0): Monitor Name                 : Samsung 570V TFT
(--) NVIDIA(0): Product ID                   : 2
(--) NVIDIA(0): 32-bit Serial Number         : 1129197877
(--) NVIDIA(0): Serial Number String         : HCLR801932
(--) NVIDIA(0): Manufacture Date             : 2001, week 32
(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 300mm x 230mm
(--) NVIDIA(0): Valid HSync Range            : 30 kHz - 61 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 50 Hz - 75 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 80.0 MHz
(--) NVIDIA(0):
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 56 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 70 Hz
(--) NVIDIA(0):
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0):
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 65.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1024, 1048
(--) NVIDIA(0):     HSyncEnd, HTotal : 1184, 1344
(--) NVIDIA(0):     VRes, VSyncStart : 768, 771
(--) NVIDIA(0):     VSyncEnd, VTotal : 777, 806
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):
(--) NVIDIA(0): --- End of EDID for Samsung 570V TFT (CRT-1) ---
(--) NVIDIA(0):
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): TV modes supported by this encoder:
(II) NVIDIA(0):   1024x768; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI,
(II) NVIDIA(0):     PAL-N, PAL-NC
(II) NVIDIA(0):   800x600; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   720x576; Standards: PAL-BDGHI, PAL-N, PAL-NC
(II) NVIDIA(0):   720x480; Standards: NTSC-M, NTSC-J, PAL-M
(II) NVIDIA(0):   640x480; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   640x400; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   400x300; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   320x240; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   320x200; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0): Frequency information for CRT-0:
(II) NVIDIA(0):   HorizSync   : 35.000-60.000 kHz
(II) NVIDIA(0):   VertRefresh : 60.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
(II) NVIDIA(0):
(II) NVIDIA(0): --- Modes in ModePool for CRT-0 ---
(II) NVIDIA(0): "nvidia-auto-select" : 1024 x  768 @  75.0 Hz  (from: VESA)
(II) NVIDIA(0): "1440x900"           : 1440 x  900 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x800"           : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x800_60"        : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768"           : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768_60"        : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  75.0 Hz  (from: VESA)
(II) NVIDIA(0): "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: VESA)
(II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "832x624"            :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "800x600"            :  800 x  600 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "720x450"            :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"         :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: VESA)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x400"            :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x400d60"         :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384"            :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384d60"         :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for CRT-0: ---
(II) NVIDIA(0):
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "640x480_60"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(WW) NVIDIA(0): No valid modes for "640x480_60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1024x768":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1024, 768]
(II) NVIDIA(0):     CRT-0: "1024x768"
(II) NVIDIA(0):         Size          : 1024 x 768
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1024 x 768
(II) NVIDIA(0):         Position      : [0, 0, 1024, 768]
(II) NVIDIA(0): MetaMode "800x600":
(II) NVIDIA(0):     Bounding Box: [0, 0, 800, 600]
(II) NVIDIA(0):     CRT-0: "800x600"
(II) NVIDIA(0):         Size          : 800 x 600
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 800 x 600
(II) NVIDIA(0):         Position      : [0, 0, 800, 600]
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(II) NVIDIA(0):
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0):
(II) NVIDIA(0): "1024x768_70" : 1024 x  768 @  70.1 Hz
(II) NVIDIA(0): "1024x768_60" : 1024 x  768 @  60.0 Hz
(II) NVIDIA(0): "832x624"     :  832 x  624 @  74.5 Hz
(II) NVIDIA(0): "800x600_72"  :  800 x  600 @  72.2 Hz
(II) NVIDIA(0): "800x600_60"  :  800 x  600 @  60.3 Hz
(II) NVIDIA(0): "720x450"     :  720 x  450 @  60.2 Hz DoubleScan
(II) NVIDIA(0): "640x480"     :  640 x  480 @  75.0 Hz
(II) NVIDIA(0): "640x480_73"  :  640 x  480 @  72.8 Hz
(II) NVIDIA(0): "640x480d60"  :  640 x  480 @  60.0 Hz DoubleScan
(II) NVIDIA(0): "640x400"     :  640 x  400 @  60.0 Hz DoubleScan
(II) NVIDIA(0): "640x384"     :  640 x  384 @  60.1 Hz DoubleScan
(II) NVIDIA(0): "512x384"     :  512 x  384 @  75.1 Hz DoubleScan
(II) NVIDIA(0): "512x384d70"  :  512 x  384 @  70.1 Hz DoubleScan
(II) NVIDIA(0): "512x384d60"  :  512 x  384 @  60.0 Hz DoubleScan
(II) NVIDIA(0): "416x312"     :  416 x  312 @  74.7 Hz DoubleScan
(II) NVIDIA(0): "400x300"     :  400 x  300 @  75.1 Hz DoubleScan
(II) NVIDIA(0): "400x300d72"  :  400 x  300 @  72.2 Hz DoubleScan
(II) NVIDIA(0): "400x300d60"  :  400 x  300 @  60.3 Hz DoubleScan
(II) NVIDIA(0): "320x240"     :  320 x  240 @  75.0 Hz DoubleScan
(II) NVIDIA(0): "320x240d73"  :  320 x  240 @  72.8 Hz DoubleScan
(II) NVIDIA(0):
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd8000000 - 0xdfffffff (0x8000000) MX[B]
        [1] 0   0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [7] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [8] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [9] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [10] -1 0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [11] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [12] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [13] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [14] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [15] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [22] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [23] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [24] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [25] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [26] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
        [27] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [28] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): CRT-0 assigned CRTC 0
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(**) Option "Device" "/dev/input/mice"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!



```

---

### Post by tseliot on 2006-11-13
> **hotttoddie said:**
> Following up with my startx verbose log output:
Try adding this to the Section screen of your xorg.conf:
```
Option "UseEDID" "False"
```

---

### Post by oliwally on 2006-11-13
I can't get Nvidia going on the edgy generic kernel.

[B]EDIT: 

         OOPS! All started working after I updated everything using Synaptic. How embarrassing. Left my problem listed below in case others have the same (silly) problem.
[/B]

Problem was:

I'm trying to get Nvidia going on my Dell D820, with Nvidia Quadro NVS 120 and 1920x1200 screen. Running the generic kernel and also the 386 keernel (although not sure how the 386 got there - got installed with my nvidia trials I think).

Most of the downloading was done over wireless (I saw on previous posts that this may make a difference?)

I have tried various methods, including the envy script (did not work - seemed to do nothing ?)

I used Method 1 and had some success, but only when booting the 386 kernel. (Yes, made sure I installed linux-generic). Nvidia splash screen comes up and all seems well.

But when booting the generic kernel, the X server fails. I'm presented with a shell in which I can log in.

When typing "startx" I'm presented with something like the following error:

```
Error: API Mismatch: NVIDIA kernel module has the version 1.0-8774,
 but this x module has the version 1.0-7886. Please make sure that the 
kernel module and all NVIDIA driver components have the same version.
Failed to initialize the NVIDIA kernel module! Please ensure that the
 NVIDIA device files have been created properly.
```

There is some other text as well about a log file, but I thought the above would be the most important.

All fixed after updating system using Synaptic. NVIDIA fully working.

---

### Post by peebly on 2006-11-13
thanks you for this, it worked perfectly on my computer.

easily the best way so far to install the nvidia drivers in my opinion.

and I even have a nvidia control panel.

cheers mate:KS

---

### Post by oliwally on 2006-11-13
Why is it that once the NVIDIA drivers are running, a lot of things seem larger - fonts, icons and menus appear to be a bit bigger, although the screen size is still 1920x1200 (on mine) as before, and the font and icon settings don't seem to have changed either.

---

### Post by SpikeyMike on 2006-11-13
Hi

I am trying to install the Nvidia drivers using this guide but I get an error at the first step, after typing 'sudo apt-get install linux-generic I get the following error:

root@MikeysUbuntu:/home/mikey# sudo apt-get install linux-generic
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@MikeysUbuntu:/home/mikey# 

any idea what is causing this?

Regards

Spikey

---

### Post by hotttoddie on 2006-11-13
> **SpikeyMike said:**
> Hi

I am trying to install the Nvidia drivers using this guide but I get an error at the first step, after typing 'sudo apt-get install linux-generic I get the following error:

root@MikeysUbuntu:/home/mikey# sudo apt-get install linux-generic
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@MikeysUbuntu:/home/mikey# 

any idea what is causing this?

Regards

Spikey

make sure you arent running synaptic in the background or using automatix, etc...  its complaining that it cant get a lock on the apt DB... you need to make sure no one else is using it...

---

### Post by SpikeyMike on 2006-11-13
Hi Hottoddie

I had synaptic running in the background :-O

thanks for your help

Spikey

---

### Post by SpikeyMike on 2006-11-13
hi hi

I now have another problem, part of the installation involves using ctrl+alt+f1 to go to a command line, I did this but now I can't get back to the desktop, I have tried ctrl+alt+backspace but it doesn't work, I am using Edgy btw, help

Spikey

---

### Post by tseliot on 2006-11-13
> **SpikeyMike said:**
> hi hi

I now have another problem, part of the installation involves using ctrl+alt+f1 to go to a command line, I did this but now I can't get back to the desktop, I have tried ctrl+alt+backspace but it doesn't work, I am using Edgy btw, help

Spikey
Please, avoid Method 2. It's not for beginners.

You might try Envy 0.7.1 or Method 1 instead.

Type this to get back to your desktop environment:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

---

### Post by hotttoddie on 2006-11-14
> **tseliot said:**
> Try adding this to the Section screen of your xorg.conf:
```
Option "UseEDID" "False"
```

Nope - Same result - Monitory goes to standby with no output.  Am still able to swith to the other virtual text teminals just fine though...

Here is my xorg.conf:
```
toddmc@goose:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:47:17 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       35.0 - 60.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"

    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth   16
    Option "UseEDID" "False"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "640x480_60" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection


```


And here is my Xorg.0.log from the output of: $ sudo startx -- -verbose 5 -logverbose 5

```
toddmc@goose:~$ cat /var/log/Xorg.0.log

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux goose 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 13 23:02:09 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/TTF/,
        /usr/share/fonts/X11/OTF,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/CID/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.0
        X.Org XInput driver : 0.6
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0741 card 1019,1b13 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1019,1b13 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:6: chip 1039,7013 card 1019,0c04 rev a0 class 07,03,00 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1019,1b13 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1019,1b13 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1019,1b13 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1019,1b13 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1019,1b13 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1019,1b13 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:09:0: chip 3388,0021 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 01:00:0: chip 10de,0322 card 10de,01b9 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe9000000 - 0xeaffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:9:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xe9000000/24, 0xd8000000/27
(--) PCI: (2:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xe0000000/26
(--) PCI: (2:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xe4000000/26
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [1] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [2] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [3] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [4] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [5] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [6] -1  0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [7] -1  0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [8] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [11] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [12] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [13] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [14] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [15] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [1] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [2] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [3] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [4] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [5] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [6] -1  0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [7] -1  0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [8] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [11] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [12] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [13] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [14] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [15] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [5] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [6] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [7] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [8] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [9] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [10] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [13] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [19] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [20] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [21] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.1.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9629  Wed Nov  1 19:31:54 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) NVIDIA(0): Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [5] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [6] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [7] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [8] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [9] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [10] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [13] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [19] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [20] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [21] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [5] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [6] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [7] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [8] -1  0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [9] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [10] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [13] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [14] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [15] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [16] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [20] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [21] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [22] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [23] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [24] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
        [25] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [26] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "False"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x83e
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(GPU-0): Not probing EDID on CRT-0.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(II) NVIDIA(0): GPU Architecture: 0x30
(II) NVIDIA(0): GPU Implementation: 0x34
(II) NVIDIA(0): GPU Revision: 0xa2
(--) NVIDIA(0): VideoBIOS: 04.34.20.22.bc
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0):
(II) NVIDIA(0): Mode timing constraints for  : GeForce FX 5200
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0):
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0):
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0):
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0):
(--) NVIDIA(0): --- EDID for CRT-0 ---
(--) NVIDIA(0):
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0):
(--) NVIDIA(0): --- End of EDID for CRT-0 ---
(--) NVIDIA(0):
(--) NVIDIA(0): CRT-1: 350.0 MHz maximum pixel clock
(--) NVIDIA(0):
(--) NVIDIA(0): --- EDID for CRT-1 ---
(--) NVIDIA(0):
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0):
(--) NVIDIA(0): --- End of EDID for CRT-1 ---
(--) NVIDIA(0):
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): TV modes supported by this encoder:
(II) NVIDIA(0):   1024x768; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI,
(II) NVIDIA(0):     PAL-N, PAL-NC
(II) NVIDIA(0):   800x600; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   720x576; Standards: PAL-BDGHI, PAL-N, PAL-NC
(II) NVIDIA(0):   720x480; Standards: NTSC-M, NTSC-J, PAL-M
(II) NVIDIA(0):   640x480; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   640x400; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   400x300; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   320x240; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   320x200; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0): Frequency information for CRT-0:
(II) NVIDIA(0):   HorizSync   : 35.000-60.000 kHz
(II) NVIDIA(0):   VertRefresh : 60.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
(II) NVIDIA(0):
(II) NVIDIA(0): --- Modes in ModePool for CRT-0 ---
(II) NVIDIA(0): "nvidia-auto-select" : 1024 x  768 @  75.0 Hz  (from: VESA)
(II) NVIDIA(0): "1440x900"           : 1440 x  900 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x800"           : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x800_60"        : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768"           : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768_60"        : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  75.0 Hz  (from: VESA)
(II) NVIDIA(0): "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: VESA)
(II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "832x624"            :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "800x600"            :  800 x  600 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "720x450"            :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"         :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: VESA)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x400"            :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x400d60"         :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384"            :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384d60"         :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for CRT-0: ---
(II) NVIDIA(0):
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "640x480_60"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(WW) NVIDIA(0): No valid modes for "640x480_60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1024x768":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1024, 768]
(II) NVIDIA(0):     CRT-0: "1024x768"
(II) NVIDIA(0):         Size          : 1024 x 768
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1024 x 768
(II) NVIDIA(0):         Position      : [0, 0, 1024, 768]
(II) NVIDIA(0): MetaMode "800x600":
(II) NVIDIA(0):     Bounding Box: [0, 0, 800, 600]
(II) NVIDIA(0):     CRT-0: "800x600"
(II) NVIDIA(0):         Size          : 800 x 600
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 800 x 600
(II) NVIDIA(0):         Position      : [0, 0, 800, 600]
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(II) NVIDIA(0):
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0):
(II) NVIDIA(0): "1024x768_70" : 1024 x  768 @  70.1 Hz
(II) NVIDIA(0): "1024x768_60" : 1024 x  768 @  60.0 Hz
(II) NVIDIA(0): "832x624"     :  832 x  624 @  74.5 Hz
(II) NVIDIA(0): "800x600_72"  :  800 x  600 @  72.2 Hz
(II) NVIDIA(0): "800x600_60"  :  800 x  600 @  60.3 Hz
(II) NVIDIA(0): "720x450"     :  720 x  450 @  60.2 Hz DoubleScan
(II) NVIDIA(0): "640x480"     :  640 x  480 @  75.0 Hz
(II) NVIDIA(0): "640x480_73"  :  640 x  480 @  72.8 Hz
(II) NVIDIA(0): "640x480d60"  :  640 x  480 @  60.0 Hz DoubleScan
(II) NVIDIA(0): "640x400"     :  640 x  400 @  60.0 Hz DoubleScan
(II) NVIDIA(0): "640x384"     :  640 x  384 @  60.1 Hz DoubleScan
(II) NVIDIA(0): "512x384"     :  512 x  384 @  75.1 Hz DoubleScan
(II) NVIDIA(0): "512x384d70"  :  512 x  384 @  70.1 Hz DoubleScan
(II) NVIDIA(0): "512x384d60"  :  512 x  384 @  60.0 Hz DoubleScan
(II) NVIDIA(0): "416x312"     :  416 x  312 @  74.7 Hz DoubleScan
(II) NVIDIA(0): "400x300"     :  400 x  300 @  75.1 Hz DoubleScan
(II) NVIDIA(0): "400x300d72"  :  400 x  300 @  72.2 Hz DoubleScan
(II) NVIDIA(0): "400x300d60"  :  400 x  300 @  60.3 Hz DoubleScan
(II) NVIDIA(0): "320x240"     :  320 x  240 @  75.0 Hz DoubleScan
(II) NVIDIA(0): "320x240d73"  :  320 x  240 @  72.8 Hz DoubleScan
(II) NVIDIA(0):
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd8000000 - 0xdfffffff (0x8000000) MX[B]
        [1] 0   0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xeb002000 - 0xeb002fff (0x1000) MX[B]
        [7] -1  0       0xeb001000 - 0xeb001fff (0x1000) MX[B]
        [8] -1  0       0xeb000000 - 0xeb000fff (0x1000) MX[B]
        [9] -1  0       0xeb004000 - 0xeb004fff (0x1000) MX[B]
        [10] -1 0       0xeb003000 - 0xeb003fff (0x1000) MX[B]
        [11] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [12] -1 0       0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
        [13] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [14] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [15] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [22] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [23] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [24] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [25] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [26] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
        [27] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [28] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): CRT-0 assigned CRTC 0
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/input/mice"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
toddmc@goose:~$

```

---

### Post by Lester King on 2006-11-14
> **oliwally said:**
> I can't get Nvidia going on the edgy generic kernel.

[B]EDIT: 

         OOPS! All started working after I updated everything using Synaptic. How embarrassing. Left my problem listed below in case others have the same (silly) problem.
[/B]



Oli, I'm getting the same error. What exactly did you do with synaptic to fix it?

---

### Post by tseliot on 2006-11-14
> **hotttoddie said:**
> Nope - Same result - Monitory goes to standby with no output.  Am still able to swith to the other virtual text teminals just fine though...

Here is my xorg.conf:

Try point 4 of the Problems Section of my guide.

---

### Post by hotttoddie on 2006-11-15
> **tseliot said:**
> Try point 4 of the Problems Section of my guide.


Nope - no go, same result - I give up!  Im going to try an ATI card I have lying around... Thank you for your help and time TSELIOT - If anyone has experienced the same problems I have, please PM me and let me know the result

---

### Post by christooss on 2006-11-15
tseliot is there envy which instals 9625. There is a bug for nv2x cards in 9629. Or maybe a repositorie from which I can install old dirvers?

---

### Post by oliwally on 2006-11-15
> **Lester King said:**
> Oli, I'm getting the same error. What exactly did you do with synaptic to fix it?

In Synaptic I clicked the "Mark All Upgrades" button, chose the 'Smart Upgrade' option (default option), and clicked 'Apply'.

After the upgrade, everything started working as it should, although I can't remember if I had to go through the steps of Method 1 again.

After that I rebooted and all was well.

---

### Post by dreadnought on 2006-11-15
Hi tseliot,

I am capable of manual installation but feeling lazy I decided to try out Envy and am very happy to report all went well and I have Nvidia running on my Edgy amd64 install.


This is the sort of tool I like best, It does one thing and does it well.
Many thanks Please keep up the good work.
:):):)

---

### Post by tseliot on 2006-11-15
> **christooss said:**
> tseliot is there envy which instals 9625. There is a bug for nv2x cards in 9629. Or maybe a repositorie from which I can install old dirvers?

Try Envy Unstable 0.6.1

---

### Post by tseliot on 2006-11-15
> **hotttoddie said:**
> Nope - no go, same result - I give up!  Im going to try an ATI card I have lying around... Thank you for your help and time TSELIOT - If anyone has experienced the same problems I have, please PM me and let me know the result

you might try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Scimon on 2006-11-16
Just to say I just tried the Envy script and it ran like a charm. My machine did have some weird graphical glitches (which considering it was fresh out of the box on Monday was a bit annoying).

Now to see what else I can do with it. Or maybe get some work done.

---

### Post by christooss on 2006-11-16
Tseilot 0.6.1 works perfectly

I really hope that nv20 cards will be supported in future

---

### Post by peebly on 2006-11-16
hello

Will this script work with Kubuntu.

---

### Post by tseliot on 2006-11-16
> **peebly said:**
> hello

Will this script work with Kubuntu.

yes, of course

---

### Post by pjman on 2006-11-16
Having trouble installing the newest (non-beta) Nvidia drivers, 9629. I've tried installing both manually and using the envy script. Glxinfo gives me "segmentation fault (core dump)". If I run any app that uses 3D it crashes. 

At first I thought I was having this trouble because I upgraded from Dapper to Edgy. Well last night I installed a fresh copy of Edgy and the problem is still there. My video card is a Ti-4200. Someone on a different thread with a Ti-4200 is having a similar issue. 

[http://ubuntuforums.org/showpost.php?p=1763930&postcount=1056](http://ubuntuforums.org/showpost.php?p=1763930&postcount=1056)

Could the 9629 drivers be buggy with the Ti-4200? 

I'll try the 8776 drivers tonight.

Thanks!
Travis

**EDIT**

It's a bug: [http://www.nvnews.net/vbulletin/showthread.php?t=79792](http://www.nvnews.net/vbulletin/showthread.php?t=79792)

Time to downgrade :-(

---

### Post by Spare Tire on 2006-11-16
This information might come in handy to some people:
For me, since ownership of xorg.conf is root, you must be running NVIDIA X Server Settings as root if you want to save your configuration. So if your settings volatilize each time, try that.

problem 1:
Now my problem is, it saves to the xorg.conf, but each time ubuntu loads, it still loads the setting i set with the tool in system > preferences > screen resolutions. How do i dissable this override, if it's an override of the NVIDIA configurations.

problem 2:
The text-only console you get to with ctrl+alt+F2 does not display properly. At first, it does not display anything, if you switch back with ctrl+alt+F7 and then back agin into text console with ctrl+alt+F2, it will work, but the display is full of scanlines and it goes off the screen at the bottom. How do i fix this, what were the settings before i installed NVIDIA drivers? Because those worked perfectly in the console. Maybe if i knew what parameters in xorg.conf affects the console, i could set it back to what it was.

---

### Post by Satellite1410 on 2006-11-17
aaaa I got the 9629 nvidia driver to work on my Satellite1410 :) 

Download Phoenix EDID editor and switch to windows (if you can)
and import the EDID from the windows registry
then export it to tos5082.raw (or something)
copy the file to /etc/X11/tos5082.raw
and add this to your xorg.conf file:

Section "Device"

Option "UseDisplayDevice" "DFP-0"
Option "CustomEDID" "DFP-0:/etc/X11/tos5082.raw"


[http://www.nvnews.net/vbulletin/showthread.php?t=80317](http://www.nvnews.net/vbulletin/showthread.php?t=80317)

---

### Post by tseliot on 2006-11-18
> **Spare Tire said:**
> problem 2:
The text-only console you get to with ctrl+alt+F2 does not display properly. At first, it does not display anything, if you switch back with ctrl+alt+F7 and then back agin into text console with ctrl+alt+F2, it will work, but the display is full of scanlines and it goes off the screen at the bottom. How do i fix this, what were the settings before i installed NVIDIA drivers? Because those worked perfectly in the console. Maybe if i knew what parameters in xorg.conf affects the console, i could set it back to what it was.
Try point 13 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION)

but instead of removing splash you might need to add vga=791 (or vga=792)

---

### Post by pumo on 2006-11-18
> **tseliot said:**
> you might try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have same problem like hotttdottie with geforce 6600, but I don' have ati. so must "fight" with nvidia...
black screen after usplash and can't even reboot with keyboard.
I have tested with kernels 2.6.17-10-generic, 2.6.17-10-386 and 2.6.17-10-generic (k7). every steps with your howto.

in dapper it worked like a glove...

---

### Post by tseliot on 2006-11-18
> **pumo said:**
> I have same problem like hotttdottie with geforce 6600, but I don' have ati. so must "fight" with nvidia...
black screen after usplash and can't even reboot with keyboard.
I have tested with kernels 2.6.17-10-generic, 2.6.17-10-386 and 2.6.17-10-generic (k7). every steps with your howto.

in dapper it worked like a glove...

try point 4 of the Problems Section

---

### Post by adamkat on 2006-11-20
I am sorry I am  such a newbie but I did not pass the first step.
I went to the site and downloaded:
> [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.2-0ubuntu1_all.deb)
now it says:
> Download and install the deb package
how do I install the deb package?
I appreciate your help and would also want to see idiot proof instructions for people like myself :)
thanks

---

### Post by littlec on 2006-11-20
> **adamkat said:**
> 
how do I install the deb package?
I appreciate your help and would also want to see idiot proof instructions for people like myself :)
thanks

Adamkat, you can click it from Nautilus to run the Install.

TSeliot,
I just ran the latest envy stable release.
After rebooting, I can't start X and get an error similar to:

X: cannot stat /etc/X11/X (no such file or directory found) something something
and another line...

I did a quick google and read that it's possible due to jsut needing to symlink?

Or do I need to reinstall xserver?
Thanks.

---

### Post by tseliot on 2006-11-21
> **littlec said:**
> TSeliot,
I just ran the latest envy stable release.
After rebooting, I can't start X and get an error similar to:

X: cannot stat /etc/X11/X (no such file or directory found) something something
and another line...

I did a quick google and read that it's possible due to jsut needing to symlink?
I guess not.

> **littlec said:**
> Or do I need to reinstall xserver?
Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vesa" instead of "nv" and try again.

Then (if you want) we can try to diagnose the error.

---

### Post by pumo on 2006-11-21
> **tseliot said:**
> try point 4 of the Problems Section

tried every option even accel off, didn't work. 
but now it won't freeze, it goes to direct to console.

edit:
Haaa! It works, with newest envy ! thanks tseliot, because this point 4 I got X11.0.log error message which said that my nvidia logo image is too big for screen.
so Option "NoLogo"  to xorg.conf and now it works !
so my device in xorg.conf is:
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "NvAGP" "0"
        Option "RenderAccel" "Off"
        Option  "NoLogo"
EndSection

---

### Post by littlec on 2006-11-21
> **tseliot said:**
> I guess not.


Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vesa" instead of "nv" and try again.

Then (if you want) we can try to diagnose the error.

Hi Tseliot, thanks.
I gave that a try, it said xserver-xorg was not installed.
So I did sudo apt-get install xserver-xorg , reboot, and again in xserver YAY.  looks like a new nvidia driver is installed (i'm g uessing because the nvidia splash screen was a new one, not sure how to check).
Something while executing the script uninstalled my xserver.  
I'm not sure if i need to reconfig or not, but it's working for now, yay:)
If you'd like to look into debugging that script or if it was the script that caused my error, let me know what I can do to help.

---

### Post by littlec on 2006-11-21
*edit:
running a programing that requires GLX (quake 1) resets my X.

I have a GForce2 mx400

---

### Post by Mithrilhall on 2006-11-21
Worked like a charm.

Thank you.

---

### Post by tseliot on 2006-11-23
> **littlec said:**
> *edit:
running a programing that requires GLX (quake 1) resets my X.

I have a GForce2 mx400

1) Which driver did you install?
2) How did you install the driver?

---

### Post by tseliot on 2006-11-23
> **littlec said:**
> Something while executing the script uninstalled my xserver.
weird... my script can't do that.

> **littlec said:**
> I'm not sure if i need to reconfig or not, but it's working for now, yay:)
If you'd like to look into debugging that script or if it was the script that caused my error, let me know what I can do to help.
I really appreciate your offer but I have no idea of how we could diagnose the problem.

---

### Post by littlec on 2006-11-24
> **tseliot said:**
> 1) Which driver did you install?
2) How did you install the driver?

STABLE VERSION (0.7.2-0ubuntu1, released on November 8 2006)
(See my Blog for an explanation of Envy's features)

Licence: GPL

Package for Ubuntu Edgy Eft 6.10/Dapper Drake 6.06

envy_0.7.2-0ubuntu1_all.deb

----

installed that one. and installed it by leaving X, and executing the script, followed by a reboot

---

### Post by xenoalien on 2006-11-24
My system doesn't startup when I have "nvidia" in xorg.conf as the device but when I have "nv" it works fine. Why does it do that?

---

### Post by jagrav on 2006-11-25
Thanks a ton for your HOWTO. Method 2 worked great for my 3 or 4 years old Toshiba laptop Satellite 2410 , 512MB ram, GeForce4 420 Go, Pentium4m 1.8 ghz. Bless you.
jagrav

---

### Post by tseliot on 2006-11-25
> **xenoalien said:**
> My system doesn't startup when I have "nvidia" in xorg.conf as the device but when I have "nv" it works fine. Why does it do that?

How did you install the driver?

---

### Post by oskvaz on 2006-11-25
Excellent!!!  I've followed your instructions and the driver was installed succefully!.
I've installed driver 9629.  My PC is an AthlonXP 2600 and my card is a GForce FX5500.

Thanks buddy!

---

### Post by christooss on 2006-11-25
If you have Geforce 4 or older use 0.6.2 envy and not 0.7.2

nvidia 8x29 has bug for those cards

---

### Post by mingotta on 2006-11-26
> **tseliot said:**
> 
Script to make Method 2 faster

You can also use my Envy script which you can find below (for automating Method 2 and solving problems of driver mismatch)

Awesome (da paura)!!
Your envy script worked right out of the box for me!
I just bought a Nvidia Geforce FX-5200 and for the life of me I just couldn't make X start, I tried all sorts of tweaks on xorg.conf.
Then I reread this post and saw there was a quickier and dirtier way (the kind of ways that I like best, actually): using Envy.

I couldn't believe my eyes as I saw the login manager instead of a frozen unusable PC, after loading the initial drivers and bootup scripts.

My hardware: AGP 8X Geforce FX-5200, LG Studioworks 77M monitor.
OS: Ubuntu 6.10 (Edgy Eft)

Thanks, tseliot, you made my day!

---

### Post by pearish on 2006-11-26
Thank you, tseliot.

Your latest "envy" script worked the first time I tried it. I started with a fresh installation of ubuntu 6.10, downloaded your script, and followed the instructions you provided [here]("http://albertomilone.com/nvidia_scripts1.html"). When I restarted the xserver, I had access to all resolutions possible for my monitor (incl 1600x1200).

I think it is sad that most (all?) linux distributions don't support the main graphics cards available today (I have an nvidia 7900) "out of the box". The lack of support for graphics cards is another, significant hurdle/obstacle for the mainstream adoption of linux as a desktop alternative to Windows (IMHO).

Thankfully, there are people like you who are generous and knowledgable enough to "fill the gap".

---

### Post by Duhkha on 2006-11-28
Hi all!
i'm trying to use a riva tnt2 m64 card in a xubuntu system. i finally got to install the driver (nvidia-legacy), but when xorg uses it X freezes... i found it was an agp problem, and i disabled agp and then it works... 
Does anybody knows how to set up this agp?!?!
Thank u very much!

---

### Post by Hierzuhelfen on 2006-12-02
Thank you very much.  I used Method 1 to install drivers for my GeForce4 MX 440, and it's working beautifully.  One one problem I have (and its very minor) is that the Nvidia-Settings link is not coming up in the Applications or System menu.  I can still run it using a Run prompt; however, it just bugs me that it's not in the menu.  I did:
```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

[Desktop Entry] Name=NVIDIA 
Settings Comment=NVIDIA X Server Settings 
Exec=nvidia-settings 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System;
```
But it's just simply not in the menu.  I restarted the X Server, and then I just plain restarted, but still no sign of it.

Thanks again, everything else is working great!  I'm just OCD about these kind of things!

---

### Post by nikdo on 2006-12-02
tseliot,

thank you very much for all your hard work. Your tutorials save the day for many users.

May I point out the following:

In your tutorial "Latest Nvidia Edgy" (link from this sticky) in section "[Problems section #5 (refresh rates / resolution)]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION")" points to a wiki "HOWTO: change resolution/refresh rate in Xorg". In that wiki, under section "[Adding custom modeline]("http://doc.gwos.org/index.php/ChangeResolution#Adding_custom_modeline")", you have a link to an online modline generator. Alas that generator doesn't allow you to choose widescreen resolution monitors and is thus useless to tons of people. I suggest you put a link to this tool: "[XFree86 modeline generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")"

This generator let's you input your horizontal / vertical frequencies, your  dot clock frequency and your resolution and generates the modeline. This way, no matter the monitor you have you can get the accurate modeline.

Thanks for all your hard work!

Peter Endisch

---

### Post by Roderik on 2006-12-04
I seem to be having problems with the latest driver and my twinview setup. I'm running a 1600x1200 20" LCD and a 1280x1024 17" LCD and with the 9xxx versions the 1600x1200 screen does not work anymore. I've tried with envy and a deb from some repository with "amaranth" behind the name of the deb.

I only get an image on the 1280x1024 / 17" screen, and it stops at the borders of that screen. No matter what dvi-x combination, LeftOf, RightOf or dvi cables on the card combination i use.

There are no errors in the xorg log as far as i can see (below), and the nvidia-settings application sees the two screens, i can configure them so i have a twin view setup, but only with a max resolution of 1280x1024 per screen. The stock nvidia driver in edgy works flawlessly. 

I believe that it is a configuration problem or a driver bug, because the same happens with a similar setup at work.

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "CursorShadow" "1"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "true"
(**) NVIDIA(0): Option "TwinViewOrientation" "DFP-0 LeftOf DFP-1"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: 1600x1200, DFP-1: 1280x1024"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0,DFP-1"
(**) NVIDIA(0): Option "UseEdidDpi" "false"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Enabling cursor shadow
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.83.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:5:0:0:
(--) NVIDIA(0):     Acer AL2021 (DFP-0)
(--) NVIDIA(0):     Acer AL1721 (DFP-1)
(--) NVIDIA(0): Acer AL2021 (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL2021 (DFP-0): Internal Single Link TMDS
(--) NVIDIA(0): Acer AL1721 (DFP-1): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL1721 (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(WW) NVIDIA(0): Unable to find all display devices requested in TwinView
(WW) NVIDIA(0):     Orientation string "DFP-0 LeftOf DFP-1".
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-0:1600x1200,DFP-1:1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Setting mode "DFP-0:1600x1200,DFP-1:1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "DigitalVibrance" is not used

(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)

```

```

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
    Option         "Twinview" "true"
    Option         "TwinViewOrientation" "DFP-0 LeftOf DFP-1"
    Option         "MetaModes" "DFP-0: 1600x1200, DFP-1: 1280x1024"
    Option         "UseDisplayDevice" "DFP-0,DFP-1"
    Option         "UseEdidFreqs" "True"
    Option         "NoLogo" "1"
    Option         "CursorShadow" "1"
    Option         "DigitalVibrance" "60"
    Option         "RenderAccel" "true"
    Option         "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "AL2021"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Acer AL2021"
    DefaultDepth    24
   Option "AddARGBGLXVisuals" "True"
   SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by Roderik on 2006-12-04
ok, found and resolved the problem!

adding the following to my xorg.conf did the job: 
```

Option "ModeValidation" "NoDFPNativeResolutionCheck"

```

Help found at: [http://www.nvnews.net/vbulletin/showthread.php?p=1087379](http://www.nvnews.net/vbulletin/showthread.php?p=1087379)

---

### Post by taco-man on 2006-12-05
ok im having some problems hopefully you can help.
I have tried methods 1 AND 2. both result in a black screen after the ubuntu splash screen when the computer starts up (the loading screen) i have ubuntu 6.10 and its fully up to date my video card is a geforce 6600. If i use envy to install the driver after its done installing instead of me getting a blank screen i get something that looks somewhat liek white/gray diagonal lines that a jagged on the screen with a black background and it just flashes. after i uninstall the driver and restor the xorg.conf backup ubuntu works again as its back to using the nv driver. If i use the "unstable" version of envy (after uninstalling the regular version of envy to get it to let me install the unstable one)that installs the beta driver it results in the same black screen i get from methods 1 and 2. somebody PLEASE help me this is incredibly frustrating. Thanks

---

### Post by ivuntu on 2006-12-09
Hi,

Thank you so much for the python script to install the  nvidia drivers!:D It worked like a charm. It was installed in about 2 minutes, where as usually this sort of thing takes me at least one hour.

I really disliked going through the entire process every time I updated the system (though your earlier howto's worked for me too). For a relative newbie like me, this is the kind of thing that keeps me motivated to keep using Ubuntu Linux.

---

### Post by janfsd on 2006-12-09
Hi, I installed the latest NVIDIA drivers from your repositories, all works fine, except that now i dont have sound... please can you help me? maybe is a problem of the restricted-modules you updated?

EDIT:
After trying a lot of things to make the sound work, I just got back to the old driver and restricted modules, and sound is working now.

---

### Post by tseliot on 2006-12-11
> **janfsd said:**
> Hi, I installed the latest NVIDIA drivers from your repositories, all works fine, except that now i dont have sound... please can you help me? maybe is a problem of the restricted-modules you updated?

EDIT:
After trying a lot of things to make the sound work, I just got back to the old driver and restricted modules, and sound is working now.

I'm afraid I can't help you with that.

AFAIK the restricted modules should not conflict with your sound card module.

---

### Post by tseliot on 2006-12-11
> **taco-man said:**
> ok im having some problems hopefully you can help.
I have tried methods 1 AND 2. both result in a black screen after the ubuntu splash screen when the computer starts up (the loading screen) i have ubuntu 6.10 and its fully up to date my video card is a geforce 6600. If i use envy to install the driver after its done installing instead of me getting a blank screen i get something that looks somewhat liek white/gray diagonal lines that a jagged on the screen with a black background and it just flashes. after i uninstall the driver and restor the xorg.conf backup ubuntu works again as its back to using the nv driver. If i use the "unstable" version of envy (after uninstalling the regular version of envy to get it to let me install the unstable one)that installs the beta driver it results in the same black screen i get from methods 1 and 2. somebody PLEASE help me this is incredibly frustrating. Thanks

Try point 4 of the Problems Section of my guide

---

### Post by nami on 2006-12-15
I'm trying to install the nvidia drivers.  i downloaded the deb file getting ready to install the script but i dont know how to install a deb file.

I get this

nami@nami-desktop:~/Desktop$ sudo dpkg -i envy_0.6.1-0ubuntu3_all.deb
dpkg-deb: `envy_0.6.1-0ubuntu3_all.deb' is not a debian format archive
dpkg: error processing envy_0.6.1-0ubuntu3_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 envy_0.6.1-0ubuntu3_all.deb
nami@nami-desktop:~/Desktop$ 

Can anyone help?

---

### Post by tseliot on 2006-12-15
> **nami said:**
> I'm trying to install the nvidia drivers.  i downloaded the deb file getting ready to install the script but i dont know how to install a deb file.

I get this

nami@nami-desktop:~/Desktop$ sudo dpkg -i envy_0.6.1-0ubuntu3_all.deb
dpkg-deb: `envy_0.6.1-0ubuntu3_all.deb' is not a debian format archive
dpkg: error processing envy_0.6.1-0ubuntu3_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 envy_0.6.1-0ubuntu3_all.deb
nami@nami-desktop:~/Desktop$ 

Can anyone help?
Delete that deb file
then type:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu3_all.deb
```
```
sudo dpkg -i envy*.deb
```

---

### Post by nami on 2006-12-15
Thanks!

---

### Post by ziritrion on 2006-12-21
Looks like there's a new driver available at the NVIDIA website:

[http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)

Does anyone know wether the x crashing when fullscreen OpenGL bug has been fixed? I'm really looking forward to play quake3 and enemy territory on my PC :)

---

### Post by ziritrion on 2006-12-21
Nevermind, I actually reformated my PC and made a fresh Ubuntu install, and after installing the nvidia driver with envy Nexuiz seems to work fine, so I guess that my problems have finally ended! :D .

I'd like to thank tseliot for all his work (I forgot to thank him in the other threads he's helped me)

---

### Post by tophatandy on 2006-12-22
cant get full hardware exceleration on my old computer..

its running a GeForce 4 440

Arent these cards the ones that run funny?




tried loading nexuiz after a 2 hour download and no go..

bet you can imagine how happy I was..

---

### Post by tseliot on 2006-12-22
> **tophatandy said:**
> cant get full hardware exceleration on my old computer..

its running a GeForce 4 440

Arent these cards the ones that run funny?




tried loading nexuiz after a 2 hour download and no go..

bet you can imagine how happy I was..

read point 7 of the Problems section of my guide

---

### Post by xyrer on 2006-12-23
Hi, i'm all confused about the installation of the nvidia card, my case is this: I installed it and now it doesn't initiate gdm, i tried dpkg-reconfigure xserver-xorg but no luck

I have ubuntu edgy eft 6.10 and my card is a geforce mx 4000

---

### Post by fre4k on 2007-01-01
envy worked great for me ... geforce 4 mx 400 ... thanks :-)

---

### Post by tseliot on 2007-01-01
> **xyrer said:**
> Hi, i'm all confused about the installation of the nvidia card, my case is this: I installed it and now it doesn't initiate gdm, i tried dpkg-reconfigure xserver-xorg but no luck

I have ubuntu edgy eft 6.10 and my card is a geforce mx 4000
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

### Post by rotorcraig on 2007-01-09
I'm trying to get NVIDIA working with my Edgy installation on an ASUS A7N266-VM based system.

Tried a couple of methods found elsewhere but couldn't force 1280x1024_60 without terminally destabilising the system - have reinstalled Edgy a few times and am living with the (very stable but less performant) NV drivers at the moment.

Keen to read [your guide]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy") and see if it fixes my problems, but it seems to be offline?

Craig

---

### Post by pjbgravely on 2007-01-09
I keep getting a time out when envy tries to download the drivers from nvidia. Could this be a problem on my end?


Paul

---

### Post by iputz on 2007-01-09
Doesn't work...

When the X server tried to start up it gave me these two error messages:

glx: unknown module type
nvidia: unknwon module type

Will the next version have a fix for this bug?

---

### Post by iputz on 2007-01-10
tseliot, I followed your instructions in Method 1 exactly, but when I restarted the xserver, the screen turned black and my monitor shut off. What gives?

Update:
I tried your envy script---didn't work. I get the Ubuntu splash screen, but the xserver fails because nvidia.ko is not an ELF file

My card is a GeForce 6600, my OS is Edgy.

Here's my /etc/X11/xorg.conf:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by tseliot on 2007-01-10
> **iputz said:**
> tseliot, I followed your instructions in Method 1 exactly, but when I restarted the xserver, the screen turned black and my monitor shut off. What gives?

Update:
I tried your envy script---didn't work. I get the Ubuntu splash screen, but the xserver fails because nvidia.ko is not an ELF file


Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by rabbit83 on 2007-01-10
I have a similar Problem.
If I uncomment > Load "glx" the 9746 driver works, if it's not uncommented, I only get a black screen when starting gdm.
It tells > fatal IO error 104 on xserver ":0.0" when I type startx in console.
For Xorg.0.log and Xorg.conf see attachements.
I tried reinstalling, deletet the repo-version and tried envy.

EDIT:
The Nvidia-Installer says:
```

.> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
ERROR: The runtime configuration check failed for the library
       'libnvidia-tls.so.1.0.9746' (expected:
       '/usr/lib/tls/libnvidia-tls.so.1', found:
       '/usr/lib/libnvidia-tls.so.1').  The most likely reason for this is that
       conflicting OpenGL libraries are installed in a location not inspected
       by `nvidia-installer`.  Please be sure you have uninstalled any
       third-party OpenGL and/or third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

The Problem occured first after yesterday's xserver-xorg-common update.

Thanks in advance
Jan

---

### Post by drink on 2007-01-11
I just used envy on the latest edgy linux-generic kernel, which was necessary to get SMP support (as opposed to linux-386, which is specified by nvidia-glx.) Unfortunately I now have no GL support. If I try to do anything with GL then X crashes with the following log entry:

[INDENT]
ProcXCloseDevice to close or not ?

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting[/INDENT]

Also worth noting is that I apparently have no nvidia-glx-config. I do have an nvidia-xconfig.

Enclosed are my xorg.conf and my X error log. I did try using the uninstall option in envy before using the install option.

---

### Post by DerHesse on 2007-01-15
Just wanted to say thank you for your excellent script!

---

### Post by tseliot on 2007-01-16
> **drink said:**
> I just used envy on the latest edgy linux-generic kernel, which was necessary to get SMP support (as opposed to linux-386, which is specified by nvidia-glx.) Unfortunately I now have no GL support. If I try to do anything with GL then X crashes with the following log entry:

[INDENT]
ProcXCloseDevice to close or not ?

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting[/INDENT]

Also worth noting is that I apparently have no nvidia-glx-config. I do have an nvidia-xconfig.

Enclosed are my xorg.conf and my X error log. I did try using the uninstall option in envy before using the install option.
I suggest you to ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by tseliot on 2007-01-16
> **rabbit83 said:**
> I have a similar Problem.
If I uncomment  the 9746 driver works, if it's not uncommented, I only get a black screen when starting gdm.
It tells  when I type startx in console.
For Xorg.0.log and Xorg.conf see attachements.
I tried reinstalling, deletet the repo-version and tried envy.
Envy should uncomment it automatically :confused: 

> **rabbit83 said:**
> EDIT:
The Nvidia-Installer says:
```

.> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
ERROR: The runtime configuration check failed for the library
       'libnvidia-tls.so.1.0.9746' (expected:
       '/usr/lib/tls/libnvidia-tls.so.1', found:
       '/usr/lib/libnvidia-tls.so.1').  The most likely reason for this is that
       conflicting OpenGL libraries are installed in a location not inspected
       by `nvidia-installer`.  Please be sure you have uninstalled any
       third-party OpenGL and/or third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

The Problem occured first after yesterday's xserver-xorg-common update.

Thanks in advance
Jan
Try using the install and the uninstall function of Envy

---

### Post by thewall83 on 2007-01-16
I have installed through this guide the Nvidia drivers v9746 on the 2.6.17-10-generic kernel.

Now I compiled and installed the 2.6.20-rc4 kernel and want to use (for a little period to test the new kernel) both with nvidia acceleration...
The driver works on the two kernel prefectly but it can't be installed on both. If I install it on the 2.6.17, it doesn't work anymore when I boot the 2.6.20 and viceversa.

How can I solve?
If I use two different versions (e.g. 9746 and 9744) of the nvidia on the two kernel?

---

### Post by beuno on 2007-01-16
I've tried the latest version 0.8.1, and I get the following:

```
martin@martin:~$ envy
Password:


       +-------------------------------------------------+
       |                                                 |
       |             Welcome to Envy 0.8.1               |
       |                                                 |
       |    Developed by Alberto Milone (aka tseliot)    |
       |                                                 |
       +-------------------------------------------------+


       +---------------------------------------+
       |    Envy Menu ver.0.8.1                |
       |                                       |
       |    1 - Install the NVIDIA driver      |
       |                                       |
       |    2 - Uninstall the NVIDIA driver    |
       |                                       |
       |    3 - Install the ATI driver         |
       |                                       |
       |    4 - Uninstall the ATI driver       |
       |                                       |
       |    5 - Restart the Xserver            |
       |                                       |
       |    6 - Exit                           |
       |                                       |
       +---------------------------------------+
Please select one of the activities displayed above and press ENTER:

3
rm: cannot remove `*.deb': No such file or directory
Ubuntu Edgy 32bit
Traceback (most recent call last):
  File "interface.py", line 20, in ?
    objects.mainmenu()
  File "/usr/share/envy/instun/objects.py", line 355, in mainmenu
    menu1.process()
  File "/usr/share/envy/instun/interfaceclasses.py", line 61, in process
    objects.atiinstconfirm()
  File "/usr/share/envy/instun/objects.py", line 297, in atiinstconfirm
    confirmation.gotoop = atiinstall()
  File "/usr/share/envy/instun/objects.py", line 224, in atiinstall
    atiinstall2()#CONTINUE THE INSTALLATION
  File "/usr/share/envy/instun/objects.py", line 180, in atiinstall2
    task.drivertype()#latest, middle, oldest driver
  File "/usr/share/envy/instun/classes.py", line 98, in drivertype
    print 'Your graphic card has been detected as a ' + legacycards[card]
NameError: global name 'legacycards' is not defined
martin@martin:~$ 
```

It's a laptop with ATi Radeon 9100 IGP (RS300M) and Edgy

---

### Post by msemtd on 2007-01-17
Hmmm, just tried latest envy to install legacy nvidia on a clean edgy with GeForce2mx, and it vomits the following...
[HTML]<code><pre>
       +-------------------------------------------------+
       |                                                 |
       |             Welcome to Envy 0.8.1               |
       |                                                 |
       |    Developed by Alberto Milone (aka tseliot)    |
       |                                                 |
       +-------------------------------------------------+


       +---------------------------------------+
       |    Envy Menu ver.0.8.1                |
       |                                       |
       |    1 - Install the NVIDIA driver      |
       |                                       |
       |    2 - Uninstall the NVIDIA driver    |
       |                                       |
       |    3 - Install the ATI driver         |
       |                                       |
       |    4 - Uninstall the ATI driver       |
       |                                       |
       |    5 - Restart the Xserver            |
       |                                       |
       |    6 - Exit                           |
       |                                       |
       +---------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
Ubuntu Edgy 32bit
Traceback (most recent call last):
  File "interface.py", line 20, in ?
    objects.mainmenu()
  File "/usr/share/envy/instun/objects.py", line 355, in mainmenu
    menu1.process()
  File "/usr/share/envy/instun/interfaceclasses.py", line 56, in process
    objects.nvinstconfirm()
  File "/usr/share/envy/instun/objects.py", line 283, in nvinstconfirm
    confirmation.gotoop = nvidiainstall()
  File "/usr/share/envy/instun/objects.py", line 105, in nvidiainstall
    nvidiainstall2()#CONTINUE THE INSTALLATION
  File "/usr/share/envy/instun/objects.py", line 71, in nvidiainstall2
    task.drivertype()#latest, middle, oldest driver
  File "/usr/share/envy/instun/classes.py", line 94, in drivertype
    print 'Your graphic card has been detected as a ' + middlecards[card]
NameError: global name 'middlecards' is not defined
</pre></code>[/HTML]

---

### Post by Severa on 2007-01-17
tseliot, just wanted to say THANK YOU for your excellent work on nvidia drivers! I just ran Method 1 on my Feisty Herd 2 and I can happily say it works great!

---

### Post by oCfuu on 2007-01-17
I get the same error message as 'msemtd'...

what's going on there?

I have a Geforce 3 Ti 200 on an Asus A7N8X with Athlon XP 2500+ and I run Ubuntu 6.10

Hope that helps!

---

### Post by boywander on 2007-01-18
Just to add thanks and greets to the roll. =D>

Tried a couple different methods before, the first from Hub's guide and the second from Automatix, which resulted in a full reinstall.

Now the refresh rate numbers in the default resolution preferences are incorrect (50-60Hz?!), but the nvidia panel works fine.

---

### Post by rotorcraig on 2007-01-20
I'm sorted now, using your instructions and the legacy drivers.

Thanks for a great guide!

Craig

---

### Post by Big-Wayne on 2007-01-23
Many thanks,
I have had the problems outlined in the following thread;
[http://www.ubuntuforums.org/showthread.php?t=318206&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=318206&highlight=nvidia)
And spent hours trying to fix this and was considering reformatting and reinstalling ubuntu after I just got a black screen upon booting. I was in the last chance saloon and sshed into it which  successfully got  me a shell back. I followed the instructions for envy and hey presto, my nix box is up and running again with better graphics than ever. 


[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23694&stc=1&d=1169550223[/IMG]

---

### Post by mrgnash on 2007-01-23
Envy doesn't recognize my card (7950gt), so the nv driver it installed, while it gave me X back again, doesn't seem to support any of the hardware acceleration stuff. I'm also running the 2.6.20 kernel, so all this business about linux-generic and whatnot doesn't really work for me. Considering that both the Intel GMA950 and ATI X700 drivers installed on Edgy without any pain on my part, I'm not sure that the reputation of ease which Nvidia's drivers under Linux seem to have is well-earned.

---

### Post by C-A on 2007-01-24
I had trouble with my initial install of drivers (without envy). I used envy and everything is working now.

Thanks for the great work!

---

### Post by joecoin on 2007-01-24
Envy worked great for me once I followed the instructions. An excellent piece of work!

gforce4 MX 4000

---

### Post by Wipster on 2007-01-27
Massive kudos to you sir, most awesome piece of scripting, I was having real problems with xserver not being able to start up when trying to manualy do it.
My only question is that after running your script the update manager is asking me to install updates to the linux-restricted modules..... is this safe to do? I'v read somewhere to remove them when trying to install the nvidia drivers.

I'v only just downloaded your script and I have your repository on and all the universe and multiverse ones, so I think its all up to date.

---

### Post by jwazzz on 2007-01-27
Thanks Alberto! I tried Envy on a fresh edgy install with a geforce 3 ti200 and it worked!
The graphics on the screensavers look good now but still a little slow, is there anthing else I should 
do? I didnt see an nvidia screen either.

---

### Post by Orionek on 2007-01-28
I want install nVidia driver with Envy (envy_0.8.1-0ubuntu3_all.deb)  but i have problem:

```
No installer detected
Download of the driver in progress, please wait
md5new: 
md5sumold: 68cf7f155786daf6946b9daeb64c7a35
md5 Error! Operation aborted
orion@orionek:~$ 
```
I have GeForce 2 Ti
What i have to do?

---

### Post by trueloki on 2007-01-29
Hi,

I followed the awesome guide posted at the beginning of this thread and make my Geforce FX Go 5200 run with the Nvidia's proprietary drivers. 

The problem is that I'm not being able to hibernate my laptop (Toshiba Satellite M30) since then: it seems to work ok, but when I try to recover the session I get a black screen right after the KUbuntu logo (yes, I'm using KUbuntu). I've read I'm not the only one with this problem but, obviously, I've haven't found a solution.

¿Is it possible to make hibernation work with this drivers? If it's so, I could post any information of my system so anybody could help me.

Thanks.

---

### Post by fj4 on 2007-02-01
:cry: I've been fighting with these drivers ever since I started using Ubuntu.
First I was having this problem: [http://www.nvnews.net/vbulletin/showthread.php?t=75085](http://www.nvnews.net/vbulletin/showthread.php?t=75085)
Your excellent guide fixed that for me. Now, after installing the official package at the CLI, X fails with this message:

sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia

Any ideas? Over at the nvnews forum they seem to pass this off as not being related to nvidia drivers, which I don't believe.
Thanks in advance for any suggestions.

EDIT: I suppose I should provide more pertinent information. I'm running a Chaintech GeForce 7600 GS PCI-E with 256MB DDR3 on Edgy Eft for amd64. Sorry, I'm tired from trying different things to get this to work, all night.

---

### Post by Baboontu on 2007-02-01
hello
When I run the [COLOR="Navy"]envy script[/COLOR] (of tseliot) I get this:
> Ubuntu Edgy 32bit
Traceback (most recent call last):
  File "interface.py", line 20, in ?
    objects.mainmenu()
  File "/usr/share/envy/instun/objects.py", line 355, in mainmenu
    menu1.process()
  File "/usr/share/envy/instun/interfaceclasses.py", line 56, in process
    objects.nvinstconfirm()
  File "/usr/share/envy/instun/objects.py", line 283, in nvinstconfirm
    confirmation.gotoop = nvidiainstall()
  File "/usr/share/envy/instun/objects.py", line 105, in nvidiainstall
    nvidiainstall2()#CONTINUE THE INSTALLATION
  File "/usr/share/envy/instun/objects.py", line 71, in nvidiainstall2
    task.drivertype()#latest, middle, oldest driver
  File "/usr/share/envy/instun/classes.py", line 94, in drivertype
    print 'Your graphic card has been detected as a ' + middlecards[card]
NameError: global name '[COLOR="Red"]middlecards[/COLOR]' is not defined

my card:Nvidia Geforce 440 mx 
system:  Pentium 4 2.4Ghz
what is the problem?:confused: 
Thanks in advance

---

### Post by fj4 on 2007-02-02
Well I feel pretty stupid right now. To fix my issue I just went to the NVIDIA archives and downloaded older drivers until I found one that worked. :roll:

---

### Post by dcstar on 2007-02-02
> **Orionek said:**
> I want install nVidia driver with Envy (envy_0.8.1-0ubuntu3_all.deb)  but i have problem:

```
No installer detected
Download of the driver in progress, please wait
md5new: 
md5sumold: 68cf7f155786daf6946b9daeb64c7a35
md5 Error! Operation aborted
orion@orionek:~$ 
```
I have GeForce 2 Ti
What i have to do?

Same with me (NVIDIA Corporation NV5 [RIVA TNT2/TNT2 Pro]).

---

### Post by Footer on 2007-02-03
I want to use envy on Feisty Fawn Herd 3 but when I tried it said, "Operating System not supported" (or something like that!).

The kernel is:  2.6.20-6-generic

Am I doing something wrong or is envy not supported yet on Feisty?  If not, is there a workaround?

Thanks!

---

### Post by ziritrion on 2007-02-04
Feisty Fawn Herd 3 user here. I just dist-upgraded (I used to run Edgy with the nVidia driver via Envy and Beryl) and X crashed on me; everything else is running flawlessly. Envy doesn't work in Feisty, and all the methods I've tried to make the nVidia driver work aren't working. Will there be any update to Envy to make it work with Feisty? Because it would be a real life saver. Thanks!

---

### Post by FarazAbbas on 2007-02-04
After 2 days of guides that didnt work, i used your envy script and finally got all my drivers working properly. However, i cant seem to use the nvidia-settings program correctly. Heres what happens when i try it in terminal:

faraz@faraz-laptop:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

[IMG]http://i19.tinypic.com/2upfuit.png[/IMG]

I dont have all the options i should have here.


Please help, thanks, Faraz.

---

### Post by atact88 on 2007-02-04
You sure it needs to be this complicated? Seems like the Nvidia installer is willing to compile its own kernel and all that (the latest one, at least).
I haven't gotten to installing it yet, because it keeps interrupting where it says I don't have the libraries. But it doesn't seem like it needs all that! lol

but what do I know

:lolflag:

---

### Post by Arup on 2007-02-05
Envy is the program that lets me install nvidia-legacy for my ancient GeForce 256DDR card, the default generic Kernel gets changed by Ubuntu if you go the Synaptic route of install, it puts i386 which makes me loose SMP on my machine, its a dual P-III 850 so full kudos to TSELIOT, only thing is I have to use the older Envy version .73, the newer .8x series give me a md5 checksum error for nvidia legacy driver which it downloads from the nvidia site.

---

### Post by sv452 on 2007-02-06
hay rotocraig - i have the exact same mobo as what u have - 

have u been able to get the nvidia drivers to work ? i tried envy but i don't have a inet connection where the pc is - is there a way to run envy offline???

also my Geforce 2 Integrate GPU freezes and gives me GLX missing errors. any ideas ???

---

### Post by CallsignBaron on 2007-02-06
Fantastic script!!! Thank you so much! Envy installed the _latest_ drivers from the nvidia site which I had alot of trouble trying to do myself. The up-to-date drivers got me an extra ***10***fps in X-Plane over the older driver version in the Ubuntu repos. Thanks again.

CallsignBaron

---

### Post by iainmcc on 2007-02-07
I just fumbled my way around exactly this problem with a Toshiba Satellite Pro M10 (has GeForce4 402 Go)

If you get a black laptop screen (or black external VGA) look in the log /var/log/Xorg.0.log.

There's a few lines:

> (--) NVIDIA(0): Connected display device(s) on GeForce4 420 Go at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     TOSHIBA Internal Panel (DFP-0)
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): 224.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
(II) NVIDIA(0): Mode Validation Overrides for TOSHIBA Internal Panel (DFP-0):
(II) NVIDIA(0):     NoVesaModes
(II) NVIDIA(0): Assigned Display Device: DFP-0

Which tell you what display outputs are detected (I haven't looked into getting my TV-out working yet). On my laptop, X always chose CRT-0 for reasons unknown. I had to add the following line to my Screen section in xorg.conf...

> Option "UseDisplayDevice" "DFP"

To force the beast to use my laptop screen.

---

### Post by predator on 2007-02-08
I've been stuffing around for hours trying to get this to work.. Firstly, I installed Envy, and ran it through to get /install the latest nvidia drivers. I can get it to work in the 'nv' driver at 1024x768+, but when i try the 'nvidia' driver, it won't allow anything above 800x600 :( 

Setup is 

Nvidia 5200 AGP w/ 128mb RAM
2x 19" CRT

**** FIXED - in the end it turned out having my second monitor plugged in was causing the problem. It must have had trouble with two monitors on the bus, and thereby not being able to talk to the monitor to see which resolution were valid (or something similar). Unplugged the second monitor completely from the card, and wa'la, all high-res modes enabled with acceleration and OpenGL. Works nicely now :)**

Here is my xorg.conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BusID 	   "PCI:2:0:0"
    VendorName     "NVIDIA Corporation"
   Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option         "UseDisplayDevice" "CRT"


EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768"
    EndSubSection
EndSection


```


Here is the Xorg.0.log file - it says something about 'display doesn't support 1024x768 mode, ignoring', etc and then something like 'falling back to auto-detect 800x600 mode'

my X log is included below..

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux gfresh-desktop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb  8 23:42:47 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/share/fonts/X11/TTF/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/CID/" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(**) RgbPath set to "/usr/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 0000,0000 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1458,0c11 rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1458,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1458,5004 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1458,5004 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1458,5004 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,006a card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:08:0: chip 11c1,044c card 11c1,044c rev 02 class 07,80,00 hdr 00
(II) PCI: 01:0a:0: chip 14f1,8800 card 107d,6611 rev 05 class 04,00,00 hdr 80
(II) PCI: 01:0b:0: chip 10ec,8139 card 1458,e000 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(--) PCI: (1:10:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xde000000/24
(--) PCI:*(2:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xdc000000/24, 0xd0000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdf001000 - 0xdf0010ff (0x100) MX[B]
	[1] -1	0	0xdf000000 - 0xdf0000ff (0x100) MX[B]
	[2] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[3] -1	0	0xe0005000 - 0xe00050ff (0x100) MX[B]
	[4] -1	0	0xe0004000 - 0xe0004fff (0x1000) MX[B]
	[5] -1	0	0xe0003000 - 0xe0003fff (0x1000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[13] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf001000 - 0xdf0010ff (0x100) MX[B]
	[1] -1	0	0xdf000000 - 0xdf0000ff (0x100) MX[B]
	[2] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[3] -1	0	0xe0005000 - 0xe00050ff (0x100) MX[B]
	[4] -1	0	0xe0004000 - 0xe0004fff (0x1000) MX[B]
	[5] -1	0	0xe0003000 - 0xe0003fff (0x1000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[13] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdf001000 - 0xdf0010ff (0x100) MX[B]
	[5] -1	0	0xdf000000 - 0xdf0000ff (0x100) MX[B]
	[6] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[7] -1	0	0xe0005000 - 0xe00050ff (0x100) MX[B]
	[8] -1	0	0xe0004000 - 0xe0004fff (0x1000) MX[B]
	[9] -1	0	0xe0003000 - 0xe0003fff (0x1000) MX[B]
	[10] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdf001000 - 0xdf0010ff (0x100) MX[B]
	[5] -1	0	0xdf000000 - 0xdf0000ff (0x100) MX[B]
	[6] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[7] -1	0	0xe0005000 - 0xe00050ff (0x100) MX[B]
	[8] -1	0	0xe0004000 - 0xe0004fff (0x1000) MX[B]
	[9] -1	0	0xe0003000 - 0xe0003fff (0x1000) MX[B]
	[10] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdf001000 - 0xdf0010ff (0x100) MX[B]
	[5] -1	0	0xdf000000 - 0xdf0000ff (0x100) MX[B]
	[6] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[7] -1	0	0xe0005000 - 0xe00050ff (0x100) MX[B]
	[8] -1	0	0xe0004000 - 0xe0004fff (0x1000) MX[B]
	[9] -1	0	0xe0003000 - 0xe0003fff (0x1000) MX[B]
	[10] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
(**) NVIDIA(0): Option "UseDisplayDevice" "CRT"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.18.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:2:0:0:
(--) NVIDIA(0):     EEA D@???@@ (CRT-0)
(--) NVIDIA(0): EEA D@???@@ (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Option "UseDisplayDevice" "CRT" converted to "CRT-0".
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): Invalid display device in Mode Description "1280x1024"
(WW) NVIDIA(0): Not using mode description "1280x1024"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): Invalid display device in Mode Description "1024x768"
(WW) NVIDIA(0): Not using mode description "1024x768"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): No valid modes for "1280x1024,1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768,1024x768"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdf001000 - 0xdf0010ff (0x100) MX[B]
	[7] -1	0	0xdf000000 - 0xdf0000ff (0x100) MX[B]
	[8] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[9] -1	0	0xe0005000 - 0xe00050ff (0x100) MX[B]
	[10] -1	0	0xe0004000 - 0xe0004fff (0x1000) MX[B]
	[11] -1	0	0xe0003000 - 0xe0003fff (0x1000) MX[B]
	[12] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

```

---

### Post by Luk0r on 2007-02-08
Wow, Envy really did well automating it all.  Nice work!

---

### Post by CC=AC3 on 2007-02-08
I have a weird problem with envy that I just dont know how to fix.

When I got the latest .deb package and tried to install it, I got this message: 

The package might be corrupted or you are not allowed to open the file. Check the permissions of this file.

I tried getting the latest .deb package to install it, but it didnt work at all. Now I get this message and I have no idea how to fix it:

E: The package envy needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I use ubuntu eddy 6.10 of course :). I recently reinstalled my ubuntu. Envy worked like a charm for me before, and I dont understand this problem. I did use an older version of Envy before, but I dont think its the version that is causing the problem. I believe I have all teh correct repositories enabled. Its really annoying to have this problem because now I cant access any of my repositories. Im fairly new to Ubuntu, so maybe I am making a dumb mistake...please help. 

EDIT: Sorry if this issue has already been raised and solved. :(

Thanks in advance
-AC3

---

### Post by meckert on 2007-02-10
Just wanted to say thanks for the script...installation was perfect.

cheers,
mike

---

### Post by Pinniped on 2007-02-10
[COLOR="DarkOrchid"]Thank-you for the script - my system is now back to the way it was before the recent upgrade debacle =D> [/COLOR]

---

### Post by 16777216 on 2007-02-10
I ran the script and for the most part it runs fine except when it tries to download the driver from nVidia I keep getting a time out error.

I have had similar problems with other "auto-scripts" *cough Automatix cough* and setting the time out to a higher value always fixed it but I can't find where to change the time out in your code.
( I wish I knew what the issue with my net connect was, probably my crappy ISP. )

I would like a little help on this if possible please.

---

### Post by 16777216 on 2007-02-10
I'm going to manually download the driver  and move it to the  /usr/share/envy directory and re run the script.

---

### Post by 16777216 on 2007-02-10
That worked perfectly!:KS

---

### Post by neighborlee on 2007-02-10
> **tseliot said:**
> Hi, I've ported my guide about the Nvidia Drivers to Edgy Eft on the USDF.
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Or on my website:
[Latest Nvidia Edgy]("http://albertomilone.com/latest_nvidia_udsf_edgy.html")

**[COLOR="Red"]The guide works ONLY for driver 8774 or higher (Method 2)[/COLOR]**



--------------------------------------------------------------------
Script to make Method 2 faster

You can also use my Envy script which you can find below (for automating Method 2 and solving problems of driver mismatch)

NOTE: this might be dangerous and buggy

This script will download the Nvidia installer (and all the files the installer needs) and set the driver for you.

Get to the following website:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And follow the instructions you will find there.

The scripts will install the Nvidia driver 9631 and 7184

That isnt working here sorry to say ..when I run it, it gives me a black screen with blinking cursor in upper left corner of screen..

is there somethign I need to remove via apt-get to let script work properply possibly ?

thx
nl

---

### Post by fstephens on 2007-02-10
I am having the exact same problem. Have tried many times to install and configure the nvidia driver manually. Tried the Method 1 given by tselliot, tried his Envy script too. No luck.

Seems I cannot load the nvidia driver. lsmod does not show it loaded, modprobe nvidia fails, and depmod didn't help either.

nv driver works OK, except for a really annoying duplicated vertical insertion point bar during text editing in some applications.

The card is a generic Gforce 6200. with both VGA and DVI outputs. I have only one monitor turned on while testing this, but I want to configure dual monitors if I can get the nvidia driver to load.

Help please!

---

### Post by 16777216 on 2007-02-11
Well I am not sure what your problem is or how to fix it, tell us the steps that you used, you know the answers to prompts you were given and the response you got back.

I hope you can get this issue fixed.

When you get it fixed you can use my xorg.conf as a guide for your dual head setup.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "EMI eView 17f2"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 TurboCache(TM)"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "CoolBits" "1"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

You will probably need to change the metamodes but other than that it should drop right in.:)

---

### Post by neighborlee on 2007-02-11
> **fstephens said:**
> I am having the exact same problem. Have tried many times to install and configure the nvidia driver manually. Tried the Method 1 given by tselliot, tried his Envy script too. No luck.

Seems I cannot load the nvidia driver. lsmod does not show it loaded, modprobe nvidia fails, and depmod didn't help either.

nv driver works OK, except for a really annoying duplicated vertical insertion point bar during text editing in some applications.

The card is a generic Gforce 6200. with both VGA and DVI outputs. I have only one monitor turned on while testing this, but I want to configure dual monitors if I can get the nvidia driver to load.

Help please!

A friend had given me a url, and no where in it did I recall that first I had to 'ctrl-alt-F1', but doing that solves the black screen issue entirely as you clearly need to do this in console not X..

good luck
g.leej

---

### Post by rfs1970 on 2007-02-12
Hi,

I have a GeForce4 MX 4000 AGP 8x installed in my computer (AMD 1.8 ghz) with Ubuntu Edgy 6.10 and Linux Kernel 2.6.17-11-generic.

I downloaded and run the latest envy script created by Alberto Milone and during the instalation everything was all right even the new nvidia splash screen came out when it restarted my GDM.

The only problem that I'm having is: 
$: glxinfo | grep direct
direct rendering: No

My xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:47:17 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option         "AIGLX" "true"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
    Option         "XkbVariant" "intl"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "AOC D556"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Monitor        "AOC D556"
    DefaultDepth    24
    Option         "DisableGLXRootClipping" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```


Thank you,


r.

---

### Post by MichiganMan on 2007-02-17
The Envy script went off without a hitch.  But now I have an interesting quirk on my system.  Using a new Samsung 225bw and an Nvidia 6800gt.  Before Envy I didn't have any trouble setting up the LCD.  A simple dpkg-reconfigure xserver-xorg set me up with my LCD's native 1680x1050@60Hz.  Didn't even need a modeline, (although I later threw one in for curiousity's sake)

Now, after Envy, Gnome's System>Preferences>Screen Resolution app reports that I'm running a refresh rate of 50Hz, and only gives me the option of changing to 54.  But then the Nxidia Xserver settings app says I'm running at 60Hz.  And if I change from Auto to 60Hz in it, Gnome's app then says 97...!

Anyone else seeing anything like this?

---

### Post by 16777216 on 2007-02-18
I,m getting the same thing Gnome says one thing nVidia and xvidtune say something else. ( Though the latter two agree )
I just ignore Gnome.

---

### Post by rbil49 on 2007-02-19
> **tseliot said:**
> You have to remove the ATI driver before installing the Nvidia one.

Type:
```
sudo aptitude purge xorg-driver-fglrx
```

then
```
sudo aptitude install nvidia-glx
```

Does this apply to the oss ati/radeon driver that comes with Ubuntu? I've upgraded Dapper to Edgy and have been running with an old ATI 7500 and the oss radeon driver. Shortly I'm going to switch video cards and will be using a GeForce 6800 GT.

If I need to remove the ati driver, please tell me how I'd do it. Or will running envy take care of all that?

Thanks

Cheers.

---

### Post by stansford on 2007-02-21
Hi,
Don't know if you can help.
I have just installed the latest NVIDIA drivers using your Envy script onto my core2duo system with a GEFORCE 7300LE PCI-E 128mb graphics card under Ubunut 6.10.

This seems to have worked OK and I get the NVIDIA splash screen before going back into GNOME. 

However sometimes, and it's not every time, once I get into the desktop it freezes. I can often still move the mouse somewhat jerkily around, but no applications will load and everything else seems frozen.

As I say, this doesn't always happen, but it will happen regularly enough for me to be frustrated.

Have you any idea how to solve this.
Any suggestions appreciated. I enclose my xorg.conf in case it helps at all.

---

### Post by Xer0 on 2007-02-23
After the upgrade to 2.6.7-11-generic, my nvidia drivers broke. Expected!
So I did the following to fix:
```

sudo apt-get remove nvidia-glx
sudo apt-get remove linux-restricted-modules-2.6.17-10-generic
sudo apt-get install linux-restricted-modules-`uname -r`
sudo apt-get install nvidia-glx
```

And this works... until I reboot my computer. X always fails on startup (something about not being able to find nvidia.ko - normal error you get when you upgrade kernels, I think) and I need to repeat the above procedure every time I start up. I have tried installing linux-generic instead of the restricted modules, but this has the same problem.

From grub, I have 386 images installed, though I don't use them. I'm sure there was a good reason for me doing this in the past, but I can't recall it now.

Any ideas?

---

### Post by unknown_zohaib on 2007-02-24
hey guys, 

for some reason i cant seem to find a option under nvidia-settings where i can select my screen resolution... im not sure what my max resolution my monitor supports... is there a way i can get it to auto detect? because it seems to be defaulting to 800*600 and i knwo it can go higher>!

thanks
-zee

---

### Post by gholen on 2007-02-24
Thanks man får this program or script, it really saved my day, been working on the 2.6.20 kernel, and the nvidiadrivers died, thanks to this, my comuter is working as it should be. Thanks again!

---

### Post by itchanddino on 2007-02-27
Should I still install gcc-3.4?  It appears I already have gcc-4.1.  Thanks!

---

### Post by sh4d3z on 2007-02-27
i have geforce fx 5200
i tried method two with NVIDIA-Linux-x86-1.0-9746-pkg1.run 
step seven said it was unable to run it
went to get back into gdm and x was messed up so i restored my xorg.conf file by copying the backup i made of it... still wasn't able to get into gui mode
```
sudo dpkg -reconfigure -phigh xserver-xorg
``` 
(stupidly i didn't get the output of that err message)
wouldn't fix it either
i figured i would reboot and try to fix in single user
the i got grub error 17
with no selections...
i booted the live cd and tried the various how-to on repairing the grub menu
```
grub> find /boot/grub/stage1
```
produced grub error 15
i was completely screwed only thing i could do was reinstall
(luckily i had a home partition :] so all my files were safe)

i remember trying to get this piece of crap to work on winblows too!
took fifteen hours of banging my head on the keyboard for it finally to work

i guess what i'm say is don't get the geforce fx 5200
as for these 3d accelerators period, i won't be attempting to install any of them again

---

### Post by Segovia on 2007-02-28
Thanks for this, tseliot.  It worked perfectly.  I appreciate your efforts.

---

### Post by Johnathon on 2007-03-06
Hi guys. 

I've just used the latest (GUI) envy to install the ATI legacy drivers for my card (Works a dream - thankyou!)

Only problem, is that now, my repos are broken, aptitude is saying this:

The following packages have unmet dependencies:
  fglrx-kernel-2.6.17-10-generic: Depends: xorg-driver-fglrx (= 8.33.6-1) but 8.28.8-1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
fglrx-kernel-2.6.17-10-generic


Any ideas?

---

### Post by oboontoo on 2007-03-07
I just ran envy 0.9.0 to install nvidia drivers on my ubuntu6.10 64bit and even though  I choose "Update xorg.conf automatically" it didn't. There's no difference between xorg.conf and xorg.conf_backup_200703080858.
Looking through the envy log I see some errors (might be nothing to worry about, but I'm posting them here)

```
md5new: d41d8cd98f00b204e9800998ecf8427e
md5sumold: c0afc66e1c21a9a54ba6719b8edd3166
ENVY ERROR: md5 Error! Trying to fetch the driver from the website

``````

/bin/sh: cannot create /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patche
s: Is a directory

``````

[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86_64-1.0-9746-pkg2/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-gl
x/usr/bin/

``````

dpkg: dependency problems prevent configuration of nvidia-glx-ia32:
 nvidia-glx-ia32 depends on nvidia-kernel-1.0.9746; however:
  Package nvidia-kernel-1.0.9746 is not installed.
 nvidia-glx-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing nvidia-glx-ia32 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-1.0.9746; however:
  Package nvidia-kernel-1.0.9746 is not installed.
dpkg: error processing nvidia-glx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.
dpkg: error processing nvidia-kernel-source (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx-dev:
 nvidia-glx-dev depends on nvidia-glx (>= 1.0.9746); however:
  Package nvidia-glx is not configured yet.
dpkg: error processing nvidia-glx-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-glx-ia32
 nvidia-glx
 nvidia-kernel-source
 nvidia-glx-dev
```

Maybe some of these errors come from the nvidia install package and not envy.
However the nv driver is still used in xorg.conf.

Envy was the first thing I used after installing ubuntu6.10 and downloading all the updates so it was a completely fresh system. Why didn't it update the xorg.conf? it did create a backup so it must have tried to update.

Martin

---

### Post by useResa on 2007-03-09
I normally install my nvidia driver using the ".run" file as provided by nvidia.
However ... since I like to experiment ... today I have downloaded Envy.
Maybe just got tired of doing it manually, don't know.

The reason for downloading Envy today was the fact that a new nvidia driver has been released: **1.0-9755** (see [here](http://www.nvnews.net/vbulletin/showthread.php?t=87714)).
Regardless of how impressed I was by the ease of use of envy (and I was really quite impressed), I was also disappointed by the fact that Envy did NOT install the latest driver but the one I already had (.10.9746).

Can someone explain why NOT the latest driver is downloaded, but the previous version (which I already had :()

---

### Post by 16777216 on 2007-03-09
I believe it's because the script has a predetermined list of package versions.
For example: 

instead of Bob has ```
nVidia-1.1.12 so look for nVidia-1.1.12+n
```It has a list such as ```
known drivers= nVidia-1.1.10, nVidia-1.1.11, nVidia-1.1.12
``` etc...

So until the script is manually updated it will download the latest module as of the time the script was written.

---

### Post by elventear on 2007-03-12
I have a GeForce 4 MX 420. When I try to install the 96xx legacy with Envy the install process fails complaining about a missing file, since I cannot make a log all I've seen is that the name of the file is libnvidia-wfb.

When I try to install the older Legacy drivers, they compile but then I am unable to get to X. 

Any ideas on how to solve this problem with Envy?

---

### Post by nicoladimaria on 2007-03-13
> **elventear said:**
> Any ideas on how to solve this problem with Envy?
here's the log
/var/log/envy-installer.log
submit it to the author

---

### Post by nicoladimaria on 2007-03-13
> **useResa said:**
> Can someone explain why NOT the latest driver is downloaded, but the previous version (which I already had :()
are you using the latest envy version ?
0.9.1-0ubuntu3, released on March 10 2007
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

note that you need to remove your old envy to install the new one

---

### Post by useResa on 2007-03-13
> **nicoladimaria said:**
> are you using the latest envy version ?
0.9.1-0ubuntu3, released on March 10 2007
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

note that you need to remove your old envy to install the new one
Guess I was just a little to quick ;)
Indeed I had version  0.9.1-0ubuntu2, thus resulting in the installation of the previous version.

I now did the installation using the latest version of Envy and I now have the latest version of the Nvidia driver.
10x for pointing this out.

---

### Post by Dock on 2007-03-15
I installed the drivers using Method 2 and 3d acceleration works fine. I couldn't get Oblivion to play through Cedega cause it couldn't read my card, so I went into xorg file and looked under device and it doesn't list my Graphics card. Here is the info:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "N71S"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option 	   "TwinView" "True"
    Option 	   "TwinViewOrientation" "RightOf"   
    Option  	   "UseEdidFreqs" "True"
    Option 	   "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option 	   "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "N71S"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

And the Glxinfo is:
 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6800 GS/XT/AGP/SSE2
OpenGL version string: 2.1.0 NVIDIA 97.55
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x154 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```

My graphics card is an XFX Geforce 6800 (i think gt) AGP 8x
I read through the forums and tried to find an answer, but I came up short or overlooked it. Any help would be appreciated!

---

### Post by tseliot on 2007-03-15
> **Dock said:**
> I installed the drivers using Method 2 and 3d acceleration works fine. I couldn't get Oblivion to play through Cedega cause it couldn't read my card, so I went into xorg file and looked under device and it doesn't list my Graphics card. 
Your card is listed in your xorg.conf.

The fact that the model of your card is not written there will not affect the functioning of your card in any way. What you see in there is only a label.

1) I guess the problem is Cedega's. Or maybe Cedega has problems with twinview. Try disabling twinview and see if it works.

2) What does this command say?
```
glxinfo | grep rendering
```

---

### Post by Dock on 2007-03-15
It still says the same thing. I was just wondering if that had anything to do with why Oblivion wouldn't play. It worked in Windows, but I'm havin a rough time gettin it to work in Linux. The direct rendering is enabled and working. Thanks for your help and all you do!

---

### Post by irishman2020 on 2007-03-16
I just found the link to this forum on the envy site, so I thought I'd post my question here... Sorry tselliot for the extra email in your box, but I'm stuck, and I want to figure this out.

Sorry to bother you, and I'm sure theres some forum about this, but I couldnt find one very quickly, so I decided to email you.  I just installed a copy of ubuntu edgy eft 6.10 with an nvidia 7300 le graphics card.  I had problems running dual monitoring off the card (would show the VGA, but the SVGA would show scrambled images once X loaded).  So I downloaded Envy.  I installed the software and ran it.  Then, after a reboot I lost the ability to load x.  I went in and deleted the xorg.conf and replaced it with the xorg.conf.backup and still nothing.  I'm pretty new to linux tbh, but I've got some idea of how to do simple items.  What do you suggest to restore ubuntu?

Thank you a ton!
Caleb/Irishman

---

### Post by adriant51 on 2007-03-19
Thanks tseliot! I have a Geforce4 Go 420. I followed your advice in problems section 7 (the first suggestion) and my problems were solved.

Regards,
 Adrian

---

### Post by craigyjack on 2007-03-20
Hey,

First off, I am a noob. I ran Envy, and like Irishman 2 posts ago, now X will not load, and I really do not know what to do now. I tried to follow the wiki HOWTO for nvidia drivers to reconfigure X, but to no ado. X still will not run and I do not know what to do.

Please, if anyone could help I would greatly appreciate it.

EDIT: I reconfigured the x.conf back to nv to get X to load back up. But I am wondering if using nv and not the nvidia driver will have any effect when I start to play game, etc. Will I need to change it to nvidia driver? I really do not know.

Thanks,
Craig

---

### Post by Joco_Ultimate on 2007-03-20
I have the same problem...

---

### Post by tirengarfio on 2007-03-20
thanks tseliot for your steps. It works on me, I mean, i think it works because i can see the logo and glxgears works.

anyway i cant find the NVDIA settings to configure the resolution of my screen. Where is it?

It should be in applications folder but it is not there.

I tried to find it with "locate NVIDIA-Settings.desktop" but it didnt find anything in my HD.

Can someone help me?

EDITED:

ok, just typing "nvidia-settings" on the terminal.

---

### Post by useResa on 2007-03-20
You can get the Nvidia settings by either installing them using Synaptics (package name: nvidia-settings) or install them from terminal using ```
sudo apt-get install nvidia-settings
```

Hope this helps.

---

### Post by tirengarfio on 2007-03-20
> **useResa said:**
> You can get the Nvidia settings by either installing them using Synaptics (package name: nvidia-settings) or install them from terminal using ```
sudo apt-get install nvidia-settings
```

Hope this helps.

I have just write "sudo apt-get install nvdia-settings" and it has installed something, but when i have rebooted the system it has show me the blue screen saying "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"


It is for sure a problem with the line "sudo apt-get install nvdia-settings" because I rebooted before without problems.

---

### Post by stavpal on 2007-03-20
Hello, I need a little help on installing right nvidia drivers

My specs are Pentium4 1.9GHz, 512mb rdram, geforce6600gt (agp) etc...

I read the guide ([http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)) but I didn't exactly understand what to do here: (method 2)


```

1) Download the installer from this page according to your architecture (32bit or 64bit) http://www.nvidia.com/object/unix.html

2) Open Terminal or Konsole and type:
[code]

sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config

```

NOTE: [COLOR="Red"]replace the -generic above with -386 or -server.[/COLOR] The same arch as you installed above, when installing the linux-generic package
[/code]

I'm not sure what to write (red color. I just installed Ubuntu. I didn't select 386 or server

---

### Post by GMU_DodgyHodgy on 2007-03-20
TSEliot,

Your Envy software was brilliant.  It got my drivers installed without a hitch.

Is it possible to get this application installed as a standard install on Ubuntu?

It worked flawlessly.  

Where can I donate. 

How else can we help as users for testing?

Job Well Done Sir!!

---

### Post by zeroooooooooooo on 2007-03-20
I ran Envy this morning in Edgy, and I have a 7600GT. I let it do everything automatically, rebooted, and the X server won't load.

"Error: API mismatch, the nvidia kernel module has the version 1.0-9755 but this x module has version 1.0-8776. Please make sure the kernel module and the x module have the same version."

I don't know what to do.

Thanks.

---

### Post by techstop on 2007-03-21
> **zeroooooooooooo said:**
> I ran Envy this morning in Edgy, and I have a 7600GT. I let it do everything automatically, rebooted, and the X server won't load.

"Error: API mismatch, the nvidia kernel module has the version 1.0-9755 but this x module has version 1.0-8776. Please make sure the kernel module and the x module have the same version."

I don't know what to do.

Thanks.

Follow the instructions at the bottom of the envy page here (start at step 5) unless you have an old installation of envy...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You need to uninstall the previous nvidia installation, then do a clean install again with envy;

> 5) Run Envy's textual installer by typing:
sudo envy -t

6) Choose to "Clean the Installation of any Nvidia driver" by typing "6" and press ENTER.

WARNING: if "Envy" seems to hang on Ubuntu's splash screen you will have to press Alt+F1. (this usually happens on Kubuntu)

7) Then you can use the "Install" function.

NOTE: you will NOT need to repeat the whole process next time you want to install the Nvidia driver (you should be able to use Envy's GUI)

---

### Post by useResa on 2007-03-21
> **stavpal said:**
> Hello, I need a little help on installing right nvidia drivers
 
My specs are Pentium4 1.9GHz, 512mb rdram, geforce6600gt (agp) etc...
 
I read the guide ([http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)) but I didn't exactly understand what to do here: (method 2)
 
 
```

1) Download the installer from this page according to your architecture (32bit or 64bit) http://www.nvidia.com/object/unix.html
 
2) Open Terminal or Konsole and type:
[code]
 
sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config

```
 
NOTE: [COLOR=red]replace the -generic above with -386 or -server.[/COLOR] The same arch as you installed above, when installing the linux-generic package
[/code]
 
I'm not sure what to write (red color. I just installed Ubuntu. I didn't select 386 or server
Basically what is trying to be indicated is that you install the linux-headers that match your kernel. If you would like to make sure that you install the correct linux-headers, you can also type```
sudo apt-get install linux-headers-`uname -r`
```
NOTE: The single quotes used here are the ones that are next to the 1 on a US keyboard

---

### Post by samael_ on 2007-03-28
i have reinstalled Ubuntu since the ****** around alot on the old one, i am pretty new to linux as you may understand. and i have had alot of trouble getting up the ress till 1680x1050... Now i finally figured out how to install envy but i have a problem (some modules i havent understood how to add). I install envy and the driver, start up the Nvidia thingie and i change the ress, till the one best suited for my screen, which BTW is a 20¨ LG L204WT (widescreen). But when i reboot my screen-ress fall back to 12xx-something. cant remember... i have tried both to apply the new setting, then close. and click the applu then click save to Xconfig button. but it wont work... what do i need to do to make it stick, also when i reboot... if anyone could help i would greatly appreciate it. Keep in mind if you want to explain it that i am a newbie and dont know alot about Linux..

BTW: my graphic card is a Nvidia GeForce 6800GS...

and yes i have tried to search for the solution, but havent found anything:confused:

EDIT: BTW i run Ubuntu 6,10 Edgy

---

### Post by 16777216 on 2007-03-28
Try ```
sudo nvidia-settings
```
Any changes you make should stick then.

---

### Post by samael_ on 2007-03-28
> **16777216 said:**
> Try ```
sudo nvidia-settings
```
Any changes you make should stick then.


thanks alot mate... Now i have changed the ress, checked som boxes, rebooted and the ress hasnt changed\\:D/ 

spent so much time trying to fix this, so nice that it seemed to have agreed with me on the ress atm. so much better then the 1024 and the 1280 i had to use earlier...

thanks again;)


EDIT
I also have to direct a HUGE thanks to tseliot that has made envy. i love that app, atleast now that its working for me. hehe. Keep up the good work ;)

---

### Post by cyb3rj on 2007-03-29
> **Lord Landis said:**
> 
```
sudo dpkg-divert --remove /usr/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
```

After that, apt-get installed the drivers just fine!


That just helped me enormously.  Thanks for sharing that! :)

---

### Post by Dude_man on 2007-03-29
I may have overlooked this information, but do these tutorials apply to the 64 bit edition of Ubuntu? I have done a few methods, not this particular one, but a different one, and when I reboot I always get an error within the X system and I am then only able to use command line instead of getting a desktop. The error is quite messed up actually. There are many different unrecognizable characters spread throughout my screen and then an error message in the middle which is hardly readable. I dont recall what the message said, I am currently in school right now. Any ideas or answers? :)

---

### Post by tseliot on 2007-03-30
> **Dude_man said:**
> I may have overlooked this information, but do these tutorials apply to the 64 bit edition of Ubuntu? I have done a few methods, not this particular one, but a different one, and when I reboot I always get an error within the X system and I am then only able to use command line instead of getting a desktop. The error is quite messed up actually. There are many different unrecognizable characters spread throughout my screen and then an error message in the middle which is hardly readable. I dont recall what the message said, I am currently in school right now. Any ideas or answers? :)
Yes, it's aimed at 64bit users as well.


let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by Dude_man on 2007-03-30
Alright awesome. Thanks for the reply. I am currently at school again lol so I cant get this info atm. I work a lot so I dont have a lot of time. Atleast for this week. I will edit this post with the information you have requested as soon as I can. Again thanks for the help. Ill be back :)

---

### Post by badhat on 2007-04-03
Hello, I can't seem to get the driver working, although it was working before. I have tried for many hours, tried everything I could think of. 

I'm running Edgy on a Toshiba laptop with a GeForce4 440 Go.  A couple months ago, I did get the nvidia driver working, thanks to your Latest Nvidia Edgy howto :guitar:  (method 1, attention to problem 7).  Of course that gave me driver 1.0-8776.  Most everything was ok; the only new problem I saw was that the Synaptics device would crash often when I logged out (it still does, even with the nv driver).

Last Saturday, I used Envy 0.9.1 to try and upgrade the driver to 1.0-9631.  It did try to install that version, but something went wrong and X would not start.  Since then I've tried many installs and uninstalls, including Method 2 from the howto, and most recently Method 1 again, but no success.

I just did the diagnostic you suggested to Dude_man.  After startx, there was an error message onscreen that did not make it to the log file.  I think it said,

```
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9631, but
this X module has the version 1.0-8776.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.

```

(edit: I just read techstop's reply to a post from about about a week ago, where zeroooooooooooo was getting a similar error message.  I will try the suggestion (envy -t; select 6 to remove any nvidia drivers) and let you know that happens.)

Here is the log file:

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux blue-moon 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  3 07:00:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 440 Go]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 3

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 1179,0001 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2482 card 1179,0001 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2484 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2487 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,248c card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,248a card 1179,0001 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,2485 card 1179,0002 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,2486 card 1179,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0174 card 1179,0001 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 104c,8023 card 1179,0001 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:08:0: chip 8086,1031 card 1179,0001 rev 42 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 168c,0013 card 144f,7064 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 1179,0617 card d000,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0b:1: chip 1179,0617 card d800,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0c:0: chip 1179,0804 card 1179,0001 rev 03 class 08,80,00 hdr 00
(II) PCI: 02:0d:0: chip 1179,0805 card 1179,0001 rev 03 class 08,80,00 hdr 00
(II) PCI: 03:00:0: chip 1033,0035 card 9710,0035 rev 43 class 0c,03,10 hdr 80
(II) PCI: 03:00:1: chip 1033,0035 card 9710,0035 rev 43 class 0c,03,10 hdr 00
(II) PCI: 03:00:2: chip 1033,00e0 card 9710,1906 rev 04 class 0c,03,20 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd7f00000 - 0xdfffffff (0x8100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,8), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfce00000 - 0xfcefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x43ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:11:0), (2,3,4), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x41ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (2:11:1), (2,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[1] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x42000000 - 0x43ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 440 Go] rev 163, Mem @ 0xfd000000/24, 0xd8000000/27, 0xd7f80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
	[1] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
	[2] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
	[3] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
	[4] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[5] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
	[6] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
	[7] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[13] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[18] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[19] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[20] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[21] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
	[1] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
	[1] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
	[2] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
	[3] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
	[4] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[5] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
	[6] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
	[7] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[13] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[18] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[19] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[20] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[21] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
	[1] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
	[5] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
	[6] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
	[7] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
	[8] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[9] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
	[10] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
	[11] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
	[17] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[21] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[24] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[25] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[26] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[27] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[28] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[29] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[30] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[31] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[32] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
	[5] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
	[6] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
	[7] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
	[8] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[9] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
	[10] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
	[11] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
	[17] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[21] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[24] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[25] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[26] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[27] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[28] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[29] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[30] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[31] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[32] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
	[5] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
	[6] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
	[7] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
	[8] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[9] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
	[10] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
	[11] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
	[17] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[24] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[25] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[26] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[27] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[28] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[29] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[30] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[31] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[32] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[33] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[34] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[35] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "ExactModeTimingsDVI" "TRUE"
(**) NVIDIA(0): Option "UseEdidDpi" "false"
(**) NVIDIA(0): Option "DPI" "133 x 133"
(**) NVIDIA(0): Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x83e
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

(Although I addressed this message to tseliot, I welcome all replies.)
Thanks!
BadHat

---

### Post by badhat on 2007-04-03
Again I did envy -t, "6 - Clean the Installation of any Nvidia driver", then "1 - Install the NVIDIA driver".  But the nvidia drivers are still not working ](*,) 

With startx, this time I don't see the message about the api mismatch.

The new log file is about twice as long, too long to post in one message.
Xorg.0.log, part 1:

```

	
	X Window System Version 7.1.1
	Release Date: 12 May 2006
	X Protocol Version 11, Revision 0, Release 7.1.1
	Build Operating System: Linux 2.6.15.7 i686 
	Current Operating System: Linux blue-moon 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
	Build Date: 07 July 2006
		Before reporting problems, check http://wiki.x.org
		to make sure that you have the latest version.
	Module Loader present
	Markers: (--) probed, (**) from config file, (==) default setting,
		(++) from command line, (!!) notice, (II) informational,
		(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
	(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  3 10:01:33 2007
	(==) Using config file: "/etc/X11/xorg.conf"
	(==) ServerLayout "Default Layout"
	(**) |-->Screen "Default Screen" (0)
	(**) |   |-->Monitor "Generic Monitor"
	(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 440 Go]"
	(**) |-->Input Device "Generic Keyboard"
	(**) |-->Input Device "Configured Mouse"
	(**) |-->Input Device "stylus"
	(**) |-->Input Device "cursor"
	(**) |-->Input Device "eraser"
	(**) |-->Input Device "Synaptics Touchpad"
	(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
		Entry deleted from font path.
	(**) FontPath set to:
		/usr/share/X11/fonts/misc,
		/usr/share/X11/fonts/100dpi/:unscaled,
		/usr/share/X11/fonts/75dpi/:unscaled,
		/usr/share/X11/fonts/Type1,
		/usr/share/X11/fonts/100dpi,
		/usr/share/X11/fonts/75dpi,
		/usr/share/fonts/X11/misc,
		/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
		/usr/share/fonts/X11/misc/,
		/usr/share/fonts/X11/TTF/,
		/usr/share/fonts/X11/OTF,
		/usr/share/fonts/X11/Type1/,
		/usr/share/fonts/X11/CID/,
		/usr/share/fonts/X11/100dpi/,
		/usr/share/fonts/X11/75dpi/
	(==) RgbPath set to "/usr/share/X11/rgb"
	(==) ModulePath set to "/usr/lib/xorg/modules"
	(**) Extension "Composite" is enabled
	(II) Open ACPI successful (/var/run/acpid.socket)
	(II) Module ABI versions:
		X.Org ANSI C Emulation: 0.3
		X.Org Video Driver: 1.0
		X.Org XInput driver : 0.6
		X.Org Server Extension : 0.3
		X.Org Font Renderer : 0.5
	(II) Loader running on linux
	(II) LoadModule: "bitmap"
	(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
	(II) Module bitmap: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.0.0
		Module class: X.Org Font Renderer
		ABI class: X.Org Font Renderer, version 0.5
	(II) Loading font Bitmap
	(II) LoadModule: "pcidata"
	(II) Loading /usr/lib/xorg/modules/libpcidata.so
	(II) Module pcidata: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.0.0
		ABI class: X.Org Video Driver, version 1.0
	(--) using VT number 3
	
	(II) PCI: PCI scan (all values are in hex)
	(II) PCI: 00:00:0: chip 8086,1a30 card 1179,0001 rev 04 class 06,00,00 hdr 00
	(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
	(II) PCI: 00:1d:0: chip 8086,2482 card 1179,0001 rev 02 class 0c,03,00 hdr 80
	(II) PCI: 00:1d:1: chip 8086,2484 card 1179,0001 rev 02 class 0c,03,00 hdr 00
	(II) PCI: 00:1d:2: chip 8086,2487 card 1179,0001 rev 02 class 0c,03,00 hdr 00
	(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
	(II) PCI: 00:1f:0: chip 8086,248c card 0000,0000 rev 02 class 06,01,00 hdr 80
	(II) PCI: 00:1f:1: chip 8086,248a card 1179,0001 rev 02 class 01,01,8a hdr 00
	(II) PCI: 00:1f:5: chip 8086,2485 card 1179,0002 rev 02 class 04,01,00 hdr 00
	(II) PCI: 00:1f:6: chip 8086,2486 card 1179,0001 rev 02 class 07,03,00 hdr 00
	(II) PCI: 01:00:0: chip 10de,0174 card 1179,0001 rev a3 class 03,00,00 hdr 00
	(II) PCI: 02:07:0: chip 104c,8023 card 1179,0001 rev 00 class 0c,00,10 hdr 00
	(II) PCI: 02:08:0: chip 8086,1031 card 1179,0001 rev 42 class 02,00,00 hdr 00
	(II) PCI: 02:0a:0: chip 168c,0013 card 144f,7064 rev 01 class 02,00,00 hdr 00
	(II) PCI: 02:0b:0: chip 1179,0617 card d000,0000 rev 32 class 06,07,00 hdr 82
	(II) PCI: 02:0b:1: chip 1179,0617 card d800,0000 rev 32 class 06,07,00 hdr 82
	(II) PCI: 02:0c:0: chip 1179,0804 card 1179,0001 rev 03 class 08,80,00 hdr 00
	(II) PCI: 02:0d:0: chip 1179,0805 card 1179,0001 rev 03 class 08,80,00 hdr 00
	(II) PCI: 03:00:0: chip 1033,0035 card 9710,0035 rev 43 class 0c,03,10 hdr 80
	(II) PCI: 03:00:1: chip 1033,0035 card 9710,0035 rev 43 class 0c,03,10 hdr 00
	(II) PCI: 03:00:2: chip 1033,00e0 card 9710,1906 rev 04 class 0c,03,20 hdr 00
	(II) PCI: End of PCI scan
	(II) Intel Bridge workaround enabled
	(II) Host-to-PCI bridge:
	(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
	(II) Bus 0 I/O range:
		[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
	(II) Bus 0 non-prefetchable memory range:
		[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	(II) Bus 0 prefetchable memory range:
		[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	(II) PCI-to-PCI bridge:
	(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
	(II) Bus 1 non-prefetchable memory range:
		[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	(II) Bus 1 prefetchable memory range:
		[0] -1	0	0xd7f00000 - 0xdfffffff (0x8100000) MX[B]
	(II) Subtractive PCI-to-PCI bridge:
	(II) Bus 2: bridge is at (0:30:0), (0,2,8), BCTRL: 0x0000 (VGA_EN is cleared)
	(II) Bus 2 I/O range:
		[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
	(II) Bus 2 non-prefetchable memory range:
		[0] -1	0	0xfce00000 - 0xfcefffff (0x100000) MX[B]
	(II) Bus 2 prefetchable memory range:
		[0] -1	0	0x40000000 - 0x43ffffff (0x4000000) MX[B]
	(II) PCI-to-ISA bridge:
	(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
	(II) PCI-to-CardBus bridge:
	(II) Bus 3: bridge is at (2:11:0), (2,3,4), BCTRL: 0x0500 (VGA_EN is cleared)
	(II) Bus 3 I/O range:
		[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
		[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	(II) Bus 3 prefetchable memory range:
		[0] -1	0	0x40000000 - 0x41ffffff (0x2000000) MX[B]
	(II) PCI-to-CardBus bridge:
	(II) Bus 5: bridge is at (2:11:1), (2,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
	(II) Bus 5 I/O range:
		[0] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
		[1] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	(II) Bus 5 prefetchable memory range:
		[0] -1	0	0x42000000 - 0x43ffffff (0x2000000) MX[B]
	(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 440 Go] rev 163, Mem @ 0xfd000000/24, 0xd8000000/27, 0xd7f80000/19
	(II) Addressable bus resource ranges are
		[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
		[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
	(II) OS-reported resource ranges:
		[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
		[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
		[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
	(II) Active PCI resource ranges:
		[0] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
		[1] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
		[2] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
		[3] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
		[4] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
		[5] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
		[6] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
		[7] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
		[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
		[9] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
		[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
		[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
		[12] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
		[13] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
		[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
		[15] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
		[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
		[17] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
		[18] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
		[19] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
		[20] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
		[21] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
		[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
		[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
		[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	(II) Inactive PCI resource ranges:
		[0] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
		[1] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
	(II) Active PCI resource ranges after removing overlaps:
		[0] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
		[1] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
		[2] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
		[3] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
		[4] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
		[5] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
		[6] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
		[7] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
		[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
		[9] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
		[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
		[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
		[12] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
		[13] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
		[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
		[15] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
		[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
		[17] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
		[18] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
		[19] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
		[20] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
		[21] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
		[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
		[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
		[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	(II) Inactive PCI resource ranges after removing overlaps:
		[0] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
		[1] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
	(II) OS-reported resource ranges after removing overlaps with PCI:
		[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
		[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
		[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	(II) All system resource ranges:
		[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
		[4] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
		[5] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
		[6] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
		[7] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
		[8] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
		[9] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
		[10] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
		[11] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
		[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
		[13] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
		[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
		[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
		[16] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
		[17] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
		[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
		[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
		[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
		[21] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
		[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
		[23] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
		[24] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
		[25] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
		[26] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
		[27] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
		[28] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
		[29] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
		[30] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
		[31] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
		[32] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	(II) LoadModule: "i2c"
	(II) Loading /usr/lib/xorg/modules/libi2c.so
	(II) Module i2c: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.2.0
		ABI class: X.Org Video Driver, version 1.0
	(II) LoadModule: "bitmap"
	(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
	(II) Loading font Bitmap
	(II) LoadModule: "ddc"
	(II) Loading /usr/lib/xorg/modules/libddc.so
	(II) Module ddc: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.0.0
		ABI class: X.Org Video Driver, version 1.0
	(II) LoadModule: "extmod"
	(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
	(II) Module extmod: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.0.0
		Module class: X.Org Server Extension
		ABI class: X.Org Server Extension, version 0.3
	(II) Loading extension SHAPE
	(II) Loading extension MIT-SUNDRY-NONSTANDARD
	(II) Loading extension BIG-REQUESTS
	(II) Loading extension SYNC
	(II) Loading extension MIT-SCREEN-SAVER
	(II) Loading extension XC-MISC
	(II) Loading extension XFree86-VidModeExtension
	(II) Loading extension XFree86-Misc
	(II) Loading extension XFree86-DGA
	(II) Loading extension DPMS
	(II) Loading extension TOG-CUP
	(II) Loading extension Extended-Visual-Information
	(II) Loading extension XVideo
	(II) Loading extension XVideo-MotionCompensation
	(II) Loading extension X-Resource
	(II) LoadModule: "freetype"
	(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
	(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
		compiled for 7.1.1, module version = 2.1.0
		Module class: X.Org Font Renderer
		ABI class: X.Org Font Renderer, version 0.5
	(II) Loading font FreeType
	(II) LoadModule: "glx"
	(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
	(II) Module glx: vendor="NVIDIA Corporation"
		compiled for 4.0.2, module version = 1.0.9631
		Module class: X.Org Server Extension
		ABI class: X.Org Server Extension, version 0.1
	(II) Loading extension GLX
	(II) LoadModule: "int10"
	(II) Loading /usr/lib/xorg/modules/libint10.so
	(II) Module int10: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.0.0
		ABI class: X.Org Video Driver, version 1.0
	(II) LoadModule: "type1"
	(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
	(II) Module type1: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.0.2
		Module class: X.Org Font Renderer
		ABI class: X.Org Font Renderer, version 0.5
	(II) Loading font Type1
	(II) LoadModule: "vbe"
	(II) Loading /usr/lib/xorg/modules/libvbe.so
	(II) Module vbe: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.1.0
		ABI class: X.Org Video Driver, version 1.0
	(II) LoadModule: "nvidia"
	(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
	(II) Module nvidia: vendor="NVIDIA Corporation"
		compiled for 4.0.2, module version = 1.0.9631
		Module class: X.Org Video Driver
	(II) LoadModule: "kbd"
	(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
	(II) Module kbd: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.1.0
		Module class: X.Org XInput Driver
		ABI class: X.Org XInput driver, version 0.6
	(II) LoadModule: "mouse"
	(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
	(II) Module mouse: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.1.1
		Module class: X.Org XInput Driver
		ABI class: X.Org XInput driver, version 0.6
	(II) LoadModule: "wacom"
	(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
	(II) Module wacom: vendor="X.Org Foundation"
		compiled for 4.3.99.902, module version = 1.0.0
		Module class: X.Org XInput Driver
		ABI class: X.Org XInput driver, version 0.6
	(II) Wacom driver level: 47-0.7.2 $
	(II) LoadModule: "synaptics"
	(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
	(II) Module synaptics: vendor="The XFree86 Project"
		compiled for 4.2.0, module version = 1.0.0
		Module class: XFree86 XInput Driver
		ABI class: XFree86 XInput driver, version 0.3
	(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
	(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
	(II) Primary Device is: PCI 01:00:0
	(--) Assigning device section with no busID to primary device
	(--) Chipset NVIDIA GPU found
	(II) NVIDIA(0): Found 1 NVIDIA X Screens
	(II) Loading sub module "fb"
	(II) LoadModule: "fb"
	(II) Loading /usr/lib/xorg/modules/libfb.so
	(II) Module fb: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 1.0.0
		ABI class: X.Org ANSI C Emulation, version 0.3
	(II) Loading sub module "ramdac"
	(II) LoadModule: "ramdac"
	(II) Loading /usr/lib/xorg/modules/libramdac.so
	(II) Module ramdac: vendor="X.Org Foundation"
		compiled for 7.1.1, module version = 0.1.0
		ABI class: X.Org Video Driver, version 1.0
	(II) resource ranges after xf86ClaimFixedResources() call:
		[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
		[4] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
		[5] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
		[6] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
		[7] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
		[8] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
		[9] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
		[10] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
		[11] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
		[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
		[13] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
		[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
		[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
		[16] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
		[17] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
		[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
		[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
		[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
		[21] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
		[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
		[23] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
		[24] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
		[25] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
		[26] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
		[27] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
		[28] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
		[29] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
		[30] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
		[31] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
		[32] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	(II) resource ranges after probing:
		[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
		[4] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
		[5] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
		[6] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
		[7] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
		[8] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
		[9] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
		[10] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
		[11] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
		[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
		[13] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
		[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
		[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
		[16] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
		[17] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
		[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
		[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
		[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
		[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
		[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
		[23] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
		[24] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
		[25] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
		[26] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
		[27] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
		[28] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
		[29] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
		[30] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
		[31] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
		[32] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
		[33] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
		[34] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
		[35] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
		[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
		[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

```

BadHat

---

### Post by badhat on 2007-04-03
Xorg.0.log, part 2:

```
	(II) Setting vga for screen 0.
	(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
	(==) NVIDIA(0): RGB weight 565
	(==) NVIDIA(0): Default visual is TrueColor
	(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
	(**) NVIDIA(0): Option "NoLogo" "true"
	(**) NVIDIA(0): Option "ExactModeTimingsDVI" "TRUE"
	(**) NVIDIA(0): Option "UseEdidDpi" "false"
	(**) NVIDIA(0): Option "DPI" "133 x 133"
	(**) NVIDIA(0): Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
	(==) NVIDIA(0): Using HW cursor
	(**) NVIDIA(0): Enabling RENDER acceleration
	(==) NVIDIA(0): Video key set to default value of 0x83e
	(WW) NVIDIA(0): Unrecognized ModeValidation token "NoEdidDFPMaxSizeCheck";
	(WW) NVIDIA(0):     ignoring.
	(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
	(II) NVIDIA(0):     enabled.
	(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
	(II) NVIDIA(0): NVIDIA GPU GeForce4 440 Go at PCI:1:0:0 (GPU-0)
	(--) NVIDIA(0): Memory: 65536 kBytes
	(II) NVIDIA(0): GPU Architecture: 0x10
	(II) NVIDIA(0): GPU Implementation: 0x17
	(II) NVIDIA(0): GPU Revision: 0xa4
	(--) NVIDIA(0): VideoBIOS: 04.17.00.41.c5
	(--) NVIDIA(0): Found 2 CRTCs on board
	(II) NVIDIA(0): Supported display device(s): CRT-0, DFP-0, TV-0
	(II) NVIDIA(0): Bus detected as AGP
	(II) NVIDIA(0): Detected AGP rate: 4X
	(--) NVIDIA(0): Interlaced video modes are supported on this GPU
	(II) NVIDIA(0): 
	(II) NVIDIA(0): Mode timing constraints for  : GeForce4 440 Go
	(II) NVIDIA(0): Maximum mode timing values   :
	(II) NVIDIA(0):     Horizontal Visible Width : 8192
	(II) NVIDIA(0):     Horizontal Blank Start   : 8192
	(II) NVIDIA(0):     Horizontal Blank Width   : 4096
	(II) NVIDIA(0):     Horizontal Sync Start    : 8184
	(II) NVIDIA(0):     Horizontal Sync Width    : 504
	(II) NVIDIA(0):     Horizontal Total Width   : 8224
	(II) NVIDIA(0):     Vertical Visible Height  : 8192
	(II) NVIDIA(0):     Vertical Blank Start     : 8192
	(II) NVIDIA(0):     Vertical Blank Width     : 256
	(II) NVIDIA(0):     Veritcal Sync Start      : 8191
	(II) NVIDIA(0):     Vertical Sync Width      : 15
	(II) NVIDIA(0):     Vertical Total Height    : 8193
	(II) NVIDIA(0): 
	(II) NVIDIA(0): Minimum mode timing values   :
	(II) NVIDIA(0):     Horizontal Total Width   : 40
	(II) NVIDIA(0):     Vertical Total Height    : 2
	(II) NVIDIA(0): 
	(II) NVIDIA(0): Mode timing alignment        :
	(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
	(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
	(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
	(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
	(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
	(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
	(II) NVIDIA(0): 
	(--) NVIDIA(0): Connected display device(s) on GeForce4 440 Go at PCI:1:0:0:
	(--) NVIDIA(0):     CRT-0
	(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
	(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
	(--) NVIDIA(0): 
	(--) NVIDIA(0): --- EDID for CRT-0 ---
	(--) NVIDIA(0): 
	(--) NVIDIA(0): No EDID Available.
	(--) NVIDIA(0): 
	(--) NVIDIA(0): --- End of EDID for CRT-0 ---
	(--) NVIDIA(0): 
	(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 224.0 MHz maximum pixel
	(--) NVIDIA(0):     clock
	(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
	(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Native FlatPanel Scaling is
	(--) NVIDIA(0):     not supported
	(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): DFP modes are not limited
	(--) NVIDIA(0):     to 60 Hz refresh rate
	(--) NVIDIA(0): 
	(--) NVIDIA(0): --- EDID for Nvidia Default Flat Panel (DFP-0) ---
	(--) NVIDIA(0): EDID Version                 : 1.3
	(--) NVIDIA(0): Manufacturer                 : NVD
	(--) NVIDIA(0): Monitor Name                 : Nvidia Default Flat Panel
	(--) NVIDIA(0): Product ID                   : 1024
	(--) NVIDIA(0): 32-bit Serial Number         : 0
	(--) NVIDIA(0): Serial Number String         : 
	(--) NVIDIA(0): Manufacture Date             : 2002, week 45
	(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
	(--) NVIDIA(0): Prefer first detailed timing : Yes
	(--) NVIDIA(0): Supports GTF                 : No
	(--) NVIDIA(0): Maximum Image Size           : 320mm x 240mm
	(--) NVIDIA(0): Valid HSync Range            : 29 kHz - 76 kHz
	(--) NVIDIA(0): Valid VRefresh Range         : 0 Hz - 60 Hz
	(--) NVIDIA(0): EDID maximum pixel clock     : 170.0 MHz
	(--) NVIDIA(0): 
	(--) NVIDIA(0): Detailed Timings:
	(--) NVIDIA(0):   1588 x 1200 @ 60 Hz
	(--) NVIDIA(0):     Pixel Clock      : 162.00 MHz
	(--) NVIDIA(0):     HRes, HSyncStart : 1588, 1664
	(--) NVIDIA(0):     HSyncEnd, HTotal : 1856, 2160
	(--) NVIDIA(0):     VRes, VSyncStart : 1200, 1201
	(--) NVIDIA(0):     VSyncEnd, VTotal : 1204, 1250
	(--) NVIDIA(0):     H/V Polarity     : +/+
	(--) NVIDIA(0): 
	(--) NVIDIA(0): --- End of EDID for Nvidia Default Flat Panel (DFP-0) ---
	(--) NVIDIA(0): 
	(II) NVIDIA(0): Frequency information for CRT-0:
	(II) NVIDIA(0):   HorizSync   : 28.000-80.000 kHz
	(II) NVIDIA(0):   VertRefresh : 43.000-60.000 Hz
	(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
	(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
	(II) NVIDIA(0):     section)
	(II) NVIDIA(0): 
	(II) NVIDIA(0): --- Modes in ModePool for CRT-0 ---
	(II) NVIDIA(0): "nvidia-auto-select" : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1920x1200"          : 1920 x 1200 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1920x1200_60"       : 1920 x 1200 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1680x1050"          : 1680 x 1050 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1680x1050_60"       : 1680 x 1050 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1600x1200"          : 1600 x 1200 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1600x1200_60"       : 1600 x 1200 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1600x1024"          : 1600 x 1024 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1600x1024_60"       : 1600 x 1024 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1440x900"           : 1440 x  900 @  60.2 Hz  (from: X Server)
	(II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  60.2 Hz  (from: X Server)
	(II) NVIDIA(0): "1400x1050"          : 1400 x 1050 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1400x1050_60"       : 1400 x 1050 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1280x1024_60"       : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1280x800"           : 1280 x  800 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1280x800_60"        : 1280 x  800 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1280x768"           : 1280 x  768 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1280x768_60"        : 1280 x  768 @  60.0 Hz  (from: X Server)
	(II) NVIDIA(0): "1152x768"           : 1152 x  768 @  54.8 Hz  (from: X Server)
	(II) NVIDIA(0): "1152x768_55"        : 1152 x  768 @  54.8 Hz  (from: X Server)
	(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "960x600d60"         :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "840x525"            :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "840x525d60"         :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "800x600"            :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
	(II) NVIDIA(0): "800x512"            :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "800x512d60"         :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "720x450"            :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "720x450d60"         :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x512"            :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  60.0 Hz  (from: VESA)
	(II) NVIDIA(0): "640x400"            :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x400d60"         :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x384"            :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "640x384d60"         :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "576x384"            :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "576x384d55"         :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "512x384"            :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "400x300"            :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "320x240"            :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
	(II) NVIDIA(0): --- End of ModePool for CRT-0: ---
	(II) NVIDIA(0): 
	(II) NVIDIA(0): Assigned Display Device: CRT-0
	(II) NVIDIA(0): Requested modes:
	(II) NVIDIA(0):     "1600x1200"
	(II) NVIDIA(0): Validated modes:
	(II) NVIDIA(0): MetaMode "1600x1200":
	(II) NVIDIA(0):     Bounding Box: [0, 0, 1600, 1200]
	(II) NVIDIA(0):     CRT-0: "1600x1200"
	(II) NVIDIA(0):         Size          : 1600 x 1200
	(II) NVIDIA(0):         Offset        : +0 +0
	(II) NVIDIA(0):         Panning Domain: @ 1600 x 1200
	(II) NVIDIA(0):         Position      : [0, 0, 1600, 1200]
	(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
	(II) NVIDIA(0): 
	(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
	(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
	(II) NVIDIA(0): 
	(II) NVIDIA(0): "nvidia-auto-select" : 1024 x  768 @  60.0 Hz 
	(II) NVIDIA(0): "1600x1024"          : 1600 x 1024 @  60.0 Hz 
	(II) NVIDIA(0): "1440x900"           : 1440 x  900 @  60.2 Hz 
	(II) NVIDIA(0): "1400x1050"          : 1400 x 1050 @  60.0 Hz 
	(II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  60.0 Hz 
	(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz 
	(II) NVIDIA(0): "1280x800"           : 1280 x  800 @  60.0 Hz 
	(II) NVIDIA(0): "1280x768"           : 1280 x  768 @  60.0 Hz 
	(II) NVIDIA(0): "1152x768"           : 1152 x  768 @  54.8 Hz 
	(II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan 
	(II) NVIDIA(0): "840x525"            :  840 x  525 @  60.1 Hz DoubleScan 
	(II) NVIDIA(0): "800x600"            :  800 x  600 @  60.3 Hz 
	(II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan 
	(II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz 
	(II) NVIDIA(0): "800x512"            :  800 x  512 @  60.0 Hz DoubleScan 
	(II) NVIDIA(0): "720x450"            :  720 x  450 @  60.2 Hz DoubleScan 
	(II) NVIDIA(0): "640x512"            :  640 x  512 @  60.0 Hz DoubleScan 
	(II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan 
	(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  60.0 Hz 
	(II) NVIDIA(0): "640x400"            :  640 x  400 @  60.0 Hz DoubleScan 
	(II) NVIDIA(0): "640x384"            :  640 x  384 @  60.1 Hz DoubleScan 
	(II) NVIDIA(0): "576x384"            :  576 x  384 @  54.8 Hz DoubleScan 
	(II) NVIDIA(0): "512x384"            :  512 x  384 @  60.0 Hz DoubleScan 
	(II) NVIDIA(0): "400x300"            :  400 x  300 @  60.3 Hz DoubleScan 
	(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan 
	(II) NVIDIA(0): "320x240"            :  320 x  240 @  60.1 Hz DoubleScan 
	(II) NVIDIA(0): 
	(**) NVIDIA(0): DPI set to (133, 133); computed from "DPI" X config option
	(II) do I need RAC?  No, I don't.
	(II) resource ranges after preInit:
		[0] 0	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B]
		[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
		[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
		[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
		[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
		[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
		[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
		[7] -1	0	0x46002000 - 0x460020ff (0x100) MX[B]
		[8] -1	0	0x46001000 - 0x46001fff (0x1000) MX[B]
		[9] -1	0	0x46000000 - 0x46000fff (0x1000) MX[B]
		[10] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
		[11] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
		[12] -1	0	0xfce10000 - 0xfce13fff (0x4000) MX[B]
		[13] -1	0	0xfce16000 - 0xfce167ff (0x800) MX[B]
		[14] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
		[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
		[16] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
		[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
		[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
		[19] -1	0	0xfce16800 - 0xfce169ff (0x200) MX[B]
		[20] -1	0	0xfce16a00 - 0xfce16a1f (0x20) MX[B]
		[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
		[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
		[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
		[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
		[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
		[26] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
		[27] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
		[28] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
		[29] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
		[30] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
		[31] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
		[32] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
		[33] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
		[34] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
		[35] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
		[36] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
		[37] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
		[38] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
		[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
		[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	(II) NVIDIA(0): kernel module enabled successfully
	(II) NVIDIA(0): Memory mapped
	(II) NVIDIA(0): Interrupts enabled
	(II) NVIDIA(0): Setting mode "1600x1200"
	(II) NVIDIA(0): CRT-0 assigned CRTC 0
	(II) NVIDIA(0): First mode initialized
	(II) Loading extension NV-GLX
	(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
	(II) NVIDIA(0): Visuals set up
	(II) NVIDIA(0): Pixmap depths set up
	(II) NVIDIA(0): GLX visuals set up
	(II) NVIDIA(0): Framebuffer set up
	(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
	(==) NVIDIA(0): Backing store disabled
	(==) NVIDIA(0): Silken mouse enabled
	(II) NVIDIA(0): Default colormap initialized.
	(II) NVIDIA(0): Palette loaded
	(**) Option "dpms"
	(**) NVIDIA(0): DPMS enabled
	(II) Loading extension NV-CONTROL
	(II) NVIDIA(0): Screen initialization complete
	(==) RandR enabled
	(II) Initializing built-in extension MIT-SHM
	(II) Initializing built-in extension XInputExtension
	(II) Initializing built-in extension XTEST
	(II) Initializing built-in extension XKEYBOARD
	(II) Initializing built-in extension XC-APPGROUP
	(II) Initializing built-in extension SECURITY
	(II) Initializing built-in extension XINERAMA
	(II) Initializing built-in extension XFIXES
	(II) Initializing built-in extension XFree86-Bigfont
	(II) Initializing built-in extension RENDER
	(II) Initializing built-in extension RANDR
	(II) Initializing built-in extension COMPOSITE
	(II) Initializing built-in extension DAMAGE
	(II) Initializing built-in extension XEVIE
	(II) Initializing extension GLX
	error opening security policy file /usr/lib/xserver/SecurityPolicy
	(**) Option "CoreKeyboard"
	(**) Generic Keyboard: Core Keyboard
	(**) Option "Protocol" "standard"
	(**) Generic Keyboard: Protocol: standard
	(**) Option "AutoRepeat" "500 30"
	(**) Option "XkbRules" "xorg"
	(**) Generic Keyboard: XkbRules: "xorg"
	(**) Option "XkbModel" "pc104"
	(**) Generic Keyboard: XkbModel: "pc104"
	(**) Option "XkbLayout" "us"
	(**) Generic Keyboard: XkbLayout: "us"
	(**) Option "CustomKeycodes" "off"
	(**) Generic Keyboard: CustomKeycodes disabled
	(**) Option "Protocol" "ExplorerPS/2"
	(**) Configured Mouse: Device: "/dev/input/mice"
	(**) Configured Mouse: Protocol: "ExplorerPS/2"
	(**) Option "CorePointer"
	(**) Configured Mouse: Core Pointer
	(**) Option "Device" "/dev/input/mice"
	(**) Option "Emulate3Buttons" "true"
	(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
	(**) Option "ZAxisMapping" "4 5"
	(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
	(**) Configured Mouse: Buttons: 9
	(**) Option "SendCoreEvents"
	(**) stylus: always reports core events
	(**) stylus device is /dev/wacom
	(**) stylus is in absolute mode
	(**) stylus: forcing TabletPC ISD V4 protocol
	(**) WACOM: suppress value is 2
	(**) Option "BaudRate" "9600"
	(**) stylus: serial speed 9600
	(**) Option "SendCoreEvents"
	(**) cursor: always reports core events
	(**) cursor device is /dev/wacom
	(**) cursor is in relative mode
	(**) cursor: forcing TabletPC ISD V4 protocol
	(**) WACOM: suppress value is 2
	(**) Option "BaudRate" "9600"
	(**) cursor: serial speed 9600
	(**) Option "SendCoreEvents"
	(**) eraser: always reports core events
	(**) eraser device is /dev/wacom
	(**) eraser is in absolute mode
	(**) eraser: forcing TabletPC ISD V4 protocol
	(**) WACOM: suppress value is 2
	(**) Option "BaudRate" "9600"
	(**) eraser: serial speed 9600
	(II) Synaptics touchpad driver version 0.14.6 (1406)
		Option "SendCoreEvents" "true"
		Option "Device" "/dev/psaux"
		Option "Protocol" "auto-dev"
		Option "HorizScrollDelta" "0"
	(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
	(**) Option "Device" "/dev/input/event2"
	(**) Option "HorizScrollDelta" "0"
	(--) Synaptics Touchpad touchpad found
	(**) Option "SendCoreEvents" "true"
	(**) Synaptics Touchpad: always reports core events
	(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
	(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
	(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
	(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
	(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
	(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
	(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
	(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
	(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
	xkb_keycodes             { include "xfree86+aliases(qwerty)" };
	xkb_types                { include "complete" };
	xkb_compatibility        { include "complete" };
	xkb_symbols              { include "pc(pc104)+us" };
	xkb_geometry             { include "pc(pc104)" };
	(**) Option "Device" "/dev/wacom"
	(EE) xf86OpenSerial: Cannot open device /dev/wacom
		No such file or directory.
	Error opening /dev/wacom : Invalid argument
	(**) Option "Device" "/dev/wacom"
	(EE) xf86OpenSerial: Cannot open device /dev/wacom
		No such file or directory.
	Error opening /dev/wacom : Invalid argument
	(**) Option "Device" "/dev/wacom"
	(EE) xf86OpenSerial: Cannot open device /dev/wacom
		No such file or directory.
	Error opening /dev/wacom : Invalid argument
	(**) Option "Device" "/dev/wacom"
	(EE) xf86OpenSerial: Cannot open device /dev/wacom
		No such file or directory.
	Error opening /dev/wacom : Invalid argument
	(**) Option "Device" "/dev/wacom"
	(EE) xf86OpenSerial: Cannot open device /dev/wacom
		No such file or directory.
	Error opening /dev/wacom : Invalid argument
	(**) Option "Device" "/dev/wacom"
	(EE) xf86OpenSerial: Cannot open device /dev/wacom
		No such file or directory.
	Error opening /dev/wacom : Invalid argument
	Synaptics DeviceInit called
	SynapticsCtrl called.
	(**) Option "Device" "/dev/input/mice"
	(II) Configured Mouse: ps2EnableDataReporting: succeeded
	Synaptics DeviceOn called
	(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
	(**) Option "Device" "/dev/input/event2"
	(--) Synaptics Touchpad touchpad found
	Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
	Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
	Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
	Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
	Synaptics DeviceOff called
	
	Backtrace:
	0: /usr/bin/X(xf86SigHandler+0x81) [0x80c3971]
	1: [0xffffe420]
	
	Fatal server error:
	Caught signal 11.  Server aborting

```

It's weird how nvidia drivers can be as hard as all the other setups put together. 

I would appreciate any help about what to try, how to diagnose why I can't get the drivers working again, why I can't even go back to 8776... :confused: ...which *was* working for two months.

Of course I should have backed things up first ...FLW!  I have done way too much installing and customizing on this Kubuntu system, to think of starting over. I do make a backup of the entire partition, every so often, but not in the last two months :( 

I have tried to include everything relevant I could think of, here and in the previous two posts.
BadHat

---

### Post by ethoslite on 2007-04-04
Excellent howto, tseliot.  Thank you.

---

### Post by rameshg87 on 2007-04-04
Hi,

   I have Geforce 4 MX 440 with AGP 8x on my computer. I recently installed Ubuntu 6.10 EDGY. I followed the instructions in

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#HOWTO:_Latest_NVIDIA_drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#HOWTO:_Latest_NVIDIA_drivers)

to install the nvidia accelarated drivers. In the page it is said that those who own "GeForce4 420/440" should follow the point 7 in the problems section. I think I almost tried all the possible combinations in problem 7, but I cannot start the Xserver with the "nvidia" driver. Somebody who has got it to work in this graphic card please help me with the correct steps . Now what I have is a black screen with a cursor when I start the xserver with nvidia driver......  PLEASE HELP ME !!!!

---

### Post by tseliot on 2007-04-05
> **rameshg87 said:**
> Hi,

   I have Geforce 4 MX 440 with AGP 8x on my computer. I recently installed Ubuntu 6.10 EDGY. I followed the instructions in

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#HOWTO:_Latest_NVIDIA_drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#HOWTO:_Latest_NVIDIA_drivers)

to install the nvidia accelarated drivers. In the page it is said that those who own "GeForce4 420/440" should follow the point 7 in the problems section. I think I almost tried all the possible combinations in problem 7, but I cannot start the Xserver with the "nvidia" driver. Somebody who has got it to work in this graphic card please help me with the correct steps . Now what I have is a black screen with a cursor when I start the xserver with nvidia driver......  PLEASE HELP ME !!!!
try point 4 of the Problems section

---

### Post by tseliot on 2007-04-05
> **badhat said:**
> Hello, I can't seem to get the driver working, although it was working before. I have tried for many hours, tried everything I could think of. 

I'm running Edgy on a Toshiba laptop with a GeForce4 440 Go.  A couple months ago, I did get the nvidia driver working, thanks to your Latest Nvidia Edgy howto :guitar:  (method 1, attention to problem 7).  Of course that gave me driver 1.0-8776.  Most everything was ok; the only new problem I saw was that the Synaptics device would crash often when I logged out (it still does, even with the nv driver).

Last Saturday, I used Envy 0.9.1 to try and upgrade the driver to 1.0-9631.  It did try to install that version, but something went wrong and X would not start.  Since then I've tried many installs and uninstalls, including Method 2 from the howto, and most recently Method 1 again, but no success.


Can you post Envy's log (/var/log/envy-installer.log)?

---

### Post by badhat on 2007-04-05
"envy-installer.log"

```
python pulse.py nvidia
root@blue-moon:/usr/share/envy# python pulse.py nvidia
Ubuntu Edgy 32bit
Your graphic card has been detected as a GeForce4 440 Go
Your graphic card is supported by the new legacy driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-11-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
Package nvidia-kernel-2.6.17-11-386 is not installed, so not removed
Package nvidia-glx-dev is not installed, so not removed
Package nvidia-kernel-source is not installed, so not removed
Package nvidia-legacy-kernel-source is not installed, so not removed
Package libgl1-mesa-dev is not installed, so not removed
Package mesa-common-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not installed, so not removed
Package nvidia-settings is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rm: cannot remove `/usr/src/nvidia*.deb': No such file or directory
rm: cannot remove `/usr/src/*.deb': No such file or directory
rm: cannot remove `/usr/src/modules/fglrx-kernel': No such file or directory
An installer has been detected
md5new: b0d721c962c4df1a028ae18416d7e862
md5sumold: b0d721c962c4df1a028ae18416d7e862
dpkg-buildpackage: source package is nvidia-graphics-drivers
dpkg-buildpackage: source version is 1.0.9631
dpkg-buildpackage: source changed by Alberto Milone (tseliot) <albertomilone@alice.it>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.0.9631
debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp build-kernel-stamp configure-stamp
dh_clean
rm -fr NVIDIA-Linux-x86-1.0-9631-pkg0  nvidia-kernel-source.tar.gz
 debian/rules build
rm -f debian/nvidia-kernel-source.README.Debian debian/control debian/copyright debian/nvidia-glx.links debian/nvidia-glx-dev.links debian/nvidia-glx.override debian/nvidia-glx.docs debian/nvidia-glx.examples debian/nvidia-glx.postrm debian/nvidia-glx.init debian/nvidia-glx-ia32.override debian/nvidia-glx-ia32.links debian/nvidia-kernel-source.docs debian/nvidia-glx-dev.preinst || true
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-kernel-source.README.Debian.in > debian/nvidia-kernel-source.README.Debian
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
< debian/control.in > debian/control
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/copyright.in > debian/copyright
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx.links.in > debian/nvidia-glx.links
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx-dev.links.in > debian/nvidia-glx-dev.links
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx.override.in > debian/nvidia-glx.override
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx.docs.in > debian/nvidia-glx.docs
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx.examples.in > debian/nvidia-glx.examples
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
< debian/nvidia-glx.postrm.in > debian/nvidia-glx.postrm
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
< debian/nvidia-glx.init.in > debian/nvidia-glx.init
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx-ia32.override.in > debian/nvidia-glx-ia32.override
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx-ia32.links.in > debian/nvidia-glx-ia32.links
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-kernel-source.docs.in > debian/nvidia-kernel-source.docs
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9631}g;' \
        -e 's{#VERSION#}{1.0.9631}g;' \
        -e 's{#NEXTVER#}{1.0.9632}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9631-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
        < debian/nvidia-glx-dev.preinst.in > debian/nvidia-glx-dev.preinst
dh_testdir
./NVIDIA-Linux-x86-1.0-9631-pkg0.run --extract-only
Creating directory NVIDIA-Linux-x86-1.0-9631-pkg0
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 1.0-9631..............................................................................................................................
if test -d /usr/share/envy/nvidia-graphics-drivers/patches; \
        then \
                pwd; \
                ls -al; \
                cd NVIDIA-Linux-x86-1.0-9631-pkg0/usr/src/nv; \
                for i in /usr/share/envy/nvidia-graphics-drivers/patches/*; \
                        do patch -p3 <$i; \
                done; \
        fi
sed 's/^nvidia-graphics-drivers/nvidia-kernel/g'  debian/changelog > debian.binary/changelog
touch configure-stamp
touch build-stamp
debian/rules binary
touch build-stamp
dh_testroot
dh_testdir
# build kernel module source tarball
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv
cp -r /usr/share/envy/nvidia-graphics-drivers/debian.binary/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
for f in `ls /usr/share/envy/nvidia-graphics-drivers/debian.binary` ; do \
                perl -p \
                -e 's{#BASE_VERSION#}{1.0}g;' \
                -e 's{#RELEASE#}{9631}g;' \
                -e 's{#VERSION#}{1.0.9631}g;' \
                -e 's{#UPSTREAMVERSION#}{1.0-9631}g;' \
                -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg0.run}g' \
                < /usr/share/envy/nvidia-graphics-drivers/debian.binary/$f >            /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
                chmod 0644 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
            done
/bin/sh: cannot create /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches: Is a directory
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches          
cp /usr/share/envy/nvidia-graphics-drivers/NVIDIA-Linux-x86-1.0-9631-pkg0/usr/src/nv/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv || true
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/rules
chown -R root:src /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules
tar -zcvf /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz -C /usr/share/envy/nvidia-graphics-drivers/debian/temp modules
modules/
modules/nvidia-kernel/
modules/nvidia-kernel/debian/
modules/nvidia-kernel/debian/README.Debian
modules/nvidia-kernel/debian/changelog
modules/nvidia-kernel/debian/control.template
modules/nvidia-kernel/debian/copyright
modules/nvidia-kernel/debian/devfs.devices
modules/nvidia-kernel/debian/dirs.template
modules/nvidia-kernel/debian/override.template
modules/nvidia-kernel/debian/patches/
modules/nvidia-kernel/debian/patches/01_sysfs
modules/nvidia-kernel/debian/patches/00list
modules/nvidia-kernel/debian/patches/03_pci_get_class
modules/nvidia-kernel/debian/patches/02_pcialias
modules/nvidia-kernel/debian/patches/04_minion
modules/nvidia-kernel/debian/postinst
modules/nvidia-kernel/debian/postrm
modules/nvidia-kernel/debian/rules
modules/nvidia-kernel/nv/
modules/nvidia-kernel/nv/Makefile.kbuild
modules/nvidia-kernel/nv/Makefile.nvidia
modules/nvidia-kernel/nv/README
modules/nvidia-kernel/nv/conftest.sh
modules/nvidia-kernel/nv/cpuopsys.h
modules/nvidia-kernel/nv/gcc-version-check.c
modules/nvidia-kernel/nv/makefile
modules/nvidia-kernel/nv/nv-i2c.c
modules/nvidia-kernel/nv/nv-kernel.o
modules/nvidia-kernel/nv/nv-linux.h
modules/nvidia-kernel/nv/nv-memdbg.h
modules/nvidia-kernel/nv/nv-misc.h
modules/nvidia-kernel/nv/nv-vm.c
modules/nvidia-kernel/nv/nv-vm.h
modules/nvidia-kernel/nv/nv.c
modules/nvidia-kernel/nv/nv.h
modules/nvidia-kernel/nv/nvreadme.h
modules/nvidia-kernel/nv/nvtypes.h
modules/nvidia-kernel/nv/os-agp.c
modules/nvidia-kernel/nv/os-agp.h
modules/nvidia-kernel/nv/os-interface.c
modules/nvidia-kernel/nv/os-interface.h
modules/nvidia-kernel/nv/os-registry.c
modules/nvidia-kernel/nv/pat.h
modules/nvidia-kernel/nv/rmretval.h
rm -rf debian/temp
touch build-kernel-stamp
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
install -m 644 /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-kernel-source/usr/src
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/X11R6/lib/modules/drivers/nvidia_drv.so \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/drivers
install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/X11R6/lib/libXvMCNVIDIA.a /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libXvMCNVIDIA.a;
install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/X11R6/lib/libXvMCNVIDIA.so.1.0.9631 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libXvMCNVIDIA.so.1.0.9631;
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/include/GL/gl.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/include/GL/glext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/include/GL/glx.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/include/GL/glxext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/libGL.so.1.0.9631 \
/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/libGLcore.so.1.0.9631 \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libGL.la
# install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libGL.la
# TLS (nvidia-tls new for 6106)
install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/libnvidia-tls.so.1.0.9631 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/
install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/tls/libnvidia-tls.so.1.0.9631 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
#sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/tls/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib\/tls/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/nvidia/libGL.la
# install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/tls/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/libGL.la
install -m 0644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib/libnvidia-cfg.so.1.0.9631 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/
install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/X11R6/lib/modules/extensions/libglx.so.1.0.9631 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/extensions/
install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/bin/tls_test /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/bin/tls_test_dso.so /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install -d /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides
install -m 0644 debian/nvidia-glx.override \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides/nvidia-glx
if [ "i386" == "amd64" ] ; then \
                install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib32/libGLcore.so.1.0.9631 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib32/libGL.so.1.0.9631 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib32/libnvidia-tls.so.1.0.9631 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9631-pkg0/usr/lib32/tls/libnvidia-tls.so.1.0.9631 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9631-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs
dh_installdocs -s
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_1.0.9631_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_1.0.9631_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_1.0.9631_i386.deb'.
tar: -: file name read contains nul character
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 150431 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_1.0.9631_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.
dpkg: error processing nvidia-kernel-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-kernel-source
rm: cannot remove `/usr/src/nvidia-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.17-11-386
Kernel headers available in /lib/modules/2.6.17-11-386/build
apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nvidia-kernel-source: Depends: dpatch (>= 2.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Done!

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Updating cached package data&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                                                           &#9474; acx100-source                                                           &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                               100%                                &#9474;  &#9474;  
                                                           &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
                                                           &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Updated infos about 83 packages
Extracting the package tarball, /usr/src/nvidia-kernel-source.tar.gz, please wait...

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Building nvidia-kernel-source, step 1, please wait...&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                                                           &#9474; Build starting...                                                       &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                                 0%                                &#9474;  &#9474;  
                                                           &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
                                                           &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Building nvidia-kernel-source, step 2, please wait...&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;                                                                         &#9474;  
                                                           &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                               100%                                &#9474;  &#9474;  
                                                           &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
                                                           &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Done with /usr/src/nvidia-kernel-2.6.17-11-386_1.0.9631+2.6.17.1-11.35_i386.deb .
Selecting previously deselected package nvidia-kernel-2.6.17-11-386.
(Reading database ... 150439 files and directories currently installed.)
Unpacking nvidia-kernel-2.6.17-11-386 (from .../nvidia-kernel-2.6.17-11-386_1.0.9631+2.6.17.1-11.35_i386.deb) ...
Setting up nvidia-kernel-2.6.17-11-386 (1.0.9631+2.6.17.1-11.35) ...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dpatch
Suggested packages:
  curl
Recommended packages:
  patchutils
The following NEW packages will be installed:
  dpatch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 84.1kB of archives.
After unpacking 319kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com edgy/main dpatch 2.0.20 [84.1kB]
Fetched 84.1kB in 0s (92.6kB/s)
Selecting previously deselected package dpatch.
(Reading database ... 150446 files and directories currently installed.)
Unpacking dpatch (from .../archives/dpatch_2.0.20_all.deb) ...
Setting up dpatch (2.0.20) ...
Setting up nvidia-kernel-source (1.0.9631) ...
Selecting previously deselected package nvidia-glx.
(Reading database ... 150489 files and directories currently installed.)
Unpacking nvidia-glx (from nvidia-glx_1.0.9631_i386.deb) ...
Setting up nvidia-glx (1.0.9631) ...
Creating NVIDIA TLS links... done.

Selecting previously deselected package nvidia-glx-dev.
(Reading database ... 150535 files and directories currently installed.)
Unpacking nvidia-glx-dev (from nvidia-glx-dev_1.0.9631_i386.deb) ...
Setting up nvidia-glx-dev (1.0.9631) ...

rm: cannot remove `*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.deb': No such file or directory
rm: cannot remove `/usr/share/envy/*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.changes': No such file or directory
ENVY: Operation Completed

```

---

### Post by Gelinder on 2007-04-06
Hi, I'm having problems getting Ubuntu to display the correct resolution, I have tried Envy but everything hangs when I reboot after installing. See my problems in this thread:

[http://ubuntuforums.org/showthread.php?t=402006](http://ubuntuforums.org/showthread.php?t=402006)

---

### Post by jmooney on 2007-04-07
First off, I have an old GeForce 2Ti card - definitely legacy driver.  Driver stopped working, which I suppose was due to the Kernel upgrade. 

Couldn't fix it with Envy so, checked the website and found a later version.  

It didn't work either.  However, the "Method 1" manual instructions on the Envy website did.

So...a couple of things.  If Envy doesn't work, try his manual install instructions.

and...could this be a bug in the latest Envy script?

Oh, one last thing...I almost didn't try his instructions because of this statement within them:

=========
"OR (If you need Legacy drivers, i.e. your graphic card is in the list at the end of the page or you need driver 7184) 

  sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings

  This does not work... "
==========

The final note in the instructions "This does not work...." almost made me abandon the attempt....in actuality...it did work.


So, great work tselliot, not only for an excellent install script, but for following up with detailed instructions.

:)

---

### Post by jay1227 on 2007-04-18
ignore, was a dual monitor issue.

---

### Post by kulus1969 on 2007-04-20
I copied line 2 of Method 2 into Terminal.   I am not sure why it aborted at the end.  Can anyone help me with this?

Kevin

sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
gcc is already the newest version.
pkg-config is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
  xserver-xorg-dev
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 8230kB of archives.
After unpacking 32.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

---

### Post by bg1256 on 2007-04-20
I realize this guide is for Edgy, but I used it on Edgy, and it worked great.

However, I did a fresh install of Feisty last night, and I can't get the Nvidia driver install using any method...

Has anyone had luck with Nvidia, the new kernel, and feisty?

---

### Post by nami on 2007-04-20
> **bg1256 said:**
> I realize this guide is for Edgy, but I used it on Edgy, and it worked great.

However, I did a fresh install of Feisty last night, and I can't get the Nvidia driver install using any method...

Has anyone had luck with Nvidia, the new kernel, and feisty?

I've still got 6.10 installed as I haven't had a chance to try out 7.04 except via VMWare.  Can you not use the new builtin functionality to install the NVIDia drivers?

Check out this page from [wiki.ubuntu.com]("https://wiki.ubuntu.com/7.04Tour#head-83d7cdd5e03c9dbfa171dde3f05d96348c81925a").

Please let us know how you get on. :KS

---

### Post by bg1256 on 2007-04-20
I just insatlled kubuntu 7.04 last night, and I installed the nvidia drivers from the command line.

```
sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable
```

Worked like a charm.

for those who prefer Gnome, it seems some are able to install them with just a few clicks, and others are required to install through the command line.

---

### Post by hessiess on 2007-05-10
instaled it now the gui wont load. how do i go back to the old one?

---

### Post by blaznlion on 2007-05-27
Hi there, I've been having problems trying to get my Dell Inspiron 8200 video card to work with the Nvidia drivers on Ubuntu 7.04.  I have an NVIDIA GeForce4 440 MX card.  I followed the instructions for Method 2 and had no success.  I used the 9631 version linux drivers to do this.  I also followed the notes section information as well.  When X starts I get an completely blank screen and then the login screen sound plays.  Has anyone had success yet on getting this video card to work?

---

### Post by sparehead02 on 2007-06-30
Hi, I am fairly new to linux and I am having some trouble with your guide. I am using method 1 (the online version) and everything goes great until I reboot the x server. Instead of getting the login screen, I get a blinking cursor in the top left corner of the screen without a command prompt. If I hit ctrl+alt+f1 I can get to a command prompt. If I type startx, I get an error message that says that it cannot find the nvidia kernel. I have done every step in your guide, using the 9775 driver from nvidia-glx-new. I have also tried the apt-get install linux-headers-generic command from the problems section, and it still does not work. Here is some info on my system:

NVidia GeForce 7600GT
2.6.20-15-generic kernel
KUbuntu Feisty Fawn

Also, I have been copying in my backup xorg.conf file from the command prompt and that seems to make everything work again, but I am now using the nv driver and my resolution is very low. I have been working on this for days, and any help would be appreciated.

---

### Post by DeleiMaciel on 2007-07-02
Hi all...
I'm with some troubles with my nvidia card. And looking for some solution on the brazilian Ubuntu Feisty forum, I met some other guys (from Brazil and Uruguay, and maybe some other places) who have the same problem with the same graphic card. 
My nvidia card is a "Nvidia GeForce FX 5200 - 128 MB - AGP 8X"   and I'm using the Ubuntu 7.04 with the newest update.

My problem is: when I start, the Ubuntu load perfectly, but when I'm wainting for the gdm screen, I hear the drums but the screen just don't appear! When I tried something like "Crtl + Alt + F1" and back to X with "ctrl + alt + F7" the gdm screen is there!! If I don't do this, but change the resolution with "crtl + alt + Nun + or -" the gdm appears too. If I login and try something who use the 3D acceleration, the pc just freeze!!! And I go to the "reset" button... :(

My first solution:
I found this guide!! Then I uninsttaled all nvidia drivers and install it again with 'aptitude'... So... my driver is nvidia-glx-new (that 1.0.9755) ... and I read a lot of Readme files and other documention in a lot of places... and find something saying to "disable the DRI module" 'cause this module "don't work in some graphic cards". Then I did it. With dpkg-reconfigure xserver-xorg, I disabled the DRI module. When I restart my computer, the gdm´s screen appears in the same time as i listen the drums the drums, and the 3D acceleration was working fine!! XD

And now:
But... a week ago I updated the sistem (and I'm sorry for that...) and I went back to the original problem... The 'nvidia-glx-new' package has been updated too, I guess...
I try uninstall and reinstall the drivers... but it just don't work anymore.

Friends, I'm a Biologist... I know more about frogs than about computers! :D
I'm just a single user!! I even know what is that DRI thing or if my AGP 8X works properly on my machine... :/

I've spent some nights on this... And a any help will be really really welcome... and it will help a lot of people...
If any other information would be necessary, please ask me.

Thanks for the chance!
And forgive me for my english...

---

### Post by phonky on 2007-07-08
Hi

I successfully installed all the nvidia drivers - for a while everything worked great - although I had to forget about beryl because of my 32MB graphics card not beeing enough (thanx for the hint) : -(

Today I had the pleasure to install the lowlatency kernel from the ubuntustudio project.

Of course, as stated in 
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

my X wouldn't load again.

After I did a 
sudo apt-get install linux-lowlatency

though, I had a wonderful experience - it worked!
But only until the next reboot....

First I got an error message that it could not load the nvidia driver because the file 
/lib/modules/...-lowlatency/volatile/nvidia.ko coulnd't be found.

After a 'sudo depmod'
and a 'sudo nvidia-glx-config enable" the error disappeared,
but X still doesn't start anymore, and the error message is not descriptive:

FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***

Any ideas?
I'm very disappointed, as it really seemed it worked again, and then....

Thank you very much.

By the way, how can I clean up the huge kernel list at boot (I don't mean just editing the grub menu file,
I mean really cleaning up the system?)

---

### Post by phonky on 2007-07-08
Hi,

 just solved my own problem:

I had installed my driver via the envy tool.

after kernel update I needed to run envy -t in text mode, that fixed it!

bye

---

### Post by arvlad on 2007-07-16
Hey! 
I'm having some problems with Method 1 of this HOWTO. Basically, my card is a GForce4 MX440, so I used the legacy driver and went straight to Problems Section 7. But even after trying all the options available there, my console still fails to recognize this command:

               sudo nvidia-xconfig --no-composite

It simply says "Invalid command line". I checked in the help section of nvidia-xconfig and, indeed, the command wasn't in the list. So.. my question is: why isn't that command available and how can I make it available?
Cheers!

---

### Post by yct on 2007-08-11
Hi tseliot, this is a comment to your:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2)

I've run into a situation where following file prevented me from loading the nvidia.ko at all:
/lib/linux-restricted-modules/.nvidia_new_installed

This file is used by /sbin/lrm-video and it looks like it should have been removed by purging the package nvidia-glx-new (or maybe not - I don't see it in the package file listing).

Based on the /sbin/lrm-video, there's another similar file (probably for the nvidia-glx-legacy package):
/lib/linux-restricted-modules/.nvidia_legacy_installed

So people may need to remove these by hand - it certainly worked for me.
I'm not sure if my problem had anything to do with purging of restricted-manager.

____________________________
Linux ready for desktop? My Fiesty install - rt61: 5 hours, nvidia: 6 hours:) (but works like a charm once installed and you learn a lot)

---

### Post by tseliot on 2007-08-11
> **yct said:**
> Hi tseliot, this is a comment to your:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2)

I've run into a situation where following file prevented me from loading the nvidia.ko at all:
/lib/linux-restricted-modules/.nvidia_new_installed

This file is used by /sbin/lrm-video and it looks like it should have been removed by purging the package nvidia-glx-new (or maybe not - I don't see it in the package file listing).

Based on the /sbin/lrm-video, there's another similar file (probably for the nvidia-glx-legacy package):
/lib/linux-restricted-modules/.nvidia_legacy_installed

So people may need to remove these by hand - it certainly worked for me.
I'm not sure if my problem had anything to do with purging of restricted-manager.

____________________________
Linux ready for desktop? My Fiesty install - rt61: 5 hours, nvidia: 6 hours:) (but works like a charm once installed and you learn a lot)
I know, but I can't edit the guide right now since I protected it from writing and I'm now unable to unprotect it :/

---

### Post by valkarin on 2007-10-05
Just wanted to drop you a note on envy.  I just used it to install the nvidia legacy driver and it worked like a charm.  Thanks for the great program!

---

### Post by bouncingmolar on 2007-10-05
should there be two "method one"s in [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#Notes](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#Notes) or is that a typo

---

### Post by zwygart on 2008-04-09
Hi tseliot,

I have a problem with the glxinfo. I use Edgy Eft and had a GeForce FX 5600 Nvidia card.

When I run glxinfo it makes a error

```
zwygart@zwygart-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
zwygart@zwygart-desktop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2e 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2f 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x30 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x31 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x32 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x33 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x34 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x35 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x36 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x37 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x38 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x40 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x41 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x42 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x43 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x44 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x45 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x46 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x47 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x48 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x49 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x50 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x51 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x52 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x53 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x54 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x55 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x56 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x57 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x58 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0xd9 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Erreur de segmentation (core dumped)

```

After that it crash and mades the file wich I attached. Couldn't because to big.
The 3D games crashed to (not started) but I think the file of glxinfo is enough.

I made what you have written at [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) except the first step because I have already installed the driver of step 2. I tried some things found at forums like made a link, but it still doesn't work. I lost the package Ubuntu-desktop on my offline computer. Can the problem be related to this?

Thanks for help.

---

