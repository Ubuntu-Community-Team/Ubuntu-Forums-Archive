---
title: "None of the Nvidia Drivers Work with Gutsy"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Anlace on 2007-11-07
[I]Update:  This issue remains unresolved for the majority of us who may not be comfortable with the changes suggested as a work-around as posted in the bug reports listed in my post below.

The best of luck to you all, personally I am going back to Feisty and waiting for the next Ubuntu release to try again.[/I]


Greetings,

I'll try to make this coherent, it's late and I'm ready to give up on the whole Gutsy project and go back to Feisty.  After two days of arm wrestling with Gutsy trying to get Nvidia drivers to work properly I am ready to call Gutsy a failure and reinstall Feisty tomorrow unless I can get some kind of help with this.

First my pertinent system information:
Video Card is Nvidia GeForce 6800 GS/XT
System is a new command-line installation of Ubuntu with KDE 3.5.8 (no Kubuntu)
My Monitor is ViewSonic VX2025wm, native resolution is 1680x1050

The install went fine until I used Synaptic to install nvidia-glx-new.  After a reboot I had a resolution of 640x480.  At a console login I used dkpg-reconfigure xserver-xorg to go back to using the "nv" driver and restarted X.

Then I hand-edited xorg.conf to include only the resolution of my monitor (the exact same thing that I did in Feisty to make the resolution work) and changed the "nv" driver to "nvidia".  After I restarted X it was back to 640x480 again and no amount of editing xorg.conf would make the monitor display at 1680x1050.

Back to the forums and more research.

Next I tried Envy which had tons of dependencies and after doing some fairly extensive installations of its own, I held my breath as the system rebooted.  Again I had a 640x480 screen resolution but this time I had "virtual" space of 1900x1600!  EEK!

Once again I went back to hand-edit xorg.conf.  First I tried to eliminate all resolutions except the native one of 1680x1050, No good, that had absolutely no affect at all.  Next I tried to change the "virtual" setting to 1680x1050 and this time my resolution was 640x480 without any virtual space at all.

Back to dpkg-recofigure xserver-xorg where I used the "nv" driver again with no problems and the correct resolution for my monitor.

Next I tried a manual installation of the driver from Nvidia's web site.  That seemed to go well until I restarted X and all I got was a black screen.  I tried the Nvidia --update, that found a much newer driver than Envy found or that I found as a link on the Nvidia web site (100.14.19 and --update found 100.14.24).  This time a reboot caused a kernel panic.

Fortunately I was able to reboot successfully and uninstalled the Nvidia driver.  Now I am back to the "nv" driver with no 3D, no OpenGL, nothing that my vid card is perfectly capable of doing, not even a decently working screen saver.

All of this worked great in Feisty so what's the deal?

Searches through the forums have turned up nothing but other frustrated people trying all of the same things that I've already done.  At this point I wonder if I've made such a mess trying to get things to work that nothing will.  I'm hesitant to reinstall Gutsy and face the same challenges.  I mean come on folks, it should not take two days of slamming my head against the wall to make a video card work like it's capable of.

Any and all comments are welcome.  I will read each and every one of them.  I am also willing to show any logs or files if anyone thinks they can sort through the minutia and help.  Please don't tell me to use Envy or dkpg-reconfigure xserver-xorg.  I've already done those things many many times.

Thanks again for any and all help!

Peace,
Gail

---

### Post by eye208 on 2007-11-07
I wonder why people avoid using the "Restricted Drivers/Devices Manager" to install the binary drivers. It's the official supported method and worked well for me every time.

---

### Post by Anlace on 2007-11-07
Greetings,

The "Restricted Drivers/Devices Manager" is in GNOME, as I stated in my post I am using KDE so this pointless comment doesn't really apply now does it?

All of the restricted/universe/multiverse/medibuntu repositories have been added to my apt/sources.list (otherwise I would have never found nvidia-glx-new).

Regards,
Gail

---

