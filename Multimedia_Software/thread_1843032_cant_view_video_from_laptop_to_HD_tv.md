---
title: "cant view video from laptop to HD tv"
date: 2011-09-12
forum: Multimedia Software
---

### Post by mattpl1981 on 2011-09-12
i just installed ubunta and i cant view videos on my HD tv from my laptop. i tried to down load drivers from hp but ubunta isn't a supported os. can someone help figure out how i can hook my laptop up to my hd tv. thanks

---

### Post by papibe on 2011-09-12
What is your graphic card?

Could you post the result of:
```
sudo lshw -C display
```
Regards.

---

### Post by mattpl1981 on 2011-09-12
im not sure. its a hp dv8 1000 laptop. im new to ubunta and im trying to figure out how to get my laptop to show up on my HD tv thru hdmi. im also having trouble trying to figure out how to get itunes on here.

---

### Post by mattpl1981 on 2011-09-12
how do i figure out what kind of graphic card i have?

---

### Post by papibe on 2011-09-12
Run the command of my previous post in the terminal, and paste it in a new post.

Regards.

---

### Post by mattpl1981 on 2011-09-12
description: VGA compatible controller
       product: GT216 [GeForce GT 230M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:7000(size=128) memory:d3080000-d30fffff
matt@matt-HP-Pavilion-dv8-Notebook-PC:~$

---

### Post by mattpl1981 on 2011-09-12
when i installed i selected 32 bit bc it was recommended

---

### Post by papibe on 2011-09-12
> **mattpl1981 said:**
> product: GT216 [GeForce GT 230M]
Congrats! that's a very nice card: you have an Nvidia GT 230M.

In order to fully take advantage of your card, I would advice to install the Nvidia proprietary driver. Go to 'Additional Drivers' and install the Nvidia driver (current). Once it's installed, restart your machine.

Now, to setup a second monitor or a HDTV, run 'Nvidia X Server Settings'.

I hope this helps. Tell us how it goes.
Regards.

---

### Post by mattpl1981 on 2011-09-12
ok thanks but where do i go to install that?

---

### Post by mattpl1981 on 2011-09-12
i went to additional drivers and it says
 no proprietary drivers are in use on this system

this driver is activated but not currently in use so what do i need to do?

---

### Post by papibe on 2011-09-12
Which version of Ubuntu do you have?

If you have 11.04, press the super key (windows key) and type 'addi' that would be enough for the program's icon to appear.

If you have a previous version go to the main menu: System -> Administration -> Hardware Drivers.

Regards.

---

### Post by papibe on 2011-09-12
Follow this instructions to make sure it is installed: [How Do I Install My Video Card Drivers]("http://ubuntuforums.org/showpost.php?p=11210512&postcount=2")

Tell us how it went.
Regards.

---

### Post by mattpl1981 on 2011-09-12
it says i need to install this driver if i wish to use the unity desktop enable desktop effects, or run software that requires 3d acceleration, such as games. but how do you install this driver ? it only has a tab for remove

---

### Post by papibe on 2011-09-12
Then run the Nvidia X Server Setings:
```
$ gksudo nvidia-settings
```
Select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine.

Regards.

---

### Post by mattpl1981 on 2011-09-12
i went to Nvidia X Server Setings: and followed those intructions and its the same thing. its still not working. yeah i have 11.04 im about to try to type that code in the terminal

---

### Post by mattpl1981 on 2011-09-12
i typed that in and said command not found.

---

### Post by papibe on 2011-09-12
Unfortunately, there is a bug on the 'Additional Drivers' so it doesn't recognize when the driver is installed. If you run the command I gave you, save the X configuration file, and restart, you should be OK.
 
After that, connect you HDTV and open 'Nvidia X Server...', go to X Server Display Configuration and configure your displays.

Regards.

---

### Post by mattpl1981 on 2011-09-12
ok dont want to sound like a dummy here but im not big into computers so can u tell me how to run that command bc i went to the terminal and type that code it. lol i know thats not right so where do i type that code in at??

---

### Post by papibe on 2011-09-12
You run that command on a terminal:

Super key -> Terminal

The command will ask your password so you can run nvidia-settings as superuser, and save the config file in the proper directory.

Regards.

---

### Post by mattpl1981 on 2011-09-12
well i ran that command in the terminal and it said no command found

---

### Post by papibe on 2011-09-12
This command?
```
gksudo nvidia-settings
```
Regards.

---

### Post by mattpl1981 on 2011-09-12
yeah ive tried that and still nothing but now in the NVidia servings is shows my HD tv in the layout but it has (disabled) next to it

---

### Post by mattpl1981 on 2011-09-12
*settings

---

### Post by mattpl1981 on 2011-09-12
i can click on the tv display and i hit configure button and gives me an option of Seperate X screen (restart required) or twin view

---

### Post by papibe on 2011-09-12
You are getting closer!

Twin View is for either cloning your laptop display or extending it.

Separate X Screen is to create 2 independent screens (with bars, lauchers, and all).

Tell us how is going,
Regards.

---

### Post by mattpl1981 on 2011-09-12
well im going from my laptop to my tv so it will be for when i watch movies on my laptop to show up on the tv but ive tried both of those options and its still nothing. i went back to additional drivers and its still saying no proprietary drivers are in use on this system. it says proprietary drivers do not have public source code that ubuntu developers are free to modify. security updates and corrections depend solely on the responsiveness of the manufacturer. ubuntu cannot fix or improve these drivers. 

NVIDIA accelerated graphics driver (version current) {recommended}

says i need to install this driver and that this driver is activated but not currently in use.

---

### Post by nuclearj on 2011-09-13
I am having the same problem and thought i could piggy-back the thread.  Seems like there is no solution out there for the ATI Radeon HD 3200.

description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:29 memory:c0000000-cfffffff(prefetchable) ioport:7000(size=256) memory:d2400000-d240ffff memory:d2300000-d23fffff

---

### Post by papibe on 2011-09-13
> **mattpl1981 said:**
> 
NVIDIA accelerated graphics driver (version current) {recommended}

says i need to install this driver and that this driver is activated but not currently in use.
As I said before, that's a bug.

To make sure 100% that you are using the Nvidia driver, check [this]("http://ubuntuforums.org/showpost.php?p=11210579&postcount=6").

Regards.

---

### Post by mattpl1981 on 2011-09-13
how do you put the driver in use??

---

### Post by mattpl1981 on 2011-09-13
i typed that command in the terminal and it said no command found

---

### Post by mattpl1981 on 2011-09-13
and why is there a tab for "remove" in the additional drivers menu

---

### Post by mattpl1981 on 2011-09-13
is there a way to go to NVIDIA website and download the driver manually??

---

### Post by papibe on 2011-09-13
Yes, but I assure you that  generate more trouble than benefits.

Try again, paste this into a terminal and paste the result into a replay:
```
grep -i nvidia /var/log/Xorg.0.log
```
Regards.

---

### Post by mattpl1981 on 2011-09-13
matt@matt-HP-Pavilion-dv8-Notebook-PC:~$ grep -i nvidia /var/log/Xorg.0.log
[    11.053] (II) Module glx: vendor="NVIDIA Corporation"
[    11.053] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    11.054] (II) LoadModule: "nvidia"
[    11.054] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    11.055] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.055] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    11.055] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.056] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    11.056] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    11.056] (==) NVIDIA(0): RGB weight 888
[    11.056] (==) NVIDIA(0): Default visual is TrueColor
[    11.056] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.056] (**) NVIDIA(0): Option "TwinView" "0"
[    11.056] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    12.040] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    12.040] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    12.073] (II) NVIDIA(GPU-0): Display (VIZ SV470M (DFP-1)) does not support NVIDIA 3D Vision
[    12.073] (II) NVIDIA(GPU-0):     stereo.
[    12.075] (II) NVIDIA(0): NVIDIA GPU GeForce GT 230M (GT216) at PCI:1:0:0 (GPU-0)
[    12.075] (--) NVIDIA(0): Memory: 1048576 kBytes
[    12.075] (--) NVIDIA(0): VideoBIOS: 70.16.25.00.17
[    12.075] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    12.075] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    12.075] (--) NVIDIA(0): Connected display device(s) on GeForce GT 230M at PCI:1:0:0
[    12.075] (--) NVIDIA(0):     Chi Mei Optoelectronics corp. (DFP-0)
[    12.075] (--) NVIDIA(0):     VIZ SV470M (DFP-1)
[    12.075] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): 330.0 MHz maximum pixel
[    12.075] (--) NVIDIA(0):     clock
[    12.075] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): Internal Dual Link
[    12.075] (--) NVIDIA(0):     LVDS
[    12.075] (--) NVIDIA(0): VIZ SV470M (DFP-1): 165.0 MHz maximum pixel clock
[    12.075] (--) NVIDIA(0): VIZ SV470M (DFP-1): Internal Single Link TMDS
[    12.144] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    12.145] (II) NVIDIA(0): Validated modes:
[    12.145] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    12.145] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    13.216] (--) NVIDIA(0): DPI set to (118, 119); computed from "UseEdidDpi" X config
[    13.216] (--) NVIDIA(0):     option
[    13.217] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    13.227] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    13.570] (==) NVIDIA(0): Disabling shared memory pixmaps
[    13.570] (==) NVIDIA(0): Backing store disabled
[    13.570] (==) NVIDIA(0): Silken mouse enabled
[    13.571] (**) NVIDIA(0): DPMS enabled
[    13.572] (II) NVIDIA(0): [DRI2] Setup complete
matt@matt-HP-Pavilion-dv8-Notebook-PC:~$

