---
title: "Automating nvidia-settings tool"
date: 2010-08-22
forum: Multimedia Software
---

### Post by thieTe4l on 2010-08-22
[B]What it is about:

[/B][INDENT]The nvidia-settings tool is a great GUI enabling on-the-fly configuration of Monitors/TV/Projector without X-restart on nvidia-cards. It's possibilities go beyond a whatsoever sophisticated Xorg.conf. Unfortunately, if you use some specific setups all the time, there is no obvious way to use the functionality of nvidia-settings tool automated, by means of a script or something similar. 

In my case, I wanted to toggle between two different Twinview setups involving 3 Monitors, one setup with 2 Monitors attached, TV-out disabled, the other with one Monitor attached and the TV-out enabled.

The solution I came up with is not very obvious, took a while and lots of research, but I can shed some light on this issue now.[/INDENT][B]
What it is not about:[/B][INDENT]Getting a Twinview configuration to work.[/INDENT]**The Problem in more detail:**[INDENT]
In a proper Xorg.conf no more than 2 outputs can be defined at the same time, for one server layout. You can, however, define 2 other outputs in an additional server layout section, but then you cant switch between them dynamically. This disables using Ctrl-Alt-+/- for a setup involving more than 2 outputs (DVI DVI TV-OUT, so 3, in my case).

XRandR: This is, as far as I can see, the utility which *should* enable dynamically switching on/off monitors and a lot more, but it seems that fully supporting XRandR is not the priority of nvidia. So with this tool, you can just switch between already defined Twinview setups, switching on or off a monitor is not possible up to now. In conjunction with the limitation to 2 Monitors in one setup (see above), solely XRandR can not be used to script a dynamic DVI-DVI/DVI-TV toggle.

