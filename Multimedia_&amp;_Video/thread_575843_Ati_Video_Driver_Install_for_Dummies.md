---
title: "Ati Video Driver Install for Dummies"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by Spydr4590 on 2007-10-14
**DO NOT USE THIS GUIDE IT IS OUTDATED and IT WILL NOT WORK WITH THE LATEST DRIVER. Instead use [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) Choose Ubuntu on the right and then your Ubuntu Build number and follow Step 2 Manual install the driver. This will install the ATI Driver Correctly. I will leave this for referance.**

I'm making this guide for the Dummies out there. I was one of them, and this almost drove me insane! This will work for any ATI video card out there on Ubuntu Feisty/Gutsy! No need to goto multiple sites for help!

Note:I don't recommend using ati-driver-installer-8.42.3-x86.x86_64.run You can't even compile this on 64-bit Ubuntu without some major editing and the thing that gets me is ATI knew about this before their public release. I'm not sure how well this works on 32-bit Ubuntu. I'm not providing any support till next driver release 8.43. Feel free to continue discussing.

First I will give credit to two main sources [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

Unfortunately neither site actually helped me install the drivers completely without any issues. I had to merge the guides through trial and error.

Note: If you're running a crossfire system remove the crossfire master card, and leave one non crossfire card in the primary pci express slot. (Shut off your system and know what you're doing before you attempt this.)

Step 1. Download your driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) to your desktop

Step 2. In the upper right corner goto Applications ----->  Accessories --------> Terminal

Step 3. Type this into the terminal or Right Click this code and copy it, then right click in the terminal and choose paste. This will ask you if you want to download some libraries, just hit y and enter to continue. Note: In Gutsy you are now asked for the install cd. ```
sudo apt-get update
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper \
debconf libstdc++5 linux-headers-generic
```

Step 4. Type LS to get contents of your current directory, You should see Desktop and Examples. Everything is case sensitive in linux so type cd Desktop. You will now be in the desktop folder. Type LS again and you will see the file that you have downloaded. At this point you want to type in the terminal ```
bash ./ati driver file name*.run --buildpkg Ubuntu/feisty or --buildpkg Ubuntu/gutsy (Depending on your version)
``` This will put several files on your desktop which we can delete later.

Step 5.Type in the teminal LS to get a list of the new files created. Now type in this to the terminal then hit enter ```
sudo dpkg -i fglrx-kernel-source_8.41.7-1*.deb
sudo dpkg -i xorg-driver-fglrx_8.41.7-1*.deb
sudo dpkg -i fglrx amdcccle_8.41.7-1*.deb

``` 

Note: You don't have to do sudo dpkg -i fglrx amdcccle_8.41.7-1*.deb (this install the ATI AMD Catalyst Control Panel which is worthless, but gives you pretty information about your video card) If you're on 64-bit Ubuntu it will complain about libraries. Just go ahead and type ```
sudo apt-get install -f Note: This is no longer necessary in Gutsy.
``` This will install the missing libraries. After that you will need to run sudo dpkg -i fglrx amdcccle_8.41.7-1*.deb to compile the on 64-bit.

Step 6. ```
sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb
``` You can find fglrx-kernel*.deb by going to places in the upper right and choosing computer. Once there goto filesytem, then the folder usr, then the folder src, right click and move to trash. Then in the lower right corner right click trash and empty file.

Step 7.Type in ```
gksu gedit /etc/default/linux-restricted-modules-common
``` in the terminal.  Add fglrx to DISABLED_MODULES="" in the middle of the parenthesis. Save and exit the file.

Step 8. At this point I choose to reboot. After the reboot type in ```
sudo aticonfig --initial --force
``` This generates a default ATI device section in the configuration file which is capable of loading the fglrx driver. Then type in```
sudo aticonfig --overlay-type=Xv
``` This will enable Enable Video acceleration (Xv Overlay). Now reboot again. If you come up with errors writing to your xorg.conf file, type in this command sudo -i then enter in your password. Now retype the previous commands for aticonfig, after that reboot and follow step 9.

Step 9. Open up the terminal to make sure you have ATI installed correctly type in  ```
fglrxinfo
``` (This should display ati)
Then type in ```
glxinfo | grep direct
``` (Makes sure you have 3d acceleration and it should display yes)

Hopefully you will have no more issues and everything worked! Whew! And yes you can delete all those ati files on your desktop now!

---

### Post by andyakadum on 2007-10-16
Hi,

Does this mean ATI Crossfire is supported under Ubuntu.
I've looked everywhere and I just can't find a proper answer.

Any news would be greatly appreciated.

---

### Post by Spydr4590 on 2007-10-17
> **andyakadum said:**
> Hi,

Does this mean ATI Crossfire is supported under Ubuntu.
I've looked everywhere and I just can't find a proper answer.

Any news would be greatly appreciated.

It's not supported.

---

### Post by karbo on 2007-10-19
Thanks for this! I am on a HP Compaq nx9420 with a ATI Radeon Mobility X1600 and this guide fixed my problems. Works like a charm!

---

### Post by weirdguille on 2007-10-19
Hi.
Just want to say it did not work for me.  I have a ATi Radeon Xpress 200, and I have serious problems.  More info (and a desperate request for help) here:
[http://ubuntuforums.org/showthread.php?t=581147](http://ubuntuforums.org/showthread.php?t=581147)

---

### Post by XxZtemxX on 2007-10-19
> **Spydr4590 said:**
> It's not supported.



i have dual ati radeon hd 2600 xt's (Crossfire on Vista), and i am looking to dual boot. (i havent done it yet.) if i leave the cards in the same configuration as i use for Vista, is it going to cause problems?

will it only utilize one card even with the bridges between cards intact?

---

### Post by KrotBot on 2007-10-19
will this work for the radeon 9200 pro on gutsy and will it make a difference to enabling dual monitor support?

---

### Post by voivoi on 2007-10-19
HI New Like  I borned baby here.

I have made  new Installation and I have the Bad thing ATI Radeon X1600.
I Have try to follow the Dummi but i am so stupid I  am lost all ready In the step 4.

[COLOR="Black"]bash ./ati driver file name*.run --buildpkg Ubuntu/feisty or --buildpkg Ubuntu/gutsy (Depending on your version)
[/COLOR]


I have downloade the drivers to desktop so I need some Help...:confused:

---

### Post by snerd on 2007-10-19
Another brand-noob here. i get this after command to buildpkg:

Created directory fglrx-install.cM7409
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 175: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.cM7409

So........... what is it that I need to do now?

Thanks,
Mike

---

### Post by Kleppemeister on 2007-10-19
Do's not seem to work on the ATI Radeon 1950PRO Agp card. But then again, nothing else seems to work on it.
Also im getting stuck with a blackscreen when im about to get to the login screen everytime I try to get this to work. No ide how many guides ive followed now. Non seem to work, at all. Same problem with all of them.
Any way i can restore to default or something so I dont need to reinstall the OS yet another time?

---

### Post by ramadhian on 2007-10-20
Radeon Xpress 1100 IGP] not available there

---

### Post by GriffiN on 2007-10-20
i did everything it says... no errors no warning... it just completed everything...
when i do fglrxinfo y get ati... and when i do fglrxinfo | grep direct it does absolutly nothing... no message no nothing... wierd huh?

did glxinfo and found out that i DO have direct rendering... also i have x1900gt for the record

---

### Post by voivoi on 2007-10-20
Att Last I fix the Problem to Radeon FX1600.

Whath do to fixed so its working ..

1 go to Synaptic Package Manager.
uninstall fglrx

2 go to ati.com get the new driver ati-driver-installer-8.40.4-x86.x86_64.run
Install this in Terminall.

3 Restart
And here should evrything work you can enable even the visual effects.
Open the terminal and write compiz and I hope some get this info.

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator

------------------------------------------
I hawe never ever worked whit linux ore Ubuntu. damn I like the produkt allready.
Now I have to lurn more.
I have only Installing and installing 3 tims I messed upp some time.
Only 1 week working whit reading reading and searh info more reading and att
last upp and running.
Dont give upp you new ubuntu frends there in space.

---

### Post by Spydr4590 on 2007-10-20
> **XxZtemxX said:**
> i have dual ati radeon hd 2600 xt's (Crossfire on Vista), and i am looking to dual boot. (i havent done it yet.) if i leave the cards in the same configuration as i use for Vista, is it going to cause problems?

will it only utilize one card even with the bridges between cards intact?

No, you will come up with an error when you install the offical ati driver after reboot. You won't be able to log back into ubuntu, unless you're well versed in rebuild commands for your xorg.conf file from the terminal. So the awnser is you can only have one card in.

---

### Post by TheDudeOfDoom on 2007-10-21
Thank you, first of all, for the wonderful guide. I ran it completely, and and very next reboot it autodetected and implemented the proper resolution for my display. 

However....when I run

fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I have an ATI X1300 pro card....forgive me if someone has already addressed this issue.

---

### Post by creon_of_thebes on 2007-10-22
> Step 1. Download your driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) to your desktop
What should I do if my driver isn't on the site? (Radeon X1200 in a Toshiba Satellite a215.)

---

### Post by jao on 2007-10-22
I also get unsupported architecture error when I get to that step. I have an AMD x2 4800 on a x86 Ubuntu Gutsy install. so Ati doesn't support its own architecture? lol. Anybody know what's wrong? It s a2600XT card.

---

### Post by geogrip.e on 2007-10-22
this installation notes working for ATI HD2400PRO?
Is this  the best drivers for using compiz or beryl in Gutsy (upgrade from Feisty)

---

### Post by Dr Kenneth Noisewater III on 2007-10-22
I just wanted to let you know that I found your post and made a user account just to personally thank you for sorting the fly crap from the pepper and helping me with ATI drivers.  Your advice worked PERFECTLY and now my Myth TV runs like a charm with my Radeon 9600

---

### Post by BCoon on 2007-10-22
> **Dr Kenneth Noisewater III said:**
> I just wanted to let you know that I found your post and made a user account just to personally thank you for sorting the fly crap from the pepper and helping me with ATI drivers.  Your advice worked PERFECTLY and now my Myth TV runs like a charm with my Radeon 9600

This is strange.. I have an All-In-Wonder 9600XT and when I ran:
```
fglrxinfo
```
I get
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```
I followed this guide accurately.  Anybody know what I can do to fix this?

---

### Post by diizy on 2007-10-22
> **BCoon said:**
> This is strange.. I have an All-In-Wonder 9600XT and when I ran:
```
fglrxinfo
```
I get
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```
I followed this guide accurately.  Anybody know what I can do to fix this?

I still seem to run into this as well, is there any solution for this?

---

### Post by The Shaolin on 2007-10-22
> **diizy said:**
> I still seem to run into this as well, is there any solution for this?

I'm running into the same problem as well.  Two monitors and a Radeon X850 XT.

theshaolin@theshaolin-desktop:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

theshaolin@theshaolin-desktop:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


The tutorial seemed to work fine, what did I miss?

---

### Post by noefear on 2007-10-23
I get the same GLX missing lines...what are we missing?

---

### Post by SKiFF on 2007-10-23
> **Kleppemeister said:**
> Do's not seem to work on the ATI Radeon 1950PRO Agp card. But then again, nothing else seems to work on it.
Also im getting stuck with a blackscreen when im about to get to the login screen everytime I try to get this to work. No ide how many guides ive followed now. Non seem to work, at all. Same problem with all of them.
Any way i can restore to default or something so I dont need to reinstall the OS yet another time?

yeah I have the same problem with my 1950, after step 8 when you reboot, the UBUNTU loading bar is showing and then black screen ... 

if anyone solved this with ati x1950 please pm me, would greatly appreciate it.

~ Skiff.

---

### Post by greenhat on 2007-10-23
> **weirdguille said:**
> Hi.
Just want to say it did not work for me.  I have a ATi Radeon Xpress 200, and I have serious problems.  More info (and a desperate request for help) here:
[http://ubuntuforums.org/showthread.php?t=581147](http://ubuntuforums.org/showthread.php?t=581147)

I was able to get my ATi Radeon Xpress 200 working following this forum guide as well as this  wiki page [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Hope that helps!

---

### Post by volty on 2007-10-23
Running a Mobile Radeon 9000 on this POS Dell, and of course, it isnt supported by the newest drivers. Attempting to use the 8.28.8 drivers (the last ones that work) and I get an error:

```
volty@volty-dell:~/Desktop$ bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Extraction failed.
Signal caught, cleaning up

```

---

### Post by Dr Kenneth Noisewater III on 2007-10-23
Ehh, I don't know if I'm really the right person to ask about doing this right.  I guess looking back the part I had the most difficult time was step 6, just making sure that file got deleted, but that's me not knowing the Ubuntu terminal commands very well and that little asterisk is deceptive about how much text is actually there...  I have a feeling that most people on here are not as confused by the little details as I am, at this point in my Ubuntu career the hardest part for me is figuring out what to do on the steps that most people consider so easy they don't go into detail or just don't mention them at all.  That's why this guide was good is that no steps were omitted or explained in any less detail.

---

### Post by jctweb on 2007-10-23
It helps to look for errors in /var/log/Xorg.0.log - if you're attempting to load the fglrx module and there's an issue, that should show you where it is.

I've been struggling with my ATI card for a bit, but I've finally got everything working how I want it.

My only peeve is I can't move a running application between monitors in dual-head mode.  When I switch to BigDesktop mode, it doesn't like it when I try to run different resolutions on the monitors.  The setup isn't perfect, but it's doing the job I want it to.

Once again, check your Xorg log to see where your errors are occuring - it will most definitely help in your troubleshooting.

---

### Post by daradib on 2007-10-23
**This worked for me, but when I restarted I got a white screen when Compiz Fusion loaded. I had to redo the commands in a virtual terminal (Control-Alt-F2) and then switch to the white screen (Control-Alt-F7) and then restart the X server (Control-Alt-Backspace). So the following does work, but it is not permanent, so it has to be repeated at every boot.**

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

I had that problem. In /var/log/Xorg.0.log there was the following:
```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
(WW) fglrx(0): Failed to open DRM connection
```

I fixed this problem by doing the following:
```
sudo rmmod fglrx
cd /lib/modules/*/misc
sudo insmod fglrx.ko
modprobe fglrx
```

Note: The fglrx module was not found for me, but that is okay. Also, replace * with the kernel version (2.6.22-14-generic for me), but you can leave the asterisk if you have only one kernel version.

Then restart the X server.

Then I got the following from fglrxinfo.
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.0.6958 Release
```

---

### Post by VCSkier on 2007-10-23
> **volty said:**
> Running a Mobile Radeon 9000 on this POS Dell, and of course, it isnt supported by the newest drivers. Attempting to use the 8.28.8 drivers (the last ones that work) and I get an error:

```
volty@volty-dell:~/Desktop$ bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Extraction failed.
Signal caught, cleaning up

```

I've got the ATi Radeon Mobility 9000 in my 4 year old IBM ThinkPad T41, and the open source "ati" driver has great 3D direct rendering.  Compiz runs great with a default setup on AIGLX.  Your's should too, as long as you can get all the proprietary fglrx stuff off.  I tried to install fglrx once; it didn't work, and then I couldn't get the oss driver working again.  I ended up reformatting :/

---

### Post by superyounan1 on 2007-10-23
deleted

---

### Post by Zakk Walid on 2007-10-23
> **snerd said:**
> Another brand-noob here. i get this after command to buildpkg:

Created directory fglrx-install.cM7409
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 175: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.cM7409

So........... what is it that I need to do now?

Thanks,
Mike

try typing the first commands again but separately ... worked for me,,,

---

### Post by Zakk Walid on 2007-10-23
```
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

[B][U][SIZE="7"][COLOR="Red"]
Help me before I commit Suicide! [/COLOR][/SIZE][/U][/B]


> **Dr Kenneth Noisewater III said:**
> I just wanted to let you know that I found your post and made a user account just to personally thank you for sorting the fly crap from the pepper and helping me with ATI drivers.  Your advice worked PERFECTLY and now my Myth TV runs like a charm with my Radeon 9600

HoooowWW 


I have 9600 and it dosent workkkk!!! 
Please help me damn this radeon is driving me crasy!@$

---

### Post by jctweb on 2007-10-23
> **Zakk Walid said:**
> ```
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```


Alrighty - here's what I had to do:
1.  Remove all fglrx-related packages - ALL of them
2.  Verify that the fglrx module is blocked in /etc/default/linux-restricted-modules-common
3.  Restart your computer

sudo rmmod fglrx - just to make sure

Follow the install [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") (I used method 2)

Here's my working xorg.conf (dual-head with external CRT):
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Laptop" 0 0
	Screen      1  "External" LeftOf "Laptop"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "On"
	Option "TexturedVideo" "True"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Laptop LCD"
	VendorName   "Dell"
	ModelName    "Dell 1680x1050 Laptop Display Panel (16/10)"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "ViewSonic CRT"
	VendorName   "ViewSonic"
	ModelName    "ViewSonic GS790"
	HorizSync    30.0 - 97.0
	VertRefresh  50.0 - 180.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Laptop Internal"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "HSync2" "30-97"
	Option	    "VRefresh2" "50-180"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Mode2" "1280x1024"
	Option	    "UseFastTLS" "2" #for wine
	BusID       "PCI:1:0:0"
	Screen      0
EndSection

Section "Device"
	Identifier  "Laptop External"
	Driver      "fglrx"
	Option      "VideoOverlay" "on"
	Option      "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Laptop"
	Device     "Laptop Internal"
	Monitor    "Laptop LCD"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "External"
	Device     "Laptop External"
	Monitor    "Viewsonic CRT"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection

```

---

### Post by Zakk Walid on 2007-10-23
woooorked!!!!!!!!!!!!!1
but no desktop effects -_- ===> no compiz fusion working ==> im starting to think where to hang myself ==> how to fix effects? :)


Ps: it worked because i did the tutorial again and i missed 1 step ^^ 
but now its ok, but no effects :(

---

### Post by VSpecII on 2007-10-23
When I type:

fglrxinfo

I get:

fglrx: error while loading shared libraries: libGL.so.1: cannot open shared object file: no such file or directory.

When I type:

glxinfo |  grep direct

I get: 

glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: no such file or directory.

Please help before I trash something!

Also, when I type compiz, it says Xgl is not found. What do I do?

---

### Post by Zakk Walid on 2007-10-23
yeyyyyyyyyyyyyy it worked! 
tnx jctweb 
ur great!

---

### Post by mrplow on 2007-10-23
I reached step 6 until recieved the following error
using gusty and 8.42 along with the fglrx-8.42-ubuntu+debian-2.tar.bz2 patch on my 9600xt


```
dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.22-14-rt.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:365: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:366: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘fglrx_pci_suspend’:
/usr/src/modules/fglrx/firegl_public.c:799: warning: passing argument 1 of ‘firegl_pci_save_state’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘fglrx_pci_resume’:
/usr/src/modules/fglrx/firegl_public.c:841: warning: passing argument 1 of ‘firegl_pci_restore_state’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_pci_find_device’:
/usr/src/modules/fglrx/firegl_public.c:2019: warning: ‘pci_find_device’ is deprecated (declared at include/linux/pci.h:477)
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:
/usr/src/modules/fglrx/firegl_public.c:2962: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:68)
/usr/src/modules/fglrx/firegl_public.c:2962: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:5439: warning: ‘kmem_cache_t’ is deprecated
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /usr/src/modules/fglrx/.libfglrx_ip.a.GCC4.cmd for /usr/src/modules/fglrx/libfglrx_ip.a.GCC4
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make: *** [build] Error 2
```

---

### Post by Dropknee on 2007-10-23
When I login the screen goes completely white, the only solution I have right now is to enter in Gnome Failsave section to correct this problem.

Any clue???

my xorg.

```

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "alt-intl"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerFlags"
        Option "AIGLX" "on"
EndSection

Section "Extensions"
    Option "Composite" "1"
EndSection
```

I add the AIGLX and the composite option manually to see is this work but isn´t

pls help

---

### Post by seamus7 on 2007-10-23
I'm having the same issue as VspecII and DropKnee ... 

When I login the screen goes completely white, the only solution I have right now is to enter in Gnome Failsave section to correct this problem.

When I type: fglrxinfo
I get: fglrx: error while loading shared libraries: libGL.so.1: cannot open shared object file: no such file or directory.

Help would be appreciated.
Thanks.

---

### Post by Dropknee on 2007-10-24
> **jctweb said:**
> Alrighty - here's what I had to do:
1.  Remove all fglrx-related packages - ALL of them
2.  Verify that the fglrx module is blocked in /etc/default/linux-restricted-modules-common
3.  Restart your computer

sudo rmmod fglrx - just to make sure

Follow the install [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") (I used method 2)

Here's my working xorg.conf (dual-head with external CRT):
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Laptop" 0 0
	Screen      1  "External" LeftOf "Laptop"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "On"
	Option "TexturedVideo" "True"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Laptop LCD"
	VendorName   "Dell"
	ModelName    "Dell 1680x1050 Laptop Display Panel (16/10)"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "ViewSonic CRT"
	VendorName   "ViewSonic"
	ModelName    "ViewSonic GS790"
	HorizSync    30.0 - 97.0
	VertRefresh  50.0 - 180.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Laptop Internal"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "HSync2" "30-97"
	Option	    "VRefresh2" "50-180"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Mode2" "1280x1024"
	Option	    "UseFastTLS" "2" #for wine
	BusID       "PCI:1:0:0"
	Screen      0
EndSection

Section "Device"
	Identifier  "Laptop External"
	Driver      "fglrx"
	Option      "VideoOverlay" "on"
	Option      "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Laptop"
	Device     "Laptop Internal"
	Monitor    "Laptop LCD"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "External"
	Device     "Laptop External"
	Monitor    "Viewsonic CRT"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection

```

Ok this work for me, the install method, but now I got a scrolling problem, is very slow, any help??

By the way, my X800 XT PE still have the overheating issue, but the fan at full blast is controlled just a bit, because the fan isn''t at normal RPM but isn''t at full blast ether.

---

### Post by kingzing1 on 2007-10-24
I'm also having problems with 

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Does anyone know a solution? Thanks!

---

### Post by soulence on 2007-10-24
Will this work on a FireGL? 
And will compiz work with that FireGL and these drivers?

---

### Post by Technophobia on 2007-10-24
soulence ->  Will this work on a FireGL? 


[http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1)

"This release is tested for all ATI Radeon GPU products from the R300 to R600 series. This does not include support for the FireGL series, but the workstation compatibility will be introduced next month in fglrx 8.43."

---

### Post by Tinka on 2007-10-24
I tried this and ended up with a black screen when I rebooted :( The only way I can log on now is in failsafe mode.  Is there anyway to undo what I have done without reinstalling?  Thanks in advance.

---

### Post by Dropknee on 2007-10-24
Use [this]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") guide, this work for me, is you still have some problems, just remove all the fglrx package, restore you original xorg, reinstall this package:

```
sudo apt-get install --reinstall libgl1-mesa-glx libglu1-mesa  libgl1-mesa-dri
```

and reboot and you are done.

I need to do this, this drivers still have the overheating issue in X800 cards, so I go back to the open source once again. I have been waiting all the freaking month for just this.... ohh well .. maybe a good nVidia card is coming soon.

---

### Post by stats on 2007-10-24
Hey
For those of you trying to get compiz to work, this worked for me
[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

AIGLX works fine, but XVideo overlay dint work. (XV however works with compiz off)

Arvind

Radeon 9600 PRO (R350 series)
Kubuntu Gutsy 7.10 - 32bit

---

### Post by raist78 on 2007-10-24
I have a Sapphire Radeon x1950pro AGP and i got the new 8.42 drivers working right. AIGLX is working but i got a small annoyance: animations are very slow. bu the real victory is to have direct rendering YES

---

### Post by _VWV_ on 2007-10-24
The same here.
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
:-( I've reinstalled the driver several times using different howtos. Each time I delited the fglrx driver, reverted back to x-org driver (but didn't do sudo apt-get install --reinstall libgl1-mesa) and recompiled  the 8.42 driver. Then I installed deb packages.. ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)) with 0 result. Seems like AIGLX + ATI doesn't work in my case.:-( :confused:
PLEASE help.

---

### Post by uaeB on 2007-10-24
> **_VWV_ said:**
> The same here.
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
:-( I've reinstalled the driver several times using different howtos. Each time I delited the fglrx driver, reverted back to x-org driver (but didn't do sudo apt-get install --reinstall libgl1-mesa) and recompiled  the 8.42 driver. Then I installed deb packages.. ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)) with 0 result. Seems like AIGLX + ATI doesn't work in my case.:-( :confused:
PLEASE help.

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by rozhman on 2007-10-24
> **jao said:**
> I also get unsupported architecture error when I get to that step. I have an AMD x2 4800 on a x86 Ubuntu Gutsy install. so Ati doesn't support its own architecture? lol. Anybody know what's wrong? It s a2600XT card.
I have an AMDX2 4400 with ATI 2600 pro and I have the same problem on Ubuntu 7.10 x86 .Do you have find any solution?

