---
title: "nVidia drivers again"
date: 2012-03-21
forum: Mythbuntu
---

### Post by timswait on 2012-03-21
Hi, I've just built a new Mythbuntu machine that I'm trying to set up. I've got a nVidia GT520 card running HDMI to a 1920x1080 TV. Like everyone else seems to, I was having problems getting audio through HDMI.
In the hardware drivers window it said "No proprietary drivers are in use on this system" and didn't give any options for installing the the nVidia ones. So I downloaded them from their website, and installed them. I do now get audio through HDMI :KS but now my picture is really shonky :( It looks kind of blocky and funny and whichever resolution I choose (including 1920x1080) it doesn't quite fit the screen so that I loose the edges of the image (including the top bar which is annoying).
The hardware drivers window still says "No proprietary drivers are in use on this system", but there is an nVidia control centre item in the system menu, and I've tried playing with settings in this but can't make it look decent.

---

### Post by nickrout on 2012-03-21
Big mistake not to use the proper packaging but never mind.

What resolution are you running at? in a terminal window ```
xwininfo -root
``` will tell you.

Are you using vdpau as your profile? You need to.

You are also suffering from overscan. Your TV should have a setting to get rid of overscan. If not then nvidia-settings will control it.

---

### Post by timswait on 2012-03-21
I'm at 1360x768 at the moment, because I get less clipping of the image at this res, but I've tried lots of resolutions including 1920x1080, which is what I want to use.
What is vdpau and how do I use it?
I can't see anything about overscan settings in "NVIDIA S Server settings" which is what I've been playing with so far. Where can I adjust that?

---

### Post by nickrout on 2012-03-21
> **timswait said:**
> I'm at 1360x768 at the moment, because I get less clipping of the image at this res, but I've tried lots of resolutions including 1920x1080, which is what I want to use.
What is vdpau and how do I use it?[http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)> 
I can't see anything about overscan settings in "NVIDIA S Server settings" which is what I've been playing with so far. Where can I adjust that?
It's in the nvidia settings gui somewhere. I am not in front of an nvidia machiine right now, i will try and remeber to post again tonight when I am home.

---

### Post by nickrout on 2012-03-22
in nvidia-settings look at the left hand panel. About second from the bottom should be the name of your monitor/TV (mine says DFP-0 - (PANASONIC-TV)

Click on that  and in the right hand panel is a slider for overscan compensation. Save the settings once you get it how you want.

PS if your TV has a setting to do away with overscan it is a MUCH better solution.

---

### Post by timswait on 2012-03-22
Thanks for your help. I've not even tried playing back TV or videos yet (I've got another thread on my tuner card problems!) so I don't think vdpau comes into it yet? I'm currently trying to get just the desktop to look right, at the moment the edges of the test are all a bit blocky, before I installed the NVIDIA driver everything looked really crisp.
I can't find anything about overscan correction in my TV controls. I've found the slider in  NVIDIA X Server settings, but it's greyed out.

---

### Post by timswait on 2012-03-22
I *think* I might have found the problem. In the "Information" tab under "DFP-1 - (Targa LCD TV) it gives Native resolution as 1360x768 and Best fit resolution as 1920x1080. But surely the TV should be 1920 x 1080 as native? Its a full HD TV sold as 1920x1080p and when I turn the computer on the bottom of the screen displays "HDMI 1 1080p 60Hz" So is the card trying to squeeze 1920x1080 onto 1360x768 and then force the result on the TV which then tries to convert it back to 1920x1080?!
In which case how can I convince the card that it really is 1920x1080 native and that it doesn't need to fiddle about with it?! As I say the original drivers that came out of the box were fine with this!
P.S. I've tried unchecking the "Force Full GPU Scaling" box and tried all three options for GPU scaling, but none make any difference.

---

### Post by nickrout on 2012-03-22
perhaps your tv gives wrong edid information?

---

