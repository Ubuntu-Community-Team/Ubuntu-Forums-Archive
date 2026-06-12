---
title: "Gusty &amp; 8800GT?"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by themindrecoils on 2007-11-25
Does anyone have this working?  After I install the nvidia drivers, it works great until I reboot...then it reverts back to vesa.   Is there some startup script I need to change or a module I need to blacklist or anything like that?

---

### Post by Azakus on 2007-11-25
Do you have the newest beta nvidia drivers? Only those fully support the 8800GT. 
[32-bit 169.04]("http://www.nvidia.com/object/linux_display_ia32_169.04.html")
[64-bit 169.04]("http://www.nvidia.com/object/linux_display_amd64_169.04.html")
Also, after you install, run this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals --composite --nologo
```

---

### Post by themindrecoils on 2007-11-25
Thanks.   I do have the right drivers--it works perfectly after I install (when I restart gdm), just doesn't pick it up on reboot for whatever reason.  I'll give running that config command a shot.

---

### Post by themindrecoils on 2007-11-29
Thanks, that seems to have worked.   Do you know if there's any way to control the fan speed?

---

### Post by blitze on 2007-11-30
Great question.  Need Riva Tuner or like program under Windows, some line commands in xorg.conf would be great if one could to control the fan.

---

### Post by regomodo on 2007-12-01
> **blitze said:**
> Great question.  Need Riva Tuner or like program under Windows, some line commands in xorg.conf would be great if one could to control the fan.

nvclock may work (it's cli), however, my fan seems to be automatic and never gets above 53C

---

### Post by Jabb3r on 2007-12-02
Ohhh live saver thread! wil try this now, been goin mad, lol

---

### Post by bruno321 on 2007-12-02
I too am using 8800GT, kubuntu gutsy and the latest nvidia drivers.

However, when I run that line, X does work with the nvidia driver when I do $ startx , yes, but when I reset I find myself on BusyBox v1.1.3 without knowing what to do. I have to reset, load on failsafe and once again, run that command line, do startx... If I dont re-run the command, I get "no screens found" when I startx.

How can I truly fix it? Thanks

---

### Post by Jabb3r on 2007-12-02
Not so much luck here either, everytime I restart X I get a low graphics mode error and it always seems to use the vesa driver even if I've deleted it out of xorg.conf which I made with nvida-xconfig, but nvidia-settings say I aint usint the NVIDIA X driver which I aint I guess. Completel  lost with it all though.

---

### Post by Jabb3r on 2007-12-02
A development. May help someone diagnose my prob

I'm using the command /etc/init.d/gdm stop and /etc/init.d/gdm start to reboot my xserver, but i tried to startx instead and got a fatal error. I had a quick look through things and I found that my /etc/X11/xinit file is completely empty. I guess thats the problem?

So really X isn't workin but I'm able to get gdm booted in the low graphics mode. :S

---

### Post by themindrecoils on 2007-12-02
My problem came back, but I think I've got the steps down now:  

1. Install gusty.
2. Install build-essential from disk (didn't work when it got the updated version for whatever reason).
3. Stop gdm.
4. Install driver.  When it asks you to auto config, say yes.
5. Start gdm, make sure it worked.
6. Back up xorg.conf.
7. Reboot a couple of times, make sure it still works.
8. Install updates.
9. Reboot.
10. Re-install nvidia driver since it won't work after updates are installed.
11. Restore xorg.conf from step 6.

At least that's what worked for me.  We'll see how stable it is, I guess.

---

### Post by Jabb3r on 2007-12-02
thanks for the advice. It'll have to wait till tomoz if I need a reinstall. Sad if I do

---

### Post by regomodo on 2007-12-02
guys, have you ran nvidia-xconfig?

Seriously, installing this driver is easy so long as you have the dependencies (which the nvidia installer will warn you if you don't)

---

### Post by bruno321 on 2007-12-02
Yeah, I had... anyway, since I wasn't getting anywhere now I'm reinstalling Kubuntu. When I first installed the drivers I had some dependencies missing (the installation program COULD tell me to check if I have this or that installed, couldn't it?), and I forgot to do kdm stop :$ . Afterwards I installed the dependencies and did a proper reinstall of the drivers, but to no avail. So maybe with a system reinstall and properly installing the driver it will work... dunno. I will inform later. Right now I'm waiting at 83% of "installing linux-generic" which is a reported bug. How boring.

---

### Post by bruno321 on 2007-12-02
Okay-- I made it! It was a little bit tricky for the person not used to install nvidia drivers every day. Here's how I got it going:

1) Make a fresh install. Easy for me to say since in my case it's a new system, but I couldn't get it done without making a fresh install.

2) # sudo apt-get install pkg-config xserver-xorg-dev build-essential

3) # sudo apt-get remove linux-restricted-modules-common linux-restricted-modules

4) a) Now logout and login in text mode
     b) sudo /etc/init.d/gdm stop (kdm stop if using kubuntu)

5) # sudo sh NVIDIA-Linux-x86-169.04-pkg1.run
Follow the instructions. It will have to build the module. At the end say YES, you want it to configure xorg (by default it's no).

You can try # sudo /etc/init.d/kdm start now and see if it loads. In my case, it doesn't. To repair it:

6) # sudo nano /etc/modprobe.d/lrm-video
Comment out the line "install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS" (i.e. put a # in front of the line)

7) # sudo /etc/init.d/kdm start

That did the trick. I realized that it is advised to uninstall the nvidia-kernel* packages before attempting an nvidia driver installation. I didn't do it. Perhaps if I had done it, steps 6 and 7 wouldn't have been necessary, but I won't touch anything else anymore because it's working just fine :)

Cheers!

---

### Post by Jabb3r on 2007-12-02
Thanks bruno, will try that now

Edit: M8 your a legend, thank you and I did it with no reinstall too, w00t!

---

### Post by bruno321 on 2007-12-03
Hey, glad it helped :) Perhaps it will also help the original poster.

---

### Post by Spiffington on 2007-12-06
I've been having problems trying to install these drivers. I can only assume it's some simple oversight on my part though, but here it is anyway.

I've downloaded the drivers and theyre sitting on my desktop currently. they are the "NVIDIA-Linux-x86_64-169.04-pkg2.run" version. As far as i know i've set everything required up properly - i.e the 'uname -r header thing', made sure the 'pkg-config and xserver-xorg' are installed, made sure any other nvidia drivers are uninstalled and so forth.

so i logout, hit ctrl alt f1 to go into text mode, run the '...gdm stop' command, so far so good. However no matter what i do, when i come to:

*sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run*

i just get a simple error returned - "can't open NVIDIA-Linux-x86_64-169.04-pkg2.run"

I read somewhere else i may have to change directory to wherever the file was stored, but i cant actually figure out how that works,,

Anyway help would be appreciated with this since for now im stuck at 800x600.. its not overly nice.

---

### Post by synthaxx on 2007-12-06
> **Spiffington said:**
> i just get a simple error returned - "can't open NVIDIA-Linux-x86_64-169.04-pkg2.run"

First you need to check where you downloaded the program, then go to that directory (using the "cd" command).
You should be able to auto complete the command if the file is in the directory (type in "sudo sh NVI" and then press the [TAB] key).

Then you simply run the same command.

If that doesn't work do (while still in that directory) "sudo chmod +x NVIDIA-Linux-x86_64-169.04-pkg2.run" and run the install command again.

That said, i've tried these drivers, and can't get them to install. Every time i reboot i just get a black screen crash (no CTRL+ALT+DEL, a real crash) and the Xorg.0.log looks like it just booted without a problem... really strange.

 I will try the above steps again on a fresh Gutsy to see if it helps.

---

### Post by Spiffington on 2007-12-06
Thanks for the help. Ill get a chance to try some of that tomorrow.. after this exam on human rights..

Regarding the CD command, how do you form it? Ive tried:

*cd home/myname/desktop*

for example, but it produces an error. 

Also what is the default directory it will be looking in if i simply type:

*sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run*

?

---

### Post by synthaxx on 2007-12-06
First, you need to understand that everything in linux is CaSeSeNsItIvE. So you'd need to cd to ../Desktop

Second, you need to cd to /home/yourname/Desktop , since your home directory is mounted to the root. Hence the "/" infront of it.

If you just type the command without going to the directory, it'll look in the path for the file (which is not there) and give you an error message like the one you allready saw.

Use "ls" to list the files in the current directory, and if you're not sure where you are use "pwd" to find out.

Good luck!

---

### Post by Spiffington on 2007-12-06
aah.. case sensitive eh. That explains one or two things. Again, thanks for the help - i'll post back with my results later on.

---

### Post by Spiffington on 2007-12-07
Well i got the drivers working, bruno's suggestion for:

6) # sudo nano /etc/modprobe.d/lrm-video
Comment out the line "install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS" (i.e. put a # in front of the line)

Did the trick quite nicely.

---

### Post by _algol_ on 2007-12-08
> **bruno321 said:**
> 

6) # sudo nano /etc/modprobe.d/lrm-video
Comment out the line "install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS" (i.e. put a # in front of the line)

7) # sudo /etc/init.d/kdm start

That did the trick. I realized that it is advised to uninstall the nvidia-kernel* packages before attempting an nvidia driver installation. I didn't do it. Perhaps if I had done it, steps 6 and 7 wouldn't have been necessary, but I won't touch anything else anymore because it's working just fine :)

Cheers!

THANK YOU for posting this....I was having no end of trouble getting my Gutsy install to recognize my 8800GT's existence.  

I can confirm that steps six and seven are indeed unnecessary if you uninstall the "nvidia-kernel-common" package via Synaptic before you roll your own.  \\:D/

EDIT:  by the way, where bruno uses "kdm" (e.g.: # sudo /etc/init.d/**kdm** start), substitute "gdm" if you're using GNOME and not KDE.  I imagine most people would pick up on that, but sometimes noobers like myself copy verbatim and get royally confused. :)

---

### Post by blitze on 2007-12-10
Thanks for the instructions as well.

Now I have found that the Nvidia drivers do not like TV-Out on the 8800GT and when twinview is enabled, it will lead to signal loss to your monitor.

Ironically, TV-Out now works on Vista x64 with the 8800GT and Nvidia drivers.  Bloody typical.

Hopefully Nvidia will rectify the problem oneday soon.

Still, I have Ubuntu back with Nvidia drivers on my LCD Monitor.

---

### Post by rAiN mAn 2o0o on 2007-12-10
> **_algol_ said:**
> THANK YOU for posting this....I was having no end of trouble getting my Gutsy install to recognize my 8800GT's existence.  

I can confirm that steps six and seven are indeed unnecessary if you uninstall the "nvidia-kernel-common" package via Synaptic before you roll your own.  \\:D/

EDIT:  by the way, where bruno uses "kdm" (e.g.: # sudo /etc/init.d/**kdm** start), substitute "gdm" if you're using GNOME and not KDE.  I imagine most people would pick up on that, but sometimes noobers like myself copy verbatim and get royally confused. :)

I had tried everything... installing , uninstalling nvidia kernerls... nothing worked.. fresh install or not on gutsy.... the ONLY thing that worked for me was thanks to BRUNO's STeps #6 and #7... THANK YOU!!!!  I love ubunutu and ditched my ATI x1950 pro to buy an Nvidia 8800gt only to find that it wouldn't work either!!.. NOW IT DOES!!! ALL visual effects! works GREAT.. also... Nvidia Xconfig is a wonderful tool as well.. INSTALL it once you have your drivers installed!.   ONCE AGAIN... THANK YOU BRUNO!!!!!!!!!!!!!!!!!!

---

### Post by GackY2K on 2007-12-11
> **bruno321 said:**
> Okay-- I made it! It was a little bit tricky for the person not used to install nvidia drivers every day. Here's how I got it going:

1) Make a fresh install. Easy for me to say since in my case it's a new system, but I couldn't get it done without making a fresh install.

2) # sudo apt-get install pkg-config xserver-xorg-dev build-essential

3) # sudo apt-get remove linux-restricted-modules-common linux-restricted-modules

4) a) Now logout and login in text mode
     b) sudo /etc/init.d/gdm stop (kdm stop if using kubuntu)

5) # sudo sh NVIDIA-Linux-x86-169.04-pkg1.run
Follow the instructions. It will have to build the module. At the end say YES, you want it to configure xorg (by default it's no).

You can try # sudo /etc/init.d/kdm start now and see if it loads. In my case, it doesn't. To repair it:

6) # sudo nano /etc/modprobe.d/lrm-video
Comment out the line "install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS" (i.e. put a # in front of the line)

7) # sudo /etc/init.d/kdm start

That did the trick. I realized that it is advised to uninstall the nvidia-kernel* packages before attempting an nvidia driver installation. I didn't do it. Perhaps if I had done it, steps 6 and 7 wouldn't have been necessary, but I won't touch anything else anymore because it's working just fine :)

Cheers!


I've tried this EXACTLY, but I'm still having trouble.
I also did a fresh install...didn't even run the update before starting this (don't know if that is good or bad).  As soon as I'm done (reloading UI after commenting out the line in lrm-video) it attempts to load gdm but gives me the low res error...so I change the display to LCD and set the resolution, click the Graphics driver tab...Specify with the bullet to look by MODEL.  In the list of names, I select NVIDIA, and then from the list of drivers, I select "Geforce 8 Series" and click OK.  Gnome loads, but is in low res.  I then Goto:  SYSTEM>ADMINISTRATION>SCREENS AND GRAPHICS and repeat the process, of selecting LCD and resolution, then the Driver all over again...it tells me I need to logout..so I do it one better and just reboot!  Gnome loads and damn it...its back to that ugly "Ubuntu is running low-graphics mode" screen again...asking me to CONFIGURE, SHUTDOWN, or CONTINUE.   /sigh
So, I do it all over again..setting my LCD and Driver...always reverts to low res and the Generic Vess compliant video card driver though...no matter what I do.

I'm at a loss...I'm about to cry    

/cry

SEE...I TOLD YOU!

Any other suggestions?  Should I let it do the UPDATE (145 updates found from a fresh install) first?  Does that matter?  Also...My BenQ LCD isn't listed, so I keep choosing Generic LCD...don't think that that would matter though...but I'm at a loss.

SYSTEM:
MB: Asus P5N-E
Card:  EVGA e-GeForce 8800 GT
RAM:  Corsair 2 Gigs
Proc:  Intel E6700


HELP :)


EDIT!  Working!   I wasn't using the BETA drivers like shown above, but the ones i manually downloaded from nVidia...my mistake there....I was assuming that the release ones would be better...WRONG!  Works great using the beta drivers!  

Tx a TON!!!

---

### Post by taliosfalcon on 2007-12-16
so i finally got my 8800gt working fine with the 169.04 drivers, but how do i enable desktop effects, if i do it through preferences-appearence it tells me i need to enable the restricted nvidia driver, which breaks the 169.04 driver and sticks me back to low visual mode if i do..?

---

### Post by Johanneke on 2008-01-21
Hello, I'm trying to INSTALL gutsy on my brand new PC with my nvidia 8800GT video card. But whenever I start the install, my monitor (samsung Syncmaster 226cw) goes off. 
I tried with a Compaq CRT but no result, it is like i am loosing a video signal. 
I read on different topics that 8800GT is not supported by Gutsy, but some of you guy's are really running Gutsy with 8800GT, so my question is; 
How can I install Gutsy with 8800GT without removing my video card and install with an older card and after install Gutsy replace the older video card for my 8800GT??

I did not put anything from my xorg.conf or any other error messages in this post, because I don't have one, I still have to install Gutsy.

Hope that there is an answer for my problem, otherwise I have wait for the next version of Ubuntu and hope there is support for 8800GT.
:(:(:(

---

### Post by subtex on 2008-01-24
> **Azakus said:**
> 
Also, after you install, run this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals --composite --nologo
```

