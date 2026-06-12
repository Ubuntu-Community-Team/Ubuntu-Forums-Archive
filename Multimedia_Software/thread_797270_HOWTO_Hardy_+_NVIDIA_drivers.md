---
title: "HOWTO: Hardy + NVIDIA drivers"
date: 2008-05-17
forum: Multimedia Software
---

### Post by Xiong Chiamiov on 2008-05-17
[SIZE="3"]**Attention!**:[/SIZE] it seems that the new version of [envy]("http://albertomilone.com/nvidia_scripts1.html") has finally gotten the new drivers, so you should be able to install it (with its nifty GUI configuration!).  Haven't tested myself, but definitely try that first.
**2008-06-15**: Took envy for a spin today, and it lists 169.12 as the NVIDIA driver (for the series that needs 173, that is).  I think it's just hardy-proposed that it's gotten to, so who knows how long that'll be 'til it gets to us.

~~~~~~~~~~~~

I've been typing this out quite a bit recently, so I though I'd just make a well-formatted post to link to.

Before we start, let me tell you that most of this code you can directly copy and paste.  The part about killing X that's in bold is the only part that will vary, and you just use the number that's in bold for the first part in the second.

The kernel in Hardy is causing problems with the NVIDIA drivers included in the repositories, so we need to download and install the newest drivers.

From [here]("http://www.nvidia.com/object/unix.html"), download the 173.14 driver (first one listed).  If you're using 64-bit *buntu, download the 173.14 from the 3rd section, the one entitled "Linux AMD64/EM64T".  Save/move to your home directory.

Write down these instructions, because we're going to be dropping to a command-prompt.
Press ctrl+alt+f1, then enter these commands:
```

sudo apt-get remove --purge nvidia*
sudo apt-get install linux-headers-$(uname -r) libc-dev build-essential
cd ~
sudo /etc/init.d/gdm stop
sudo sh NVID[tab]
sudo /etc/init.d/gdm start

```

If you're using KDE3, replace gdm in the fourth and sixth lines with kdm; KDE4 users replace with kdm-kde4.  Xubuntu users will also use gdm.
If stopping the window manager doesn't bring you back to a prompt, press alt+f1 again to do so.

Make sure that when the installer complains about the versions of GCC not matching, you select "no".  This will continue the installation.
I would recommend that you select "yes" when the installer asks if you want it to generate an X configuration file.  It will create a backup of your current one in /etc/X11 if you need it.

After doing this, I recommend you follow vor's [excellently-constructed guide]("http://ubuntuforums.org/showthread.php?t=835573") for keeping your NVIDIA drivers working after a kernel update.

~~~~~~~~~~

If you're getting an error with the installer saying that X is running:
First run
```

ps -ef |grep X (make sure that's a capital X!)

```
You should see something like this:
```

root     **14341**  5346  2 20:05 tty7     00:00:16 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-G56yJI
pearson  17629 14881  0 20:16 pts/0    00:00:00 grep X

```
Take a look at the number that I put in bold.  Then kill X like so
```

sudo kill -9 **14341**

```
changing the last number to what it was for you when you ran the previous command.

[Alternate trick #1.]("http://ubuntuforums.org/showthread.php?p=4970051#post4970051")
[Alternate trick #2.]("http://ubuntuforums.org/showthread.php?t=792276#5")

[Nullack had to]("http://ubuntuforums.org/showthread.php?p=5148785#post5148785") make a few adjustments to his Xorg.conf to get his to work on a fresh 64-bit install.

If this doesn't work, you find an alternate solution, or you had to do something in addition, please let me know so I can update accordingly.  We want to reduce pain for others, right?

Also, the well-formatted post I originally started off with has grown rather... well, it's not as good as it could be.  However, I am rather bad at things this long, so if anyone would like to reorganize/reformat anything to make it a bit more friendly, then just let me know!

---

### Post by Aardolan on 2008-06-03
The link to nvidia's site you provided goes to the archive of drivers. The latest driver I've found so far is [173.14.05, for 32 bit users](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html). I didn't look for a 64 bit version, since I don't use 64 bit, but I'm sure it exists, as well.

---

### Post by Xiong Chiamiov on 2008-06-03
> **Aardolan said:**
> The link to nvidia's site you provided goes to the archive of drivers. The latest driver I've found so far is [173.14.05, for 32 bit users](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html). I didn't look for a 64 bit version, since I don't use 64 bit, but I'm sure it exists, as well.
Ah, thank you.  When I wrote this, 173.08 was the latest, and I hadn't checked since then.  Updated.

EDIT: Or not.  The forums aren't letting me save changes to that post (db error, though this one works just fine), so I'll update it later.

---

### Post by philinux on 2008-06-03
I'm currently using nvidia-glx-new from the repo. What difference will this driver make.

Thanks.

---

### Post by Xiong Chiamiov on 2008-06-03
Last I checked, the drivers in the repos weren't the most up-to-date, which meant they didn't have some of the fixes that NVIDIA put in to deal with the new kernel in Hardy.  It [looks like]("http://packages.ubuntu.com/hardy/nvidia-glx-new") the repo version is 169.12, which caused endless rebooting for [some people]("http://ubuntuforums.org/showthread.php?t=785074").  If it's working for you, then I don't think there are any specific benefits.

---

### Post by Aardolan on 2008-06-06
I've tried nvidia-glx-new, as well as the latest three drivers from Nvidia, and they all make my desktop look like someone took an Xacto knife to them. Guess I'll have to wait and see if this gets fixed for my specific card later, or until I can save up for a new PC. I'm currently using (apparently) a GEForce 6200A

---

### Post by Xiong Chiamiov on 2008-06-08
Hmm, sorry to hear that.  If you do get it working, though, please tell me what you did.

---

### Post by Unix_Slayer on 2008-06-08
[IMG]http://mysite.verizon.net/mgm_mgm/realnv.jpg[/IMG]

---

### Post by Xiong Chiamiov on 2008-06-08
I'm sorry; what is this supposed to mean?  I oftentimes require a bit more explaining perhaps than most people.

---

### Post by Unix_Slayer on 2008-06-08
> **Xiong Chiamiov said:**
> I'm sorry; what is this supposed to mean?  I oftentimes require a bit more explaining perhaps than most people.

The latest drivers are the working drivers. Each time the kernel is updated, the video drivers need to be re-installed. So goes with the wireless network drivers as well.

---

### Post by Xiong Chiamiov on 2008-06-08
> **Unix_Slayer said:**
> The latest drivers are the working drivers. Each time the kernel is updated, the video drivers need to be re-installed. So goes with the wireless network drivers as well.
This is correct.  Of course, it would solve problems if the repo was updated, but it's still at 169.12.  However, some people are operating just fine on old drivers (eg, nvidia-glx-new), and some (like Aardolan) can't get it to work even with the newest drivers.

---

### Post by sonoma_jack on 2008-06-08
X- "From here, download the 173.14 driver (first one listed). Save/move to your home directory."

to show my complete freshman knowledge, how does one move to home directory?

---

### Post by Unix_Slayer on 2008-06-08
> **Xiong Chiamiov said:**
> This is correct.  Of course, it would solve problems if the repo was updated, but it's still at 169.12.  However, some people are operating just fine on old drivers (eg, nvidia-glx-new), and some (like Aardolan) can't get it to work even with the newest drivers.

The old drivers are slow though..... I've been using the newest driver so far, and it's been phenomenal. And between you and I, it's pretty easy to install the newest driver. What driver are you using? And what card are you using btw.

---

### Post by Unix_Slayer on 2008-06-08
> **Aardolan said:**
> I've tried nvidia-glx-new, as well as the latest three drivers from Nvidia, and they all make my desktop look like someone took an Xacto knife to them. Guess I'll have to wait and see if this gets fixed for my specific card later, or until I can save up for a new PC. I'm currently using (apparently) a GEForce 6200A

The newest driver should run your card. The nvidia-glx-new is not running par excellence, and I would consider installing the latest, and greatest. Shouldn't it Xiong Chiamiov.

---

### Post by Xiong Chiamiov on 2008-06-08
> **sonoma_jack said:**
> X- "From here, download the 173.14 driver (first one listed). Save/move to your home directory."

to show my complete freshman knowledge, how does one move to home directory?

Well, you could of course use the command line, but the far simpler way would be to use Nautilus (the filemanager).  I assume that Firefox still saves files by default to the desktop (and that you're using Firefox, not to mention GNOME), so you would just go to Places -> Home Folder (at the top left) and drag it in there.

The file doesn't need to be there per se, but then you don't have to find it through the command line when you get to the installation step.

> **Unix_Slayer said:**
> The old drivers are slow though..... I've been using the newest driver so far, and it's been phenomenal. And between you and I, it's pretty easy to install the newest driver. What driver are you using? And what card are you using btw.

Everything is working just peachily for me using 171(?) I think, on a 6800GT.  While I may think that the installation of the driver is fairly easy, knowing what to do is not intuitive, and there are many people who frequent these forums who would not find the procedure "easy".  You must remember that this is *buntu; this is the first (or possibly, the first positive) experience for many with Linux (myself included).

> **Unix_Slayer said:**
> The newest driver should run your card. The nvidia-glx-new is not running par excellence, and I would consider installing the latest, and greatest. Shouldn't it Xiong Chiamiov.

While my experience would say so, he specifically said that he had tried the latest drivers, and they produced... less than spectacular results.  I have a different card than he, and am running on 32-bit (as opposed to 64-bit).  Those alone remove any presumption on my part that I *know* how things will work for him, much less the difference that comes from customization and use of individual's computers.

---

### Post by Unix_Slayer on 2008-06-09
> **Xiong Chiamiov said:**
> Everything is working just peachily for me using 171(?) I think, on a 6800GT.  While I may think that the installation of the driver is fairly easy, knowing what to do is not intuitive, and there are many people who frequent these forums who would not find the procedure "easy".  You must remember that this is *buntu; this is the first (or possibly, the first positive) experience for many with Linux (myself included).

While my experience would say so, he specifically said that he had tried the latest drivers, and they produced... less than spectacular results.  I have a different card than he, and am running on 32-bit (as opposed to 64-bit).  Those alone remove any presumption on my part that I *know* how things will work for him, much less the difference that comes from customization and use of individual's computers.

I've been installing Ubuntu desktops on a lot of clientele's lately. Way more than Windows. I've gotten so used to installing these drivers, that I do them in my sleep. Of course I always recommend the easier, and better chips to include in a new desktop. This makes the install so much more rewarding.

---

### Post by Nullack on 2008-06-09
On a fresh hardy install this didnt work first off. I had to install the libc development files so that the nvidia kernel module would compile. I then ran the nvidia shell script, choosing not to support 32bit open gl compatability mode on my amd64 hardy install. Dunno if thats the wrong choice or not :)

xorg.conf - Editied my monitor for the right v and h sync values, turned off dynamic twin view and the nvidia splash and its all good.

---

### Post by Xiong Chiamiov on 2008-06-09
> **Nullack said:**
> On a fresh hardy install this didnt work first off. I had to install the libc development files so that the nvidia kernel module would compile. I then ran the nvidia shell script, choosing not to support 32bit open gl compatability mode on my amd64 hardy install. Dunno if thats the wrong choice or not :)

xorg.conf - Editied my monitor for the right v and h sync values, turned off dynamic twin view and the nvidia splash and its all good.
Thanks for the info!  I incorporated the libc-dev package into the post and linked to yours for the rest.

---

### Post by Nullack on 2008-06-10
No worries :)