---

### Post by any1care on 2007-10-24
Is there any possibility for an update anytime soon? Compaq Evo N610C ATI RADEON 7500 needs a fix to get dual display. Still, I Cant really complain, Windblows requires a display driver install, and wont find it automatically.

---

### Post by obsifi on 2007-10-24
i'm stuck with step 8.

```
obsi@ubuntu:~$ sudo aticonfig --initial --force
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
```

I undestand that it should make it own cfg file right?

---

### Post by Neo4 on 2007-10-24
i've followed this guide where:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
using method 2

and after this the flgxinfo still shows:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

I have an x700 mobile...

anyone can help?

---

### Post by CheeseEatingBulldog on 2007-10-24
I have recently reinstalled my gf Sony Vaio (PCG-GR214MP) which has a ATI Radeon Mobility M6 LY card. Now in Feisty, dri was on out of the box and Effects were just a click of a button. Now with Gutsy I have tried many different tries:

Using the ati, radeon and fglrx drivers (the latter not working)
Using the xgl-xserver, which gave me broken graphics and no effects /compiz
Adding modules to the /etc/X11/xorg, which in a default gutsy seem to be vacant
Adding extra options to the device section

None of which in any order, rebooted or not have gotten me dri nor effects.

---

### Post by BernardB on 2007-10-24
Followed the guide and a patch which is supposed to fix AMD64 problems yet I still get the following:
```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

---

### Post by will0957 on 2007-10-24
> **Neo4 said:**
> i've followed this guide where:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
using method 2

and after this the flgxinfo still shows:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

I have an x700 mobile...

anyone can help?

i followed the guide in this thread and have the same result, but it is with a radeon 9500. 

```
~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

---

### Post by will0957 on 2007-10-24
> **BernardB said:**
> Followed the guide and a patch which is supposed to fix AMD64 problems yet I still get the following:
```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

Earlier in the thread someone posted a fix for that issue that worked for me:

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by BernardB on 2007-10-24
I think that works, brilliant!

---

### Post by Neo4 on 2007-10-24
> **will0957 said:**
> i followed the guide in this thread and have the same result, but it is with a radeon 9500. 

```
~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

yes! just like mei have that (if you want to find..) too!

---

### Post by obsifi on 2007-10-24
> **BernardB said:**
> Followed the guide and a patch which is supposed to fix AMD64 problems yet I still get the following:
```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

I have this same thingie right now! What to do? :C

---

### Post by will0957 on 2007-10-24
> **obsifi said:**
> I have this same thingie right now! What to do? :C

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by Raphaelo on 2007-10-24
The solution posted on page 3:

sudo rmmod fglrx
cd /lib/modules/*/misc
sudo insmod fglrx.ko
modprobe fglrx

Works for me, but now i have to do this every time i reboot. Isn't there someway to let let ubuntu do this automaticly on startup?

---

### Post by ZTiger on 2007-10-24
> **will0957 said:**
> i followed the guide in this thread and have the same result, but it is with a radeon 9500. 

```
~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

I'm running into the same problem. I installed using the ATI 8.42.3 (See: [ATI 8.42.3 Released]("http://ubuntuforums.org/showthread.php?t=588383&highlight=ati+install")). When I used this guide before with the 8.40. drivers it just had problems. Every thing seemed to go better with the new driver. Save I'm getting the Mesa driver issue.

Any help would be appreciated.

Here is my xorg.conf
```

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
#	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection


```

---

### Post by jctweb on 2007-10-24
Just so you're aware, there's more to the new ATI driver than just your xorg.conf or the output of fglrxinfo.  When you post something like:

"I still just have the Mesa driver - what do I do ?" - that's just not helpful.

It's not too hard to help you troubleshoot, but you need to give more information:
[LIST=1]
[*]What version of the driver are you installing?
[*]What do the (pertinent) sections of the xorg.conf look like?
[*]What errors are you getting in /var/log/Xorg.0.log?
[*]Are you trying to use Compiz ?  If so, did you make sure you were running the ATI driver first?
[*]Is fglrx whitelisted in /etc/xdg/compiz/compiz-manager ?
[*]Does compiz give you errors when you enable it at the command line?
[*]If you're using the ATI driver <  8.42.3, do you have XGL installed?
[/LIST]

Help us help you - provide as much detail as you can to help pinpoint the issues.

---

### Post by will0957 on 2007-10-24
> **jctweb said:**
> 
It's not too hard to help you troubleshoot, but you need to give more information:
[LIST=1]
[*]What version of the driver are you installing?
[*]What do the (pertinent) sections of the xorg.conf look like?
[*]What errors are you getting in /var/log/Xorg.0.log?
[*]Are you trying to use Compiz ?  If so, did you make sure you were running the ATI driver first?
[*]Is fglrx whitelisted in /etc/xdg/compiz/compiz-manager ?
[*]Does compiz give you errors when you enable it at the command line?
[*]If you're using the ATI driver <  8.42.3, do you have XGL installed?
[/LIST]

Help us help you - provide as much detail as you can to help pinpoint the issues.

[LIST=1]
[*]What version of the driver are you installing? -- 8.42.3
[*]What do the (pertinent) sections of the xorg.conf look like? Not sure which sections are considered pertinent. here's the whole thing:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dri"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```


[*]What errors are you getting in /var/log/Xorg.0.log?
```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc8000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 7291
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```



[*]Are you trying to use Compiz ?  If so, did you make sure you were running the ATI driver first? I would like to use Compiz, but ubuntu won't let me. it is reporting that I am using the following graphics driver:

```
~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```


[*]Is fglrx whitelisted in /etc/xdg/compiz/compiz-manager ?
```
$ cat /etc/xdg/compiz/compiz-manager 
# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
COMPIZ_NAME="compiz.real"

```

Not sure?

[*]Does compiz give you errors when you enable it at the command line?
```
~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

I guess that answers the question of fglrx being whitelisted -- which begs the question, how do I whitelist it?

[*]If you're using the ATI driver <  8.42.3, do you have XGL installed? -- I don't know how to check this.
[/LIST]

Thanks for your help.

---

### Post by jctweb on 2007-10-24
> **will0957 said:**
> 
What do the (pertinent) sections of the xorg.conf look like? Not sure which sections are considered pertinent. here's the whole thing:

Let's start with your xorg.conf and go one step at a time.  Add this to your xorg.conf:
```

Section "DRI"
	Mode         0666
EndSection

```
> 
I would like to use Compiz, but ubuntu won't let me. it is reporting that I am using the following graphics driver:
```
~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```


Once this says you're using an ATI driver, then we can work on the rest of your issues.  For now, let's just get fglrx running :)

---

### Post by will0957 on 2007-10-24
> **jctweb said:**
> Let's start with your xorg.conf and go one step at a time.  Add this to your xorg.conf:
```

Section "DRI"
	Mode         0666
EndSection

```


Once this says you're using an ATI driver, then we can work on the rest of your issues.  For now, let's just get fglrx running :)

I added that section to my xorg.conf, restarted, and the result of fglrxinfo is the same:

```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

Any ideas? Thanks again :)

---

### Post by kportertx on 2007-10-24
Great it all seems to be working...  Except when I run fglrxinfo it showit worked correctly...  Wen i run glxinfo | grep direct, it is still using Mesa GLX Indirct...  Any idears?

kporter@kporter:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release

kporter@kporter:/etc/X11$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
kporter@kporter:/etc/X11$

---

### Post by jctweb on 2007-10-24
> **will0957 said:**
> I added that section to my xorg.conf, restarted, and the result of fglrxinfo is the same:

```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

Any ideas? Thanks again :)

Remember --- one step at a time ;)

Next step.  Let's load a few more modules in xorg.conf.  In your "module" section, here's what I'm loading:
```

Section "Module"
	Load  "bitmap"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection

```

You don't have to do a full restart of your computer for this change - just ctrl+alt+backspace to restart X after you've added those modules.

---

### Post by will0957 on 2007-10-24
> **jctweb said:**
> Remember --- one step at a time ;)

Next step.  Let's load a few more modules in xorg.conf.  In your "module" section, here's what I'm loading:
```

Section "Module"
	Load  "bitmap"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection

```

You don't have to do a full restart of your computer for this change - just ctrl+alt+backspace to restart X after you've added those modules.

I just added all of those modules, restarted X with ctrl+alt+backspace (which I tried last time but X didn't come back up -- it DID come back up this time), and it still shows the mesa driver

---

### Post by jctweb on 2007-10-24
Alrighty - next we need to ensure that the fglrx driver is in the right place.
```

sudo modprobe fglrx

```
If that generates an error, you don't have the correct symlink in place.  
Just for overkill purposes, let's run through some stuff:
```

sudo apt-get -f install
sudo depmod -ae
sudo mkdir /lib/modules/$(uname -r)/volatile
sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

```
Now you should have the fglrx driver *available* to you.  (There have been reported issues that the restricted modules manager deletes the symlink in the volatile directory, but we can address that later)

Restart X after doing those things....let me know what happens.

---

### Post by will0957 on 2007-10-24
> **jctweb said:**
> Alrighty - next we need to ensure that the fglrx driver is in the right place.
```

sudo modprobe fglrx

```
If that generates an error, you don't have the correct symlink in place.  
Just for overkill purposes, let's run through some stuff:
```

sudo apt-get -f install
sudo depmod -ae
sudo mkdir /lib/modules/$(uname -r)/volatile
sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

```
Now you should have the fglrx driver *available* to you.  (There have been reported issues that the restricted modules manager deletes the symlink in the volatile directory, but we can address that later)

Restart X after doing those things....let me know what happens.

Alrighty, i think we're getting warmer. Here's the result of all that:

```
 sudo modprobe fglrx
[sudo] password for jason:
FATAL: Could not open '/lib/modules/2.6.22-14-generic/volatile/fglrx.ko': No such file or directory
jason@vanitymustdie:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdvdread-dev emerald libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@vanitymustdie:~$ sudo depmod -ae
jason@vanitymustdie:~$ sudo mkdir /lib/modules/$(uname -r)/volatile
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/volatile': File exists
jason@vanitymustdie:~$ sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
jason@vanitymustdie:~$ 
```

restarted X

```
 ~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 PRO / 9700
OpenGL version string: 2.0.6958 Release
```

It now says I have ati, but when i try to enable desktop effects it fails. I believe it is because the driver is not whitelisted. Not sure how to do that.

---

### Post by betamike on 2007-10-24
Sorry to push in, but I was having the same problem, with the same error, so I've been following up to this point, but I get a different error on 'sudo modprobe fglrx':
```

betamike@c3po:~$ sudo modprobe fglrx
FATAL: Error running install command for fglrx

```

The rest of the commands ran exactly like will's.  Any ideas?

EDIT: Still getting this:
```

betamike@c3po:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

---

### Post by jctweb on 2007-10-24
> **will0957 said:**
> Alrighty, i think we're getting warmer. Here's the result of all that:

restarted X

```
 ~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 PRO / 9700
OpenGL version string: 2.0.6958 Release
```

It now says I have ati, but when i try to enable desktop effects it fails. I believe it is because the driver is not whitelisted. Not sure how to do that.
I'm going to slightly break from my "one step at a time" mantra for this one...

There's a couple of things that you need to do for compiz:
xorg.conf:
```

Section "Extensions"
	Option	    "Composite" "1"
EndSection

```

/etc/xdg/compiz/compiz-manager:
```

#Add this to the end of the file
WHITELIST="fglrx"

```

Make sure you don't have xgl installed:
```

sudo apt-get remove xserver-xgl

```

(I'm assuming you have all the compiz stuff installed, so I won't go into that.  Suffice to say, you can use synaptic package manager and install the compiz stuff)

Restart X.

From the command line:
```

compiz --replace

```
If you get any errors, post them here.  If you get no errors, you're good to go.

[SIZE="4"][COLOR="Red"]WARNING!!![/COLOR][/SIZE]:  I had problems with the restricted drivers manager deleting the symlink for the fglrx.ko module in the volatile directory.  You will only realize this if you do a complete restart of your computer and end up with the white screen of death.  You may want to remove the restricted drivers manager and the restricted packages in addition to all the steps I've given thus far if this happens to you.

---

### Post by jctweb on 2007-10-24
> **betamike said:**
> Sorry to push in, but I was having the same problem, with the same error, so I've been following up to this point, but I get a different error on 'sudo modprobe fglrx':
```

betamike@c3po:~$ sudo modprobe fglrx
FATAL: Error running install command for fglrx

```

The rest of the commands ran exactly like will's.  Any ideas?



Did you run modprobe after creating the symlink ?  Did you get the same error after restarting X ?  Check your /var/log/Xorg.0.log to see if there are other errors preventing fglrx from running.

I'm leaving the office in about 5 minutes - won't be able to respond to anyone for a few hours so, good luck :)

---

### Post by will0957 on 2007-10-24
> **jctweb said:**
> 

[SIZE="4"][COLOR="Red"]WARNING!!![/COLOR][/SIZE]:  I had problems with the restricted drivers manager deleting the symlink for the fglrx.ko module in the volatile directory.  You will only realize this if you do a complete restart of your computer and end up with the white screen of death.  You may want to remove the restricted drivers manager and the restricted packages in addition to all the steps I've given thus far if this happens to you.

Before I go through with those steps... are there any other better ways around this? I don't necessarily care about having the restricted drivers manager.. but there are some restricted drivers i am using (for my WIFI card, for instance). If I remove the manager, does that mean that i can no longer use my wifi?

How does one go about removing it?

---

### Post by Fenix-TX on 2007-10-24
I have this problem:
```

jesus@tux-CT:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

jesus@tux-CT:~$ glxinfo |grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


```

xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"v4l
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
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


Section "Device"
	Identifier	"ATI Technologies Inc RV350 AQ [Radeon 9600]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"VideoOverlay" 		"on"
	Option		"OpenGLOverlay" 	"off"
	Option		"XaaNoOffscreenPixmaps"
	Option		"UseFastTLS"		"2"
	Option      	"BusType" 		"AGP"
	Option		"PseudoColorVisuals"	"off"
	Option		"TexturedVideo"		"true"
	Option		"UseInternalAGPGART"	"no"
	Option		"mtrr"			"off"
	Option		"no_accel"		"no"
	Option		"no_dri"		"no"
	Option		"EnablePrivateBackZ"	"no"
EndSection

#Section "ServerFlags"
#	Option		"AIGLX"		"off"
#EndSection

#Section "Extensions"
#	Option		"Composite"	"Disable"
#EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AQ [Radeon 9600]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


Xorg.log.0
```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux tux-CT 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 24 21:53:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "ATI Technologies Inc RV350 AQ [Radeon 9600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3189 card 147b,1408 rev 80 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 109e,036e card 0000,0000 rev 11 class 04,00,00 hdr 80
(II) PCI: 00:0b:1: chip 109e,0878 card 0000,0000 rev 11 class 04,80,00 hdr 80
(II) PCI: 00:0f:0: chip 1106,3149 card 147b,1408 rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 147b,1408 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 147b,1408 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 147b,1408 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 147b,1408 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 147b,1408 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 147b,1408 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 147b,1408 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 147b,1408 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 147b,1408 rev 78 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4151 card 12ab,4151 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4171 card 12ab,4150 rev 00 class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe80fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:11:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe8100000/12
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AQ [Radeon 9600] rev 0, Mem @ 0xc0000000/28, 0xe8030000/16, I/O @ 0xc000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary) rev 0, Mem @ 0xd0000000/28, 0xe8020000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8103000 - 0xe81030ff (0x100) MX[B]
	[1] -1	0	0xe8102000 - 0xe81020ff (0x100) MX[B]
	[2] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B](B)
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[9] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000e200 - 0x0000e20f (0x10) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000de00 - 0x0000de0f (0x10) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000ee07 (0x8) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8103000 - 0xe81030ff (0x100) MX[B]
	[1] -1	0	0xe8102000 - 0xe81020ff (0x100) MX[B]
	[2] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B](B)
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[9] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000e200 - 0x0000e20f (0x10) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000de00 - 0x0000de0f (0x10) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000ee07 (0x8) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
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
	[4] -1	0	0xe8103000 - 0xe81030ff (0x100) MX[B]
	[5] -1	0	0xe8102000 - 0xe81020ff (0x100) MX[B]
	[6] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B](B)
	[11] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000e200 - 0x0000e20f (0x10) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000de00 - 0x0000de0f (0x10) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[25] -1	0	0x0000ee00 - 0x0000ee07 (0x8) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "fglx"
(WW) Warning, couldn't open module fglx
(II) UnloadModule: "fglx"
(EE) Failed to load module "fglx" (module does not exist, 0)
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4151) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8103000 - 0xe81030ff (0x100) MX[B]
	[5] -1	0	0xe8102000 - 0xe81020ff (0x100) MX[B]
	[6] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B](B)
	[11] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000e200 - 0x0000e20f (0x10) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000de00 - 0x0000de0f (0x10) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[25] -1	0	0x0000ee00 - 0x0000ee07 (0x8) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82088a8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8103000 - 0xe81030ff (0x100) MX[B]
	[5] -1	0	0xe8102000 - 0xe81020ff (0x100) MX[B]
	[6] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B](B)
	[11] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[22] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[24] -1	0	0x0000e200 - 0x0000e20f (0x10) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[26] -1	0	0x0000de00 - 0x0000de0f (0x10) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[28] -1	0	0x0000ee00 - 0x0000ee07 (0x8) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "BusType" "AGP"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(**) fglrx(0): Option "UseFastTLS" "2"
(**) fglrx(0): Option "EnablePrivateBackZ" "no"
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(**) fglrx(0): Option "TexturedVideo" "true"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI RADEON 9600 Series" (Chipset = 0x4151)
(--) fglrx(0): (PciSubVendor = 0x12ab, PciSubDevice = 0x4151)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xe8030000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(**) fglrx(0): Option "mtrr" "off"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(**) fglrx(0): Forced into AGP mode
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 10b  Serial#: 1196634423
(II) fglrx(0): Year: 2005  Week: 10
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.633 redY: 0.351   greenX: 0.298 greenY: 0.592
(II) fglrx(0): blueX: 0.143 blueY: 0.092   whiteX: 0.316 whiteY: 0.337
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HMEY311870
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2d0b0137315347
(II) fglrx(0): 	0a0f01036c221b782a36a1a2594c9724
(II) fglrx(0): 	175156bfef808180714f010101010101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300520e1100001e000000fd00384b1e
(II) fglrx(0): 	510e000a202020202020000000fc0053
(II) fglrx(0): 	796e634d61737465720a2020000000ff
(II) fglrx(0): 	00484d45593331313837300a202000d0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 324/179MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(**) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 37 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (340, 270) mm
(--) fglrx(0): DPI set to (95, 96)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: no
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(0): UseFastTLS=2
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8030000 - 0xe803ffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe8103000 - 0xe81030ff (0x100) MX[B]
	[7] -1	0	0xe8102000 - 0xe81020ff (0x100) MX[B]
	[8] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000e200 - 0x0000e20f (0x10) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[29] -1	0	0x0000de00 - 0x0000de0f (0x10) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[31] -1	0	0x0000ee00 - 0x0000ee07 (0x8) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7ed3000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.42.3
(II) fglrx(0):     Date: Oct 19 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 21.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f000a1b bridge: 0x1106/0x3189
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000b1a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0100000 FBMappedSize: 0x00701c00
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1435)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 411
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(**) fglrx(0): Option "XaaNoOffscreenPixmaps"
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
BOGUS LENGTH in write keyboard desc, expected 5400, got 5404
BOGUS LENGTH in write keyboard desc, expected 5636, got 5640
BOGUS LENGTH in write keyboard desc, expected 5684, got 5688
BOGUS LENGTH in write keyboard desc, expected 5680, got 5684
BOGUS LENGTH in write keyboard desc, expected 5696, got 5700
BOGUS LENGTH in write keyboard desc, expected 5408, got 5412


```

