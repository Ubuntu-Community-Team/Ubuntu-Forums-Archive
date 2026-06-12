---
title: "After installing NVIDIA drivers, boots directly to blank screen"
date: 2012-01-29
forum: Mythbuntu
---

### Post by ErWenn on 2012-01-29
I'm running Mythbuntu 11.10, and I just put in a new video card: a GeForce GT 430 (Fermi). My "monitor" is a brand new 40" Element edge-LED-backlit LCD TV, and I'm connected to it via HDMI. When I put in the new card and turned on the computer, I get the video card BIOS, then the motherboard BIOS, then a blank screen. There's a text cursor on the screen for about half a second and then nothing. The computer sounds like it's booting normally otherwise, but then it's just black. I can't get to see a grub menu by pressing repeatedly or pressing and holding <shift>.

I tried booting with an ordinary monitor plugged in to the VGA port, but I got the exact same behavior.

When I first installed this OS a couple weeks ago with a different video card (an old NVIDIA GeForce FX 5200), I had some the same problem immediately after the first reboot of the installation. I fixed it that time by reinstalling the whole damn thing with different graphics settings until I was able to see something (I think I ended up using the generic drivers, instead of the NVIDIA drivers). Then I installed the NVIDIA-common drivers and I was able to work from there.

So I tried that again (booted to the Mythbuntu install disk and chose to "upgrade" to a new install, with generic drivers), and I was able to boot to the GUI. But when I installed the NVIDIA-common drivers and rebooted, I ended up right back where I started.