The reason I modify the dynamictwinview is that I dont use two monitors and due to a limitation of X, with it enabled the nvidia driver incorrectly reports the refresh rate of the monitor. I disable the logo simply because I dont want to see it on boot.

With the monitor edits, I adjust the conf to correctly deal with my monitors' valid vertical and horizontal sync ranges. Each monitor model will have different values. I find EDID doesnt always use the correct ones.

Heres my edits to xorg.conf:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Sony"
    ModelName      "CPD-G520"
    HorizSync       30.0 - 130.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option	   "DynamicTwinView" "FALSE"
    Option	   "NoLogo" "TRUE"
EndSection

---

### Post by michael_mallett on 2008-06-10
Installation guide works seamlessly on a 3-day old Hardy 64bit install, thanks very much.
The only thing that needed changing was driver version - to a 64bit driver for AMD systems and 8800GT card (located here: [http://www.nvidia.com/object/linux_display_amd64_173.14.05.html]("http://www.nvidia.com/object/linux_display_amd64_173.14.05.html") )
This was the most recent driver as of 10th June 2008 12:00 GMT.

Thanks again.

---

### Post by Xiong Chiamiov on 2008-06-10
> **michael_mallett said:**
> Installation guide works seamlessly on a 3-day old Hardy 64bit install, thanks very much.
The only thing that needed changing was driver version - to a 64bit driver for AMD systems and 8800GT card (located here: [http://www.nvidia.com/object/linux_display_amd64_173.14.05.html]("http://www.nvidia.com/object/linux_display_amd64_173.14.05.html") )
This was the most recent driver as of 10th June 2008 12:00 GMT.

Thanks again.
Ah yes, I had a separate link for the 64-bit driver for a little bit, but when I updated something it sorta diappeared.  Thanks for reminding me.

---

### Post by Pyoro on 2008-06-10
First of all, thank you for taking the time to post this! :)
But unfortunately, it didn't work for me. :(

I did everything and after typing startx it actually worked, but after rebooting, it "tries" to start X (I can see the screen with the X-shaped cursor for a split second) then it drops to the command prompt. After a few seconds, it tries again, and the same thing happens.

If I redo everything in the tutorial, it works again after startx, but when I reboot, I get the same error.

I'm using 64-bit Kubuntu 8.04 and my video card is a GeForce 8400M GS. Any help will be much appreciated :)

---

### Post by Xiong Chiamiov on 2008-06-10
So it worked until you rebooted?  That's half the battle!

That's actually what I was originally having problems with when I was first doing this.  Some said to make sure kdm's stopped first, and others said [to delete some modules]("http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847").  In the end, I had to install the latest (then beta) driver to get it working, but it's possible that one of the other things I did was partially reponsible, so try that out and see if it does anything.

---

### Post by Pyoro on 2008-06-10
Never mind! It's working! :D

When I entered **sudo apt-get remove --purge nvidia***, it compiled a new kernel (2.6.24-18-generic). When I rebooted before, I selected this one, but now I selected the old one (2.6.24-16-generic) and it's working perfectly!

Thanks again for the howto and for the fast reply! =D>

---

### Post by Nullack on 2008-06-11
I wouldnt be running an old kernel though.

Basically the process is:

Install libc dependency
Block out nvidia-new from restricted drivers
Goto console ctrl+alt+f1
shutdown gdm and x
remove and purge all existing nvidia packages
sudo sh NVID tab to run the nvidia sh script
Set nvidia to configure x,org conf
Review x.org conf for your setup

---

### Post by Nullack on 2008-06-11
FYI : just saw an email that Envy is hitting hardy proposed with 173 driver support in it...will make it easy

---

### Post by Xiong Chiamiov on 2008-06-11
> **Nullack said:**
> FYI : just saw an email that Envy is hitting hardy proposed with 173 driver support in it...will make it easy
That will be nice.  However, I've been waiting for them to update the nvidia-glx-new package, especially since there are quite a few people who are having problems with it.  If either package gets updated, I'll adjust the directions accordingly as soon as I know.

---

### Post by Nullack on 2008-06-12
Yeah, Ubuntu seem reluctant to do driver updates to an existing distro release.

I think its a shame because drivers have bugs and in some cases, those bugs are serious.

Not having the distro update the driver and the user manually updating provides other grief when the distro updates its kernel. Then the user has to re-estibalish the kernel module to taint it up from default.

---

### Post by xaris106 on 2008-06-12
Nice info. I followed the instructions but I had some problems. I am new to Linux and I am using Ubuntu Hardy for about a week, although i am familiar with PCs.
basically i followed the instructions:

```
sudo apt-get remove --purge nvidia*
```  >> worked

```
cd ~
``` >> i had the nvidia file on desktop so i used ```
cd Desktop
```

```
sudo chmod +x NVIDIA[press tab to autocomplete]
``` >> i did that, dunno why though, no errors

```
sudo /etc/init.d/gdm stop
``` >> worked

```
sudo ./NVID[tab]
``` >> didnt work i had to do (working in ~/Desktop) :
```
sudo **sh** NVID[tab]
``` >>worked but i had no idea what was going on so i entered the options just guessing. i chose not to dowload something from nvidia (kernel-ish) and i agreed for 32bit support. might be forgeting some stuff also.more info for the nvidia installer please...

```
startx
``` >> problems , basically i got errors all over the place but i was in X, user switch didnt work and i couldnt shut down /restart pc from red button thingy at top right.

So I went back to console and looked at the things i did and i figured to start the gdm thing again ```
sudo /etc/init.d/gdm start
``` and all worked fine.

I hope it helps someone with the same problems as me.

---

### Post by rosali on 2008-06-12
Will this work with an older card? I have a GeForce2 and I have been struggling to make it work correctly. I'm stuck with a super low resolution that's driving me nuts... I installed the nvidia-glx-legacy package but I can't configure it. 
Thanks in advance.

---

### Post by Xiong Chiamiov on 2008-06-12
> **xaris106 said:**
> 
```
startx
``` >> problems , basically i got errors all over the place but i was in X, user switch didnt work and i couldnt shut down /restart pc from red button thingy at top right.

So I went back to console and looked at the things i did and i figured to start the gdm thing again ```
sudo /etc/init.d/gdm start
``` and all worked fine.

Startx isn't as reliable, so I changed it.

> **xaris106 said:**
> 
```
sudo chmod +x NVIDIA[press tab to autocomplete]
``` >> i did that, dunno why though, no errors

```
sudo ./NVID[tab]
``` >> didnt work i had to do (working in ~/Desktop) :
```
sudo **sh** NVID[tab]
``` >>worked but i had no idea what was going on so i entered the options just guessing. i chose not to dowload something from nvidia (kernel-ish) and i agreed for 32bit support. might be forgeting some stuff also.more info for the nvidia installer please...

I was reading somewhere recently about this.  Essentially, using sh assumes that you want to run a file, so it doesn't need executable permissions.  Just running the file itself, though, requires you to first make it executable (which is what chmod +x does).  There are some technical reasons for not using sh, but I may end up switching it.

> **rosali said:**
> Will this work with an older card? I have a GeForce2 and I have been struggling to make it work correctly. I'm stuck with a super low resolution that's driving me nuts... I installed the nvidia-glx-legacy package but I can't configure it. 
Thanks in advance.
For an older card like that, you'll have to use different drivers.  Other than that, though, it should be the same.
[URL="http://www.nvidia.com/object/IO_32667.html"]
It looks like[/URL] the proper driver for a GeForce2 is the 96 driver.  The latest one from NVIDIA is 96.43.05, and the one in [the Hardy repos]("http://packages.ubuntu.com/hardy/nvidia-glx") is also 96.43.05, meaning that you can just install it that way, rather than going through this mess.  The package you need, though, is nvidia-glx, not nvidia-glx-legacy.

---

### Post by xaris106 on 2008-06-12
Ok..i had some serious ubuntu linux with those drivers as a newbie..
i was ready to do a new install at some point.

anyway i wanted to use the old drivers for...some reason, those that came with ubuntu so i added them from synaptic and all hell broke loose..
so for anyone that had messed around too much or whants to go back to using the ubuntu resticted drivers..

I figured out the hard way that the drivers from nvidia site can be removed and i strongly advise it before adding any drivers from envy or synaptic.
 DO alt-ctrl-f2 and login
```
#sudo apt-get remove --purge nvidia* (in case you have intalled any extra driver)
cd [directory of nvidia driver]
sudo /etc/init.d/gdm stop
**sudo sh NVIDIA[tab] --uninstall**
sudo shutdown -r -n
```
Now you have no nvidia driver and the system is rebooting.
Chances are you will start at low resolution and a configuration screen will pop. Use it to have some desktop and install any driver you want.
Or hit alt-ctrl-f2 again to install any driver from terminal.

---

### Post by Divide_Overflow on 2008-06-12
> **Nullack said:**
> On a fresh hardy install this didnt work first off. I had to install the libc development files so that the nvidia kernel module would compile.

I ran into the same problem on a fresh AMD64 8.04 install.  I first used the Synaptic package manager to install libc-dev and followed things step by step but the nvidia shell couldn't find what it wanted to see, couldn't download it from the web and couldn't find the right install headers.  I kept trying over and over again without success, so I'm back to a clean install and the canned restricted driver.

---

### Post by Xiong Chiamiov on 2008-06-12
I know that there is no precompiled binary for the kernel we have, but what exactly was the error after that?  The installer complained to me about using a different version of GCC to compile than the kernel was compiled with, but that didn't affect anything for me.  Granted, there have been a few kernel updates since then, so I'm curious to know.

---

### Post by Divide_Overflow on 2008-06-12
The shell produced the prompt to accept the terms, then failed to find a compiled binary.  The second prompt sought to seek for one on the web.  That was unsuccessful and it then attempted to compile one then and ended up with the final error mentioning that the install headers could not be found on the system. Is linux-libc-dev the proper package that is needed?  Are you sure there aren't any additional dependencies that are required to go on a clean install?

---

### Post by Xiong Chiamiov on 2008-06-12
Ok, I think you need the build-essential package, if you don't have it already.  Tell me if that works.

---

### Post by IanW on 2008-06-13
The updated envy has now hit the repos. Worked perfectly for me.

---

### Post by Xiong Chiamiov on 2008-06-13
Hmm, [I see]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/239115").  I don't know my way around launchpad very well, but it seems that it's fixed, for Hardy at least, though strangely, I still see the old driver in the nvidia-glx-new package.  I'll update accordingly.

---

### Post by Xiong Chiamiov on 2008-06-14
> **Divide_Overflow said:**
> The shell produced the prompt to accept the terms, then failed to find a compiled binary.  The second prompt sought to seek for one on the web.  That was unsuccessful and it then attempted to compile one then and ended up with the final error mentioning that the install headers could not be found on the system. Is linux-libc-dev the proper package that is needed?  Are you sure there aren't any additional dependencies that are required to go on a clean install?
Ok, in addition to build-essential, I think you need the appropriate linux-headers package (which I should have caught on to when it complained about lack of proper headers >.<).  Updated instructions, though hopefully we won't have to do this anymore with the new release of Envy.

---

### Post by Xiong Chiamiov on 2008-06-16
> **IanW said:**
> The updated envy has now hit the repos. Worked perfectly for me.
Since I'm lazy, this is copy-n-pasted from the first post:
> **Xiong Chiamiov said:**
> 
**2008-06-15**: Took envy for a spin today, and it lists 169.12 as the NVIDIA driver (for the series that needs 173, that is).  I think it's just hardy-proposed that it's gotten to, so who knows how long that'll be 'til it gets to us.

---

### Post by Nullack on 2008-06-19
Ok so had to reinstall Ubuntu again. From fresh install on x64, all I did was get the libc development package and download the new Nvidia 173.14.09 driver. Got Nvidia to configure X and added my usual tweaks to my xorg.conf.

I didnt have to fiddle around with the RDM or anything.

Just run the script once the dependencies on libc is met with the gdm stopped.

---

### Post by the_exodus on 2008-06-19
Well then... right when I come up with a new thread that I've had trouble installing the latest graphics driver with little help from Envy.

Ah well. I don't really care, as long as I get it running properly with both of my Geforce 9600 GT cards working.

---

### Post by Nullack on 2008-06-19
EnvyNG is nice but I like control. And caffeine :)

I should add, that I was going through the xorg.log and:

1. Most of the modules that Nvidia added to xorg.conf are loaded by default

2. The module "type1" in the log....

(EE) Failed to load module "type1" (module does not exist, 0)

So Im wiping it from xorg.conf since all seems ok anyway. Apparently it enables x to rasterize type1 fonts. Dunno if Ubuntu has type 1 fonts or not.

---

### Post by Xiong Chiamiov on 2008-06-19
> **the_exodus said:**
> Well then... right when I come up with a new thread that I've had trouble installing the latest graphics driver with little help from Envy.

Ah well. I don't really care, as long as I get it running properly with both of my Geforce 9600 GT cards working.
Were you able to get it working?

---

### Post by ktechman on 2008-06-20
Very smooth install. Thank you for the guide.:)

Regards

---

### Post by momo07 on 2008-06-20
Hi there,
I need some help pls.  I was able to install my nVidia drivers succesfuly using the envy instalation application.  Everything was working fine for two days and now my system seems not to be able to load the device. I guese it is using vesa drivers im not sure.  Here is some info regarding my machine:

OS: Ubuntu ver 8.04 Hardy
PC: Sony Vaio VGN-SZ5MN/B
Graphics Card: nVidia GeForce Go 7400 GPU

This is what I get when I run the lspci command:

```
moe@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
moe@ubuntu:~$ 

```

Please help, thanks so much

---

### Post by Zorael on 2008-06-20
> **momo07 said:**
> ```
moe@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
[B]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/B]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
moe@ubuntu:~$ 

```

Curious. I don't see any Nvidia devices there at all, only Intel integrated.

What's the output of the following?
```
$ lshw -C video
```
Also make sure that the card is seated properly (physically, in your computer casing.)

---

### Post by momo07 on 2008-06-20
Hi there thanks for your prompt response, this is what I get;

```
moe@ubuntu:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
moe@ubuntu:~$ 

```

It is a nVidia card in my laptop and I dont know why it is saying Intel.

---

### Post by momo07 on 2008-06-20
Hi there,

I ran a nvidia-xconfig and this is what I got;

```
moe@ubuntu:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

moe@ubuntu:~$ 

```

This is what my xorg.conf looks like;

```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Pls help I'm new to Ubuntu and would like to keep the os.  Thanks

---

### Post by Zorael on 2008-06-20
Well, something's dearly wrong. It doesn't see your Nvidia card at all, so it's far from a driver issue. Perhaps a kernel one.

Does it work from a live cd, or in Windows? Else I would suspect hardware failure.

---

### Post by momo07 on 2008-06-20
How do you check with a live cd?  I had the same problem before and I had to do a clean install and it worked, as with windows I don't have it anymore.

---

### Post by momo07 on 2008-06-20
Hello,

I just did a fresh install and my video card seems to be ok.  Here is what I get from typing: lshw -C video

```
moe@ubuntu:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
moe@ubuntu:~$ 



```

Is there anyway to make this permanent so I dont loose it again

---

### Post by Zorael on 2008-06-20
In that case it was likely a kernel bug of some sort; I can't imagine it being anything else. If you later apply upgrades and you notice it breaking again, try loading your older kernel and use those commands we mentioned. If it shows both as Intel devices, something's not right.

Remember, just because a kernel is newer than the one you have doesn't mean that it suits your system better. Bugs are inevitable, and you seem to have been the victim of one. Enabling other updates repositories (proposed, unsupported) in Software Sources might be a way of getting newer ones, too, which may just work for you. The grub menu will by default list them all.

---

### Post by IbnKuldun on 2008-06-20
[I]I've moved this post [to a new thread]("http://ubuntuforums.org/showthread.php?p=5231113#post5231113")...

[/I]

---

### Post by Zorael on 2008-06-20
To make sure your xorg.conf is precisely the way the nvidia driver wants it, try this.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0806
$ sudo dpkg-reconfigure xserver-xorg
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Save your work, log out, restart X with Ctrl+Alt+Backspace.

---

### Post by Unix_Slayer on 2008-06-23
> **Zorael said:**
> 
Save your work, log out, restart X with Ctrl+Alt+Backspace.

Be careful with this one. I've gotten many a tongue lashing for using that command. Remember.... most people are using Gnome, unlike us who are using KDE.

The Gnome command is Control+Alt+F1 I believe.

---

### Post by Zorael on 2008-06-23
> **Unix_Slayer said:**
> Be careful with this one. I've gotten many a tongue lashing for using that command. Remember.... most people are using Gnome, unlike us who are using KDE.

The Gnome command is Control+Alt+F1 I believe.
I don't follow.

It's dangerous to use *unless* you log out. Your running applications won't have the opportunity to shut down cleanly. Hence, "save your work, log out, Ctrl+Alt+Backspace".

Ctrl+Alt+Backspace is an X-specific keybind ("zap"), and as such apply to all desktop environments, be they Gnome, KDE, Fluxbox, Xfce, or just an X session running xterm - unless you have explicitly disabled it in your xorg.conf or in your X startup script.

Ctrl+Alt+Fx switches between tty screens when in X. Outside X, you just need to do Alt+Fx. The seventh is usually where your graphical interface is running. F1 puts you at a normal, command-line one. F2 puts you at a similar, command-line one. As does F3, F4, F5, and F6.

---

### Post by Xiong Chiamiov on 2008-06-23
> **Unix_Slayer said:**
> Be careful with this one. I've gotten many a tongue lashing for using that command. Remember.... most people are using Gnome, unlike us who are using KDE.

The Gnome command is Control+Alt+F1 I believe.
As Zorael said, Ctrl+Alt+Backspace is an X key combo; as long as you're running X, it will work. (barring remapping or disabling for some reason, but if you're doing that, you don't need this guide)

Ctrl+Alt+F(x) switches between tty screens.  I'm not really sure what tty means (nor do I wish to look it up at the moment), but the normal GUI you boot into is usually assigned ctrl+alt+f7.  If you start another session, you can switch between those using those key combos.  The lower F keys will bring you to a prompt.

---

### Post by Unix_Slayer on 2008-06-23
> **Zorael said:**
> I don't follow.

It's dangerous to use *unless* you log out. Your running applications won't have the opportunity to shut down cleanly. Hence, "save your work, log out, Ctrl+Alt+Backspace".

Ctrl+Alt+Backspace is an X-specific keybind ("zap"), and as such apply to all desktop environments, be they Gnome, KDE, Fluxbox, Xfce, or just an X session running xterm - unless you have explicitly disabled it in your xorg.conf or in your X startup script.

Ctrl+Alt+Fx switches between tty screens when in X. Outside X, you just need to do Alt+Fx. The seventh is usually where your graphical interface is running. F1 puts you at a normal, command-line one. F2 puts you at a similar, command-line one. As does F3, F4, F5, and F6.

I know, I know, but everyone else seems to think that control+alt+backspace works in KDE only.

---

### Post by Xiong Chiamiov on 2008-06-23
> **Unix_Slayer said:**
> Be careful with this one. I've gotten many a tongue lashing for using that command. Remember.... most people are using Gnome, unlike us who are using KDE.

The Gnome command is Control+Alt+F1 I believe.

> **Unix_Slayer said:**
> I know, I know, but everyone else seems to think that control+alt+backspace works in KDE only.

:-k

---

### Post by tobiasly on 2008-06-25
Thanks for all the great info on this guys, I have a particular problem I'm trying to get around (if this should be a new thread let me know). I'm using Hardy on AMD x86_64 + GNOME. I had an NVidia card that was maybe a couple years old but still used the nvidia-glx-new; Compiz was working "pretty well".

Well I came by a newer card (8500GT based, made by Asus) so I decided to use it instead. I thought that I could just pull out the old card and put in the new since they're both Nvidia based. But when I started up, it gets through the Ubuntu splash screen then goes blank and my monitor says it lost the signal. I never hear a login sound, and no key combinations work (tried CTRL+ALT+BKSP, CTRL+ALT+DEL, CTRL+ALT+F1). My monitor has a VGA connector but I've tried using both VGA and DVI ports on my card (using an adapter for the DVI).

I've tried various combinations of Envy, installing drivers from NVidia site (both 173 and 169), and reinstall nvidia-glx-new. Every time I get the same problem (blanks/locks up after splash) then when I go to recovery mode & fix X it sets me back to "nv" driver.

So did I screw up by just trying to swap the cards out? Is there some hidden setting I need to get rid of to get it to detect correctly?

---

### Post by Zorael on 2008-06-25
tobiasly: Please post the contents of your **/etc/X11/xorg.conf** file, and the terminal output of the following commands.
```
$ uname -r
$ sudo updatedb; locate nvidia.ko    # this will take some time
```

---

### Post by castoroil97 on 2008-06-25
I will need to try this, cause my res is only 640X480, installed Hardy fresh.  It had worked fine under 7.04.  I even tried using the xorg.conf to see if would work and it did not.

I will update!

---

### Post by tobiasly on 2008-06-25
> **Zorael said:**
> tobiasly: Please post the contents of your **/etc/X11/xorg.conf** file, and the terminal output of the following commands.

Thanks Zorael but now the thing won't even boot. I'm guessing it's a bad card @ this point, gonna try a few more things before sending it back (my mobo has a debug LED, but the error code it's giving isn't in the manual, not a good sign!)

BTW, <3 the S&O avatar :)

---

### Post by tobiasly on 2008-06-27
> **Zorael said:**
> tobiasly: Please post the contents of your **/etc/X11/xorg.conf** file, and the terminal output of the following commands.
```
$ uname -r
$ sudo updatedb; locate nvidia.ko    # this will take some time
```

OK, turns out my boot issue was unrelated and now it's resolved... here's the info you asked for:
**$ uname -r**
2.6.24-19-generic
**$ sudo updatedb; locate nvidia.ko**
/lib/modules/2.6.24-17-generic/kernel/drivers/video/nvidia/nvidia.ko
/lib/modules/2.6.24-19-generic/updates/dkms/nvidia.ko
/var/lib/dkms/nvidia/173.14.05/2.6.24-19-generic/x86_64/module/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.24-19-generic/x86_64/nvidia.ko

And here's the xorg.conf it was trying to use when it wouldn't come up (I added the "UseDisplayDevice" line from [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") since I'm using DVI, but it doesn't work either way):
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"UseDisplayDevice"	"DFP"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by Zorael on 2008-06-27
tobiasly: Owkay. Your xorg.conf looks well enough.
```
$ sudo aptitude purge ~nnvidia-glx

            *# the next lines may output errors, no worries*
$ mkdir /tmp/nvidia.backups /tmp/nvidia.backups/dkms /tmp/nvidia.backups/modules
$ sudo mv /var/lib/dkms/nvidia* /tmp/nvidia.backups/dkms/
$ sudo mv /lib/modules/`uname -r`/updates/dkms/nvidia* /tmp/nvidia.backups/modules/

$ sudo aptitude install nvidia-glx-new nvidia-settings
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Then reboot and see if it helped. Only the first and last two lines should technically be needed; the other three are just to make sure that everything gets removed properly.

***IF* it doesn't work** and you get to the displayconfig window, reboot into recovery mode *without* letting it change into safe mode. Once in recovery, pick 'root' or whatever the entry is named. "Drop to shell", anyway. You want to get to the command-line interface. Once there, enter the following (which you may want to write down).
```
# cp /var/log/Xorg.0.log /var/log/Xorg.0.backup
# exit
```
Now pick 'fix X' to log in into safe mode and post **/var/log/Xorg.0.backup** here.

---

### Post by tobiasly on 2008-06-27
Still no go... my logfile is attached, but maybe I did something wrong; why does it say it's using "xorg.conf.failsafe"? There was also an Xorg.0.log.old but it looked the same...

Also, when running the "purge" command, I got the following warnings; should I clear these out manually too?

```

Removing nvidia-glx-new-envy ...
Purging configuration files for nvidia-glx-new-envy ...
dpkg - warning: while removing nvidia-glx-new-envy, directory `/usr/lib32/tls' not empty so not removed.
dpkg - warning: while removing nvidia-glx-new-envy, directory `/usr/lib/tls' not empty so not removed.

```

---

### Post by Zorael on 2008-06-28
That's a failsafe log file in which it didn't try the nvidia driver. :< As for the purging, just accept any prompts, you shouldn't need to do anything extra.

When you say 'no go', do you mean 'no 3d acceleration' or 'X doesn't start'?

---

### Post by tobiasly on 2008-06-28
Sorry, shoulda been more specific.. after the Ubuntu splash, it switched briefly to the text/boot screen and flickered a few times between that and a blank screen, then it started in low-resolution mode. So I selected Shut Down at that point, then started into recovery mode and proceeded as you said (dropped to root shell & copied the log file).

So does the log file mean that it didn't even try to use the nvidia driver? I know that at least in recovery mode, I saw a message going by about the nvidia driver (something like loaded driver version nnn, with a license that taints the kernel or whatever).

---

### Post by okdok on 2008-06-29
Confirmed these instructions worked perfect for me.

Fresh updated Hardy 8.04
Nvidia Quadro FX 1600

Thanks! :guitar:

---

### Post by berserkpi on 2008-07-01
It worked like charm :). Thank you.

