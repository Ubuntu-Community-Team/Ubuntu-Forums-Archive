---
title: "More nVidia woes. Frustrating the heck out of me."
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by kingbuxton on 2007-05-19
I have tried about 5 different ways of doing this (why there isn't one straightforward method I have no idea). Last one I used was the Envy auto install thing. Regardless of how I do it I get the exact same error.

Ubuntu reboots - I get a bluescreen saying X is wrong.

From what I can remember the fault is along the lines of: 

Screens found with no useable config.
Fatal Server Error.
No screens found.

There may have been more, that is all I can remember. This is starting to remind me of every other Linux I have tried, it is just problem after problem doing what should be simple. It's just a Gfx driver, you know what I mean. All I want is a foolproof method of getting them on, and then I will do the figuring out why and how all this works. 

I am wondering if the 8800Gts is supported in the nVidia drivers, it has only got Windows support in the last few weeks so I may be pi**ing in the wind trying to get it working :lolflag:

If there is support for the 8800 can someone just list some fool proof instructions that you gan guarentee will work. Anything you need to know beforehand - just say.

It's Ubuntu 7.04.

What worries me now is I can't actually boot Ubuntu as it will stop at that annoying X screen. So first off I could do with some way of getting it back into the O/S - TBH it is as easy to reinstall the damn thing, it only takes about 10 mins.

---

### Post by glennric on 2007-05-19
I assume you have installed the linux-restricted-modules and nvidia-glx-new packages.

If so post your /etc/X11/xorg.conf file and we can probably figure out what is wrong.

---

### Post by kingbuxton on 2007-05-19
I have no idea tbh. It was a clean install of 7.04. I ran that Envy thing figuring that was fool proof. That's all I can tell you. The restricted thing, that was the first thing I tried, it all worked, it asked me to reboot Ubuntu, and we have blue X screen again. Every method I have tried has done exactly what it is supposed to do, no error messages, until I reboot, and then it all goes wrong. Are we 100% that the 8800Gts is supported?

I just tried sudo dpkg-reconfigure xserver-xorg

Ran through that, stuck all the defaults in - still the same when I reboot.

I have no idea how I get /etc/X11/xorg.conf - and if I do how do I get it into XP - that is how I am on here, it is dual booting. 

I am thinking LiveCD it - redo Ubuntu, already done that three times today so I am getting good at that :)

Ask a silly question, but why hasn't anyone in the Linux world just copied Windows, you download the driver to the desktop, double click it, it installs, you reboot, it works. I am sure there are all manner of ways to get drivers into XP - but why struggle when you can make it as easy as that. If you want to be more hands on, fine, do it that way, but make it easy for those just starting. Then I will figure the nitty gritty out later.

I dread to think how someone that isn't computer literate goes on.  :lolflag: ](*,)

---

### Post by glennric on 2007-05-19
To get to your xorg.conf file you could use Explore2fs.  Do a google search for it.  With this you can browse your linux partitions.

You should also check the nvidia website to see if your video card is supported in linux.

---

### Post by kingbuxton on 2007-05-19
Figuring I could very well waste time messing about - 10mins and Ubuntu is redone, So here I am.

Added initial support for NVIDIA SLI with GeForce 8800 - so I am taking it as read that there is single support for the 8800.

OK - I have a clean install of Ubuntu 7.04 - all I have done is the updates it asks you to do when it installs. And I have NVIDIA-Linux-x86-1.0-9755-pkg1.run sitting on the desktop. And installed Opera. I have done nothing else. I am actually loath to try anything tbh - at least it is up and running and I have www.

If you are in this position, what is the way you would go, foolproof and that doesn't require me to have a degree in Linux command lines. I have pretty much exhausted all the tutorials from this site. On the www they are all pretty much the same walkthroughs, the Envy way didn't work. The restricted drivers option doesn't work.

I am pretty much at a loss.

---

### Post by kingbuxton on 2007-05-19
Only assume one thing - that I am a complete moron :lolflag:

No I haven't, fresh install, updated, drivers on desktop and Opera. That is it.

I have no idea what that website is, dude, I am struggling enough as it is, I can't learn a new language as well, my brain will stop me breathing. :)

I have several tabs, with different ways of doing this, I am just scared that whichever I choose will leave me with the X Bluescreen. Then I will go ballistic. 

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.19/2.6.19.3-2](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.19/2.6.19.3-2) wtf? This gets more complex.

