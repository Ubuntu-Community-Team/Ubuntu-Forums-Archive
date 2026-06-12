---
title: "running dual screen - video stationary?"
date: 2010-03-14
forum: Multimedia Software
---

### Post by duble08 on 2010-03-14
So I've been doing research on this for a while, and haven't been able to find a solution to what I've been trying to do.. I've got a home theater set-up going at my home, and i'm wanting to set up a dual screen setup with my laptop and my projector running Ubuntu 9.1 with an nvidia graphics card.  The way i want it set up is to be able to watch movies on my projector, and still be able to flip threw my different desktops on my laptop screen, while keeping the video stationary.  I'm currently using compiz to flip threw desktops.  I can get dual screen to work no problem using twinview, but when i switch desktops on my laptop, the video rotates with it - this means if i'm browsing the web on desktop 1 and instant messaging on desktop 2, and watching a movie on my projector, if i have the video open on desktop 2, then want to check the internet for something on desktop 1, the video rotates with it on the separate screen, meaning i can't watch my video if i'm doing anything on any other desktop than the one it has been opened on... is there anyway to setup the projector to be one desktop, and still cycle threw the desktops set up on the laptop screen without them interfering with each other?  I've spent a lot of money on my home theater and would love to see everything work out the way i visioned it.  Any help is greatly appreciated!! let me know if you need more info from my end.

Thank you!!

---

### Post by duble08 on 2010-03-18
anyone? does anyone even see my posts??? i never get responses on these things....

---

### Post by markbuntu on 2010-03-18
Twinview treats your monitors as one big screen so when you rotate the screen they both move. What you want is separate x-sessions for each monitor so they will be independently controllable. I am not a big nvidia fan so I don't know how to do that with the nvidia driver but if you do a search of the forums you will probably find a whole bunch of threads about it.

---

### Post by duble08 on 2010-03-18
thanks for the response! but like i posted earlier, i've been digging threw threads trying to find a solution, and haven't found one.  For some reason, the x-sessions set up that you're talking about doesn't work for me, for the following reasons...

1.  Whenever i try to enable it, it states that it requires a restart for the changes to take effect.  when i reboot, it goes back to single monitor, at which point i can either set it for twin view, or i can try to reset for x-sessions again, which upon reboot, does not work.

2.  x-sessions, from what i've read, seems to be more of a permanent dual screen set-up. by this, i mean to be able to turn it on and off, if it was to work, then i would have to reboot every time.  i don't always have my projector on when i use my laptop, so it would be nice if i could quickly enable/disable the secondary video (projector) "on the fly" so to speak without having to stop every other function i'm doing just to watch a video.

are there any other options, or ways to reconfigure my dual screen options to avoid the inconveniences, or am i just SOL?  i refuse to go back to winblows due to other issues i had with sound production with it, and ubuntu is perfect, if it wasn't for the dual monitor setup being inconvenient.

any other ideas?  is there maybe a way to configure things threw compiz?

---

### Post by GSF1200S on 2010-03-18
> **duble08 said:**
> thanks for the response! but like i posted earlier, i've been digging threw threads trying to find a solution, and haven't found one.  For some reason, the x-sessions set up that you're talking about doesn't work for me, for the following reasons...

1.  Whenever i try to enable it, it states that it requires a restart for the changes to take effect.  when i reboot, it goes back to single monitor, at which point i can either set it for twin view, or i can try to reset for x-sessions again, which upon reboot, does not work.

2.  x-sessions, from what i've read, seems to be more of a permanent dual screen set-up. by this, i mean to be able to turn it on and off, if it was to work, then i would have to reboot every time.  i don't always have my projector on when i use my laptop, so it would be nice if i could quickly enable/disable the secondary video (projector) "on the fly" so to speak without having to stop every other function i'm doing just to watch a video.

are there any other options, or ways to reconfigure my dual screen options to avoid the inconveniences, or am i just SOL?  i refuse to go back to winblows due to other issues i had with sound production with it, and ubuntu is perfect, if it wasn't for the dual monitor setup being inconvenient.

