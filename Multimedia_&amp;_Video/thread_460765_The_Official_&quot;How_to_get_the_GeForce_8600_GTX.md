---
title: "The Official &quot;How to get the GeForce 8600 GTX BETA drivers to work in Fiesty&quot; Thread"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by anim on 2007-06-01
[B][COLOR="Red"]{Update}[/COLOR]
Haven't been monitoring this thread (Physical Chemistry been demanding...well all of my time) but at of 11/11/2007 I've updated a few links and added some great advice by Durand about reinstalling the driver every time you update the Kernal, something that I had to learn the hard way. Hope this guide is still helping people, and thanks to those who have been helping people out in my stead. As stated in a later post, these drivers are no longer in beta, but most of the advice below should still work if you're having issues. /patrick[/B]

**Disclaimer
I've reconstructed these instructions from a few websites (Cited Below) and the help of some community members, but they are mainly a result of my memory, so sorry I couldn't provide a greater level of detail. Use your common sense and the reply button on this thread to help you out with the rest.

Ok after a day that was WAY to long, I've gotten the Beta nvidia drivers to work for this card.

Heres a step by step way to do it yourself.

download the proper driver package from nvidia [here]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run").
If the file isn't on your desktop, copy it there. (All my instructions will assume this)

Open the terminal (Applications->Accessories->Terminal).
Type ```
sudo apt-get install module-assistant gcc nvidia-kernel-common
```
you may have to enter your password after any of the sudo commands.
Ubuntu will now download some required files for you. After this has completed... type```
sudo m-a update

```And then```
sudo m-a prepare

```and then```
m-a auto-install nvidia
``` You will get some log messages and hopefully a Done! at the end of it.
Now Exit the terminal.
At this point, you will want to print out the remaining instructions, or open this thread on a nearby laptop to read the remainder of the instructions. The next command will boot you to the full screen console and you will not be able to see the firefox window. Please close all open applications at this time.
Hit keys```
Ctrl + Alt + F1
``` to go to console.
Login if propted, otherwise type```
sudo /etc/init.d/gdm stop
``` again it may ask for a password. Then type:```
cd /home/<INSERTYOURUSERNAMEHERE>/Desktop/
** BELOW IS AN EXAMPLE!!!**
cd /home/joeubuntu/Desktop/
``` Finally type ```
dir
``` to view the filename of your driver package. They are long, and this will help you with the next step, which is to type:```
sudo sh <YourSpecificDriver>.run
** BELOW IS AN EXAMPLE!!!**
sudo sh NVIDIA-Linux-x86-100.14.06-pkg1.run
```
If you entered the correct filename, you should enter the nvidia driver install program, it looks like old school DOS or a BIOS screen.

Make sure you tell the installer to change your config to use the new driver by default (one of the last screens)

Follow the instructions on screen and there should be NO PROBLEMS with X (YAY!!!) and if it doesn't find a precompiled kernel, you already compiled one earlier (Yay!!!). 
[B]
IF FOR SOME REASON IT DOESN'T LET YOU INSTALL[/B]
it should kick you to console. Type:```
sudo /etc/init.d/gdm start
``` to return to the ubuntu you know and love, and ask a question about what went wrong below, I'll try to help.

After a successful install, it should boot you to the console. Type:```
sudo reboot
```
AND ENJOY THE NVIDIA EXPERIENCE.

Helpful resources:
NVidia ReadMe : [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.06/README/part-01.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.06/README/part-01.html)
Kernel Compile Help : [http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)

Hope this helps save someone the 4 hours it took me to work this all out.
/Patrick K

****SOME ADDITIONAL GOOD ADVICE IF YOU CARD APPEARS TO STOP WORKING AFTER UBUNTU UPDATES ******
> **durand said:**
> 
EDIT: This is the first time I've actually read the whole thread from the start and it seems that people don't understand one thing. Whenever you update the kernel or initrd or some other stuff, you will need to reinstall the driver so it can make the ko file against the latest kernel. Its pretty simple.
cd to where you downloaded the installer
then type:
```
sudo ./NV* -s
```
This way it just updates the driver module for your current kernel version without opening the graphical interface. As of now, until ubuntu updates its drivers in restricted-manager to the latest, you will have to keep doing this for every new kernel you install. :(

---

### Post by anim on 2007-06-01
bump - seeing questions about this.

---

### Post by father of 2 sons on 2007-06-02
When I initially utilized your instructions, X crashed upon reboot concerning a kernel module version conflict with the new beta driver.  Here is what I did to resolve it.

1) reconfigured X to use the "nv" driver.  "sudo dpkg-reconfigure xserver-xorg"
2) I used the synaptic package manager to [U]completely[U] uninstall anything that had to do with Nvidia, Build-essential, Gcc, module-assistant, nvidia-kernel-common.
3) Followed your walk through again.

  Xserver now started correctly for me.  I just had to "sudo nvidia-settings" to enable twin view and save my resolution(s) as 1280x1024.   Beryl is smooth with the latest beta driver (Nvidia-Linux-100.14.06) on my XFX 8600gt XXX Edition.

  I am sure my uninstall process was overkill, but being a Linux novice, I was not sure what particular module was causing the conflict.