OK - stuck the Glx on nvidia-glx_1.0.9631+2.6.20.5-15.20_i386.deb I hope these are the correct ones, again, I have no real idea what I am doing, but they installed fine. But I still can't change resolution above 1024. In restricted there is still a disabled nVidia driver. What exactly did I just install?

---

### Post by dummies85 on 2007-05-19
you installed the wrong one, it was supposed to be nvidia-glx-new
you could use

> sudo apt-get install nvidia-glx-new

but i'm also having trouble with this driver, every time i boot the X always fail and i have to reinstall the Nvidia driver, still trying to find out why

---

### Post by kingbuxton on 2007-05-19
That doesn't suprise me, the fact I have the wrong one and you are having issues. I have basically lost patience with it. Every year or so I try the new great version of Linux, only to get hit with the same exact issues. Surely something as simple as installing a graphics driver shouldn't be this difficult. Although I am sure once you have done it, you get it, and it is easy. But getting the first step is a nightmare. I mean call XP but a complete novice can have it running with drivers without very much hassle. Unless downloading/saving/double clicking and rebooting are beyond you. 

Back in the day I never had this much hassle getting 3.1/95 on a PC, and I had no idea what a PC was. 98/2000/XP/Vista all a piece of you know what to get up and running. It's getting late and I am getting weary, so I might give it one more go tommorow. If that blo*dy X screen appears again, that will be that, another year and I will try the next big windows killer. I know it is a more hands on O/S - but i don't really care these days. It was fun configuring IRQ's and editing Batch files and all that, but I no longer care about fiddling, I just want it done for me. 

I will try that apt-get command - I am pretty sure it will all go to pot when I do it. 

Linux still has a really Looooooooong way to go before people, even PC compitent ones, will switch. It's a shame they can't get the basics sorted. That Envy is the way to go, I mean it didn't work, but that is more the sort of thing. This O/S has so much going for it, but it's the stuff that they should have working without fail from day1 that lets it down.

Linux needs to do what it does well and combine it with the few things Windows does well.

---

### Post by kingbuxton on 2007-05-19
OK - back in Ubuntu - did "sudo apt-get install nvidia-glx-new"

Looks like it removed the other one and replaced it with the new one. But I still don't get what I just installed. This isn't the nVidia driver, it is the OpenGL driver only or something? So do I now I have 3D acceleration under GL or do I still need to put the nVidia driver on.

Do I go into the restricted driver manager and enable it? That messed up last time. 

Should I run Envy again, will that now work? That messed up last time.

I still can't see any way of getting my desktop to run 1280. 

I know, don't laugh, I am a dumbass, I accept this. All I need is someone to sit at the side of me, get this working, and that will be that, I will be away.

---

### Post by z0phi3l on 2007-05-19
No don't do anything else for now. 

You have the current Nvidia drivers, Limux uses OpenGL for 3D rendering, since DirectX is a Windows only thing.

To fix your resolutions, I don't remember but someone will come by and give you an answer.

The main thing you need right now is some patience, with Linux things aren't dumbed down so that a Vegetable can run it, things can get a bit dicey from time to time and need a reinstall here and there.

---

### Post by kingbuxton on 2007-05-19
Oh I get the whole GL/D3D thing. That I am OK on.

sudo apt-get install nvidia-glx-new - has that installed the lastest GL driver? Example - in XP - I grab the latest Forceware drivers for an 8800 install and reboot. Is that what I have basically just done? 
Or have I just done a portion of that? I mean there is no nVidia control panel, that I can see, But again, I am a Linux dumbass, there may not  even be a control panel, who needs shed loads of 3D settings in an O/S where games aren't an issue.

So basically do I now have 3D (via OpenGL) and general Gfx ability? Or is the nVidia driver NVIDIA-Linux-x86-1.0-9755-pkg1.run still required. Or is that going to install the same thing ie nvidia-glx-new with nVidia control panel and settings?

---

### Post by z0phi3l on 2007-05-19
> **kingbuxton said:**
> Oh I get the whole GL/D3D thing. That I am OK on.

sudo apt-get install nvidia-glx-new - has that installed the lastest GL driver? Example - in XP - I grab the latest Forceware drivers for an 8800 install and reboot. Is that what I have basically just done? 
Or have I just done a portion of that? I mean there is no nVidia control panel, that I can see, But again, I am a Linux dumbass, there may not  even be a control panel, who needs shed loads of 3D settings in an O/S where games aren't an issue.