---

### Post by jctweb on 2007-10-24
> **will0957 said:**
> Before I go through with those steps... are there any other better ways around this? I don't necessarily care about having the restricted drivers manager.. but there are some restricted drivers i am using (for my WIFI card, for instance). If I remove the manager, does that mean that i can no longer use my wifi?

How does one go about removing it?

My wifi card uses the restricted drivers as well.  You don't need the manager to use the driver.  I would first start with removing the manager (you can do this with the synaptic package manager).  If you end up with a white screen of death, you may want to download the windows drivers for your wifi card and then just use ndiswrapper.  Once that works, you can remove the restricted modules altogether, I think.

---

### Post by betamike on 2007-10-24
I ended up getting it working by doing the installation again, but made sure to uninstall linux-restricted-modules before.

Thanks for the help!

---

### Post by NOSintake on 2007-10-24
ok, im having a problem. it says:
Warning: Could not find configuration file

what configuration file am i looking for?

---

### Post by gnychis on 2007-10-24
i have an x300, and according to the release notes it is supported by the new driver, but when i go to [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) to get it, it gives me the 8.40.4 driver, ideas?

---

### Post by LeBurt on 2007-10-25
I've been trying and trying and some more since Gutsy was out and I'm still not an inch ahead of where I was. It appears I'm hitting every problem in the book installing drivers for my Radeon All-In-Wonder 9600 (RV350 GPU). I have however tried to document my problems as best I can. Help would be greatly appreciated!!

Problem: I cannot get ATI's fglrx driver to work.

Symptom: Upon booting, I get a black screen and no response whatsoever from anything. My only option out is a hard reset.

What I did so far:

1. Fresh Gutsy install, all booted ok using "ati" device in xorg.conf

2. Followed procedure on page 1 of this thread using the new 8.42.3 driver, went up to step 7 and rebooted as suggested. I was able to log in normally and then, whitescreen! In fact, I can see my Desktop for a very short time before everything turns white. Below are xorg.conf and Xorg.0.log for this attempt.

xorg.conf:
```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Acer AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1680" "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Desktopita-L 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 24 20:42:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Acer AL2216W"
(**) |   |-->Device "ATI Technologies Inc RV350 AP [Radeon 9600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0760 card 105b,0c54 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 105b,0c54 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 105b,0c54 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 105b,0c54 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 105b,0c54 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 105b,0c54 rev 01 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 163c,3052 card 163c,3052 rev 04 class 07,03,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,4150 card 1002,4722 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4170 card 1002,4723 rev 00 class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe80fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xe7ffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AP [Radeon 9600] rev 0, Mem @ 0xd8000000/27, 0xe8030000/16, I/O @ 0xd000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xe8020000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[1] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[2] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[3] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[4] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[5] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[1] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[2] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[3] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[4] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[5] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9600 AP (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[22] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[26] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[27] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xe8030000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150)
(--) RADEON(0): Linear framebuffer at 0xd8000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=19575
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port1: DDCType-4, DACType-1, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-1 using monitor section Acer AL2216W
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "CRT2_DDC" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- CRT2_DDC
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) RADEON(0): Year: 2006  Week: 22
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: Acer AL2216W
(II) RADEON(0): Serial No: ETL7409038
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047274ad47232062
(II) RADEON(0): 	16100103682f1e782ec585a459499a24
(II) RADEON(0): 	125054bfef0081808140714f9500950f
(II) RADEON(0): 	b30081c08bc021399030621a274068b0
(II) RADEON(0): 	3600d9281100001c000000fd00384c1e
(II) RADEON(0): 	5215000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c32323136570a000000ff
(II) RADEON(0): 	0045544c373430393033382020200006
finished output detect: 0
(II) RADEON(0): DDC Type: 4, Detected Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) RADEON(0): Year: 2006  Week: 22
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: Acer AL2216W
(II) RADEON(0): Serial No: ETL7409038
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047274ad47232062
(II) RADEON(0): 	16100103682f1e782ec585a459499a24
(II) RADEON(0): 	125054bfef0081808140714f9500950f
(II) RADEON(0): 	b30081c08bc021399030621a274068b0
(II) RADEON(0): 	3600d9281100001c000000fd00384c1e
(II) RADEON(0): 	5215000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c32323136570a000000ff
(II) RADEON(0): 	0045544c373430393033382020200006
(II) RADEON(0): Output VGA-1 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) RADEON(0): Year: 2006  Week: 22
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: Acer AL2216W
(II) RADEON(0): Serial No: ETL7409038
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047274ad47232062
(II) RADEON(0): 	16100103682f1e782ec585a459499a24
(II) RADEON(0): 	125054bfef0081808140714f9500950f
(II) RADEON(0): 	b30081c08bc021399030621a274068b0
(II) RADEON(0): 	3600d9281100001c000000fd00384c1e
(II) RADEON(0): 	5215000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c32323136570a000000ff
(II) RADEON(0): 	0045544c373430393033382020200006
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(II) RADEON(0): Modeline "1280x720"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
(II) RADEON(0): Modeline "1360x765"   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) RADEON(0): EDID vendor "ACR", prod id 44404
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1360x765"x59.8   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync (47.6 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): DDC Type: 4, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-1 connected
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-1 using initial mode 1680x1050
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (470, 300) mm
(**) RADEON(0): DPI set to (90, 101)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): MM_TABLE: 01-0c-0f-19-06-00-33-66-02-05-06-00-00-07
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8030000 - 0xe803ffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[7] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[8] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[9] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[10] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[11] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[24] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[25] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[26] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[28] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[29] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[30] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xd8000000,0x8000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1728,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1728,1202)
(II) RADEON(0): Largest offscreen area available: 1728 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x202b000
(II) RADEON(0): Will use depth buffer at offset 0x2814000
(II) RADEON(0): Will use 81920 kb for textures at offset 0x2ffd000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf8b3c000
(II) RADEON(0): [drm] mapped SAREA 0xf8b3c000 to 0xb7ae7000
(II) RADEON(0): [drm] framebuffer handle = 0xd8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(==) RADEON(0): Using AGP 8x
(II) RADEON(0): [agp] Mode 0x1f004e0a [AGP 0x1039/0x0760; Card 0x1002/0x4150]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(EE) RADEON(0): [agp] Could not bind
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf8b3c000 at 0xb7ae7000
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1202)
(II) RADEON(0): Largest offscreen area available: 1728 x 6986
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): Using R200 i2c bus access method
(II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
(II) Loading sub module "fi1236"
(II) LoadModule: "fi1236"
(II) Loading /usr/lib/xorg/modules/multimedia//fi1236_drv.so
(II) Module fi1236: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): I2C device "Radeon multimedia bus:FI12xx Tuner" registered at address 0xC6.
(II) RADEON(0): Detected FI1236W device at 0xc6
(II) Loading sub module "tda9885"
(II) LoadModule: "tda9885"
(II) Loading /usr/lib/xorg/modules/multimedia//tda9885_drv.so
(II) Module tda9885: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): I2C device "Radeon multimedia bus:TDA9885 Alignment-free IF-PLL" registered at address 0x86.
(II) Loading sub module "uda1380"
(II) LoadModule: "uda1380"
(II) Loading /usr/lib/xorg/modules/multimedia//uda1380_drv.so
(II) Module uda1380: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "msp3430"
(II) LoadModule: "msp3430"
(II) Loading /usr/lib/xorg/modules/multimedia//msp3430_drv.so
(II) Module msp3430: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): No response from device 0 on VIP bus
(II) RADEON(0): Device 1 on VIP bus ids as 0x4d4a1002
(II) RADEON(0): No response from device 2 on VIP bus
(II) RADEON(0): No response from device 3 on VIP bus
(II) RADEON(0): Detected Rage Theatre as device 1 on VIP bus with id 0x4d4a1002
(II) RADEON(0): Detected Rage Theatre revision 00000001
(II) RADEON(0): video decoder type is 0x4c77 (BIOS value) versus 0x4c77 (current PLL setting)
(II) RADEON(0): Tuner is on port 0
(II) RADEON(0): Composite connector is port 2
(II) RADEON(0): SVideo connector is port 6
(II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=2, svideo=6
(II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=2, svideo=6
(II) RADEON(0): video decoder type used: 0x0006
(II) RADEON(0): Going to load the corresponding theatre module
(II) Loading sub module "theatre200"
(II) LoadModule: "theatre200"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre200_drv.so
(II) Module theatre200: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): Microcode: Use default microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use default microcode type: BINARY
(EE) RADEON(0): Microcode: cannot load microcode
(II) RADEON(0): Rage Theatre disabled
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 473 x 296
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ca"
(**) Generic Keyboard: XkbLayout: "ca"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) RADEON(0): Year: 2006  Week: 22
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: Acer AL2216W
(II) RADEON(0): Serial No: ETL7409038
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047274ad47232062
(II) RADEON(0): 	16100103682f1e782ec585a459499a24
(II) RADEON(0): 	125054bfef0081808140714f9500950f
(II) RADEON(0): 	b30081c08bc021399030621a274068b0
(II) RADEON(0): 	3600d9281100001c000000fd00384c1e
(II) RADEON(0): 	5215000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c32323136570a000000ff
(II) RADEON(0): 	0045544c373430393033382020200006
(II) RADEON(0): Output VGA-1 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) RADEON(0): Year: 2006  Week: 22
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: Acer AL2216W
(II) RADEON(0): Serial No: ETL7409038
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047274ad47232062
(II) RADEON(0): 	16100103682f1e782ec585a459499a24
(II) RADEON(0): 	125054bfef0081808140714f9500950f
(II) RADEON(0): 	b30081c08bc021399030621a274068b0
(II) RADEON(0): 	3600d9281100001c000000fd00384c1e
(II) RADEON(0): 	5215000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c32323136570a000000ff
(II) RADEON(0): 	0045544c373430393033382020200006
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(II) RADEON(0): Modeline "1280x720"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
(II) RADEON(0): Modeline "1360x765"   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) RADEON(0): EDID vendor "ACR", prod id 44404
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1360x765"x59.8   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync (47.6 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): DDC Type: 4, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
SetClientVersion: 0 9
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) RADEON(0): Year: 2006  Week: 22
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: Acer AL2216W
(II) RADEON(0): Serial No: ETL7409038
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047274ad47232062
(II) RADEON(0): 	16100103682f1e782ec585a459499a24
(II) RADEON(0): 	125054bfef0081808140714f9500950f
(II) RADEON(0): 	b30081c08bc021399030621a274068b0
(II) RADEON(0): 	3600d9281100001c000000fd00384c1e
(II) RADEON(0): 	5215000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c32323136570a000000ff
(II) RADEON(0): 	0045544c373430393033382020200006
(II) RADEON(0): Output VGA-1 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) RADEON(0): Year: 2006  Week: 22
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: Acer AL2216W
(II) RADEON(0): Serial No: ETL7409038
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047274ad47232062
(II) RADEON(0): 	16100103682f1e782ec585a459499a24
(II) RADEON(0): 	125054bfef0081808140714f9500950f
(II) RADEON(0): 	b30081c08bc021399030621a274068b0
(II) RADEON(0): 	3600d9281100001c000000fd00384c1e
(II) RADEON(0): 	5215000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c32323136570a000000ff
(II) RADEON(0): 	0045544c373430393033382020200006
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(II) RADEON(0): Modeline "1280x720"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
(II) RADEON(0): Modeline "1360x765"   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) RADEON(0): EDID vendor "ACR", prod id 44404
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1360x765"x59.8   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync (47.6 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): DDC Type: 4, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
disable montype: 1
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
```

3. Hit [CTRL][ALT][F1] to get out of X and did steps 8 and 9 of the procedure on page 1. xorg.conf now looked like this:

xorg.conf:
```

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "ca"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Acer AL2216W"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor    "Acer AL2216W"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1680x1680" "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

4. Rebooted. Got to a black screen this time. Total crash. Did a hard reset and rebooted in recovery mode to get the log file:

Xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Desktopita-L 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 24 22:30:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0760 card 105b,0c54 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 105b,0c54 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 105b,0c54 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 105b,0c54 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 105b,0c54 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 105b,0c54 rev 01 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 163c,3052 card 163c,3052 rev 04 class 07,03,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,4150 card 1002,4722 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4170 card 1002,4723 rev 00 class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe80fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xe7ffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AP [Radeon 9600] rev 0, Mem @ 0xd8000000/27, 0xe8030000/16, I/O @ 0xd000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xe8020000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[1] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[2] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[3] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[4] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[5] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[1] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[2] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[3] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[4] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[5] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4150) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82095d0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[22] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[26] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[27] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI RADEON 9600 Series" (Chipset = 0x4150)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x4722)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd8000000
(--) fglrx(0): MMIO registers at 0xe8030000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) fglrx(0): Year: 2006  Week: 22
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) fglrx(0): Monitor name: Acer AL2216W
(II) fglrx(0): Serial No: ETL7409038
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00047274ad47232062
(II) fglrx(0): 	16100103682f1e782ec585a459499a24
(II) fglrx(0): 	125054bfef0081808140714f9500950f
(II) fglrx(0): 	b30081c08bc021399030621a274068b0
(II) fglrx(0): 	3600d9281100001c000000fd00384c1e
(II) fglrx(0): 	5215000a202020202020000000fc0041
(II) fglrx(0): 	63657220414c32323136570a000000ff
(II) fglrx(0): 	0045544c373430393033382020200006
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
```

I haven't seen enough of those yet but it doesn't seem like it's ending properly.

5. While I was in recovery mode, I switched back to the original (ati) xorg.conf file and rebooted. Got to the same white screen as above.

6. I hit [CTRL][ALT][F1] again and switched to the second (fglrx) xorg.conf file. I went back to the still-white X and hit [CTRL][ALT][Backspace] to restart it (found the trick on this thread, thanks! Still learning...) This time, everything booted ok. The xorg log below:

Xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Desktopita-L 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 24 22:35:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0760 card 105b,0c54 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 105b,0c54 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 105b,0c54 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 105b,0c54 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 105b,0c54 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 105b,0c54 rev 01 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 163c,3052 card 163c,3052 rev 04 class 07,03,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,4150 card 1002,4722 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4170 card 1002,4723 rev 00 class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe80fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xe7ffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AP [Radeon 9600] rev 0, Mem @ 0xd8000000/27, 0xe8030000/16, I/O @ 0xd000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xe8020000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[1] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[2] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[3] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[4] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[5] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[1] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[2] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[3] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[4] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[5] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4150) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82095d0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[5] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[6] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[7] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[8] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[9] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[22] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[26] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[27] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI RADEON 9600 Series" (Chipset = 0x4150)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x4722)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd8000000
(--) fglrx(0): MMIO registers at 0xe8030000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) fglrx(0): Year: 2006  Week: 22
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) fglrx(0): Monitor name: Acer AL2216W
(II) fglrx(0): Serial No: ETL7409038
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00047274ad47232062
(II) fglrx(0): 	16100103682f1e782ec585a459499a24
(II) fglrx(0): 	125054bfef0081808140714f9500950f
(II) fglrx(0): 	b30081c08bc021399030621a274068b0
(II) fglrx(0): 	3600d9281100001c000000fd00384c1e
(II) fglrx(0): 	5215000a202020202020000000fc0041
(II) fglrx(0): 	63657220414c32323136570a000000ff
(II) fglrx(0): 	0045544c373430393033382020200006
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 324/196MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 32 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (470, 300) mm
(--) fglrx(0): DPI set to (90, 88)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8030000 - 0xe803ffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe8124000 - 0xe8124fff (0x1000) MX[B]
	[7] -1	0	0xe8123000 - 0xe8123fff (0x1000) MX[B]
	[8] -1	0	0xe8122000 - 0xe8122fff (0x1000) MX[B]
	[9] -1	0	0xe8121000 - 0xe8121fff (0x1000) MX[B]
	[10] -1	0	0xe8120000 - 0xe8120fff (0x1000) MX[B]
	[11] -1	0	0xe8125000 - 0xe8125fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xe8030000 - 0xe803ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe8020000 - 0xe802ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[24] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[25] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[26] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[28] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[29] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[30] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 7141
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ca"
(**) Generic Keyboard: XkbLayout: "ca"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Wed Oct 24 22:36:01 2007: 5861 X: client 2 rejected from local host (uid 1000)
AUDIT: Wed Oct 24 22:36:01 2007: 5861 X: client 3 rejected from local host (uid 1000)
SetClientVersion: 0 9
```

Again, I can't analyze this in detail but what strikes me is that a module DRI did not initialize. What's that? Important?

7. I thought I was out of the water but a simple reboot brought me back to the black screen.

8. I did my steps 4, 5 and 6 again and tried:

```
burt@Desktopita-L:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

burt@Desktopita-L:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```

And that's where I am.
Help...
Please...
:confused:

More details if you want them:
a) using an ACER AL2216W LCD display, native resolution 1680x1050
b) my CPU is AMD 64 3000+
c) Gutsy is the i386 32-bit version, stock
d) Graphic card is ATI All-in-Wonder 9600 series (RV350 GPU I believe)

---

### Post by jctweb on 2007-10-25
This error:
```
(WW) fglrx(0): Failed to open DRM connection

```
occurs because of the DRI extension.  Add this to your xorg.conf:
```

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by ASPCartman on 2007-10-25
i done everything as it must be and all is ok butt....

```

aspcartman@ASP:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

```

aspcartman@ASP:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by kportertx on 2007-10-25
I cannot find a solution to this problem, I have searched many forums.
When I run fglrxinfo I get
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release

```

So great that works as it is supposed to but when I run  glxinfo | grep direct
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

I receive direct rendering No!!! and its using Mesa!!

I am lost on when to go from here.

here is my xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
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
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	Option	    "AIGLX" "true"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

And here is my Xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux kporter 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 25 09:14:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "AIGLX" "true"
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 103c,3091 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 103c,3091 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,3091 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,3091 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,3091 rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,3091 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 103c,3091 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,3091 rev 02 class 04,01,00 hdr 80
(II) PCI: 00:14:6: chip 1002,4378 card 103c,3091 rev 02 class 07,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5955 card 103c,3091 rev 00 class 03,00,00 hdr 00
(II) PCI: 05:00:0: chip 10ec,8139 card 103c,3091 rev 10 class 02,00,00 hdr 00
(II) PCI: 05:02:0: chip 14e4,4318 card 103c,1355 rev 02 class 02,80,00 hdr 00
(II) PCI: 05:09:0: chip 104c,8031 card a400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:20:4), (0,5,9), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc02fffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (5:9:0), (5,6,9), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[1] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) rev 0, Mem @ 0xc8000000/27, 0xc0100000/16, I/O @ 0x9000/8
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
(II) Active PCI resource ranges:
	[0] -1	0	0xc0204000 - 0xc0205fff (0x2000) MX[B]
	[1] -1	0	0xc0208000 - 0xc02080ff (0x100) MX[B]
	[2] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[3] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[4] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[5] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[6] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0204000 - 0xc0205fff (0x2000) MX[B]
	[1] -1	0	0xc0208000 - 0xc02080ff (0x100) MX[B]
	[2] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[3] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[4] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[5] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[6] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
	[4] -1	0	0xc0204000 - 0xc0205fff (0x2000) MX[B]
	[5] -1	0	0xc0208000 - 0xc02080ff (0x100) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x5955) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0204000 - 0xc0205fff (0x2000) MX[B]
	[5] -1	0	0xc0208000 - 0xc02080ff (0x100) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82088b8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0204000 - 0xc0205fff (0x2000) MX[B]
	[5] -1	0	0xc0208000 - 0xc02080ff (0x100) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3091)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON Xpress 200G Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: QDS  Model: 33  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.591 redY: 0.325   greenX: 0.314 greenY: 0.562
(II) fglrx(0): blueX: 0.137 blueY: 0.119   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) fglrx(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) fglrx(0):  QUANTADISPLAY
(II) fglrx(0):  QD15XL062
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004493330000000000
(II) fglrx(0): 	000f0103801e17780a58209753509023
(II) fglrx(0): 	1e505400000001010101010101010101
(II) fglrx(0): 	01010101010164190040410026301888
(II) fglrx(0): 	360030e4100000190000000f0004c02e
(II) fglrx(0): 	c00211111176c0126301000000fe0051
(II) fglrx(0): 	55414e5441444953504c4159000000fe
(II) fglrx(0): 	0051443135584c3036320a20202000f5
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 301/200MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 100/150MHz @ 60Hz []
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 0)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
(**) fglrx(0): *Mode "848x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   65.00  848 960 1096 1344  480 627 633 806
(**) fglrx(0): *Mode "800x600": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   65.00  800 936 1072 1344  600 687 693 806
(**) fglrx(0): *Mode "720x576": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   65.00  720 896 1032 1344  576 675 681 806
(**) fglrx(0): *Mode "720x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   65.00  720 896 1032 1344  480 627 633 806
(**) fglrx(0): *Mode "640x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   65.00  640 856 992 1344  480 627 633 806
(**) fglrx(0):  Default mode "640x400": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   65.00  640 856 992 1344  400 587 593 806
(**) fglrx(0):  Default mode "640x350": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   65.00  640 856 992 1344  350 562 568 806
(**) fglrx(0):  Default mode "512x384": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   65.00  512 792 928 1344  384 579 585 806
(**) fglrx(0):  Default mode "400x300": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   65.00  400 736 872 1344  300 687 693 806 doublescan
(**) fglrx(0):  Default mode "320x240": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   65.00  320 696 832 1344  240 627 633 806 doublescan
(**) fglrx(0):  Default mode "320x200": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   65.00  320 696 832 1344  200 587 593 806 doublescan
(--) fglrx(0): Display dimensions: (300, 230) mm
(--) fglrx(0): DPI set to (86, 84)
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
(**) fglrx(0): *Mode "848x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   65.00  848 960 1096 1344  480 627 633 806
(**) fglrx(0): *Mode "800x600": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   65.00  800 936 1072 1344  600 687 693 806
(**) fglrx(0): *Mode "720x576": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   65.00  720 896 1032 1344  576 675 681 806
(**) fglrx(0): *Mode "720x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   65.00  720 896 1032 1344  480 627 633 806
(**) fglrx(0): *Mode "640x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   65.00  640 856 992 1344  480 627 633 806
(**) fglrx(0):  Default mode "640x400": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   65.00  640 856 992 1344  400 587 593 806
(**) fglrx(0):  Default mode "640x350": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   65.00  640 856 992 1344  350 562 568 806
(**) fglrx(0):  Default mode "512x384": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   65.00  512 792 928 1344  384 579 585 806
(**) fglrx(0):  Default mode "400x300": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   65.00  400 736 872 1344  300 687 693 806 doublescan
(**) fglrx(0):  Default mode "320x240": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   65.00  320 696 832 1344  240 627 633 806 doublescan
(**) fglrx(0):  Default mode "320x200": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   65.00  320 696 832 1344  200 587 593 806 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0204000 - 0xc0205fff (0x2000) MX[B]
	[7] -1	0	0xc0208000 - 0xc02080ff (0x100) MX[B]
	[8] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[9] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[10] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[11] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[12] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[13] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[14] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x3d01000
(II) fglrx(0): [drm] mapped SAREA 0x3d01000 to 0xb7cb2000
(II) fglrx(0): [drm] framebuffer handle = 0x3d02000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.42.3
(II) fglrx(0):     Date: Oct 19 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x03d03000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x00501000
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,1281)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1024 x 513
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
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
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
SetClientVersion: 0 9
```