If I <shift>+<ctrl><f1>, I can get a command line interface. (God, I wish I'd known that ages ago.)

I have looked around the web and tried a lot of different things, including trying to set nomodeset or api=off in the grub configuration file, blacklisting nouveau, purging all the NVIDIA drivers, deleting the Xorg.conf and restarting, reinstalling new Linux headers, and a few other things that I think I've forgotten.

Here are what seem to be the relevant lines from my Xorg.0.log file:

```

[    20.398] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:2:0:0. Please
[    20.398] (EE) NVIDIA(0):    check your system's kernel for additional error
[    20.398] (EE) NVIDIA(0):    messages and refer to Chapter 8: Common Problems in the
[    20.398] (EE) NVIDIA(0):    README for additional information.
[    20.398] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    20.398] (II) UnloadModule: "nvidia"
[    20.398] (II) Unloading nvidia
[    20.398] (II) UnloadModule: "wfb"
[    20.398] (II) Unloading wfb
[    20.398] (II) UnloadModule: "fb"
[    20.398] (II) Unloading fb
[    20.398] (EE) Screen(s) found, but none have a usable configuration.
[    20.398] 
Fatal server error:
[    20.398]  no screens found

```Can anyone give me a hand here?

UPDATE: So I tried one more thing I saw on another forum, resulting in a different problem. I used "hwinfo --framebuffer" to see what resolutions my video card supports. I picked one that was close to what my TV is supposed to be displaying (i.e. 1080p). The relevant line was:

```
Mode 0x031b: 1280x1024 (+5120), 24 bits
```31B in hex is 775 in decimal, so I edited the grub configuration file "/etc/default/grub" and changed the "GRUB_CMDLINE_LINUX_DEFAULT" line to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=775"
```Then I updated the grub configuration "sudo update-grub" and rebooted.

I got the Mythbuntu startup screen. Yay! Next, it decided to check the hard drive for errors. No problem!

But it never finished loading up the GUI. It's been sitting for about 30 minutes now on a screen with some text stuff. This is what the screen is displaying right now:

```

 * Starting NTP server ntpd                                                                                                                    [ OK ]
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                               * Starting web server apache2   [ OK ]
fsck from util-linux 2.19.1
ata_id[757]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument

/dev/sda1 has been mounted 31 times without being checked, check forced.
/dev/sda1: 148978/60923904 files (0.2% non-contiguous), 475187/243666176 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles                                                                                                                  [ OK ]
Loading the saved-state of the serial devices...
Checking for running unattended-upgrades:
 * Checking battery state...                                                                                                                   [ OK ]

```I'm about out of stuff to try now.



UPDATE2:

Okay, so upon subsequent reboots, I don't even get that splash screen anymore. It's back to just a black screen.

I tried a couple more things based on nickrout's suggestions and on other stuff I've seen online. You can see what I did in my replies below, but I'm repeating them here for those who are reading this for the first time:

> Try ```
sudo nvidia-xconfig
```I've done that quite a few times to no avail. But for  completeness's sake, I just did it again. Same problem (boot to blank  screen). I even went and undid the manual setting of  "GRUB_CMDLINE_LINUX_DEFAULT" in the grub configuration and then ran  nvidia-xconfig again. Still the same.

> and/or putting the correct horizontal sync and vertical refresh info into the xorg.conf file.                      I was able to find the vertical refresh rate for my TV (Element 40" Full  HD Digital LED TV (ELEFC401)) online (it's 60Hz), but I can't track  down any info about the horizontal refresh rate. (Neither are in the  manual for the TV.)

So I replaced the VertRefresh line in my xorg.conf file to:
     
         ```
VertRefresh     60.0 
```
and I left the HorizSync line the same:
     ```
HorizSync        28.0 - 33.0 
```
I saved xorg.conf and rebooted, but there was no change in symptoms.

Okay, so I did a little research and I was able to figure out that with a  60Hz refresh rate, the horizontal scan rate at 1080p would have to be  at around 61.7kHz. So I changed the relevant lines of my xorg.conf file  to:

     
         ```
VertRefresh     55.0 - 65.0     HorizSync        50.0 - 70.0 

```

No dice. Still booting to a blank screen.

Also, following another hint I saw online, I tried adding the line

```

         Option "MetaModes" "1920x1080" 

```
to the "Monitor" section of the xorg.conf file, but still no change.

Anyone have any other suggestions?

---

### Post by nickrout on 2012-01-29
Try looking in the log for xorg, which is /var/log/xorg.0.log

---

### Post by ErWenn on 2012-01-29
> **nickrout said:**
> Try looking in the log for xorg, which is /var/log/xorg.0.log
I'm not positive what you mean by that. I already posted the error messages from Xorg.0.log. Was there something else in that log that I should be looking for?

---

### Post by nickrout on 2012-01-29
> **ErWenn said:**
> I'm not positive what you mean by that. I already posted the error messages from Xorg.0.log. Was there something else in that log that I should be looking for?

Sorry, so you did.

Looks like it cannot get sufficient EDID info from the monitor/TV to know what resolution to use.

Try ```
sudo nvidia-xconfig
``` and/or putting the correct horizontal sync and vertical refresh info into the xorg.conf file.

---

### Post by ErWenn on 2012-01-29
> Try  	Code:
 	sudo nvidia-xconfig 
 

I've done that quite a few times to no avail. But for completeness's sake, I just did it again. Same problem (boot to blank screen). I even went and undid the manual setting of "GRUB_CMDLINE_LINUX_DEFAULT" in the grub configuration and then ran nvidia-xconfig again. Still the same.

> 
and/or putting the correct horizontal sync and vertical refresh info into the xorg.conf file. 	

Now this is something I haven't tried. Any ideas on how to find what the correct horizontal sync and vertical refresh would be? I'll poke around to see what I can dig up.

Thanks for your help!

---

### Post by nickrout on 2012-01-29
> **ErWenn said:**
> I've done that quite a few times to no avail. But for completeness's sake, I just did it again. Same problem (boot to blank screen). I even went and undid the manual setting of "GRUB_CMDLINE_LINUX_DEFAULT" in the grub configuration and then ran nvidia-xconfig again. Still the same.



Now this is something I haven't tried. Any ideas on how to find what the correct horizontal sync and vertical refresh would be? I'll poke around to see what I can dig up.

Thanks for your help!

your tv manual should tell you

---

### Post by ErWenn on 2012-01-29
I was able to find the vertical refresh rate for my TV (Element 40" Full HD Digital LED TV (ELEFC401)) online (it's 60Hz), but I can't track down any info about the horizontal refresh rate. (Neither are in the manual for the TV.)

So I replaced the VertRefresh line in my xorg.conf file to:
```

    VertRefresh     60.0

```

and I left the HorizSync line the same:
```

    HorizSync        28.0 - 33.0

```

I saved xorg.conf and rebooted, but there was no change in symptoms.

Any ideas as to how to figure out what the correct HorizSync value should be? I don't even know what range these things typically are, so I wouldn't even know where to start guessing.

---

### Post by ErWenn on 2012-01-30
Okay, so I did a little research and I was able to figure out that with a 60Hz refresh rate, the horizontal scan rate at 1080p would have to be at around 61.7kHz. So I changed the relevant lines of my xorg.conf file to:

```

    VertRefresh     55.0 - 65.0
    HorizSync        50.0 - 70.0

```

No dice. Still booting to a blank screen.

Also, following another hint I saw online, I tried adding the line

```

    Option "MetaModes" "1920x1080"

```

to the "Monitor" section of the xorg.conf file, but still no change.

Anyone have any other suggestions?

---

### Post by rodercot on 2012-01-30
HI,

 I just went through this on the weekend and I was completely ready to throw out the the setup and go back to 10.04. I have an P8H61-i and i3 2120 chip. Clean install of 11.10 and believe me I Searched everywhere for a fix. This is what I did

 Clean install - update all software after the first boot std - Then I added the x-swat ppa - sudo apt-get update - sudo apt-get upgrade. let it install those three files, reboot. Then goto the optional (additional) drivers selection under system in the toolbar if I recall (I am at work) and choose to activate the nvidia-current (NOT the nvidia-current-updates driver) driver there. This was on a clean install with nothing else loaded for nvidia other than the nouveau driver by default I guess.

 Finally reboot and you should have a nice clean screen with 290.10 installed. 

 I did not blacklist anything on this install, I did not run nvidia-xconfig or any of that. The weird thing after all this is that if I look in the Xorg.0.log it looks the nouveau driver is still loading as well as the 290.10 driver but the system is using the 290.10 driver which is what I wanted and after two days of solid pain I was not going to muck with it. 

 I have to say these two new version of buntu natty and oneiric have to be the worst. I do not mind upgrading software but when I basically have to relearn EVERYTHING everytime I do and then full of bugs or workarounds it's just too much. Like the suspend resume issue with the H61, H67, P67 boards acpi VER.5.0 boards. I sure hope 12.04 is solid but not if it is shipping with the 3.2 kernel as the suspend fix is just being added to the 3.3rc version kernels. I am waiting for 3.3rc2 to get the patched commits to fix it and no backports that I know off yet. 

 Sorry for the rant hope it helps.
 
 rgds,

 Dave

---

### Post by ErWenn on 2012-01-30
Thanks for the suggestion rodercot. I'm going to try that next.

But before I read this, I tried a few more changes to the xorg.conf file with no help and then I had the thought that if I couldn't even see the grub menu, then maybe the problem is lower-level than something that could be fixed in xorg.conf.

Of course, I don't really know what I'm talking about, as I'm not *that* versed in Linux. (I'm the sort of person that has to do a Google search to remember how to delete directories, if that gives you a vague idea of where I'm coming from.)

---

### Post by rodercot on 2012-01-30
Grub - Boot menu is not shown by default. you have to hold down your shift key after post to get it unless you have done something the system like repair a grub boot config from a livecd or the like. Your problem is not low level it is well documented, driver installs reboots to a scaled driver not loaded but restricted gui, in the old days we would at that point sudo nvidia-xconfig and reboot to a full scaled 1920x1080p desktop and then edit the xorg.conf to what we needed. Now it's not like that issuing sudo nvidia-xconfig causes a black screen but the system is still running as you can access it from a putty (ssh) session across the network. All this is just FYI for you. As a new user I suggest doing the above in my post only, you can get yourself in deep doo-doo pretty quick issuing commands from all the posts you read across the internet.

 Rgds,

 Dave

---

### Post by ErWenn on 2012-01-30
> **rodercot said:**
> HI,

 I just went through this on the weekend and I was completely ready to throw out the the setup and go back to 10.04. I have an P8H61-i and i3 2120 chip. Clean install of 11.10 and believe me I Searched everywhere for a fix. This is what I did

 Clean install - update all software after the first boot std - Then I added the x-swat ppa - sudo apt-get update - sudo apt-get upgrade. let it install those three files, reboot. Then goto the optional (additional) drivers selection under system in the toolbar if I recall (I am at work) and choose to activate the nvidia-current (NOT the nvidia-current-updates driver) driver there. This was on a clean install with nothing else loaded for nvidia other than the nouveau driver by default I guess.

 Finally reboot and you should have a nice clean screen with 290.10 installed. 

 I did not blacklist anything on this install, I did not run nvidia-xconfig or any of that. The weird thing after all this is that if I look in the Xorg.0.log it looks the nouveau driver is still loading as well as the 290.10 driver but the system is using the 290.10 driver which is what I wanted and after two days of solid pain I was not going to muck with it. 

 I have to say these two new version of buntu natty and oneiric have to be the worst. I do not mind upgrading software but when I basically have to relearn EVERYTHING everytime I do and then full of bugs or workarounds it's just too much. Like the suspend resume issue with the H61, H67, P67 boards acpi VER.5.0 boards. I sure hope 12.04 is solid but not if it is shipping with the 3.2 kernel as the suspend fix is just being added to the 3.3rc version kernels. I am waiting for 3.3rc2 to get the patched commits to fix it and no backports that I know off yet. 

 Sorry for the rant hope it helps.
 
 rgds,

 Dave
By the way, I'm not quite sure what you mean by "x-swat ppa".

---

### Post by ErWenn on 2012-01-30
> **rodercot said:**
> Grub - Boot menu is not shown by default. you have to hold down your shift key after post to get it unless you have done something the system like repair a grub boot config from a livecd or the like. Your problem is not low level it is well documented, driver installs reboots to a scaled driver not loaded but restricted gui, in the old days we would at that point sudo nvidia-xconfig and reboot to a full scaled 1920x1080p desktop and then edit the xorg.conf to what we needed. Now it's not like that issuing sudo nvidia-xconfig causes a black screen but the system is still running as you can access it from a putty (ssh) session across the network. All this is just FYI for you. As a new user I suggest doing the above in my post only, you can get yourself in deep doo-doo pretty quick issuing commands from all the posts you read across the internet.

 Rgds,

 Dave
I'm doing the clean reinstall now, but in reference to this reply:

I'm not able to get the grub menu to appear (or anything past the BIOS  screen) by holding shift, nor by tapping shift repeatedly. (For a while,  I felt like my only option was booting from a CD, until I found the  <ctrl>+<alt>+<f1> command.)

In any case, since this was a clean install a couple weeks ago, I was  willing to experiment as the worst* case scenario was that I'd have to  another clean install. Even so, I like to have at least a vague idea of  what the suggestions I'm trying are supposed to do, so I'm not  completely stumbling blind here.

---

### Post by rodercot on 2012-01-30
before all this and after the clean install you should have a fully scaled X screen (GUI) working and your /var/log/Xorg.0.log should be showing that it using the nouveau driver; (you can google x-swat ppa to get some info about the ppa) THEN

 you need to open a terminal on your desktop and then enter or copy and paste this line. 

 sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

 now hit enter to accept the ppa then it will import the key add the ppa to your apt sources.list (where your install get it's software and updates from)

 now enter

 sudo apt-get update (enter) let it run

 then 

 sudo apt-get upgrade (Answer Y then enter) let it run. it will install a few files from the ppa x-swat. Then reboot as I said and install the additional drivers (nvidia-current)

 Dave

---

### Post by ErWenn on 2012-01-30
Bah, humbug.

So now I can't even do a a clean reinstall. I tried three times. Once it froze in the middle of the process, and twice, while it got through the install and asked me to reboot, upon rebooting, it got stuck. I've got a screen full of "starting" and "stopping" notices on the screen (looks like the last bit of the boot.log file). Most of them read [OK], with two [[COLOR=Red]fail[/COLOR]]s:

```

 * Starting automatic crash report generation                    [[COLOR=Red]fail[COLOR=Black]][/COLOR][/COLOR]
 .
 .
 .
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 .
 .
 .
 * Starting LightDM Display Manager                              [[COLOR=Red]fail[COLOR=Black]]
[/COLOR][/COLOR]
```[COLOR=Red][COLOR=Black]

It got stuck both times at the same place. I can <ctrl>+<alt>+<f1> to get a terminal, so I looked in the Xorg.0.conf file. It's got the same errors as before with the "Failed to initialize the NVIDIA GPU" and "Screen(s) found, but none have a usable configuration" nonsense, but there are a couple more warnings an errors earlier in the file:

```

[    25.25.562] (II) LoadModule: "nv"
[    25.25.562] (WW) Warning, couldn't open module nv
[    25.25.562] (II) UnloadModule: "nv"
[    25.25.562] (II) Unloading nv
[    25.25.562] (EE) Failed to load module "nv" (module does not exist, 0)

```and

```

[    25.762] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.762] (WW) Falling back to old probe method for vesa
[    25.762] (WW) Falling back to old probe method for fbdev