So basically do I now have 3D (via OpenGL) and general Gfx ability? Or is the nVidia driver NVIDIA-Linux-x86-1.0-9755-pkg1.run still required. Or is that going to install the same thing ie nvidia-glx-new with nVidia control panel and settings?

You are done from what I understand

Nvidia didn't recreate their control panel for linux.

If we keep this bumped you will hopefully soon get a way to fix your resolution and you should be set after that :)

---

### Post by kingbuxton on 2007-05-19
Oh OK, Cool. Lets hope. I will let the Yanks all wake up and come on, will check again tommorow. As much as the O/S can frustrate the hell out of you, the forums are nothing but patience and help. If this was Windows I would have snot nose 12 year olds slagging me in text type.

Thanks to all for the replies. Not just on this thread. This will all click at some point and that will be that, I will be on here helping. I have to get it working this time.

---

### Post by justinae on 2007-05-19
I am having the same frustration. Here is what I've done.

1. When I check to enable Nvidia accelerated graphics driver it restarts my computer and X doesn't work.
2. I restore xorg.conf
3. I try to turn on Deskop effects but that puts me right back to step one.
4. Then i tried automatix. When I rebooted I got the same thing, broken X.
5. Then I tried the manual installation of the Nvidia driver, again, broken X.


So does the latest nvidia driver (nvidia-glx-new) actually contain the accelerated piece or is that seperate?

I have the Nvidia Geforce FX 5200. Running Fiesty Fawn.

I'm totally lost here. It seems like a vicious loop. Any help is appreciated. 
Many thanx!

---

### Post by kerss on 2007-05-19
I have the exact same issue, but I can't get anything related to nvidia and driver to work... For me, X says that the nvidia kernel won't accept interrupt signals from the device, and then that there are no usable screens, but I don't know if that is what you're getting. I have given up on Linux for now, because I honestly don't want it this bad!

Just a few things I've picked up in my many hours pulling my hair out over this:

-You might have to manually "unlock" resolutions. Use the X server reconfiguration and mark the desired ones, or manually add them to /etc/X11/xorg.conf if you have gotten a setup that works, and don't want to fiddle with it.

-The control panel must be installed seperatly. I think the command is "sudo apt-get install nvidia-settings", but you should google that first.

If you have a working setup, make a backup of the xorg.conf file. That way, if it stops working, simply press alt+F1 to enter the text interface, and restore file by typing "sudo cp /etc/X11/xorg.conf_BACKUP /etc/X11/xorg.conf", if your backup is called xorg.conf_BACKUP. 

I'm actually a complete n00b, so if any of the info above is wrong, I hope someone will correct it. It's just that I remember what it's like to reinstall everytime something stops working, and how it's like to get answers you have to be Linus Torvalds to understand... :)

---

### Post by ricrac on 2007-05-19
Please also if you would, direct some of your frustration to Nvidia.

Your systems worked upon install with the open source driver.  You wanted openGL, etc. additions which are only available in a closed source driver.  

Until Nvidia opens the driver, there will probably always be these issues.

Please contact NVidia and voice your opinion, if enough people complain perhaps they will see it as a marketing win to open up the driver source.


Here a working config to compare.  Single monitor output.
The highest mode written in xorg.conf will be the startup mode, then any mode (including modes not in xorg.conf) can be selected within X using nvidia-settings.
Set    
Modes      "1024x768" 
to whatever you want to boot up in, i.e. 1600x1200
Modes      "1600x1200"    

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007
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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
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
    HorizSync       30.0 - 130.0
    VertRefresh     50.0 - 160.0
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
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" 
    EndSubSection
EndSection