I posted my problem at:  [http://ubuntuforums.org/showthread.php?t=846496]("http://ubuntuforums.org/showthread.php?t=846496")

My problem was solved with these easy-to-follow-steps. :guitar:

---

### Post by normac_36 on 2008-07-05
After a fresh install of Hardy Ubuntu 64-bit the following worked like a charm for me.

Open your terminal and type the following:

sudo apt-get install build-essential

// Now we need to to disable the X server before installing.

Press Ctrl + Alt + F1 to enter command mode

Now type:

sudo /etc/init.d/gdm stop //to disable the X server

Now we need to install the driver.

For me I downloaded the latest drivers which were the 173 64-bit drivers.

In the terminal type:

sudo sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run //The version number may change depending on the driver you are installing.

Start the X server again:

sudo /etc/init.d/gdm start

Ctrl + Alt + Backspace to start the X server again.

The driver installation should have configured the new xorg.conf file.

Go to Application->System Tool->NVIDIA X Server Settings 

Click the X Server Display Configuration tab

Now open terminal and edit the xorg.conf file and save to the new xorg.conf file from the Nvidia driver installation.

In terminal type:

sudo gedit /etc/X11/xorg.conf

Back in the Display Configuration Tab click Save to X Configuration File and preview the .conf file.
- Copy and paste the text from the nvidia xorg.conf file into the xorg.conf file in Gedit.

Save and reboot, you should be good to go!

---

### Post by angvz on 2008-07-16
Trying ti make a MythTV system, I tried this on hardy with an FX5200.

The shell script built and installed the 175.19 drivers, the nvidia-xconfig ran without error, but I dont get a working X.

I've seen other posts with my same problem - the screen flashes a few time between blank and the terminal, then gives up.

I've tried a bunch of different changes to xorg.conf...

BusID, Modes, Metamodes, Modelines, NvARG 0,1,2 everyhting I see in posted xorg.confs that work but no luck.

Before I switched to the nvidia driver I did get a partially working twinview using the original hardy drivers but the only resolution available was 'nvidia-auto-config' which gave me low res on the 2nd display.

I've not heard of 'envy' before, no I guess I'll look into that next. My goal is a 1280X1024 on display 0 with 1280X720 on display 1 - a htdv

---

### Post by angvz on 2008-07-17
OK I downloaded envy - it loaded the 173 driver and I am much happier - i couldn't get 1280X720 on my 2nd display but 1024X768 is gonna be fine for watching TV, playing DVD's..

Now to build mythv....

..what i've learned from this...

use Envy not nvidia-xconfig

---

### Post by legatoistheman on 2008-07-17
Ever since I installed the new kernel update and the new driver through envyng i can't get the graphics drivers to work at all.  I have tried everything from uninstalling driver with envy and installing again to uninstalling with envy and installing an older version of the driver.  I have tried to install the driver by using command line(could not get x to shut down, no matter how i tried).

I was able to play world of warcraft using wine even though the drivers were showing up in the list as restricted but the box was not checked like they were in use(although the light was green saying they were in use) up until yesterday when i decided to install that nvidia glx from synaptics.  I went so far as to uninstall that when warcraft would start up but play really crappily (unplayable).

I really do not know what im doing, and I did manage to get the cards working in sli before this new driver and kernel update.  I am so confused.  This is what I have for you, if you know of other commands for me to give more system specs let me know I need all the help I can get because I dont want to have to do a clean install and reinstall everything.

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)
08:0a.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge (rev 12)
08:0a.1 PIC: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
08:0b.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge (rev 12)
08:0b.1 PIC: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
0a:09.0 Multimedia audio controller: Creative Labs SB X-Fi
80:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
80:01.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
80:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
80:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
81:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)

