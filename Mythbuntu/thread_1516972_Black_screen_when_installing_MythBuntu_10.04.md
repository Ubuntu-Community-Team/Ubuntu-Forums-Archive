---
title: "Black screen when installing MythBuntu 10.04"
date: 2010-06-24
forum: Mythbuntu
---

### Post by punkhunter on 2010-06-24
Hey All,

I am new to MythTV and kind of a noob with Linux/Unix. I know my way around with some basic commands...

Anyway, I am trying to revive an old gaming machine (about 5 years old) to make a HTPC. When I try to install MythBuntu 10.04 I see the splash screen and then the screen goes black and does nothing else. I've done a little research and found I can hit F-6 to get to a menu where I have selections like "Try MythBuntu without installing", "Install MythBuntu", "Check memory", " Check CD for errors", etc. I tried hitting F-6 again to bring up the submenu where you can select "nomodeset" (I believe that's what it's called...going off of memory), among some other selections. Escaping this submenu I see a command line. Doing some research, people are saying to remove the "quiet splash --" and replace with i915.modeset=0 or i915.modeset=1 or radeon.modeset=1, etc. I have been trying this because I believe my issue is a video driver, but nothing has worked.

Next I tried to download the 10-6 ATI Linux driver and the latest xOrg ATI Linux driver, but those either didn't work or I am not doing something right. I was selecting the "update driver" option after hitting F-6 at bootup. Then when I select "Install MythBuntu" it asks me to install a driver CD, but doing that for either driver didn't seem to help. Still lands at a blank screen.

After I land at the blank screen, I can hit control-alt-F-1 and I am taken to a command prompt. I have mounted the hard drive (sudo mount /dev/sda1 /mnt) but it still has the Windows XP install there, so I pretty certain that the install did not work and I am just in a Linux shell or something like that.

I am about to download the previous release of MythBuntu, but I don't want to do that.....I would like the latest and greatest.

My PC specs are:
P4 3.0C
2 GB RAM
ATI 128MB video card (I still have to determine what one exactly...thinking x300)
Abit AI7 Motherboard
ATI Video Capture card (will replace once I can prove this thing works and will replace our pretty lame Comcast DVR :)

Any help would be appretiated! I've been spinning my wheels for about 3-4 nights now. Sorry for the long post, just trying to give as much info as possible. If I missed anything....feel free to ask!!!

Thanks,
Chris

---

### Post by punkhunter on 2010-06-24
I talked to a Unix guy at my work and he said that ATI video cards have given him nothing but trouble with Linux. I hate to kick down for an Nvidia card when I have a perfectly good ATI card already, so I was hoping for a better solution...

---

### Post by punkhunter on 2010-06-30
So I bought a new nvidia card (Geforce 7300 GT) and a new Hauppauge 1600 dual tuner card. Still having the same issues with video....yeah.
 
So now I am going back to MythBuntu 9.10 in hopes I can get SOMETHING working. Bad time to start trying MythTV I guess?
 
Does anyone know the fix to this? I would still like to move to 10.04....it's the latest and as someone else put it....it's an LTS build (long term support)

---

### Post by punkhunter on 2010-06-30
Installed MythBuntu 9.10, when finished it asked me to reboot and now have this issue:

[http://ubuntuforums.org/showthread.php?t=1305459&highlight=flashing+login&page=1](http://ubuntuforums.org/showthread.php?t=1305459&highlight=flashing+login&page=1)

Definitely not winning me over from Windows to Linux...just a pain in the @#$!

I guess since no one else has posted here, this is just my Ubuntu life story and gripe thread. :)

---

### Post by ian dobson on 2010-07-01
Hi,

Can you try a different monitor? I have a test box with an old (and I mean old) 15inch LCD monitor and I always get a black screen with the text "frequency too high" or something like that until I manually edited the x config file.

The splash screen is always "missing" but X starts OK.

Regards
Ian Dobson

---

### Post by punkhunter on 2010-07-02
I actually got 9.10 working last night, so I don't think it's the monitor now...but I still have some issues to work out. I'm still thinking it is the video driver/kernel mix that's causing the issue. Reading around I've heard people having to roll back to an older kernel. I have my machine updated now and I show 3 Nvidia graphics drivers (185, 173, and 96), trying any one of these drivers and rebooting the system gets an error at startup saying there is an issue loading the Nvidia module or kernel or something like that and the machine is entering low graphics mode. At least now the OS is handling it gracefully and not just getting stuck at a black screen or flickering login page.

Now I just have to figure out my next step, which I assume is rolling the kernel back to a previous version...

---

### Post by mdaitc on 2010-07-02
i too had the black screen when trying to install.

i worked round it : if i booted with the "try mythbuntu, don' install option" (cant remember the exact words) in the boot menu of the installer cd, then the display works just fine. 

Once booted into that, there's a desktop icon to install mythbuntu - that's what i used, since i had to mess around with RAID stuff.

