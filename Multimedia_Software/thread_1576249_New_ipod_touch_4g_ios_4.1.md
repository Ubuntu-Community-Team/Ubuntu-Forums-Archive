---
title: "New ipod touch 4g ios 4.1"
date: 2010-09-17
forum: Multimedia Software
---

### Post by crisponions on 2010-09-17
I just got a new 4G ipod touch.  The one with the camera etc.  It came with ios 4.1 which apparently doesn't work with Ubuntu yet.  Any ideas when this might be fixed.

---

### Post by Swazzi on 2010-09-29
having the same issue with the iphone 4 with ios 4.1

any info would be appreciated

thanks

---

### Post by Swazzi on 2010-10-01
after following the guide on this thread i was able to get Banshee to recognize my iphone 4.  It explains in very simple terms how to update banshee. 


[http://ubuntuforums.org/showthread.php?t=1345833](http://ubuntuforums.org/showthread.php?t=1345833)


hope this helps for your ipod as well

cheers

im pretty new to ubuntu but if u cant figure it out let me know and ill try and walk you through it step by step.

---

### Post by mr_luksom on 2010-10-03
check out the new libimobiledevice! PPA from Paul McEnery.

I just got my iPhone 3GS (iOS 4.1) syncing again today. I have to manually mount though (ifuse), and sync with gtkpod. Nothing a quick script can't take care of.

---

### Post by chuchutta on 2010-10-04
has anyone figured this out yet? i still cannot connect my ipod touch 4g to ubuntu and sync like i could with my older i devices.

thank you in advance!

chuchutta

---

### Post by mr_luksom on 2010-10-04
Yep. I got my phone working yesterday.

See this: [http://ubuntuforums.org/showthread.php?t=1567271](http://ubuntuforums.org/showthread.php?t=1567271)

It is not as polished as iTunes, however it will sync iOS 4.1.

---

### Post by chuchutta on 2010-10-04
> **mr_luksom said:**
> Yep. I got my phone working yesterday.

See this: [http://ubuntuforums.org/showthread.php?t=1567271](http://ubuntuforums.org/showthread.php?t=1567271)

It is not as polished as iTunes, however it will sync iOS 4.1.

Do you know if this method works with the iPod touch 4g?

---

### Post by mr_luksom on 2010-10-05
I don't have an iPod touch 4g to try, however I believe they run the same iOS as the iPhone 4 (iOS 4.1 - same as my 3GS). There should be no impediment to syncing your iPod.

Try it out and let me know how you go.

---

### Post by seadao on 2010-10-06
ipod touch 4g shows up in banshee, info like os 4.1 and free space are displayed correctly, but no data on the i pod is visible and nothing can be copied over

---

### Post by mr_luksom on 2010-10-07
> **seadao said:**
> ipod touch 4g shows up in banshee, info like os 4.1 and free space are displayed correctly, but no data on the i pod is visible and nothing can be copied over

Have you tried gtkpod, after mounting it with ifuse? I know that I can't get rhythmbox to see my iOS 4.1 3GS at all.

No problems with amarok - but I am not a fan, so I don't use it.

---

### Post by tcrapper on 2010-10-07
> **mr_luksom said:**
> Have you tried gtkpod, after mounting it with ifuse? I know that I can't get rhythmbox to see my iOS 4.1 3GS at all.

No problems with amarok - but I am not a fan, so I don't use it.

ifuse doesn't detect it.

```
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

```

Ran it with sudo.

---

### Post by seadao on 2010-10-07
$ ideviceinfo
usbmuxd_get_device_list: error opening socket!
No device found, is it plugged in?

???? even ideviceinfo cant see it

---

### Post by mr_luksom on 2010-10-08
How about lsusb?

```
 lsusb -v | grep Apple
```

It should show an 'Apple' device.

If that shows nothing, what does ```
 dmesg | tail 
``` show when you connect it?

---

### Post by maxvaillancourt on 2010-10-08
> **mr_luksom said:**
> How about lsusb?

```
 lsusb -v | grep Apple
```

It should show an 'Apple' device.

If that shows nothing, what does ```
 dmesg | tail 
``` show when you connect it?

It shows up my iPod touch, but still, I can't see it neither on my desktop, in Nautilus nor in Rhythmbox or Banshee!

Here's what the command results in exactly:
```
maxime@HPmax:~$ lsusb -v | grep Apple
Bus 001 Device 008: ID 05ac:129e Apple, Inc. 
  idVendor           0x05ac Apple, Inc.
  iManufacturer           1 Apple Inc.
    iConfiguration          7 PTP + Apple Mobile Device
    iConfiguration          8 PTP + Apple Mobile Device + Apple USB Ethernet
```

---

### Post by maxvaillancourt on 2010-10-08
Also, typing "ideviceinfo" in the terminal shows up the same thing as "seadao":

```
maxime@HPmax:~$ ideviceinfo
usbmuxd_get_device_list: error opening socket!
No device found, is it plugged in?
```

And yes, I unlocked it before plugging it in. Still, it doesn't show up anywhere but when I type "*lsusb -v | grep Apple*" in the Terminal.

Thanks for the help! ;)

---

### Post by mr_luksom on 2010-10-08
Maxv:

Using ifuse I can't see it in rhythmbox/banshee either.  It doesn't show up in nautilus (I use xubuntu - so thunar) as a separate mounted device either on my desktop or in the browser. However if you go to the directory you mounted it in using ifuse (media/iPhone maybe?) you can browse it. 

Using the ifuse method, I can only sync with amarok (didn't like it's interface) an gtkpod (which I am using).

Once you successfully mount the iPod, you may need to create a repository in gtkpod for it to 'see' the device (edit -> iPod repository preferences).

---

### Post by mr_luksom on 2010-10-08
So, it looks like it is showing up in lsusb by your previous post. Did something change?

If it is no longer showing up in lsusb, can you post:
```
 dmesg | tail 
```

If it is not being recognized by lsusb you should see errors in dmesg.

---

### Post by mr_luksom on 2010-10-08
> **tcrapper said:**
> ifuse doesn't detect it.

```
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

```

Ran it with sudo.

As long as your user has r/w access to the mounting directory, you don't need sudo. I use a shell script with gtkpod myself.

All previous comments above also (latest libimobiledevice, check lsusb/dmesg).

---

### Post by maxvaillancourt on 2010-10-09
> **mr_luksom said:**
> So, it looks like it is showing up in lsusb by your previous post. Did something change?

If it is no longer showing up in lsusb, can you post:
```
 dmesg | tail 
```

If it is not being recognized by lsusb you should see errors in dmesg.

Well, my 4th gen iPod touch never appeared whether in Nautilus (so not on my desktop either), Rhythmbox or Banshee. However, it does show up in "*lsusb -v | grep Apple*" (what I posted yesterday), but here's what "*dmesg | tail*" says:

```
maxime@HPmax:~$ dmesg | tail
[  181.581037] wlan0: direct probe to AP 00:23:69:9b:14:62 (try 1)
[  181.585176] wlan0: direct probe responded
[  181.585184] wlan0: authenticate with AP 00:23:69:9b:14:62 (try 1)
[  181.587000] wlan0: authenticated
[  181.587030] wlan0: associate with AP 00:23:69:9b:14:62 (try 1)
[  181.590569] wlan0: RX AssocResp from 00:23:69:9b:14:62 (capab=0x431 status=0 aid=6)
[  181.590575] wlan0: associated
[  181.592239] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  192.132053] wlan0: no IPv6 routers present
[  259.138045] lo: Disabled Privacy Extensions
```

Thanks for the help! ;)

---

### Post by maxvaillancourt on 2010-10-09
In fact, I think I'll let my iPod without music for today and clean install Ubuntu 10.10 tomorrow. Everything should work then, right? Still, I'll try to figure out why it doesn't work on 10.04.

Thanks for helping out, everyone!

---

### Post by tcrapper on 2010-10-09
> **maxvaillancourt said:**
> In fact, I think I'll let my iPod without music for today and clean install Ubuntu 10.10 tomorrow. Everything should work then, right? Still, I'll try to figure out why it doesn't work on 10.04.

Thanks for helping out, everyone!

I'm using ubuntu 10.10 but my iPod touch 4g is only detected as a camera.

---

### Post by maxvaillancourt on 2010-10-09
> **tcrapper said:**
> I'm using ubuntu 10.10 but my iPod touch 4g is only detected as a camera.

Uh. Now that's a bummer. We must find a solution together very quickly! I'm tired not to have music on my brand new 4G iPod touch... :(

---

### Post by seadao on 2010-10-10
jailbreak is out, has anyone try wireless sync??

---

### Post by seadao on 2010-10-10
Ok I got it to wirelessly connect with file in ubuntu, so we need a script to build and transfer the database, I don't know how to build the iTunes control folder, copying and deleting works over wifi with ifile

---

### Post by seadao on 2010-10-12
[http://wiki.archlinux.org/index.php/IPod#The_SSHFS_Way](http://wiki.archlinux.org/index.php/IPod#The_SSHFS_Way)

this looks promising

---

### Post by Flash858 on 2010-10-16
I have successfully gotten my new, jailbroken iPod touch (4.1 pre-installed) to be seen in Banshee. However, I cannot transfer music to it. I have it being seen in both Lucid and Maverick, and in both cases, I had to uninstall Rhythmbox to get the iPod to be seen.

On initial boot, I get 2 instances of the iPod visible. One of them I am guessing, is the DCIM (pictures) mount, as it does not show the capacity bar at the bottom. The other is the correct mount that Banshee should be able to use to sync Music, Video, Audiobooks, and podcasts.

When I drag an item to the iPod, it goes well initially, then an error pops up indicating the mp3 format is not supported by the device, and no converter was found to convert it.

After unplugging and reconnecting, I see only one, but it is the one without the capacity bar. It will not return until I reboot, and reconnect. That particular driver seems very fragile. Additionally, I am getting a dbus error when I connect it the 2nd time, and it typically will not mount in Nautilus when Banshee is running.

I am guessing I have some conflicting libraries, but I cannot find them. Apt-get autoremove got rid of libipodui-cil, libipod-cil, and podsleuth, but I am guessing tyhere is more housecleaning to do if others are having success with ios 4.1.

Any cleaning tips would be appreciated... ;)

---

### Post by wickstopher on 2010-10-17
I'm having the EXACT same issue as maxvaillancourt.  Using 10.04, have installed libimobiledevice1 from ppa:pmcenery/ppa and still no dice.  I get the same message from ideviceinfo, and lsusb shows a device from "Apple, Inc."  The iPod shows up on my desktop, but as a camera with 56MB of free space (this is a 32GB iPod), indeterminate permissions, and no apparent mount point.  No luck on my laptop running 10.10, either.

---

### Post by seadao on 2010-10-17
i compiled gtkpod from git, it has the serials for all 3 new ipods touch 4gs, my theory was to build an itunes db on my harddrive first and then transfer it(copy paste) over wifi ssh into iTunes_Control on the device

but gtkpod terminology is not making sense to me, it just kept failing when i tried to create structure locally???? can someone who understands gtkpod terminology try this??

---

### Post by Flash858 on 2010-10-22
Anyone made any progress on this?

Just checking...

---

### Post by jgordon510 on 2010-10-24
From a relevant ticket at libiphone:
[http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected](http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected)

[INDENT]kerdosa updated this ticket at October 24th, 2010 @ 05:28 AM

This is a very simple problem. Ipod touch 4g has idProduct 0x129e. Current usbmuxd has max idProduct 0x129a. It means usbmuxd will ignore any ixxx device with idProduct 0x129a or higher. Just change this to 0x129f, then re-compile usbmuxd. Everything is working OK.

Modify two places:
1. In daemon/usb.h, change #define PID_RANGE_MAX 0x129a  to #define PID_RANGE_MAX 0x129f. Recompile usbmuxd with cmake, install it.
2. Modify udev rules to recongize ipod touch 4g. In /lib/udev/rules.d/85-usbmuxd.rules, change ATTR{idProduct}=="129[0-9a]" to ATTR{idProduct}=="129[0-9ae]". Restart udev by "sudo restart udev".

Just plug in ipod touch 4g, enjoy it![/INDENT]

You can get the usbmuxd package here:
[http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.5.tar.bz2](http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.5.tar.bz2)

You need cmake and libusb-dev

---

### Post by Fluffgar on 2010-10-24
*face palm* 

I got this error: 
```
***username***@***username***-desktop:~$ cd build
***username***@***username***-desktop:~/build$ cmake '/home/***username***/build/usbmuxd-1.0.5' 
-- Configuring usbmuxd v1.0.5
-- Found PLIST 
-- Will build usbmuxd: YES
-- libusbmuxd will be built with protocol version 1 support
-- checking for module 'libusb-1.0>=1.0.3'
--   package 'libusb-1.0>=1.0.3' not found
USB_INCLUDE_DIR=USB_INCLUDE_DIR-NOTFOUND
USB_LIBRARY=USB_LIBRARY-NOTFOUND
CMake Error at Modules/LibFindMacros.cmake:74 (message):
  Required library USB NOT FOUND.

  Install the library (dev version) and try again.  If the library is already
  installed, use ccmake to set the missing variables manually.
Call Stack (most recent call first):
  Modules/FindUSB.cmake:40 (libfind_process)
  daemon/CMakeLists.txt:1 (find_package)


-- Configuring incomplete, errors occurred!
***username***@***username***-desktop:~/build$ 
 
```Searched Synaptic for libusb. Noticed that libusb-1.0-0-dev wasn't installed. Now I've got the install working just got to check if my ipod is detected. 

*crosses fingers*

---

### Post by tcrapper on 2010-10-24
> **jgordon510 said:**
> From a relevant ticket at libiphone:
[http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected](http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected)

[INDENT]kerdosa updated this ticket at October 24th, 2010 @ 05:28 AM

This is a very simple problem. Ipod touch 4g has idProduct 0x129e. Current usbmuxd has max idProduct 0x129a. It means usbmuxd will ignore any ixxx device with idProduct 0x129a or higher. Just change this to 0x129f, then re-compile usbmuxd. Everything is working OK.

Modify two places:
1. In daemon/usb.h, change #define PID_RANGE_MAX 0x129a  to #define PID_RANGE_MAX 0x129f. Recompile usbmuxd with cmake, install it.
2. Modify udev rules to recongize ipod touch 4g. In /lib/udev/rules.d/85-usbmuxd.rules, change ATTR{idProduct}=="129[0-9a]" to ATTR{idProduct}=="129[0-9ae]". Restart udev by "sudo restart udev".

Just plug in ipod touch 4g, enjoy it![/INDENT]

You can get the usbmuxd package here:
[http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.5.tar.bz2](http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.5.tar.bz2)

You need cmake and libusb-dev

Doing that lets you see/copy music to iPod but the music doesn't show up on iPod under music. Tried gtkpod, rhythmbox, and banshee.

---

### Post by seadao on 2010-10-25
try renaming ipod_control to itunes_control,

edit: opps it's just a sym link, i'm gonna give this usbmuxd trick a try

---

### Post by tcrapper on 2010-10-25
The git version has it fixed, so you don't have to edit the old version if you don't want to.

git clone git://git.marcansoft.com/usbmuxd.git 
cd usbmuxd
mkdir build
cd build
cmake ..
make
sudo make install 

you can use checkinstall instead of make install if you want to.

---

### Post by Fluffgar on 2010-10-25
No luck so far :( 
```
***username***@***username***-desktop:~$ sudo ifuse mount /media/iPod
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.
***username***@***username***-desktop:~$ 
```

---

### Post by tcrapper on 2010-10-25
> **Fluffgar said:**
> No luck so far :( 
```
***username***@***username***-desktop:~$ sudo ifuse mount /media/iPod
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.
***username***@***username***-desktop:~$ 
```

you might need to restart udev.

sudo restart udev

also try unplugging iPod and replugging it in.

---

### Post by maxvaillancourt on 2010-10-25
> **tcrapper said:**
> The git version has it fixed, so you don't have to edit the old version if you don't want to.

git clone git://git.marcansoft.com/usbmuxd.git 
cd usbmuxd
mkdir build
cd build
cmake ..
make
sudo make install 

you can use checkinstall instead of make install if you want to.

My iPod finally shows up in Rhythmbox! I can copy files onto it, but they don't show up in Music.app. Just like Fluffgar, I had to install "libusb-1.0-0-dev" for my iPod to appear.

Still, no sync.

---

### Post by Fluffgar on 2010-10-26
Okay. I can see the iPod in Rhythmbox after: 
                               ```
sudo apt-get install git
git clone git://git.marcansoft.com/usbmuxd.git 
cd usbmuxd
mkdir build
cd build
cmake ..
make
sudo make install
sudo restart udev
```Will give updates if discover further issues.

---

### Post by maxvaillancourt on 2010-10-26
Since Ubuntu and Rhythmbox recognize my iPod, I can't seem to open Mail.app on my iPod to fetch Gmail (Exchange). It always crashes a few seconds after I launch it. 

I tried respringing, turning it off and on, then hard rebooting, but nothing seems to do the trick. Does anyone experience the same issue after a "sync"? I think I have a broken Mail.app.

EDIT: Nevermind, problem solved. iPhone sync problem with Gmail. Just deleted my Exchange account from the iPod and created the same thing again.
EDIT 2: Finally, it was not a Gmail sync problem. Jailbreak app "Notified Pro" was causing the problem. Just uninstalled and everything works perfectly.

---

### Post by seadao on 2010-10-28
confirmation!! usbmuxd hack works, also the git version works!!

successful sync with rhythmbox and playback with native music app!!

NOTE:jailbroken, i also changed the DB version to 2 in lockdown YEEEE :)

---

### Post by nicocarbone on 2010-10-28
> **seadao said:**
> confirmation!! usbmuxd hack works, also the git version works!!

successful sync with rhythmbox and playback with native music app!!

NOTE:jailbroken, i also changed the DB version to 2 in lockdown YEEEE :)

What did you do to make the iPod sync successfully with Rhythmbox?

I can make the iPod visible to Ubuntu using the git version of usbmuxd, and even see the music inside the device, but I can't sync with Rhythmbox or Banshee. 

Investigating in the libimobile website ([http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)) I concluded that it was a limitation of the current version of the library, but if you could sync, I am wrong.

My device is not jailbroken, may this be the problem? What do you mean by "change DB version to 2 in lockdown"?

---

### Post by maxvaillancourt on 2010-10-28
> **seadao said:**
> confirmation!! usbmuxd hack works, also the git version works!!

successful sync with rhythmbox and playback with native music app!!

NOTE:jailbroken, i also changed the DB version to 2 in lockdown YEEEE :)

Does not work for me. Here's what I have done, from the very beginning.

[LIST=1]
[*]I installed the required packages listed on libimobiledevice's website.
[*]I ran all the commands in a Terminal to download the new git version of usbmuxd (commands by tcrapper)
[*]I changed the "DBVersion" key value from "5" to "2".
[/LIST]

To change the DBVersion key value, take a look at [this]("https://marcansoft.com/blog/2009/01/using-amarok-and-other-itunesdb-compatible-software-with-the-iphone-2x/").

I then tried copying a couple of songs on the iPod. It did not work. Why? Did I miss out on something?

Thanks,

Max

EDIT: Oh and also, the behavior of my iPod vs Rhythmbox is EXACTLY the same as nicocarbone, but my iPod is jailbroken.

---

### Post by pYrO1v1aniac on 2010-10-28
> **seadao said:**
> try renaming ipod_control to itunes_control,

edit: opps it's just a sym link, i'm gonna give this usbmuxd trick a try

Can you please explain where this renaming occurs? Since you got it to work I conclude this is how it's done.

---

### Post by seadao on 2010-10-28
OK!! here is a detailed steps:
1: jailbreak your device install ifile from cydia
2: with ifile change the DB version to 2 like in the wiki [https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower](https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower)

3:with ifile find you(/var/mobile/media) itunes_control, and delete it along with all the sym links ex: ipod_control .... if they exist (note an empty itunes_control will be created by firmware, it's i good idea to reboot the device after this)

4: use itunes all in windows (i used virtual box NOT OSE, you need usb support)
upload 1 mp3 file to the ipod, this will create the new DB

5: install libimobiledevice from ppa:pmcenery/ppa

6: (UPDATE!!!!) usbmuxd is updated(1.0.6) in ppa:pmcenery/ppa so it will work with ipod touch 4g use this one!!!!!!!

7: reboot, ipod will mount and ask if you want to start a music app

banshee daily build works as well as stock rhythmbox ENJOY!!


NOTE THIS IS WITH UNUNTU 10.10

---

### Post by maxvaillancourt on 2010-10-28
> **seadao said:**
> OK!! here is a detailed steps:
1: jailbreak your device install ifile from cydia
2: with ifile change the DB version to 2 like in the wiki [https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower](https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower)

3:with ifile find you(/var/mobile/media) itunes_control, and delete it along with all the sym links ex: ipod_control .... if they exist (note an empty itunes_control will be created by firmware, it's i good idea to reboot the device after this)

4: use itunes all in windows (i used virtual box NOT OSE, you need usb support)
upload 1 mp3 file to the ipod, this will create the new DB

5: install libimobiledevice from ppa:pmcenery/ppa

6: use make install(NOT CHECKINSTALL cmake in not debian rules) to compile usbmuxd from git

7: reboot, ipod will mount and ask if you want to start a music app

banshee daily build works as well as stock rhythmbox ENJOY!!


NOTE THIS IS WITH UNUNTU 10.10

Now, YOU, **seadao**, are GOD to me! THANK YOU VERY MUCH FOR THIS! I LOVE CAPS LOCK! :D

By the way, can I post your instructions on my blog? 

Thanks, Max.

EDIT: The OP might want to change the thread title prefix to _***SOLVED***_.
EDIT 2: Not working. :S When I tap a song on my iPod, it doesn't play and skips through all of them before going to the last one. None of them are playing. I'm using Rhythmbox.
EDIT 3: Works in Banshee, but not in Rhythmbox. Gotta adopt Banshee! ;) Now you can change the title to "***_Solved_***", for real.

---

### Post by seadao on 2010-10-28
YES please post this everywhere!!!!! hope this get pushed to the repos ASAP
try daily build of banshee, it's proly cuz you need the new libgpod

---

### Post by pYrO1v1aniac on 2010-10-28
> **seadao said:**
> YES please post this everywhere!!!!! hope this get pushed to the repos ASAP
try daily build of banshee, it's proly cuz you need the new libgpod


Fantastic! Thanks so much. I'll try it as soon as I'm back home with a windows box. What part would you push to repos though? There's no new files, per say (except usbmuxd), but a great workaround.

---

### Post by seadao on 2010-10-28
thats what i ment, usbmuxd and libgpod, make installing into debian messes up apt for future updates

---

### Post by igorbelchior on 2010-11-01
What should i do to got this working on my ipod not jailbroken? I've compiled usbmuxd from git and now banshee see my device, says its synchronizing, but when it finish, i got less space available at my ipod and no music at all...

---

### Post by seadao on 2010-11-01
> **igorbelchior said:**
> What should i do to got this working on my ipod not jailbroken? I've compiled usbmuxd from git and now banshee see my device, says its synchronizing, but when it finish, i got less space available at my ipod and no music at all...

??????? you just answered your own question

please read page 5 of this thread, i have posted instructions use the new ipod touch with ubuntu, follow my instruction in order from 1 to 7

---

### Post by igorbelchior on 2010-11-01
> **seadao said:**
> ??????? you just answered your own question

Did you read what i wrote? My sync isn't work at all. Banshee recognizes my ipod, send some kind of file to it, but i have no music. How i answered my question? I wanna know how to put this working properly, with correct sync...

---

### Post by maxvaillancourt on 2010-11-02
> **igorbelchior said:**
> Did you read what i wrote? My sync isn't work at all. Banshee recognizes my ipod, send some kind of file to it, but i have no music. How i answered my question? I wanna know how to put this working properly, with correct sync...

For now, you won't be able to sync it properly until "libimobiledevice" updates to support the iPod touch 4G. However, you can jailbreak and install SSH to edit the "DBVersion" value in the "Lockdown" folder. 

[i-FunBox]("http://www.i-funbox.com/"), [iPhoneBrowser]("http://code.google.com/p/iphonebrowser/") and [DiskAid]("http://www.digidna.net/products/diskaid") allow you to navigate some of your files/folders on your iPod through USB, but you can't access the root folder (/).

In this case, since the "DBVersion" value is located in "Checkpoint.xml" which is in "/System/Library/Lockdown/", you won't be able to access it and edit the value.

**Jailbreaking is the only option for now.** Believe me, you should. ;)

---

### Post by igorbelchior on 2010-11-02
I know i should, the problem is that this is my first ipod, i live in Brazil and bought at usa. If i do something wrong i have no guarantee and i'll need to pay for a fix. I'll wait 'til libimobiledevice gets an update

---

### Post by maxvaillancourt on 2010-11-02
> **igorbelchior said:**
> I know i should, the problem is that this is my first ipod, i live in Brazil and bought at usa. If i do something wrong i have no guarantee and i'll need to pay for a fix. I'll 'til libimobiledevice gets an update

Don't worry. A very poor number of people got their iPods bricked by jailbreaking it. People bricking their iPods are complete newbies that didn't ask for help, trying to do everything by their own.

However, sometimes, you must ask for help. That's why there are lots of forums available for you to ask help, just like you're doing right now.

***Jailbreak your iPod.*** If something wrong happens or you don't understand something, just tell us. We'll try to help you as quickly as possible. ;)