I noticed from that log I get a slew of > (WW) AIGLX: 3D driver claims to not support visual 0x5b warning messages.  Are the two issues possible related?

Thanks in advanced on any direction or solutions provided.  

O btw off the wall problem I noticed (really no biggy) cyrillic font says its missing so I removed it from xorg.conf... But it still shows up in the log here as missing... Thought it was strange and was interested and any explanation on why I am still recieving that message.

---

### Post by johnapeterson on 2007-10-25
Hey,
Great to find this dummies instruction here, but I am having a little problem in that when I get to the point in your instruction where is says to type:

bash ./ati driver file name*.run --buildpkg Ubuntu/feisty or --buildpkg Ubuntu/gutsy (Depending on your version)

(replacing items with the right info) I get the following:


john@john-desktop:~/Desktop$ bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


I have tried it three time and keep getting this bad substation error, and cannot get beyond this point.  Please help.

John

---

### Post by jctweb on 2007-10-25
> **johnapeterson said:**
> 
john@john-desktop:~/Desktop$ bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy


Have you tried running as sudo?
```

sudo sh ./ati-driver-foo.run --buildpkg Ubuntu/gutsy

```

---

### Post by jctweb on 2007-10-25
> **kportertx said:**
> I cannot find a solution to this problem, I have searched many forums.
When I run fglrxinfo I get
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release

```

So great that works as it is supposed to but when I run  glxinfo | grep direct
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

I receive direct rendering No!!! and its using Mesa!!



There are others that have experienced the problem you're describing - unfortunately I don't know the answer - I can only help people that experienced the same problems that I did :(

There are a lot of discussions about this driver on the [Phoronix Forums]("http://phoronix.com/forums/showthread.php?t=5947") - you may want to check there.

sorry..

---

### Post by frsd on 2007-10-25
I somehow get stuck by step 3.
when i enter: 
debconf libstdc++5 linux-headers-generic

i get

Can't exec "libstdc++5": No such file or directory at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of libstdc++5 linux-headers-generic failed at /usr/share/perl5/Debconf/ConfModule.pm line 58

wtf???

Ive got a X1950 Pro PCIe an i am a total n00b at ubuntu(just installed it 3 days ago)
im thanksful for any replies.

---

### Post by LeBurt on 2007-10-25
> **jctweb said:**
> This error:
```
(WW) fglrx(0): Failed to open DRM connection

```
occurs because of the DRI extension.  Add this to your xorg.conf:
```

Section "DRI"
	Mode	0666
EndSection

```

Thanks for the tip. Unfortunately, no change... :(

---

### Post by ASPCartman on 2007-10-25
So u all guys wanna say, that noone knows solution for Mesa problem?:confused:

---

### Post by jctweb on 2007-10-25
> **ASPCartman said:**
> So u all guys wanna say, that noone knows solution for Mesa problem?:confused:

There are many "solutions" to the Mesa problem - what have you tried?  This thread and several others address most of the issues people are experiencing.  The output of fglrxinfo and glxinfo are only indications of the symptoms - your /var/log/Xorg.0.log is one of the first places to look for errors.  The second place is to check for a properly configured xorg.conf

---

### Post by LeBurt on 2007-10-25
> **LeBurt said:**
> Thanks for the tip. Unfortunately, no change... :(

Wait! I resolved the black screen problem.

Found the answer [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

Added this line in xorg.conf, in the device section containing "fglrx":

```
Option "BusType" "PCI"
```

So now, I'm left with the MESA problem as with a lot of people. I haven't done much research there yet but I'll post my answer here when I find a solution.

---

### Post by johnapeterson on 2007-10-25
Hey,

I was having the problem with this after the second step:

Hey,
Great to find this dummies instruction here, but I am having a little problem in that when I get to the point in your instruction where is says to type:

bash ./ati driver file name*.run --buildpkg Ubuntu/feisty or --buildpkg Ubuntu/gutsy (Depending on your version)

(replacing items with the right info) I get the following:


john@john-desktop:~/Desktop$ bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8............................................ .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .........................
-e ==================================================
-e ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

jctweb mentioned about entering the following code using sudo:

Have you tried running as sudo?
Code:

sudo sh ./ati-driver-foo.run --buildpkg Ubuntu/gutsy

But I still get the same syntax error result.  Could I have gotten a bad copy of the driver?

Thanks,
John

---

### Post by kportertx on 2007-10-25
> **jctweb said:**
> There are others that have experienced the problem you're describing - unfortunately I don't know the answer - I can only help people that experienced the same problems that I did :(

There are a lot of discussions about this driver on the [Phoronix Forums]("http://phoronix.com/forums/showthread.php?t=5947") - you may want to check there.

sorry..

Thanks for the tip...  If I find a solution I will post it here.  Good luck

---

### Post by jctweb on 2007-10-25
> **johnapeterson said:**
> 
But I still get the same syntax error result.  Could I have gotten a bad copy of the driver?


It's possible - doesn't hurt to try downloading again.  OTOH, you've ensured that you have all the pre-requisite packages, right?  Here's the required packages mentioned on the ATI site:

From the ATI release notes:
> 
The following packages must be installed in order for the Catalyst&#8482; Linux driver to install and work properly:

    * XFree86-Mesa-libGL
    * libstdc++
    * libgcc
    * XFree86-libs
    * fontconfig
    * freetype
    * zlib 


If you've made sure all of those are installed and it still doesn't work, I'm not 100% sure I know how to get you past running the script to make the packages.  I supposed I could make my debs available ?  Not sure if that will help or not.

---

### Post by andreeh on 2007-10-26
A very common problem (if you get mesa) is that your old driver is still active.
```
sudo rm /lib/modules/2.6.22-14-generic/volatile/fglrx.ko
```
```
sudo depmod -a
```

Run this (or just reboot):
Press CTRL+ALT+F1 and login
```
sudo invoke-rc.d gdm stop
```
```
sudo modprobe -r fglrx
```
```
sudo invoke-rc.d gdm start
```
(Since fglrx is modprobe'd on the start of GDM, there's no need to manually do it)

Hope this helps.

---

### Post by LeBurt on 2007-10-26
No effect, i still have: 

burt@Desktopita-L:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

---

### Post by igmo on 2007-10-26
You sir, are my new hero

---

### Post by Laidbacklux on 2007-10-26
the solution to "./ati-installer.sh: 176: Syntax error: Bad substitution"  :

[URL="http://ubuntuforums.org/showthread.php?t=286769"]
[http://ubuntuforums.org/showthread.php?t=286769](http://ubuntuforums.org/showthread.php?t=286769)[/URL]

Got past that, but the problem for me now is 

Requested package is not supported.

I have tried any driver close to my videocard from ati website, problem is I have ATI All-in-wonder Radeon, a model not listed under linux at the ati website.

---

### Post by andreeh on 2007-10-26
> **LeBurt said:**
> No effect, i still have: 

burt@Desktopita-L:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

Could you please post the output of
```
grep -i fglrx /var/log/Xorg.0.log
```

---

### Post by kshane on 2007-10-26
This is my 3rd or 4th time running this how-to.  I have the same problem each time.

After this step:
> 

Code:

sudo aticonfig --overlay-type=Xv

This will enable Enable Video acceleration (Xv Overlay). Now reboot again. If you come up with errors writing to your xorg.conf file, type in this command sudo -i then enter in your password. Now retype the previous commands for aticonfig, after that reboot and follow step 9.

Step 9. Open up the terminal to make sure you have ATI installed correctly type in
Code:

fglrxinfo




I get this:

```

kevin@enigma:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

Can someone help here?  I've been waiting for the new ATI driver and am nearly going insane with this...

Thanks!

Kevin

---

### Post by gillis on 2007-10-26
> **kshane said:**
> This is my 3rd or 4th time running this how-to.  I have the same problem each time.

After this step:


I get this:

```

kevin@enigma:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

Can someone help here?  I've been waiting for the new ATI driver and am nearly going insane with this...

Thanks!

Kevin


The most common sollution of getting mesa instead of ati is  
enabling fglrx in xorg.conf.
somewhere you see driver = "ati"  change this into driver = "fglrx" .
other way is to enable propiated driver in system -> preferences -> driver
most tutorials out here dont tell you that to do that.
i took me 2 days to find that out.

---

### Post by kshane on 2007-10-26
Whoa...  My xorg.conf looks TOTALLY different than I've seen it before.  I don't klnow where to begin with it!  

```


# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
	Option		"Composite"	"0"
EndSection


```

Is something in here putting Mesa in???

HELP PLEASE!!!

---

### Post by jctweb on 2007-10-26
> **kshane said:**
> Whoa...  My xorg.conf looks TOTALLY different than I've seen it before.  I don't klnow where to begin with it!  

```

--snip--

```

Is something in here putting Mesa in???

HELP PLEASE!!!

I hate to be a bother on this - but how much of this thread have you actually read and tried?  At the time I'm posting this, there are ***11*** pages of tips, tricks, and suggestions for:
[LIST=1]
[*]What you xorg.conf should look like
[*]How to troubleshoot problems
[/LIST]
Your post makes me think of this scenario: 
You read the title of the OP, decided you have a related problem, then skipped to the end and hit "Reply"

I've spent HOURS in this and one other thread doing my best to help people with the EXACT problem you are experiencing.  I can't keep doing the same work over and over again.  Spend some time and read through everything here.  I guarantee the problem you're trying to solve is in here somewhere.

I'm not trying to be mean - but you have no idea how frustrating it is to try and help people only to be ignored.

---

### Post by kshane on 2007-10-26
Appreciate your candor.  I have maybe 1 or 2 hours a day to work on my box because of my job.  I can't do anything during work.  (critical care nurse), so I try to wack things out at home when I can.

There are (currently) 105 replies to this thread.  No, I haven't read each reply.  I have tried to skim through and find something like my problem.  Usually, I find what I THINK is similar, only to find it isn't, or it references something else I can't find, so I post.

So happens I'm off today, so I can put a little more time into it.  I have 6 tabs open on my browser right now trying to find answers.

Not everyone works IT and can do things at work.  Not everyone is living with their parents and have all the time in the world.  I don't mean to be offensive - truly.  But, it seems I get more lectures than help.  

Maybe I'm too impatient, my apologies for that.  It''s just that I've been trying to get this stuff working for about 4 months straight (I DID get Compiz going once - thanks jsully - but my box was so slow, it wasn't worth using).  Now the new ATI driver comes out and I can't even get the driver installed!  I had no problems with the last one, just this one.

Later

---

### Post by jctweb on 2007-10-26
> **kshane said:**
> Appreciate your candor.  I have maybe 1 or 2 hours a day to work on my box because of my job.  I can't do anything during work.  (critical care nurse), so I try to wack things out at home when I can.

There are (currently) 105 replies to this thread.  No, I haven't read each reply.  I have tried to skim through and find something like my problem.  Usually, I find what I THINK is similar, only to find it isn't, or it references something else I can't find, so I post.

I'd start with the xorg.conf.  There are several examples within the thread.  [Here's one that I posted]("http://ubuntuforums.org/showpost.php?p=3614546&postcount=34")

Here's a step-by-step (sorta) process I took a person through to try and get things running.  The conversation [starts with this one]("http://ubuntuforums.org/showthread.php?p=3621506#post3621506").

> 
Not everyone works IT and can do things at work.  Not everyone is living with their parents and have all the time in the world.  I don't mean to be offensive - truly.  But, it seems I get more lectures than help.  

Maybe I'm too impatient, my apologies for that.  It''s just that I've been trying to get this stuff working for about 4 months straight (I DID get Compiz going once - thanks jsully - but my box was so slow, it wasn't worth using).  Now the new ATI driver comes out and I can't even get the driver installed!  I had no problems with the last one, just this one.
Later
I wish I was living with my parents.  At least I'd have fewer bills to contend with.  I'm sure my wife and kids would get annoyed about the move. :)

To be totally honest with you, the latest ATI driver is crap if you're on a laptop.  Dual-head support causes memory problems and compiz actually slows down (if you use it) compared to using XGL.  They still haven't nailed down being able to use STANDBY (pretty common laptop activity). And there are issues with firefox scrolling slowly once you manage to get compiz working.  If you're not on a laptop, go ahead and move forward with the install; otherwise stick with the restricted drivers that come with Ubuntu.  I was able to get Compiz working with those drivers in less than 10 minutes.

Let us know how things go.

---

### Post by Jaydude765 on 2007-10-26
I am also getting the mesa driver issue. I have tried most the tips on the 11 pages here so far.

I have a radion X1400 in a dell inspiron 6400.

My XORG.conf:

> 
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

I have tried commenting out the default and generic devices/screens etc but that cause various problems when logging in (error messages such as cannot find trash can?!)

Here is my grep -i fglrx /var/log/Xorg.0.log:

> (II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x82099f0
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1400" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2003)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2006  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  DD282154X3
(II) fglrx(0):  '@PZ&#65533;&#65533;&#65533;&#65533;
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff004ca3000000000000
(II) fglrx(0):  00100103802115780a87f594574f8c27
(II) fglrx(0):  27505400000001010101010101010101
(II) fglrx(0):  010101010101c71b00a0502017303020
(II) fglrx(0):  26004bcf100000190000000f00000000
(II) fglrx(0):  00000000002387026400000000fe0044
(II) fglrx(0):  443238320431353458330a20000000fe
(II) fglrx(0):  002740505a81b0d9ff01010a2020009d
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 432/396MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 324/135MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 392/252MHz @ 60Hz [enable sleep, thermal diode mode]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1328 1360 1440  800 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   71.11  1280 1328 1360 1440  720 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1328 1360 1440  768 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1328 1360 1440  600 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   71.11  640 1328 1360 1440  432 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1328 1360 1440  400 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 1328 1360 1440  384 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   71.11  400 1328 1360 1440  300 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   71.11  320 1328 1360 1440  240 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   71.11  320 1328 1360 1440  200 802 808 823 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1328 1360 1440  800 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   71.11  1280 1328 1360 1440  720 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1328 1360 1440  768 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1328 1360 1440  600 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   71.11  640 1328 1360 1440  432 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1328 1360 1440  400 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 1328 1360 1440  384 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   71.11  400 1328 1360 1440  300 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   71.11  320 1328 1360 1440  240 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   71.11  320 1328 1360 1440  200 802 808 823 +hsync +vsync
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
root@jason-laptop:~# gedit /etc/X11/xorg.conf
^[[A^[[Aroot@jason-laptop:~# grep -i fglrx /var/log/Xorg.0.log
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x82099f0
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1400" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2003)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2006  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  DD282154X3
(II) fglrx(0):  '@PZ&#65533;&#65533;&#65533;&#65533;
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff004ca3000000000000
(II) fglrx(0):  00100103802115780a87f594574f8c27
(II) fglrx(0):  27505400000001010101010101010101
(II) fglrx(0):  010101010101c71b00a0502017303020
(II) fglrx(0):  26004bcf100000190000000f00000000
(II) fglrx(0):  00000000002387026400000000fe0044
(II) fglrx(0):  443238320431353458330a20000000fe
(II) fglrx(0):  002740505a81b0d9ff01010a2020009d
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 432/396MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 324/135MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 392/252MHz @ 60Hz [enable sleep, thermal diode mode]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1328 1360 1440  800 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   71.11  1280 1328 1360 1440  720 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1328 1360 1440  768 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1328 1360 1440  600 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   71.11  640 1328 1360 1440  432 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1328 1360 1440  400 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 1328 1360 1440  384 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   71.11  400 1328 1360 1440  300 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   71.11  320 1328 1360 1440  240 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   71.11  320 1328 1360 1440  200 802 808 823 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1328 1360 1440  800 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   71.11  1280 1328 1360 1440  720 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1328 1360 1440  768 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1328 1360 1440  600 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1328 1360 1440  480 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   71.11  640 1328 1360 1440  432 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1328 1360 1440  400 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 1328 1360 1440  384 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   71.11  400 1328 1360 1440  300 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   71.11  320 1328 1360 1440  240 802 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   71.11  320 1328 1360 1440  200 802 808 823 +hsync +vsync
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
root@jason-laptop:~# grep -i fglrx /var/log/Xorg.0.log


and the output of fglrxinfo:
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


Any ideas? I have reinstalled and tried I think everything mentioned here so far. :|

Jason

---

### Post by kshane on 2007-10-26
I appreciate the assist.  I think I have reached the limits of my frustration.  I'm going out in a few hours when the stores open and buying a new Nvidia.  I feel really screwed by ATI.  I spent a pretty penny for my card and now, six months later, it's selling for half what I paid (gee, what a surprise).  

It seems to me that Nvidia users have much less trouble and seem to get good results with low-end cards.  So, Nvidia for me...

Thanks again.

Kevin

---

### Post by jctweb on 2007-10-26
> **Jaydude765 said:**
> I am also getting the mesa driver issue. I have tried most the tips on the 11 pages here so far.

I have a radion X1400 in a dell inspiron 6400.

My XORG.conf:



I have tried commenting out the default and generic devices/screens etc but that cause various problems when logging in (error messages such as cannot find trash can?!)

Here is my grep -i fglrx /var/log/Xorg.0.log:



and the output of fglrxinfo:


Any ideas? I have reinstalled and tried I think everything mentioned here so far. :|

Jason

FYI - use CODE tags around your files - it's more tidy ;)

My first suggestion is to make sure you don't have XGL installed:
```

sudo apt-get remove xserver-xgl

```

---

### Post by jctweb on 2007-10-26
> **kshane said:**
> I appreciate the assist.  I think I have reached the limits of my frustration.  I'm going out in a few hours when the stores open and buying a new Nvidia.  I feel really screwed by ATI.  I spent a pretty penny for my card and now, six months later, it's selling for half what I paid (gee, what a surprise).  

It seems to me that Nvidia users have much less trouble and seem to get good results with low-end cards.  So, Nvidia for me...

Thanks again.

Kevin
Before you spend $$, have you tried the restricted drivers that come with Gutsy?  Sometimes it's easier to move from a configuration you **know** works before moving on.  At least that way you can revert when you need to get work done.

---

### Post by Jaydude765 on 2007-10-26
> **jctweb said:**
> FYI - use CODE tags around your files - it's more tidy ;)

My first suggestion is to make sure you don't have XGL installed:
```

sudo apt-get remove xserver-xgl

```

Yeah sorry was in a rush at the time and didn't for some reason!

I tried to remove that and it stated that it was not installed, however that nvidia-kernel-common or similarly named was automatically installed and not needed... I removed this just in case.

Either way i have the same mesa info showing so no luck.

In regards to the hate ATI comments, I agree. On my desktop at home I bought a nvidia specifically due to the better Linux experience. My laptop however I did not get as much of a choice in the matter!

:confused:

Jason

---

### Post by Jeffrey Magder on 2007-10-26
> [SIZE="4"][COLOR="Red"]WARNING!!![/COLOR][/SIZE]:  I had problems with the restricted drivers manager deleting the symlink for the fglrx.ko module in the volatile directory.  You will only realize this if you do a complete restart of your computer and end up with the white screen of death.  You may want to remove the restricted drivers manager and the restricted packages in addition to all the steps I've given thus far if this happens to you.
I've been searching for an alternative to removing the *restricted driver manager*, but I've had no luck.  Did you ever find another way to prevent the [FONT="Courier New"]/lib/modules/*/volatile/fglrx.ko[/FONT] symlink from being removed across reboots?

It is the removal of the symlink that is causing [FONT="Courier New"]fglrxinfo[/FONT] to return "Mesa".   When keeping the restricted driver manager,  I currently have to goto a console window ([FONT="Courier New"]Ctrl Alt F1[/FONT]) and run: 

[FONT="Courier New"]sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko[/FONT]

every time I reboot.   Then I run:

[FONT="Courier New"]sudo insmod /lib/modules/$(uname -r)/volatile/fglrx.ko[/FONT]

I go back to the X instance ([FONT="Courier New"]Ctrl Alt F7[/FONT]) And restart X ([FONT="Courier New"]Ctrl + Alt + Backspace[/FONT]) and things are fine.  This is however, a huge pain seeing that I can't suspend or hibernate with the current drivers.

---

### Post by jctweb on 2007-10-26
> **Jeffrey Magder said:**
> Did you ever find another way to prevent the [FONT="Courier New"]/lib/modules/*/volatile/fglrx.ko[/FONT] symlink from being removed across reboots?

Yes.  For whatever reason, depmod -a isn't enough.  The next time I booted (and the symlink had been deleted), I ran:
```

sudo depmod -ae

```
Apparently, the -e flag forces the module to resolve the dependencies differently with regards to symlinks.  I haven't had the problem since.

---

### Post by Jeffrey Magder on 2007-10-26
> **jctweb said:**
> Yes.  For whatever reason, depmod -a isn't enough.  The next time I booted (and the symlink had been deleted), I ran:
```

sudo depmod -ae