```

---

### Post by justinae on 2007-05-19
yeah my xorg.conf looks pretty similar to yours ricrac. the problem is that I followed all the steps to purge my old nvidia driver, installed the new 9755 driver but it still won't change my driver from "nv" to "nvidia". Every time i change it myself it breaks X.

---

### Post by zero244 on 2007-05-19
Your right the video drivers are the biggest hassle with Linux if your going to try and use Beryl or Compiz. I wont go into it but I had much better luck with a ATI card and XGL with Beryl.
Im now using a Nvidia card which doesnt work very well with Beryl or Compiz.
Something that might make your transition easier is install Automatix2.........it will install your video drivers and give you ntfs support with a couple of clicks.
Its the only way I could get my 7600 card to work with Opengl.
It has some other nice programs to install too.
Check it out.
Ive decided once I get Ubuntu running the way I want I will not do anymore updates.........sometimes the updates will cause problems........just like they do in Windows sometimes.
Hang in there Linux has merit.

---

### Post by kingbuxton on 2007-05-20
I installed Automatrix - clicked on the nVidia driver - installed it - laughed at the bit where it says in the "RARE" event of X not restarting - rare event - that's a good one. In the rare event type automatrix-nvidia-restore.

Rebooted and got a rare event - same exact X failed blue screen that I am sick of seeing. 

Typed automatrix-nvidia-restore and suprise suprise, nothing happened. Other than telling me this isn't a command. Great. So now I am back to an O/S that doesn't boot. With the only way of getting it back being an intimate knowlege of the inner workings of Linux and half a dozen command lines memorised. This is absolutely pathetic. I could go through the X setup, but I did that yesterday and it never seems to come back. So I am back to reinstalling Ubuntu for about the fifth time. 

I mean it could be nVidia it could be Linux I really don't know, but something so simple shouldn't be this difficult. If it was going to work I would have got it working by now. All I want is my desktop at 1280 - I have totally given up on ever getting 3D desktop working, I mean if the ruddy drivers can't be installed after trying 4 manual and 2 automatic methods, what hope is there of getting anything to actaully run in 3D?

Should I do one last plea for help?

No point in linking me to walkthroughs on this site, I tried all the ways I could find before I even posted, they all create a RARE event. Envy and Automatrix do the same. 

So either I am so unbelievably stupid when it comes to Linux that a step that you guys take for granted is getting missed by me. The two automated ways have no input from me other than install/run/reboot, I don't see how I messed up letting an automated script do it for me. 

Maybe the drivers simply don't work? 

I still have chipset and sound drivers to battle with yet #-o

---

### Post by kingbuxton on 2007-05-20
OK. Fresh install of 7.04 - I tried the tseliot walkthrough again to if I missed or messed something up. 

Make sure you have both the Universe and Multiverse repositories enabled - did that.

uname -r -  2.6.20-15-generic

sudo apt-get install linux-generic

Went to the driver page - first list - GeForce 8800 GTS 0x0193 - 9755

sudo apt-get install nvidia-glx-new

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nvidia-xconfig --no-composite

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;

Copy/Pasted into the empty text file and saved it.

Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver) - did that - the screen went blank - flashed On/Off a few times - bang - X Blue Screen.

Tried sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf didn't help.

Tried sudo dpkg -reconfigure -phigh xserver-xorg didn't help.

Also tried sudo apt-get --purge remove nvidia-glx-new didn't help.

When I originally did the X re-start and it failed I checked the LOG and it an all new error compared to last time.

Using config file /etc/x11/xorg.conf
Failed to load module WFB (module doesn't exist,0)
nVidia(0): Need libwfb but wfb screeninit not found
Fatal server error
Add Screen/Screeninit failed for driver 0

I scribbled it down fast so some of that maybe wrong, but I am sure this is common and you get what I mean.

So now I am back to can't boot to a desktop and no idea, bar re-installing it for the sixth time, how to sort it.

I think it is time to admit defeat? :(

---

### Post by whb on 2007-05-20
I have a 8800GTS and followed the instructions on

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

This worked perfectly for me. It seems so simple now,

Hunter

---

### Post by kingbuxton on 2007-05-20
1. Thanks for the replay and a different way of doing it.

2. WTF is wrong with this O/S? It seems to go out of it's way to not do what you want it to do, what the hell is wrong with it?

I did all of it up to sudo vi /etc/default/linux-restricted-modules* it opens a text file - I scrolled down to the bit where it says Change the DISABLED_MODULES=”" 

I tried to change it to DISABLED_MODULES=”nv” and it wont let me type anything in! As soon as I try to put nv between the "" I get an error (an error in Linux what a suprise) 

E35: No previous Regular expression ARGGGGHHHHHH - it's a ruddy joke this now. It's one problem after another. Then I clicked the middle button of my mouse by accident and it pasted.......

sudo vi /etc/default/linux-restricted-modules* inbetween the "" 

OH OK - it wants to be crappy and annoying and childish - I opened a .text file and put nv in there - copied it - went to the "" and pressed the middle button, oh of course it didn't paste that time, why would I expect anything else? Linux is always one step ahead of you, when you try to apply logic.

And people call Windows, give me a break, overall it wipes the floor with this joke, at least I wouldn't have to go through all this to install (two days, seven installs, and several different ways of doing the same thing) a driver, and now I have to go through another huge involved procedure to add two letters to a text file. It is sickening, it really is.

So, more help. Why can't I alter the text file? What do I need to do to alter this file? What does that error mean?

---

### Post by glennric on 2007-05-20
> **kingbuxton said:**
> 1. Thanks for the replay and a different way of doing it.

2. WTF is wrong with this O/S? It seems to go out of it's way to not do what you want it to do, what the hell is wrong with it?

I did all of it up to sudo vi /etc/default/linux-restricted-modules* it opens a text file - I scrolled down to the bit where it says Change the DISABLED_MODULES=&#8221;" 

I tried to change it to DISABLED_MODULES=&#8221;nv&#8221; and it wont let me type anything in! As soon as I try to put nv between the "" I get an error (an error in Linux what a suprise) 

E35: No previous Regular expression ARGGGGHHHHHH - it's a ruddy joke this now. It's one problem after another. Then I clicked the middle button of my mouse by accident and it pasted.......

sudo vi /etc/default/linux-restricted-modules* inbetween the "" 

OH OK - it wants to be crappy and annoying and childish - I opened a .text file and put nv in there - copied it - went to the "" and pressed the middle button, oh of course it didn't paste that time, why would I expect anything else? Linux is always one step ahead of you, when you try to apply logic.

And people call Windows, give me a break, overall it wipes the floor with this joke, at least I wouldn't have to go through all this to install (two days, seven installs, and several different ways of doing the same thing) a driver, and now I have to go through another huge involved procedure to add two letters to a text file. It is sickening, it really is.

So, more help. Why can't I alter the text file? What do I need to do to alter this file? What does that error mean?

The problem is that you don't know how to use vi. vi is a moded editor.  In order to insert text you need to put the editor into insert mode.  To do this move the cursor to where you want to put the text and press 'i'.  Then type in the text and hit escape to leave insert mode.  Then type "shift-z-z" to save and exit vi.

---

### Post by kingbuxton on 2007-05-20
I don't know if I should Laugh or Cry or do both.

The problem is I have no idea full stop. And that is THE problem. All the walkthroughs ASSUME stuff like "VI is a modded editor" see that means nothing to me, it's like I have a hurdle between each step, and each hurdle needs help to get over.

I have this exact issue when I try and explain Windows to new users that know nothing, you say stuff or do stuff that you take for granted and you simply don't realise you lost them when you said Copy/Paste. 

I was just going to dump it tbh but it is too late to start trying to fix MBR's. If I can be bothered I will try that last walkthough, if that fails it's gone. 

Thanks for the reply.

---

### Post by C0n5ci3n53 on 2007-05-21
instead of vi I would recommend "pico" so it'd be like "sudo pico /etc/default/linux-restricted-modules*"

To quit just press CTRL-X (as it says at the bottom) and it will ask you if you want to save. Pico is a normal text editor, you dont need to know 100 commands to actually edit a file =] I don't understand why people recommend the harder to use vi instead of pico. Anyways, I feel your pain, I too have a GF8800GTS and the only way I can boot to linux is to boot into recovery mode, reinstall the driver using that NVIDI....sh file and restart GNOME. If I find a way to fix this I'll tell you ;)

---

### Post by heldal on 2007-05-21
> **C0n5ci3n53 said:**
> instead of vi I would recommend "pico" so it'd be like "sudo pico /etc/default/linux-restricted-modules*"


Sure, "pico"/"nano" is easier than "vi" for newbies. Anything is ... probably... 

This particular problem with some GPU's (8k's at least) is caused by a file that is missing in the nvidia-glx-new package. One possibility is of course to do a full installation of the driver-package from NVidia. The downside to that is that you'll have to keep it up to date and re-build kernel-modules whenever the kernel gets an update. An alternative is to install the missing file manually, let the ubuntu-maintainers take care of the bug and hopefully avoid problems with future updates. 

More [here]("http://ubuntuforums.org/showthread.php?p=2687780#post2687780")

---

### Post by dannyboy79 on 2007-05-21
I had this problem as well, though mine was with Envy unstable and trying to install the brand spankest newest nvidia driver 100.xx.xx. No matter what I did, no matter what, X would fail, it would either keep trying to load the 9755 kernel module or it would not try to load any module. This was after some1 told me to add:
blacklist nvidia_new 
to the /etc/modprobe.d/blacklist file as well as make sure i had "nv" within the file, /etc/defaults/linux-restricted-modules-common or whatever the file is. SO the I troubleshot this for about 2 hrous with the help of a forum users that goes by the screen name psyke83 or somethign very similar to that. HE was helping me thru gaim. It turned out that the Envy unstable program had a bug and didn't do somethign correctly. So the soltuion was to add a hack to my rc.local file so that the correct nvidia kernel module would load. This is what I added BEFORE the exit 0 within the rc.local file:
find /lib/modules/`uname -r` | grep -i nvi | grep -v fb | grep nvidia.ko$ | xargs insmod
and finally the damn 100.xx.xx kernel module would load. BUT to no avail, random freezing is STILL OCCURING!!!! I have posted a million times in various threads about Fiesty freezing on simple tasks, like gedit, or various config dialog boxes opened thru System, Admin or Prefs. ANyway, I thoguht I'd at least let other know about the solution if they get teh dreaded API mismatch error when the nvidia driver is 100.xx.xx but the module being loaded was 9755 when they used Envy Unstable. The developer has been notified. Now, what do I do about frickin 3d Acceleration since both the NV and the NVIDIA driver freeze like this????? I am certainly not going to stick with VESA!!!!!! Might be moving on from Fiesty, not sure yet though.

---

### Post by kingbuxton on 2007-05-21
Used Pico in place of VI - added nv and saved (double checked it to make sure it saved).

Grabbed the latest driver NVIDIA-Linux-x86-1.0-9755-pkg1.run saved to desktop.

Ctrl-Alt-F2 to open up a console and login (did that).

Logged in on desktop.

sudo /etc/init.d/gdm stop (did that)

sudo sh NV* - does nothing. Now I have no idea if this is another assumption moment? Is he putting the * in to mean the entire driver name ie NVIDIA-Linux-x86-1.0-9755-pkg1.run - so I tried that as well and it just says it can't open it.

Lets face it, this aint happening. Lets forget the installation of a driver, clearly nVidia are as bad as ATI for Linux drivers and it is all a front when people say they are better, and I have already given up on any kind of 3D desktop, the whole point of me doing this really.

So as a small victory, how in Gods name do I get 1280*1024 on desktop. Surely that has to be simple?

---

### Post by glennric on 2007-05-21
Nvidia is considerably better for linux than ATI.  There is no question about it.  Nvidia provides drivers for linux and doesn't make linux developers try to backwards engineer the card to figure out how to make it work.

As to why you can't run the shell executable, there are a couple of possibilities.  It could be that you had a faulty download, or it could have to do with dash being your default shell instead of bash.  Although I don't think dash has a problem with this particular file.

Try to download the file again and try 
```
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```
again.

If that doesn't work try 
```
ls -al /bin/sh
```
and see if that is pointing to bash or dash.  If it is dash then try
```
sudo dpkg-reconfigure dash
```
and answer no to the one question it asks.  Then try to run the NVIDIA installer again.

I just realized another possible problem.  You said you saved the file to the desktop.  So when you went to the console and stopped gdm, did you change directories to the desktop?  Make sure you are in the directory that you saved the file to when you try to run it.

---

### Post by glennric on 2007-05-21
> **C0n5ci3n53 said:**
> instead of vi I would recommend "pico" so it'd be like "sudo pico /etc/default/linux-restricted-modules*"

To quit just press CTRL-X (as it says at the bottom) and it will ask you if you want to save. Pico is a normal text editor, you dont need to know 100 commands to actually edit a file =] I don't understand why people recommend the harder to use vi instead of pico. Anyways, I feel your pain, I too have a GF8800GTS and the only way I can boot to linux is to boot into recovery mode, reinstall the driver using that NVIDI....sh file and restart GNOME. If I find a way to fix this I'll tell you ;)

The reason so many people recommend vi over pico or nano is because it is immensely more powerful than those editors.  Sure if all you want to do is edit a little text file those editors are fine.  But if you take the time to learn more about the features of vi, you can do much more at a much higher efficiency level than probably any other text editor in the world.  Emacs users may have some room to argue.  When I was in windows I probably would have said UltraEdit was the best ever.  That is probably the best GUI text editor ever, but once you really start to learn the advanced features of vi (or really vim) it leaves any GUI text editor behind.

It is true that vi should never be recommended for a linux newbie.  Unfortunately that is what the old timer *nix users are accustomed to.

---

### Post by dannyboy79 on 2007-05-21
> **kingbuxton said:**
> Used Pico in place of VI - added nv and saved (double checked it to make sure it saved).

Grabbed the latest driver NVIDIA-Linux-x86-1.0-9755-pkg1.run saved to desktop.

Ctrl-Alt-F2 to open up a console and login (did that).

Logged in on desktop.

sudo /etc/init.d/gdm stop (did that)

sudo sh NV* - does nothing. Now I have no idea if this is another assumption moment? Is he putting the * in to mean the entire driver name ie NVIDIA-Linux-x86-1.0-9755-pkg1.run - so I tried that as well and it just says it can't open it.

Lets face it, this aint happening. Lets forget the installation of a driver, clearly nVidia are as bad as ATI for Linux drivers and it is all a front when people say they are better, and I have already given up on any kind of 3D desktop, the whole point of me doing this really.

So as a small victory, how in Gods name do I get 1280*1024 on desktop. Surely that has to be simple?

the Envy script will take care of all of this for ya, no need to have to use a bash shell (sh). Just download the  latest  stable release of Envy. paste this into a terminal.
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.3-0ubuntu5_all.deb
```
then go to places, and if you were at your home directory when you used the wget command (directory can be found by hitting "pwd" from the terminal line. it should return, /home/username/) then chose Home, then just double click on the envy.deb file. It'll open a dialog box, click to install it. It will do some stuff and not go away but you;ll notice that there'll be button towards the bottom right that should say close after awhile because it's installed now.
Then go up into Menu, Programs (or whichever pick is on the far left, then go into system I believe it is and chose Envy, then chose to install the 9755 driver, and restart as requested.

---

### Post by orrorin on 2007-05-22
Have you checked out this forum from NVidia for linux users? 

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

You might want to check if you are indeed using the right drivers from NVIDIA.
There are also some requirements to "purge" previous installs. (I dunno what it means, just repeating what I read.)

cheers!

---

### Post by eye208 on 2007-05-22
> **glennric said:**
> Nvidia is considerably better for linux than ATI.  There is no question about it.
This was true in the past and has since turned into urban legend. Feisty's version of the ATI driver can be installed and activated with just a few clicks in the restricted driver manager and no reboot. It has become so easy you can even do it from the Live CD.

I didn't even know there's such a thing as a blue screen in X until I read this thread... :shock:

---

### Post by glennric on 2007-05-22
> **eye208 said:**
> This was true in the past and has since turned into urban legend. Feisty's version of the ATI driver can be installed and activated with just a few clicks in the restricted driver manager and no reboot. It has become so easy you can even do it from the Live CD.

I didn't even know there's such a thing as a blue screen in X until I read this thread... :shock:

That is true if you have a newer ati video card.  Many older (5 or 6 year old) cards are not well supported.  From what I understand ati is working harder to get more support for linux now.  Many hardware manufacturers are in an effort to bring down software prices (for Windoze) and thus be able to increase hardware prices.

---

### Post by kingbuxton on 2007-05-22
Woah, loads of replies.

glennric, it said Desktop at the command promt.

dannyboy79, I tried Envy and I got the X blue screen.

I dunno about the Bash Dash :p I will check that out.

orrorin, yeah been there as well. Seems like lots of people have got it working lots of different ways. And lots of people can't get it working regardless of what way they use. Which all in seems really odd.

It isn't a Blue Screen as in the Windows BSD! It is just a Blue Screen that says X isn't configured fully and gives you a log of the problem before dumping you to a command prompt. I guess it allows you to sort it out if you know what you are doing.

---

### Post by kingbuxton on 2007-05-22
When I CTRL/ALT F2 the command prompt is me@me-desktop$ something like that. Is this not the desktop?

---

### Post by dannyboy79 on 2007-05-22
ok, after X fails, and you log in anyway under the terminal, what does this result in
dmesg | grep NVIDIA
If it says that it was trying to load a nvidia module that doesn't match the Nvidia Driver than that's the dreaded API Mismatch problem. Some solutions include adding "blacklist nvidia_new" to the /etc/modprobe.d/blacklist file and if you're trying to get the latest nvidia driver to work, 100.xx.xx, than there is even a command you need to add to the /etc/rc.local file to get it to load the correct module. This is a very nasty problem as I have been dealing with it myself. Good luck. Have you emailed the author of Envy if you used it and it resulted in the API Mismatch? He doesn't believe me and another user that Envy has a bug in it.

---

### Post by kingbuxton on 2007-05-22
Using config file /etc/x11/xorg.conf
Failed to load module WFB (module doesn't exist,0)
nVidia(0): Need libwfb but wfb screeninit not found
Fatal server error
Add Screen/Screeninit failed for driver 0

I have tried so many ways now that I am unsure if I wrote that down after Envy failed or one of the other methods. 

Also (off topic a bit) I assume Root is equivalent to Administrator is Windows? I understand why Linux does it, but I have no real need for a locked system, only me on this PC. So is there a simple way of getting 7.04 into a permanent Root mode - so I can alter anything and copy/Paste files into any directory. I know, I know once you know how to do this it is easy, but I don't. So being root all the time would help. I found a guide to doing it for an older version but it looks like 7.04 is a bit different and what it told me to do wasn't there when I looked. 

I just did CD .. to goto the Home Dir - but I don't have permission to Copy files into the folder.

---

### Post by glennric on 2007-05-22
> **kingbuxton said:**
> When I CTRL/ALT F2 the command prompt is me@me-desktop$ something like that. Is this not the desktop?

No that is not the desktop directory.  The desktop directory is "Desktop".  After you log in type
```
cd Desktop
```
to get into that directory.  Type ls to see if the file NVIDIA* is in the directory you are in.

By the way, I don't know if you realize this or not, but unlike in windows upper and lower case letters in file and directory names make a difference.  The directory "Desktop" is not the same as the directory "desktop".

---

### Post by dannyboy79 on 2007-05-22
> **kingbuxton said:**
> Using config file /etc/x11/xorg.conf
Failed to load module WFB (module doesn't exist,0)
nVidia(0): Need libwfb but wfb screeninit not found
Fatal server error
Add Screen/Screeninit failed for driver 0

I have tried so many ways now that I am unsure if I wrote that down after Envy failed or one of the other methods. 

Also (off topic a bit) I assume Root is equivalent to Administrator is Windows? I understand why Linux does it, but I have no real need for a locked system, only me on this PC. So is there a simple way of getting 7.04 into a permanent Root mode - so I can alter anything and copy/Paste files into any directory. I know, I know once you know how to do this it is easy, but I don't. So being root all the time would help. I found a guide to doing it for an older version but it looks like 7.04 is a bit different and what it told me to do wasn't there when I looked. 

I just did CD .. to goto the Home Dir - but I don't have permission to Copy files into the folder.

Well there is 2 ways to do this. 1.) You can always just log in in the first place as root. 2.) You can switch to root after you login  under your own username. (if you want to make it so that your username has root privalages without having to enter sudo here is the link: [http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33))

  You can enable root login within the Users and Groups within System, Admin, or is it the Login preferences within System, Admin? Once you enable root to be able to log in, then you just need to give him a password, that's done with 

```
sudo passwd root
```
it'll ask you for a password 2 times and now you'll be able to log in as root using that password (dont' confuse the sudo password and the root password).

OR you can always switch to root if you're sick of entering sudo all the time. You can do that many different ways but the way that I do it is with this command

```
sudo -i
```
then enter YOUR usernames password (sudo password)  and you're temporarily logged in as root, you can tell because the terminal changes to root instead of you username. good luck 

PS, they came up with sudo for a very good reason but if you're confident about running as root all the time and as long as you're aware of the risks, than good luck)

---

### Post by kingbuxton on 2007-05-22
Right - Good news and bad news.

Good News [http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html) this works! I have a big fat nVidia logo at boot. And in the restricted drivers it is finally enabled.

My issue was lower case UPPER case, no I didn't know that, so I was doing desktop and it is Desktop! ARGHHHHHHH. Ran through the nVidia installer and it all worked fine.

Bad News - I still don't have an option to set desktop to anything about 1024*768, but I do have several wierd resolutions below this?

:popcorn: I HAVE nVIDIA drivers installed :popcorn:

Now, if any of you can figure out why I can't do 1280 I will be truly happy. I can only think that my TFT is set as some generic type and I need to tell it that it can support upto 1280. I saw this in the X setup I think, but I don't want to balls it up after all this. Although I know how to get the drivers to work, so it is a 30 second job next time.

---

### Post by kingbuxton on 2007-05-22
Incorrect. The screen resolution in System/Preferences doesn't seem to work. Applications/System tools has the nvidia control panel, and you can set it to 1280 in there. And then it appears in System/Preferences list. 

Got 1280, wobbly icons and a big fat rotating cube of a desktop.

Excellent.

---

### Post by glennric on 2007-05-22
> **kingbuxton said:**
> Incorrect. The screen resolution in System/Preferences doesn't seem to work. Applications/System tools has the nvidia control panel, and you can set it to 1280 in there. And then it appears in System/Preferences list. 

Got 1280, wobbly icons and a big fat rotating cube of a desktop.

Excellent.

Good news.  Glad you got things working.

---