hth....

---

### Post by punkhunter on 2010-07-13
Thank you for the idea! I will try it. I am a very determined wanna be Ubuntu user! :)

Since last updating this thread I have tried:
-Installing 10.04
-Installing 9.10
-Installing 9.04
-Googling every error I got and trying every suggestion
-Installing MythDora 12
-Installing 10.04 on my laptop that I use to surf the internet while trying to build my MythTV box

All of these did not work. I thought the last two would get me SOMEWHERE....but nope. I thought installing the Fedora version would maybe work.....but definitely installing 10.04 on another machine would have gotten me somewhere (completely different hardware!).

Anyway, I'll try booting into the liveCD and trying to install that way. (Thanks again!)

---

### Post by Mad_Professor on 2010-07-14
Yeah don't beat up linux, linux is just a kernel, BLAME ATI/AMD for being closed source.

Any nvidia card should just work, hell my 6600 and 7800GS worked fine with mythbuntu.
Try 10.04 install media again, when you see the "MYTHBUNTU" Logo, hit enter, select your language  then select F6 but don't select anything, hit escape to get rid of the menu. You'll see a "BOOT OPTIONS," with alot of stuff. At the end you'll see ```
quiet splash --
``` remove that then add ```
vga=791
``` hit enter, at some point, it will go blank, don't panic just keep an eye on your dvd-rom light. If it stops for a long period and no progress is made then assume it has hung up or made it to the live environment. From this you can safely assume it's not your hardware, but your monitor being stupid.

If it fails and leaves an error you can see what causing the problem.



ON THE OTHER HAND!


If you already got a copy of mythbuntu installed
try this in terminal

```
dpkg-reconfigure xserver-xorg
```restart, login, install nvidia driver, restart, it should just work.

if it doesn't, I would suspect the monitor having issues in displaying.
Maybe it's outputting but your monitor refuses to display due to wrong configurations, try turning it off and back on see if it displays. 

I def. don't recommend 9.04 or 9.10, they were terrible releases, 10.04 has the least amount of bugs/glitches and is the most stable, for me that is.

Also HVR1600 is a good card, but closed captions don't work due to  driver development.
Picture is really good, I didn't try the digital side. 

Linux in genral is hard to be friends with but once you have acouple of fights you'll be good friends with it.

---

### Post by punkhunter on 2010-07-14
I blew away the 9.10 install I had working in low-graphics mode trying to install other builds. I will try installing from within the liveCD (from a couple posts ago) and your first suggestion. (I have tried this one, but no one has suggested vga=791 before....only seen "nomodeset", "xforcevesa", "nv" or "nvidia" as options....all didn't work.

I have tried "nvidia-xconfig", but that failed to give any results. If I get another build going in low-graphics again I'll try your second option.

This has been a two-week fight....but I'm determined to win it! :)

Thanks everyone for your input!

---

### Post by punkhunter on 2010-07-15
I finally found the way to install Mythbuntu 10.04 consistently:
- Use the 9.10 install disk, and select 'try mythbuntu without installing'
- Use the 'install mythbuntu' desktop icon to install permanently
- Go to the update manager and click the button at the top to install 10.04 ("A new version of Ubuntu is available - 10.04 LTS")
- Then update mythtv to .23 if wanted/needed

This is cool.....I can at least get an install of 10.04 anytime I want.

I'm still running in low-graphics mode however. I tried the command:
dpkg-reconfigure xserver-xorg then rebooted, installed the nvidia graphics driver through the driver manager, then rebooted.....but still errors and makes me go into low-graphics mode. Any other ideas? Should I try to update a config file to use vga=791 somewhere/somehow?

The error at bootup is "Failed to load the nvidia kernel module" and "Screens detected, but no configurations exist". Not sure on the exact wording, but these are pretty close.

---

### Post by punkhunter on 2010-07-21
Looks like this is going to turn into a missed opportunity for Ubuntu/MythTV to convert a Windows user...

I still cannot get this thing to run correctly with the Nvidia drivers. Even in low-res I can start to configure mythtv and I have to say there is a lot of little weird settings that look like they will takes hours of trial and error to get working correctly.

I'm now looking at GB-PVR and XBMC running on Windows as my options. :(

Thanks for all the help and hopefully my issues are just a one-off scenario. (I would assume from hearing about all the people using MythTV and liking it!)

---

### Post by Mad_Professor on 2010-07-22
Don't give up man!
This is just the start of the battle!
it should just work.

Have you checked hardware drivers to see if the nvidia driver is activated?

Do you get any errors when you install the nvidia driver?

What happens when you run this command from a terminal

```
sudo nvidia-settings
```if it pops up, you should be able to configure your monitor?

if not, then the nvidia driver or nvidia-settings is not installed, and we need to find out why it's not installing.

[SIZE=4]

[/SIZE] [B][SIZE=4]Only do this section if the nvidia driver is not working or not installed.[/SIZE]

Lets try installing an nvidia driver to see if this fixes the problem.

[/B]I found out today that 10.04 runs an opensource nvidia driver called **Nouveau** which is installed by default from install.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

it has some information, but it doesn't have everything.

you need to remove Nouveau
```
sudo apt-get --purge remove xserver-xorg-video-nouveau 
```You're gonna need headers and a kernel source to compile against and compiler.

```