---

### Post by papibe on 2011-09-13
100% sure, you are using the nvidia driver.

Then, what is left is to configure your TV out.

Are you able to see the 2 monitors connected on the Nvida X Server Settings?

Regards.

---

### Post by mattpl1981 on 2011-09-13
now i went to NVIDIA display configuration and set it to twin view and then saved to x config file and now its showing the background but thats it. nothing esle. but its still saying in additional drivers that my driver isnt in use. thoughts?

---

### Post by mattpl1981 on 2011-09-13
yeah its showing my two screens in the layout

---

### Post by mattpl1981 on 2011-09-13
just saw on x server xvideo settings at the bottom there is a box saying sync to display device
the box that was selected was chi mei opt but right under it was VIZ SV470 (DPF-1) which is my tv i just selecting that box but still nothing new. should i restart or what do u think?

---

### Post by mattpl1981 on 2011-09-13
im just guessing that is my tv since its a vizio

---

### Post by papibe on 2011-09-13
> **mattpl1981 said:**
> ...but its still saying in additional drivers that my driver isnt in use. thoughts?

As I said before, that's a bug: the ability to detect the installation of the driver, not the use the driver itself.

We have already confirm that you are using the Nvidia proprietary driver.

Now to business:

In order to connect the 2 displays:
[LIST]
[*]Connect the cable to the TV.
[*]Switch the TV to the proper input (for example HDMI1).
[*]Open 'Nvidia X Server settings'.
[*]From the list of the right select 'X Server Display Configuration.'.
[*]Now on the right, select the rectangule that represents the TV.
[*]Press the button 'Configure' below.
[*]Select Twin View.
[*]Press the button aplay (a little below).
[*]In a couple of seconds it should appear an image on the TV's screen.
[/LIST]
Tell me how it goes,
Regards.