---

### Post by edu77pose on 2007-06-06
I previously had a computer with a 6400 series card, it was a piece of cake to set up because it was recognised by the 'Restricted Drivers Manager'. I would like to add that Ubuntu are heading in the right direction with this functionality, keep up the magnificent work.

The graphics video card I'm using is a XFX 8600GT. I used the setup as listed but when I restarted my computer I received the 'xserver' error and now i can't enter. I wish I was a geek to get me out of trouble but looks like i'll have to reinstall the OS.  

Does anyone know how to get the xserver running from an error, such as installing the nvidia drivers?

Go Ubuntu

Eduardo

---

### Post by holdinout on 2007-06-10
Works great! Left out the "sudo" in step 4. Only worked for me when I typed "sudo m-a auto-install nvidia". Thanks so much though, had a hard time doing this on my own.

---

### Post by Rosse on 2007-06-10
Anim you hero!

Tried 3 days to get this card to work in Feisty and almost switched too Fedora (luckily the cd wouldnt boot :p)

Now i am playing quake 4.

thx a lot

---

### Post by Vixyfox on 2007-06-10
Well, I tried to follow your guide there when I first installed Ubuntu. Though I think something to note here is that I tried to the first time after the updater wanted me to go to Kernel .16

I think this may cause people some issues when they try. I was reading and saw that .16 has quite a few errors in it and people shouldn't really upgrade to it. I'm not sure exactly why but so I decided to stay in .15 to try these steps again.

After reinstalling .15 again I successfully was able to install the beta driver just fine. No errors or anything.

If people are having difficulties I would suggest trying with kernel .15 instead of the new .16.

If anyone knows anything more about this I would love to hear. I just installed Ubuntu so I'm really new ^^

Thanks again for the great guide!! It really helped me!! :D

---

### Post by papatrpt89 on 2007-06-13
THANK YOU SO MUCH!

For the first time today, I laid hands on a really good pc.  For the longest time, I had watched beryl videos and drooled.

Specs:
Core 2 Duo, 2.4 ghz.
2 gig 667 mhz ram
256 mb nvidia 8600gt card

I bought nvidia knowing they support linux.  Booted into fiesty, and restricted-manager didn't recognize the card.  After searching around, I found this guide.  I tried it, and everything worked perfectly, the first time!!!!  Thank you so much for saving me tons of time and frustration!

---

### Post by odiaz1979 on 2007-06-14
Hi.
Thx for the tips.

I followed every step carefuly and It worked, even got beryl working
but after the first reboot I've got the "not matching kernel" error.
I removed everything (uninstalled) and tried again a couple of times. It did fail every time.
Right now is working fine but I had to edit the xorg.conf file to "composite"= "disabled".
Now every time I reboot my card is recognized (I see the nvidia logo).
I guess I have to wait until there's a new driver/fix for this.
I tried 100.14.06 and 100.14.09 both did the same.

Thx Againg for the Tips.

my machine conf..
Mobo: Intel P965LT
Proc: Intel C2D E6600
Ram: A-Data 2G 800
Video: XFX GeForce 8600 GT 256 
Mon: Samsung SyncMaster 906BW 1440x900@60 
HDD: Seagate SATA II 320 Gb

---

### Post by blazko on 2007-06-15
Hello,

It will just not work. I removed all restricted modules and nVidia-Packages and used the beta *09 driver (also removed "splash" from grub). When I start X, the last lines are:

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.

```

...and then the box freezes - i.e. my monitor shows "no signal" and I even cannot access the computer via ssh - so it is really locked.

I also tried "nv", but is says of course that it does not know a Geforce 8600 and "vesa" complains about a found screen which is not usable:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "GeForce8600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
##              Modes           "1360x768" "1280x768"
                Modes           "1280x768"
        EndSubSection
EndSection

```