```Also, when I looked at the boot.log file, while it was very similar to what was on the screen, it doesn't have a [[COLOR=Red]fail[COLOR=Black]] message for "Starting LightDM Display Manager". It has an [ OK ] message, and then it continues on, with the last line being:

```

 * Stopping Userspace bootsplash                        [ OK ]

```I'm kind of at a loss here. Something is clearly wrong as I didn't have these problems with previous clean installations and that one time it froze up strikes me as really weird. I'm going to try to manually format the hard drive and then do another clean install next, but please let me know if anyone has any thoughts.


[/COLOR][/COLOR] [/COLOR][/COLOR]

---

### Post by ErWenn on 2012-01-30
[LEFT]Oh, also, if I force a reboot, I'm back to the blank screen on boot again.

[/LEFT]

---

### Post by ErWenn on 2012-01-30
Okay, so I didn't format the drive, but I did another clean install. Got a couple lines further in the boot process... made it all the way to

```

 * Checking battery state...                   [ OK ]

```

 before freezing up again.


*sigh*

---

### Post by nickrout on 2012-01-30
If it keeps freezing at different points you may have a hardware problem :(

---

### Post by rodercot on 2012-01-31
That is correct, I would run memtest and see what up with your ram. You should be able to do a CLEAN INSTALL off the live cd back to a nouveau driver installed desktop at full scale.

 Regards,

 Dave

---

### Post by ErWenn on 2012-01-31
Okay, so after I couldn't get to the GUI after the first reboot, I figured "what's the worst that could happen?" and followed your instructions anyway. Obviously, it didn't work. And then I might've tried something else, but I don't really remember at this time. So I turned off the computer and went to work. Came back today and turned it on to see if I could figure out what might be wrong with the hardware and suddenly everything worked. I mean everything. The NVIDIA settings had properly detected the exact make and model of my video card and my television and I was able to watch 1080p video with no problem.

Of course, I had a nagging sensation that it wouldn't work if I rebooted again, and that turned out to be right.

I'll go make a memtest boot disk, I mean boot... uh... boot stick?

---

### Post by nickrout on 2012-01-31
> **ErWenn said:**
> Okay, so after I couldn't get to the GUI after the first reboot, I figured "what's the worst that could happen?" and followed your instructions anyway. Obviously, it didn't work. And then I might've tried something else, but I don't really remember at this time. So I turned off the computer and went to work. Came back today and turned it on to see if I could figure out what might be wrong with the hardware and suddenly everything worked. I mean everything. The NVIDIA settings had properly detected the exact make and model of my video card and my television and I was able to watch 1080p video with no problem.

Of course, I had a nagging sensation that it wouldn't work if I rebooted again, and that turned out to be right.

I'll go make a memtest boot disk, I mean boot... uh... boot stick?

doesn't grub offer memtest any more?

---

### Post by rodercot on 2012-01-31
yes memtest should be on bootloader. Are you sure that it was the nvidia-current driver that loaded and not the nouveau driver.

 here are a link to another thread I posted to have a gander at the two links that are posted in there and that may help with your black screen as well. I could not take it anymore, I went back to Lucid and installed the new 3.3rc2 kernel on it and have the nvidia drivers working great, alsa 1.0.25 installed and I am working on lirc. OH ya suspend and resume is working on my Intel Sandy Bridge Test Rig. 

 [http://ubuntuforums.org/showpost.php?p=11653760&postcount=20](http://ubuntuforums.org/showpost.php?p=11653760&postcount=20)

 Dave

---

### Post by ErWenn on 2012-02-01
I'm still having trouble getting to the grub menu. Don't know why. No amount of holding or tapping <SHIFT> seems to bring it up.

Anyway, I ran memtest from a boot stick. Ran it all day long. Almost 9 passes and no errors. Is there anyway to do some kind of testing on the video card? That was the new piece of hardware.

> Are you sure that it was the nvidia-current driver that loaded and not the nouveau driver.

I'm pretty sure it's the nvidia-current driver. On the most recent install, I never got to the GUI* with the default nouveau drivers. I went and installed nvidia-current from command line a couple reboots before that one magic boot where everything worked. I spent some time looking at the NVIDIA settings menus, so I'm pretty sure those are the drivers I was running.

Having said that, this doesn't seem to have an effect on whether the GUI loads or not. So far, it's loaded with the new video card twice. Once after an "upgrade" installation using the nouveau drivers, before I activated the nvidia-current drivers. And once recently with the nvidia-current drivers.

It might be having some effect on the blank screen problem, though. I haven't seen just the blank screen in a while. It's mostly just stopping somewhere with a bunch of boot log messages on the screen, right after a message about the LightDM Display Manager or about checking the battery.

[SIZE=1]*I keep calling it "the GUI", but I'm pretty sure there's a better name for it. Is it just "X"?[/SIZE]

---

### Post by nickrout on 2012-02-01
> **ErWenn said:**
> I'm still having trouble getting to the grub menu. Don't know why. No amount of holding or tapping <SHIFT> seems to bring it up. it may be the control or escape key?> 

Anyway, I ran memtest from a boot stick. Ran it all day long. Almost 9 passes and no errors. Is there anyway to do some kind of testing on the video card? That was the new piece of hardware.



I'm pretty sure it's the nvidia-current driver. On the most recent install, I never got to the GUI* with the default nouveau drivers. I went and installed nvidia-current from command line a couple reboots before that one magic boot where everything worked. I spent some time looking at the NVIDIA settings menus, so I'm pretty sure those are the drivers I was running.
 the log (var/log/Xorg.0.log will be explicit about what driver is loaded. Read it.[/quote]
Having said that, this doesn't seem to have an effect on whether the GUI loads or not. So far, it's loaded with the new video card twice. Once after an "upgrade" installation using the nouveau drivers, before I activated the nvidia-current drivers. And once recently with the nvidia-current drivers.

It might be having some effect on the blank screen problem, though. I haven't seen just the blank screen in a while. It's mostly just stopping somewhere with a bunch of boot log messages on the screen, right after a message about the LightDM Display Manager or about checking the battery.

[SIZE=1]*I keep calling it "the GUI", but I'm pretty sure there's a better name for it. Is it just "X"?[/SIZE][/QUOTE]

It is X :)

Have you tried starting the display manager from the command line? ```
sudo restart lightdm
```

Or just X```
startx
```

---

### Post by ErWenn on 2012-02-02
> the log (var/log/Xorg.0.log will be explicit about what driver is loaded. Read it.

Duh. Should've thought of that. I checked. It's definitely the NVIDIA drivers.

It booted again to X this morning! Given that my few successful boots have always been right after the computer (which has now been named MikeTeavee because it's being such a little brat) was off for a long time, I'm starting to think it's an overheating problem.

(Honestly, every intermittent, completely unpredictable error I've had in any OS in the past has turned out to be an overheating problem, so I should've thought of that a couple days ago. I think I was distracted by the original blank screen problem, which I'm now starting to suspect was a separate problem entirely.)

I suspect it's the video card itself that's got the heating problem or it would've shown up with the older video card. But maybe it's possible that it's more to do with the port, as the old card was just straight up PCI and the new one is PCI Express (2.0? x16? I think? Probably doesn't matter.) Or I guess it could just be one of those things that happens when you're moving stuff around.

I want to be sure about the hardware problem as most of the hardware (motherboard, processor, RAM, video card, even the wireless network card) is less than a month old, and I can probably get it replaced without paying extra if I'm sure that that's what's gone wrong.

> Have you tried starting the display manager from the command line?  	Code:
 	sudo restart lightdm 
Or just X 	Code:
 	startx 




I have tried "startx", and it didn't work, but I honestly don't remember what the error message was. The next time it fails to boot normally, I'll try both of those things and report what happens.

I'll also see if I can ascertain the temperature of the video card. I think it's got its own BIOS, so I'll start there. (Man, I wish my IR thermometer was still working.) There must be a program for monitoring the temperature... anyone know what it is?

In the meantime, I'm going to leave it on for a while and see what happens. If it is an overheating problem, I wonder if it will manifest itself while it's running, or if it only seems to affect booting problems. I'm also going to see if I can figure out what the lightDM manager is actually supposed to do.

Thanks to both of you for sticking with me here.

---

### Post by rodercot on 2012-02-02
if you open nvidia settings in the gui or X as you called it later there is a thermal page for the gpu which gives it current temp. you can also google lm-sensors and read up on it. That is the program in linux the probes the temps if you have really new hardware then make sure it is supported with the latest version sometimes it is a bigger pain to get lm-sensors working than just checking the bios. There may be a gui version of it as well - google is your friend here. 

 Dave

---

### Post by nickrout on 2012-02-02
> **rodercot said:**
> if you open nvidia settings in the gui or X as you called it later there is a thermal page for the gpu which gives it current temp. you can also google lm-sensors and read up on it. That is the program in linux the probes the temps if you have really new hardware then make sure it is supported with the latest version sometimes it is a bigger pain to get lm-sensors working than just checking the bios. There may be a gui version of it as well - google is your friend here. 

 Dave

actually the correct command is ```
nvidia-settings -q GPUCoreTemp
```

---

### Post by ErWenn on 2012-02-02
Okay, so I let MikeTeavee run all day today and then came home to see if he would reboot. Before I did, I checked the GPU temperature using the NVidia settings and it was running at a balmy 26°C, so that didn't look like it was going to be an issue. I shut down the computer and a quick hand check seems to back up that reported 26°C. I turned him on and and expected, the boot process froze up. The last three or four failed boots have all ended at the same place, with only one message at the top of the screen (the numbers are different each time, of course):

```