In all, I have jailbroken seven iPods/iPhones for friends and family. Everytime, it worked perfectly. No brick, no problem.

Tip: Even though [greenpois0n]("http://www.greenpois0n.com/") has a Linux version, you might want to use [limera1n]("http://limera1n.com/"). IMHO, it's better. However, you need a Windows machine or a Mac. :)

---

### Post by pYrO1v1aniac on 2010-11-06
I can confirm Seadao's hack works, and my iOS4.1 running iPod touch is now syncing with rhythmbox, banshee, etc, on 2 different Ubuntu installs (10.04)

---

### Post by earthhere on 2010-11-08
> **seadao said:**
> OK!! here is a detailed steps:
1: jailbreak your device install ifile from cydia
2: with ifile change the DB version to 2 like in the wiki [https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower](https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower)

3:with ifile find you(/var/mobile/media) itunes_control, and delete it along with all the sym links ex: ipod_control .... if they exist (note an empty itunes_control will be created by firmware, it's i good idea to reboot the device after this)

4: use itunes all in windows (i used virtual box NOT OSE, you need usb support)
upload 1 mp3 file to the ipod, this will create the new DB

5: install libimobiledevice from ppa:pmcenery/ppa

6: use make install(NOT CHECKINSTALL cmake in not debian rules) to compile usbmuxd from git

7: reboot, ipod will mount and ask if you want to start a music app

banshee daily build works as well as stock rhythmbox ENJOY!!


NOTE THIS IS WITH UNUNTU 10.10

  I also confirm seadao's method totally works. 

  Just to add, I jailbroke my iphone 3gs, ios 4.1 with redsn0w. It gave me the access to root. I installed openssh on my iphone via cydia, as a result I can access to root on nautilus from my ubuntu box. This means you don't need ifile or any other program to edit those files in iphone/itouch. 
  Also for me, Banshee didn't even show iphone connected, while rhythmbox showed it. Rhythmbox gave an error when I attempted to copy a song into iphone. I was sshed into the iphone at that time, so I disconnected. I exited rhythmbox, and ran it again; retried; it worked flawlessly. Thank you a lot seadao!!

 Cheers!

ps. I use ubuntu 10.04 x64.

---

### Post by igorbelchior on 2010-11-12
> **maxvaillancourt said:**
> Don't worry. A very poor number of people got their iPods bricked by jailbreaking it. People bricking their iPods are complete newbies that didn't ask for help, trying to do everything by their own.

However, sometimes, you must ask for help. That's why there are lots of forums available for you to ask help, just like you're doing right now.

***Jailbreak your iPod.*** If something wrong happens or you don't understand something, just tell us. We'll try to help you as quickly as possible. ;)