The nVidia module is loaded and seems to be the actual one (the .ko file has the correct timestamp of today).

Has anyone had the same problems?

Regards,
Timo

---

### Post by FictionPimp on 2007-06-16
Now that these drivers are offically released, do you think fiesty will be updated to automatically use them?

---

### Post by The Brain on 2007-06-25
Have just managed to get mine working as of 5 minutes ago. Tried just about everything - and I think that was the problem. Finally got it working by firing up Envy but selecting 'uninstall nvidia' and then 'clean settings' I think it was before installing nvidia. Basically wiping all the crap that I'd managed to install and starting fresh. Phew ! Your waste of time will not be refunded !

Also had to vi xorg.conf and add 'Option "NoPowerConnectorCheck" "true"'. Fun, fun, fun...

---

### Post by durand on 2007-06-25
Just about to install a new graphics card - XFX 8600 GT XXX...hope this works...sems like most people are successful :) Thanks in advance for this guide :X

---

### Post by durand on 2007-06-26
Ok, I've got it installed and working, i think... I've been playing tremulous at the highest quality with a high fps so it seems like its working. Any other ways to check? thanks :D

---

### Post by Linux_Punk on 2007-07-02
Hey i know this forum is kind of old or what not, but i just wanted to so a huge thanks because i know it means a lot to people on positive feedback. Worked grea, can run Desktop Effects and Beryl perfectly. thanks to everyone who contributed:D

---

