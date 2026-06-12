---
title: "can't play HD with geforce 8400 GS"
date: 2011-10-21
forum: Multimedia Software
---

### Post by crchtiger on 2011-10-21
Hi, is there a minimum hardware requirement to play high digital video ?

I am running ubuntu 10.04 
with AMD athlon 64x2 4000+ , 2 GB of ram DDR 2 and nvidia gforce 8400 GS and I can't play any HD video... it freezes...

Am I missing any driver, plugin necessary or my hardware is just obsolete?

I just installed the video card and the system did it all by itself, and it installed the latest nvidia drivers...

thanks for any help!

---

### Post by BicyclerBoy on 2011-10-21
With the right setting the 8400GS can playback HD using VDPAU.
8400GS can do full h/w based HD decode but is a little weak on post processing.

Using VDPAU will reduce the CPU load to near idle.

To use VDPAU directly you need to be using mplayer MythTV or XBMC.

It is possible to use VDPAU via VAAPI which is supported by later VLC & mplayer.

There are libraries to install to make all/any of this work..search synaptic for vdpau.

The VLC VAAPI route is more complicated...

The recommended HTPC video cards are GT430 (best), GT220, GT240

---

### Post by Flymo on 2011-10-24
Confirmed - we run 720P successfully on Acer Aspire Revo with Atom 330 and nVidia 9400M, ditto on AMD K325 (=Atom++) with nVidia 9200M.  Same setup as referenced above.

Why 720P? that's what the screens support.

---

### Post by crchtiger on 2011-10-26
I tried playing with mplayer and it didn't work out for one video... I think its consuming all cpu power and crashes...

---

### Post by BicyclerBoy on 2011-10-26
What's the cmd line options you used ?

Something like..
mplayer -vo vdpau -vc ffh264vdpau
for mpeg4/10 H264AVC

---

### Post by crchtiger on 2011-10-27
I didn't use any... I just opened with mplayer... sorry I'm such a noob :(

Now I've found stellarium isn't opening, I can open it with safe-mode though..

---

### Post by BicyclerBoy on 2011-10-27
Maybe you should be using smplayer or any GUI wrapper for mplayer.

mplayer is kind of a uber-geek program..

---

### Post by crchtiger on 2011-10-27
I installed smplayer but still no success... I tried selecting the vdpau video codec in video preferences and I get no video... what am I doing wrong :(

---

### Post by BicyclerBoy on 2011-10-28
Try running from cmd line (terminal)
Check any log files.
Try the mplayer cmd line posted previous.

Check you have the libvdpau installed
Can get later version of this lib & video driver smplayer from here:
[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid)

---

### Post by crchtiger on 2011-10-30
Ok, I got this from cmd

Playing /home/laura/Desktop/2011-06-24 U2 Glastonbury HD mkv 1080/2011-06-24 U2 Glastonbury.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Error: API mismatch: the NVIDIA kernel module has version 195.36.24,
but this NVIDIA driver component has version 280.13.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)

---

### Post by BicyclerBoy on 2011-10-30
How did you try to install the video driver ? because it has not installed correctly..

Kernel module does not match the driver...

---

### Post by crchtiger on 2011-11-01
basically I added the new card (I had an ati 1200 onboard) and when I booted into ubuntu it asked to install the driver , first I installed the old version and then I checked and there was a new one (it said "current" I think) I installed that...

---

### Post by crchtiger on 2011-11-01
umm I just checked "Hardware drivers" and it doesn't show the driver version, it says its the "current"... now how do I make the kernel module and the driver to match?...

---

### Post by BicyclerBoy on 2011-11-01
If they don't match it means the installer scripts did not work..
A part of the kernel module must be compiled against your kernel headers & then the module has to be inserted (dkms), boot image regenerated (update-initramfs).

I would try to re-install nvidia-current from synaptic package manager.

Failing that...need to purge all nvidia packages & then re-install nvidia-current.

I would avoid the jockey driver tool (additional drivers)..It worked okay for me on 11.10 but historically is was not reliable.

The problem could be a broken install script in the ubuntu package.
There are other sources of packaged drivers..
xorg-edgers ppa
x-swat team ppa
mythbuntu ppa most likely..

---

### Post by crchtiger on 2011-11-01
alright... so removing them won't mess everything up? (shouldn't do it...?)