thanks in advance for the help because I cant seem to do anything to even get the restricted nvidia drivers to show up anymore in the restricted driver list even if i do use envy to install them(big long sighhhhh)

---

### Post by Xiong Chiamiov on 2008-07-18
I'm afraid I'm not very good at fixing video card issues; I merely stumbled upon the way to install a driver manually (and found out that it fixed my problem!) and wrote up what I did.

I may be able to help with the issue of not being able to install via this method because X won't shutdown, though.

If you boot into recovery mode instead of normal (when your computer first starts, and you get the GRUB menu), then X won't start.  However, I don't believe you'll have a connection to the 'net either, so make sure you've downloaded the package first and know how to get to it (or just put it in your home folder).

You should then be able to run the installer as per the directions.

Let me know how it turns out.

---

### Post by legatoistheman on 2008-07-18
thanks for the reply, I did get the driver installed again it appears, killed x and it let me install it but even after that it still wont show up in my restricted drivers.  Neither I or a friend that has been trying to help me has had any luck with getting the drivers recognized.

If anyone has any answers as to what it might be feel free to please chime in.  

The person that was trying to help me had me do these steps to try to get the nvidia drive working again.  

[http://wiki.innovativegeeks.com/index.php5?title=Nvidia_linux_sli](http://wiki.innovativegeeks.com/index.php5?title=Nvidia_linux_sli)

What happened after I edited x to the config he told me was that it restarted and kubuntu splash loaded but after that there was a blank screen that didnt let me do anything.

---

### Post by Xiong Chiamiov on 2008-07-18
I don't think that the driver will show up in the restricted drivers list if you install it manually, only if it's installed through the package manager.  If you can specify it as the driver in your xorg.conf and it loads, though, then it's working.

Can you post your /etc/X11/xorg.conf please?  (and wrap it in [ code ] tags too, if you could)

And also, you can see if 3d rendering and stuff is up (which only happens with the restricted driver) by looking at the third line of this:
```

glxinfo | less

```
You're hoping to see "direct rendering: Yes".

---

### Post by ktechman on 2008-08-11
Just wondering if anyone knew if I could, or should manually install the ATI driver on a new laptop with an ATI card? And could I do it with these instructions?

---

### Post by Xiong Chiamiov on 2008-08-11
I wouldn't recommend installing *any* driver manually unless it's not working otherwise; you're not going to gain a noticable speed benefit or anything, except in very rare cases.

These instructions are for NVIDIA cards specifically, although I'm sure you could modify them to your needs, since the stopping of X and such is the same.  I'd try following the instructions on [this wiki page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), since they are ATI-specific.

---

### Post by zieglerj on 2008-08-15
I tried your steps and all went well up until:
sudo sh NVID[tab]
When I type this command all I get is:
sh can not open NVID[tab]

is there any way to fix it?

---

### Post by zieglerj on 2008-08-16
O.k. my problem turned out to be that I had install the driver once before and it hadn't worked. 
I corrected it by typing:

sudo init 3
sudo sh NVIDIA*

---

### Post by mister_pink on 2008-08-16
> **zieglerj said:**
> O.k. my problem turned out to be that I had install the driver once before and it hadn't worked. 
I corrected it by typing:

sudo init 3
sudo sh NVIDIA*

Its also worth noting that [tab] meant press the tab key so it fills in the rest of the line for you, just in case that wasn't what you were doing.

---

### Post by kerryhall on 2008-08-16
This worked, but first I had to do
but first i had to do

sudo apt-get remove libgl1-mesa-glx
then
sudo apt-get install libgl1-mesa-glx

which for some reason uninstalled everything that depended upon it! Is there anyway i can uninstall and then reinstall a package without everything that depends upon it getting messed up?

The nvidia installer was also complaining about some gl libraries being in /usr/local
and officially the installer failed, but everything seems to be working now except...


glxinfo:
direct rendering: No 


how do i enable direct rendering?

---

### Post by Xiong Chiamiov on 2008-08-23
> **kerryhall said:**
> This worked, but first I had to do
but first i had to do

sudo apt-get remove libgl1-mesa-glx
then
sudo apt-get install libgl1-mesa-glx

That *is* odd.  Hmm.

> **kerryhall said:**
> 
which for some reason uninstalled everything that depended upon it!

That's the way apt works; rather than leave all of those packages broken, it will remove them as well.  Installing it again, however, won't automatically reinstall those packages; from apt's perspective, you're installing it for the first time, so it assumes you just want what you said you wanted.

> **kerryhall said:**
> 
Is there anyway i can uninstall and then reinstall a package without everything that depends upon it getting messed up?

Why yes there is (I'm glad you asked).  The first is to use the reinstall command, rather than uninstalling and installing:
```

apt-get --reinstall [package]

```
I was thinking there was a way to remove something and leave alone things that depended on it, but I can't seem to see how to do that, so I'm guessing it was with a different package manager.  I know that I was looking for that because I sometimes needed to reinstall something with a --purge flag, and you can't do both (I think, it's been a while since I've used apt).

> **kerryhall said:**
> 
The nvidia installer was also complaining about some gl libraries being in /usr/local
and officially the installer failed, but everything seems to be working now except...


glxinfo:
direct rendering: No 


how do i enable direct rendering?
Hmm, that library thing is also interesting.  I'll have to look that up sometime (which means, don't count on me).

Make sure that at the end of your xorg.conf you have this:
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by mastergunner on 2008-09-05
Guys I am a noob at linux and have Hardy with a Geforce 8500. Can someone take me step-by-step on how to get this card working correctly. I am so frustrated it makes me like Windows more and more. Please can someone help me out I would greatly appreciate it.

This is a fresh install with any updates from Adept already done. 

If I have to install anything please put that in the instructions.

THANK YOU

---

### Post by Xiong Chiamiov on 2008-09-05
> **mastergunner said:**
> Guys I am a noob at linux and have Hardy with a Geforce 8500. Can someone take me step-by-step on how to get this card working correctly. I am so frustrated it makes me like Windows more and more. Please can someone help me out I would greatly appreciate it.

This is a fresh install with any updates from Adept already done. 

If I have to install anything please put that in the instructions.

THANK YOU
Well, that's what this guide is supposed to be. ;)

If you have any problems following the guide, then telling me will do two things:
a) allow me to help you
b) tell me how to improve the guide