### Post by bigboy4074 on 2007-07-17
Just wanted to give my thanks also, was getting no where trying to do this on my own had some issues at first but getting the newer driver from nvidia (the one linked in the guide wouldn't work for me) and not updating to the .16 Kernel ... now everything works great thanks so much.

---

### Post by phinn on 2007-08-20
So does anyone know what the cause of this problem is? Is it a Feisty issue or is it that the actual NVIDIA drivers don't support Linux?

As of Version: 100.14.11  off of NVIDIA's site they still do not work.

This is an absolutely terrible problem as it is forcing me to abandon Linux until I can get some decent drivers.  I almost wish I hadn't upgraded my video card to an 8600GT

---

### Post by durand on 2007-08-20
> **phinn said:**
> So does anyone know what the cause of this problem is? Is it a Feisty issue or is it that the actual NVIDIA drivers don't support Linux?

As of Version: 100.14.11  off of NVIDIA's site they still do not work.

This is an absolutely terrible problem as it is forcing me to abandon Linux until I can get some decent drivers.  I almost wish I hadn't upgraded my video card to an 8600GT

What? They don't work for you? That driver version works perfectly here...on XFX 8600GT maybe its your computer...Whats the error anyway?

PS: Its just that ubuntu needs to update restricted-manager to the latest version and I don't know much but I think its a long process..

---

### Post by phinn on 2007-08-21
They don't work for me at all.  I follows the guide closely and all I do is get tossed out to the terminal with a ton of errors about no valid screens being found.

If I edit my xorg.conf file from "nvidia" to the regular "nv" driver it starts right up. (using sudo /etc/init.d/gdm restart)

I don't understand why this doesn't work, I tried a few other things as well. Drivers seem to be a constant headache with Ubuntu for me.  If only they would update there repos more often a lot of problems might go away...

By the way, I have an XFX 8600GT (620MHz) video card just like you. I doubt its my computer, everything was fine when I had my old card in, and this current setup works perfect in Windows I'm sad to say.

This really blows, especially because I am now forced to use Windows until I can get this running...

---

### Post by durand on 2007-08-21
hmm, i get that error when they update the kernel...this might be far fetched but maybe the kernel was updated since you last installed the drivers...if so, run the driver installer again. it will build the module for the new kernel...its worth a try anyway.

EDIT: You say that you restarted gdm but ur profile on the sidebar says that you use Kubuntu...Kubuntu uses kdm...not gdm
....
..
unless you installed it, that is >_>

---

### Post by phinn on 2007-08-23
It's working!  Although this guide did not work for my Feisty box I downloaded the Envy script and ran it. I don't know why I didn't try this first as this worked for me a year or so ago when I had an issue too.

I ran Envy and the whole thing worked after a reboot...
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

This worked perfect on my new GeForce 8600GT 620MHz card


edit:   Although everything does appear to be working there is some serious sluggishness in Gnome.  I have always thought KDE to be a bit faster than Gnome in terms of windows being moved and resized, mainly in the redraw speed (which has compelled me to use KDE for most stuff). However on my home PC where I have just Ubuntu (with only Gnome installed) the windows redraw SLOW.  If I open Pidgin and resize a chat window say, it'll redraw sluggish.  Also if I open new tabs or close them in Firefox you can see the redraw time instead of it looking instant like Windows.  I think this is a driver issue as I don't remember Gnome being THIS SLOW.

Anyone have any ideas?  Maybe an xorg.conf setting, I dunno.

---

### Post by durand on 2007-08-23
> **phinn said:**
> 

edit:   Although everything does appear to be working there is some serious sluggishness in Gnome.  I have always thought KDE to be a bit faster than Gnome in terms of windows being moved and resized, mainly in the redraw speed (which has compelled me to use KDE for most stuff). However on my home PC where I have just Ubuntu (with only Gnome installed) the windows redraw SLOW.  If I open Pidgin and resize a chat window say, it'll redraw sluggish.  Also if I open new tabs or close them in Firefox you can see the redraw time instead of it looking instant like Windows.  I think this is a driver issue as I don't remember Gnome being THIS SLOW.

Anyone have any ideas?  Maybe an xorg.conf setting, I dunno.

Um, maybe its using the vesa drivers instead? You should post your xorg.conf.

---

### Post by anim on 2007-08-26
Sorry guys for not supporting this thread so much, I forgot to subscribe to it and my research starting taking up too much time to check the forums.

I don't know how well these directions will work now, because the 8600 GTX drivers are now out of beta and *should* be different to install. Since I'm still running on beta drivers myself, I'll try to install the official drivers sometime in the next few weeks and make a post on how to get those up and running...

I appreciate the kind words, it makes documenting this stuff well worth it.

anim

---

### Post by durand on 2007-08-27
The beta drivers are now the official drivers but they work in exactly the same way so you might want to change the link in the OP to the official nvidia.com site.

---

### Post by Marat Galiev on 2007-08-27
Hi guys!
Sorry for my English:)
I'm only a Russian student...
Today i have my NVIDIA 8600GT card worked in Ubuntu 7.04!!!
I'm so happy!
This my way:
[CODE]
Only 27 steps:)
1)Install packages xserver-xorg-dev,pkg-config,libc6-dev.
You an find them at packages.ubuntu.com.
2)Press ctrl+alt+F2.
3)sudo nano /etc/init.d gdm stop
4)cd /there/your/driver/location
5)sudo sh NVIDIA-100.14...-xxx.run --ui=none
(without GUI menu).
To the question with nvidia-xconfig answer "Yes".
6)sudo nano /etc/default/linux-restricted-modules-common
Edit line
DISABLED_MODULES="nv nvidia_new"
7)sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko /lib/modules/2.6.20-15-generic/volatile/
8)sudo modprobe nvidia
9)/sbin/ldconfig
10)/sbin/depmod -aq
11)reboot
12)step 7
13)cd /lib/modules/2.6.20-15-generic/volatile/
13)sudo insmod ./nvidia,ko
14)sudo modprobe nvidia
15)step 9
16)step 10
17)sudo /etc/init.d/gdm start
18)reboot
19)cd /lib/modules/2.6.20-15-generic/kernel/drivers/video/
20)sudo cp nvidia.ko nvidia_new.ko
21)sudo insmod ./nvidia.ko
22)step 9
23)step 10
24)ctrl+alt+F7
25)sudo nvidia-xconfig
26)reboot

OK!So,please check you glxinfo command.
You can see what:
[B]OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11[/B]
Thank's.

---

### Post by jazzun4141 on 2007-08-29
After 5 attempts I finally got the Geforce 8600 GT working on a x64 installation. Had to reconfigure x to use nv driver.

Thank you so much guys.:)

---

### Post by durand on 2007-08-29
@Marat Galiev Thanks for the step by step guide but why do all that when you can just use the original one? That works just as well...at least for me...Maybe you should translate it into Russian for russian ubuntu users?

@jazzun4141 Why did you reconfigure it to use the nv driver? It's supposed to be using the nvidia driver if it is to work properly. nv is the open source version which is great for most things but for this thread, the point is to use the nvidia driver which is the proprietory one. Anyway, you could post how you did it. It might be useful to other people running x64.

