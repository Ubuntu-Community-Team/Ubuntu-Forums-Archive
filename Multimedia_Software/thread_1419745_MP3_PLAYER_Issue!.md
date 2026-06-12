---
title: "MP3 PLAYER Issue!"
date: 2010-03-02
forum: Multimedia Software
---

### Post by jokei on 2010-03-02
Hi, I just got a cheap MP3 player and am having issues with it...

I'm just using the Audio CD Extractor to copy MP3s from my cds and was assuming I could just drag and drop them from my music folder onto the player.  

It comes up with "Unrecognised Media" - I'm definitely converting the cds > MP3.

There are 2 folders on the player 
FMIN.DIR
MICIN.DIR

Does it need to be in one of these specifically?  

This is probably a facepalm moment for anyone reading this, but I'm an old person and more in touch with the world of vinyl.

---

### Post by jokei on 2010-03-02
Bump

---

### Post by zeroseven0183 on 2010-03-02
Those two files with .DIR are definitely needed by the player, I assume.
What appears on the screen if you open either of those files (or maybe, they are directories)?

---

### Post by ubunterooster on 2010-03-02
FMIN.DIR is likely radio and MICIN.DIR, Microphone.
Try making a folder called MUSIC

What kind of portable media player are you using?

[http://rockbox.org](http://rockbox.org)
linux-ish firmware for several players.
[http://anythingbutipod.com](http://anythingbutipod.com)
another site w/ good forums. It deals especially with portable media players [also refferred to as PMP's]

---

### Post by jokei on 2010-03-13
Ok, so I'm pretty hungover, please bear with me.

I put a load of cds onto my laptop and transferred them over to the MP3 player, some came up with an error message - which I can't remember, was in a hurry to get to work, so just set off with the music I had on it.

Now, all the files on the MP3 have padlock symbols over them and it's not letting me put any new music on or take any off???

It's this one [http://www.clasohlson.co.uk/link/m3/Product,Product.aspx?artnr=38-3191](http://www.clasohlson.co.uk/link/m3/Product,Product.aspx?artnr=38-3191)

I've listened to the new Silver Mt Zion album 8 times now and it's starting to do my head in.

What's Rockbox?

---

### Post by ubunterooster on 2010-03-13
Copy any files that are only on the player so you don't lose them.

    Go to the system settings of your player and look for a reformat option.

[rockbox does not list your player as one of the ones it runs on to give more features and a better battery life]

---

### Post by zeroseven0183 on 2010-03-13
Try accessing the MP3 player when you have root access. Open Nautilus with root privilege by typing
```
gksu nautilus
```

Browse to that folder and start copying or deleting the music files.

---

### Post by jokei on 2010-03-13
Thanks to the both of you for your help so far, please don't facepalm too much reading this...  :)

What is Nautilis?  I'm using Xubuntu 9.1 and using Audio CD Extractor to convert cds to MP3.

I can't find any Reformat option on/in the player???

---

### Post by ubunterooster on 2010-03-13
nautilus is a gnome file manager.
try: ```

sudo thunar

``` and then try to delete them

As for reformat, I can't help to much as there is no manual I can find to view.

[no face palming has yet occured]

---

### Post by jokei on 2010-03-13
Ok, the Sudo Thunar command allowed me to view the MP3 player, but still wouldn't allow the files to be deleted???

I'm off to dig out the manual, that's probably hidden somewhere.

I've attached a couple of screenshots.  Thanks very much for your help and patience.

---

### Post by ubunterooster on 2010-03-13
[facepalms at your player's manufacturer for no having a viewable instruction book online, not at you]

you could ```

sudo apt-get nautilus

```
then 
```

gksu nautilus

```



Also see your player for a "reset to defaults" or similar option

---

### Post by jokei on 2010-03-13
Right, sudo apt-get Nautilus yields
"E: Invalid Operation Nautilus"

???

I got the instruction manual and surprisingly there's no help for anything but Windows...
their online help is ludicrously bad and I know they're just going to tell me that Linux isn't supported.

I'm using a Windows XP emulator on here to play some games, is that of use?

---

### Post by ubunterooster on 2010-03-13
"Nautilus" should be "nautilus". No capitals.

 Edit:  I was looking for instructions for telling device to reset itself to factory settings. If the nautilus file browser works, there will be no need to reformat/reset to factory defaults

---

### Post by jokei on 2010-03-13
Yeah, sorry, I should've been more clear - I just copied and pasted the text from your post, still not working though.

---

### Post by ubunterooster on 2010-03-13
ok. Go to System>Administration>Synaptic Package Manager.

Install nautilus from there

---

### Post by jokei on 2010-03-13
:(  ???  Got this message trying to install it...

W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/main Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/multiverse Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/restricted Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/universe Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_universe_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/main Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/multiverse Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/restricted Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/universe Packages (/var/lib/apt/lists/Xubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20i386%20(20091027)_dists_karmic_universe_binary-i386_Packages)
got

---

### Post by ubunterooster on 2010-03-13
Hmmm. It is trying to get the packages off a cd drive, leading me to think that you have disabled repositories

---

### Post by jokei on 2010-03-13
Not knowingly...

I just went back into the Add/remove Applications and got this

There has been an error installing the following application - Nautilus...

I tried to download that and got this

W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/n/nautilus-actions/nautilus-actions_2.29.1-1~getdeb1_i386.deb](http://archive.getdeb.net/ubuntu/pool/apps/n/nautilus-actions/nautilus-actions_2.29.1-1~getdeb1_i386.deb)
  500  Internal Server Error

---

### Post by ubunterooster on 2010-03-13
try clicking the said link above
edit: never mind, link is errant.

---

### Post by jokei on 2010-03-13
404 Not found.

I've not really tinkered with Xubuntu much, I just use it for web/browsing and a bit of nerdery...

Not messed with any of the settings programmes...  I'm feeling lost, thanks for trying.

---

### Post by ubunterooster on 2010-03-13
wait! did a lil' bit of url tinkering:  [http://getdeb.fastbull.org//ubuntu/pool/apps/n/nautilus-actions/](http://getdeb.fastbull.org//ubuntu/pool/apps/n/nautilus-actions/)

---

### Post by jokei on 2010-03-13
You're a gentleman.  

Which one do I go for?

---

### Post by ubunterooster on 2010-03-13
One of the .deb files, likely the amd_64

---

### Post by jokei on 2010-03-13
Ok, installed some updates - must keep more on top of that, then managed to install Nautilus fine...

I've now done this (below), what next?

---

### Post by ubunterooster on 2010-03-13
no nautilus window comes up?

---

### Post by jokei on 2010-03-13
Nope, I put the mp3 player in, wait for it to detect, then click on it under "places" then opened the terminal in that place, typed "gksu nautilus"

and that's it so far?

---

### Post by ubunterooster on 2010-03-13
Don't navigate to that folder, try typing the command into the default terminal location (home).
  

 Also try just typing "nautilus" into the terminal to see if it opens that way

---

### Post by ubunterooster on 2010-03-13
try : gksudo nautilus , or 
try: gksudo thunar

Try to add files, not removing yet
Also, are the files copied via thunar or ripped by another program?

edit: we tried sudo thunar. Try that again, but right-click the folders and select properties. change permissions if possible.

---

### Post by jokei on 2010-03-14
Ok, here we go

gksudo thunar - opens, allows me into the mp3, but not to change anything on it.

gksudo nautilus - gave me this:

(nautilus:5193): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

I copied the cds using audio cd extractor

Just typing in Nautilus also yields the above error, but did open a window that allowed me to view files on the MP3 but not do anything with them, cut/paste etc.

This might be a stab in the dark, but could I do something via Wine/Windows emulator?

---

### Post by denham2010 on 2010-03-15
Ok, the padlock you are seeing means you do not have the necessary file permissions to do anything to the files.

You don't need nautilus (the gnome filebrowser) as you are using xfce and this has thunar which does the same thing.

Open thunar as root - in a terminal type:
```
sudo thunar
```
and enter your password.

Navigate to the mp3 player and right click on one of the album folders.

Select Properties from the menu that appears. Paste a screenshot of the properties window so we can see what permissions are set.

Cheers.

---

### Post by jokei on 2010-03-15
Hmm, it's early and I have to run out to work.

Plugging my MP3 into the usb, it lights up, but Xubuntu no longer seems to recognise it???

---

### Post by zeroseven0183 on 2010-03-15
Shame on me, I suggested "gksu Nautilus"... Didn't notice you're using Xubuntu. Sorry for that.

Anyway, did gksu Thunar work?

---

### Post by ubunterooster on 2010-03-15
@07: he said "gksudo thunar" opens it. right  now the problem is mounting

---

### Post by jokei on 2010-03-15
Pardon my lack of knowledge, if times weren't so hard I'd just go buy a recommended one that would work on Xubuntu...  but I'm poor.  :(

Anyway, I have a drivers cdrom that came with it, but being a man, thought "screw the instructions" and just plugged it in...  initially this was fine, I managed to get some music on there and play it no problems, but then it was choosey about what it would let you put on and now the whole thing's locked-up.

Should I load the drivers?  They're for Windows 98se or later, I'm using a Windows emulator to play games on my laptop already.

---

### Post by ubunterooster on 2010-03-15
Can't see a problem with that. Go ahead.

---

### Post by jokei on 2010-03-15
Ok, installed the drivers, setup.exe file after I did this, a Windows-style box popped up and said you need to restart, do this now.  I hit yes and the box closed, nothing happened so I restarted Xubuntu.

It's still not registering the mp3 player???  Curses!!!

I'm guessing there MIGHT be an issue with Wine not registering the restart?

Here's a screenshot of the other files on the disc.  I

---

### Post by ubunterooster on 2010-03-15
need to automount. Forget how [hits head on wall]. Will go look then post back here.

---

### Post by ubunterooster on 2010-03-15
(&#8593; A temporary slip of "professionalism")

Start thunar [gksudo thunar] then go to your filesystem, then to media. It will be under some cryptic name, but once you double-click on it, you'll see the same folders inside. Go back to the folder "media" right-click on your player and select "properties"

---

### Post by jokei on 2010-03-15
Ok, did that, in the media folder there were cdrom, with an arrow across the folder/symbol and cdrom0.

I went into both folders, neither had anything in.

---

### Post by ubunterooster on 2010-03-15
Completely ignoring....meh. [Shotgun to GUI.] Terminal it is [even though I dislike it]

In the terminal type: ```
 dmesg &#65372; grep ' [hs]d[a-z]: ' 
``` (this is "check all disk types/locations") and paste results here. Then we'll try mounting them.

---

### Post by jokei on 2010-03-15
Thanks man.

Here's the screenshot, will check in tomorrow, I'm going to drown my sorrows.

---

### Post by ubunterooster on 2010-03-15
[edit]you may disregard this post if you wish as the guy below really knows what he is doing. But the last paragraph is worth consideration[end edit]

  There is a Disk Utility, likely in system tools. This will have a Storage list with your player (it will likely be a 3.8-4.5Gb disk) listed among your CD and  hard drive(s). Click on the player then look at the partitions under 'storage properties'. We are looking for something similar to /dev/sdc or /dev/hdb1.  It will be a "/dev/", followed by a "h" or "s" followed by a "d" followed by another letter and possibly a number. 
  Once you have this, go to the terminal and enter ```
 sudo mount -t vfat /dev/hdb1 /mnt 
``` Replace "/dev/hdb1" with the appropriate device location.

BUT, if this does not work, you can get a microSD card with an adapter to regular SD for very little at many stores. Stick the microSD in the SD adapter and stick that adapter into your computers SD slot, put the files on it, unmount it and stick the microSD into your player.

---

### Post by scraze on 2010-03-15
Hey jokei! Took your bait at 'the other' forum and actually read your thread. ;]

For me, I always have to visualize (if you will) the problem, before I can get to a solution. The biggest hurdle to overcome in this case is the randomness: obviously, if you succeeded to write mp3s to your player, everything is in place to work. We don't have to install drivers or reboot or anything - at least we shouldn't have to.. But still, things don't work as they should be. Until we figure out why, this dissonance between expected and experienced state seems to indicate a factor of randomness, causing the logical paradox of having all the hardware and software but not being able to use it.

So it's time to hunt this randomness down :D and shoot it in the face for a little bit. It's only random as long as we don't know what it is.

Before we head out, I'd like to add a tiny disclaimer; I live in the terminal, I love editing files manually. It's probably possible to do everything in GUI nowadays, but I'm not familiar with those ridiculously crazy new methods (terminal's always faster anyway ;D).
Even worse, I don't have Ubuntu installed - just Debian (Ubuntu's unisex parent). Many things are the same, but I'm not aware of most of the differences.. A bit of stumbling may occur.

Now then - first things first; when trying things like 'sudo apt-get install nautilus', do you still get those cd-rom errors? If so, you 'need' to change the files in /etc/apt so they refer to proper ubuntu repositories. While installing Ubuntu, you usually get the choice to change the apt source from the cdrom to an internet repository - seems like that didn't work out too well on your system ;). [This page](https://help.ubuntu.com/community/Repositories/CommandLine) adequately describes everything you'd need to know, and provides an example /etc/apt/sources.list file. If you're going to copy those lines, make sure you change it so it's adequate for your version (the example is based on Ubuntu Hardy). It's also quite possible that your sources.list already contains the correct lines to make use of Ubuntu's repositories. Finally, on Debian there's a program called 'netselect' which is a front-end for writing /etc/apt/sources.list files - you just choose a mirror and voila. It's worth a shot to see if Ubuntu has netselect as well (just try to run it in a terminal or via Alt-F2).
When you're done changing /etc/apt/sources.list, make sure to run sudo apt-get update so that the package database on your system can be updated. Packages themselves won"t be updated by that command (sudo aptitude upgrade or sudo aptitude safe-upgrade will; GUI frontend is synaptic).

Back on topic! Randomness hunting and such!

Now let's lay out the order in which things should go:
1. You plug in your player; it makes an USB connection
2. The kernel notices the USB event, and tries to find out whether there is a driver for the device
3.The driver has been successfully loaded, and supplied a handle or node for the device (/dev/X); the system likes to know what to do with it (for example, automount).

and

4. Your device is properly mounted and allows you to do anything the driver can do for you.


It sure sounds simple when put like this. So I'll try to keep this approach intact, by describing what we can do in each step to check whether it is working as supposed, and if not, what is causing the problem. I felt the urge to write a complete step-by-step guide, but the most important ones for you are probably just step 1 and step 4; step 1 for simply recognizing the USB device, and step 4 for those padlocks. Here goes:


  **Step 1**
To list all the USB devices the kernel acknowledges;  ```
lsusb  
```
Not all manufacturers supply USB names to the usb id list, so it might not show a easily recognizable name (ie MP3 player); so if you see no obvious match, just try to spot the difference between lsusb's output when the player's plugged in versus out. Codewise:
```

lsusb > /tmp/lsusb1 # while plugged in
lsusb > /tmp/lsusb2 # while plugged out
diff /tmp/lsusb1 /tmp/lsusb2

```
In this case, what matters most is that something shows up, since the driver already worked once; we won't have to figure out what driver to use.
Also, we need to know (for troubleshooting) the USB ID - two 4-character hexadecimals separated by a colon, prefixed by "ID" (eg "ID **041e:4157**"). This number is unique for each implementation of chipsets, meaning that it indicates exactly which device you're using. The verbose output of lsusb for that device offers even more information about the used chipset: ```
lsusb -v -d 041e:4157
```
For mp3 players, the verbose output should report MTP or Mass Storage as the interface. Since troubleshooting differs substantially between those two, it's a good idea to find out now.

If your device shows up in lsusb's output, the USB part is fine, and you can jump to step 2. If it doesn't, something is askew in the hardware department.. It's possible that your system powers down USB ports when unused, and fails to switch them back on when needed. In my case, I have to wait about 10 seconds before my system notices anything. If the problem persists, you could try to enter the BIOS at startup and see whether such an option exists (probably under ACPI or APM), and if so, change it. If that fails, you might want to try temporarily shutting off APM or ACPI entirely (not recommended for laptops though - they get hot) - something like /etc/init.d/acpi stop or /etc/init.d/apm stop should do the trick. This should be the last resort - let's hope for a working port. :)


  **Step 2**
The easiest way (I know of) to find out what your kernel is doing with the USB event, is to watch it while working. Try:
```

sudo tail -F /var/log/syslog # press ctrl-c to quit!

```
and, while it's running, play pluggetyplug with your device again (once could be enough). A lot of information may scroll by; all of it is relevant to us. It should start by reporting changes in an USB port, followed by recognition by USB ID. The latter starts like this:
```

Mar 15 23:47:32 avithy kernel: usb 2-2.4.2: New USB device found, idVendor=041e, idProduct=4157

```
and ends like this:
```

Mar 15 23:59:00 avithy kernel: usb 2-2.4.2:1.0: uevent

```
This uevent is the signal sent through after USB recognition; anything that would like to act on this kind of device should react now.

For a USB Mass Storage device, the reaction should look like this:
```

Mar 15 23:59:00 avithy kernel: usb-storage 2-2.4.2:1.0: usb_probe_interface
Mar 15 23:59:00 avithy kernel: usb-storage 2-2.4.2:1.0: usb_probe_interface - got id
Mar 15 23:59:00 avithy kernel: usb-storage: USB Mass Storage device detected
[..]
Mar 16 23:59:06 avithy kernel: sd 14:0:0:0: [sde] Attached SCSI removable disk

```
The lines in syslog should describe the node assigned to the device. In this example, the node /dev/sde was assigned.

For mp3 players employing the MTP protocol, no such node is assigned - neither is there a reaction at all. Instead programs like libmtp provide a virtual interface, which can be used by other software (such as Amarok) on the spot. If yours is a MTP device, continue at step 3 (see explanation of lsusb's verbose output above to find out whether yours is MTP or Mass Storage).

If the device is a Mass Storage device and yet there is no reaction except for the USB port, then things are wonky. Since it worked before, it should be recognized. There are two possible causes; either the driver module can't loaded, or there are no system rules to ask for the module to be loaded. Since both are quite improbable for your situation and an adequate explanation (again) too lengthy for this post, I'll just say the same as in step 1 ... let's hope it works ;D and if it doesn't, we'll go into details.


  **Step 3**
For Mass Storage devices; the device has to be mounted to be used. First, check whether it is mounted already:
```
mount
```
If the device node from the syslog (/dev/sde in the example) is listed in the output, then head to step 4! If not, then try to mount it by:
```

sudo mount /dev/sdX /media/usb

```
or (for partitioned disks)
```

sudo mount /dev/sdX1 /media/usb

```
Make sure the target directory exists and is empty (/media/usb may be Debian-specific). After mounting, simply head to that location with your favorite filebrowser (nautilus, thunar?). If the device has indeed been successfully mounted (ie. you can see the files), but it didn't show up in the output of mount earlier, then the correct rules for device handling after driver loading is missing. Again the approach to solve the problem of missing rules is too much of an endeavour for this post, but it boils down to udev rules in /etc/udev and automounting.

For MTP devices, there is nothing to do in this step :).


  **Step 4**
The device's drivers are running, all the actions have been performed. But something is still wrong.. padlocks perchance? Ideally, we would find out why it once worked fine and now doesn't.. but there is such a myriad of possible causes that it might be easier to force it to work again, instead.

For Mass Storage devices, all the permissions are regulated simply through the moutned file-system. The output of mount provides the information we need:
```

/dev/sde1 on /media/usb type vfat (rw)

```
In this example, the mounted device is of the vfat format, and mounted read-write (rw). Permissions for vfat type disks aren't compatible with ext2/ext3 permissions (linux' default filesystems), so only root can write to vfat disks mounted like this. But we can mount it differently..
```

umount /dev/sde1 # umount is .. unmount :}
mount -o uid=username,gid=username /dev/sde1 /media/usb # replace 'username'

```
Now, the output of mount shows:
```

/dev/sde1 on /media/usb type vfat (rw,uid=1000,gid=1000)

```
The uid=x,gid=x refers to the user specified by 'username' above; now, that user has access to the device as well. You should be able to filebrowse to /media/usb and do whatever you want.

For MTP devices, the software should do all the work. Unfortunately I'm not so well versed in MTP devices (using nor troubleshooting them), but as a starting point, the package mtp-tools should be installed. Confirm this with:
```
dpkg -l mtp-tools
```
It should return a line beginning with "ii". If it's not installed, install it with:
```
aptitude install mtp-tools
```

If mtp-tools is installed, then try:
```
mtp-detect
```
This should show you whether libmtp is able to find the device at all. If it can't, it will quit immediately. If it hangs for a while, then at least it has found an MTP device; and if after a while it spits out pages of info, then you're golden.


That concludes the steps to be taken (conceptually at least). At any point, if something goes wrong, please provide the output of the commands before the breakpoint. The information from lsusb could help a lot for us to figure out what you're dealing with as well.

I hope this post hasn't become too dazzling; if so, don't hesitate to ask for clarification. It's becoming evermore difficult to relate to the viewpoint of someone who normally wouldn't choose to deal with something like this ;} but I hope it provides a structural approach for a quick solution. I mean, one wants one's damned music, right! :guitar: :D

---

### Post by jokei on 2010-03-16
Gentlemen, thankyou both for your time on this.

**STEP 1:**

Ok, the lsusb command gave me this:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0402:5661 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**STEP 2**

Gave me this:

Mar 16 13:28:53 benjohnson kernel: [ 7144.696641] end_request: I/O error, dev sr0, sector 0
Mar 16 13:28:53 benjohnson kernel: [ 7144.699546] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 16 13:28:53 benjohnson kernel: [ 7144.699550] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 16 13:28:53 benjohnson kernel: [ 7144.699554] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 16 13:28:53 benjohnson kernel: [ 7144.699560] end_request: I/O error, dev sr0, sector 0
Mar 16 13:28:53 benjohnson kernel: [ 7144.704201] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 16 13:28:53 benjohnson kernel: [ 7144.704208] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 16 13:28:53 benjohnson kernel: [ 7144.704213] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 16 13:28:53 benjohnson kernel: [ 7144.704219] end_request: I/O error, dev sr0, sector 0
Mar 16 13:29:33 benjohnson wpa_supplicant[1013]: CTRL-EVENT-SCAN-RESULTS 

[B]STEP 3

[/B]The command
sudo mount /dev/sdX /media/usb
Gave This:

Mar 16 13:33:33 benjohnson wpa_supplicant[1013]: CTRL-EVENT-SCAN-RESULTS

[B]STEP 4

[/B]umount /dev/sde1 # umount is .. unmount :} mount -o uid=username,gid=ben johnson /dev/sde1 /media/usb
Mar 16 13:41:33 benjohnson wpa_supplicant[1013]: CTRL-EVENT-SCAN-RESULTS

aptitude install mtp-tools - nothing happened for a while then:

Mar 16 13:43:33 benjohnson wpa_supplicant[1013]: CTRL-EVENT-SCAN-RESULTS 
aptitude install mtp-tools
Mar 16 13:45:23 benjohnson kernel: [ 8134.588068] usb 2-1: USB disconnect, address 3
Mar 16 13:45:29 benjohnson kernel: [ 8140.728052] usb 2-1: new high speed USB device using ehci_hcd and address 4
Mar 16 13:45:29 benjohnson kernel: [ 8140.867503] usb 2-1: configuration #1 chosen from 1 choice
Mar 16 13:45:29 benjohnson kernel: [ 8140.868297] scsi7 : SCSI emulation for USB Mass Storage devices
Mar 16 13:45:29 benjohnson kernel: [ 8140.868408] usb-storage: device found at 4
Mar 16 13:45:29 benjohnson kernel: [ 8140.868410] usb-storage: waiting for device to settle before scanning
Mar 16 13:45:33 benjohnson wpa_supplicant[1013]: CTRL-EVENT-SCAN-RESULTS 
Mar 16 13:45:34 benjohnson kernel: [ 8145.870344] usb-storage: device scan complete
Mar 16 13:45:34 benjohnson kernel: [ 8145.874004] scsi 7:0:0:0: Direct-Access              Audio Player          PQ: 0 ANSI: 0 CCS
Mar 16 13:45:34 benjohnson kernel: [ 8145.874550] sd 7:0:0:0: Attached scsi generic sg2 type 0
Mar 16 13:45:34 benjohnson kernel: [ 8145.883099] sd 7:0:0:0: [sdb] 8207360 512-byte logical blocks: (4.20 GB/3.91 GiB)
Mar 16 13:45:34 benjohnson kernel: [ 8145.884262] sd 7:0:0:0: [sdb] Write Protect is off
Mar 16 13:45:34 benjohnson kernel: [ 8145.884267] sd 7:0:0:0: [sdb] Mode Sense: 3b 00 00 00
Mar 16 13:45:34 benjohnson kernel: [ 8145.884269] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Mar 16 13:45:34 benjohnson kernel: [ 8145.893548] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Mar 16 13:45:34 benjohnson kernel: [ 8145.893556]  sdb: sdb1
Mar 16 13:45:34 benjohnson kernel: [ 8145.900228] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Mar 16 13:45:34 benjohnson kernel: [ 8145.900235] sd 7:0:0:0: [sdb] Attached SCSI removable disk

[B]STEP 5

[/B]Nice cup of coffee and a cigarette - again, thank you gentlemen.  Do you think this is worth me trying it on a friends (Windows) computer?  See if it's accessible/detectable that way?  I guess at least it would indicate whether or not I've destroyed the MP3 somehow.

---

### Post by ubunterooster on 2010-03-16
I think you have the device listed as dev/sde1 so try ```
 sudo mount -t vfat /dev/sde1 /mnt 
``` then check in thunar to see if it is mounted.

---

### Post by jokei on 2010-03-16
No luck there I'm afraid Sir.

mount: special device /dev/sde1 does not exist

---

### Post by ubunterooster on 2010-03-16
uh, oops. Replace e with b to make it:

```
 sudo mount -t vfat /dev/sdb1 /mnt 
```

---

### Post by jokei on 2010-03-16
Ok, I feel like I've made some progress, tried the last post and got this:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Looks like the above message is incomplete, but I just copied/pasted, not sure if that last sentence was meant to run on???

Where do I find the syslog?

---

### Post by ubunterooster on 2010-03-16
um, it's not vfat. My mistake. I forget if ```
 sudo mount /dev/sde1 /mnt 
``` is the correct code for fat [not fat32]

If not ```
 sudo mount /dev/sde1 /mnt 
```

---

### Post by scraze on 2010-03-16
Uh-oh, seemed I forgot to explain some important things! Mostly pertaining to the way the terminal works.

When you start a command, it takes over the terminal until it stops. If it isn't done yet, then everything you type gets sent to the command, instead of the terminal itself. So when using tail to follow a file:
```
tail -F /var/log/syslog
```
.. the only thing happening in your terminal is that the file /var/log/syslog (a text file) is displayed on your screen, and everything that gets written to /var/log/syslog also shows up on your screen. Anything you type is lost to tail; commands can use input, but they don't have to. In this case, tail ignores your input.

So before executing any other commands, make sure the last command has ended its task and has returned your terminal. In the case of tail, it will just keep running until you end it yourself; you can do this by pressing **Ctrl-C**. When the terminal is available, it always shows an easy recognizable line:
```

roddy@avithy:~$

```
When this line is at the bottom of the screen, you're ready to go.

Unfortunately all the commands you tried since the tail command never got executed. The only outputs you ever got were from lsusb and tail -F /var/log/syslog! Still, there is some useful information in there, so don't worry - we'll get there. The usb ID is 0402:5661, the device is recognized on a basic hardware level and some SCSI activity is going on. Now that it's more or less confirmed that the mp3 player is a mass storage device, we can focus on one path of troubleshooting - and it should be relatively easy! Ubunterooster has been exploring that path - with combined forces, who knows what we can accomplish! ;D

To make it a bit easier for us all, could you supply the output of these commands, with the player plugged in?
```

sudo lsusb -vd 0402:5661
mount
ls /dev/[sh]d*

```

Apologies for the brevity, I gotta go!

---

### Post by jokei on 2010-03-17
Hey guys, still no luck as yet I'm afraid, but thanks for bearing with me

Scraze:

Bus 002 Device 002: ID 0402:5661 ALi Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0402 ALi Corp.
  idProduct          0x5661 
  bcdDevice            0.02
  iManufacturer           3 ALi Corp.
  iProduct                1 Audio Player
  iSerial                 2 00101000101410066786
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              16
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
ben@benjohnson:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=ben)
ben@benjohnson:~$ ls /dev/[sh]d*

---

### Post by ubunterooster on 2010-03-17
```
 sudo mount -t fat /dev/sde1 /mnt 
``` or
```
 sudo mount /dev/sde1 /mnt 
```

---

### Post by jokei on 2010-03-17
Hey :)

ben@benjohnson:~$  sudo mount -t fat /dev/sde1 /mnt
[sudo] password for ben: 
mount: unknown filesystem type 'fat'
ben@benjohnson:~$  sudo mount /dev/sde1 /mnt
mount: special device /dev/sde1 does not exist
ben@benjohnson:~$

---

### Post by ubunterooster on 2010-03-17
```
 sudo mount /dev/sdb1 /mnt 
``` Sorry, I keep going back errantly to "e"

---

### Post by jokei on 2010-03-17
Says:
mount: you must specify the filesystem type

?

---

### Post by ubunterooster on 2010-03-17
I only have devices with fat32 not fat. Further, all of my reading also deals with fat32. If the following does not work I'll have to silently follow Scraze's helping you until I get more info.

```
 sudo mount /dev/sdb1 
``` OR ```
 sudo mount /dev/sdb 
``` OR ```
 sudo mount /dev/sdb /mnt 
```

Just guesses that I'm not sure if one will work but know it can't break anything.

---

### Post by jokei on 2010-03-17
Thanks for trying man, no joy with those commands, might get there - Thanks loads for your input.

---

### Post by scraze on 2010-03-17
Oh my, another important thing I should have explained! This time the first two commands got executed, but the last one did not:
```

ben@benjohnson:~$ ls /dev/[sh]d*

```

As I described the last time, the first part of that line (ben@benjohnson:~$) indicates that the terminal is ready for action. The command itself (ls /dev/[sh]d*) is entered correctly. There is only one thing missing.. You have to press Enter (or Return) in order to execute it! :}

I guess you knew that you need to press Enter or Return to make the command execute. Probably you just didn't notice how it didn't execute, because I never explained what it should do.

The command **ls** simply lists files. What we're trying to do with ls /dev/[sh]d* is to list every device in the directory /dev/ that either starts with a s or an h (specified by [sh]), followed by a d, and then followed by any number of alphanumerical characters. Here's my output for instance:
```

roddy@avithy:~$ ls /dev/[sh]d*
/dev/sda   /dev/sda3  /dev/sdb   /dev/sdc1  /dev/sdc6  /dev/sdd
/dev/sda1  /dev/sda4  /dev/sdb1  /dev/sdc2  /dev/sdc7
/dev/sda2  /dev/sda5  /dev/sdc   /dev/sdc5  /dev/sdc8

```

The reason this information is useful, is because each physical disk gets assigned a node with its own letter. So, in my case, I have 4 different disks; sda, sdb, sdc and sdd. Each of these disks can have its own number of partitions; my first harddisk sda has 5 partitions, the second (sdb) just 1, sdc has 6 partitions and finally sdd is partitionless. 


Now that you know what kind of output you should expect from ls, please enter it again and make sure it executes ;)!
```

ls /dev/[sh]d*

```

By the way, the other information you supplied indeed confirmed your mp3 player is a mass storage device, which means it should be relatively easy to fix. Just hang on! 

p.s. also, you asked where you could find the syslog; it's in /var/log. A lot of other interesting files in there as well (messages for instance)!

---

### Post by jokei on 2010-03-17
:)  Thankyou.

Added that last command again and got this:

/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdb1

---

### Post by scraze on 2010-03-17
Well! The output shows that indeed the disk we're looking for is /dev/sdb1. Ubunterooster already knew that, because he didn't look over the output of step 4 you gave on the previous page.. *shamy blush*

All we need to accomplish at this point is to mount the device node to a directory you can access. The commands ubunterooster provided should have accomplished that, so there may be some kind of kink in the road - the critter of randomness may still be afoot! But not for long.. ;)

First, we need to make sure what kind of filesystem we're trying to mount. Normally mount can figure out what filesystem it's looking at by itself, but apparently that's not working too well. So let's just list the partition table:

```

fdisk -l /dev/sdb

```

The output should list the first partition (/dev/sdb1) and it's type. That should provide us with the final ammunition; if it's indeed FAT16 or FAT32, then ubunterooster's line should work:

```
sudo mount -t vfat /dev/sdb1 /mnt
```

If it doesn't return an error, then you should be able to explore the player by filebrowsing to /mnt. If it does return an error, then it should describe exactly what the problem is! :}

---

### Post by ubunterooster on 2010-03-17
"fdisk -l" memorized now, thanks! [Regains confidence] :-D

---

### Post by jokei on 2010-03-18
Still working away, but that just returned.

Cannot open /dev/sdb

---

### Post by scraze on 2010-03-18
Oops!

One of these things might have happened; 
1. ubuntu probably needs superuser permissions (ie. sudo) for fdisk
2. the player wasn't recognized yet 

It's probably the first, but in order to exclude both from being possible, let's first make sure that the player is plugged in and recognized.
```

ls /dev/sdb1

```
This should return a line simply saying '/dev/sdb1'. If it's not there, try 're'plugging the player, wait for a few seconds. 

When /dev/sdb1 is there.. well.. let's try the correct command :D I assumed fdisk could be executed as a normal user but forgot to verify, but in retrospect, partition table information is not the kind of data you want every user to be able to access (it's in the relatively sensitive MBR part of the harddisk). So with further sudo instead of ado:

```

sudo fdisk -l /dev/sdb

```
 
:)

---

### Post by jokei on 2010-03-18
:)

PROGRESS!!!

Disk /dev/sdb: 4202 MB, 4202168320 bytes
130 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 8060 * 512 = 4126720 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     4102509    c  W95 FAT32 (LBA)

---

### Post by scraze on 2010-03-18
Yay! Everything we need to know has been confirmed - player is recognised on a USB level, then initialised as a mass storage device at /dev/sdb with one partition at /dev/sdb1 of type FAT32.. All that's left to do is to make sure it mounts.

To make use of the partition types FAT16 and FAT32, Linux uses a module called vfat. To see whether that module is loaded & ready to be used, we can list all the modules currently active with lsmod. Additionally we can simply try to load it with modprobe, and try an lsmod again to see whether this has changed anything:
```

lsmod | grep fat
modprobe vfat
lsmod | grep fat

```

If the lsmod output shows a line starting with the word vfat, then we should be all set to do:
```

sudo mount -t vfat /dev/sdb1 /mnt
mount

```

If the randomness is still alive, he's cowering in a corner now.. :P


PS. Have you been typing over the output each time? If so, I commend your efforts! :O and it occurred to me that it may not be logical that you can copy the output simply by selecting it, and paste it by middle-click. It's kind of a second clipboard (differing from the clipboard used by ctrl-c / ctrl-v). In case I'm mistaken, nevermind ;p

---

### Post by jokei on 2010-03-18
Ah, it was looking good...
But then I got this 

Typing over the output?  Copy/paste.

---

### Post by scraze on 2010-03-18
Oh no, I did it again :( forgot to prefix with sudo! Initializing kernel modules is something you need superuser permissions for (that's generally a good idea, because of the importance of the kernel :p). Listing the modules with lsmod is allowed for normal users, but modprobe is only for root and sudo'ers.

So it should have been:
```

sudo modprobe vfat
lsmod | grep fat

```

Apologies for the mistake! And for the weirdness of thinking you were typing over the output - I must have misinterpreted some missing lines. Never mind :P

---

### Post by jokei on 2010-03-18
Don't worry about that at all, I just appreciate the help.

Right, here's the screenshot.

---

### Post by scraze on 2010-03-18
There we go.. the module wasn't loaded at first, and now it is. Generally this should mean you can mount FAT16 and FAT32 partitions now..

Fingers crossed for an attempt to make mount detect the partition type itself:
```

sudo mount /dev/sdb1 /mnt

```

If that returns this error:
```

mount: you must specify the filesystem type

```

- then we will simply specify the filesystem type:
```

sudo mount -t vfat /dev/sdb1 /mnt

```

and if one of those does not return an error, let's see how it's mounted:
```

mount

```

Cue the drumroll!

---

### Post by jokei on 2010-03-18
Getting there?

---

### Post by scraze on 2010-03-18
That can't be right.. It still didn't mount. Did you by any chance reboot? In that case, we probably lost the vfat module.

If not, something may be wrong with the partition.. that would be nasty.

```

lsmod | grep fat # to check whether vfat is still loaded
sudo modprobe vfat # never hurts to modprobe
fsck.vfat -v /dev/sdb1 # lets examine this puppy!

```

That should give us some information. The command fsck.vfat is like a disk checking utility - it checks whether the filesystem is validly vfat.
Hope the partition is ok!

---

### Post by ubunterooster on 2010-03-18
In my player, there is no music on it! I stick it all on the removable SD card because the cards are less likely to develop problems. Thought that may be of consideration if you continue to have problems, since I know your player has a microSD slot.

---

### Post by jokei on 2010-03-19
No, didn't reboot...

If there's a SD slot on my player it's well-hidden...  very well hidden :)?

---

### Post by ubunterooster on 2010-03-19
The link you gave said it has one...

microSD slots are easily hidden. The hole is slightly smaller than my pinkie finger-nail. It may be near (or even in!) the USB port.

---

### Post by jokei on 2010-03-19
Ah, really?  You live, you learn - I was thinking it'd be the size of the one in my phone!

:confused: :o:redface:

---

### Post by ubunterooster on 2010-03-19
There are three sizes: SD, miniSD(common one for phones), and microSD.

---

### Post by scraze on 2010-03-19
oh hai! Meant to reply earlier, but ran out of time.

Either way, this .. should be the last time I forget to prefix a command with **sudo** .. I'm thoroughly ashamed now :} not quite the first time I forgot.

As you by now understand, the "permission denied" you received as an output was because fsck.vfat (like fdisk) needs superuser permissions, which we get with sudo. 
Just in case we lost the vfat module (ie reboot, unlikely), I've added the modprobe vfat also.

```

sudo modprobe vfat
sudo fsck.vfat -v /dev/sdb1

```

By the way, the SD-card thing is not a bad idea.. I have a Creative with a SD slot and - though there is plenty of space - it's really nice to use SD's as a kind of cd's. But instead of about 12 songs, it fits 1200.. Well, you know :)

However from a technical standpoint, mounting a SD-card is done exactly the same way as your player (both are Mass Storage devices), so if you can use SD, you should be able to use your player. It's particularly great as a temporary solution, I guess.

Fsck.vfat to the rescue?

---

### Post by jokei on 2010-03-20
Ok, small problem - definitely can't afford an SD card :( - although new job soon, so that will change, although I may just invest in a player that WILL work with Xubuntu :)

---

### Post by ubunterooster on 2010-03-20
Looks to me like there is a partition with a size of...zero?

I reccomend a SanDisk Sansa player. I've used an e250, a Fuse, and a Clip. Both the Fuse and the Clip are inexpensive lines that continue.

---