---

### Post by mastergunner on 2008-09-05
> **Xiong Chiamiov said:**
> Well, that's what this guide is supposed to be. ;)

If you have any problems following the guide, then telling me will do two things:
a) allow me to help you
b) tell me how to improve the guide

I understand but it looks like you arent installing any drivers or whatever. Also you reference another guys guide. I do not understand what he wants to be done. When I mean step-by-step that is all inclusive. Every step should be in the guide. I have seen some guides on here that are like that. I can just copy and paste commands into terminal and be good.

---

### Post by Xiong Chiamiov on 2008-09-05
> **mastergunner said:**
> I understand but it looks like you arent installing any drivers or whatever.
That's entirely what this guide is about!?

We aren't installing them through apt, because the ones in the repo are out of date.  We're just running an install script from NVIDIA.

---

### Post by mastergunner on 2008-09-05
What is the install script from Nvidia?

What version of KDE do I have if I am running Hardy?

---

### Post by Xiong Chiamiov on 2008-09-05
> **Xiong Chiamiov said:**
> 
From [here]("http://www.nvidia.com/object/unix.html"), download the 173.14 driver (first one listed).  If you're using 64-bit *buntu, download the 173.14 from the 3rd section, the one entitled "Linux AMD64/EM64T".

The NVIDIA drivers aren't open-source (they only provide binaries), so instead of having it packaged into a nice .deb, you just use the script that NVIDIA provides that puts things in the right places.