---

### Post by BicyclerBoy on 2011-11-02
If you purge the nVidia packages & then reboot (new kernel image).

You end up with the std fallback ubuntu driver which could be veas or nouveau depending on blacklists..

I have had no problems with fallback driver working on nVidia 9400GT GTX260. It is real slow & laggy but you can still use the GUI..
Login to a failsafe mode or console.

Learn what the apt-get cmd needs to be. This is possible:
sudo apt-get install nvidia-current


You can't mess up your install by purging packages..you can always recover if you understand some basic console/terminal commands & can use apt-get or synaptic.

---

### Post by Flymo on 2011-11-17
Did it all come good in the end?
....or is your system borked?  Do hope not...
Been offline a bit, or I'd have come back earlier.

---

### Post by crchtiger on 2011-11-20
> **Flymo said:**
> Did it all come good in the end?
....or is your system borked?  Do hope not...
Been offline a bit, or I'd have come back earlier.

Hi sorry, I've been busy... actually I didn't change anything but I had a regular update for ubuntu and now I don't have the error that the driver doesn't match the kernel module, however I still don't get good HD either... the video is jumpy ... 

I guess I will have to try to uninstall the driver then..

---

### Post by BicyclerBoy on 2011-11-20
Don't rush into purging the nvidia drivers..

Do you still get the ABI mis-match error ?

The update likely included a new kernel ..this will have triggered a image rebuild. This could have fixed the version mis-match..

Check your /var/log/Xorg.0.log for errors..

glxinfo | grep OpenGL
glxgears
vdpauinfo
qvdpautest  (need to download/compile)

---

### Post by crchtiger on 2011-11-20
> **BicyclerBoy said:**
> Don't rush into purging the nvidia drivers..

Do you still get the ABI mis-match error ?

The update likely included a new kernel ..this will have triggered a image rebuild. This could have fixed the version mis-match..

Check your /var/log/Xorg.0.log for errors..

glxinfo | grep OpenGL
glxgears
vdpauinfo
qvdpautest  (need to download/compile)

I don't get the mis-match error now

I tried those commands and got this:

laura@laura-desktop:~$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2/3DNOW!
OpenGL version string: 3.3.0 NVIDIA 280.13
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
laura@laura-desktop:~$ vdpauinfo
vdpauinfo: command not found
laura@laura-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
3332 frames in 5.0 seconds
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 43 requests (43 known processed) with 0 events remaining.

---

### Post by BicyclerBoy on 2011-11-21
To play HD video using GPU h/w decode (VDPAU), you need the vdpau library package.

This package is freely distributed but separate to the driver..could be in std repository but I get it (& the driver etc) from..
```

lucid:
https://launchpad.net/~nvidia-vdpau/+archive/ppa

or later:
https://launchpad.net/~ubuntu-x-swat/+archive/x-updates

```

vdpauinfo needs to run successfully..

To take advantage of VDPAU you need to use mplayer/MythTV/XBMC etc.
You can use VAAPI (VLC) by using the vdpau backend for vaapi.
vdpau-va-driver.

---

### Post by crchtiger on 2011-11-21
> **BicyclerBoy said:**
> To play HD video using GPU h/w decode (VDPAU), you need the vdpau library package.

This package is freely distributed but separate to the driver..could be in std repository but I get it (& the driver etc) from..
```

lucid:
https://launchpad.net/~nvidia-vdpau/+archive/ppa

or later:
https://launchpad.net/~ubuntu-x-swat/+archive/x-updates

```

vdpauinfo needs to run successfully..

To take advantage of VDPAU you need to use mplayer/MythTV/XBMC etc.
You can use VAAPI (VLC) by using the vdpau backend for vaapi.
vdpau-va-driver.

ufff I added the ppa:nvidia-vdpau/ppa source and updated, when I try to add libvdpau it says :
laura@laura-desktop:~$ sudo apt-get libvdpau
E: Invalid operation libvdpau

laura@laura-desktop:~$ vdpauinfo
vdpauinfo: command not found

umm how should I install those libraries!?

---

### Post by beew on 2011-11-21
It should be 
```

sudo apt-get install libvdpau
```