In all, I have jailbroken seven iPods/iPhones for friends and family. Everytime, it worked perfectly. No brick, no problem.

Tip: Even though [greenpois0n]("http://www.greenpois0n.com/") has a Linux version, you might want to use [limera1n]("http://limera1n.com/"). IMHO, it's better. However, you need a Windows machine or a Mac. :)

I know this is not the right place, but i'm using a windows computer right now. What the main diferences between jailbreak and not jailbreak. I need to know this before try and put the hack of this thread to work.

---

### Post by maxvaillancourt on 2010-11-12
> **igorbelchior said:**
> I know this is not the right place, but i'm using a windows computer right now. What the main diferences between jailbreak and not jailbreak. I need to know this before try and put the hack of this thread to work.

When you jailbreak your iPod, you can install and use paid App Store apps _for free_. Also, you can [customize your iPod with themes, fonts, colors, *everything*]("http://www.google.ca/images?client=ubuntu&channel=cs&q=winterboard&um=1&ie=UTF-8&source=og&sa=N&hl=fr&tab=wi&biw=1366&bih=652"). Plus, you have access to [Cydia, the other app store]("http://en.wikipedia.org/wiki/Cydia_(application)"), in which you can download **ANYTHING**. There are millions and millions of packages in there. From tweaks to wallpapers to games, Cydia is your one-stop destination for all your jailbreak needs.

*that last sentence was like the end of a commercial :P

---

### Post by igorbelchior on 2010-11-13
Thank you. I've jailbroke my device and now i can sync with Rhythmbox. Now i'm learning how to use cydia and stuff...
The hack works flawlessly.

---

### Post by maxvaillancourt on 2010-11-13
> **igorbelchior said:**
> Thank you. I've jailbroke my device and now i can sync with Rhythmbox. Now i'm learning how to use cydia and stuff...
The hack works flawlessly.

You're very welcome! ;)

---

### Post by francois.e on 2010-11-13
Very interested by seadao method. I have a ipod touch 4g with 4.1 ver software.

However, I am not so much accustomed with some of the cli manoeuvers: 

I am simply stuck at first step:1: jailbreaking the device.

1) downloaded greenpois0n linux package for ipod touch ver 4.1 :
[http://www.greenpois0n.com/](http://www.greenpois0n.com/)

2) moved the bz2 file and untar it:
root@max:/usr/share/doc/usbmuxd/build# mv /tmp/gp_lin32_rc4_2.tar.bz2 /usr/local
root@max:/usr/share/doc/usbmuxd/build# cd /usr/local
root@max:/usr/local# tar xvjf gp_lin32_rc4_2.tar.bz2
greenpois0n_x86

3) Permission seemed ok to me (I might be wrong), so I did try to execute it, without compiling anything:
max@max:/usr/local$ ls
bin  games                   greenpois0n_x86  lib  sbin   src
etc  gp_lin32_rc4_2.tar.bz2  include          man  share
max@max:/usr/local$ sudo greenpois0n_x86
[sudo] password for max: 
sudo: greenpois0n_x86: command not found
max@max:/usr/local$ ./greenpois0n_x86
./greenpois0n_x86: error while loading shared libraries: libusb-1.0.so.0: cannot open shared object file: No such file or directory