[ 79.354080] init: lightdm main process (2026) terminated with status 1

```I rebooted and checked the BIOS settings and both the motherboard and CPU were in the 25-35°C range, so no trouble there.

Since the "NVIDIA graphics device" "failed to initialize", I can't use the nvidia-settings command. I just get:

```

ERROR: The control display is undefined: please run `nvidia-settings --help`
for usage information.

```Since the lightDM terminates, I can't restart it. "sudo restart lightdm" results in:

```

restart: Unknown instance:

```If I try "sudo start lightdm", it flips back over to the screen with the boot error message and adds another of the same message:

```

[ 499.898609] init: lightdm main process (234 terminated with status 1

```Running "startx" shows error messages similar to those that showed up earlier in the Xorg.0.log:

```

(==) Log file:"/var/log/Xorg.0.log", Time: Thu Feb 2 15:59:07 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
NVIDIA: could not open the device file /dev/nvidia0 (input/output error).
(EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:2:0:0. Please
(EE) NVIDIA(0): check your system's kernel log for additional error
(EE) NVIDIA(0): messages and refer to Chapter 8: Common Problems in the
(EE) NVIDIA(0): README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screens(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
at http://wiki.x.org
for help
Please also check the log file at "/var/log/Xorg.0.log" for additional informati
on.

ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

```Not sure what to check next.

---

### Post by nickrout on 2012-02-02
> **ErWenn said:**
> Not sure what to check next.

It tells you what to do next:

> (EE) NVIDIA(0): check your system's kernel log for additional error
(EE) NVIDIA(0): messages and refer to Chapter 8: Common Problems in the
(EE) NVIDIA(0): README for additional information.

---

### Post by rodercot on 2012-02-03
the issue with the nvidia-settings command is exactly why I mentioned lm-sensors that you could run across a ssh terminal even if X is not running knowing your issues I wanted you to be able to access the info in some manner.

 The reason for the errors in the log, I think if you look in the log you will see that the driver (290.10) did not load and nouveau will not load if it see an instance of the prop driver. 

 Did you have a look at the two links I posted previously they were fixes for this issue with "greeter" which is built into 11.10. 
 
 I rolled back to 10.04 after spending a ton of time working on this. I use JYA's repos anyhow and he has not created one for 11.10 yet so for me 10.04 is a better fit, I will test 12.04 once it comes out and maybe then it will be time to upgrade my 6 machines. All of this I do on my test machined not production system.

 Dave

---

### Post by ErWenn on 2012-02-03
> It tells you what to do next:

[QUOTE]
 	```

(EE) NVIDIA(0): check your system's kernel log for additional error
(EE) NVIDIA(0): messages and refer to Chapter 8: Common Problems in the
(EE) NVIDIA(0): README for additional information.
[\CODE]
[\QUOTE]
[\QUOTE]

Since I'd seen this before, I'd already looked through the kernel.log and I wasn't able to find anything useful. Just now, I grepped that monster of a log (/var/log/kern.log) for nvidia and lightdm and only the following lines seem relevant:

[CODE]
nvidia: module license 'NVIDIA' taints kernel
nvidia 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
nvidia 0000:02:00.0: setting latency timer to 64

init: lightdm main process (2037) terminated with status 1

```

I haven't the slightest clue where to find the README. Any ideas?

[QUOTE]
The reason for the errors in the log, I think if you look in the log you  will see that the driver (290.10) did not load and nouveau will not  load if it see an instance of the prop driver. 

Unfortunately, even when I *didn't* have the nvidia-current drivers loaded and nouveau was loading, X was still failing to boot most of the time. I do think that had something to do with the blank screen problem, but that seems to be fixed now.

> Did you have a look at the two links I posted previously they were fixes  for this issue with "greeter" which is built into 11.10.

I did look at those links, but I don't currently have the unity-greeter program installed that they mentioned. I tried "sudo apt-get --purge remove unity-greeter", and I received the message "Package unity-greeter is not installed, so not removed".

I let MikeTeavee sit all night long and it still failed with the same "lightdm terminated with status 1" message. So my theory about X booting if you let it sit off for a long time isn't 100% true. Still, the few times X has booted have been after sitting for a long time, but temperature doesn't seem to be the issue. At least not the temperature of the motherboard, CPU, or GPU.

Bah.

---

### Post by nickrout on 2012-02-03
> **ErWenn said:**
> It tells you what to do next:


I haven't the slightest clue where to find the README. Any ideas?```
zless /usr/share/doc/nvidia-current/README.txt.gz
```

X does not "boot" - a computer boots. X starts (or doesn't start in your case :(

---

### Post by ErWenn on 2012-02-03
Thanks for helping me find that readme. Unfortunately, there's nothing in there relevant to my problem in there. I even tried to increase the verboseness of the logging as indicated in the README ("startx -- -verbose 5 -logverbose 5"), but that actually change what was logged.

---

### Post by ErWenn on 2012-02-03
If I try an older version, should I go back to 10.04 like you did, or just back to 10.10?

---

### Post by nickrout on 2012-02-03
10.04 is LTS

---

### Post by rodercot on 2012-02-04
LTS = Long Term Support from ubuntu. 

 I have been researching and I came across this thread which may help I am loading up a 2nd partition on my test machine right now with 11.10 to try as well. This has to get fixed there are FAR to many cases of this reported and google is the proof. 

 [http://ubuntuforums.org/showpost.php?p=11467050&postcount=797](http://ubuntuforums.org/showpost.php?p=11467050&postcount=797)

 There are a ton of hints in his posts and he has taken the time to write up a very large tutorial on black screens etc... and if you have the time reading through his stuff will be helpful along the way on any installs or upgrades. The one thing about that post that I question is do we do that on a fresh clean system or at least one single reboot. but it is worth a try. it may be better for you if we can get you going with 11.10 instead of 10.04. check out that thread. I should be ready to test his theories in about an hour once I get the system loaded and updated.
 
 rgds,

 Dave

---

### Post by ErWenn on 2012-02-04
> LTS = Long Term Support from ubuntu. 

Thanks. I was going to ask, but then I just Googled it.

 > I have been researching and I came across this thread which may help I  am loading up a 2nd partition on my test machine right now with 11.10 to  try as well. This has to get fixed there are FAR to many cases of this  reported and google is the proof. 

 [http://ubuntuforums.org/showpost.php...&postcount=797]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")

 There are a ton of hints in his posts and he has taken the time to  write up a very large tutorial on black screens etc... and if you have  the time reading through his stuff will be helpful along the way on any  installs or upgrades. The one thing about that post that I question is  do we do that on a fresh clean system or at least one single reboot. but  it is worth a try. it may be better for you if we can get you going  with 11.10 instead of 10.04. check out that thread. I should be ready to  test his theories in about an hour once I get the system loaded and  updated.
 

I'd seen that post before I posted here. I tried what I could from there, but it didn't get me anywhere.

I'm starting to think that I had two separate problems: the blank screen and the randomly failing to start X. I think I've solved the blank screen problem already as I haven't seen that symptom in a long time.

I burned a 10.04 installation disk last night, but my computer must've botched the burn because I can't boot to it. I'll try again tonight.

---

### Post by rodercot on 2012-02-04
Well I have been at this since 7 this morning and finally got a working x-server and nvidia-current driver. I followed along with that link (which I suggest you do as well from the start for the nvidia current drivers)I posted above for both the packaged drivers and the binary driver and nothing worked and I had NO errors in the Xorg.0.log file and the drivers were loading fine as well. I played with the xorg.conf files that I have as back-ups and just no luck at all. So finally I went over the syslog on a clean boot with a fine tooth comb and found this. 

 Oops: 0002 [#1] SMP

 generated by acpi polling the nvidia card and producing a stack trace and error with the card.

 you can try this and see if it works if not you can just remove it after.

 in /etc/modprobe.d creat a file called

 nvidia-graphics-drivers-options.conf

 and in that new file you want to put this line.

 options nvidia_current NVreg_RegisterForACPIEvents=0
 
 Then save the file and reboot. Hopefully it works for you.

 Dave

---

### Post by ErWenn on 2012-02-04
> **rodercot said:**
> Well I have been at this since 7 this morning and finally got a working x-server and nvidia-current driver. I followed along with that link (which I suggest you do as well from the start for the nvidia current drivers)I posted above for both the packaged drivers and the binary driver and nothing worked and I had NO errors in the Xorg.0.log file and the drivers were loading fine as well. I played with the xorg.conf files that I have as back-ups and just no luck at all. So finally I went over the syslog on a clean boot with a fine tooth comb and found this. 

 Oops: 0002 [#1] SMP

 generated by acpi polling the nvidia card and producing a stack trace and error with the card.

 you can try this and see if it works if not you can just remove it after.

 in /etc/modprobe.d creat a file called

 nvidia-graphics-drivers-options.conf

 and in that new file you want to put this line.

 options nvidia_current NVreg_RegisterForACPIEvents=0
 
 Then save the file and reboot. Hopefully it works for you.

 Dave

Tried it. No change.

Gonna try 10.04 now.

---

### Post by ErWenn on 2012-02-04
I feel like I'm going insane here.

I installed Mythbuntu 10.04. Had to burn the install disc twice as the first one didn't take.

Everything went fine, but my wireless network card (an Encore ENEWI-2XN42) wasn't recognized. So I downloaded Linux drivers from Encore's website. I made sure to get the "2.6.34 and earlier" version since Mythbuntu 10.04 came out just before 2.6.35. It took me about 2 hours to figure out how to install the damn drivers, but that's mostly just me not knowing enough about Linux.

Anyway, once I had internet access, I ran all the recommended updates from the update manager, rebooted, and then tried to install the NVidia drivers so that I could configure my display properly. Now every other version of Mythbuntu I've done this with had those drivers already downloaded and I just had to activate them. This time, I had to get them myself ("sudo apt-get install nvidia-current") and then install them ("sudo nvidia-xconfig") and reboot.

The computer boots. But before X starts, I get a blank screen with a cursor in the upper left corner. Every 5 seconds, the CLI login text flashes on the screen for an instant and then disappears. It just keeps doing this ad infinitum. <alt>+<ctrl>+<f1> doesn't seem to do anything.

I'm going to see if I can get into the grub menu and start in recovery mode or something, but I thought I'd let you know where I was.

---

### Post by ErWenn on 2012-02-05
After about 5 tries, I was able to get the GRUB menu loaded. Holding <shift> didn't seem to work, and repeatedly tapping shift only sometimes seems to work. It must be a really narrow window.

Anyway, I tried rebooting with graphics settings set to default and that didn't work. Still got to the blank-screen/flashing-login cycle.

The Xorg.0.log file has the same messages as it did before with 11.10. I now also have Xorg.1.log and Xorg.99.log files as well. the Xorg.1.log shows it trying a bunch of different resolution/refresh-rate combos and failing. I can post those contents if desired. None of the attempted resolutions are the appropriate 1080p, for some reason.

---

### Post by mabloom on 2012-02-07
It is possible that something being run when X starts is killing Xorg almost immediately if the nvidia driver is *used alone* (explanation below).

I've noticed with the more recent Xorg's,  that you don't actually need an [FONT="Courier New"]**xorg.conf**[/FONT] for nvidia cards.  In fact,  having one can do more harm than good in certain circumstances.

If you remove **[FONT="Courier New"]xorg.conf[/FONT]** (or never have one to begin with),  when Xorg starts, it will sequentially load just about every driver that it could possibly use for your hardware,  then use some heuristics to decide which is best, then unload everything else. Without an **[FONT="Courier New"]xorg.conf[/FONT]**, Xorg will start up with the native resolution, and you can use [FONT="Courier New"]**xrandr**[/FONT] to set it to something else

On my system it is essential for me to run *without* an **[FONT="Courier New"]xorg.conf[/FONT]**.

If I have an **[FONT="Courier New"]xorg.conf[/FONT]** that was created by the nvidia software (or even one handcrafted for the Nvidia hardware),  then as soon as I run certain programs, such as *[FONT="Courier New"]**emacs**[/FONT]* or *[FONT="Courier New"]**VirtualBox**[/FONT]* (or who knows what else), Xorg gets a segmentation violation (:evil:).  This has been a problem for me ever since I installed Ubuntu (at 10.04), and I discovered the following after upgrading to 11.04:

If, on the other hand, I do not have an **[FONT="Courier New"]xorg.conf[/FONT]**, after Xorg goes through the process of loading all those drivers and then unloading all of them except for nvidia-current,  something seems to get initialized:D that prevents emacs or Virtualbox (or who knows what else) from triggering an Xorg SEGV.

Of course, this does not help if you need to configure multiple monitors ](*,).

Interestingly, I do not need to remove **[FONT="Courier New"]xorg.conf[/FONT]** on an older system that has a card which requires the nvidia-96 driver. On that system,  Xorg never gets this SEGV.

---

