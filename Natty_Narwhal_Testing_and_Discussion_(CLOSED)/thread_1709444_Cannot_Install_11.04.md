---
title: "Cannot Install 11.04"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Buschbarber on 2011-03-18
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I have downloaded the Desktop AMD 64bit version numerous times. I have burned numerous DVD's, both in Windows 7 and Ubuntu. Each time I boot from the DVD, I receive an error indicating the Installer has failed and a Desktop session comes up. If I try to run the Installer, I receive a Ubiquity error. I cannot get any further.

---

### Post by ngsupb on 2011-03-18
what is the Ubiquity error? I had some error with it too when I tried to intall from usb. Had to setup a symlink from /media/cdrom to some folder on the usb drive (casper folder?? don't remember).

---

### Post by jerrylamos on 2011-03-18
> **ngsupb said:**
> what is the Ubiquity error? I had some error with it too when I tried to intall from usb. Had to setup a symlink from /media/cdrom to some folder on the usb drive (casper folder?? don't remember).
If you scan the threads in the Natty forum, you'll find all sorts of entries that 11.04 won't install over the last couple months.  

Basically Natty install and ubiquity have been busted since sometime in late February.  Following the many launchpad bugs I don't see much progress.

If you do want to get Natty running, then do the Natty alternate install and then load in all the features you need:

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

Jerry

---

### Post by VMC on 2011-03-18
> **Buschbarber said:**
> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I have downloaded the Desktop AMD 64bit version numerous times. I have burned numerous DVD's, both in Windows 7 and Ubuntu. Each time I boot from the DVD, I receive an error indicating the Installer has failed and a Desktop session comes up. If I try to run the Installer, I receive a Ubiquity error. I cannot get any further.

That is the correct link you listed, make sure you download this [amd64 ISO]("http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso").

Everything works using todays ISO. Major progress. The partitions are only listed if you mount the device. Saves much space.

---

### Post by Buschbarber on 2011-03-18
The first error I see is:
"Install Failed"
"The installer encountered an unrecoverable error. A Desktop session will now be run so that you may investigate the problem or try installing again"

When I try to run the Installer from the Desktop session:

"Application Problem"
"Sorry, GSettings Data Conversion closed unexpectedly"

"Application Problem"
"Sorry, ubquity closed unexpectedly"

From this point on, I get the same two errors every time I try to run the Installer.

---

### Post by Buschbarber on 2011-03-18
Title:
 ubiquity crashed with DebconfError in command(): (10, "debian-
 installer/fallbacklocale doesn't exist")

Status in “ubiquity” package in Ubuntu:
 New

Bug description:
 Binary package hint: ubiquity

 Trying to Install 11.04 after booting from DVD and running Insall
 11.04 from Desktop Session

 ProblemType: Crash
 DistroRelease: Ubuntu 11.04
 Package: ubiquity 2.5.26
 ProcVersionSignature: Ubuntu 2.6.38-6.34-generic 2.6.38-rc7
 Uname: Linux 2.6.38-6-generic x86_64
 Architecture: amd64
 Date: Fri Mar 18 19:25:15 2011
 ExecutablePath: /usr/lib/ubiquity/bin/ubiquity
 InterpreterPath: /usr/bin/python2.7
 LiveMediaBuild: Ubuntu 11.04 "Natty Narwhal" - Alpha amd64 (20110317)
 ProcCmdline: /usr/bin/python /usr/lib/ubiquity/bin/ubiquity gtk_ui
 ProcEnviron: Error: [Errno 13] Permission denied: '/proc/4255/environ'
 PythonArgs: ['/usr/lib/ubiquity/bin/ubiquity', 'gtk_ui']
 SourcePackage: ubiquity
 Title: ubiquity crashed with DebconfError in command(): (10, "debian-installer/fallbacklocale doesn't exist")
 UpgradeStatus: No upgrade log present (probably fresh install)
 UserGroups:

---

### Post by KegHead on 2011-03-18
Hi!

I use a USB stick only-32 bit.

Never had a problem.

I know it's a very simple answer, but it works for me.

KegHead

---

### Post by KegHead on 2011-03-18
Hi!

Ooops!

When I downloaded today's image I noticed that the iso won't fit on a cd. 700mb.

Just checking to make sure a dvd is used!

KegHead

---

### Post by Buschbarber on 2011-03-18
> **KegHead said:**
> Hi!

Ooops!

When I downloaded today's image I noticed that the iso won't fit on a cd. 700mb.

Just checking to make sure a dvd is used!

KegHead

It states, on the Download WebSite, that due to a bug, the image needs to be put on a DVD.

I downloaded and burned a DVD of today's ISO. This time, the Installer worked as designed and I was able to install 11.04 64bit AMD, from DVD. 

There were a couple of apps, including GSettings Data Conversion that quit unexpectedly. I clicked on Report Problem, but was informed that the Crash was not reportable.

I installed the recommended 3D Nvidia driver, but I need to know how to install the latest Nvidia Driver. I could not find System/Preferences to see if the Nvidia Settings was installed.

Is there a Package Manager that allows me to install other software? Ubuntu Software Center does not have any choices for Gmail. I also need a Wallpaper Changer, like Wally.

---

### Post by cariboo on 2011-03-18
To find nvidia-settings, click the Application icon (the one with the scissors and triangle) and type nv in the search box. I'd suggest you use synaptic package manager to install and update, as there seems to be a bit of a problem with the Software Center. If the two apps you want to install are panel applets, you are out of luck, as panel applets don't work in Unity. You can still install them on the Classic Desktop though.

---

### Post by Buschbarber on 2011-03-18
Where did they hide Synaptic Package Manager?
How do you get to the Classic Desktop?

---

### Post by Buschbarber on 2011-03-18
I found the switch for the Classic Desktop at the bottom of the Login screen and I also found Synaptic.

I am unable to install the latest Nvidia driver. I boot in the Recovery Mode, escape to the Terminal, run sudo /etc/init.d/gdm stop then sudo sh ./N.....

The installation fails and it cannot update the kernel.

I was able to do it in 10.10

---

### Post by cariboo on 2011-03-18
Why not install nvidia-current from the repositories, click the Applications icon in the panel and type add in the search box for Additional Drivers. To open Synaptic do the same thing except type synaptic in the search box.

As you use applications in Unity, the most used apps are presented first. See the screenshot.

---

### Post by Buschbarber on 2011-03-18
Thank you!! Synaptic did the trick and the drivers are installed and working.

I output from my PC's video card to a 50" HDTV using DVI to HDMI, at 1920x1080p. Early on, with Ubuntu, I had problems with the edges of the Ubuntu Desktop being Cutoff due to Overscan. Since then, the newer versions of the Nvidia Driver have a slider that lets me Shrink the Desktop to fit the HDTV frame. I just wanted to make sure I had a new enough driver to do that. Also, GoogleEarth requires such a driver, as well.

---

### Post by Buschbarber on 2011-03-19
I have 4 HDD's on my PC. One is running W7 Pro 64bit, one is a backup HDD for W7, one is running UE 2.8 (based upon 10.10) and one is running Ubuntu 11.04.

When the Grub Menu was established, during the install of 11.04, it only lists 11.04 and W7. There is no longer any choice for my UE 2.8.

How can I add that back in to the Grub Menu?

---

### Post by VastOne on 2011-03-19
> **VMC said:**
> That is the correct link you listed, make sure you download this [amd64 ISO]("http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso").

Everything works using todays ISO. Major progress. The partitions are only listed if you mount the device. Saves much space.

Decided to try today's current based on this and just like the other 15 wasted DVD's this one failed... exact same way and place... 75% in and dead

---

### Post by Buschbarber on 2011-03-19
I downloaded today's 64bit iso and burned it to DVD. It booted to a screen that gave me the option of Try It or Install It. I chose Try It and it booted to a Live DVD. When I tried to run the Install Icon, it crashed about half way through. I Shutdown and Rebooted. I clicked on Install It and the Install went without a hitch. When I rebooted, the Grub2 Menu had the listings for the new Kernel, Windows 7, and the Kernels from UE 2.8, as well. I installed the Nvidia Current drivers and all is well. 

GSettings Data Conversion quit. I do not know what this process does. Nothing else seems to be wrong.

---

### Post by jerrylamos on 2011-03-19
> **VastOne said:**
> Decided to try today's current based on this and just like the other 15 wasted DVD's this one failed... exact same way and place... 75% in and dead

Have you tried the Natty alternate install?

[http://cdimage.ubuntu.com/cdimage/daily/current/](http://cdimage.ubuntu.com/cdimage/daily/current/)

It still fits on a CD.  It uses a text based screen and doesn't run across all the X and Compiz problems with the daily-live.

After the install finishes you have the option of what packages to install which can include all the stuff that's on the regular install.

I don't know what hardware you've got.  On my older pc's Unity 2D runs fine, on the later faster pc's I'm running Unity 3D looking for bugs.

[http://ubuntuforums.org/showthread.php?t=1706469](http://ubuntuforums.org/showthread.php?t=1706469)

Good luck, Jerry

BTW on my later pc's which will boot from USB I use the USB stick to fit the obese Natty daily builds.

Having said that, there's only been a couple daily builds over the last month that will install on my pc's.  Mostly install and/or ubiquity are busted even to the extent of altering grub2 boot menu even though I haven't issued a "change".  After Natty Grub 1.99 has messed up my boot choices I run Meerkat or Lucid update-grub and grub-install /dev/sda to straighten things out.

---

### Post by Buschbarber on 2011-03-19
I spoke too soon. When I rebooted into Classic Desktop, everything was OK, but when I booted into Unity, I had no menus on top and I received an error the Compiz had crashed. I was able to Right Click on the Desktop and get a menu, although there were no useful choices. I was able to Ctrl-Alt-Del, and click on Restart. I logged in to Unity, but I still had no menus on top and no icons anywhere except the ones for my iPod.

The only difference between this install and the last one was that for this one, I ran Update Mgr and installed the Updates it recommended. I do not know if that caused the problem.

I had no problem with Unity after my first install yesterday.

---

### Post by Buschbarber on 2011-03-19
I can go into Ubuntu Desktop Safe Mode and Classic Desktop, but not into Ubuntu Desktop. Perhaps the Nvidia driver has something to do with it, but I tried reducing the Overscan with the Nvidia Settings, while in Ubuntu Desktop Safe Mode, yet, when I login to Ubuntu Desktop, the display is smaller but it appears all the edges of the Desktop are cutoff, so I have no controls.

---

### Post by Buschbarber on 2011-03-19
An IT friend of mine just ran into the same problem I did, as soon as he ran Update Mgr. After rebooting, he logged in to Ubuntu Desktop and only had the Wallpaper. I believe he said that he reinstalled choosing to add Updates during the Install. Now he is working OK.

---

### Post by cariboo on 2011-03-19
If you can get a right-click menu, you should be able to create a launcher for gnome-terminal. Once you have created it, double-click to open a terminal and type:

```
unity --reset
```

Or try Ctrl-Alt-t to open a terminal and type the above command.

---

### Post by Buschbarber on 2011-03-19
When I right click and try to create a launcher, I click on Browse, and choose gnome-terminal from the bin folder. When I try to type the name for the Launcher or try to type a comment, it will not let me. If I click Ok, Ivreceive an error that there is no name.

---

### Post by VMC on 2011-03-20
> **Buschbarber said:**
> When I right click and try to create a launcher, I click on Browse, and choose gnome-terminal from the bin folder. When I try to type the name for the Launcher or try to type a comment, it will not let me. If I click Ok, Ivreceive an error that there is no name.

That's the problem I was having. No keyboard input. Only mouse input. As I stated earlier, when I first install natty using classic , I then create a desktop file with the command cariboo mentioned, made it executable. then install 3d drivers and if compiz crashes I then double click on the file I created. It was worked wonders so far.

---

### Post by Buschbarber on 2011-03-20
I reinstalled 11.04 64bit and just installed gm-notify and Nvidia Current. I did not run Update Mgr. I am able to work in Ubuntu Desktop, however, System crashes every so often. I am trying to get used to the Unity interface. I do not know how to add Icons to the list on the left side of the Desktop.

---

### Post by cariboo on 2011-03-20
I run docky just in case something like that happens. You should be able to create a launcher on the Classic Desktop, and then try to run Unity again. You can then run the unity --reset command if you need it.

---

### Post by mc4man on 2011-03-20
> I do not know how to add Icons to the list on the left side of the Desktop.
There are several ways to add - 
When you open an app you should see it's icon in the launcher, just r. click on the icon - "Keep in Launcher"

You also can drag an icon from the dash (applications) to the launcher, though that may not work very well right now, the former method is better atm.
(there are currently some potential issues introduced in the dash with unity 3.6.6

You can also drag an app from /usr/share/applications/ directly to the launcher - that should work well now, as will dragging any launcher or .desktop you have created

---

### Post by jerrylamos on 2011-03-20
> **mc4man said:**
> There are several ways to add - 


Delete is also easy.  Default launchers include Tomboy which I never use, Ubuntu One, ... so right click on them and delete.

Jerry

---

### Post by Buschbarber on 2011-03-21
I now am dealing with a nasty ticking sound whenever an audio clip is played. I have a Realtech Sound Adapter. Are there any other options for additionally controlling sound? I have chosen 5.1 Surround Sound in the Sound Control Panel. In other versions of Ubuntu you could install additional Sound Controls.

---

### Post by VastOne on 2011-03-21
> **jerrylamos said:**
> Have you tried the Natty alternate install?

[http://cdimage.ubuntu.com/cdimage/daily/current/](http://cdimage.ubuntu.com/cdimage/daily/current/)

It still fits on a CD.  It uses a text based screen and doesn't run across all the X and Compiz problems with the daily-live.

After the install finishes you have the option of what packages to install which can include all the stuff that's on the regular install.

I don't know what hardware you've got.  On my older pc's Unity 2D runs fine, on the later faster pc's I'm running Unity 3D looking for bugs.

[http://ubuntuforums.org/showthread.php?t=1706469](http://ubuntuforums.org/showthread.php?t=1706469)

Good luck, Jerry

BTW on my later pc's which will boot from USB I use the USB stick to fit the obese Natty daily builds.

Having said that, there's only been a couple daily builds over the last month that will install on my pc's.  Mostly install and/or ubiquity are busted even to the extent of altering grub2 boot menu even though I haven't issued a "change".  After Natty Grub 1.99 has messed up my boot choices I run Meerkat or Lucid update-grub and grub-install /dev/sda to straighten things out.

Yes Jerry I did based on your recommendation, thank you... 

The install got to a point and just stalled out.. A Half purple and half white screen where I had no choices to do anything.  After an hour I shut it down..

For anyone suspecting the machine, I can and have installed every other version of Ubuntu, Kubuntu, Xubuntu, and at least 10 other flavors of Linux with no issues, including Alpha 3 of anything other than Ubuntu...

I do not like the upgrade -d option from a fresh install of Maverick, but it is the only thing I can get to work

---

### Post by mc4man on 2011-03-21
> **VastOne said:**
> 

The install got to a point and just stalled out.. A Half purple and half white screen where I had no choices to do anything.  After an hour I shut it down..

It's too bad you can't use a usb stick, it would save you some money and certainly a lot of time, it's  either going to install in a few min. or not at all.

If inclined to attempt again from the live cd there's an outside possibility you could catch what it's failing on.
In the bottom panel of the installer is a little white arrow - if you click on it once the install starts  you'll get a small terminal like window, maybe you can see the failure there

---

### Post by VastOne on 2011-03-21
> **mc4man said:**
> It's too bad you can't use a usb stick, it would save you some money and certainly a lot of time, it's  either going to install in a few min. or not at all.

If inclined to attempt again from the live cd there's an outside possibility you could catch what it's failing on.
In the bottom panel of the installer is a little white arrow - if you click on it once the install starts  you'll get a small terminal like window, maybe you can see the failure there

I can use a USB to install... 

But the point of testing is to test all facets, and this one definitely needs resolving..

Thank you for your concern and tips, I do appreciate it

---

### Post by jerrylamos on 2011-03-21
> **mc4man said:**
> It's too bad you can't use a usb stick, 

The CD Daily Build has been sitting at 708 MB for days (or is it weeks?).

Do the developers want people to install and test Natty or not?

I can't believe they couldn't dump some games or even Libre to get the space down for a CD.  I can download Libre later after install.

Maybe the developers are trying to keep the bug rate down.

Yes, I can install Natty from USB  on one of my pc's, but not two others for example IBM Thinkpad T40 and IBM ThinkCentre A30 with integrated i915 type video graphics.  There's lots of them out there to judge from the Launchpad bug entries on Maverick.

To me the ultimate "ankle-biter" to testers is "won't install" which has been around for a month. 

And yes I could go the "alternate" install route, but is that what Ubuntu thinks most new users would do?

Jerry

---

### Post by lucazade on 2011-03-21
> **jerrylamos said:**
> 

And yes I could go the "alternate" install route, but is that what Ubuntu thinks most new users would do?



New users should use stable releases.. 
Why can't you use usb stick with T40? It has 2 usb ports and a boot-capable bios.

---

### Post by Buschbarber on 2011-03-21
I too have installed many versions of Ubuntu and I sometimes have to Download and Burn the Install CD in order to get a good working copy.

Have you run the Check CD for Defects, on the menu below Install?

---

### Post by jerrylamos on 2011-03-21
> **lucazade said:**
> New users should use stable releases.. 
Why can't you use usb stick with T40? It has 2 usb ports and a boot-capable bios.
I've tried any number of times to get my T49 to boot from USB.  It hangs up every time.

I tried booting from a USB hard drive, which it recognized, started to boot then nothing eventually timing out.

When not trying to boot from USB, the USB ports work fine for a keyboard, a mouse, and an Epson printer.

Looking at Compiz Settings Manager, maybe we need two CD's - one for Compiz and Unity 3D, the other for all the rest of Ubuntu.  I'm assuming Compiz growth is what shoved Ubuntu past the CD size limit.

Jerry

---

### Post by VastOne on 2011-03-21
> **Buschbarber said:**
> I too have installed many versions of Ubuntu and I sometimes have to Download and Burn the Install CD in order to get a good working copy.

Have you run the Check CD for Defects, on the menu below Install?

Yes, every single download

---

### Post by Buschbarber on 2011-03-21
I live in Rochester, NY. There are several Linux groups here. One group has an InstallFest every so often. It is held at a site where there are many benches with power and network access. The usually have a server with goodies on it. You bring in your laptop or desktop and they will help you with stubborn installs.

I guess I have been lucky that I have not run into many hardware issues.

---

### Post by VastOne on 2011-03-21
> **Buschbarber said:**
> I live in Rochester, NY. There are several Linux groups here. One group has an InstallFest every so often. It is held at a site where there are many benches with power and network access. The usually have a server with goodies on it. You bring in your laptop or desktop and they will help you with stubborn installs.

I guess I have been lucky that I have not run into many hardware issues.

I would be ecstatic if this were a simple hardware problem, then I could fix it!!!!

As posted earlier, I can and have run every version of X,K,L and Ubuntu and 15 or so other distros with nary an issue..

Only Ubuntu Alpha 3 fails... Alpha 2 did not fail (and still does not).... Alpha 3 of Xubuntu installs perfectly

As Jerry has been saying, this issue is Alpha3 release timing on the head

---

### Post by Buschbarber on 2011-03-21
Is Alpha 3 what is currently on the Daily Build page? Jerry posted a like to the Daily Build site for Alternate images. There is another Daily Build site that looks almost the same, but has the images for the Live CD versions.

How would you know if it were Alpha 3?

---

### Post by VastOne on 2011-03-21
> **Buschbarber said:**
> Is Alpha 3 what is currently on the Daily Build page? Jerry posted a like to the Daily Build site for Alternate images. There is another Daily Build site that looks almost the same, but has the images for the Live CD versions.

How would you know if it were Alpha 3?

Yes, Alpha 3 is the what is on the Daily (a daily release of it)  and is the latest on the other install download for Natty

---

### Post by mc4man on 2011-03-22
A3 here
[http://www.ubuntu.com/testing/natty/alpha3](http://www.ubuntu.com/testing/natty/alpha3)
A3+ (daily
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Buschbarber on 2011-03-22
What is the difference between this site:

[http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/)

and these sites, which is where I have been getting my images to install:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
[http://cdimage.ubuntu.com/cdimage/daily/current/](http://cdimage.ubuntu.com/cdimage/daily/current/)

---

### Post by cariboo on 2011-03-22
> **Buschbarber said:**
> What is the difference between this site:

[http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/)

This one is the Alpha 3 iso which is more or less obsolete

> and these sites, which is where I have been getting my images to install:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

This is the daily live cd that allows you to Try Natty without installing, there is usually a new iso every day.

> [http://cdimage.ubuntu.com/cdimage/daily/current/](http://cdimage.ubuntu.com/cdimage/daily/current/)

This is the daily alternate install cd, it has a text interface, as well as options that aren't available on the Live CD.

[LIST]
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*]LVM and/or RAID partitioning;
[*]installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).
[/LIST]

---

### Post by Buschbarber on 2011-03-22
Thanks!!

---

### Post by VastOne on 2011-03-27
To address this again with an update...

Tried yesterday and today's daily with the same results..

It gets to Installing System at the very end and completely quits with a generic message

I went back to March 01 2011 daily and used it and it worked perfectly

I have been on every bug report and added me as one afflicted

This is now in it's 4th week and 17 wasted dvd's - I do not mind this, someone has to test!

---

### Post by kansasnoob on 2011-03-28
With Beta 1 coming in just three days I'd hope this would be exposed during iso testing. I always test the i386 image so I'll be watching for problems.

---

### Post by jerrylamos on 2011-03-28
> **kansasnoob said:**
> With Beta 1 coming in just three days I'd hope this would be exposed during iso testing. I always test the i386 image so I'll be watching for problems.

Well, Ubuntu Development has been reducing exposure of Natty to testing by having the .iso image larger than a CD for weeks and weeks.  That blocks me from testing latest images on the IBM Thinkpad T40 and IBM ThinkCentre A30 for example.

I'd like to spend more test time looking for bugs on Unity 3D and 2D however my time is being spent on "install" inabilities example ubiquity bug 742125.  I haven't a clue what "ubiquity code 10" is but ubiquity stops there.  

I think ubiquity bug 742102 might be fixed where as late as 24 March ubiquity failed on boot even before "install" was selected on this Acer Aspire one netbook - 1 GB memory, 250 GB hard drive, as far as I can tell has the hardware for all the Unity 3D bells and whistles,  

Of course Maverick installs quickly no problems....

Jerry

p.s.  Seems to me if Development wants a new Ubuntu to be tested the first thing they would do would be to get install solidly running -- not the last.  I do wonder what Development is spending their time on, obviously not install.  

Having said that, it's interesting testing Unity 3D and 2D something new on the block.

---

### Post by kansasnoob on 2011-03-28
I keep watching the ubiquity changelog and I've seen no indication that the UI has been completed to include full functioning of the "Use largest continuous free space" option.

I can't see much point in burning a disc ATM because I'd bet iso-testing will begin very soon, maybe tomorrow. If anyone is aware of any specific steps needed to reproduce a particular bug I'll certainly try my best to do so :)

---

### Post by jerrylamos on 2011-03-28
28 March Daily build ubiquity hung "Preparing to install Ubuntu".  There is a blank partition available formatted by gparted.  Launchpad bug #744438.

This is a multi-boot test system, Acer Aspire one netbook this entry is from a Natty vintage a month ago updated.

Beta, here we come....

Jerry

---

### Post by VastOne on 2011-03-28
> **jerrylamos said:**
> 28 March Daily build ubiquity hung "Preparing to install Ubuntu".  There is a blank partition available formatted by gparted.  Launchpad bug #744438.

This is a multi-boot test system, Acer Aspire one netbook this entry is from a Natty vintage a month ago updated.

Beta, here we come....

Jerry

I will wait for the call for ISO testing...

Then perhaps it will be relevant.

---

### Post by kansasnoob on 2011-03-28
I've just begun my first round of iso-testing for Beta1 and found no show-stopper bugs, only these two:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

They're neither new bugs.

I'd really like to get a handle on what's stopping you from being able to install but I need more info :)

The first round was using "Install alongside" next is "Manual".

---

### Post by VastOne on 2011-03-28
> **kansasnoob said:**
> I've just begun my first round of iso-testing for Beta1 and found no show-stopper bugs, only these two:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

They're neither new bugs.

I'd really like to get a handle on what's stopping you from being able to install but I need more info :)

The first round was using "Install alongside" next is "Manual".

I am ISO testing now...

Will post in 30 or so to let you know...

---

### Post by VastOne on 2011-03-28
ISO testing method - Manual Partitioning

Installer Crashed

Please send syslog and partman to launchpad Ubiquity +file bug

Problem is getting those two files as when I close the Crashed message, nothing works...

Will try to get them on a reboot

Edit - This is the same method and same results as the last 4 weeks

---

### Post by VastOne on 2011-03-28
Had to post these on pastebin as they exceeded the limit

[[COLOR="Blue"]_partman.txt_[/COLOR]]("http://pastebin.com/cAqRyQ49")

[_[COLOR="Teal"]syslog.txt[/COLOR]_]("http://pastebin.com/8QeFHepa")

Will also send these to ISO testing results and Launchpad Bugs

---

### Post by VastOne on 2011-03-28
Turns out mine is actually bug

[_[COLOR="Blue"]739632[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/739632")

---

### Post by cariboo on 2011-03-28
The installer crashed on me, but I manually installed grub, and it at least takes me to a working desktop. I'm just installing the experimental 3D driver, then I'll reboot to see what happens.

---

### Post by VastOne on 2011-03-28
I have been asked to gather data for the bug 739632, so I am reinstalling and getting it..

Glad to see traction...

---

### Post by kansasnoob on 2011-03-28
> **VastOne said:**
> I have been asked to gather data for the bug 739632, so I am reinstalling and getting it..

Glad to see traction...

Awesome! I haven't had that happen, but iso-testing is the best time to get attention focused on a bug (or bugs).

Sometimes it wears me out but I think it's well worth the effort.

I did subscribe just in case I can help.

---

### Post by VastOne on 2011-03-28
> **kansasnoob said:**
> Awesome! I haven't had that happen, but iso-testing is the best time to get attention focused on a bug (or bugs).

Sometimes it wears me out but I think it's well worth the effort.

I did subscribe just in case I can help.

Exactly... It is what makes the community just that...

Where I have been teased for wasting DVD's, I do not mind... This is the necessary evil...  And, the wasted DVD's are recycled...

A milestone has been given for this bug as Beta-1 so it is sitting pretty high

---

### Post by cariboo on 2011-03-28
the bug now says **fix committed**, so someone is working on it. :)

---

### Post by VastOne on 2011-03-28
> **cariboo907 said:**
> the bug now says **fix committed**, so someone is working on it. :)

Great to see and be a part of!

---

### Post by VastOne on 2011-03-28
Fixed Released!!!

Wow, ISO testing is the way to go!

---

### Post by VastOne on 2011-03-28
Isn't it possible to update Ubiquity whilst in Live CD? 

How would I go about that?  I know I have seen it done on here somewhere...

Edit - Found the method, but it has not reached the repositories yet..

Thanks

---

### Post by VastOne on 2011-03-29
An hour ago I was able to apt-get update ubiquity to 2.5.31 and resumed the installation

On my AMD64 Natty Daily  20110328.1 

MD5Sum: (b1b2873564bce6372b04c04bd5403ee6)

I was able to successfully install!!  

I will reinstall the full ISO from DVD when it is released - I assume later today

---

### Post by Buschbarber on 2011-04-08
I just installed 11.04 X86 on an HP Pentium D 2Ghz machine. It is a 32bit machine. The install went fine. When I first opened FireFox, it defaulted to the size of half the screen. When I clicked on Maximize, the screen went completely White. When I clicked on Maximize, again, the window went to half screen and the text appeared again. I experimented with dragging the border of the window to the right and after 1/4", the window went White.

I got up this Am to find my Desktop all White. I could see the mouse, but clicking or hitting Enter on the Keyboard, did nothing. I hit Ctrl-Alt-F1 and it took me to Terminal. I did a Sudo Reboot and it rebooted to the Login screen. It sat there for a few minutes and then the display turned White.

I did not have this problem on my other machine with the 64bit install.

---