```
Apparently, the -e flag forces the module to resolve the dependencies differently with regards to symlinks.  I haven't had the problem since.
Hmmm, I'm still having issues.  How did you remove the restricted driver manager?  I'm beginning to think that I removed the wrong package. :P

---

### Post by infine0n on 2007-10-26
ATI Proprietary Linux x86 Display Driver 8.42.3

released today

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by DestroyMicroshaft on 2007-10-26
I have a alternative guide if any of you are interested, its had some success. 


[http://ubuntuforums.org/showthread.php?t=591445]("http://ubuntuforums.org/showthread.php?t=591445")

---

### Post by jctweb on 2007-10-26
> **Jeffrey Magder said:**
> Hmmm, I'm still having issues.  How did you remove the restricted driver manager?  I'm beginning to think that I removed the wrong package. :P

I've had some strange experience with this.  Here's the sequence of events:
[LIST=1]
[*]removed everything related to restricted drivers
[*]did the whole ATI install all over again with depmod -ae
[*]Everything seemed to work - except my wireless card
[*]Tried using ndis wrapper with my 3945abg card - failed miserably
[*]Tried compiling the intel-provided ipw3945 driver - failed miserably
[*]Re-installed the restricted modules
[*]The wireless card suddenly started forgetting it was there - had to insmod everytime I booted :(
[*]Removed the ati drivers and the restricted drivers - back to "vanilla" install
[*]Installed the restricted modules *and* the restricted manager
[*]Disabled the fglrx module in the /etc/default/linux-common..blah blah file
[*]restarted
[*]did the ATI driver install
[*]The restricted manager (for some reason) was OK with me using the newly installed "restricted" driver and left the checkbox enabled 
[*]Everything worked
[/LIST]

I'm not sure if that's an official procedure, but it was a PITA.  If I'm feeling adventurous, I may attempt to compile the ipw3945 again to see if I can use it instead of the gutsy-provided restricted module, but we'll see.

I dunno if this helps you or not?

---

### Post by daradib on 2007-10-26
> **Jeffrey Magder said:**
> I've been searching for an alternative to removing the *restricted driver manager*, but I've had no luck.  Did you ever find another way to prevent the [FONT="Courier New"]/lib/modules/*/volatile/fglrx.ko[/FONT] symlink from being removed across reboots?

It is the removal of the symlink that is causing [FONT="Courier New"]fglrxinfo[/FONT] to return "Mesa".   When keeping the restricted driver manager,  I currently have to goto a console window ([FONT="Courier New"]Ctrl Alt F1[/FONT]) and run: 

[FONT="Courier New"]sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko[/FONT]

every time I reboot.   Then I run:

[FONT="Courier New"]sudo insmod /lib/modules/$(uname -r)/volatile/fglrx.ko[/FONT]

I go back to the X instance ([FONT="Courier New"]Ctrl Alt F7[/FONT]) And restart X ([FONT="Courier New"]Ctrl + Alt + Backspace[/FONT]) and things are fine.  This is however, a huge pain seeing that I can't suspend or hibernate with the current drivers.

If you installed the new driver by generating a deb package, you could try to unblacklist the fglrx module.

Edit these two files:

/etc/default/linux-restricted-modules-common
/etc/modprobe.d/blacklist-restricted

Remove fglrx from the files if it is blacklisted.

---

### Post by jweb on 2007-10-26
> **jctweb said:**
> 

To be totally honest with you, the latest ATI driver is crap if you're on a laptop.  Dual-head support causes memory problems and compiz actually slows down (if you use it) compared to using XGL.  They still haven't nailed down being able to use STANDBY (pretty common laptop activity). And there are issues with firefox scrolling slowly once you manage to get compiz working.  If you're not on a laptop, go ahead and move forward with the install; otherwise stick with the restricted drivers that come with Ubuntu.  I was able to get Compiz working with those drivers in less than 10 minutes.



jctweb,

Your instructions have been a great help.  I finally got Compiz running without XGL.  My goal at the beginning of all of this was to find a way to get an external monitor running (efficiently and to my liking) with my Asus laptop (ATI x1700) - my card isn't supported by the open source radeon driver and with the restricted fglrx driver provided with Gutsy, I couldn't run AIGLX or xrandr with XGL -- and, hence, couldn't get xrandr and Compiz at the same time.  Now I have that.  BUT, I also have the slow scrolling problems and relatively poor window dragging performance.  Also, I haven't rebooted yet (as I have the restricted driver manager package still installed) and I fully anticipate the problems associated with the deletion of the symlink (I run the restricted wireless driver as you do and don't feel like messing with that just yet).

My question is: What is the prospect of improving scrolling and dragging performance?  Why is the performance so bad on laptops only?  I don't care much about suspend, I just want to get my external display working well.

Thanks for your help on all of this... 

JWeb

---

### Post by vibe666 on 2007-10-26
Spydr4590 you are my new hero!

i tried endlessly to get above 1024x768 with my ATI 9800pro and followed lots of different gyuides and barely escaped with a usable system because of them.

then I stumbled across this guide whilst looking for advice on upgrading from fiesty to gutsy and i bookmarked it till i had the other thing done.

my linux knowledge is very poor despite doing europe wide windows server support and even blindly following all your code entries and just cut/pasting everything I now have glorious 1600x1200 res where it has NEVER been before.

you my friend are a 24 carat diamond!

---

### Post by revolutio on 2007-10-26
Wahoo, one more person with the Mesa curse.  Unfortunately I've got Xubuntu and I'm never sure when the material here applies to it and when it doesn't.  Regardless I have tried every solution in this thread and every one linked to from here plus getting a priest to perform an exorcism on my case.

Alas nothing, so here's the data

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

xorg.conf
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

Xorg.0.log
```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x8208a00
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "RADEON 9800 PRO" (Chipset = 0x4e48)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe8000000
(--) fglrx(0): MMIO registers at 0xf8030000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R350
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 1ae  Serial#: 1112683056
(II) fglrx(0): Year: 2005  Week: 50
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) fglrx(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HVFYC04029
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff004c2dae0130325242
(II) fglrx(0):  320f010380291f782aee95a3544c9926
(II) fglrx(0):  0f5054bfef80a94081808140714f0101
(II) fglrx(0):  010101010101483f403062b0324040c0
(II) fglrx(0):  130098321100001e000000fd00384b1e
(II) fglrx(0):  5111000a202020202020000000fc0053
(II) fglrx(0):  796e634d61737465720a2020000000ff
(II) fglrx(0):  00485646594330343032390a202000f8
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 32 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (410, 310) mm
(--) fglrx(0): DPI set to (99, 98)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe8000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 6991
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor

```

Maybe I have missed something extremely simple, maybe I'm terminally screwed I don't know.

EDIT: **IT WORKS!** I just had to go back to the Restricted Drivers Manager and reactivate it.  Victoly!

---

### Post by daradib on 2007-10-26
revolutio-

BTW, you can enable composite in xorg.conf

I didn't see it enabled. If you want to enable it, make your xorg.conf something like this, adding the bold parts.

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
	Load  "dbe"
	Load  "v4l"
EndSection
[B]
Section "ServerFlags"
	Option	"AIGLX" "On"
	Option	"TexturedVideo" "True"
EndSection
[/B]
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

[B]Section "Extensions"
	Option	    "Composite" "1"
EndSection[/B]
```

---

### Post by jctweb on 2007-10-26
> **jweb said:**
> My question is: What is the prospect of improving scrolling and dragging performance?  Why is the performance so bad on laptops only?  I don't care much about suspend, I just want to get my external display working well.

Just to clarify - most of the bugs I've encountered have been in dual-head mode.  That being said, why in the h3ll would ATI pass off a driver without better testing of dual-head?  I mean - this is their hardware, isn't it?  Sigh....

Anyway, someone posted a fix (I think) in the phoronix forums.  I recommend you check that thread out regarding the slow scrolling in firefox.  With regards to the second display - it should work fine as long as you aren't running compiz.

There has been word on the street that the new driver actually does support suspend--but it still behaves the same for me (i.e. crashes the computer).  For the moment, I've switched back to the restricted driver.  I've lost too many hours screwing around with this new driver.

---

### Post by Jaydude765 on 2007-10-27
Well I went back to installing the restricted driver version just to check something and that even gives me the mesa bug.

Maybe I should go back a few versions of ubuntu (the last one I had) when this used to work for me lol.. 

Chances are now with playing around with so many different things I've probably introduced other unforseen problems.. :|

Jason

---

### Post by Jaydude765 on 2007-10-27
Ok, I just re-installed Ubuntu and when through the instructions in the first post again and it is working fine. I know this was extreme but I had only just installed Ubuntu the other day for the first time in a while.

I think my problems may have been caused by me using the original restricted drivers first then trying to update to the newest version, and possibly some mistakes early on. Either way it's working for me now.

Thanks guys,

Jason

---

### Post by Blond on 2007-10-27
I just installed gutsy (upgraded from feisty), and now I'm trying to get my resolution to 1280*1024. But I can't get it above 1024*768 :confused:.
I tried your instructions but when I run the command "bash..." I get the following output:

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8..................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

So I can't start with the next step, because the directory is removed automatically.

Please help

---

### Post by d3k4y on 2007-10-27
If anyone is still having problems, I think I mat have the answer.  I have a X1600 pro running in 32 bit gutsy install and ran into the same problems with Mesa and Direct rendering.  Here's what I did:

1) Open "Synaptic Package Manager" and search for "fglrx"

2) Remove any packages that have "fglrx" in the NAME of the package.  You will get results with "fglrx" in the description that come up.  Do NOT remove these unless "fglrx" is also in the name of the package.

3) Restart your machine.  It will most likely start up in Safe Graphics Mode.  When the box comes up and tells you its in Safe Graphics mode, just click "Continue", don't fix it right now, we will have to work in low res for 2 minutes.

4) Now you have to do the whole process all over following the directions at: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)


Note: This is what I did for Gutsy, if you are running feisty, it may work too, just follow the link in step 4, but choose feisty instructons link on the right of the page.  Hope this is clear and helps some ppl out there.

---

### Post by willow147 on 2007-10-27
Been following this thread an acting on some very useful info (I'm a complete Linux novice so haven't a clue what the commands have been doing).

I'm now at the point where I get

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6958 Release

$ glxinfo | grep direct
direct rendering: Yes
```

To me this is what people are trying to get, HOWEVER, when I try to turn on the visual effects all I can then see is the bacground and nothing else. Hitting escape brings things back again. Also, if I go to look at the screensavers all I see is a blank screen (apart from the bar at the top with the 'Leave Fullscreen' button on it).


```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection

Section "ServerFlags"

Option "AIGLX" "off"

EndSection

```


Any ideas.

---

### Post by johnbhoy on 2007-10-27
I also seem slightly stuck.  

fglrxinfo gives:

jp@jp-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


xorg as follows:

I am concerned that i dont seem to have many modules loaded. Please bear with me as i am a relatively new linux newb

 xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AQ [Radeon 9600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 AQ [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

 xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AQ [Radeon 9600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 AQ [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

---

### Post by Nikos.Alexandris on 2007-10-27
Which driver do you use? The one's that Gutsy provides?


You could try with ATI's new driver **8.42.3**

( **Install ATI 8.42.3 driver ( [B][COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]** ), that is done with: sudo ./ati-driver-installer-8.42.3-x86.x86_64.run[/B] )

[I]And then edit your xorg.conf:
[/I]
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen **[COLOR="Red"]0[/COLOR]**      "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
        [COLOR="Red"][B]Load  "v4l"
        Load  "dbe"[/B][/COLOR]
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS" **[COLOR="Red"]"true"[/COLOR]**
EndSection

[B][COLOR="Red"]Section "DRI"
         Mode   0666
EndSection[/COLOR][/B]

Section "Extensions"
	Option	    "Composite" "**[COLOR="Red"]1[/COLOR]**"
EndSection

---

### Post by snerd on 2007-10-28
Call me lucky or stupid, but I just downloaded the 8.42.3 from ATI's site, ran sudo bash and the auto-installer came up and installed them lickity-split. Now my Helios ss works normal again!  :mrgreen:

---

### Post by kshane on 2007-10-28
> **snerd said:**
> Call me lucky or stupid, but I just downloaded the 8.42.3 from ATI's site, ran sudo bash and the auto-installer came up and installed them lickity-split. Now my Helios ss works normal again!  :mrgreen:

Not to sound like a complete idiot (though I feel that way), what exactly is the command line you ran?

Thanks!

Kevin

---

### Post by snerd on 2007-10-28
Just terminal to the file location and run   sh ./ati-driver-installer-8.42.3.run to get it to start.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html)

I originally ran

sudo bash ati-driver-installer-8.41.7-x86.x86_64.run --buildpkg Ubuntu/gutsy

but I don't think it's needed with the newer driver, dated the 27th.

I'm pretty new to this myself, so try at your own risk!

---

### Post by Drillbit on 2007-10-28
> **snerd said:**
> Just terminal to the file location and run   sh ./ati-driver-installer-8.42.3.run to get it to start.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html)

I originally ran

sudo bash ati-driver-installer-8.41.7-x86.x86_64.run --buildpkg Ubuntu/gutsy

but I don't think it's needed with the newer driver, dated the 27th.

I'm pretty new to this myself, so try at your own risk!

I keep getting

sh: Can't open ./ati-driver-installer-8.42.3.run

Anyone know how to fix this?

---

### Post by CheeseEatingBulldog on 2007-10-28
> **Drillbit said:**
> I keep getting

sh: Can't open ./ati-driver-installer-8.42.3.run

Anyone know how to fix this?

You have to add read and execute rights to the file for example:

sudo chmod 777 /path/file.sh

and then try executing it.

---

### Post by johnbhoy on 2007-10-28
well after numerous attempts at trying to do it manually. i followed the gutsy guide to the automatic install just by using restricted manager and it worked first time!!!  As per the sticky at the top of the page.

Still cannot seem to get the blimin thing in cloned mode though and i kinda really need that.  Will keep perservering. Might leave it for a wee while now though.

---

### Post by khristian on 2007-10-28
Another user of the XPress 1100 card. I kept getting the Mesa driver even after re-enabling the fglrx driver from the Restricted Manager. Turned out that X server was always falling back to some other free driver (ati, apm, ark).
I then removed all of the xserver-xorg-video- packages, and suddenly the X server liked the fglrx driver again!
Weird thing is, when I installed the fglrx driver via the packages generated by the ATI installer, I couldn' t start a X session because some .sh script was missing in /etc/ati (don' t remember which one now, I couldn' t reproduce the error and the ~/.xsession-errors was overwritten).
If anyone that got the new driver could post the scripts in that folder, maybe I could get it to work.
EDIT: [COLOR="Red"][SIZE="7"]**_*IT WORKS!*_**[/SIZE][/COLOR]
:lolflag:
After removing those stupid drivers that came with the xserver-xorg-video-all package, installation through the ATI installer (not with the generated packages) worked, finally.
Compiz is running well, and the only problem is the already-mentioned slow scrolling in Firefox. The maker of the tutorial should add this possibility to his post, I think.

---

### Post by soulwind on 2007-10-28
Here is my problem:
when I use

```
fglrxinfo
```

I get

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6747 (8.40.4)
```

but...

```
glxinfo | grep direct
```

shows

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

direct rendering should be "yes", right? how am I gonna do that??

---

### Post by farewell2RMS on 2007-10-28
> **geogrip.e said:**
> this installation notes working for ATI HD2400PRO?
Is this  the best drivers for using compiz or beryl in Gutsy (upgrade from Feisty)
I just followed this installation guide, and it gives me my proper resolution, but it has caused new problems, i.e. - when scrolling in firefox it is now horribly slow in rendering the image...(using an HD2400 Pro)

---

### Post by scorpiusmaximus on 2007-10-29
You are the man! I have been struggling with this for 6 weeks solid, about to get divorced because of it. Fixed my driver and 3D rendering like a charm. I can not begin to tell you what a relief this was.
AGP Radeon X1550. I have 2 monitors I have not tried to configure yet.
TNX!!!

---

### Post by StooJ on 2007-10-29
I've gotten to this stage...


> Step 5.Type in the teminal LS to get a list of the new files created. Now type in this to the terminal then hit enter
Code:

```
sudo dpkg -i fglrx-kernel-source_8.41.7-1*.deb
sudo dpkg -i xorg-driver-fglrx_8.41.7-1*.deb
sudo dpkg -i fglrx amdcccle_8.41.7-1*.deb
```

Note: You don't have to do sudo dpkg -i fglrx amdcccle_8.41.7-1*.deb (this install the ATI AMD Catalyst Control Panel which is worthless, but gives you pretty information about your video card) If you're on 64-bit Ubuntu it will complain about libraries. Just go ahead and type

Unfortunately I didn't read ahead. I have run the command "sudo dpkg -i fglrx amdcccle_8.41.7-1*.deb" but I *definitely* don't want the Catalyst Control Centre. How can I reverse/undo the dpkg command?

Will "sudo dpkg -r fglrx-amdcccle" work?

Thanks

---

### Post by Kronos2785 on 2007-10-29
This worked a treat!!! Just took me a while to realise I needed to change the version numbers in some of the comands! :P

Now all I need to do is get it to extend my desktop and I'll be back with the full functionality I had under feisty

---

### Post by Toadmund on 2007-10-29
Anyone have an answer to this?
```
toad@toad-desktop:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)

```
Envy now has the 8.42 ati driver, but even Envy could not get my driver going again.

I've been at this for a week, tried everything, but no success.
I think I gunked up some stuff, I need a way out, other than a fourth re-install.

Thanks.

PS, my card is an ATI xpress 200g

---

### Post by Toadmund on 2007-10-29
OK, so I ran:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It reconfigured my xorg.conf.
I ran Envy again, uninstalled ATI drivers, then installed and 

BEHOLD!
```
toad@toad-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release

```
I wonder how long until it uninstalls itself again?

---

### Post by booyip on 2007-10-30
Yep, this worked great for me too on Gutsy.  Thanks to Spydr for working it out.  

However, this might be useful for fellow newbs (if not already mentioned somewhere in this thread) I couldn't get Compiz working correctly on my ATI Radeon 9550 until I did this too (first post)....
[http://ubuntuforums.org/showthread.php?t=582207&page=2](http://ubuntuforums.org/showthread.php?t=582207&page=2)

:-)

---

### Post by bagodonut1 on 2007-10-30
My first experience with Linux and have read so many good things about gusty 7.10, wanted to give it a try. I love the fact that there is so many folks willing to offer help.
Anyway, at step 4 I receive an error that Ubuntu/gusty is not recognizes
I have an ATI Raedon 9250 pro 256 mb and am using ati-driver-installer.8.28.8.run
Am I using the correct driver. Can anyone clue me in on what I am missing. I have been all over these boards in the past 2 weeks and have tried many different guides, but nothing has worked.

I really would love to get this up and running. If anyone could help, it would be greatly appreciated. Thanks
:confused:

---

### Post by kshane on 2007-10-30
I went through all this rigamrole to install the new ATI drivers and found this How-to.  It worked great!

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html)

So very easy, not a ton of terminal work.

**Actually, this command line is basically all you need to know.**  Just answer the questions in the installer and you're done!

```

gksudo sh ./ati-driver-installer-8.42.3.run

```

Hope this helps someone...

Kevin

---

### Post by kshane on 2007-10-30
Just an aside:

Everyone keeps saying not to install the ATI Control Center because it does nothing.  ***Not true!***  If you are a gamer (World of Padman, Tremulous, Quake/OpenArena, etc.) you will notice that the games will darken considerably, to the point that they are really not playable. 

If you go into the ATI Control Center and go to the Color section, by increasing the levels to about 2.00, you'll be able to see great in the games!  You may need to adjust the levels a little differently for your particular system, but it DOES work!

---

### Post by Toadmund on 2007-10-30
> **Toadmund said:**
> 
I wonder how long until it uninstalls itself again?

Answer: Until I reboot again! :confused::mad:

(seems my xorg.conf changes itself, then I reset it with the 'phigh' command, I re-enable it, then it works again, why does my xorg keep changing? Did I forget to save it?-Nope, that's not it)

At least I can get it going by checking the 'enabled' box in the restricted driver GUI, if anybody knows why it unchecks itself, I'd sure would like to here it.

Thanks.

---

### Post by kportertx on 2007-10-31
> **booyip said:**
> Yep, this worked great for me too on Gutsy.  Thanks to Spydr for working it out.  

However, this might be useful for fellow newbs (if not already mentioned somewhere in this thread) I couldn't get Compiz working correctly on my ATI Radeon 9550 until I did this too (first post)....
[http://ubuntuforums.org/showthread.php?t=582207&page=2](http://ubuntuforums.org/showthread.php?t=582207&page=2)

:-)

Yea I been meaning to post that this is what I wound up doing to correct my previous posted problem. :).  
[COLOR="Red"]But now I have a new problem[/COLOR]

if I set composite to enabled in xorg.conf totem no longer displays movies instead it is a blank screen with sound

[PHP]glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
###If I set the option composite to enable this will show as yes.
tail /etc/X11/xorg.conf
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection
###Right now its disabled on purpose.
[/PHP]

---

### Post by Snub_Fighter on 2007-10-31
Well I'm stuck.. I installed the newest ati drivers for my x1700 mobility and I've played games for the most part besides having them freeze 10-30 mins later.. But non of the compiz stuff works. Any ideas where I should go from here? I've modified the xorg.conf according to the suggestions in this topic but non of the modifications really had much of an effect.. I'm at work so I can't really get ya the log files... Just need some suggestions, debating if i should try the newest xorg drivers to see if those will give me any results...

---