### Post by mactece on 2007-11-07
I had Gutsy working fine from a feisty upgrade with a GEforce 6200 and the nvidia driver. So of course I fiddled with the controls and tried to get a tv card working with mythtv. This involved recompiling the kernel and hey presto I have the same problem as you. 

So this isn't helping you but I am trying to solve it as well and if I get anywhere will post it here; likewise for failed attempts.

Current plan of action

1) try the other nvidia driver (the middle one: not "legacy" but not "new", either)
2) physically remove the card and replace for a fresh detection; try another card (I have a geforce II in a box somewhere), etc...
3) I kept a spare partition on my drive so can try a fresh install of Gutsy there and see if it works
4) reinstall Feisty on the spare partition and see if it works; try to upgrade  to gutsy
5) start trying other kernels
6) buy a wireless keyboard and sit much further back :)

I'll post again when I've tried all this (which will be later today - at work at the moment).

David

---

### Post by Anlace on 2007-11-07
Hello David,

Thanks for the reply.  I will keep you posted on my progress also.

This is my plan of action.

First I will post the problem to both Nvidia and Xorg forums and see if they are more helpful than this one has been.  I think this has to be an issue between Ubuntu and Xorg/xserver with the nvidia driver.  My understanding of how things work precisely is limited so I'm kind of fumbling here and could be way off base but it does lead me to wonder what is different between Xorg and Unbuntu in the Gutsy release.  It would be nice to have the attention of someone knowledgeable in this arena so maybe it is time to file a bug report.  Of course the Xorg and/or Nvidia forums may cough something useful up too.

I plan to dump the command-line installation and begin again.  This time I intend to install the nvidia-glx-new driver just after the installation of xorg and kde-core but before I begin the full KDE packages installation.  I did just the opposite in the current installation by installing the nvidia driver last after everything else.

My thoughts on doing a re-installation are that maybe without any changes to the kernel/modules the Nvidia driver could set itself up to work correctly.  If that fails I will go back to Feisty where everything worked great and wait to see what Ubuntu brings in the future.

Peace,
Gail

PS  Which is your posting so that I may keep an eye on it too?

---

### Post by robrmd9 on 2007-11-07
Why wouldn't you use the nvidia-glx (rather than nvidia-glx-new) driver?  That works fine for my 6800GT, and my display is 1680x1050 as well.

---

### Post by mactece on 2007-11-07
Well, I got home and switched on the PC. Suddenly its all working again. I tried various things last night and none worked but what I didn't do was to switch the PC off - I always restarted it instead. I think that the last set of changes combined with a cold start may have made the difference. I wonder how long it will last.

The last things I did were:

- disabled all the changes I could find that I'd made for the TV card
- set desktop effects to "none"
- disabled and uninstalled the nvidia driver
- restarted
- reinstaled and enabled the nvidia driver
- switched it off and left it overnight
- switched it on tonight.

I remember now reading about a cold start being important for installing other types of card so you might need to do something similar when trying things out.

I'm sorry this is likely to be of no use to you whatsoever. If I stumble on anything else I'll post again.

Good luck!

David

PS my post is your post so no help there either. Sorry.

---

### Post by Anlace on 2007-11-07
Greetings,

Thanks for the reply robrmd9, I do appreciate it.  The answer to your question is - why would I do that?  The correct current driver for my card is nvidia-glx-new or the driver directly from Nvidia.  What would I gain by downgrading?  The card already works with the nv driver, what is the difference between the nv driver and a legacy driver?

I'm simply trying to get my installation to be able to use glx, etc to the best of my card's abilities, do the legacy drivers enable all of that?  My needs are such that I am running VMWare and wine so it's not all about cool desktop effects though it would be nice to have a working screensaver.

David, that's interesting news and the only thing that I haven't tried yet.  What heck, nothing to lose here if I turn the silly thing off and go have lunch ;-)

I have posted to the Nvidia web site and will let you all know what they have to say about this.

Peace,
Gail