---

### Post by mastergunner on 2008-09-05
Once I download the file and run the script to install the drivers what needs to be done next?

---

### Post by knix on 2008-09-05
> **mastergunner said:**
> Once I download the file and run the script to install the drivers what needs to be done next?

If you let it configure your xorg.conf, just reboot.
When going through the script- let it compile the kernel interface. you will need linux-headers for your kernel.

---

### Post by mastergunner on 2008-09-05
> **knix said:**
> If you let it configure your xorg.conf, just reboot.
When going through the script- let it compile the kernel interface. you will need linux-headers for your kernel.

So how do I get the linux-headers? Thought they were already there.

---

### Post by Xiong Chiamiov on 2008-09-05
> **mastergunner said:**
> So how do I get the linux-headers? Thought they were already there.
They should be, assuming you did
```

sudo apt-get install linux-headers-$(uname -r)

```

After installing them, all you should have to do is reboot.  If you have any problems, we probably just need to make a few adjustments to your xorg.conf.

---

### Post by mastergunner on 2008-09-05
> **Xiong Chiamiov said:**
> They should be, assuming you did
```

sudo apt-get install linux-headers-$(uname -r)

```

After installing them, all you should have to do is reboot.  If you have any problems, we probably just need to make a few adjustments to your xorg.conf.