EDIT: This is the first time I've actually read the whole thread from the start and it seems that people don't understand one thing. Whenever you update the kernel or initrd or some other stuff, you will need to reinstall the driver so it can make the ko file against the latest kernel. Its pretty simple.
cd to where you downloaded the installer
then type:
```
sudo ./NV* -s
```
This way it just updates the driver module for your current kernel version without opening the graphical interface. As of now, until ubuntu updates its drivers in restricted-manager to the latest, you will have to keep doing this for every new kernel you install. :(

---

### Post by huntermix on 2007-09-06
I've just bought an 8600gt xfx xxx edtition.. being a previous owner of an asus 6600gt I thought this would work better but once I installed the drivers it seemed that everything worked MUCH slower...

resizing windows is awfully slow, also changing tabs in firefox... anyone got the same results, should I wait for a new driver?

thanks for the help :)

---

### Post by durand on 2007-09-07
Um, thats because your using the vesa driver. It is the failsafe driver used by X if it cant get one for your card. Anyway, you should follow the guide here, its pretty simple...

To Everyone: As of Gutsy, the latest nvidia driver is now in the repositories so you can now use restricted manager to install it! Makes things so simple :)

---

### Post by huntermix on 2007-09-08
Hi durand, thanks for the reply... I checked xorg.conf and it's using "nvidia" driver, glx extensions are working, it's just working wayyy slower than with my previous card. Even the vesa driver works slower with my 8600 than with my 6600. I think it has something to do with xorg, since with gutsy it seems much more responsive

I have the same card that you have, xfx xxx edition.... I tried gutsy yesterday and after installing restricted drivers xorg wouldn't work with nvidia driver... weird! :)

---

### Post by durand on 2007-09-08
um, I actually installed nvidia-glx-new manually...that way, it should work..:

nvidia-glx-new - NVIDIA binary XFree86 4.x/X.Org 'new' driver

---

### Post by huntermix on 2007-09-08
thanks, I will download latest gutsy build today and try again following the guide.....

gutsy does look promising ! :)

---

### Post by wizochelle on 2007-09-14
I am really new to Ubuntu; I installed it on my PC and I am dual-booting with XP; I have tried for a week to install the nvidia drivers without avail. tonight I will try this method and see if it works for me. I have been all over the internet trying to find a solution. this one looks promising.

---

### Post by jrutten on 2007-09-17
Hey i hope this isnt a completly dumb question but i have spent the last few days on and off trying to get it to work and i am new to ubuntu but, well for starters when i try 

 sudo /etc/init.d/gdm stop 

it says 'sudo: /etc/init.d/gdm: command not found0000 @ 8000-d000'

not sure if that is important... but the main problem is when i run 

NVIDIA-Linux-x86_64-100.14.06-pkg2.run

it comes up with:
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
in the log it says:
Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5214'
   of a running X server.

like i said im long time windows but since my bro showed me the Ubuntu way have no desire to go back... tried few things to stop the X server, however i don't even know what one is and i imagine it is important because i always get 'access denied' 

i just got this computer few days ago and this is the first thing i am atempting to do to the computer... 
spec:
Intel Core2 Duo E6750 running at 2.66GHz
2 GB DDR2 667 MHz
320 GB Hdd, 2 GB partition for boot, 45GB empty for room for windows, 50GB (45 linux 5 swap) and rest for storage...
and GeForce 8600 GT... its NOT The GTX or the XXX or the XFX version... 
thinking its a simple thing with the X servers but i don't know what to do with them...
would really appreciate some help, cheers Jules

---

### Post by jrutten on 2007-09-17
omg i am a complete git! i had ect not ETC!!!!! ohhh dont worry i fixed the problem... after like 3 days it was a simple spelling error... always the simplest mistakes the most challenging... anywayz i recon it should work now, so cheers and grats on the post!!! :D:D

jules

---

### Post by Leon945 on 2007-10-12
ok.. i have a problem...
this doesnt work for me..

i tried thew guide at the begining, but no..
i tried envy, and it installed the "vesa" driver...

i first, (before attempting the guide) tried to install the nvidia driver from the nvidia web page following their instructions..

it compiled some stuff..
and told me it would write it to my xorg.conf file

but when i reboot, it tells me to ensure my system has an nvidia gpu.

i know it does! i just bought it...

dang...
iu know im not giving many details...
what should i post? any help? thanks...

---

### Post by durand on 2007-10-12
Um, ok... can you post the output of lspci here.

```

lspci > lspci_output
```

Then just attach the lspci_output file.

---

### Post by Leon945 on 2007-10-12
thanks for the help...

i uninstalled the nvidia driver via envy this morning, because i was planning to upgrade to gutsy just so you know...

