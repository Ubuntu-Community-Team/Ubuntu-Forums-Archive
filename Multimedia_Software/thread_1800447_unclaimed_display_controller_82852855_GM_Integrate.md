---
title: "unclaimed display controller 82852/855 GM Integrated Graphics Device"
date: 2011-07-09
forum: Multimedia Software
---

### Post by 3bsalcedo on 2011-07-09
I need help! I'm new to ubuntu(linux) but I really wanna use the OS. I wiped my laptop and installed it but I can't change my screen resolution (it's stuck at 1024 X 768 and my refresh rate is at 0 HZ) I tried installing a driver that was for both the i9xx and i8xx chipset family but it doesn't look like it helped anything. I want to be able to play World of Warcraft Wrath of The Lich King but when I try it the way the computer is now the the frame rate is really really slow. I also need to fix my audio because there's crackling that comes from the speakers often.
I attached a screen shot of what I get when I enter the command: sudo lshw -c video
Changing the resolution isn't the problem so much as the fact that I can't change the refresh rate from "0 HZ" to anything higher so that my game will play smoothly. I would also like to put compiz fushion on my laptop as well but I don't believe it will work unless I resolve this problem. Any help would be much appreciated, thanks.

---

### Post by 3bsalcedo on 2011-07-17
Can anyone help me out with my unclaimed drivers!? Please! I've tried using a source file of the driver I need for linux but after extracting the folder from the tar ball and I 'cd' into the folder and I try to use the command 'sudo ./configure' it doesn't work and says "command not found" and I see that there is no configure file in the folder,however there is a 'configure.ac' file but when I try the 'autoconf' command I get an error saying I need to install xorg-macros 1.8 or later but i'm sure I have it installed..i'm lost on what to do and I have several devices that are unclaimed when I run the command 'sudo lshw'. I need help, please!!

---

### Post by BicyclerBoy on 2011-07-18
From what I understand the unclaimed device is not your problem..I think this message is referring to a 2nd unused wired port.
My netbook (945GME) has the same result to lspci etc..

The lspci output shows the i915 driver is being used...(correct).

Compiling the intel driver is not a trivial undertaking & I would avoid it like the plague.
I would try the xorg-edgers ppa for the latest intel driver & Xorg.

---

### Post by 3bsalcedo on 2011-07-18
> **BicyclerBoy said:**
> From what I understand the unclaimed device is not your problem..I think this message is referring to a 2nd unused wired port.
My netbook (945GME) has the same result to lspci etc..

The lspci output shows the i915 driver is being used...(correct).

Compiling the intel driver is not a trivial undertaking & I would avoid it like the plague.
I would try the xorg-edgers ppa for the latest intel driver & Xorg.

I'm sure I already have the most recent intel driver but if display 1 is referring to the external monitor port on my laptop then why is it that I cannot change the resolution or the refresh rate? It seems like I should have a refresh rate higher than 0 HZ.

---

### Post by BicyclerBoy on 2011-07-19
The 0 Hz can not be real but some incorrect reporting.
Why do you get this info from ?

You could post (as attachments) your
/var/log/Xorg.0.log

outputs from:
xdpyinfo | head
glxinfo | grep glx
xrandr -q

---

### Post by 3bsalcedo on 2011-07-20
> **BicyclerBoy said:**
> The 0 Hz can not be real but some incorrect reporting.
Why do you get this info from ?

You could post (as attachments) your
/var/log/Xorg.0.log

outputs from:
xdpyinfo | head
glxinfo | grep glx
xrandr -q

I got the resolution and refresh rate info from the "Monitors" program under the tabs "System>Prefrences>Monitors" and I should be able to change my resolution and refresh rate there but I can't. I attached the files you were asking for.

---

### Post by BicyclerBoy on 2011-07-20
Looks to me that you are running the vesa driver & not the intel (i915). That explains why you are stuck at 1024x768.

You could edit your /etc/X11/xorg.conf file with a device section with Driver  "intel".
If the file does not exist then run Xorg -configure & then edit the file

xorg-edgers ppa versions Xorg.
X.Org version: 1.10.2.902

---

### Post by 3bsalcedo on 2011-07-21
I uninstalled the Xorg Vesa driver from the software center. I don't have an xorg.conf file and it fails to make one when I try to. I press ctrl + alt + f1 to get the the black screen and login as root then I use the command 'stop gdm' before I can run the command 'Xorg -configure' but 'Xorg -configure' gives me "configuration failed" when the command is all done running. Other than a couple of modules failing to load it says "number of created screens does not match number of detected devices" and in the end it makes an xorg.conf.new file in the root directory. can I use this file or do I need to figure out why 'Xorg -configure' failed and get the command to run without failing?

---

### Post by BicyclerBoy on 2011-07-21
You are logging in as user on a console terminal.

You should have used
[sudo] service gdm stop
[sudo] Xorg -configure

could then
[sudo] modprobe i915
[sudo] service gdm start

---

### Post by 3bsalcedo on 2011-07-21
I will try that, thanks. The process I used before was compiled from reading several different things online.

---

### Post by 3bsalcedo on 2011-07-21
> **BicyclerBoy said:**
> You are logging in as user on a console terminal.

You should have used
[sudo] service gdm stop
[sudo] Xorg -configure

could then
[sudo] modprobe i915
[sudo] service gdm start

When I used 'sudo service gdm stop' in the console terminal signed in with my user account, the whole screen changed to a black screen with text saying several different things like:

"* Starting the Winbind daemon winbind"
"* Starting Bluetooth"
"* PulseAudio configured for peer-user sessions"
"saned disabled; edit /etc/default/saned"
"Enabling additional executable binary formats binfmt-support"

Then it just left the cursor there so I tried typing the next command, 'sudo Xorg -configure' and nothing happend so I ctrl+alt+f1 to get to the screen with the prompt and I logged in and ran the command 'sudo service gdm start' to get the GUI back.

---

### Post by BicyclerBoy on 2011-07-21
And did you modprobe the i915 driver ?

What is in the /var/log/Xorg.0.log ?  (please attach as Xorg.0.log.txt)..

It is possible your install is partly broken or re-configure did not happen when removing the vesa driver..
This should not do any harm..
[COLOR=Black]
[/COLOR][COLOR=Black]dpkg-reconfigure xserver-xorg[/COLOR][COLOR=Black]

if this does not work then..[/COLOR]
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by 3bsalcedo on 2011-07-21
I didnt modeprobe cause it had taken me to the black screen with just text on it when I put the command 'sudo service gdm stop'in the console terminal. When I had ctrl+alt+f1 to the other black screen with the cmd prompt I then tried the command 'sudo Xorg -configure' but I got the same results as last time that configuration had failed so I didn't bother doing the command 'sudo modprobe i915' because I didn't think it would work right so I just ran 'sudo service gdm start' to get my GUI back.

Im attatching the Xorg.0.log in .doc format. The forum won't let me post it in .txt format because the file size is to large.

---

### Post by BicyclerBoy on 2011-07-22
The forum editor seems to be "Word" based..continually messes up formatting.

It is likely that Xorg -configure will fail if intel driver is not loaded first.

Try to install
xserver-xorg-video-intel
(xorg-edgers 2.15.0+git20110714.212fa986-0ubuntu0sarvatt~natty)


The console screen changes from stopping gdm are probably nothing to be concerned about..
But the nVidia X server does not do this when gdm is stopped.
It could be a good idea to logout of GUI (console 7) before logging into console 1..that may stop the console switching..

Your log file shows that the video driver is now swrast ? but not i915..

You could just make your /etc/X11/xorg.conf file from this
```

Section "Module"
#        Load          "dri"
#        Load          "glx"
EndSection

Section "DRI"
    Group "video"
    Mode 0660
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
#        Option          "AccelMethod" "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by 3bsalcedo on 2011-07-22
I checked on my Synaptic Package Manager and I already have the latest xserver-xorg-video-intel package installed, the same one you were talking about so I marked it for reinstallation.

Should I now make my /etc/X11/xorg.conf file from the code you have provided, and if so would that be all I would need to do or would I need to go through the process as I have done before to run the command 'sudo Xorg -configure' again?

---

### Post by BicyclerBoy on 2011-07-22
Just reboot after creating/editing xorg.conf file..
It is possible to restart X server but easier to just reboot.

---

### Post by 3bsalcedo on 2011-07-22
Ok I will try that, thank you. Should this solve my problem or will there be more involved?

---

### Post by BicyclerBoy on 2011-07-22
Should not be any thing else involved but the problem should not have been in the first place.

I don't know why the intel driver did not claim the h/w from the start..
Must be some udev rule that is out-dated.

Using Xorg -configure was just an attempt to avoid having to create xorg.conf file.

I would still use the xorg-edgers ppa for the driver.

---

### Post by 3bsalcedo on 2011-07-23
so when I made the xorg.conf file from the code you provided and rebooted and tried to click on the applications tab it just showed the whole bar that would normally show up with other tabs, as a black box. If I tried to open the computer shortcut on my desktop, the window opens as a black box as well. When I try and cursor over the boxes I can occasionally make out the contents because it flashes(showing up then going back to being a black box over and over again at different random intervals as I cursor over it). I managed to get the monitors tab open and through the flashing I could tell that it was now recognizing my monitor as "Laptop" instead of "Unknown" like it was before. The resolution looks like it can be changed and the refresh rate is showing as "60 HZ" instead of "0 HZ" but I can't really do anything because whatever I open comes up as a black box or parts of the screen start turning black as I'm right or left clicking places.

---

### Post by BicyclerBoy on 2011-07-23
Sounds like the desktop rendering/effects are not working correctly with the driver..
Are you using unity 3d or classic desktop ?
 
Maybe you need to uncomment the three lines prefixed with "#" but I doubt it..
Because the (2) lines in the modules section are automatically loaded.
And the 3rd commented line [EXA | UXA] controls the level of h/w acceleration used. 

Post your Xorg.0.log again..
And unless you are using the xorg-edgers ppa we are just wasting our time.

Your laptop is not an optimus graphics beast ?

---

### Post by 3bsalcedo on 2011-07-23
I'm sure I'm using the most recent xorg-edgers-intel driver. I had added the xorg-edgers ppa repo a while back and I've tried updating my packages through the synaptic package manager.

My laptop is a compaq pressario 2209cl with mostly intel chips. I had to use the terminal on window 1 to copy the Xorg.0.log to my usb drive so that I could upload it from another computer because window 7(the GUI) is pretty much unusable the way it is right now.

I just realized that I can't see the file on my usb drive because I copied it to my usb as root because it wouldn't let me copy it using 'sudo'. Every time I tried to copy the file as my user using 'sudo' it told me "permission denied". I'm working on getting the file on my usb drive now.

---

### Post by BicyclerBoy on 2011-07-23
That's an old intel extreme(ly bad) graphics laptop..
I think the driver is the same (i915) as it supports 852GM.

Maybe your user is not a member of the required groups...
I'm not sure which group is related with USB sticks & media..
Windows will not respect the file permissions on the USB stick so the file must not be there.
Could use your windows box to fix the file permissions on the USB stick (windows fat32 does not have any permissions).

Graphics Driver:
Your user should be in the video group..
To recover from the current state you can console login (as a user) & rename/delete the xorg.conf file

Make a local copy of the log file & then fix the xorg.conf file..
sudo cp /var/log/Xorg.0.log ~/Documents/Xorg.logfile

to edit..
sudo nano /etc/X11/xorg.conf
to backup..
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
to delete..
sudo rm /etc/X11/xorg.conf

---

### Post by 3bsalcedo on 2011-07-23
Ya I had thought about renaming the xorg.conf file but I was being more difficult by just trying to copy the file to my USB drive through the command prompt, but I got it. I needed the practice of using the command prompt anyways because im learning linux in one of my classes right now.

---

### Post by 3bsalcedo on 2011-07-23
So should I backup and remove the Xorg.conf file or should I back up and edit it, removing  the # commented lines?

---

### Post by 3bsalcedo on 2011-07-23
I backed up my Xorg.conf file and my xorg.0.log file and tried removing the comments from the Xorg.conf file but it didn't help anything so I removed the Xorg.conf file so that I can use the GUI again without getting black boxes everywhere. After that, I went to the xorg.0.log file and noticed it went from using the i915 driver back to using the swrast driver. I'm attaching the current(after removing the Xorg.conf file) xorg.0.log file named xorg.0.log.doc and I will also attach the old log file(from when I was using the Xorg.conf file that I made from your code where it was using the i915 driver) named xorg.logfile.doc

---

### Post by BicyclerBoy on 2011-07-23
Your Xorg log file (from post #23) tells you that the intel driver loaded just fine (AFAIK)
glx & dri,dri2 modules loaded..

The only warning is
[    23.269] (WW) intel(0): Textured video not supported on this hardware
That is normal as is supported post i915..

The reported EDID modelines show the max (native) panel LVDS resolution is 1024x768.

So it should be working perfectly..

What kind of fiddling with users /groups desktop managers & effects have you been doing ?
Did you check your user groups ?

---

### Post by 3bsalcedo on 2011-07-23
> **BicyclerBoy said:**
> Your Xorg log file (from post #23) tells you that the intel driver loaded just fine (AFAIK)
glx & dri,dri2 modules loaded..

The only warning is
[    23.269] (WW) intel(0): Textured video not supported on this hardware
That is normal as is supported post i915..

The reported EDID modelines show the max (native) panel LVDS resolution is 1024x768.

So it should be working perfectly..

What kind of fiddling with users /groups desktop managers & effects have you been doing ?
Did you check your user groups ?

I wish that were so but the problem is that the screen is broken(missing sections of the top task bar and completely missing the bottom task bar) and has black boxed sections/areas and if I manage to click on something that I manage to see on my desktop, it opens up as a black window and as I cursor around It will sometimes flash in areas or sections of the window so that I can see whats there but only for a second as it flashes.

---

### Post by BicyclerBoy on 2011-07-23
I know I was wishing it were so...

Sounds like a driver bug/regression on old h/w.
There may be some way to turn off certain driver functions but any intel driver info is hard to find.
You could post/search on the driver forum but I think it is futile.
[http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

Recent changes with Xorg means just finding an old copy of driver will fail with 11.04.

I would try install ubuntu 10.04 & see if the stock standard intel driver works.
Your h/w is never going to run unity 3d, & gnome classic 10.04 is not too different to 10.04.

Give up & use a $150 netbook.. faster graphics & same CPU, less power/heat.

---

### Post by 3bsalcedo on 2011-07-23
I thought I had mentioned before that when I had tried the 'sudo Xorg -configure' command and it failed, that it had made a file called "xorg.conf.new" but it didnt put it in /etc/X11. I was just looking at the file and it looks like its set up to use the intel driver so I'm woundering if it would work well if i renamed it and put it as /etc/X11/xorg.conf

I'll attach the file.

---

### Post by 3bsalcedo on 2011-07-23
lol I don't know if I wan't to give up just yet, I'm persistent. I don't have the money to get even a cheap $150 netbook but I know this laptop works well for how old it is. I ran WoW Wrath of the lich king on it when I was running WinXP and it ran pretty smooth, I was hoping to install it on ubuntu and run it but when I did it just ran way to slow. The audio was good but the screen was way behind, the refresh rate or fps was off or something. I had installed it through "wine". Maybe ill try ubuntu 10.04 instead if thats the case. Thanks.

---

### Post by BicyclerBoy on 2011-07-23
Worth trying the auto-generated xorg.conf file...but most if it is deprecated cruft.

---

### Post by 3bsalcedo on 2011-07-23
Ok ill give it a try.. I put the same version of ubuntu on my girlfriends laptop and there were no unclaimed devices(except for her wifi which I fixed easily) and her laptop is older than mine is. She has a dell inspiron 600m. I put the unity 2D desktop package on her laptop and the unity desktop and everything works fine. I'm not sure why my laptop would have so many problems compared to hers when mine is newer.

---

### Post by 3bsalcedo on 2011-07-24
It didn't help any using the xorg.conf.new file. It looked the same as the xorg.conf file I made from your code. I guess i'll be trying ubuntu 10.04 then. Hopefully with that version things will work and hopefully I can figure out how to get WoTLK to play smoothly. Thank you very much for all your help.

---

### Post by 3bsalcedo on 2011-07-24
I could still use your help. I burned ubuntu 10.04 netbook(lucid lynx I believe) on a CD and when booted into it, it seems like its loading files because it says ubuntu with dots that change color underneath it but after a while the screen goes black and then nothing. So I tried making it bootable from a usb drive and when booted from that I get a menu with options like: try ubuntu before install, install ubuntu, boot from first hard disk.. etc. so when I try install ubuntu it starts loading files but then after a bit when the screen goes black, there is text and at the bottom of the screen it says "can not mount /dev/loop1 on /cow" and It leaves the cursor there. If I start typing I noticed that I can enter commands like you can on the terminal but I don't know what to do. Would you be able to help?

---

### Post by BicyclerBoy on 2011-07-25
I have used the 10.10 netbook USB boot/installer..but never seen that problem.

Found this:
[http://www.pcmech.com/article/ubuntu-netbook-remix-9-10-usb-install-workaround/](http://www.pcmech.com/article/ubuntu-netbook-remix-9-10-usb-install-workaround/)

Guessing:
seems to relate to the exact setup of the USB boot process.
/cow might relate to supercow process/status or the live transferring of the mounted filesystem from USB to HDD.

---

### Post by 3bsalcedo on 2011-07-25
ok thanks. I'm trying what was suggested from the link you provided. I don't know why I wasn't able to install from the cd. It would just load files while on the "ubuntu" screen with the dots underneath it then after a while the screen would change to black and nothing would happen after that.

---

### Post by 3bsalcedo on 2011-07-25
I tried it the way the information from the link you provided suggested and tho it doesn't say what it did before it is now doing the same thing as when I try to install with the cd. the files load while it says ubuntu on the screen but when it's done(or so I think cuz it changes screens) the screen goes black and doesn't appear to do anything else.

---

### Post by BicyclerBoy on 2011-07-25
The transition from boot screen (console framebuffer driver) to X server GUI (Xorg & i915 driver) was a historical problem that has lots written about...

Try adding nomodeset to your Grub boot cmd.
You can do this from the Grub boot screen (non-permanent setting).

Another possibility is the old vesafb & intelfb drivers preventing X server starting..
The new intel driver (i915 etc) uses KMS & so can configure & control the console framebuffer before the X server is started.
Other than blacklisting the framebuffer drivers I do not know how to stop them.

Have a look in the file
/etc/modprobe.d/blacklist-framebuffer.conf
I have 28 lines including:
blacklist i810
blacklist intelfb
blacklist vesafb

Be aware that any changes to files in the modprobe.d/ folder will not be reflected in the boot image until you run
update-initramfs

---

### Post by 3bsalcedo on 2011-07-25
How do I add nomodeset to the grub boot cmd (Im guessing you are talking about the screen that loads up from the installer disc/usb drive, where it has the options: try ubuntu netbook without install, install ubuntu netbook, check disc for defects, etc.)

---