PS  Just in case anyone out there has the technical ability to read through these things and make sense of them, attached are my log files and xorg.conf.  The xorg.conf file reflects the change I made to the driver from nvidia back to nv to be able to access my computer to be able to see enough to post.

---

### Post by Anlace on 2007-11-07
Response from Nvidia:

"According to your bug report, you have the 1.0-7185 nvidia kernel module installed (which does not support your GPU) with the 100.14.19 X driver and X failed to start as a result. This is a known Ubuntu bug. Please see the forum sticky posts, and report this bug to Ubuntu."

[http://www.nvnews.net/vbulletin/showthread.php?t=101888]("http://www.nvnews.net/vbulletin/showthread.php?t=101888")

So . . . . now what?

**EDIT**

Here is more information on this problem:

*Specific to this issue*

[URL="https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/136838"]**Bug #136838 in linux-restricted-modules-2.6.22 (Ubuntu)**
wrong nvidia kernel module (7185 instead of 100.11.14) loads at boot time (manual install)[/URL]

*Specific to the nvidia-glx-new driver*

[URL="https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641"]**[nvidia-glx-new] Driver is missing libwfb breaking X on 8000 series cards**
The 9755 nvidia driver includes a new file called libnvidia-wfb.so.1.0.9755 and two symbolic links to that file, libnvidia-wfb.so.1 and libwfb.so.1. These files are not included in the linux-restricted-modules package.[/URL]
[I]Note:  After skimming through this bug report it is apparently not limited to 8000 series cards.  Many people, including myself, are experiencing the same problems.
[/I]
**More useful information**
[I]
From Ubuntu Documentation[/I]

[**NvidiaManual**]("https://help.ubuntu.com/community/NvidiaManual")
HowTo manually install the downloaded Nvidia drivers (not recommended by Ubuntu)

[**BinaryDriverHowto/Nvidia**]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
This guide is for installing the NVIDIA closed source binary drivers on a system running an NVIDIA graphics card.

So, the bottom line is the nvidia-glx drivers are broken for a fair number of us unfortunates.  I sincerely hope that this info is useful for you all!

Now, where did I leave my Feisty disc?

---

### Post by robrmd9 on 2007-11-07
Using nvidia-glx is not downgrading - it's the "official" binary nvidia driver for Ubuntu.  I don't understand why you would use nvidia-glx-new unless your card is not supported by nvidia-glx.

It doesn't make sense to go through all of this runaround if you haven't tried the "official" driver.  I'm saying this because my 6800 works perfectly with nvidia-glx.

By the way, nv is the free open source driver, which doesn't have 3d support - it is NOT nvidia-glx. 

So what should you do?  Uninstall nvidia-glx-new, install nvidia-glx, run "sudo nvidia-glx-config enable" and then see if your setup works.

---

### Post by fooman on 2007-11-07
nvidia 7950gt here.  kubuntu fiesty install upgraded to gutsy.  nvidia-glx-new does not work for me either...i get the exact same error as the original poster (640x480 resolution).  i have the ubuntu desktop installed as well and have tried installing the latest drivers thru every avaliable means, restricted drivers in gnome,  manually, and with envy....all with the same results: 640x480 resolution.  

i finally gave up and settled on using the nvidia-glx drivers installed thru synaptic.  it is version NVIDIA 96.39

i'd love to get the latest drivers installed so i will keep tabs on this thread and hope someone finds a solution.  until then,  these 96.39 drivers are running just fine.  i have absolutely no issues with any 3d games, apps, screensavers, compiz-fusion...everything is running great,  i'd just like to have a look at the latest drivers to see if there are any performance gains to be had.

---

### Post by Anlace on 2007-11-07
Hi robrmd9,

I tried what you suggested and installed nvidia-glx, then from a terminal "sudo nvidia-glx-config enable" I restarted the xserver and it fired up fine.  Then I went to my xorg.conf file and it was using the nv driver.  I hand-edited it to nvidia and restarted X again.  No KDM, no graphics, only a console login.  Edited xorg.conf back to using nv so I could get back into KDE.

Who knows, maybe at this point because I have tried so many different ways of making this work that I've borked my system.  And I'm simply sick and tired of trying to make it work.

Thanks again for your replies and suggestions.

Peace,
Gail

PS  Prior to installing nividia-glx I removed/uninstalled all instances of nvidia drivers that I could find.

---

### Post by fooman on 2007-11-07
anlace,  i should have metioned in my above post that i also have the viewsonic vx2025wm.

don't know if it matters but in addition to installing the nvidia-glx with synaptic,  i also installed the nvidia-kernel-source that matches the nvidia-glx version....*not* the nvidia-*new*-kernel-source.

i have also done some heavy editing of my xorg.conf....heres the pertinent parts:

Section "Monitor"
    Identifier     "ViewSonic VX2025wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Nvidia GeForce 7950 GT"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia GeForce 7950 GT"
    Monitor        "ViewSonic VX2025wm"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by Anlace on 2007-11-07
Hi fooman,

That looks a lot like my xorg.conf file from Feisty where everything worked great.

When I used Synaptic to install nvidia-glx-new I also installed all of the stated dependencies and trusted that the correct nvidia-kernel-source was part of that.  My guess is that hosed dependencies may be part of the unresolved bug.

Just an FYI for you all - the nvidia-glx driver is identified by Ubuntu as the 96xxx driver (see [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)) and on Nvidia's web site the 96xxx driver is described as a "Legacy" driver (see [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)).  I imagine that most video hardware would be downward compatible to an earlier version of driver.

Wouldn't it be great if it were possible to be able to use the latest drivers for our hardware?  Maybe I am hoping for too much at this point but it does dampen my enthusiasm for wanting to jump on the "newly released versions" bandwagon.

Peace,
Gail

---

### Post by paulmac on 2007-11-07
AMD64, MSI FX5200 Nvidia, Gutsy 7.10.
Nvidia drivers from Automatix.  
A few system hangs now and then also did this with an ATI 9800.  
No problems with display and only 1gig of ram.

---

### Post by Tarmael on 2007-11-07
Hi all.

I'm trying to install the Nvidia drivers on a mate's computer and I'm also getting the same error with the nvidia-glx (NOT nvidia-glx-new, tried that also.) driver as Anlace (Gail) my error seems to be the exact same only difference is I'm using a 6600GT and GNOME.

I haven't tried Envy yet.

I've had problems before on my own machine using ATi drivers, so I've been doing a fair amount of editing of xorg.conf so I've picked up a few tricks here and there.

I've tried restricted drivers manager 
I've tried dpkg-reconfigure -phigh xserver-xorg
and I've tried editing the xorg.conf file myself, changing nv to nvidia.

I'm almost all out of options here, except Envy

Cheers, 
Bas

---

### Post by Anlace on 2007-11-07
Update here.

I reinstalled and am sitting at a computer with nothing on it except Ubuntu command line, Xorg and kde-core.  I used Synaptic to go get the Restricted Drivers package for KDE, installed that and used it to get the Nvidia driver.  I'm back in the same boat, the highest resolution that I can get is 640x480 using the Nvidia driver.

I'm on the Nvidia forum site now [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/) and I have learned a few things.  The first is that my initial problem arose from trying to "fix" the nvidia-glx-new driver by using first Envy and then the downloaded driver from Nvidia.  Between all of this I managed to find a problem with mismatched kernel/driver.

Now with a barebones installation I am finding out a clearer picture of what's going on.  It seems that Nvidia's drivers are weak in the area of picking up monitor EDID (the information your monitor gives the driver about resolution, refresh rates, etc).  This is what my xorg.0.log looks like, this is where the trouble is:

[INDENT](WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 GS (NV41) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.41.02.47.0e
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 GS at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1280x960"; removing.
(WW) NVIDIA(0): No valid modes for "1152x864"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.[/INDENT]

You can find this log in /var/log, take a look, maybe you are having the same problem.

I am reading about this in the Nvidia forum and will post my findings here, I am keeping notes people!

Peace,
Gail

---

### Post by Anlace on 2007-11-07
***SIGH***

None of it worked, not a thing and I have been sitting here for close to 9 hours trying to make it work.

I've got my Feisty CD out.  Good bye Gutsy!

Good luck to you all, I will continue to watch this forum.

Peace,
Gail

---

### Post by Anlace on 2007-11-08
Hurray! An hour later, Feisty installed and nvidia-glx-new working like a charm.

Maybe next time Ubuntu.

---

### Post by eye208 on 2007-11-08
> **Anlace said:**
> The "Restricted Drivers/Devices Manager" is in GNOME
*"As of Kubuntu 7.10 (Gutsy Gibbon) the recommended way to install the binary driver is to open System Settings KMenu &#8594; System Settings, go to the Advanced tab and click Restricted Drivers. Then click the Administrator Mode button and check the box marked Enable to install the driver. This should install the right package for your card and set it up for you."* ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-26d824c59899f7a5692f83a8ffb1100498bd1ee1](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-26d824c59899f7a5692f83a8ffb1100498bd1ee1))