### Post by timswait on 2012-03-22
As I say, it seemed to work OK with the original mythbuntu drivers. I didn't actually look at what resolution it was set to, but I think it was 1920x1080, it looked good and there was certainly no overscan.
If it is giving the wrong edid info what can I do about it? :(
It's a DGM TV.

---

### Post by timswait on 2012-03-25
If I want to give up on HDMI audio how do I get rid of the nVidia drivers and go back to the ones that were installed in the original installation?

---

### Post by nickrout on 2012-03-25
why would you change drivers? simply point the audio to the device you want to use.

---

### Post by timswait on 2012-03-26
I couldn't get HDMI audio working with the drivers that came preinstalled with Mythbuntu. I thought that to get HDMI audio working I needed the nViDia drivers, so i installed them. This did solve the audio problem, but messed up the display. Now I'm not sure I can be bothered with HDMI audio, I'll just use the audio out of the computer, but I need to roll back to the Mythbuntu original drivers to get my display looking right again!
Unless there is some way to get the NVidia drivers working properly with the display? Assuming the TV is giving incorrect EDID Information is there any way I can correct this?

---

### Post by nickrout on 2012-03-26
_Resolution_

What does your TV's manual say the native resolution on HDMI is?

Try forcing a modeline to that resolution in xorg.conf, or put the horizontal and vertical rates into xorg.conf.

_Overscan_

Is there an option on your TV to switch off overscan? It's often called "pixel mapping" or "just scan"

[http://pixelmapping.wikispaces.com/](http://pixelmapping.wikispaces.com/)

If not then use the overscan setting in nvidia-settings.

---

### Post by timswait on 2012-03-26
The TV instruction manual has resolution as 1920 x 1080 in the specifications, it doesn't specify different resoltuions for differnt inputs, so I would assume the maximum HDMI resolution is indeed 1920 x1080.  When the computer is connected the TV comes up with "HDMI 1 1080p at 60Hz" so it does recognise its getting a HD input.
My TV manual doesn't mention overscan or pixel mapping, so I don't think I can do it with that. The overscan slider in NVIDIA settings is greyed out so I can't adjust it there either.
I don't really know much about xorg, this is how it looks at the moment, what should I change to force it?
Cheers
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Targa LCD TV"
    HorizSync       14.0 - 68.0
    VertRefresh     48.0 - 62.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by nickrout on 2012-03-26
*scratches head*

what version of nvidia drivers are you using? (/var/log/Xorg.0.log will tell you, it may also give you clues as to why you are getting 1360x768 instead of 1920x1080).

By the way are you saying that even though the TV is saying 1080p 60Hz, X is actually running at 1360x768?

Also where did you get these figures?

> HorizSync       14.0 - 68.0
    VertRefresh     48.0 - 62.0

---

### Post by timswait on 2012-03-27
Thanks for your help. I'm afraid I don't really know what to look for in the log file, I've attached it.
TBH I don't really know what I think is happening! I just find it funny that nVidia X server settings thinks that "Native resolution" is 1360x768 and "Best fit resolution" is 1920x1080. I'm suspicious its sort of trying to stretch 1360x768 to 1920x1080, and maybe if it knew that the native resolution of the display was 1920x1080 then it would work.....
I don't really know what I'm talking about!
Those figures were just what was in my Xorg.conf file that nVidia x server settings created for itself. I've not manually edited the file at all.

---

### Post by goffa on 2012-03-27
I've found this guide to be helpful to get the correct xorg.conf 

[http://forum.xbmc.org/showthread.php?tid=70068](http://forum.xbmc.org/showthread.php?tid=70068)

Also as others have said overscan can be adjusted from your TV or using nvidia-settings.

---

### Post by nickrout on 2012-03-27
> **timswait said:**
> Thanks for your help. I'm afraid I don't really know what to look for in the log file, I've attached it.
TBH I don't really know what I think is happening! I just find it funny that nVidia X server settings thinks that "Native resolution" is 1360x768 and "Best fit resolution" is 1920x1080. I'm suspicious its sort of trying to stretch 1360x768 to 1920x1080, and maybe if it knew that the native resolution of the display was 1920x1080 then it would work.....
I don't really know what I'm talking about!
Those figures were just what was in my Xorg.conf file that nVidia x server settings created for itself. I've not manually edited the file at all.

Well it is perfectly clear that X is running at 1920x1080.

Could you please give the output of the following commands:

```
xwininfo -root
xrandr
nvidia-settings --query OverscanCompensation
```

---

### Post by BicyclerBoy on 2012-03-28
Adding some noise..
I'm afraid the cheap HD TVs (& Targa sounds cheap) are typically 1360/1368x768 native resolution i.e. HDready.
The input prescaler is happy to accept full HD...

---

### Post by timswait on 2012-03-28
goffa: Thanks for that, I'll have look at the xorg guide. As I've said, I can't adjust the overscan through tht TV or nVidia settings.
Nickrout: Cheers for that, I've attached the output.
Biyclerboy: That sounds plausible, but nowhere on the box or in the manual does it mention "HD ready" or 1360x768, and it does specifically say "Full HD 1080p" and in the spec it says 1920x1080, so if it doesn't do it then I think that's against the trade desriptions act!
Here's the details for the TV:
[http://www.digimate.com/en/productDetail.asp?prod=629]("http://www.digimate.com/en/productDetail.asp?prod=629")

---

### Post by timswait on 2012-03-28
By the way, what is this canberra-gtk-module thing that it can't load? Is this the problem? I've tried looking for a package called canberra-gtk, but I can't find it in package manager.

---

### Post by nickrout on 2012-03-28
I think the package would be libcanberra-gtkN where N is an integer. Try ```
dpkg -l libcanb*
``` to see what is installed.

My nvidia-settings isn't even linked to libcanberra so i don't have a clue why yours is faulting on that. 

What happens when you simply run ```
nvidia-settings 
```from the command line? Do you get any error messages?

What about ```
nvidia-settings --query all
```

---

### Post by nickrout on 2012-03-29
One more thing - how many displays do you have plugged in? I noticed a reference to Twinview in your xorg.conf - I wonder if this somehow interferes with setting overscan (hence it being greyed out?)

Just a guess...

---

### Post by goffa on 2012-03-29
timswait, the manual for your TV show five aspect ratios, 16:9, zoom1, zoom2, Auto, 4;3. Have your tried all of these by pressing the aspect button on the remote. 

To install the latest nvidia drivers I followed this guide only the other day and it worked well. May you should try to reinstall the drivers, overscan in nvidia-settings should not be greyed out.
[http://ubuntuforums.org/showpost.php?p=9203671&postcount=1](http://ubuntuforums.org/showpost.php?p=9203671&postcount=1)

---

### Post by BicyclerBoy on 2012-03-29
The overscan compensation uses shader scaler..
The shader performance is weak in GT520.
Quote from nVidia
<QUOTE>
"Not all GPUs can perform overscan compensation at all modes. It depends on the internal bandwidth of various parts of the GPU."
"you ought to be able to set a lower resolution mode. You may need to enable the "ExactModeTimingsDVI" option and disable the "Full GPU Scaling" checkbox in nvidia-settings to make it drive the TV at a lower resolution."
</QUOTE>

The overscan comp works with old 9400GT at 1360x768 & 1600x1200 (separately).

---

### Post by nickrout on 2012-03-29
> **BicyclerBoy said:**
> The overscan compensation uses shader scaler..
The shader performance is weak in GT520.
Quote from nVidia
<QUOTE>
"Not all GPUs can perform overscan compensation at all modes. It depends on the internal bandwidth of various parts of the GPU."
"you ought to be able to set a lower resolution mode. You may need to enable the "ExactModeTimingsDVI" option and disable the "Full GPU Scaling" checkbox in nvidia-settings to make it drive the TV at a lower resolution."
</QUOTE>

The overscan comp works with old 9400GT at 1360x768 & 1600x1200 (separately).


yeah I found a post in nvnews forums like that too. I wasn't sure what specs the 520 has but I thought it should be recent enough to be grunty enough to do the job.

I mean even my ION and ION2 machines do the overscan thing!

---

### Post by BicyclerBoy on 2012-03-29
I did (recently) come across an nVidia explanation of when & why the overscan is not always available.
IIRC if the driver believes it is connected to a PC monitor then no overscan.

This may have only been the original plan/thinking.

In recent times I have no problem using it on PC monitors over DVI/VGA.

Maybe it has problems working with twinview..

---

### Post by timswait on 2012-03-29
It's always the simplest thing isn't it?! I tried Goffa's suggestion with the aspect ratio, and in addtion to the 5 listed in the manual, there was a sixth option: "Just Scan" set to that it works fine and looks good! Don't know why I didn't think of trying aspect ratios myself, but thanks everyone for your help!

---

### Post by timswait on 2012-03-29
I don't believe it :( Literally just solved that problem, installed some updates that required a restart (including a new kernel version) and now it won't boot at all :( Just gets to displaying th mythbuntu logo with the 5 red dots below it (the 5 dots don't go white in sequence like they normally do when its loading), and nothing else happens. Is there any easy way to undo the updates?

---

### Post by nickrout on 2012-03-29
> **timswait said:**
> I don't believe it :( Literally just solved that problem, installed some updates that required a restart (including a new kernel version) and now it won't boot at all :( Just gets to displaying th mythbuntu logo with the 5 red dots below it (the 5 dots don't go white in sequence like they normally do when its loading), and nothing else happens. Is there any easy way to undo the updates?

Try pressing some keys while the logo is there. You may getr a text screen that hints at the problem. Ctrl and esc come to mind.

Most likely this is a kernel issue with the particular nvidia drivers. Try the previous kernel from grub.

---

### Post by timswait on 2012-03-30
Ctrl Esc doesn't do anything, nothing on the keyboard seems to do anything except alt ctrl del which restarts it. I don't get any GRUB menu on this machine as it doesn't have any other operating system on it. Is there any way to use a different kernel or even to boot into recovery mode if I don't have a grub menu?
How can I just get rid of these nVidia drivers? They really seem to be causing more problems than they're solving! I thought nVidia was supposed to work well with Linux, that's why I chose this card....

---

### Post by nickrout on 2012-03-30
nvidia does work well with linux, I suspect operator error somewhere.

Oh and you will have a grub menu.

If you want to get rid of the nvidia drivers uninstall them, same as any other package.

---

### Post by BicyclerBoy on 2012-03-30
Don't blame nVidia ..all this is well documented in the driver readme.

The OP has used the nVidia install method (direct download from their website).
Then you have to rerun the nVidia install script from console login every time the kerenl is updated.

BUT first you need the new kernel headers to match your new update.
uname -r

You are better of finding the required driver in x-swat or xorg-edgers ppa.

---

### Post by goffa on 2012-03-30
> **nickrout said:**
> 

Oh and you will have a grub menu.


I suspect he does not know this will only be displayed if the shift key is held down during boot.

---

### Post by nickrout on 2012-03-30
> **goffa said:**
> I suspect he does not know this will only be displayed if the shift key is held down during boot.


Ahh thanks, I was wrong on ctrl or esc!

---

### Post by timswait on 2012-03-31
All the other machines I have Linux on are dual boot so show grub automatically, I didn't know how to show it. However, the grub menu doesn't show the previous kernel, it only lists "Ubuntu, with Linux 3.0.0-17-generic" and recovery mode, there's nothing under Previous Linux versions. But I can now get a command prompt to fix it.
> The OP has used the nVidia install method (direct download from their website).
Then you have to rerun the nVidia install script from console login every time the kerenl is updated.

BUT first you need the new kernel headers to match your new update.
uname -r

You are better of finding the required driver in x-swat or xorg-edgers ppa. 
I'm sorry, I don't know what this means. Does this mean my computer will stop working everytime I install an updated kernel if I don't re-install the nVidia drivers?
If I get rid of the nVidia drivers will it go back to using whatever it was using out of the box, or will it just not have any drivers at all and not put anything on the screen?

---

### Post by nickrout on 2012-03-31
> **timswait said:**
> All the other machines I have Linux on are dual boot so show grub automatically, I didn't know how to show it. However, the grub menu doesn't show the previous kernel, it only lists "Ubuntu, with Linux 3.0.0-17-generic" and recovery mode, there's nothing under Previous Linux versions. But I can now get a command prompt to fix it.

I'm sorry, I don't know what this means. Does this mean my computer will stop working everytime I install an updated kernel if I don't re-install the nVidia drivers?
If I get rid of the nVidia drivers will it go back to using whatever it was using out of the box, or will it just not have any drivers at all and not put anything on the screen?

```
sudo add-apt-repsoitory ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers
```

The nvidia drivers must be compiled against your current kernel headers. When you do it properly from the ubuntu packages this happens automatically when the kernel is upgraded.

When you go outside the proper packaging method you need to manually reinstall after a kernel upgrade. 

Of course you could not install any kernel upgrades too!

---

### Post by timswait on 2012-03-31
So is that code what I should have done in the first place? I thought my only option for getting the drivers was from the manufacturer's website.
ANother quick query, how do I turn my network connection on from the prompt? I've gone to prompt on the netroot option. I know that normally I need to type "ifconfig eth0 up". The problem is that this machine networks through a usb port, i've tried "ifconfig usb0 up" and usb numbers up to 7, but all say no such device, so what do I need to type to make it connect to the network?
Cheers

---

### Post by timswait on 2012-04-04
I'm completely stuck now. I can't boot to the previous kernel as for some reason my grub menu doesn't show it. I can't install anything from recovery mode as I can't get networking to work as I'm using a phone as a USB modem and don't have an ethernet connection. Is there anything I can do to get back to a bootable system other than starting again with a fresh install?

---

### Post by nickrout on 2012-04-04
> **timswait said:**
> I'm completely stuck now. I can't boot to the previous kernel as for some reason my grub menu doesn't show it. I can't install anything from recovery mode as I can't get networking to work as I'm using a phone as a USB modem and don't have an ethernet connection. Is there anything I can do to get back to a bootable system other than starting again with a fresh install?

Once the system has booted can you use ctr-alt-f1 to get a console?

---

### Post by timswait on 2012-04-19
I've given up trying to sort this out and just wiped and re-installed a fresh mythbuntu installation.
I'm still going to try one more time with the nVidia drivers, I've tried following the steps in post #37 to install from the repositories, but the third step doesn't work:
```
trilby@trilby-myth:~$ sudo apt-get install nvidia-graphics-drivers
[sudo] password for trilby: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Unable to locate package nvidia-graphics-drivers

```
The previous 2 steps completed, so why can't it find the package?

---

### Post by timswait on 2012-04-19
Ah, just installed it through the Ubuntu Software centre GUI, that seems to have worked :)

---