### Post by sdowney717 on 2007-10-31
[http://ubuntuforums.org/showthread.php?t=589637](http://ubuntuforums.org/showthread.php?t=589637)
try it 
I dont know whether restricted driver should be checked or not. When I did this driver install manually, it was unchecked and working, but when I just looked again it was checked.

---

### Post by frojnd on 2007-10-31
Hello there. I get problems with step 7 or 8 where I have to type in this:

CODE: sudo aticonfig --initial --force

I get: 
```
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-4

```

CODE 2: sudo aticonfig --overlay-type=Xv
```
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-4
```

And even if I try: sudo -i and repeat those two commands I won't be able to login. After reboot I can see login screen but it won't log in. Thanx for helping.

---

### Post by Zhomama on 2007-10-31
Millions and millions of thank you's.  I finally am able to update my ATI driver.  I have a X1600Pro and I can finally update it.  The ATI site is kind of vague on how to remove some stuff..  And the install doesn't work THAT great.  Thanks again.  I've been looking for something like this for months.  Is there anyway to make a program that will automatically do this?

---

### Post by ldo2104 on 2007-10-31
Hello All,
Really new to Ubuntu, I have no internect, cdroms, and video is not working like it should.  I've read numerous thread to try to fix this, but I'm not able to move forward.  
Running:
Ubuntu 7.10 (upgrade) dual boot
Dell E510
ATI Rad X300

Thanks for the help,
Rich

---

### Post by daradib on 2007-11-01
The restricted driver in the restricted driver manager should be checked after the new driver is installed.

---

### Post by Snub_Fighter on 2007-11-01
so to get my x1700 mobility to work with compiz and still register correctly and not as mesa I had to first install the xorg-driver-fglrx and restarted. then i ran the automated installer for the ati driver 40.4 and then the newest ati driver right after that, next i went to [http://combatwombat.7doves.com/index.php/2007/10/31/p377]("http://combatwombat.7doves.com/index.php/2007/10/31/p377")

I added fglrx to the compiz whitelist at /usr/bin/compiz and then used the following in my xorg.conf from the above site.

> Section "Module"
Load "glx"
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
Option "KernelModuleParm" "agplock=0"
Option "UseInternalAGPGART" "no"
Option "EnablePrivateBackZ" "no"
Option "DisableGLXRootClipping" "true"
Option "AddARGBGLXVisuals" "true"
Option "AllowGLXWithComposite" "true"
Option "mtrr" "on"
BusID "PCI:1:0:0" <-- you have to figure out what busid your card is using.
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

I can't say that this will work for anyone else, but it might be worth trying if your having issues.

---

### Post by StuipedandUgly on 2007-11-02
i followed the instructions and i keep getting the message:
glxinfo | grep direct
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

can someone help me?

---

### Post by murkin on 2007-11-02
snub_fighter, your sample xorg file worked perfectly for me. so, between the instructions in post 1 and your help, compiz is back up and running along with the latest ati drivers. everything seems to be working well. Thanks!

---

### Post by GordonFrohm on 2007-11-02
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package module-assistant

---

### Post by GordonFrohm on 2007-11-02
Only at Step 3 and already stuck.
I had no idea this would be SO ******* FRUSTRATING!! :mad:

---

### Post by GordonFrohm on 2007-11-03
I'm using 7.10 and I have a Radeon X300 by the way

---

### Post by TedGarvin on 2007-11-03
> **Spydr4590 said:**
> 
Note:I don't recommend using ati-driver-installer-8.42.3-x86.x86_64.run You can't even compile this on 64-bit Ubuntu without some major editing and the thing that gets me is ATI knew about this before their public release. I'm not sure how well this works on 32-bit Ubuntu. I'm not providing any support till next driver release 8.43. Feel free to continue discussing.

 But the driver set before this one only supports 4 HD cards and the one before that is the closed source driver.  Will this work with the closed source driver?

---

### Post by supercommode on 2007-11-03
How do I download the driver from the ati website if all i have to work with is command prompt. My computer doesnt boot to a desktop... It has driver problems (I'm gusseing) and will only show a fashing cursor in the upper left corner with a black screen. I have to use Ctrl+Alt+F5 and log in as root to do anything. This is my fisrt time using linux and I have had too many troubles.... any help would be appreciated.

thanks!

---

### Post by userfriendly on 2007-11-03
the tutorial in the OP worked perfectly fine for me on a fresh and updated gutsy install with a Radeon HD 2600 XT.

thank you, Spydr4590. :)

---

### Post by Treeckcold57 on 2007-11-03
> **karbo said:**
> Thanks for this! I am on a HP Compaq nx9420 with a ATI Radeon Mobility X1600 and this guide fixed my problems. Works like a charm!

Hey, I have same model of your HP nx9420 and ATI X1600 Mobiltiy 256MB! But I havent trying on this guide yet. Because I just installed Ubuntu 7.10.

---

### Post by userfriendly on 2007-11-04
> **userfriendly said:**
> the tutorial in the OP worked perfectly fine for me on a fresh and updated gutsy install with a Radeon HD 2600 XT.

thank you, Spydr4590. :)

alright, now i'm stuck. i'm trying the same thing, only with an ubuntu studio (with realtime kernel). i've changed the generic headers to the rt headers, but the > sudo m-a build,install fglrx-kernelstill fails, the protocol mentions something about incompatible pointer type.

so... any hints how to get the driver working in ubuntu studio with the realtime kernel?

---

### Post by GordonFrohm on 2007-11-04
this tutorial doesn't work at all...
every time i do what it tells me it can't find any of the packages and when I download them manually, the dependencies in most cases aren't 'satisfactible'...
pissing me off...

---

### Post by userfriendly on 2007-11-04
> **GordonFrohm said:**
> this tutorial doesn't work at all...
every time i do what it tells me it can't find any of the packages and when I download them manually, the dependencies in most cases aren't 'satisfactible'...
pissing me off...

it worked perfectly for me with the generic kernel. you did enable the multiverse & restricted repos, right?

---

### Post by fredclaus on 2007-11-04
Well once a newbie always etc etc
these are the results of following the " Dummies" 

Can anyone sort this out?

fred@fred-laptop:~/Desktop/Ubuntu$ ls
arch                     installer_creation_policy  preun_km.sh
ati-installer.sh         lokixml.sh                 README.distro
ATI_LICENSE.TXT          map_xname.sh               setup.data
ati-packager-helper.sh   packages                   verify_install.sh
ati-packager-wrapper.sh  post_drv.sh                x430
automatic-install.exp    post_km.sh                 x430_64a
check.sh                 postun_cp.sh               x680
common                   postun_drv.sh              x680_64a
component_config.sh      postun_km.sh               x690
config_install.sh        postun_rn.sh               x690_64a
copy_uninstall_files.sh  pre_cp.sh                  x710
create_log.sh            pre_drv.sh                 x710_64a
default_policy.sh        pre_km.sh
fglrx-uninstall.sh       preun_drv.sh
fred@fred-laptop:~/Desktop/Ubuntu$ sudo ./ati-installer.sh 8.42.3 --buildpkg Ubuntu/gutsy
[sudo] password for fred:
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.kB6827/debian/control.template ]; then \
                cat /tmp/fglrx.kB6827/debian/control.template > /tmp/fglrx.kB6827/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.kB6827/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.kB6827/debian/driver.$i > \
              /tmp/fglrx.kB6827/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.kB6827/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.kB6827/debian/10fglrx.template > /tmp/fglrx.kB6827/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.kB6827/debian/fglrx.default ]; then \
          mv /tmp/fglrx.kB6827/debian/fglrx.default /tmp/fglrx.kB6827/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.kB6827/debian/control.template ]; then \
                cat /tmp/fglrx.kB6827/debian/control.template > /tmp/fglrx.kB6827/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.kB6827/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.kB6827/debian/driver.$i > \
              /tmp/fglrx.kB6827/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.kB6827/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.kB6827/debian/10fglrx.template > /tmp/fglrx.kB6827/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.kB6827/debian/fglrx.default ]; then \
          mv /tmp/fglrx.kB6827/debian/fglrx.default /tmp/fglrx.kB6827/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.kB6827/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.kB6827/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
fred@fred-laptop:~/Desktop/Ubuntu$ cd /usr/X11R6/lib/modules/dri
fred@fred-laptop:/usr/X11R6/lib/modules/dri$ ls
fglrx_dri.so    mach64_dri.so  radeon_dri.so  trident_dri.so
i810_dri.so     mga_dri.so     s3v_dri.so     unichrome_dri.so
i915_dri.so     r128_dri.so    savage_dri.so
i915tex_dri.so  r200_dri.so    sis_dri.so
i965_dri.so     r300_dri.so    tdfx_dri.so
fred@fred-laptop:/usr/X11R6/lib/modules/dri$ 

:confused::confused:

---

### Post by alize on 2007-11-04
has anyone figured out what to do when you get this after typing in the command fglrxinfo...

```
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!
```

I have a radeon 9000 card

---

### Post by Yellow Pasque on 2007-11-04
> **StuipedandUgly said:**
> i followed the instructions and i keep getting the message:
glxinfo | grep direct
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

can someone help me?

Use this:
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```

---

### Post by Yellow Pasque on 2007-11-04
> **alize said:**
> has anyone figured out what to do when you get this after typing in the command fglrxinfo...

```
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!
```

I have a radeon 9000 card

Sounds like you need to add "glx" to the files section of your xorg.conf. Please post your  /etc/X11/xorg.conf file

---

### Post by alize on 2007-11-04
> **Temüjin said:**
> Sounds like you need to add "glx" to the files section of your xorg.conf. Please post your  /etc/X11/xorg.conf file

here is my xorg.conf file...

```
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Sony"
	Modelname	"Sony SDM-X72 (Digital)"
	Horizsync	28.0-65.0
	Vertrefresh	57.0-63.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"800x600@60"	"1024x768@60"	"640x480@60"	"1280x960@60"	"1280x1024@60"	"1400x1050@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by alize on 2007-11-04
and now i don't know what happened but whenever i type in the command "fglrxinfo" my system kind of restarts, it goes to the login screen...???

any ideas why?

---

### Post by Yellow Pasque on 2007-11-04
> **alize said:**
> and now i don't know what happened but whenever i type in the command "fglrxinfo" my system kind of restarts, it goes to the login screen...???

any ideas why?

Your xorg.conf is very fuxored. You need to make sure you've enabled the fglrx driver in the restricted driver manager (Click System -> Administration -> Restricted Driver Manager and check the box. If it complains that it's not available, make sure the restricted section is enabled in Software Sources). This uses the older version available in the repository. 

If you want a newer version, you need to download that file from ATI/AMD (for i386: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)). After you've done the above step and enabled the fglrx driver by checking the box, navigate to the directory where you saved the ati-installer that you downloaded and run it:
```
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```
Go ahead and do a normal/express install. When that's done, run:
```
aticonfig --initial -f
```

Then, post back your new xorg.conf.

---

### Post by Drenhead on 2007-11-05
When I tried this method, I get the following error when I run fglrxinfo:

Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Here is my xorg.conf:

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL 1800FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
        Monitor         "DELL 1800FP"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection


Thanks for all help.

> **Temüjin said:**
> Your xorg.conf is very fuxored. You need to make sure you've enabled the fglrx driver in the restricted driver manager (Click System -> Administration -> Restricted Driver Manager and check the box. If it complains that it's not available, make sure the restricted section is enabled in Software Sources). This uses the older version available in the repository. 

If you want a newer version, you need to download that file from ATI/AMD (for i386: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)). After you've done the above step and enabled the fglrx driver by checking the box, navigate to the directory where you saved the ati-installer that you downloaded and run it:
```
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```
Go ahead and do a normal/express install. When that's done, run:
```
aticonfig --initial -f
```

Then, post back your new xorg.conf.

---

### Post by kidguayas on 2007-11-05
**I got to step 4 with not problem but after I run this line at the ends says:**
[B]dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.e16911
**Do you know how to fix this problem?  Thanks**

---

### Post by killatoffa on 2007-11-05
It doesn't work for  my ATI Radeon HD 2600 pro!! all i want is to have compiz fusion up and running on my dual monitors (dvi)!! I tried using the Restricted Drivers tool and downloading and installing the driver from the AMD web site. the catalyst control center allows me to have my two monitors working but with alot of tearing!! and the best part is, i can't run compiz fusion!!!

can anyone out there tell me how to make this thing running to full capacity?

Specs:

Mobo: M2N-E
Chipset: NVIDIA nForce 570 Ultra
CPU: AMD Athlon 64 X2 5200+ Dual-Core Socket AM2, 2.6GHz, 1MB x2 L2 Cache
Ram: 4 GB DDR2 800MHz
HDD's internal: 2x 36 GB Raptors, 160 GB IDE, 320 GB SATA
HDD's external: 2x 500 GB SATA, 500 GB IDE
Video: ATI Radeon HD 2600 Pro
Sound: Creative Sound Blaster Audigy 2 ZS
PSU: Antec Truepower Trio 550W
Chassis: Antec P182
Beauty & Beast

---

### Post by singlewc on 2007-11-05
Well, mine worked great yesteday when I installed 7.10.

Today, its broken, and I am stuck in VESA mode, looking like trash.

I did the install, it told me about the ATI proprietary drivers, so I said sure, go ahead and install them.

Played all night. Installed apps, rebooted lots of times, went to bed pretty happy.

Booted this morning, the desktop is wrong, the sounds are back on, and I am in 800X600 mode.

The proprietary driver was unchecked in the driver box, so I checked it, rebooted, and am stuck forever in Vesa mode.

I am not all that well versed in linux. How do I get back what I had last night, and heck, how do I get back what it gave me after I first installed?

Not off to a great start. Hoping to find a solution real soon now.

Thanks,

John

---

### Post by Yellow Pasque on 2007-11-05
> **Drenhead said:**
> When I tried this method, I get the following error when I run fglrxinfo:

Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Thanks for all help.

Try adding the following to your xorg.conf:
```
Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by avargas04 on 2007-11-05
> **Temüjin said:**
> Try adding the following to your xorg.conf:
```
Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "DRI"
Mode 0666
EndSection
```

I am new to (K)Ubuntu - though not necessarily new to linux - and I have been having such a hard time installing the new ATI 8.42.3 drivers.  I love the fact that the community is so large and helpful (that's my main reason for giving kubuntu a try over FC again), and I have been trying to search for solutions to my problem, but to no avail.  

I was having that same problem with fglrxinfo not functioning, but this helped (Thanks Temujin!).  

It's so frustrating though: everytime I specify the fglrx driver in xorg.conf, X fails to restart saying that there were no screens found.  And fglrxinfo keeps saying that my OpenGL vendor and renderer is Mesa! :mad:

This is my xorg.conf file for anyone interested:

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
	Option		"Composite"	"1"
EndSection
Section "Module"
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "vbe"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "ServerFlags"
	Option "AIGLX" "on"
EndSection

```

---

### Post by Yellow Pasque on 2007-11-05
avargas04, your hardware doesn't appear to be supported by the latest release of the ATI driver (9500 series is the oldest product listed). You need to download a different driver: [http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

---

### Post by avargas04 on 2007-11-05
> **Temüjin said:**
> avargas04, your hardware doesn't appear to be supported by the latest release of the ATI driver (9500 series is the oldest product listed). You need to download a different driver: [http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

I considered that, but what's interesting is that when I look in Synaptic for fglrx, the description for xorg-driver-fglrx states that Mobility Radeon 9000 IGP (what I have) is officially supported by 8.42.3-1!  I attached a snapshot of the Synaptic Window saying so.

I was trying to install 8.28 before I found out the 8.42 was released about a week ago, and that was not even progressing through the installation.  Luckily I found 8.42, and it installed just fine (the error that I was encountering while installing 8.28 was rumored to have been fixed in 8.42 - lo and behold it was true!).

I really want to figure this out (I am hoping to transition to full-time linux from XP), but it has been incredibly frustrating.

---

### Post by unclesamslair on 2007-11-05
I cannot find my driver on the website listed. I have ati radeon xpress 1150

---

### Post by killatoffa on 2007-11-06
okay, so i guess no one out there will help a brother geek in training....i had to RTFM to actually figure sum things out, well not the manual exactly but a little researching thats all! so i got my two screens to work very nicely without no tearing! and when i tried to full crank the desktop effects it says "The composite extension is not available".........i had to be at work early today so i couldn't finish off the project i set for myself........but i'm doing alot of reading and i think i found sum answers!:)
if i get compiz fusion running to full blown effects, i'll tell u what i did to get my ATI Radeon 2600 Pro working with compiz fusion!! stay tuned!!


Specs:

Mobo: M2N-E
Chipset: NVIDIA nForce 570 Ultra
CPU: AMD Athlon 64 X2 5200+ Dual-Core Socket AM2, 2.6GHz, 1MB x2 L2 Cache
Ram: 4 GB DDR2 800MHz
HDD's internal: 2x 36 GB Raptors, 160 GB IDE, 320 GB SATA
HDD's external: 2x 500 GB SATA, 500 GB IDE
Video: ATI Radeon HD 2600 Pro
Sound: Creative Sound Blaster Audigy 2 ZS
PSU: Antec Truepower Trio 550W
Chassis: Antec P182
Beauty & Beast

---

### Post by james.worsnop on 2007-11-06
ok, i just installed these drivers and now firefox and compiz are running a lot slower than what they were.

when i do fglrxinfo i get this

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release

which looks right

but when i do glxinfo i get 



direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
are there 
OpenGL renderer string: Mesa GLX Indirect

---

### Post by Yellow Pasque on 2007-11-06
For those having difficulties, see my working xorg.conf post in the ATI driver sticky (post #93).
EDIT: [Direct Link]("http://ubuntuforums.org/showpost.php?p=3720763&postcount=93")

---

### Post by mastercho on 2007-11-07
followed the guide to the point where, i used the 8.28.8 release as thats the one ATI reckon i need. only problem is i get

```

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

```

fixed this and re ran the install and now get.

```

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.2.0

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install

```

anyone able to help with this? im using feisty 7.04 with all current updates. using onboard video at the moment, which is intel 815 crud.

---

### Post by stuccio on 2007-11-07
hey all,

I follow the tutorial up to the install part where i get this error:

<code>./ati-installer.sh: 165: Syntax error: Bad substitution<\code>

I have a ati radeon 9250 and I'm using kubuntu feisty.

thx for any info, I've digged this thread and no one seem to be having this trouble.

thx

stucci

---

### Post by stuccio on 2007-11-07
except the guy above ....

---

### Post by alize on 2007-11-08
> **Temüjin said:**
> Your xorg.conf is very fuxored. You need to make sure you've enabled the fglrx driver in the restricted driver manager (Click System -> Administration -> Restricted Driver Manager and check the box. If it complains that it's not available, make sure the restricted section is enabled in Software Sources). This uses the older version available in the repository. 

If you want a newer version, you need to download that file from ATI/AMD (for i386: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)). After you've done the above step and enabled the fglrx driver by checking the box, navigate to the directory where you saved the ati-installer that you downloaded and run it:
```
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```
Go ahead and do a normal/express install. When that's done, run:
```
aticonfig --initial -f
```

Then, post back your new xorg.conf.

Thanks, the thing I don't understand is the Restricted Driver Manager, I keep reading about checking and unchecking certain things, But there has always been only ONE (1) item in my Restricted Drivers Manager, and that is...
Atheros Hardware Access Layer (HAL)   and it is checked. There is nothing else that shows up. Do i need to do something somewhere else in order for restricted drivers to appear?
in my Software Sources I DO have my Proprietary Drivers for Devices (restricted) checked on

---

### Post by bgKoh on 2007-11-08
Hello

I use dual monitor and I followed this instruction exactly.
But I got this."Comparing resolution (2560x1024) to maximum 3D texture size(2048): Failed

Is that impossible to use dual monitor with ATI(8.42.3) ?

---

### Post by dcarpenter on 2007-11-10
I am currently stuck in Mesa hell.

I followed this guide step by step, installing the 8.42 driver for my 9800xt card in Gutsy 7.10.  The restricted driver manager has the driver IN USE and the box is checked, however fglrxinfo returns:

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

My xorg.conf is as follows:

```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

grep -i fglrx /var/log/Xorg.0.log returns:

```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x8206718
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "on"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "RADEON 9800 XT" (Chipset = 0x4e4a)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xff720000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262144 kB
(II) fglrx(0): VESA VBE OEM: ATI R360
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R360
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: e5  Serial#: 1146302775
(II) fglrx(0): Year: 2004  Week: 23
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) fglrx(0): blueX: 0.143 blueY: 0.102   whiteX: 0.318 whiteY: 0.339
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HMEX504419
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff004c2de50037315344
(II) fglrx(0):  170e010380221b782a6f8ba25a4d9424
(II) fglrx(0):  1a5156bfef0081800101010101010101
(II) fglrx(0):  010101010101302a009851002a403070
(II) fglrx(0):  1300520e1100001e000000fd00384b1e
(II) fglrx(0):  510e000a202020202020000000fc0053
(II) fglrx(0):  796e634d61737465720a2020000000ff
(II) fglrx(0):  00484d45583530343431390a202000f1
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  4 power states available:
(II) fglrx(0):   1. 412/365MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   2. 311/365MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   3. 412/365MHz @ 50Hz [overclocked, enable load balancing, overdrive]
(II) fglrx(0):   4. 419/365MHz @ 50Hz [overclocked, enable load balancing, overdrive]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 29 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (340, 270) mm
(--) fglrx(0): DPI set to (95, 96)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7f7d000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.42.3
(II) fglrx(0):     Date: Oct 19 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [pci] find AGP GART
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7f7d000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
```

The catalyst control center works and properly detects my hardware, but Information > OpenGL shows my provider and renderer as mesa.  Does anyone know how to fix this?  I have tried numerous troubleshooting steps as well as 2 clean installs of ubuntu to no avail.

---

### Post by zazery on 2007-11-10
I followed the steps in the first post of this thread exactly and have a few problems.

**Problems**
1. When I type "fglrxinfo" it crashes X and returns me to KDM.
2. Screen flickers (looks like 2 triangles) when logging in.
3. Uses Mesa GLX Indirect.

**Goals**
1. Install proprietary ATI driver with 3D acceleration.
2. Setup dual monitors

**Information**
Hardware: 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
Kubuntu 7.10 (upgraded from Fiesty)

1. What version of the driver are you installing?
    ati-driver-installer-8.42.3-x86.x86_64.run

2. What do the (pertinent) sections of the xorg.conf look like?
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "BusType" "PCI"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	"Composite" "disable"
EndSection

```
3. What errors are you getting in /var/log/Xorg.0.log?
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux sunspot 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 10 17:39:36 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1458,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1458,24d2 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1458,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1458,24d2 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1458,24d2 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1458,a002 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4152 card 174b,7c29 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4172 card 174b,7c28 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 10d9,0531 card 2078,0540 rev 25 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 1102,0002 card 1102,8027 rev 08 class 04,01,00 hdr 80
(II) PCI: 02:02:1: chip 1102,7002 card 1102,0020 rev 08 class 09,80,00 hdr 80
(II) PCI: 02:08:0: chip 8086,1050 card 1458,3013 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xefffffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AR [Radeon 9600] rev 0, Mem @ 0xd0000000/28, 0xf9000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) rev 0, Mem @ 0xe0000000/28, 0xf9010000/16
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfb001000 - 0xfb001fff (0x1000) MX[B]
	[1] -1	0	0xfb000000 - 0xfb0000ff (0x100) MX[B]
	[2] -1	0	0xfc002000 - 0xfc0020ff (0x100) MX[B]
	[3] -1	0	0xfc001000 - 0xfc0011ff (0x200) MX[B]
	[4] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[5] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xf9010000 - 0xf901ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf9000000 - 0xf900ffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfb001000 - 0xfb001fff (0x1000) MX[B]
	[1] -1	0	0xfb000000 - 0xfb0000ff (0x100) MX[B]
	[2] -1	0	0xfc002000 - 0xfc0020ff (0x100) MX[B]
	[3] -1	0	0xfc001000 - 0xfc0011ff (0x200) MX[B]
	[4] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[5] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xf9010000 - 0xf901ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf9000000 - 0xf900ffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfb001000 - 0xfb001fff (0x1000) MX[B]
	[5] -1	0	0xfb000000 - 0xfb0000ff (0x100) MX[B]
	[6] -1	0	0xfc002000 - 0xfc0020ff (0x100) MX[B]
	[7] -1	0	0xfc001000 - 0xfc0011ff (0x200) MX[B]
	[8] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[9] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xf9010000 - 0xf901ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf9000000 - 0xf900ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[32] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4152) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb001000 - 0xfb001fff (0x1000) MX[B]
	[5] -1	0	0xfb000000 - 0xfb0000ff (0x100) MX[B]
	[6] -1	0	0xfc002000 - 0xfc0020ff (0x100) MX[B]
	[7] -1	0	0xfc001000 - 0xfc0011ff (0x200) MX[B]
	[8] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[9] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xf9010000 - 0xf901ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf9000000 - 0xf900ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[32] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8208950
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb001000 - 0xfb001fff (0x1000) MX[B]
	[5] -1	0	0xfb000000 - 0xfb0000ff (0x100) MX[B]
	[6] -1	0	0xfc002000 - 0xfc0020ff (0x100) MX[B]
	[7] -1	0	0xfc001000 - 0xfc0011ff (0x200) MX[B]
	[8] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[9] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xf9010000 - 0xf901ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf9000000 - 0xf900ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "BusType" "PCI"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI RADEON 9600 Series" (Chipset = 0x4152)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x7c29)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xf9000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(**) fglrx(0): Forced into PCI mode
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: GSM  Model: 4ae8  Serial#: 216896
(II) fglrx(0): Year: 2006  Week: 2
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.647 redY: 0.346   greenX: 0.292 greenY: 0.602
(II) fglrx(0): blueX: 0.149 blueY: 0.130   whiteX: 0.313 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: L1970HR
(II) fglrx(0): Monitor name: 
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff001e6de84a404f0300
(II) fglrx(0): 	021001036a261e78eaec54a5584a9a26
(II) fglrx(0): 	215054a56b80314f454f614f81800101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300782d1100001e000000fd00384b1e
(II) fglrx(0): 	530e000a202020202020000000fc004c
(II) fglrx(0): 	3139373048520a2020202020000000fc
(II) fglrx(0): 	000a2020202020202020202020200048
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: CRT on secondary DAC [crt2]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: GSM  Model: 4ae8  Serial#: 216892
(II) fglrx(0): Year: 2006  Week: 2
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.647 redY: 0.346   greenX: 0.292 greenY: 0.602
(II) fglrx(0): blueX: 0.149 blueY: 0.130   whiteX: 0.313 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: L1970HR
(II) fglrx(0): Monitor name: 
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff001e6de84a3c4f0300
(II) fglrx(0): 	021001036a261e78eaec54a5584a9a26
(II) fglrx(0): 	215054a56b80314f454f614f81800101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300782d1100001e000000fd00384b1e
(II) fglrx(0): 	530e000a202020202020000000fc004c
(II) fglrx(0): 	3139373048520a2020202020000000fc
(II) fglrx(0): 	000a202020202020202020202020004c
(II) fglrx(0): End of Display2 EDID data --------------------
(WW) fglrx(0): More than one displays are connected,so clone mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Secondary Controller - CRT on secondary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 500/297MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 31 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) fglrx(0): Total of 31 modes found for secondary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(EE) fglrx(0): [pcie] Failed to gather memory of size 262144Kb for PCIe. Error (-1014)
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf9000000 - 0xf900ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfb001000 - 0xfb001fff (0x1000) MX[B]
	[7] -1	0	0xfb000000 - 0xfb0000ff (0x100) MX[B]
	[8] -1	0	0xfc002000 - 0xfc0020ff (0x100) MX[B]
	[9] -1	0	0xfc001000 - 0xfc0011ff (0x200) MX[B]
	[10] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[11] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xf9010000 - 0xf901ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xf9000000 - 0xf900ffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[29] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[36] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[38] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[39] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) stylus: Twinview = horizontal
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) cursor: Twinview = horizontal
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(**) eraser: Twinview = horizontal
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Graphire2 tablet speed=9600 maxX=10206 maxY=7422 maxZ=511 resX=2032 resY=2032 suppress=2 tilt=enabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=10206 bottom Y=7422
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=10206 bottom Y=7422
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=10206 bottom Y=7422
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9

```

4. Are you trying to use Compiz ? If so, did you make sure you were running the ATI driver first?
    I installed Compiz and then realized my driver was not configured.

5. Is fglrx whitelisted in /etc/xdg/compiz/compiz-manager ?
    Yes.

6. Does compiz give you errors when you enable it at the command line?
     Haven't tried.

---

### Post by Roocky on 2007-11-11
Hi All,

Hope someone out there can help me , I am a new to Ubuntu and cant get my screen res correct I have a wide screen 19" monitor and the res should be 1440x900 on a ATI Sapphire R9550 256mb video card.

I have tried for days now and cannot fix this problem , I should add that this is my first try at Ubuntu from being a Windows XP user.

Any help would be great thanks Dean

---

### Post by dcarpenter on 2007-11-11
I have found the solution to my problem.  For whatever reason, the kernel that ships with gutsy has a bug preventing agp from being detected with intel 875P chipsets.  I followed these steps

[HTML]https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684/comments/48[/HTML]

and fglrxinfo now properly displays ATI and direct rendering is now working.

Hopefully they fix this in the next kernel update.

---

### Post by 8daysaweek.co.uk on 2007-11-11
> **karbo said:**
> Thanks for this! I am on a HP Compaq nx9420 with a ATI Radeon Mobility X1600 and this guide fixed my problems. Works like a charm!
I have the same (HP Compaq nx9420 with a ATI Radeon Mobility X1600).  It's dual-booting (Gutsy/XP) and displaying fine, but in Gutsy I can't get the full resolution 1680x1050.
When you say "this guide fixed my problems", does that mean that after following the guide you can get 1680x1050?

BFN,

---

### Post by Speedoo on 2007-11-11
Is anyone else using ATI Radeon XPress 1150?  ATI doesn't list this driver on their site, even though my Gateway MT6459 is only a month old!

---

### Post by petzworld999 on 2007-11-11
I have an ATI Radon Xpress 200M and when enter this into the terminal:
```

glxinfo | grep direct

```

I get this:
```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Any idea why I am getting this? Other people on this thread got this problem and I found no solution. Any help would be appreciated.

---

### Post by mmoore99 on 2007-11-11
> **stuccio said:**
> hey all,

I follow the tutorial up to the install part where i get this error:

<code>./ati-installer.sh: 165: Syntax error: Bad substitution<\code>

I have a ati radeon 9250 and I'm using kubuntu feisty.

thx for any info, I've digged this thread and no one seem to be having this trouble.

thx

stucci

I am experiencing the same problem.  I am running Ubuntu 7.10 (Gutsy) and am attempting to install for Radeon 9200.  Please advise as to whether there has been any resolution for this issue.

Thanks.

---

### Post by singlewc on 2007-11-11
> **mmoore99 said:**
> I am experiencing the same problem.  I am running Ubuntu 7.10 (Gutsy) and am attempting to install for Radeon 9200.  Please advise as to whether there has been any resolution for this issue.

Thanks.

Don't know how to unsub from this thread, so I figure to post, and check the unsubscribe button.

John

---

### Post by 2rB on 2007-11-11
ignore this post - have not found a solution to my problem, but I missed a warning.
Have to start from the beginning, investigate my way trough the steps once more.

---

### Post by LRT on 2007-11-11
avargas04,

did you ever get the drivers for the ati mobility radeon 9000 igp installed??? i have the same video card as you. 

lrt

---

### Post by LRT on 2007-11-11
how-to is smooth until... 

# bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/Gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/Gutsy
Requested package is not supported.
Removing temporary directory: fglrx-install

i have an ati mobility radeon 9000 igp. i noticed others with the same issue, but failed to come up with real answers. could anyone out there be of any assistance???

lrt

---

### Post by LRT on 2007-11-11
doesn't look like this driver (ati-driver-installer-8.28.8.run) is built for ubuntu/gutsy

 bash ./ati-driver-installer-8.28.8.run --listpkg
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
List of generatable packages:

Package Maintainer(s): Aric Cyr <acyr@gmail.com>
Status: Verified
Debian Packages:
        Debian/woody
        Debian/oldstable
        Debian/sarge
        Debian/stable
        Debian/sid
        Debian/unstable
        Debian/etch
        Debian/testing
        Debian/experimental

Package Maintainer(s): Niko Mirthes <nmirthes@gmail.com>
Status: Verified
Fedora Packages:
        Fedora/FC3
        Fedora/FC4
        Fedora/FC5
        Fedora/FC6
        Fedora/RHEL3
        Fedora/RHEL4

Package Maintainer(s): Arnaud Patard <apatard@mandriva.com>
Status: Verified
Mandriva Packages:
        Mandriva/2006
        Mandriva/2007

Package Maintainer(s): ATI
Status: Verified
RedHat Packages:
        RedHat/RHEL3_64a
        RedHat/RHEL3
        RedHat/RHEL4_64a
        RedHat/RHEL4

Package Maintainer(s): Stefan Dirsch <sdirsch@suse.de>
Status: Verified
SuSE Packages:
        SuSE/NLD9-AMD64
        SuSE/SLES9-AMD64
        SuSE/SUSE91-AMD64
        SuSE/NLD9-IA32
        SuSE/SLES9-IA32
        SuSE/SUSE91-IA32
        SuSE/SUSE100-AMD64
        SuSE/SUSE92-AMD64
        SuSE/SUSE93-AMD64
        SuSE/SUSE100-IA32
        SuSE/SUSE92-IA32
        SuSE/SUSE93-IA32
        SuSE/SLED10-AMD64
        SuSE/SLES10-AMD64
        SuSE/SUSE101-AMD64
        SuSE/SLED10-IA32
        SuSE/SLES10-IA32
        SuSE/SUSE101-IA32
        SuSE/SUSE102-AMD64
        SuSE/SUSE102-IA32

Package Maintainer(s): Aric Cyr <acyr@gmail.com>
Status: Verified
Ubuntu Packages:
        Ubuntu/warty
        Ubuntu/4.10
        Ubuntu/hoary
        Ubuntu/5.04
        Ubuntu/breezy
        Ubuntu/5.10
        Ubuntu/dapper
        Ubuntu/6.06
        Ubuntu/edgy
        Ubuntu/6.10

For example, to build a Debian Etch package, run the following:
% ./ati-driver-installer-<version>-<architecture>.run --buildpkg Debian/etch

Removing temporary directory: fglrx-install


would i have issues if i run this package anyway????

---

### Post by skychris on 2007-11-12
Hi All,

I went through this post back and forth several time and finally managed to set the good driver at the right place... I think. but I still have some glitches,
when I run "fglrxinfo", I get this

***************
chris@chris-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release
***************
which is the correct card installed with the latest driver
but when I run "glxinfo", I get this, amongst other lines

************************
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
************************

wich one is correct, what's the difference between them?

I still have some troubles running some applications, like google earth that I'm quite sure uses some advanced 3d features, and when I lauch them, it stalls my session and brings me back to the login page.

thanks all....

Chris

---

### Post by 8daysaweek.co.uk on 2007-11-12
> **8daysaweek.co.uk said:**
> I have the same (HP Compaq nx9420 with a ATI Radeon Mobility X1600).  It's dual-booting (Gutsy/XP) and displaying fine, but in Gutsy I can't get the full resolution 1680x1050.
When you say "this guide fixed my problems", does that mean that after following the guide you can get 1680x1050?

BFN,

Just thought I'd report back to say that I got the desired resolution.  It was as simple as changing the line in xorg.conf that read > Modes		"1280x1024" to read > Modes		"1680x1050" "1280x1024" (I had already checked that the refresh rate was correct in my Windows boot).

:)

---

### Post by Gnu32 on 2007-11-12
Ah finally, a guide that knows what it's doing.

Unfortunately, before finding this guide I've tried other guides and have done so much to the point of forgetting what I've done to my system, and now I've run into a very bizzare situation.

Following the guide was all fine and dandy up until the point of trying out fglrxinfo:
"error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory"

Same for glxinfo:
"error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory"

I tried glxgears and second life, 
"error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory"

D: What have I accidentally removed/screwed up? The ATI driver (latest one, 8.42.3) installed just fine through the steps on this guide. I'm sure it's something i've done in previous guides but i just can't backtrack :X

---

### Post by Maube-Not on 2007-11-12
Hey. Great guide, but I'm having a problem. I'm on a brand new install of Feisty. 

When i try to install the driver (bash ./ati-driver-installerblablabla)

i just get this:

root@Maybe-not-desktop23:/home/maybe-not/Desktop# bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/feisty
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


Anyone know what this Syntax error is, and how i fix it? Sorry, but i have no idea what syntax means, I'm not a native English speaker.

Peace.

---

### Post by Gnu32 on 2007-11-12
To follow up on my original post, I investigated the generated packages and possibly came up with a solution.

I found there was a libGL.so and a libGL.so.1.2, but everything was looking for libGL.so.1. What I did was create a symbolic link of *libGL.so.1.2* to *libGL.so.1* and everything now seems to work fine:

```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```

I picked 1.2 because it was the one installed by the generated FGLRX package. Hopefully I haven't done anything stupid/dangerous here.

---

### Post by koprioni on 2007-11-12
~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf

~$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

~$ glxinfo | grep direct
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

what's wrong here...?

-----------------------
after this: sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
i get:
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by Yellow Pasque on 2007-11-13
koprioni, you need to reinstall the driver. What video card are you using and what does your xorg.conf look like?

If you're using a Radeon 9500 or later (including X and HD2k series), grab the latest ATI driver, 8.42.3 from ATI's site and put it in your home folder. Make sure the permissions are set properly by right-clicking the file and selecting properties. Under the permissions tab, make sure you allow the executing of the file as a program (or just do a chmod 755  ati-driver-installer-8.42.3-x86.x86_64.run in terminal).

If you've previously installed a proprietary ATI driver from the ATI site and installed it directly:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh

``` or use GDebi to remove distro packages that you've built if you installed that way.

Now, remove the fglrx driver:
```
sudo apt-get remove xorg-driver-fglrx
```

Restart your computer. If X starts up and takes you to the graphical login, go to the terminal/shell login. If your computer hangs on reboot, try Ctrl+Alt+F1 to kill X.

Now,
```
sudo apt-get install xorg-driver-fglrx
cd ~/
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```
Install directly/express, and when it's done
```
sudo update-pciids
sudo aticonfig --initial -f
```

Now look at your /etc/X11/xorg.conf with and see my guide [here](http://ubuntuforums.org/showpost.php?p=3720763&postcount=93). Use nano to edit it from the shell. Reboot.

Post back.

---

### Post by Yellow Pasque on 2007-11-13
> **Maube-Not said:**
> Hey. Great guide, but I'm having a problem. I'm on a brand new install of Feisty. 

When i try to install the driver (bash ./ati-driver-installerblablabla)
Peace.

Instead of doing buildpkg, just install directly
```
sudo sh ./ati-driverBLABLA
```

Now what does it say? Also, why are you trying to install 8.28? Do you have an old graphics card?

---

### Post by pasokon on 2007-11-13
Also koprioni's question and Gnu32's questions about ```
ibGL.so.1: cannot open shared object file: No such file or directory
``` can best be answered with this guide:

[HTML]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/HTML] 

If not this thread has some juicy bits.
[HTML]http://www.phoronix.com/forums/showthread.php?t=5963[/HTML] 

Finally, when all is said and done with the LIBGL error you may find, like me that glx rendering is not direct and that the glx renders under Mesa still. 

If that is the case I suggest this site in Portuguese. I don't understand portuguese myself but I was able to change the renderer to ATI when I did as the guide suggested and removed *XGL* like this:

```
sudo apt-get remove xserver-xgl
```

Good luck! 

I can't say I am am expert because while I temporarily fixed my problems and got 

yes direct rendering when I ran *glxinfo* now, while the renderer string is from ATI the rendering has reverted back to indirect and says 

```
LIBGL_INDIRECT_RENDERING is set
```

If someone knows what this means and what I can do about it please let me know!

Thanks

---

### Post by pasokon on 2007-11-13
Sorry the code for the last bit is wrong. This is the message I get when I enter 
```
glxinfo | grep rendering
``` :

```
LIBGL_ALWAYS_INDIRECT is set
```

Thanks in advance!:)

---

### Post by philc on 2007-11-13
Just wanted to say thanks for this guide. Following these instructions I was able to install the necessary ATI drivers and now set my screen resolution to 1280x800

There were a couple of errors from following the instructions exactly to the letter, but I'm sure if I read through all 22 pages of this thread I'd find the answer (for example I get the same error as Gnu32 above with fglrxinfo). But as it doesn't seem to effect things (and I'm not using anything 3D at the moment) I'm generally happy.

Thanks again.

---

### Post by koprioni on 2007-11-13
Thanks Temüjin
This is what i get now:

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6958 Release

~$ glxinfo | grep rendering
direct rendering: Yes

~$ glxinfo | grep direct
direct rendering: Yes
(i don't know if the last 2 are the same :lolflag:)

which i assume is right.
Thanks again

---

### Post by gonzomir on 2007-11-13
> **voivoi said:**
> 
bash ./ati driver file name*.run --buildpkg Ubuntu/feisty or --buildpkg Ubuntu/gutsy (Depending on your version)


this means to replace the string ati driver file name*.run with the actual name of the file you downloaded.
You have to execute the following:

```
sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

> **snerd said:**
> 
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 175: dpkg-architecture: not found
Error: unsupported architecture: 


The file dpkg-architecture is missing from your system and the script can't build the packages. It is part of the dpkg-dev package, you can search for it in synaptic or just execute

```
sudo apt-get install dpkg-dev
```

OOOPPPPSSS... I didn't notice this thread has so many pages, I was looking only at the firt one, this must be answered already...

---

### Post by chiefbearclaw on 2007-11-13
Okay this is what happened to me to anyone who is interested. (I am aware that it was suggested to not use this guide for the new driver.. however.. please know that even the suggested methods from the ati wiki, envy, 'the ubuntu way', along with others haven't worked correctly 100% either. I don't think anything works 100% yet for ati / linux and my particular card. The card even acted weird within XP Pro at first. I simply wanted to try this method to see what it would do. I am no expert and do not know how to fix everything but am totally open to suggestions and experimentation. I know it is a heavily posted subject and very frustrating to many on both sides of the ATI / Linux issue. Please don't consider this post another cry for help. I simply made this post in hopes more could be understood about what the hell is going on. I.. like many... have installed / reinstalled ...plus... I'm a distro junkie and love trying things.. so far.. LinuxMint + Envy has been the only thing that feels like it is on the right track. Fresh installations are certainly not a problem. Posted below was a fresh install of LinuxMint XFCE Beta 008 ...built off of gutsy). I have literally been tinkering with different linux distros along with attempts to make my gfx card work since Feb of 07 when I have a spare moment of boredom. I think I have learned a lot but I think I speak for many when I say... I'm even more confused. It seems people who want their card for gaming purposes can't have Beryl or vise versa. Or people who want both Beryl and Gaming performance have to sacrifice something else.. and this alone makes this whole issue very disturbing, confusing and exhaustive. Some just want their screen savers to work but doing so makes their normal desktop effects behave ultra slow. I simply want the fastest UI possible.. e.g. reduced resources.. no Beryl.. etc. I just want the card to work when gaming at the proper FPS. In particular for the game(s) Enemy Territory / ET:QW / Americas Army). I have tried Enemy Territory upon a fresh install of Mint and Envy with an average FPS of 60 or so. Where in XP Pro the FPS is a steady 300. This doesn't seem correct to me... but if it is.. ..the longer I'll remain in XP Pro for gaming which is all I use XP Pro for... and that is annoying to me. I'd rather have a dual boot of several linux distros that cater to my needs. In addition, with XP pro I spend most of my time making sure I have a critical update / anti-virus update / malware update / spyware update.. then I do even playing a game and enjoying myself. With linux I can worry less about all the security related issues but spend an equal amount of time trying to 'make something work'. It will be nice when I have a computer / OS, that I can actually get some work done on.. and play a game when I have some precious free time.
_______

First I did exactly the steps on the first page of this post (substituting the newer 8.42.3 driver... which is NOT recommended.. hence I had to try it :P).

I went to [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) and downloaded the correct file for my card which is the ATI Radeon X1600 (4xAGP) w/512MB ram. The driver I downloaded to my Desktop is:

ati-driver-installer-8.42.3-x86.x86_64.run

Next, Following the steps from page 1 of this thread as follows:

```
sudo apt-get update
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper \
debconf libstdc++5 linux-headers-generic
```

Then...

```
bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

Then...

```
sudo dpkg -i fglrx-kernel-source_8.42.3-1*.deb
```

```
sudo dpkg -i xorg-driver-fglrx_8.42.3-1*.deb
```

```
sudo dpkg -i fglrx-amdcccle_8.42.3-1*.deb
```

Next...
```
sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb
```

And then...
```
gksu mousepad /etc/default/linux-restricted-modules-common
```
in which I make DISABLED_MODULES="" look like this:

DISABLED_MODULES="fglrx"

I save and exit as instructed.

It is now suggested to reboot before proceeding. Also, bookmark this page so that you can come back to it once you reboot.

(Reboot)

Now I open a terminal and...
```
sudo -i
```

```
sudo aticonfig --initial --force
```

Followed by...
```
sudo aticonfig --overlay-type=Xv
```

I now reboot again.

(Reboot)

Now I open a terminal and type:

```
fglrxinfo
```

Which returns:
_______
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

Which of course...
```
glxinfo | grep direct
```

Returns:
_______
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

______

For those that want my xorg.conf:
```

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Any suggestions?