any other ideas?  is there maybe a way to configure things threw compiz?

Open a terminal and run:
```
sudo nvidia-settings
``` -or-
```
gksudo nvidia-settings
```
(Note: for some reason Ubuntu doesnt have the menu version of nvidia settings set as root, nor does it demand a password. As a result, settings you make will not be applied or saved. This is why Im having you open it as root).

In the left pane, go to the X Server Display Configuration section. If your projector is on, you should see your laptop monitor displayed as well as the projector. Select the projector and enable it. Afterwards, go to the Display tab under the Layout section and click on the configure button- select Seperate X screen. Afterwards, click apply. It will warn you that it cannot apply the settings without a restart of X. Finally, click the 'Save to X Configuration File.' This will ensure that your settings are saved for future ease of use. Then, restart X:
```
sudo /etc/init.d/gdm restart
```

Your projector should now work. Let us know what happens :)

---

### Post by markbuntu on 2010-03-18
This can be done with the latest ati drivers so surely the nvidia driver must be able to do it..or maybe not.

Are you using the nvidia-settings control app?

---

### Post by GSF1200S on 2010-03-18
> **markbuntu said:**
> This can be done with the latest ati drivers so surely the nvidia driver must be able to do it..or maybe not.

Are you using the nvidia-settings control app?

The problem with the Nvidia-settings app is that it is not run as root. It simply runs with user privileges and as such cannot modify the Xorg.conf to support dual screen operations. The solution is as simple as running it as root from the terminal, or putting gksudo before nvidia-settings in any launcher that one uses. I can see that this would be confusing for many people, especially those who are not familiar with Linux's concept of user privilege.

---

### Post by duble08 on 2010-03-19
i've tried the above mentioned advice in terminal, both ways, and this is what happens...

when i click apply, i get this message:
"Cannot Apply"
"The current settings cannot be completely applied due to one or more of the following reasons:

-The location of an X screen has changed.
-The location type of an X screen has changed.
-The color depth of an X screen has changed.
-An X screen has been added or removed.
-Xinerama is being enabled/disabled.

For all the requested settings to take effect, you must save the configuration to the X config file and restart the X server."

i then have two buttons to choose from - "Apply What Is Possible" and "Cancel".  I select "Apply What Is Possible"

Afterwards, i click "save to x configuration file"

When i click "save to x configuration file" i get this message in an error window:
"Failed to parse existing X config file '/etc/X11/xorg.conf'!"

I also recieve this message in the terminal:
"VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen"."

i get the same result with both terminal commands listed above -

"sudo nvidia-settings"
and
"gksudo nvidia-settings"

when i use the restart code afterwards, "sudo /etc/init.d/gdm restart", the GUI shuts down, throws me to terminal, and says something about how i should restart differently then with "/etc/init.d/" - at which point in time i reboot my comp with "ctrl+alt+del", because it just sits in terminal...  any suggestions?  and will i have to do this every time i turn on or off my projector, or plug it in/unplug it? this just seems like more work than it should be to watch a movie - there's got to be an easier way than to shut everything down every time.

Thank you for your help on this! hopefully we'll get it figured out!!

---

### Post by duble08 on 2010-03-22
anyone know how to get by the errors, or for other methods to accomplish what i'm trying to do?

---

### Post by AlexanderDGreat on 2010-03-24
> When i click "save to x configuration file" i get this message in an error window:
"Failed to parse existing X config file '/etc/X11/xorg.conf'!" - backup your xorg.conf first, then delete it, then make nvidia remake it.