THANK YOU!

you just saved me yet another night of pulling all my hair out trying to get my 8800GT to work!

---

### Post by boakes on 2008-02-15
> **Spiffington said:**
> I've been having problems trying to install these drivers. I can only assume it's some simple oversight on my part though, but here it is anyway.

I've downloaded the drivers and theyre sitting on my desktop currently. they are the "NVIDIA-Linux-x86_64-169.04-pkg2.run" version. As far as i know i've set everything required up properly - i.e the 'uname -r header thing', made sure the 'pkg-config and xserver-xorg' are installed, made sure any other nvidia drivers are uninstalled and so forth.

so i logout, hit ctrl alt f1 to go into text mode, run the '...gdm stop' command, so far so good. However no matter what i do, when i come to:

*sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run*

i just get a simple error returned - "can't open NVIDIA-Linux-x86_64-169.04-pkg2.run"

I read somewhere else i may have to change directory to wherever the file was stored, but i cant actually figure out how that works,,

Anyway help would be appreciated with this since for now im stuck at 800x600.. its not overly nice.

```
chmod 777 NVIDIA-Linux-x86_64-169.04-pkg2.run
```

---

### Post by Discombobulated on 2008-02-17
None of the above seemed to work for me - I could get the 169.04 driver working (beautifully - fixed the 'memory leak') but on reboot I was back to chunky VESA graphics.