---

### Post by aoanla on 2007-11-13
> **chiefbearclaw said:**
> 

Any suggestions?

Can you post the contents of /var/log/Xorg.0.log? The reason why the fglrx module is not loading should be made clear by this...

---

### Post by chiefbearclaw on 2007-11-13
> Can you post the contents of /var/log/Xorg.0.log? The reason why the fglrx module is not loading should be made clear by this...

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux sigillvm 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 13 09:54:02 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2530 card 0000,0000 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2532 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 8086,4d44 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 8086,4d44 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 8086,4d44 rev 04 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 8086,4d44 rev 04 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71c2 card 1002,030b rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e2 card 1002,030a rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 1033,0035 card 8086,4d44 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:01:1: chip 1033,0035 card 8086,4d44 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:01:2: chip 1033,00e0 card 8086,4d44 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:08:0: chip 8086,2449 card 8086,3013 rev 03 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbe900000 - 0xde9fffff (0x20100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xff900000 - 0xff9fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xdea00000 - 0xdeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xc0000000/28, 0xff8f0000/16, I/O @ 0xc800/8, BIOS @ 0xff8c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xff8e0000/16
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
	[0] -1	0	0xff9fc000 - 0xff9fcfff (0x1000) MX[B]
	[1] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[2] -1	0	0xff9fe000 - 0xff9fefff (0x1000) MX[B]
	[3] -1	0	0xff9fd000 - 0xff9fdfff (0x1000) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B](B)
	[6] -1	0	0xff8c0000 - 0xff8dffff (0x20000) MX[B](B)
	[7] -1	0	0xff8f0000 - 0xff8fffff (0x10000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[11] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[12] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[13] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff9fc000 - 0xff9fcfff (0x1000) MX[B]
	[1] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[2] -1	0	0xff9fe000 - 0xff9fefff (0x1000) MX[B]
	[3] -1	0	0xff9fd000 - 0xff9fdfff (0x1000) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B](B)
	[6] -1	0	0xff8c0000 - 0xff8dffff (0x20000) MX[B](B)
	[7] -1	0	0xff8f0000 - 0xff8fffff (0x10000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[11] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[12] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[13] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
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
	[4] -1	0	0xff9fc000 - 0xff9fcfff (0x1000) MX[B]
	[5] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[6] -1	0	0xff9fe000 - 0xff9fefff (0x1000) MX[B]
	[7] -1	0	0xff9fd000 - 0xff9fdfff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B](B)
	[10] -1	0	0xff8c0000 - 0xff8dffff (0x20000) MX[B](B)
	[11] -1	0	0xff8f0000 - 0xff8fffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71C2) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff9fc000 - 0xff9fcfff (0x1000) MX[B]
	[5] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[6] -1	0	0xff9fe000 - 0xff9fefff (0x1000) MX[B]
	[7] -1	0	0xff9fd000 - 0xff9fdfff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B](B)
	[10] -1	0	0xff8c0000 - 0xff8dffff (0x20000) MX[B](B)
	[11] -1	0	0xff8f0000 - 0xff8fffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8206a30
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff9fc000 - 0xff9fcfff (0x1000) MX[B]
	[5] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[6] -1	0	0xff9fe000 - 0xff9fefff (0x1000) MX[B]
	[7] -1	0	0xff9fd000 - 0xff9fdfff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B](B)
	[10] -1	0	0xff8c0000 - 0xff8dffff (0x20000) MX[B](B)
	[11] -1	0	0xff8f0000 - 0xff8fffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[19] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[22] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "Radeon X1600 Series" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x030b)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xff8f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PHL  Model: e007  Serial#: 71078400
(II) fglrx(0): Year: 2002  Week: 16
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) fglrx(0): Gamma: 2.90
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) fglrx(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): #5: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 202.5 MHz   Image Size:  360 x 270 mm
(II) fglrx(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) fglrx(0): Serial No:  CX  71078400
(II) fglrx(0): Monitor name: PHILIPS 109B2
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 97 kHz, PixClock max 210 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00410c07e000923c04
(II) fglrx(0): 	100c010368241bbee8bbb8a352469824
(II) fglrx(0): 	0f484cadef803159455961598199a94f
(II) fglrx(0): 	d140010101011a4f403062b0324040c0
(II) fglrx(0): 	1300680e1100001e000000ff00204358
(II) fglrx(0): 	20203731303738343030000000fc0050
(II) fglrx(0): 	48494c495053203130394232000000fd
(II) fglrx(0): 	0032a01e6115000a2020202020200047
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 57 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1440 (pitch 0)
(**) fglrx(0): *Mode "1920x1440": 234.0 MHz (scaled from 0.0 MHz), 90.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1440"  234.00  1920 2048 2256 2600  1440 1441 1444 1500 +hsync
(**) fglrx(0): *Mode "1920x1200": 193.2 MHz (scaled from 0.0 MHz), 74.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 +hsync
(**) fglrx(0): *Mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync
(**) fglrx(0):  Default mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0): *Mode "1800x1440": 219.6 MHz (scaled from 0.0 MHz), 89.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1800x1440"  219.56  1800 1928 2128 2456  1440 1441 1444 1490 +hsync
(**) fglrx(0): *Mode "1792x1344": 204.8 MHz (scaled from 0.0 MHz), 83.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1792x1344"  204.75  1792 1920 2120 2448  1344 1345 1348 1394 +hsync
(**) fglrx(0): *Mode "1600x1200": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 169.2 MHz (scaled from 0.0 MHz), 97.0 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1280x1024"  169.20  1280 1376 1512 1744  1024 1025 1028 1078 +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907 +hsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"  113.30  1024 1096 1208 1392  768 769 772 814 +hsync
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"  100.18  1024 1088 1200 1376  768 769 772 809 +hsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"   83.94  800 856 944 1088  600 601 604 643 +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"   72.85  640 680 752 864  480 481 484 527 +hsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (360, 270) mm
(--) fglrx(0): DPI set to (135, 135)
(--) fglrx(0): Virtual size is 1920x1440 (pitch 1920)
(**) fglrx(0): *Mode "1920x1440": 234.0 MHz (scaled from 0.0 MHz), 90.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1440"  234.00  1920 2048 2256 2600  1440 1441 1444 1500 +hsync
(**) fglrx(0): *Mode "1920x1200": 193.2 MHz (scaled from 0.0 MHz), 74.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 +hsync
(**) fglrx(0): *Mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync
(**) fglrx(0):  Default mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0): *Mode "1800x1440": 219.6 MHz (scaled from 0.0 MHz), 89.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1800x1440"  219.56  1800 1928 2128 2456  1440 1441 1444 1490 +hsync
(**) fglrx(0): *Mode "1792x1344": 204.8 MHz (scaled from 0.0 MHz), 83.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1792x1344"  204.75  1792 1920 2120 2448  1344 1345 1348 1394 +hsync
(**) fglrx(0): *Mode "1600x1200": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 169.2 MHz (scaled from 0.0 MHz), 97.0 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1280x1024"  169.20  1280 1376 1512 1744  1024 1025 1028 1078 +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907 +hsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"  113.30  1024 1096 1208 1392  768 769 772 814 +hsync
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"  100.18  1024 1088 1200 1376  768 769 772 809 +hsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"   83.94  800 856 944 1088  600 601 604 643 +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"   72.85  640 680 752 864  480 481 484 527 +hsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xff8f0000 - 0xff8fffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xff9fc000 - 0xff9fcfff (0x1000) MX[B]
	[7] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[8] -1	0	0xff9fe000 - 0xff9fefff (0x1000) MX[B]
	[9] -1	0	0xff9fd000 - 0xff9fdfff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B](B)
	[12] -1	0	0xff8c0000 - 0xff8dffff (0x20000) MX[B](B)
	[13] -1	0	0xff8f0000 - 0xff8fffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[22] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[24] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[25] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xc0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1440) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 6751
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by Yellow Pasque on 2007-11-14
Hi chief, looking at your output, it looks like X is confused as to the bus ID of your video card. Run:
```
sudo update-pciids
lspci | grep "VGA compatible"
```
You should get an output that looks like:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
```
You'll need to edit your xorg.conf and add the following line to your "Device" section, using the three numbers from the line above: For example, mine looks like:
```
Busid		"PCI:1:5:0"
```

Reboot.


If that doesn't work:
We'll start from the beginning. First, download the ati installer to your home dir (~/). Make sure permissions are set properly:
```
chmod 755 ~/ati-driver-installer-8.42.3-x86.x86_64.run
```

Now, create a new text file in gedit and copy the xorg file pasted at the end of this post in there. Save it as /etc/X11/xorg.new
**REMEMBER TO COMPLETE THE BusID LINE IN THE DEVICE SECTION (I started it for you, just fill in the three numbers from the lspci command)**

- Now, sudo gedit /etc/default/linux-restricted-modules-common file and remove fglrx from the disabled modules. 
- Look in your software sources (System ->Administration-> Software Sources) and make sure proprietary/restricted modules are checked. 
- Look in the Restricted Driver Manager and make sure the fglrx is allowed/enabled.

Logout and log back in using a failsafe terminal session(change the "session" with the icon in the lower-left of the login screen).

Now:
```
sudo dpkg -P fglrx-kernel-source
sudo dpkg -P xorg-driver-fglrx
sudo dpkg -P fglrx-amdcccle
sudo apt-get remove xorg-driver-fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
sudo cp /etc/X11/xorg.new /etc/X11/xorg.conf
sudo apt-get install xorg-driver-fglrx
cd ~/
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```
Select the express/regular install (don't build packages)

Reboot. Pray. Look at fglrxinfo and glxinfo | grep "direct" to make sure no Mesa

xorg.conf file
**REMEMBER TO COMPLETE THE BusID LINE IN THE DEVICE SECTION (I started it for you, just fill in the three numbers from the lspci command)**
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"fglrx"
	Load		"dbe"
	Load		"extmod"
	Load		"fbdevhw"
	Load		"glx"
	Load		"record"
	Load		"freetype"
	Load		"type1"
	Load		"dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[0]"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Busid       "PCI : : "                          #COMPLETE THIS LINE
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"on"
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection
```

---

### Post by chiefbearclaw on 2007-11-14
Right on..  I'll try to work on this tonight when I get home from work. Thanks for the reply Temüjin! :)

---

### Post by Yellow Pasque on 2007-11-14
You're welcome, but I'm afraid the package names in the dpkg -P commands might be incorrect. If those commands complain, you may need to run "sudo aptitude" and do a search for fglrx packages. Under the Package menu select Purge for all 3 you built.
Sorry if that's a brute force solution, but it's the best I have at the moment. I'll search around and see if I can't find the package names for you.

(Hopefully, the first part of my post will get you fixed up and you won't have to go through all that).

---

### Post by chiefbearclaw on 2007-11-15
Temüjin,

Okay first of all thanks again for your help but unfortunately that did not work either.. I did exactly as you instructed.. not forgetting to edit the Busid in accordance to the one that was outputted as:

```
$ lspci | grep "VGA compatible"
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
```

I tried using exactly as it is above.. then I tried with just 1:00:0 and again with 1:0:0. I did as many possible variations after my first attempts at your intructions.

After coming to the final step to your suggestions.. being:

```
sudo dpkg -P fglrx-kernel-source
sudo dpkg -P xorg-driver-fglrx
sudo dpkg -P fglrx-amdcccle
sudo apt-get remove xorg-driver-fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
sudo cp /etc/X11/xorg.new /etc/X11/xorg.conf
sudo apt-get install xorg-driver-fglrx
cd ~/
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```

After rebooting at this point with my fingers crossed... the Display Server kept jumping resolutions and looked really ugly and restarted 6 times which it then stated it would wait two minutes before trying again. I chose ok and it seemed ok for about 10 seconds and it proceeded to flicker again... jumping resolutions with artifacts and garbage on the screen which then returned me to a tty1 text login. At this point I had no choice but to:

```
sudo cp /etc/X11/xorg.old /etc/X11/xorg.conf
```

and reboot.

...now here I am again :D

(Sorry for the delay on progress... my job has been kicking my butt)

On a side note... since I share partitions with windows and have most of my data there it will be very easy for me to reinstall the linux OS and we can work fresh. If you would like I will try just plain Ubuntu 7.10 if you think it will help you. Also in addition the first final of LinuxMint Xfce should be released soon and I'd like to try it so I may just wait until it is released before going any further. Also since Mint comes with Envy.. from what I've gathered in #linuxmint.com on SpotChat... along with some forum updates there will be a newer Envy included in the final as well. I am excited about that. :)
_______
chiefbearclaw gives Temüjin a sack of chocolate covered roasted coffee beans with a sprig of linux mint :lol:

---

### Post by chiefbearclaw on 2007-11-15
Okay, I got pissed and just reinstalled LinuxMint XFCE 008 Beta. I got the screen to load by typing:
```
startx
``` (since at tty1 from the get go after many Display Server restarts).

I then made the session 'Failsafe Terminal' (for just this session) and once it loaded I typed:
```
sudo apt-get update
```

```
sudo apt-get install envy
``` (there is a newer version now)

```
envy
```

I then followed envy's instructions (Install ATI Driver) and said y (yes) to everything..  allowed it to make my xorg.conf... and also allowed it to reboot my computer.

I now type my user name as pass and was shocked at how fast everything loaded. My desktop was up faster than a prom dress hitting the floor. I open a terminal and type:
```
fglrxinfo
``` and behold... 

it returns ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6958 Release
```

I immediately started to panic.

I now type:
```
glxgears
```

It returning with:
```
15637 frames in 5.0 seconds = 3127.322 FPS
15502 frames in 5.0 seconds = 3099.545 FPS
15459 frames in 5.0 seconds = 3091.667 FPS
15817 frames in 5.0 seconds = 3163.304 FPS
15719 frames in 5.0 seconds = 3143.645 FPS
15501 frames in 5.0 seconds = 3100.075 FPS
15772 frames in 5.0 seconds = 3154.196 FPS
15698 frames in 5.0 seconds = 3139.403 FPS
15536 frames in 5.0 seconds = 3107.115 FPS
```

(For an average of 625.028488889 per second)

The ATI Catalyst Control Center works as well, allowing me to choose 3D and adjust what Anti-Aliasing I want, along with Anisotropic Filtering along with Vertical Refresh in the (more settings) area.

Compositor also works too! However... when moving windows around it stutters and is slow.. but the transparency stuff works for me now as well. I was never concerned with getting this to work and do not care. Turning off the compositor (which is what I did) makes moving the windows smooth as silk. It just doesn't have effects and transparencies and stuff. If anyone would like to look at any logs of any type (as I don't know of all the places to look) in hopes it might help them troubleshoot / fix their own problems.. just let me know. I will try some of my games a little later and see how they run. Bye for now!

---

### Post by davidkahn on 2007-11-16
There are now 23 pages of posing on this topic.  So please accept my apologies if my question has been  answered.  I actually have aiglx running and visual effects working, and only need to learn how to eliminate one manual step each time the computer reboots (highlighted in red below).  Here's what I learned:[LIST=1]
[*]The site [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) has a good description of installing the latest ATI driver 8.42.3.  The same site has a Feisty installation guide which I haven't tried.
[*]If you are running 64-bit, make sure that you follow the procedure of the section                  "If installing on Ubuntu x64...", which is discussed near the end of the web page.

It was a little unclear, but after downloading and extracting fglrx-8.42-ubuntu+debian-2.tar.bz2, you have to copy the tar file's "packages" directory over the "packages" directory that is created by the first step where you use bash to extract  the driver installer rather than immediately building the .deb packages.
[*]The step:[INDENT]sudo dpkg -i xorg-driver-fglrx_8.42.3-1*.deb \
fglrx-kernel-source_8.42.3-1*.deb \
fglrx-amdcccle_8.42.3-1*.deb

ignores one of the .deb packages that was created following the 64-bit procedure in Note 2 above.  The package is:
 "xorg-driver-fglrx-dev_8.42.3-1_amd64.deb"
I installed it with no ill effect, and it appears likely to be mandatory.
[/INDENT]
[*]My PC was going the the white screen whenever the Visual Effects we set to "Normal" or "Extra", and likewise when executed "compiz --replace".  This was fixed by:[LIST=1]
[*] editing the option in the section ServerFlags of /etc/X11/xorg.conf to:
Option        "AIGLX" "on"
which it clearly has to be.
[*]Also, _and this is critical_,  you must unload the  the fglx driver that gets loaded each time the machine boots with the new driver that you just created.  This is accomplished by:
sudo rmmod fglrx
sudo insmod /lib/modules/$(uname -r)/misc/fglrx.ko

[COLOR=Red]**And this is my one question:**[/COLOR] How can you get the correct driver to always load, because putting the these two commands (w/o the sudo) in /etc/rc.local has no effect.[/LIST] 
[*]While it is probably  necessary to disable fglrx in  /etc/default/linux-restricted-modules-common, I had to remove the line
 DISABLED_MODULES="fglrx"
so that the new driver could work, which wasn't mentioned in the procedure.
[*]You do not have to reboot the computer between most, perhaps all steps, in the the procedure for installing the new driver.  However, you do have to restart the X server, which Ctrl-Alt-BSpace does.[/LIST]Hope this helps.

---

### Post by muqo on 2007-11-22
at step 9, i get this error;

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory :(

my video card : ati radeon x300

---

### Post by Phryxus on 2007-11-23
Use this, to fix it muqo:

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by Dynar on 2007-11-26
I followed this guide, provided by the wiki, [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I have ATi Radeon 9550 and can't seem to get this to work properly. I haven't been able to get any direct rendering working properly and as an ex-Windows user, it's frustrating not being able to start searching for support on how to install some linux supported games.

This is what my end results look like. To begin with, this is my xong.conf;
```
 Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection 
```

$ glxgears: Boots me to Login Screen

$ fgl_glxgears gives me this error;

```
Using GLX_SGIX_pbuffer
Error: couldn't get fbconfig
```

$ aticonfig: I've initialized "fglrx", forced it, checked it. Everything seems to be in order

$ amdcccle: I get this error "There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following. No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig." (Which I did configure, without positive resaults.)

$ glxinfo
```
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

This is what I don't understand in this code (in glxinfo): 

```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
``` 

While;

$ fglrxinfo says:

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.1.7059 Release
```

and $ glxinfo | grep direct gives me 

```
 direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

Anyone any ideas?

---

### Post by murraypatterson on 2007-12-04
Hi, I'd just like to say that this dummies guide did not work for me either.  I don't think my problem is as severe as most though.  I tried method 1 for installation, this worked fine, but then when I got to the stage of configuring it (the aticonfig commands), these commands aborted and dumped core, so I tried the manual config (going into the xorg.conf file and changing the lines).  I rebooted and it didn't work (ubuntu generated a failsafe xorg.conf file for me, and used that)

so then I thought I'd try the manual install, since your dummies guide says that the other one is out of date.  All of the commands worked fine here, so then I went to the configuring commands.  This time the two "aticonfig" commands worked fine, so I rebooted and again ubuntu generated a failsafe xorg.conf file for me, and used that)

any ideas?

lspci -n | grep 0300
01:00.0 0300: 1002:5964 (rev 01)
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

thanks,
Murray

---

### Post by Yellow Pasque on 2007-12-04
Murray, the 9200 series is not supported in recent ATI fglrx releases. See [http://ubuntuforums.org/showthread.php?p=3888532](http://ubuntuforums.org/showthread.php?p=3888532) for info on how to use the "ati" driver.

---

### Post by PhiXion23 on 2007-12-04
I installed the new ATI driver (7.11) using this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) ,(method 2, ubuntu 7.10) i have a ATI x1650PRO AGP X8  graphic card ! all worked when i run fglrxinfo in konsole i get this>>> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7059 Release
But whan i run glxgears on konsole i dont see eny gears or picture it is just black little screen and when i start some games like enmy territory:quake wars linux 1.2 client i get black screen with sound ! when i run compiz then i see only my wallpaber with mouse cursor and i must restart linuX ! Videos have black screen !PLEASE HELP .. here is my xorg.conf file 
[ATTACH]52245[/ATTACH]   Sorry for my English

---

### Post by folletto on 2007-12-05
I found very useful this app:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

{Dell INSPIRON 1501, Ubuntu 7.10, Ati Radeon Xpress 1120}

---

### Post by mamlouk on 2007-12-05
@PhiXion23
You seem to have 2 "Device" sections in your xorg.conf. One that loads the radeon driver, and the other loads the fglrx driver. Try to manually remove the radeon one by ```
sudo gedit /etc/X11/xorg.conf
``` Delete the device section that has the radeon driver, then run ```
sudo aticonfig --initial --force
```, and restart X by pressing Ctrl-Alt-Backspace. Tell us the outcome when you've done that.

---

### Post by murraypatterson on 2007-12-08
> **Temüjin said:**
> Murray, the 9200 series is not supported in recent ATI fglrx releases. See [http://ubuntuforums.org/showthread.php?p=3888532](http://ubuntuforums.org/showthread.php?p=3888532) for info on how to use the "ati" driver.

thanks, I tried this, but unfortunately it failed as well :(

but I think you're on the right track . . . I remember having this problem with xV support everytime I install the newest version of ubuntu, and I always am able to get around it . . . and it's some other method aside from this flgrx driver (that I've never heard of until recently I must admit) . . . I thought it had something to do with ubuntu 7.10 (the way to get around it for this particular version), but I think simply the old method I used will get me around (I'll remember to record how I did it this time :)

I do remember installing totem-xine when trying to get dvd's to run smoothly (as well as getting libcccs, or something like this, for the encoding) . . . perhaps this will fix the problem?  I guess I'll find out soon enough

Cheers,
Murray

---

### Post by lamadredelsapo on 2007-12-14
I followed Method 2 from [http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page") and it worked like a charm.

---

### Post by db0 on 2008-04-01
[Still trying]("http://ubuntuforums.org/showthread.php?t=740287") to get rid of the Mesa renderer :(

---