[http://ubuntuforums.org/showthread.php?t=1101445]("http://ubuntuforums.org/showthread.php?t=1101445")

You really need that Nvidia Control Panel to make those xorg.conf's for you.

Yes you need Separate X Screens: here's where I found a solution: [http://www.regnumonline.com.ar/forum/showthread.php?t=35688]("http://www.regnumonline.com.ar/forum/showthread.php?t=35688") - the concept is you make your other monitor the main one, if it's giving you wrong resolutions, then edit the xorg.conf that nvidia generates from there.

I'm not sure myself how to play videos on the other Separate X screen, while browsing firefox or typing on the other, but I got those links above from 1 day of researching. Pls. post if you find the solution. Good luck to both of us! :)

---

### Post by AlexanderDGreat on 2010-03-24
talking about dual screen... ergo dual posts!

---

### Post by AlexanderDGreat on 2010-03-24
Hey I got it. You have to also **enable Xinerama** so you can watch movie on the other separate x screen and browse on the other, _I DONT'T use TwinView_ for the reason that my monitors are not the same resolutions.

Monitor1: 1280 x 800 (wide, 16:9)
Monitor2: 1280 x 1024 (non-wide, 4:3 or box)

Monitor1: <---1280--->
Monitor2: <---1280--->
no problems

However vertical:
Monitor1:
^
800
_

Monitor2:
^
^
1024
_
when I click something on the bottom of my monitor 1, it goes all the way down and my mouse disappears, this is the reason TwinView is not good for me, so instead I use Separate X screens. I hope you understand.

I'm not sure if I'm even addressing your question. Just for your information all these. :) good luck dude!


Maybe to help: my xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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

Section "ServerFlags"
    Option         "Xinerama" "1"
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
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 64.0
    VertRefresh     56.0 - 65.0
    Option         "DPMS"
EndSection



Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7150M / nForce 630M"
    BusID          "PCI:0:18:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7150M / nForce 630M"
    BusID          "PCI:0:18:0"
    Screen          1
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by duble08 on 2010-04-07
so i got the seperate x screen to work, but with very unsatisfying results.

1. only my usb mouse would work on both screens. the touchpad on the laptop would only work on the laptop screen

2. the keyboard would only function on the laptop screen

3. every application i opened only opened on the projector, which includes the terminal... instantly frustrating since the keyboard only worked on laptop screen - i could not work with anything

4. all the applications that opened (remember on projector only) for some reason i could not move or resize - they all seemed to lock onto the upper left part of the screen, without any title bar (meaning the close, maximize and minimize buttons failed to exist), which also made things very frustrating, since it eliminated my option to drag a screen to the laptop window to allow my keyboard to function with it

5. compiz didn't work at all - my multiple desktop functionality was completely shot - all my special enhancements were not functioning (such as 3d cube desktop, and multi desktop views)... basicaly i had only one desktop to work with (this was verified by looking at taskbar on the bottom right - only one screen was present) - i typically have 7 open - i'm quite the multi-tasker, which is why i really want this work

Is there any way to get things to work properly? like i said, my goal is to have the projector able to play videos/games of my choice, with no menus on the projector screen, and i'd like the desktop on the projector stationary, and i'd like the laptop screen to have all my functionality (e.g. menus, taskbar, icons, multiple desktops (that i can flip threw without affecting the projector desktop), compiz, ect...)

Another thing i don't like about seperate x screens, is it requires a restart to enable/disable the projector screen. *I would like to be able to enable the projector "on the fly" like you can with twinview, otherwise it's not an option that i'm willing to take. *rebooting my computer every hour/movie or so is really inconvienient, especially when you've got so many things running in the background like i usually do.

Is this an impossible task where ubuntu stands currently? i plan on upgrading to 10.4 when thats available.. hopefully that version will have some fixes... *lately i've been using twinview to get by, but that cripples my multi-tasking abilities, and it always seems to be a pain to get it to understand which screen to put my menus on - i usually have to keep fliping the settings around multiple times to get it to display right (changing screen from top to bottom, absolute, checking and unchecking main desktop).

thanks for your help!

---

### Post by duble08 on 2010-04-07
> **AlexanderDGreat said:**
> talking about dual screen... ergo dual posts!

i know there's other posts about dual screen setups, but none seem to address what i'm trying to accomplish.  it's not that i have errors getting it to connect, or nvidia/ati settings like many others post, i'm trying to accomplish a theater type setup.  i havn't seen any posts related to the specifics of what i'm seeking.  if you know of a post that does contain this information, please post a link - i have yet to find one.

Thank you!

---