nvidia-settings: In this GUI you can actually see all 3 connected outputs, and enable/disable/adjust all of them and perform the dynamic toggling of the current setup. There is also a rich command-line interface for the tool, but it seems that the important bits are set read only.[/INDENT]**The Solution in short**[INDENT]
The nvidia-settings tool is open source and accomplishes the task. So in principle we could alter the source to make it scriptable. With ```
sudo apt-get source nvidia-settings
``` we got all we need. Fortunately nvidia-settings ships with a program example ```
nv-control-dpy
``` using the control framework of nvidia, which is able to see all outputs and enable/disable them. So there is no need to dive into coding. With the aid of that nifty little program, I simply added a bash script in autostart defining the Twinview setup I want to be able to switch to, and invoke it by using the XRandR utility (switching between known setups is still possible with this tool, but you simply can't define two setups with 3 different outputs in Xorg.conf - see above). The XRandR commands in turn are quite easy to put in a bash script - Solved :-)[/INDENT]**BUT BE WARNED: I don't know how failsafe/dangerous it is to use that sample program from nvidia - USE AT YOUR OWN RISK and don't blame me if it ruins your PC/Monitors**

**Solution in Detail:**


**Step 1: Get the nvidia-settings sources**[INDENT]
```
apt-get source nvidia-settings
```This will create a folder nvidia-settings-xxx in your current directory. NOTE: don't invoke apt-get with sudo, otherwise you have to chown the folder.
[/INDENT]**Step 2: Compile the nvidia-settings sources **[INDENT]```
cd nvidia-settings-xxx
make
```Most probably you will get an error on this because there are libraries missing on your machine on which nvidia-settings depends. I had to install the following libraries to make it work

```
sudo apt-get install libgtk2.0-dev libxv-dev libxxf86vm-dev m4
```if still something is going wrong, most probably you need to install a couple more libs/apps. Google is your friend on this one.[/INDENT]**Step 3: Compile the samples**

Simply enter the samples subdirectory of nvidia-settings-xxx created above and build it.[INDENT]```
cd samples
make
```Probably, you'll get an error. I had one when compiling the newest nvidia-settings directly downloaded from the nvidia home page, but it worked flawless when using the current ubuntu nvidia-settings version. However, if you get 
> nv-control-events.c:701: error: 'NV_CTRL_COLOR_SPACE' undeclared here (not in a function) there is a workaround. The error stems from compiling the nv-control-events sample program, but we don't need it for our porpose. So we simply omit compiling it.

Edit the Makefile file and delete the whole line containing
> nv-control-events \As of nvidia-settings version 256.44 this is line number 73. Save the file.

After invoking 
```
make
``` again you should have an 
> nv-control-dpy executable in the folder. Put it in some place where the system can find it, /usr/local/bin is a good place if you have not set up a folder for your own executables yet and don't plan to do so. Copying there as root makes it system-wide available.[/INDENT]**Step 4: Gather information of the Screen configuration you want to be able to switch to by invoking a script.**[INDENT]
Switch to your desired screen configuration using the nvidia-settings tool. In my case this typically consists of firing up nvidia-settings, going to X Server Display Configuration, selecting an active Monitor, setting the resolution to off, selecting the tv-out, configure in twinview mode and setting the desired resolution there. After that, pressing the apply button and confirming.

Now invoke the nv-control-dpy twice to get the device mask and the metamode of this setup.

```
nv-control-dpy –get-associated-dpys
```shows you the device mask (in my case 0x00010102)


> Using NV-CONTROL extension 1.23 on :0.0
Connected Display Devices:
  CRT-1 (0x00000002): CRT-1
  TV-0 (0x00000100): TV-0
  DFP-0 (0x00010000): LG Electronics M228WA

associated display device mask: [COLOR=Red]0x00010102[/COLOR][COLOR=Red][/COLOR]
Note it somewhere.
```
nv-control-dpy –print-current-metamode
```shows you the metamode. 
> 
Using NV-CONTROL extension 1.23 on :0.0
Connected Display Devices:
  CRT-1 (0x00000002): CRT-1
  TV-0 (0x00000100): TV-0
  DFP-0 (0x00010000): LG Electronics M228WA

current metamode: "id=51, switchable=no, source=nv-control :: [COLOR=Red]TV-0: 800x600 @800x600 +1680+0, DFP-0: 1680x1050 @1680x1050 +0+0, CRT-1: NULL[/COLOR]"
Copy everything after the double double dot to some safe place.
[/INDENT]**Step 5: Define the screen configuration automatically at startup**[INDENT]
I am using KDE so my autostart scripts go to ~/.kde/Autostart. The right location for you may differ. Create a File add_metamode.sh with the following content:

> #!/bin/bash
nv-control-dpy --set-associated-dpys 0x00010102
nv-control-dpy --add-metamode "CRT-1: NULL, DFP-0: 1680x1050 @1680x1050 +0+0, TV-0: 800x600 @800x600 +1680+0"
And of course, replace the 0x00010102 mask with yours and the metamode with yours. Don't forget to enclose the metamode line in double quotes.

Save the file and make it executable by ```
chmod u+x add_metamode.sh
```. Put it where it gets executed after x-startup (KDE: ~/.kde/Autostart).
[/INDENT][B]
Step 6: Restart KDE/Gnome[/B]

**Step 7: Create a Setup switching script**[INDENT]
After the restart invoke ```
xrandr
```. You should see something like this:

> Screen 0: minimum 2480 x 1050, current 2480 x 1050, maximum 2960 x 1224
default connected 2480x1050+0+0 0mm x 0mm
   2960x1224      50.0     51.0  
   2480x1050      51.0* 
   2960x1050      50.0 
Test the switching by invoking xrandr

```
xrandr -r 50.0 -s 2960x1050
```and back

```
xrandr -r 51.0 -s 2480x1050
```If it does not work for you, something might have gone wrong in step 4 or 5 above. To investigate what went wrong nv-control-dpy comes in handy. See ```
nv-control-dpy --help
```. For this to work, a valid metamode must be defined. The ID of the metamodes reported by nv-control-dpy is the same as the refresh rate that xrandr reports for these modes. Creating/Deleting/querying for the modes can all be done by nv-control-dpy.

When the above xrandr commands work, you can combine them in a script to toggle between them. I created a script like this to do the job:

> #!/bin/bash

# rate 50.0 -> CRT DFP
# rate 51.0 -> DFP TV

current_rate=$(xrandr | grep "*" | cut -d"*" -f 1-1 | rev | cut -c -4 | rev )

if [[ $current_rate == "50.0" ]]; then
# switch to TV
        xrandr -r 51.0 -s 2480x1050
else 
# switch back
        xrandr -r 50.0 -s 2960x1224 
fi
If you want to have more than 2 metamodes, the script can be used as a basis to begin developing a more sophisticated switching routine than just toggling back and forth.

Finally, make it executable, and you are done![/INDENT]The method described here can be extended in various ways to handle more complicated tasks, my version is merely a proof of concept – but it does what I want and couldn't find anywhere in forums or How-To's.

For example, using the rich functionality of the nv-control-dpy utility one could make a daemon watching for hotplugged Monitors and automagically changing the screen layout to appropriate settings – a thing many laptop users with nvidia cards would be glad to have for presentations with all kinds of projectors. 

However, I won't do further fine-tuning, this is up to the community.

Please tell me if it worked out for you or not and why, so that I can edit this post accordingly to have everything in one place. This is my first sort of HowTo, so any feedback is welcome.

---