> as I stated in my post I am using KDE so this pointless comment doesn't really apply now does it?
Have a nice day.

---

### Post by Rumo on 2007-11-08
> **eye208 said:**
> *"As of Kubuntu 7.10 (Gutsy Gibbon) the recommended way to install the binary driver is to open System Settings KMenu &#8594; System Settings, go to the Advanced tab and click Restricted Drivers. Then click the Administrator Mode button and check the box marked Enable to install the driver. This should install the right package for your card and set it up for you."* 


So what? That doesn't work either. Just because you didn't have any problems with the nvidia-driver-install does not mean that everybody who does have problems is stupid.

---

### Post by eye208 on 2007-11-08
> **Rumo said:**
> So what? That doesn't work either.
The difference between an unsupported method and a supported one is that the developers will feel inclined to fix bugs affecting the latter if you file a bug report.

On the other hand, comments such as "Maybe next time Ubuntu" won't impress anyone.

---

### Post by Anlace on 2007-11-09
Hello eye208,

You are completely correct in what you said and in your advice.  I owe you an apology and it should have been said earlier.

I did find that there was a package I could install for the approved and automated way of installing restricted drivers and I'm also very sure that it works for almost everyone.  It did _not_ work in my case.

The second time I attempted to get a fresh installation of Gutsy to work with Nvidia drivers I did these steps in this order:
[INDENT]install Ubuntu command-line
add universe/restricted/multiverse/medibuntu/back-port/canonical repositories to /etc/apt/sources.list
apt-get update
apt-get dist upgrade
apt-get install Xorg
apt-get install kde-core
apt-get install kdm
apt-get install Synaptic
installed the Ubuntu restricted drivers utility for KDE with all recommended dependencies[/INDENT]
Then went through all of the proper steps to install the recommended (nvidia-glx-new) driver, enabled it, checked that all of config files were correct then rebooted . . . . . Same problem, I could only get 640x480 resolution even though everything in xorg.conf etc was peachy.