So just to make sure I should do the above command?

---

### Post by Xiong Chiamiov on 2008-09-05
> **mastergunner said:**
> So just to make sure I should do the above command?
Just make sure you follow the directions ;)

If you don't do that first, then you'll get an error when installing, in which case you can run
```

startx

```
to get back into the GUI and take another look here, assuming you have a working GUI in the first place.

---

### Post by mastergunner on 2008-09-06
I have downloaded the nvidia drivers from the nvidia site. I have tried to run it but I keep getting this error:

brad@brad-desktop:~$ sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-173.14.12-pkg2.run

What did I do wrong?

---

### Post by Xiong Chiamiov on 2008-09-07
> **mastergunner said:**
> I have downloaded the nvidia drivers from the nvidia site. I have tried to run it but I keep getting this error:

brad@brad-desktop:~$ sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-173.14.12-pkg2.run

What did I do wrong?
Assuming that you tab-completed (meaning that the file exists there and the name is correct, which it looks to be), it sounds like a corrupted file.  You can also try this method:
```

chmod +x NV[tab]
./NV[tab]

```
which is essentially the same thing.  First I'd try redownloading it, though.

---

### Post by mastergunner on 2008-09-07
ok I do not think I was completely out of X. I tried getting out of x and running as root but it keeps sayin I am running X.  Xiong could you just right out how it is supposed to work and the steps I need to get this thing working. Thanks.

---

### Post by mastergunner on 2008-09-07
OK finally got the NVIDIA driver to load. After rebooting my monitor says out of range. I ant get to anything or see X. What now?

---

### Post by Xiong Chiamiov on 2008-09-07
> **mastergunner said:**
> OK finally got the NVIDIA driver to load. After rebooting my monitor says out of range. I ant get to anything or see X. What now?
It sounds like X is trying to use a screen resolution that your monitor doesn't support.

If you press ctrl+alt+f2, you'll get to a text prompt, where you can log in.  What we need to get is your current Xorg.conf, and the previous one as well, if you had something working previously to this.

I'm not sure what your setup is, but if it *was* working before (at least, to where you could login), then get to the directory where the X configuration files are:
```

cd /etc/X11
ls

```
Xorg.conf is the file being used right now.  You can view it with
```

less Xorg.conf

```
or edit it with
```

sudo nano Xorg.conf

```
There should also be a backup file, probably named Xorg.conf.[something].  If you had it working before, then we'll go ahead and log in with that configuration file:
```

X -config Xorg.conf.[something]

```
Once there, please copy and paste the contents of both that file, and Xorg.conf on here.

---

### Post by samuraiCat on 2008-09-07
You rock! After banging my head on the desk for four hours, this worked like a charm. 

EDIT: GAH! I was wrong. On reload, it sent me back to 800X600 and the new xorg reconfigure gui. I tried to reinstall, but I had to just go back to my backup of xorg.conf. What went wrong?

---

### Post by Xiong Chiamiov on 2008-09-07
> **samuraiCat said:**
> You rock! After banging my head on the desk for four hours, this worked like a charm.
I'm glad I could help.  It took me a while to get this working, and so, once I did, I figured I'd try and share the knowledge, since it was so frustrating to me.

---

### Post by samuraiCat on 2008-09-07
> **Xiong Chiamiov said:**
> I'm glad I could help.  It took me a while to get this working, and so, once I did, I figured I'd try and share the knowledge, since it was so frustrating to me.

Sorry, Xiong, but something went wrong. After I reloaded, it kicked me back to the graphical reconfigure. I had to revert to my saved xorg.conf.

Not that I'm not still grateful, mind you -- I think this was my fault. I noticed in the new xorg.conf that the VertRefresh was 110, which is insane. But I rebooted anyway, and had to reconfigure and revert. 

I'm trying it again right now.

---

### Post by mastergunner on 2008-09-07
Xiong it was working with a fresh install. Once I utilized the NVIDIA drivers it started this. Why go back when we should be modifying this Xorg with the new drivers. How should I do this? I can use ctl+alt+f1 and get in that way without X.

---

### Post by Xiong Chiamiov on 2008-09-07
> **samuraiCat said:**
> Sorry, Xiong, but something went wrong. After I reloaded, it kicked me back to the graphical reconfigure. I had to revert to my saved xorg.conf.

Not that I'm not still grateful, mind you -- I think this was my fault. I noticed in the new xorg.conf that the VertRefresh was 110, which is insane. But I rebooted anyway, and had to reconfigure and revert. 

I'm trying it again right now.
It's odd that you got in once, but not after that.  You might try using your old Xorg.conf, but just with the driver changed to 'nvidia', instead of vesa or whatever it was.

---

### Post by Xiong Chiamiov on 2008-09-07
> **mastergunner said:**
> Xiong it was working with a fresh install. Once I utilized the NVIDIA drivers it started this. Why go back when we should be modifying this Xorg with the new drivers. How should I do this? I can use ctl+alt+f1 and get in that way without X.
If it was working with the old Xorg.conf, then we can modify that one to use the nvidia driver, thereby eliminating the possibility of problems with vertical refresh rates and that kind of nonsense.  First off I'd try just changing the driver setting (under Device) to nvidia.

---

### Post by mastergunner on 2008-09-08
SO how do I go about doing this then?

---

### Post by mastergunner on 2008-09-08
I can not get this to work. I just went into xfix and I am up now just says it is using the nv driver. I do not understand this at all. Nvidia-settings and nvidia-xconfig do not work even though they are installed. Theis is freaking ridiculous.

---

### Post by Xiong Chiamiov on 2008-09-08
> **mastergunner said:**
> SO how do I go about doing this then?
The command I gave you before starts X with a different configuration file other than /etc/X11/xorg.conf.  You need to point that at your backup.  Then edit said file and
> 
[change] the driver setting (under Device) to nvidia.


---

### Post by mastergunner on 2008-09-08
I have done that and nothing. I even put in the actual display sizes and frequencies and nothing.

---

### Post by samuraiCat on 2008-09-09
UPDATE!

It worked! I just had to add this to the Devices section of xorg.conf:
Driver    "nvidia"

*******************


> **Xiong Chiamiov said:**
> It's odd that you got in once, but not after that.  You might try using your old Xorg.conf, but just with the driver changed to 'nvidia', instead of vesa or whatever it was.