You forgot "install".

You could just use Synaptic to manage packages though, it has the advantage that you don't need to know the exact name of the packages.

---

### Post by crchtiger on 2011-11-22
> **beew said:**
> It should be 
```

sudo apt-get install libvdpau
```

You forgot "install".

You could just use Synaptic to manage packages though, it has the advantage that you don't need to know the exact name of the packages.

laura@laura-desktop:~$ sudo apt-get install libvdpau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libvdpau


but I had added the source!

---

### Post by beew on 2011-11-22
Can you try install it with synaptic just in case the package may have a different name, like libvdpau1 or something?

---

### Post by crchtiger on 2011-11-22
> **beew said:**
> Can you try install it with synaptic just in case the package may have a different name, like libvdpau1 or something?

ok, I tried that and I already have that package installed

---

### Post by beew on 2011-11-22
Ok, so it is already installed. Now in order to use vdpau you need either mplayer or xbmc. vlc doesn't work.

Install mplayer with this ppa  [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")
This is actually mplayer2, it performs much better than the stock mplayer provided by Ubuntu in the repo.

Just add the repository to synaptic as follows

Open synaptic,  go to Settings > Repositories > Other Software. Click "add" and paste this line into the box
> ppa:ripps818/coreavcThen close the dialogue and click Reload. After that search for mplayer and install it.

Now you can choose different guis for mplayer. The common one is gnome-mplayer. I never used lucid with vdpau but the version of gnome-mplayer in maverick was broken and for some reasons didn't work with vdpau. Since the version in Lucid is even older it probably didn't work either. So, install an up to date version of gnome-mplayer instead with this ppa

[https://launchpad.net/~ed10vi86/+archive/video]("https://launchpad.net/%7Eed10vi86/+archive/video")

You open synaptic and add the ppa line,--find it in the website,-- like before, reload and install gnome-mplayer

**After installing gnome-mplayer, start it and go to Edit > Preference and set the video output to vdpau**

  gnome-mplayer is very stripped down, a more feature rich gui for mplayer is umplayer. It is not in the repo but can be installed with this ppa
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")
(Now you know the drill)
[B]
Again start umplayer and go to preferences and change the video output to vdpau[/B]_._

P.S. you can add repositories and install programs with the command line like this

```
sudo add-apt repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install umplayer
```However I find synaptic very useful especially if you don't know exactly the name of the package to install or what you want to install, so I decide to explain the steps with synaptic using a bit more words than have to.

---

### Post by crchtiger on 2011-11-22
> **beew said:**
> Ok, so it is already installed. Now in order to use vdpau you need either mplayer or xbmc. vlc doesn't work.

Install mplayer with this ppa  [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")
This is actually mplayer2, it performs much better than the stock mplayer provided by Ubuntu in the repo.

Just add the repository to synaptic as follows

Open synaptic,  go to Settings > Repositories > Other Software. Click "add" and paste this line into the box
Then close the dialogue and click Reload. After that search for mplayer and install it.

Now you can choose different guis for mplayer. The common one is gnome-mplayer. I never used lucid with vdpau but the version of gnome-mplayer in maverick was broken and for some reasons didn't work with vdpau. Since the version in Lucid is even older it probably didn't work either. So, install an up to date version of gnome-mplayer instead with this ppa

[https://launchpad.net/~ed10vi86/+archive/video]("https://launchpad.net/%7Eed10vi86/+archive/video")

You open synaptic and add the ppa line,--find it in the website,-- like before, reload and install gnome-mplayer

**After installing gnome-mplayer, start it and go to Edit > Preference and set the video output to vdpau**

  gnome-mplayer is very stripped down, a more feature rich gui for mplayer is umplayer. It is not in the repo but can be installed with this ppa
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")
(Now you know the drill)
[B]
Again start umplayer and go to preferences and change the video output to vdpau[/B]_._

P.S. you can add repositories and install programs with the command line like this

```
sudo add-apt repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install umplayer
```However I find synaptic very useful especially if you don't know exactly the name of the package to install or what you want to install, so I decide to explain the steps with synaptic using a bit more words than have to.

excellent guys!!! I think it's working perfect now! WOOOHOOO!!

million thanks!! :D

---