You are also right about my comment "Maybe next time Ubuntu."  It is a flame-bait statement, and I apologize for that too.  It was said out of pure frustration with trying to get my system to work with good drivers on a great OS and spending three days trying to make it work.

Interestingly enough everything installs like butter on hot bread with Feisty, no hitches at all.  The nvidia-glx-new drivers rock in Feisty where it they were hopelessly broken in Gutsy.  Today I am happily sitting here dialing in Compiz, something I would love to have been able to do with Gutsy.  I am disappointed, but then again . . . . maybe the next release will work better!  ;-)

Peace,
Gail

---

### Post by fuzz500 on 2007-11-15
Hello Hello....
I too was quite disappointed to "upgrade" to gutsy, with my new nvidia 8600 (sweet!) and a big fat 500 gig hard drive (also sweet!), only to find that the nvidia driver, the screen resolution applet, and the "new" screens and graphics applet in the admin menu, were all completely useless pieces of crap <sigh>

In any case I tried a few different things, used the restricted devices manager, which has been quite useful in several other installs, all to no avail. I remembered that the nvidia driver installer NVIDIA-Linux-x86-100.14.11-pkg1.run was what I used on ubuntu 7.04 (which worked) and decided to go that route again... It worked. Here's what I did:

EDIT - NEWS FLASH ----
The steps listed below may not be a definitive solution! When I cold booted the next day, the nvidia driver did not load due to an API Kernel mismatch... I think it is a file permission problem... will report back... hope this can be useful to somebody...F500
END - NEWS FLASH -----