Okay, I did some more research and I found out that my exact laptop (Presario F500 series) does not work with either the 167.x or 172.x NVIDIA drivers: [https://bugs.launchpad.net/ubuntu/+bug/207749](https://bugs.launchpad.net/ubuntu/+bug/207749)

That bug report describes the exact problem that I'm having. Apparently, neither the nvidia drivers from the repos or the new ones from Nvidia will work on my machine. I need to use the old Feisty drivers (which worked great, btw).

I followed the instructions that one user posted near the end of the thread, but now I'm hung up on one part. I'm hoping someone can help me with the next step.

Here's what I followed:
> 

Ok

I solved IT, installing the latest drivers won't work either....

i have to roll back to the 100.14.19 drivers, these seems to be working fine, no garbled consoles (i don't have a system hangs yet either)

firstly uninistall the ubuntu nvidia driver in the restricted hardware app...

the follow this guide to clean the system( [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490) )[quote]

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Now donwload this drivers set ([http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html))

go to the console (crtl-alt-f1)

stop gdm
sudo /etc/init.d/gdm stop

go to the driver download folder, and do

sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run


don't donwload the kernel modules, compile it ... reboot and Voila

another nvidia nightmare solved for me....
[/quote]

I followed these instructions exactly, but the new driver does not appear to be running yet. I thought I screwed it up, but when I followed the instructions a second time, I received a message saying "Driver 100.blah.blah is currently installed. Do you want to reinstall?" I reinstalled anyway, but still nothing.

Here's my question: How do I get this old driver to work? Since this wasn't from the repos, do I need to add "nvida" into my xorg.conf file manually?

Edited to add: There was a previous issue documented here by Artificial Intelligence, but I don't know if his fix was applicable: [http://ubuntuforums.org/showthread.php?t=544856&page=4](http://ubuntuforums.org/showthread.php?t=544856&page=4)

---

### Post by mastergunner on 2008-09-09
Xiong I finally got it to work and the only thing I did was hook up a DVI cable from card to monitor. Apparently the cable is needed so it can see the monitor and adjust from there. This is the only thing I did. I hooked it up turned on the computer went into Kubuntu and during boot up I saw the NVIDIA splash screen. After logging on I went to NVIDIA Settings and it was seeing everything. WOW I wished this was written somewhere that this cable is a must (at least for me).

---

### Post by Xiong Chiamiov on 2008-09-09
> **mastergunner said:**
> Xiong I finally got it to work and the only thing I did was hook up a DVI cable from card to monitor. Apparently the cable is needed so it can see the monitor and adjust from there. This is the only thing I did. I hooked it up turned on the computer went into Kubuntu and during boot up I saw the NVIDIA splash screen. After logging on I went to NVIDIA Settings and it was seeing everything. WOW I wished this was written somewhere that this cable is a must (at least for me).
So were you installing without the monitor attached?  I've noticed that X seems to require a monitor attached oftentimes when it starts, or things go wacky.  I have a fileserver that I occasionally use to play things on my tv, and to do so, I have to make sure I boot up with it connected and the tv on.

I'm glad that you got it working.  After getting clarification from you on which part exactly the monitor needed to be attached, I'll add it to the guide.

---

### Post by mastergunner on 2008-09-09
No it was attached with a VGA cable. It seems a DVI cable is need for the driver to digitally see the monitor.

---

### Post by Xiong Chiamiov on 2008-09-09
> **mastergunner said:**
> No it was attached with a VGA cable. It seems a DVI cable is need for the driver to digitally see the monitor.
Hmm, that's odd.  My card supports VGA, DVI and S-Video out, but I've only ever had to hook it up to VGA (since that's what my monitor is).  Well, whatever works :).

---

### Post by mastergunner on 2008-09-09
Yes mine does to but I guess it might have been the monitor. The card need to get info from it since it is not a brand that is used often (Westinghouse).

---

### Post by irisblaze on 2008-10-16
> **Xiong Chiamiov said:**
> [SIZE="3"]**Attention!**:[/SIZE] it seems that the new version of [envy]("http://albertomilone.com/nvidia_scripts1.html") has finally gotten the new drivers, so you should be able to install it (with its nifty GUI configuration!).  Haven't tested myself, but definitely try that first.
**2008-06-15**: Took envy for a spin today, and it lists 169.12 as the NVIDIA driver (for the series that needs 173, that is).  I think it's just hardy-proposed that it's gotten to, so who knows how long that'll be 'til it gets to us.

~~~~~~~~~~~~

I've been typing this out quite a bit recently, so I though I'd just make a well-formatted post to link to.

Before we start, let me tell you that most of this code you can directly copy and paste.  The part about killing X that's in bold is the only part that will vary, and you just use the number that's in bold for the first part in the second.

The kernel in Hardy is causing problems with the NVIDIA drivers included in the repositories, so we need to download and install the newest drivers.

From [here]("http://www.nvidia.com/object/unix.html"), download the 173.14 driver (first one listed).  If you're using 64-bit *buntu, download the 173.14 from the 3rd section, the one entitled "Linux AMD64/EM64T".  Save/move to your home directory.

Write down these instructions, because we're going to be dropping to a command-prompt.
Press ctrl+alt+f1, then enter these commands:
```

sudo apt-get remove --purge nvidia*
sudo apt-get install linux-headers-$(uname -r) libc-dev build-essential
cd ~
sudo /etc/init.d/gdm stop
sudo sh NVID[tab]
sudo /etc/init.d/gdm start

```

If you're using KDE3, replace gdm in the fourth and sixth lines with kdm; KDE4 users replace with kdm-kde4.  Xubuntu users will also use gdm.
If stopping the window manager doesn't bring you back to a prompt, press alt+f1 again to do so.

Make sure that when the installer complains about the versions of GCC not matching, you select "no".  This will continue the installation.
I would recommend that you select "yes" when the installer asks if you want it to generate an X configuration file.  It will create a backup of your current one in /etc/X11 if you need it.

After doing this, I recommend you follow vor's [excellently-constructed guide]("http://ubuntuforums.org/showthread.php?t=835573") for keeping your NVIDIA drivers working after a kernel update.

~~~~~~~~~~

If you're getting an error with the installer saying that X is running:
First run
```

ps -ef |grep X (make sure that's a capital X!)

```
You should see something like this:
```

root     **14341**  5346  2 20:05 tty7     00:00:16 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-G56yJI
pearson  17629 14881  0 20:16 pts/0    00:00:00 grep X

```
Take a look at the number that I put in bold.  Then kill X like so
```

sudo kill -9 **14341**

```
changing the last number to what it was for you when you ran the previous command.

[Alternate trick #1.]("http://ubuntuforums.org/showthread.php?p=4970051#post4970051")
[Alternate trick #2.]("http://ubuntuforums.org/showthread.php?t=792276#5")

[Nullack had to]("http://ubuntuforums.org/showthread.php?p=5148785#post5148785") make a few adjustments to his Xorg.conf to get his to work on a fresh 64-bit install.

If this doesn't work, you find an alternate solution, or you had to do something in addition, please let me know so I can update accordingly.  We want to reduce pain for others, right?

Also, the well-formatted post I originally started off with has grown rather... well, it's not as good as it could be.  However, I am rather bad at things this long, so if anyone would like to reorganize/reformat anything to make it a bit more friendly, then just let me know!

hello, i did a manual installation of the drivers before i get into this guide, and my drivers worked until i reboot, after following your guide, the same  thing happened, it worked but until i reboot, but in your guide, i get 2 versions of the kernel when selecting the new version, the same problem happens, but when i select the old version everything works, so i removed the new version from grub... now everything works fine ...

I am gonna have to use this solution temporary until i get a better solution that will allow me to use the new version of kernel thanx

---

### Post by Xiong Chiamiov on 2008-10-18
> **irisblaze said:**
> hello, i did a manual installation of the drivers before i get into this guide, and my drivers worked until i reboot, after following your guide, the same  thing happened, it worked but until i reboot, but in your guide, i get 2 versions of the kernel when selecting the new version, the same problem happens, but when i select the old version everything works, so i removed the new version from grub... now everything works fine ...

I am gonna have to use this solution temporary until i get a better solution that will allow me to use the new version of kernel thanx
If I remember right, this can be caused either by X not being fully shutdown initially, or the appropriate module not being loaded.

For the 1st, I think the nvidia installer will warn you if it's not, but just to make sure, you did "sudo /etc/init.d/gdm stop"?

For the 2nd, do you get anything when you run the command
```

lsmod | grep nvidia

```
If you do, then you're fine on that end.

Of course, using a slightly old kernel's not particularly a bad thing, but still, it'd be nice to get it fixed.

---