---

### Post by mattpl1981 on 2011-09-13
and what should the GPU scaling method be on stretched, centered, or aspect ratio scaled??

---

### Post by papibe on 2011-09-13
Don't modify those values just yet, let's try to use the defaults for now.

Regards.

---

### Post by mattpl1981 on 2011-09-13
ok its showing my background of my computer on the tv now but nothing else, no icons, no windows, just background

---

### Post by mattpl1981 on 2011-09-13
should i hit save to x configuration?

---

### Post by papibe on 2011-09-13
> **mattpl1981 said:**
> ok its showing my background of my computer on the tv now but nothing else, no icons, no windows, just background

Yahoo!!

That's how it looks the Twin View option, it's OK (although more tweaking can me done).

Now, regarding the saving of the configuration file: Do it **only if** you are going to keep the TV connected **ALL** the time.

If you are going to connect your TV every once in a while DO NOT. Once you need it, just repeat the previous steps.

Good Night,
See you tomorrow around the forums.
Kind Regards.

---

### Post by mattpl1981 on 2011-09-13
ok thank you so much, you helped me out alot. i figured it out. i just needed to drag the windows over out of the screen to get to my tv. only thing i need to figure out now is the audio bc is coming out of my computer instead of from the output of my tv. well you have a good nite and thanks again for your help.

---

### Post by papibe on 2011-09-13
In order to have audio through your hdmi connection, you need to change the default output on Sound Preferences.

Follow [this very nice tutorial]("http://ubuntuforums.org/showthread.php?t=1741294&highlight=hdmi+audio") (with pictures!).

Good Luck,
Regards.

---

### Post by mattpl1981 on 2011-09-13
thanks

---

### Post by mattpl1981 on 2011-09-13
what is the difference between the twin screens and Seperate X display??

---

### Post by papibe on 2011-09-13
Twinview has 2 main settings:
[LIST]
[*]Clone your desktop: having the same view on both monitors.
[*]Expand your desktop: a virtual big screen the starts on one monitor and continues in the other.
[/LIST]
You can virtually array the monitors in this four layouts: 
[LIST]
[*]RightOf (the default).
[*]LeftOf
[*]Above
[*]Below
[/LIST]
You can move windows from one monitor to the other (because it is one big virtual screen).

On the other hand, 'Separate X Screen' works in just one way: you have 2 independent screens, with menus included. You can't move windows from one to another, since they are not linked.

I hope this clarify things a but for you,
Regards.

Note: I haven't tried 'Separate X Screens' in Unity (11.04) yet. I don't know if it is supported (in Classic Gnome should definitely work).

---