news flash 2
---------------
As suspected there was some kind of file permission glitch or who knows what, but basically I booted into command line, managed to initialize to runlevel 3 ( init 3), switch terminals, kill the x server, switch to super user, then did the driver install again, put my custom xorg.conf file back, rebooted, and back to double screen goodness with compiz all over it. Details for the bored or those grasping for more are at the bottom of this post. This method worked for me, I think the key was to do the nvidia driver install the nvidia way and forget using restricted driver manager and the other crapplets for screen resolution etc. Good luck!
--------------------
end news flash 2



1. boot to xwindows (i.e. regular graphical boot)

2. get the proprietary nvidia driverat [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

3. stop xwindows - in gnome it is "sudo /etc/init.d/gdm stop", in KDE use kdm (I think) instead of gdm (if you boot straight to the command line you obviously don't have to stop your x server) You should now be at the command prompt.

4. You have to change your runlevel to runlevel 3 because the nvidia driver will complain:
sudo telinit 3 - if it launches x windows again, switch to another terminal (ctrl-alt-2) and to the gdm stop again.

5. also you may have to get the c programming library because the next step may require it to do the compile (I needed it)
sudo apt-get install build-essential linux-headers-`uname -r`

6. change to the directory where you downloaded the nvidia driver and do the install
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run 
NOTE - it may be better to become superuser (sudo su), then do "NVIDIA-Linux-x86-100.14.11-pkg1.run"

7. in my case, it could not find a compatible binary file, so it went thru the compile process. just follow the prompts

Great, so the driver was now installed, and so was the nvidia-settings applet which should now show up in your main menu under system tools | Nvidia X Server Settings. This applet may allow you to configure your screen sufficiently.

In my case I have two 19 inch dell crts sitting side by side, so I tried to configure twinview with the nvidia-settings applet, but it was flaky, and kept crapping out saying that there were problems with the metamode strings or some such nonsense. So I had to hand configure the /etc/X11/xorg.conf file.

Basically I just cut out any unneccessary lines and forced it to bare essentials. The key for me was the twinview line and the metamodes line below. There is still a problem where the driver won't remember from boot to boot what the desired screen resolutions were (I prefer 1600x1200 on both monitors. 

The system now boots up to twinview (both monitors on) but forgets my preferred resolution... order of the metamodes on the metamodes line doesn't seem to make any difference. I'm now trying to figure out where the nvidia driver keeps it's settings. EDIT - I think I have a solution for that now ... using gconf-editor went to desktop/screens/0 and set the resolution to the 3200 (combined width of the 2 screens). I worked from boot to boot.

I've included my xorg.conf file for your interest. Good luck !!



# nvidia-xconfig: X configuration file generated by nvidia-xconfig
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
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
    Load           "i2c"
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
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL P991"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nvidia8600"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nvidia8600"
    Monitor        "DELL P991"
    DefaultDepth    24

    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1600x1200 +0+0, CRT-1: 1600x1200 +1600+0; CRT-0: 1024x768 +0+0, CRT-1: 1024x768 +1024+0; CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0; CRT-0: 1920x1200 +0+0, CRT-1: 1920x1200 +1920+0;"

    SubSection     "Display"
        Depth       24
        Modes      "3200x1200" "2560x1600" "2048x1536" "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection


<Additional Rambling>
-----------------------
this was fixed... this portion of narrative may give some extra insight

The story is not over. When I cold booted this morning, my machine did not boot up to 3200 pixels 
wide of glorious compiz desktop... no. X wouldn't load and I got a crappy vesa driver asking me 
whether I wanted 800x600 or 640x480 in failsafe mode. Well, to make things work, x wouldn't start
in failsafe mode so I was snafued. Ok, so I sniffed around and restored my xorg.conf to the load 
the nvidia driver, and I got a message from the x log (I think): API / Kernel mismatch. I've seen this
before... I don't understand why it rebooted several times yesterday and worked perfectly, but then 
on a COLD boot, this problem. I suspect it has something to do with file permissions, I installed
the nvidia driver by running "sudo sh NVIDIAxxx.run", and not logged into the command line as 
root. In any case I think my xorg.conf should work as soon as I get the video driver re-installed
BUT, I can't switch to runlevel 3 because as soon as you run "telinit 3" 
it tries to start x windows! Argggg. I need to boot into runlevel 3, which is proving to be
a lot more complicated than it seems it should be. I booted into non graphical mode, then 
managed to do init 3... the graphical terminal came up, I selected ctrl-alt-2 to get another
terminal, logged in as regular user, then did an x shutdown, sudo /etc/init.d/gdm stop.
That killed x, then I navigated to the driver directory and did sudo su to become root
then I did the driver install, then I put my xorg.conf file back in place, then I booted
then it worked. Phew. Looks pretty good now. Actually after configuring compiz with reflections
and cube tops, etc, it looks amazing. Back to 3200 pixels of goodness. 
<end rambling>

---

### Post by 2square on 2007-11-21
Alright guys. This thread has been very informative. I had a similar problem after I did an automated update. I guess it changed some of the gl drivers. I had Beryl flying on Feisty. But here I was stuck with a 800x600 resolution on Gutsy. I was about to go back to Feisty, but decided to give it one last try. Here's what I did, and surprisingly most of this has already been covered in this thread. I worked for me. You guys might want to give it a try before deciding to go back to Feisty.

To fix the resolution problem, I did the following

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

This is documented here [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Next, to install the Nvidia Drivers (I have a GeForce 7300), I followed the manual installation as given here [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

And that's it. I'm back on track. \\:D/

Let me know if this works for you. Thanks again guys, specially to Anlace for starting this thread!

---

### Post by cainmark on 2007-11-21
> **Anlace said:**
> Hello eye208,

Interestingly enough everything installs like butter on hot bread with Feisty, no hitches at all.  The nvidia-glx-new drivers rock in Feisty where it they were hopelessly broken in Gutsy.  

Thanks for this thread.  I tried the official way first, several times, which told me to restart, then I was stuck at low resolution, then tried all the methods you posted, and my Gutsy desktop is still stuck at 800x600.  I have an nVidia 5200fx, and older card, and I think that may be the problem.  It worked fine in Fiesty after I installed the nvidia driver.  I also have a wacom tablet that works fine in fiesty, but won't work right in Gutsy (just the pen works, not the mouse), so it's back to Fiesty for me.  I was going to try a fresh install of Gutsy, but the same wacom tablet problem is preventing me, and it keeps saying the nvidia official update for the restricted driver is broken and won't load.

Sorry, I have no solutions either.  Back to Fiesty for now.

---

### Post by mlkv on 2007-11-22
No luck here as well. I've tried everything to have my (very old) nVidia GeForce 256 work properly.. the worst effects I had while using Envy (which completely messed with my system), but none of the guides I've found online helped me.

nvidia-legacy drivers might be an ever bigger pain than the average I guess?

Well, I don't really need any specific acceleration on this old desktop.. I only use it to surf the web so it's going to stay without 3D-accel until somebody comes up with a solution for Gutsy.

PS: The restricted manager was super annoying. :\

---

### Post by starcannon on 2007-11-22
I'm using Nvidia Drivers that I downloaded right from the Nvidia site, 
	
Linux Display Driver - x86

Version: 100.14.19
Operating System: Linux x86
Release Date: September 18, 2007 

I have a 6600gt w/Gutsy, a set of twin 7950gt's in SLi mode, and an 8400m GS. Drivers work on all 3 cards, though the 8400m GS needs work (it still renders fine, it can be slow at times though)

Anyway, how I do it is
Back up my /etc/X11/xorg.conf to somewhere safe, then;
CTRL-Alt-F1
```

Login
Password
sudo /etc/init.d/gdm stop
sudo apt-get install build-essential
cd /Downloads
sudo chmod a+x ./NVIDIA*.run
sudo ./NVIDIA*.run

```
I then answer affirmatively to all on screen prompts, then;
```
sudo /etc/init.d/gdm start
```
Note, you may need to purge old drivers first if you have installed any from synaptic or some other source.

---

### Post by gutsynut on 2007-12-13
I'm new to Linux, but have 15 years development experience with mostly MS environment. I have to say I'm impressed as heck so far with the exception of the proprietary (go figure) nvidia drivers for my 7950GT.

Trying like mad to get this to work with dual monitors, edited the xorg file, used envy, most of the standard suggestions have been tried to no avail.

Wondering what gives?  Always reboots into low res mode, and I can't get my workspace to extend to both monitors unless it's in clone mode.  Have not found a thread to alleviate my problems.

If I can get this to work, and if my 3D games work with WINE, I will NEVER install another MS product as long as I live.  Please help me with this goal.  I must be missing something, maybe a simple fix?  Anyone with a dual setup have a working xorg for duals that works when you reboot?

---

### Post by Macrosoft on 2007-12-13
> **Anlace said:**
> Greetings,

The "Restricted Drivers/Devices Manager" is in GNOME, as I stated in my post I am using KDE so this pointless comment doesn't really apply now does it?


the package for the restricted drivers manager in kde is restricted-manager-kde

---

### Post by use a name on 2007-12-14
Currently, I'm using the 100.14.09 mdriver, but I also needed to add these lines to the device section of my xorg.conf:
```

    Option "NvAGP" "0"
    Option "IgnoreDisplayDevices" "DFP,TV"
    Option "TripleBuffer" "True"

```
I just put these lines in, as they saved my day in Feisty and with older drivers. It might also work with the new driver, of course, but I haven't tested that yet. (And iirc, the first line is most important, but I'm not going to trial and error now.)

---

### Post by rjcope728 on 2007-12-15
Geforce2 Ultra Bladerunner, still not right. VERY Frustrated! I'm not a big gamer or need fantastic graphics, but this "video driver issue" seems to plague so many people, I would think it would have been solved by now by all the genius' here. lol. 
Found this thread, which like many other very helpful threads here, leads to exhaustive command line work. I'm admittedly a newbie, and don't like to mess with typing in tons of command line stuff.  I understand it is the most direct way to program a computer, but are all the little fuzzy headed children who get these new XO computers going to have to learn C++ to operate their puters? I think not, they will wait for Uncle Bill G to seduce them with his wares. Which will load up easily & work flawlessly with ALL video cards. Then he lead them to the world of viruses and commercial BS. 
  Please someone resolve this "video driver issue" or tell me what brand of video card to buy and I'll buy it. 

I saw earlier in thei thread where another frustrated person made a statement about going back to an earlier distro and got called down for it. Good for him for complaining, it seemed to get someones attention, but the reply wasn't a real solution.
 I'm not trying to start anything, I'm just curious, after reading about a gazillion thhreads and posts, why there is still and issue. 
BTW, I understand the philosophy of ubuntu and love it, so we don't have to go there in the sure to follow replies.  I'm not giving up yet, but I am typing this on my XP Machine because it works.  RiK :lolflag:

Update - Go get ENVY for Nvidia problems - it will load up whatever you need - what a cry baby, huh?

---