here is the output now (nvidia driver uninstalled).
my motherboard has an integrated geforce 6200 i think, but according to the BIOS it should be disabled since im using a PCI one...

---

### Post by durand on 2007-10-12
Well, that will make things a lot easier. Gutsy is going to be released this coming Wednesday anyway.

Your lspci output does show you have a GeForce 8 card cos it says Unknown and only the new cards are shown like that..Anyway, try gutsy, and then just install nvidia-glx-new:

```
sudo apt-get install nvidia-glx-new
```

---

### Post by Leon945 on 2007-10-12
okay, thanks..

hopefully i'll be able to upgrade tonight...
:)

thanks again for your help

---

### Post by Leon945 on 2007-10-13
hello
i updated to gutsy...

but no luck with the driver...

if someone could please tell me where the Xserver log is? so i can post the output..

basically the error is.

nvidia dirver is 100.14.whatever (cant remember but i know it's the latest) but the nvidia kernel module is a different version. please make sure ALL nvidia components have the same version.

and then it says it cant find my nvidia gpu, please ensure there is an nvidia gpu in your system.

lspci now shows my card
```
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

what can i do here?
im now working with the "vesa" driver... :S

help?

---

### Post by Leon945 on 2007-10-13
okay.. i managed to find the xorg log,
here it is attached.

---

### Post by durand on 2007-10-13
Erm...why did you install the driver from the website? You should use restricted-manager as the latest driver works in gutsy. Just go to Administration > Restricted Drivers Manager

You may need to update gutsy to the latest packages first.
```
sudo apt-get dist-upgrade
```

---

### Post by Leon945 on 2007-10-13
well...
i first installed the driver from nvidia webpage using feisty because, my logic was, if it's not availble through ubuntu, i should go to nvidia..

so that's pretty much it..

umm.. i already have the latest packages...
same problem...

so what does this mean?
am i damned to hell for trusting nvidia?
will I have to do a fresh install of gutsy?

---

### Post by durand on 2007-10-13
> **Leon945 said:**
> well...
i first installed the driver from nvidia webpage using feisty because, my logic was, if it's not availble through ubuntu, i should go to nvidia..

so that's pretty much it..

umm.. i already have the latest packages...
same problem...

so what does this mean?
am i damned to hell for trusting nvidia?
will I have to do a fresh install of gutsy?

Um, no...Uninstall the official package first. Then, go to restricted-manager to get the ubuntu one. Its the same driver, just that restricted-manager recompiles every time there is a new kernel. Alternatively, you can recompile it for every kernel update urself. There is a post in this thread about doing that.

---

### Post by BaasJan on 2007-11-06
Hi, I don't know if someone can help me, I am a noob with Linux and just installed Gutsy. I have a xfx 8600GT. When I installed the nvidia drivers downloaded from their site, it didn't work and I had to edit xorg to use the nv driver again. Then I tried the restricted driver manager to do the job for me. Now Ubuntu works, but everything is blue-gray, the colors are all wrong. I am now using the nv driver and everything works fine, but I would like to get the best out of my video card. Any replies would be appreciated.

---

### Post by Leon945 on 2007-11-06
you DID say any replies would be welcome...
sooooo...

my problem was, that i updated to gutsy and i tried restriced driver manager...
that didnt work for me.. (i had downloaded the installer from the nvidia site first).

So... really.. i had no idea what to do.. so just reinstalled ubuntu completely (with gutsy)...
then, with a fresh install i went directly to restricted driver manager and "enabled" the driver...

that got it working for me...
apparently downloading the driver from nvidia is not a good thing... but dont take my word for it.
It's just my case...

---

### Post by durand on 2007-11-08
Well, I think you can uninstall the official nvidia drivers but I'm not exactly sure how....Google it ;). Anyway, BaasJan, don't use the official drivers from the site. Since you have gutsy, you can simply run the restricted manager from: System > Administration > Restricted Drivers Manager. This should configure everything for you. You have to choose the Geforce 8 Series driver, but it should detect it automatically anyway..

---

### Post by BaasJan on 2007-11-08
Thanks, but everything works now. The problem was my refresh rate. I use a resolution of 1440x900 and the automatically detected refresh rate of 50Hz caused problems. A rate of 59Hz works fine. I discovered this while playing around with resolutions.

---

### Post by anim on 2007-11-11
updated OP, sorry for not supporting this better. If you have something else for me to update, PM me and I'll get it up quick.

---