Finallly, I went for the windows version of greenpoison. I had to try  the program three time, with restoring the system each time before it  worked. It gave me the time to look for another jailbreaking solution,  that is limera1n:
[http://www.iphonehacks.com/2010/10/limera1n-out-of-beta-includes-bug-fixes-and-improvements.html](http://www.iphonehacks.com/2010/10/limera1n-out-of-beta-includes-bug-fixes-and-improvements.html)

If someone test it let me know.

---

### Post by francois.e on 2010-11-14
Now I am on step 2: with ifile change the DB version to 2 like in the wiki [https://help.ubuntu.com/community/Po...4%20or%20lower]("https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower")

This instruction is not clear for me. Which part of the text are you alluding to into the wiki. I am on ubuntu 10.10.

I am able to move thru files on the ipod. I can get into the Checkpoint.xml file, but I do not see what could be what you call the DBVersion to 2. 

Do I change:
plist version="1.0" to "2.0"

Is it the only occurence to be changed?

However, trying to reach the same files thru the computer browser does not work.

Thanks for you time.

Do I have to modify the dbversion from the computer's browser or from the ipod touch? I am not able to change the name of Checkpoint.xml file to make a backup. How do I do that from the ipod?

---

### Post by nikitajy on 2010-11-14
> **jgordon510 said:**
> From a relevant ticket at libiphone:
[http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected](http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected)

[INDENT]kerdosa updated this ticket at October 24th, 2010 @ 05:28 AM

This is a very simple problem. Ipod touch 4g has idProduct 0x129e. Current usbmuxd has max idProduct 0x129a. It means usbmuxd will ignore any ixxx device with idProduct 0x129a or higher. Just change this to 0x129f, then re-compile usbmuxd. Everything is working OK.

Modify two places:
1. In daemon/usb.h, change #define PID_RANGE_MAX 0x129a  to #define PID_RANGE_MAX 0x129f. Recompile usbmuxd with cmake, install it.
2. Modify udev rules to recongize ipod touch 4g. In /lib/udev/rules.d/85-usbmuxd.rules, change ATTR{idProduct}=="129[0-9a]" to ATTR{idProduct}=="129[0-9ae]". Restart udev by "sudo restart udev".

Just plug in ipod touch 4g, enjoy it![/INDENT]

You can get the usbmuxd package here:
[http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.5.tar.bz2](http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.5.tar.bz2)

You need cmake and libusb-dev

I did that (I can't use the git b/c I'm firewalled) but the iPod is still only recognized as a camera. I got the iPod recognized as a media device on another computer using the git, so the iPod itself is ok. Could I have forgotten something? :confused:

---

### Post by Cogizio on 2010-11-14
I'm getting an error:
> Error while getting peer-to-peer dbus connection: The name :1.974 was not provided by any .service files
That's in Rythmbox.  I can see my music, and I can play music off the device.  I can't add music to the device, I get that error above.
Good work though!

---

### Post by seadao on 2010-11-14
> **francois.e said:**
> Now I am on step 2: with ifile change the DB version to 2 like in the wiki [https://help.ubuntu.com/community/Po...4%20or%20lower]("https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower")

This instruction is not clear for me. Which part of the text are you alluding to into the wiki. I am on ubuntu 10.10.

I am able to move thru files on the ipod. I can get into the Checkpoint.xml file, but I do not see what could be what you call the DBVersion to 2. 

Do I change:
plist version="1.0" to "2.0"

Is it the only occurence to be changed?

However, trying to reach the same files thru the computer browser does not work.

Thanks for you time.

Do I have to modify the dbversion from the computer's browser or from the ipod touch? I am not able to change the name of Checkpoint.xml file to make a backup. How do I do that from the ipod?

look carefully in Checkpoint.xml you will see a line
<key>DBVersion</key>
<integer>4</integer>

change it to

<key>DBVersion</key>
<integer>2</integer>

better instructions:
[https://wiki.archlinux.org/index.php/IPod#Unobfuscating_the_Database](https://wiki.archlinux.org/index.php/IPod#Unobfuscating_the_Database)

---

### Post by seadao on 2010-11-14
> **Cogizio said:**
> I'm getting an error:

That's in Rythmbox.  I can see my music, and I can play music off the device.  I can't add music to the device, I get that error above.
Good work though!

if you see the music on it in rhythmbox and it mount you are almost done,
try the banshee build from git and update your libgpod to latest,

also note that this instructions only work in GNOME ubuntu, i'm working on LXDE and XFCE, i'm currently unable to get this working in LXDE and XFCE for some reason, i suspect that mounting works different in PCman and thunar, and messing with fuse groups didn't fix it for me

---

### Post by seadao on 2010-11-14
> **nikitajy said:**
> I did that (I can't use the git b/c I'm firewalled) but the iPod is still only recognized as a camera. I got the iPod recognized as a media device on another computer using the git, so the iPod itself is ok. Could I have forgotten something? :confused:

if you downloaded the git copy on another use a usb drive to transfer it to the other computer and compile it this will be easier i think than looking for hacking typos :-) imo

---

### Post by Cogizio on 2010-11-14
This was weird, turns out something odd happened.  Suddenly I *can *sync with Rythmbox.  Infinitely awesome!  Thank you so much!

---

### Post by francois.e on 2010-11-14
Very good seadao. Many thanks. We are now at step 5. Installing libimobiledevice from [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/). Trying directly with apt-get, I get:

max@max:~$ sudo apt-get install libimobiledevice
[sudo] password for max: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet libimobiledevice
max@max:~$ 

However, this is not from [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/).

Is there anyway with wget and then apt-get install to install the package?

Editing:
Finally, it seems that the installation of libimobiledevice had been done already according to the manipulations that we accidentally accomplished this week-end. It is present in the logithèque (we use the french version of ubuntu, I imagine this is the kind of synaptic for ubuntu).

---

### Post by seadao on 2010-11-14
> **francois.e said:**
> Very good seadao. Many thanks. We are now at step 5. Installing libimobiledevice from [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/). Trying directly with apt-get, I get:

max@max:~$ sudo apt-get install libimobiledevice
[sudo] password for max: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet libimobiledevice
max@max:~$ 

However, this is not from [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/maverick/).

Is there anyway with wget and then apt-get install to install the package?

Your patience is more than appreciated.

open synaptic package manager
copy and paste ```
ppa:pmcenery/ppa
``` into sources
thats it!! refresh and install libimobiledevice
for more info [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

EDIT:
you don't need to move the source into root to compile it, just unpack it on the desktop(or Downloads folder is default) and terminal to the folder and compile it in user space, then use sudo make install,

ubuntu 10.10 downloads to /home/user/Download or Desktop
cd Downloads/usb*
mkdir build
cd build
cmake ..
make
sudo make install

thats it

---

### Post by Cogizio on 2010-11-14
> **francois.e said:**
> 1) I picked up usbmuxd-1.0.6.tar.bz2 from [http://marcansoft.com/blog/iphonelinux/usbmuxd/](http://marcansoft.com/blog/iphonelinux/usbmuxd/)

2) Tried to unpack in /usr/local with:
max@max:/tmp$ chmod 0777 usbmuxd-1.0.6.tar.bz2
max@max:/tmp$ mv /tmp/usbmuxd-1.0.6.tar.bz2 /usr/local
mv: ne peut déplacer `/tmp/usbmuxd-1.0.6.tar.bz2' vers `/usr/local/usbmuxd-1.0.6.tar.bz2': Permission non accordée
max@max:/tmp$ su
Mot de passe : 
root@max:/tmp# chmod 0777 usbmuxd-1.0.6.tar.bz2
root@max:/tmp# exit
exit
max@max:/tmp$ mv /tmp/usbmuxd-1.0.6.tar.bz2 /usr/local
mv: ne peut déplacer `/tmp/usbmuxd-1.0.6.tar.bz2' vers `/usr/local/usbmuxd-1.0.6.tar.bz2': Permission non accordée
max@max:/tmp$ su
Mot de passe : 
root@max:/tmp# mv /tmp/usbmuxd-1.0.6.tar.bz2 /usr/local
root@max:/tmp# cd /usr/local
root@max:/usr/local# ls
bin  games                   greenpois0n_x86  lib  sbin   src
etc  gp_lin32_rc4_2.tar.bz2  include          man  share  usbmuxd-1.0.6.tar.bz2
root@max:/usr/local# exit
exit
max@max:/tmp$ sudo tar xvjf usbmuxd-1.0.6.tar.bz2
[sudo] password for max: 
tar (child): usbmuxd-1.0.6.tar.bz2 : la fonction open a échoué: Aucun fichier ou dossier de ce type
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
max@max:/tmp$ su
Mot de passe : 
root@max:/tmp# tar xvjf usbmuxd-1.0.6.tar.bz2
tar (child): usbmuxd-1.0.6.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
root@max:/tmp# 
Your patience is more than appreciated.

I'll give you a quote from a guide I just wrote for my blog (to be published in a few hours):
[QUOTE=How to quickly sync an iPod touch 4th generation to Rythmbox on Ubuntu]
**5.  Installing USBMUXD from source.**
 **5a. **Install git.
 [[IMG]http://cogizio.org/wp-content/uploads/2010/11/Selection_011-300x31.png[/IMG]]("http://cogizio.org/wp-content/uploads/2010/11/Selection_011.png")

 **5b. **Run these comands:
 git clone git://git.marcansoft.com/usbmuxd.git
cd usbmuxd
mkdir build
cd build
cmake ..
make
sudo make install
 Install any package it requires--you'll probably want to ask here if you need a package.  Something'll probably go wrong.
[/QUOTE]

Good luck!  And once again, thanks seadao for all the help!

---

### Post by francois.e on 2010-11-14
However, we still have to work hard, as:

1) I picked up usbmuxd-1.0.6.tar.bz2 from [http://marcansoft.com/blog/iphonelinux/usbmuxd/](http://marcansoft.com/blog/iphonelinux/usbmuxd/)

2) Tried to unpack in /usr/local with:
max@max:/tmp$ su
Mot de passe : 
root@max:/tmp# chmod 0777 usbmuxd-1.0.6.tar.bz2
root@max:/tmp# mv /tmp/usbmuxd-1.0.6.tar.bz2 /usr/local
root@max:/tmp# cd /usr/local
root@max:/usr/local# ls
bin  games                   greenpois0n_x86  lib  sbin   src
etc  gp_lin32_rc4_2.tar.bz2  include          man  share  usbmuxd-1.0.6.tar.bz2
root@max:/usr/local# tar xvjf usbmuxd-1.0.6.tar.bz2
usbmuxd-1.0.6/
usbmuxd-1.0.6/AUTHORS
...

...
usbmuxd-1.0.6/udev/CMakeLists.txt
usbmuxd-1.0.6/version.tag
root@max:/usr/local# make install
make: *** No rule to make target `install'.  Stop.
root@max:/usr/local# 

Should I do that under root or under normal user? It does not seem to work under normal user.


Your patience is more than appreciated.



Edit: From here I then try Cogizio procedure to get to the following post result.

---

### Post by francois.e on 2010-11-14
Originally Posted by **How to quickly sync an iPod touch 4th generation to Rythmbox on Ubuntu**                                      
                 **5.  Installing USBMUXD from source.**
 **5a. **Install git.
 [[IMG]http://cogizio.org/wp-content/uploads/2010/11/Selection_011-300x31.png[/IMG]]("http://cogizio.org/wp-content/uploads/2010/11/Selection_011.png")

 **5b. **Run these comands:
 git clone git://git.marcansoft.com/usbmuxd.git
cd usbmuxd
mkdir build
cd build


Everything works until I try:

max@max:/tmp/usbmuxd/build$ cmake ..
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring usbmuxd v1.0.6
-- Found PLIST 
-- Will build usbmuxd: YES
-- libusbmuxd will be built with protocol version 1 support
-- Found USB 
-- usbmuxd will be built with protocol version 1 support

* REMINDER
* Remember to add a user named 'usbmux' with USB access permissions
* for the udev hotplugging feature to work out of the box.

-- Configuring incomplete, errors occurred!
max@max:/tmp/usbmuxd/build$ sudo make install
make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.
max@max:/tmp/usbmuxd/build$

Edit: I just saw after that that seadoa, also made a proposition. I work tomorrow, so going to bed now. Thanks to both of you.

---

### Post by seadao on 2010-11-14
EDIT form your post i also see you don't have a C compiler installed so DO THIS FIRST
sudo apt-get install build-essentials

> **francois.e said:**
> Everything works until I try:

max@max:/tmp/usbmuxd/build$ cmake ..
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring usbmuxd v1.0.6
-- Found PLIST 
-- Will build usbmuxd: YES
-- libusbmuxd will be built with protocol version 1 support
-- Found USB 
-- usbmuxd will be built with protocol version 1 support

* REMINDER
* Remember to add a user named 'usbmux' with USB access permissions
* for the udev hotplugging feature to work out of the box.

-- Configuring incomplete, errors occurred!
max@max:/tmp/usbmuxd/build$ sudo make install
make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.
max@max:/tmp/usbmuxd/build$

it's i assume you didn't hack usbmuxd, so you should be using the git version instead since you don't need to hack anymore
1:open new terminal

2:install git
sudo apt-get install git

3:checkout the git copy
git clone git://git.marcansoft.com/usbmuxd.git

4:compile (you need libusb-dev and other deps i don't remember, cmake will tell you what is missing)
cd usb*
mkdir build
cmake ..
make
sudo make install

---

### Post by Cogizio on 2010-11-14
This isn't very good.  Seadao, when I go onto the iPod touch I can see all my music right there in the Music app, but when I actually tap on a piece of music it goes to the playing music screen, and then instantly back to the music page... ARGH!
EDIT
YES!!  IT WORKS!  IT WORKS!  IT! WORKS!  !THIS IS AMAZING!! FREEDOM!  AT LONG LAST FREEDOM! I can not express my gratitude Seadao, even if it is a case of using dev-level apps.  :P  

If you're experiencing this problem folks, install Banshee and use that instead.  It'll work!

---

### Post by Cogizio on 2010-11-15
If anybody cares to read my step-by-step guide (based on seadao's tutorial and my experience):
[http://cogizio.org/operating-systems/ubuntu/3089](http://cogizio.org/operating-systems/ubuntu/3089)

---

### Post by francois.e on 2010-11-15
@Seadoa:

Once more all my gratitude.  And thanks to cognizio for the detailed procedure. Just a little syntax error in your proposition  build-essential and not build-*essentials*  as in:

max@max:~$ sudo apt-get install build-essential
Lecture des listes de paquets... Fait
...


However in:

max@max:~/usbmuxd/build$ cmake ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
...

...
* REMINDER
* Remember to add a user named 'usbmux' with USB access permissions
* for the udev hotplugging feature to work out of the box.

-- Configuring done
-- Generating done
-- Build files have been written to: /home/max/usbmuxd/build
max@max:~/usbmuxd/build$ 

It seems that the REMINDER is not important, I imagine.

Rebooting now. The laptop recognizes the ipod touch, we are in Rhythm and box. 

However, trying to synchronize fille. The error message is:

Impossible de transférer les pistes
Aucune des pistes à transférer n'est dans un format pris en charge par le périphérique cible et il n'y a pas de codeur disponible pour convertir dans les bons formats

Translated:
No soundtrac transfer.
The format is not in a format taken in charge by the peripheral, missing appropriate codecs.

---

### Post by maxvaillancourt on 2010-11-15
> **francois.e said:**
> Now I am on step 2: with ifile change the DB version to 2 like in the wiki [https://help.ubuntu.com/community/Po...4%20or%20lower]("https://help.ubuntu.com/community/PortableDevices/iPhone#Setting%20up%20Ubuntu%209.04%20or%20lower")

This instruction is not clear for me. Which part of the text are you alluding to into the wiki. I am on ubuntu 10.10.

I am able to move thru files on the ipod. I can get into the Checkpoint.xml file, but I do not see what could be what you call the DBVersion to 2. 

Do I change:
plist version="1.0" to "2.0"

Is it the only occurence to be changed?

However, trying to reach the same files thru the computer browser does not work.

Thanks for you time.

Do I have to modify the dbversion from the computer's browser or from the ipod touch? I am not able to change the name of Checkpoint.xml file to make a backup. How do I do that from the ipod?

Do you speak French, François? Je viens du Québec, Canada. Je peux vous aider si vous voulez! Je suis présentement en train de rédiger un tutoriel étape-par-étape sur mon blog afin de même permettre aux utilisateurs un peu moins "tech-savvy" de s'y retrouver.

Maxime

---

### Post by seadao on 2010-11-16
> **francois.e said:**
> @Seadoa:

Once more all my gratitude.  And thanks to cognizio for the detailed procedure. Just a little syntax error in your proposition  build-essential and not build-*essentials*  as in:

max@max:~$ sudo apt-get install build-essential
Lecture des listes de paquets... Fait
...


However in:

max@max:~/usbmuxd/build$ cmake ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
...

...
* REMINDER
* Remember to add a user named 'usbmux' with USB access permissions
* for the udev hotplugging feature to work out of the box.

-- Configuring done
-- Generating done
-- Build files have been written to: /home/max/usbmuxd/build
max@max:~/usbmuxd/build$ 

It seems that the REMINDER is not important, I imagine.

Rebooting now. The laptop recognizes the ipod touch, we are in Rhythm and box. 

However, trying to synchronize fille. The error message is:

Impossible de transférer les pistes
Aucune des pistes à transférer n'est dans un format pris en charge par le périphérique cible et il n'y a pas de codeur disponible pour convertir dans les bons formats

Translated:
No soundtrac transfer.
The format is not in a format taken in charge by the peripheral, missing appropriate codecs.

it looks like you only ran cmake, and didn't run "make", and "sudo make install" cmake configures the build and makes sure you have all the dependences you still need to "make" this will compile the binary, then "sudo make install" this will install the binary into root system area
redo all the steps carefully


3:checkout the git copy
git clone git://git.marcansoft.com/usbmuxd.git

4:compile (you need libusb-dev and other deps i don't remember, cmake will tell you what is missing)
cd usb*
mkdir build
cmake ..
make
sudo make install

5:reboot

---

### Post by francois.e on 2010-11-16
@seadoa:

Finally, we have tried with the banshee music software, as suggested by Cogizio. The ipod did synchronize. And it is working fine now. At synchronisation there was some format file conversion going on.

I will look at rhytmbox, and try your suggestion. It would be great that it could work on that software too.

At first thought, I wonder why it works with Banshee only, but maybe a second reading of your last post will bring the light on my brain.

Cheers.:popcorn:

---

### Post by slcpunk on 2010-11-17
following these instructions, but not having any luck with the syncro.


[LIST]
[*]jailbreak?  check.
[*]change DBVersion to 2?  check.
[*]delete itunes_control?  check.
[*]attach to itunes and copy over a file?  check.  ( although - here - I had some trouble, itunes complained and wanted to restore or setup a new iphone.  I setup a new iphone, which from what i could tell was the only option to keep the JB.  The only odd thing was after I did that, it really gave me fits trying to copy over one song.  Finally i had to go into the 'sync music' screen and apply that - then it allowed me to copy over one song.
[*]install and compile packages ( git all that ) check.
[*]now, back in Ubuntu when I plug in the iphone, an icon is created on the desktop.  the properties ( and gnome ) show this to be mounted to afc://biglongstring
[*]If I open banshee ( current version from a ppa ), it sees the iphone, then dismounts the iphone and closes it.
[*]If i manually do "ifuse /media/iphone"  I can see the iphone in gtkpod, but syncing does not work.  I can also see the ipod in Banshee, but it doesn't show the one song that I copied over and if I copy something in banshee, it won't go.
[/LIST]
Thoughts?  What can I provide to help diagnose?  One other difference -- I used "checkinstall" to install usbmux .... seemed better in Ubuntu as it puts the package in the package manager, right?  But I see some strange notes about not using that ... could it be related?

One other thing - I ended up with libimobiledevice0 and libimobiledevice1 ... there is also the libimobiledevice-dev package.  Do I need to clean this up? ( if so, what should be final state? )

thanks

some version info:

libimobiledevice0 = version  0.9.7-1ubuntu1
libimobiledevice1 = version 1.0.3-1ubuntu1~lucid1

If I try to remove libimobiledevice0, this is what aptitude wants to do:
The following packages will be DOWNGRADED:
  libgpod-common libgpod4 
The following packages will be REMOVED:
  banshee{a} libgkeyfile1.0-cil{u} libgpod-dev{a} libgudev1.0-cil{u} libimobiledevice0 
  libmono-zeroconf1.0-cil{u} libtaglib2.0-cil{u} 

banshee version: 1.8.0-1ubuntu1~hyper1+lucid

libgpod4 version: 0.7.95-1~hyper1+lucid

---

### Post by slcpunk on 2010-11-17
update...

I removed libimobiledevice0 ( leaving libimobiledevice1) , as well as downgrading Banshee to the regular Ubuntu ( 10.04 ) version.

Now Banshee won't recognize the device any more after its auto mounted to the "afc://" location.

Now if I manually unmount the iphone after I plug it in, and then "ifuse /media/iPhone" from the command line, I can successfully transfer music and playlists via gtkpod.

However, I would prefer the full deal ... automatically mounted and usable in Banshee or Rhythmbox.  After mounting with ifuse, neither Banshee nor Rhythmbox see the phone as a music player.

thanks again in advance

---

### Post by seadao on 2010-11-17
> **slcpunk said:**
> update...

I removed libimobiledevice0 ( leaving libimobiledevice1) , as well as downgrading Banshee to the regular Ubuntu ( 10.04 ) version.

Now Banshee won't recognize the device any more after its auto mounted to the "afc://" location.

Now if I manually unmount the iphone after I plug it in, and then "ifuse /media/iPhone" from the command line, I can successfully transfer music and playlists via gtkpod.

However, I would prefer the full deal ... automatically mounted and usable in Banshee or Rhythmbox.  After mounting with ifuse, neither Banshee nor Rhythmbox see the phone as a music player.

thanks again in advance

please follow these steps from page 5 carefully, i suspect you didn't reboot the ipod after deleting itunes_control, if itunes restores your device you will lose the jailbreak and have to redo from step 1, don't lets itunes "fix" anything

also, i used ubuntu 10.10 so i think it has newer libs, but i don't really now, i think reinstalling newest rhythmbox and banshee might work, also try to add yourself to the fuse group, that sometimes is not on when you update fuse

---

### Post by Cogizio on 2010-11-19
Also, I did it as a restore to previous stuff rather than set up as new.

---

### Post by slcpunk on 2010-11-26
> **seadao said:**
> please follow these steps from page 5 carefully, i suspect you didn't reboot the ipod after deleting itunes_control, if itunes restores your device you will lose the jailbreak and have to redo from step 1, don't lets itunes "fix" anything

also, i used ubuntu 10.10 so i think it has newer libs, but i don't really now, i think reinstalling newest rhythmbox and banshee might work, also try to add yourself to the fuse group, that sometimes is not on when you update fuse

Thanks for the tips, but it turned out to be something else completely.  I had a .gvfs folder in my home directory.  I found another post with someone that had a similar problem - the test was to create a new user, plug in the iphone, and it all worked perfectly - that's how I knew it was a problem in my home folder.  Removing the .gvfs folder, then logging out and back in fixed Rhythmbox for me.

thanks again

---

### Post by Cogizio on 2010-11-26
Anybody want to try 4.2?

---

### Post by Cogizio on 2010-11-26
OK, I'm at least getting the error that I'm supposed to be getting:
"26.11.2010: iDevices with iOS 4.2.1 fail to establish a SSL connection.  Apparently, GNUTLS has a bug (we verified that it works when using  OpenSSL instead) which prevents libimobiledevice to do SSL communication  with an iDevice. We are debugging GNUTLS and if you like to help join  #libimobiledevice on freenode."
(from [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/))

---

### Post by Cogizio on 2010-11-28
I'm in the process of installing 1.0.4 which includes support for 4.2.1.  Jeez, I had no idea how many dependencies libimobiledevice!  I'm currently installing the dev version of Python, and I've already had to install ~7 programs from source.

---

### Post by Cogizio on 2010-11-28
So far so good!

Also--it's probably better just to download this random RPM I found ([here]("http://packman.links2linux.org/download/libimobiledevice/732562/libimobiledevice1-1.0.4-1.pm.8.1.i586.rpm")) and convert it with Alien (read up on how [here]("http://cogizio.org/operating-systems/cross-platform/2429"), my site FYI).  It works and it's a whole ton faster than making your own DEB file.

Good luck, I'm currently copying files onto my iPod.  EDIT: Just finished!  The iPod's still showing the "sync in progress" screen.  I'm cancelling it.  Opening the music app; it's "Cancelling Sync...".  I unplugged the cord now it's updating library.  The files show.  Now to test them!

UPDATE!:
EVERYTHING WORKS!  Yeah!

---

### Post by GeorgeJQ on 2010-11-30
So I've been following the advice in this thread, and everything was working perfectly up to today.  Yesterday, I did an update before shutting down my computer, and today when I plug in my iPod touch 4G nothing shows up.  Rhythmbox shows "Unknown Device" in the sidebar for a second, but it just disappears.  I'm not sure if it has anything to do with the updates... has anyone gotten this problem?

---

### Post by maxvaillancourt on 2010-11-30
> **GeorgeJQ said:**
> So I've been following the advice in this thread, and everything was working perfectly up to today.  Yesterday, I did an update before shutting down my computer, and today when I plug in my iPod touch 4G nothing shows up.  Rhythmbox shows "Unknown Device" in the sidebar for a second, but it just disappears.  I'm not sure if it has anything to do with the updates... has anyone gotten this problem?

Same for me!

---

### Post by Cogizio on 2010-12-01
I updated my Ubuntu computer today, but I'm not using that computer right now.  I'll check back to see if it's something to do with the updates.  

Also, try Banshee for your media player to see if that works.

---

### Post by slcpunk on 2010-12-01
iphone4 iOS 4.1 , ubuntu 10.04 

ran updates (libimobiledevice = 1.0.4 ), everything works as before.  ( I did not get a new version of usbmux from git ... not sure how to update that gracefully )

My setup still seems a bit different from the directions, ...rhythmbox works, but gtkpod doesn't work unless i manually mount iphone again with "ifuse /media/iPhone" ( and unmount with fusermount -u /media/iPhone )

Then it works too.

But basic auto mount ( afc://..... ) works with Rhythmbox, so I'm happy.  By right clicking and picking properties, and "sync" I was even able to add playlists ... which I've never been able to do before.  Sweet!

Wish I could move Photos off and not mess everything up.  Right now, have to copy then delete from iPhone directly.  ( tried in gtkpod, but no info on the Photos.  libimobiledevice shows not implemented yet...oh well )

installed idevicelistaller from git, and was able to install an app.  Pretty cool

---

### Post by Cogizio on 2010-12-01
> **slcpunk said:**
> iphone4 iOS 4.1 , ubuntu 10.04 
installed idevicelistaller from git, and was able to install an app.  Pretty cool
That sounds awesome! I totally have to get that app(lication on my computer).

---

### Post by Fluffgar on 2010-12-04
> **francois.e said:**
> Very interested by seadao method. I have a ipod touch 4g with 4.1 ver software.

However, I am not so much accustomed with some of the cli manoeuvers: 

I am simply stuck at first step:1: jailbreaking the device.

1) downloaded greenpois0n linux package for ipod touch ver 4.1 :
[http://www.greenpois0n.com/](http://www.greenpois0n.com/)

2) moved the bz2 file and untar it:
root@max:/usr/share/doc/usbmuxd/build# mv /tmp/gp_lin32_rc4_2.tar.bz2 /usr/local
root@max:/usr/share/doc/usbmuxd/build# cd /usr/local
root@max:/usr/local# tar xvjf gp_lin32_rc4_2.tar.bz2
greenpois0n_x86

3) Permission seemed ok to me (I might be wrong), so I did try to execute it, without compiling anything:
max@max:/usr/local$ ls
bin  games                   greenpois0n_x86  lib  sbin   src
etc  gp_lin32_rc4_2.tar.bz2  include          man  share
max@max:/usr/local$ sudo greenpois0n_x86
[sudo] password for max: 
sudo: greenpois0n_x86: command not found
max@max:/usr/local$ ./greenpois0n_x86
./greenpois0n_x86: error while loading shared libraries: libusb-1.0.so.0: cannot open shared object file: No such file or directory



Finallly, I went for the windows version of greenpoison. I had to try  the program three time, with restoring the system each time before it  worked. It gave me the time to look for another jailbreaking solution,  that is limera1n:
[http://www.iphonehacks.com/2010/10/limera1n-out-of-beta-includes-bug-fixes-and-improvements.html](http://www.iphonehacks.com/2010/10/limera1n-out-of-beta-includes-bug-fixes-and-improvements.html)

If someone test it let me know.

I have the same problem, "error while loading shared libraries: *libusb-1.0.so.0*: cannot open shared object file: No such file or directory". 

Tried making a link to *libusb-1.0.so.0.0.0* but no luck so far.

---

### Post by lucasmocellin on 2010-12-08
hi,

I followed the steps but I didn't still get it working properly.

I'm having the same issue as slcpunk described, it's working with gtkpod when I mount manually with "ifuse MOUNTPOINT". and it doesn't work with rhythmbox or banshee.

I tried to create a new user to see if there was the issue about .gvfs, but it doesn't "automount" never. but I can mount manually and also with the command "ideviceinfo" it shows information about my ipod touch 4g 4.1

does anyone have an idea how to solve that? with gtkpod I cannot put videos on my ipod. :(

I have the ipod jailbroken, libimobiledevice 1.04.

I don't understand exactly which library/program is used when, for example there is libimobiledevice, libgpod, and maybe some more.

any suggestion is welcome!

thanks in advance!

Lucas.

---

### Post by slcpunk on 2010-12-08
> **lucasmocellin said:**
> hi,

I followed the steps but I didn't still get it working properly.

I'm having the same issue as slcpunk described, it's working with gtkpod when I mount manually with "ifuse MOUNTPOINT". and it doesn't work with rhythmbox or banshee.



For what its worth, I did get it working with Rhythmbox.  I didn't do anything outside of the instructions in this thread, so you might just try starting all over again.  I was also able to point gtkpod to the .gvfs/iphone folder, and now I do not have to manually mount it any more.  

in rhythmbox, I can't just drag songs over to the ipod.  Although it appears to sync, when you unplug, the songs are not there.  HOWEVER, if I create a playlist, and then go to the properties of the iphone, and use the "sync" tab options to select the playlists I want, they will sync properly.  ( same with podcasts )  You might have some luck that way?

not sure if it matters, but you have a touch, and i have the phone...so I don't know if its all the same or not. (same OS version, so you would think pretty close )

---

### Post by lucasmocellin on 2010-12-08
> **slcpunk said:**
> For what its worth, I did get it working with Rhythmbox.  I didn't do anything outside of the instructions in this thread, so you might just try starting all over again.  I was also able to point gtkpod to the .gvfs/iphone folder, and now I do not have to manually mount it any more.  

in rhythmbox, I can't just drag songs over to the ipod.  Although it appears to sync, when you unplug, the songs are not there.  HOWEVER, if I create a playlist, and then go to the properties of the iphone, and use the "sync" tab options to select the playlists I want, they will sync properly.  ( same with podcasts )  You might have some luck that way?

not sure if it matters, but you have a touch, and i have the phone...so I don't know if its all the same or not. (same OS version, so you would think pretty close )




> **slcpunk said:**
> For what its worth, I did get it working with Rhythmbox.  I didn't do anything outside of the instructions in this thread, so you might just try starting all over again.  I was also able to point gtkpod to the .gvfs/iphone folder, and now I do not have to manually mount it any more.  

in rhythmbox, I can't just drag songs over to the ipod.  Although it appears to sync, when you unplug, the songs are not there.  HOWEVER, if I create a playlist, and then go to the properties of the iphone, and use the "sync" tab options to select the playlists I want, they will sync properly.  ( same with podcasts )  You might have some luck that way?

not sure if it matters, but you have a touch, and i have the phone...so I don't know if its all the same or not. (same OS version, so you would think pretty close )


ok, I will put step by step detalled:

1: jailbreak your device install ifile from cydia
done
2: with ifile change the DB version to 2 like in the wiki [https://help.ubuntu.com/community/Po...4%20or%20lower](https://help.ubuntu.com/community/Po...4%20or%20lower)
I used the OpenSSH, mounted with sshfs and edited the file:
/System/Library/Lockdown/Checkpoint.xml
the DBVersion para 2

3:with ifile find you(/var/mobile/media) itunes_control, and delete it along with all the sym links ex: ipod_control .... if they exist (note an empty itunes_control will be created by firmware, it's i good idea to reboot the device after this)

there is only iTunes_Control directory, erased that. After that I restarted the iPod Touch 4g 4.1

4: use itunes all in windows (i used virtual box NOT OSE, you need usb support)
upload 1 mp3 file to the ipod, this will create the new DB

here I have the same issue as posted before, itunes asks me to recover some backup o add as a new device, I added as a new device, cancelled the backup and the sync and just added one song. - it's too slow on my machine, virtualbox in a netbook. haha

5: install libimobiledevice from ppamcenery/ppa

this was already installed:
lucas@kktua:/media$ dpkg -l |grep libimobile
ii  libimobiledevice-utils                1.0.4-1ubuntu1~lucid1                           Library for communicating with iPhone and iP
ii  libimobiledevice0                     0.9.7-1ubuntu1                                  Library for communicating with the iPhone an
ii  libimobiledevice1                     1.0.4-1ubuntu1~lucid1                           Library for communicating with the iPhone an



6: use make install(NOT CHECKINSTALL cmake in not debian rules) to compile usbmuxd from git
compiled as shown in the README with make install:
lucas@kktua:~/Downloads/usbmuxd/build$ sudo make install
[ 30%] Built target libusbmuxd
[ 90%] Built target usbmuxd
[100%] Built target iproxy
Install the project...
-- Install configuration: ""
-- Up-to-date: /usr/local/lib/pkgconfig/libusbmuxd.pc
-- Up-to-date: /usr/local/lib/libusbmuxd.so.1.0.6-3-g02252a4
-- Up-to-date: /usr/local/lib/libusbmuxd.so.1
-- Up-to-date: /usr/local/lib/libusbmuxd.so
-- Up-to-date: /usr/local/include/usbmuxd.h
-- Up-to-date: /usr/local/include/usbmuxd-proto.h
-- Up-to-date: /usr/local/sbin/usbmuxd
-- Up-to-date: /lib/udev/rules.d/85-usbmuxd.rules
-- Up-to-date: /usr/local/bin/iproxy
lucas@kktua:~/Downloads/usbmuxd/build$

rebooted both iPod and machine.



7: reboot, ipod will mount and ask if you want to start a music app

rebooted but it still DOES NOT ASK FOR MOUNTING! it does not mount automagically, also the folder ".gvfs" is empty! I created the another user but it still doesn't mount automatically with the new user.

banshee daily build works as well as stock rhythmbox ENJOY!!

I didn't download from the git build, only from apt, but it doesn't work with rhythmbom neither with banshee. :(

some idea? I CAN recognize with ifuse, ideviceinfo and so on, so I think the problem is not about recognizing the device, I think it's about this "automount" and how it succeed.

thanks!

Lucas.

---

### Post by seadao on 2010-12-09
can you please tell us what version of ubuntu you use?? this guide only works with 10.10 and gnome(so people reported it working with 10.04, i haven't tried)

from what you posted, i can seen that most of the process is right, i have recently wiped out my ipod by accident and had to recreate the database with itunes in windows again, and it did complain but i chose to restore to old settings option and it worked fine(but changed my user options to older ones, that was annoying) i suspect this happens only when the ipod has been previously connected to the installed itunes, i'll try it with fresh itunes/windows install next time(that how i did it originally in virtual box)

now i suspect that you didn't install libusbmuxd correctly or something is messed up with your mounting permissions, one of the user fixed it by creating a new user in ubuntu(you can try to add yourself to the fuse group)

also about banshee daily build: DON'T USE THEM NOW use the stable ppa it works great and stable. i accidentally updated my daily build and it broke ipod compatibility

try to carefully redo each step it would work on fresh 10.10 no problem


EDIT: i did a quick search and arabis in this thread pointed out that you can get a compiled deb from a debian repo!!!!!!!
[http://packages.debian.org/experimental/usbmuxd](http://packages.debian.org/experimental/usbmuxd)
FINALLY!!!!!!!!(UPDATE, no longer needed, use the one in ppamcenery/ppa)

---

### Post by Cogizio on 2010-12-17
> **seadao said:**
> 
EDIT: i did a quick search and arabis in this thread pointed out that you can get a compiled deb from a debian repo!!!!!!!
[http://packages.debian.org/experimental/usbmuxd](http://packages.debian.org/experimental/usbmuxd)
FINALLY!!!!!!!!

Time to update my guide! :p

---

### Post by B0rat on 2010-12-26
Thanks for the above link. I was just googling about this iPod Touch 4G issue and found this page. I am still using 10.04 and before installing usbmuxd, I had to install an updated version of libusb. But it was also available on the Debian site.

---

### Post by JIMIneitor on 2010-12-30
Hi, I have 10.10, and my ipod is on 4.2.1, I changed the DB to version 2 but neither rhythmbox nor gtkpod will make the song appear on my device

Also, when i connect my device and fire up banshee, it unmounts my ipod, and this only happens with banshee

any idea on what is going on here?

---

### Post by DShad on 2011-01-05
> **JIMIneitor said:**
> Hi, I have 10.10, and my ipod is on 4.2.1, I changed the DB to version 2 but neither rhythmbox nor gtkpod will make the song appear on my device

Also, when i connect my device and fire up banshee, it unmounts my ipod, and this only happens with banshee

any idea on what is going on here?

Are there any development on iPhone 4 (iOs 4.2.1) or iPod Touch 4g (iOs 4.1)?

I have those 2 devices and they are recognized but after transferring some mp3, they don't show up after disconnecting...

Do I absolutely need to jailbreak them to make this work?

Thanks

P.S. I'm on Ubuntu 10.10 and libimobiledevice 1.0.4-1 and usbmuxd 1.0.6-1 are installed.

---

### Post by conorsulli on 2011-02-06
Method no Longer works even with jailbreaking now (6 feb 11 ) been this way a few weeks
:confused:

---

### Post by DShad on 2011-02-06
> **JIMIneitor said:**
> Hi, I have 10.10, and my ipod is on 4.2.1, I changed the DB to version 2 but neither rhythmbox nor gtkpod will make the song appear on my device

Also, when i connect my device and fire up banshee, it unmounts my ipod, and this only happens with banshee

any idea on what is going on here?

I had success ONLY with Banshee.

Give it a try.

---

### Post by seadao on 2011-02-09
to everyone still having problems:

please follow the steps on page 5 in order, if you get errors post the error and the step, i have fixed this months ago and it's still working flawlessly, i can't help you if you are not following the steps

faq:
1. do i have to jailbreak?
a: YES you must jailbreak to be able to edit files in lockdown otherwise nothing will work (thanks to apple for the new db)

2. does this work in 4.2.xx?
a: i don't know i did not update cuz i don't use itunes or windows, but i think if you read this thread some people got it working on 4.2.xx with similar steps

3. do i have to be very careful not to brick my ipod?
a: yes you must carefully read this thread starting from page 1 to 5, and carefully follow the steps on page five.

please post information about your errors, "this is not working for me" is not helpful and wastes thread space.

---

### Post by mbeierl on 2011-02-19
Sorry to say, confirmed I followed the steps exactly - and I have done this before with a 4.1 ios iPod touch, but my 2nd 4.2 (untethered jailbreak) iPod touch (same model) does not work.  It appears to, but at the end I get:

```
Failed to save iPod database - GLib.GException: Failed to generate sqlite database (in `libgpod-sharp)
```

when using Banshee and 

```
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 173 post process commands now
[run_post_process_commands] ERROR when executing 'RemoveNullFromArtistName': no such table: item_artist
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_album_artist_name_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_genre_map_genre_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_album_name_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_artist_name_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_genre_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_composer_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_album_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_album_artist_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_series_name_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_title_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_item_artist_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'InsertIntoSortMap_composer_name_order': no such function: iPhoneSortKey
[run_post_process_commands] ERROR when executing 'UpdateSortMapNameSection': no such function: iPhoneSortSection
[run_post_process_commands] ERROR when executing 'CreateIndex_SongGenres_Sections': table item has no column named genre_blank
[run_post_process_commands] ERROR when executing 'CreateIndex_ArtistAlbums_Sections': index ArtistItems_Sections already exists
[run_post_process_commands] 156 out of 173 post process commands successfully executed

```

in gtkpod.

---

### Post by stad on 2011-02-21
I have been trying this for hours. Why is this not working?! I have a ipod touch 4th gen, with OS 4.1 (8B18). The only thing I did differently was use limera1n to jailbreak. Would this cause problems?

EDIT: Ipod is jailbroken, and if seen in Banshee. However, music doesn't sync to the ipod.

---

### Post by conorsulli on 2011-02-23
Seems to be a new version of libimobiledevice called libimobiledevice2 instead of libimobiledevice1 in natty can anybody confirm if their ipod is working with this package maybe or even the libimobiledevice1? with the development build of Ubuntu Natty Narwhal 11.04?

[http://packages.debian.org/experimen...imobiledevice2](http://packages.debian.org/experimen...imobiledevice2)

I might give this a try later on and just upgrade my system altogether 

Wish me Luuccckkk!

---

### Post by pweyandt on 2011-02-26
I have been having a lot of trouble mounting my iPhone 4.  I verified I had all the correct libs in place and it still did not mount. I finally came across a post that talked about pairing the device.  This worked for me.  Might be worth a try.  Just post this into a terminal with your I-device attached:

idevicepair unpair
idevicepair pair
idevicepair validate

I hope it helps
Quick update...I even tested my iPad and I can connect that!  :^D

---

### Post by sesnf86 on 2011-02-27
I have  recently purchased an ipod touch 4g and i am trying to sync it with my  laptop running on slackware 13.1.

So i looked around these links [http://ubuntuforums.org/showthread.php?t=1567271](http://ubuntuforums.org/showthread.php?t=1567271)  and [http://everydaylht.com/howtos/deskto...ouch-on-linux/]("http://everydaylht.com/howtos/desktop/iphoneipod-touch-on-linux/")

 and downloaded 


[libimobiledevice-1.0.4.tar.bz2]("http://www.libimobiledevice.org/downloads/libimobiledevice-1.0.4.tar.bz2")
[ifuse-1.1.1.tar.bz2]("http://www.libimobiledevice.org/downloads/ifuse-1.1.1.tar.bz2")
[libplist-1.3.tar.bz2]("http://www.libimobiledevice.org/downloads/libplist-1.3.tar.bz2")
[usbmuxd-1.0.6.tar.bz2]("http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.6.tar.bz2")

I have created slackware packages using src2pkg and installed them on my  system.
But when i do ifuse /media/ipod it gives an error

 	Quote:
 	 	 		 			 				usbmuxd_get_device_list: error opening socket!
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb   device.
If you're still having issues try unplugging the device and reconnecting   it. 			 		 	 	 
i am using root account while doing this.

when i do a lsusb | grep Apple it shows 

 	Quote:
 	 	 		 			 				Bus 002 Device 006: ID 05ac:129e Apple, Inc. 			 		 	 	 
So can anybody point out what i am doing wrong 

thanks

---

### Post by seadao on 2011-03-01
i think you still need libgpod, and libplist,
now all you need to do is jailbreak your ipod and edit
/System/Library/Lockdown/Checkpoint.xml
change DBVersion to 2

then delete itunes_control in
/var/mobile/media

reboot

use itunes to transfer 1 mp3 to it

and after that it will work in linux

edit:oops you have libplist

---

### Post by stad on 2011-03-04
Please let me know if you can get this working, sesnf86. I cannot seem to get the ipod 4th gen to sync properly.

---

### Post by spongebob1981 on 2011-03-08
I confirm. I'm quite good at following instructions posted here and ubuntu 10.04 64bits, ipod touch 4gen iOS 4.1 NOT WORKING.

gtkpod: failed to generate sqlite database.
banshee: seemed to copy but songs do not appear in the device. After updating usbmux from git, it simply doesnt show the device as plugged in.
rythmbox: shows the device, copies the songs but they dont show in the device.

tried some or al of the steps in ubuntu 10.10 in VBox, same results.

Any ideas?

---

### Post by seadao on 2011-03-08
firstly i can only confirm for myself that this totally works on ubuntu 10.10 gnome(only) with ipod touch 4g on firmware 4.1 in banshee and rhythmbox, and has been working since November, i last checked 2 seconds ago

secondly please provide more info on how you jailbroke your ipod and how you edited/saved Checkpoint.xml (did you save it, please double check that DBVersion is set to 2) watch for syntax errors

also when you say it appears in rhythmbox/banshee can you see the 1 mp3 you uploaded to it from itunes(this step sets up db version 2 system on the device)

also if you followed everything correctly try to use an older version of itunes (delete itunes_contol again and upload 1 mp3 with itunes

also open up synaptic and search "ipod touch", make sure you have all the relevant libs installed

also check that you have ifuse and your user is allowed to mount with fuse(user is part of the fuse group) try to mount the ipod with ifuse

---

### Post by stad on 2011-03-22
> **seadao said:**
> firstly i can only confirm for myself that this totally works on ubuntu 10.10 gnome(only) with ipod touch 4g on firmware 4.1 in banshee and rhythmbox, and has been working since November, i last checked 2 seconds ago
Okay great, hopefully you can help me!

> **seadao said:**
> secondly please provide more info on how you jailbroke your ipod and how you edited/saved Checkpoint.xml (did you save it, please double check that DBVersion is set to 2) watch for syntax errors
I jailbroke the ipod using limera1n. Would this be a problem? If so, why?

Also, the DBVersion is set to 2. It is saved, and confirmed.

> **seadao said:**
> also when you say it appears in rhythmbox/banshee can you see the 1 mp3 you uploaded to it from itunes(this step sets up db version 2 system on the device)
Yes, it's there.

> **seadao said:**
> also if you followed everything correctly try to use an older version of itunes (delete itunes_contol again and upload 1 mp3 with itunes
I have no tried this, but will when I get home.

> **seadao said:**
> also open up synaptic and search "ipod touch", make sure you have all the relevant libs installed
I will double check

> **seadao said:**
> also check that you have ifuse and your user is allowed to mount with fuse(user is part of the fuse group) try to mount the ipod with ifuse
Can you elaborate?


Basically, it seems as though the only difference I have from the initial instructions is my jailbreak method. Would this be the reason why my sync isn't working? I was under the impression that jailbreaking was done to change the DBVersion, which I successfully did.

---

### Post by patmalcolm91 on 2011-04-09
> **spongebob1981 said:**
> I confirm. I'm quite good at following instructions posted here and ubuntu 10.04 64bits, ipod touch 4gen iOS 4.1 NOT WORKING.

gtkpod: failed to generate sqlite database.
banshee: seemed to copy but songs do not appear in the device. After updating usbmux from git, it simply doesnt show the device as plugged in.
rythmbox: shows the device, copies the songs but they dont show in the device.

tried some or al of the steps in ubuntu 10.10 in VBox, same results.

Any ideas?

I also got the "failed to generate sqlite database" error in gtkpod. The way I fixed it was to downgrade libgpod to 0.7.95. to do this, go to synaptic, find the packages libgpod4 and libgpod-common, select on of them, go Package->Force Version then select 0.7.95. Apparently there is a bug in libgpod's current version that is causing this error with DBVersion 2.

---

### Post by esta.es.nuestra on 2011-04-18
Okay, so I'm running Ubuntu 10.04 and want to get an iPod touch 4G, but a) have never owned an Apple product, and b) am still new to linux. I've been trying to follow the threads on the forums to figure out how to sync and upload music, but am wondering if anyone has found a way to do so WITHOUT jailbreak? If so, or know where there is a post that provides all that info, send me in that direction. Thanks!

---

### Post by Barbalras on 2011-05-15
> **patmalcolm91 said:**
> I also got the "failed to generate sqlite database" error in gtkpod. The way I fixed it was to downgrade libgpod to 0.7.95. to do this, go to synaptic, find the packages libgpod4 and libgpod-common, select on of them, go Package->Force Version then select 0.7.95. Apparently there is a bug in libgpod's current version that is causing this error with DBVersion 2.

I tried that but I don't get the option "0.7.95", just "0.8.0-2" and "0.8.0-2-hyper1+natty"

---

### Post by patmalcolm91 on 2011-05-15
> **Barbalras said:**
> I tried that but I don't get the option "0.7.95", just "0.8.0-2" and "0.8.0-2-hyper1+natty"

More than likely, natty doesn't have that version in the repos. You'll have to manually install it. I checked the mcenery repo and the ubuntu package database, and can't seem to find the deb file for 0.7.95, maybe someone can point out a convenient place to get it?

EDIT: [Here](https://launchpad.net/ubuntu/+source/libgpod/0.7.95-1/+build/1994702) is a page that google turned up, to get you started, you'll have to google for the dependencies if necessary.

---

### Post by paalfe on 2011-06-07
[QUOTE=http://www.gtkpod.org/wiki/Libgpod]Latest stable release is version 0.8.0. This release has support for all iPod models except the iPod Nano 6g (the touch one). Most non-jailbroken iOS devices (iPod Touch, iPhone) are also supported with the notable exception of the iPad and the iPhone/iPod Touch 4 which are only supported as read-only devices.[/QUOTE]

[QUOTE=http://www.libimobiledevice.org/]
Feature=Music/Video Synchronization
Status=Done
iOS=4.3.3
Notes=Rhythmbox, gtkpod and Amarok sync with latest libgpod >= 0.7.90. The iPhone 4, iPod Touch 4, iPad 1/2 and Apple TV do NOT work.
Any device with DBVersion > 4 does NOT work. To check your DBVersion run "ideviceinfo -q com.apple.mobile.iTunes -k DBVersion".
[/QUOTE]

My iPod touch 4g runs iOS v4.3.3 and I have tried:
- [http://cogizio.org/operating-systems/ubuntu/3089]("http://cogizio.org/operating-systems/ubuntu/3089")
- [http://ubuntuforums.org/showpost.php?p=10510355&postcount=112]("http://ubuntuforums.org/showpost.php?p=10510355&postcount=112")

it is read-only in banshee for me / banshee failes to write iPod database.

```
Failed to save iPod database - GLib.GException: Failed to generate sqlite database (in `libgpod-sharp')
  at GPod.ITDB.Write () [0x00000] in <filename unknown>:0
  at Banshee.Dap.AppleDevice.AppleDeviceSource.PerformSyncThreadCycle () [0x00000] in <filename unknown>:0
libitdbprep: itdb_iphone_stop_sync called
itdb_iphone_stop_sync: posted syncDidFinish
```

```
ideviceinfo -q com.apple.mobile.iTunes -k DBVersion
2
```


I'm confused?


Edited:
--------------------------------------------------------
Now I'm more confused and tired, I got it to work :D

I have been trying on ubuntu 11.04 so I went to my ubuntu 10.10 PC and played around with libgpod 0.7.5, gtkpod, rhytmbox and banshee. Got sql-error all the time, then suddenly I saved iPod database. Hmmm!? Not sure what I did, but it now works on my Windows PC with iTunes, ubuntu 10.10 with banshee 1.8 and ubuntu 11.04 with banshee 2.0.0.

Time to go to bed...

---

### Post by slcpunk on 2011-09-02
Hi all.  Try this if you're still stuck.  I was, and it worked for me. 

(JBroken, iOS 4.3.3, ubuntu 10.04)

[http://ubuntuforums.org/showthread.php?p=11081850](http://ubuntuforums.org/showthread.php?p=11081850)

I made the hash file as directed, put it on phone, rebooted, and BAM! sync'd with rhythmbox.

Sweet!

---

### Post by slcpunk on 2012-01-27
If you did have this working, word or warning, in case you thought it would be a good idea ... don't update to ios5 ... no worky again.  Not sure what I was thinking.

---