sudo apt-get install build-essential linux-headers-`uname -r`

```now you're set.

Now we need to get rid of some bloat.

sudo nano /etc/modprobe.d/blacklist.conf

```

blacklist vga16fb
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```Save.

```

sudo apt-get --purge remove nvidia-*

```We need the nvidia driver, go to nvidia.com and download the latest driver and be sure you get the correct architecture.

download it, save to where you can get access to it. a good place to put it is under the root directory called nvidia

in terminal
```

cd /
```then
```
sudo  mkdir nvidia
```then do
```
dir
```you should have a directory called nvidia.
Now then do this
```
sudo chmod 777 nvidia
```That way anyone on your system including root can get access to it.

Move your nvidia driver.run package to this directory via copy paste command or using the mv command in terminal. mv /source/target /dest/target 

Restart the machine, X server will freak out and say no viable driver found and drop you to shell.

LOG IN! 

Now in terminal navigate to the directory of the new shiny nvidia driver.

```
cd /nvidia
```then do
```
dir
```then this is where some human input is needed.
you need to type exactly the name of the driver, linux is cap sensitive, be sure to upper case where need it.
```

sudo sh NVIDIA-Linux-*arch-version*-pkg2.run

```example 
```
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
```once it successfully installs 

```
sudo startx
```You should not be in low-res mode anymore.

Streamers and party hats!


Any errors let me know so I can help you troubleshoot them.

try sudo nvidia-settings or nvidia-xconfig

[SIZE=4]
**ONLY DO THIS IF THE NVIDIA DRIVER IS INSTALLED AND WORKING**[/SIZE] 

[COLOR=Red]**if you can't configure the monitor in nvidia-settings then we need to do a manual configuration.**[/COLOR]

We'll need to configure /etc/X11/xorg.conf

This is what mine looks like

```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "UseEvents"     "1"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
EndSection

```It should look the same on yours, if not and you get something completely different, post it so I can see what you have.

but if you get what I get, then we need to configure the screen section and add display modes manually.

We need to edit this section of xorg.conf
you can sudo either gedit or nano

```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

```Copy and replace if you can

```

Section "Screen"
     Identifier      "Default Screen"
         Monitor         "Configured Monitor
         Device          "Configured Video Device"
         DefaultDepth    16
     SubSection "Display"
        Depth    8
        Modes        "1280x1024"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    15
        Modes        "1280x1024"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    16
        Modes        "1280x1024"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    24
        Modes        "1280x1024"    "1024x768"    "800x600"    "640x480"
    EndSubSection
EndSection

```save it

then do CTRL+ALT+BACKSPACE

which should kill the X window system, drop you to shell and then restart X and bring you back to the log in screen, at either a better resolution or the same resolution.
Or if you're stuck at shell, login and type startx.

Once you login go to settings under Applications and then go to Display and you should be able to select screen resolutions.

---

### Post by punkhunter on 2010-07-23
Dang...for two reasons:
-Nice detail in your explanation
-I already ordered a copy of Windows7 Home Premium to run my HTPC

I'm waiting for the Windows disk in the mail, so in the mean time I'll try this fix. If it works I'll use my Windows OS to upgrade my wife's laptop off of Vista. :)

It's gunna be a few days before I'll get time to do this, I'll report results ASAP. Thanks again for your time and effort!

---

### Post by punkhunter on 2010-07-24
just a black screen when I reboot! See next post...

---

### Post by punkhunter on 2010-07-24
Stuck again! Once I get to the part where I restart (I'm supposed to login and run the command sh nvidia.run to install the video driver next).....but it just boots to a black screen. Hitting esc or ctrl-alt-F1 does not get me to a console either.

---

### Post by punkhunter on 2010-07-28
I got my Windows7 disk in the mail. Installed Windows7 and bingo.....video card/display issues also. It did boot up and go into the OS with little fuss, just low res. I went into device manager to look at the video card and it said there wasn't enough resources available. I searched the error message and a bunch of forums told me to go into the BIOS and make some changes. (By the way I flashed the BIOS to the latest version and it did not fix it)

- Disabled all devices not in use (COM1 and COM2 ports if you don't have a printer connected to them, etc.)
- Change the video RAM AGP size from 128 MB to 256 MB (I have a 512 MB card, so I don't know what the deal is here)

Reboot and it fixed my video issues! I would think if this change fixed my video issues in Windows7 it would be the same for Ubuntu. I wish I had the time and hard drive space to verify...

---