This is what eventually worked:

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
sudo /etc/init.d/gdm start
```

7.10, AMD64

---

### Post by joetotale on 2008-03-08
Thanks to everyone for this thread - I've had a frustrating couple of days getting my card recognised on a new build 64 bit machine.  Glad that I don't have to switch distros again.  Should have done more research on my components before building, but I never thought 8800 cards wouldn't be supported out the box with Gutsy.  Great advice here though :grin:

---

### Post by louminati on 2008-03-19
FYI I posted my experiences [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=729150") in case it will help anyone on this thread...

Cheers!

-Lou

---

### Post by Aldanga on 2008-04-27
I've followed all the instructions in this thread to the 'T', but still cannot get a legitimate output on my card using the nVidia driver. (Even using the Vesa driver I only get 640x480; and my screen is 1680x1050 native.)

Whenever the nVidia driver is enabled, I get an error which says my card/monitor could not be detected. This has happened numerous times since I bought my 8800GT, on both 7.10 32/64 and 8.04 32/64. I have no problems on PCLinuxOS or Fedora, but only Ubuntu. I'm guessing it has to do with Ubuntu's bugs while using DVI ports.

Do you guys possess a fix for this? or would you be able to point me in the right direction?

---

### Post by Johanneke on 2008-04-28
Eh, I downloaded the official latest release, and now I am able to install with no problems at all.
Everything works :)

For me the problem is solved.

---

