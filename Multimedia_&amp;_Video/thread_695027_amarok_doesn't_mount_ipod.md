---
title: "amarok doesn't mount ipod"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by jay3712 on 2008-02-12
Sorry to bring this up again as I've seen a lot of iPod posts, but Amarok refuses to recognize my ipod. (older 20 gb, no video/pics).
 1. Ubuntu automatically mounts the ipod at /media/IPOD
 2. When I manually navigate to a song on the iPod, Amarok will play it no problem.
 3. I've tried manually adding the device in the settings>media devices menu
 4. Autodetect says Amarok found no media devices
 5. Despite #4, with Amarok not running, it starts up when I connect the iPod, just like I want it to, but still no access to the iPod.
 6. I just did a fresh Gutsy install a week ago, and was running Gutsy at the time and both this iPod and my Shuffle were automatically recognized and worked like a charm.

Thanks for your help

---

### Post by jay3712 on 2008-02-14
Anybody have any ideas? My iPod is the only place I have all my music, and I loaded it onto the computer no problem last time. I even completely uninstalled and reinstalled Amarok.

---

### Post by TomGar on 2008-02-14
hi there

I was struggling too. But went into settings in amarok, clicked on media devices, clicked add device and then put in the mount point (ie /media/ipod) (actually I cut and paste this from the settings in gtkpod) then selected the plugin for apple ipod and named it something friendly and clicked apply and it's up and running (our ipod is a 4thgen photo)

In auto detect i got a message regarding hal and building it with kde etc (not very friendly)

Hope this helps.

---

### Post by jay3712 on 2008-02-14
Yea I tried that too, still get the same "no media devices found" error. It worked like a dream 2 weeks ago. WTF?

---

### Post by bismark on 2008-02-17
I have the same problem with two seperate iPods a 4th Gen greyscale and a 2nd Gen Nano.  Both are not autodetected however if I enter them in manually with a mount point of "/media/IPOD" they are then recognized.

---

### Post by jay3712 on 2008-02-20
OK, Rhythmbox sees the iPod and mounts it no problem, so I know it's not the iPod. I've tried manually entering it into Amarok with /media/ipod, but it still doesn't see it. Same results using my roommate's brand new Nano and my other roommate's video. This is unbelievable. Has anybody else had this problem? Am I missing some package that I need for Amarok?

---

### Post by tailStrike on 2008-02-22
Just connecting my ipod mini for the first time tonight and thought I'd share that after manually adding an entry in fstab for it granting rw access, it seems to be working fine:

```
sudo mkdir /mnt/ipod
```

then edit /etc/fstab to add this line:

```
/dev/sdb2	/mnt/ipod	vfat	rw,user		0	0
```

Note that my ipod was formatted to fat32 for windows use.  Kinda remember reading something back in the day that said this is necessary for linux, too but I could be wrong.  If the thing will mount the stock apple filesystem, you could try using 'auto' in place of 'vfat' in fstab.

Also note that if you get the warning about lock existing after pressing connect, choose "Remove".  This is apparently something to do w/ file left from ungraceful dismount.  If you mounted your ipod properly with rw permissions, you should get past this warning with no issues.

Anyways, turned out to be simple fix for me.  Would not be obvious to the Linux noob, so I thought I'd share.  I have a fairly vanilla install of kubuntu.

---

### Post by jay3712 on 2008-02-22
Thanks for the reply tailstrike. I haven't changed a single thing since my last post, but when I just plugged the iPod in and it isn't recognized by the computer at all. I also plugged in my 2GB flash drive and it has a little light that turns on when it's plugged in, but it is just flashing now and I can't see that either, while my usb mouse works fine. So now it seems I have some sort of issue with my usb ports. Reboot didn't help. 
Thinkpad T40 by the way.
Edit: found this on[ thinkwiki]("http://thinkwiki.org/wiki/Problem_with_USB_2.0"). Dunno if it could be relevant.
Edit2: yep, if i prop up one corner of the thinkpad the usb ports work fine. I'm sure that it is related to the above. However, even if USB2.0 is working, amarok still doesn't see my ipod.

---

### Post by SirThom on 2008-03-22
I'm a n00b myself, I was having the same problem as you with amarok recognising my shuffle.  However, whenever I plugged it in, something called Music Player popped up.  I mainly listen to podcasts on my shuffle and I found out that Music Player understood what to do with them so I used that instead.  If you don't have Music Player installed (I don't know if it's installed by default) then you might give that a shot.

P.S. This happened only moments ago.  I found your post while searching for posts by other people having trouble getting their ipod to work in amarok.

---

### Post by bfkeats on 2008-04-26
Anyone?

---

### Post by Xintron on 2008-05-04
I solved the problem by deleting the "iTunesLock" from the "iPod_Control->iTunes" folder and then manually adding it to amarok :) Might help you :)

---

### Post by 12barz on 2008-05-05
Having the same problem.  Hardy sees the ipod, rhythmbox loads it, Amarok doesn't.  I've tried deleting iTuneslock.  I've tried manually adding the ipod.  No good.  I've tried using Synaptics to "completely remove" Amarok.  And reinstalled it.  Curiously, on the reinstall, my library was still there and my manually added (but nonfunctional) iPod entry was still in the devices tab.  Tried removing amarokrc from /etc/kde3 and doing complete removal/reinsstall.  Same thing.  Is there some hidden configuration file somewhere for amarok that I'm missing?  I was hoping that if I could get a completely virgin, fresh reinstall of Amarok, that whatever problem I'm having with the iPod would magically vanish.  Lately, magic is not my friend.  Meanwhile, I'm keeping my iPod afloat with Songbird, but I sure do like Amarok better.  Help?

---

### Post by KevNice on 2008-05-07
same problem here. It actually says "iPod mounted at /dev/sdb2", but when I try to connect it says "no mounted iPod found". :confused:

---

### Post by 12barz on 2008-05-12
Bump!  Please help us, ye mighty linux audio/amarok gurus wherever ye may be.

---

### Post by soxs on 2008-05-12
Give me the *exact* error msgs you get when trying to connect to your ipod.

The general first step would be to redetect your ipod with the amarok preferences menu (last tab).

Check whever where the ipod is actually mounted (output of mount) and where amarok searches for the iPod. the mount places varies when reconnecting rebooting (I use labeled mount instead and it works pretty fin 8GB black nano Gen 2) (see [http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/) for correct labeling of your second (2nd!!) partition, normally sdb2 or sdb2 or sdc2 or sdd2 or..).

Some of you might get it working with some of the tweaks mentioned in that thread: [http://ubuntuforums.org/showthread.php?t=497201&highlight=iPod+gnome+eject](http://ubuntuforums.org/showthread.php?t=497201&highlight=iPod+gnome+eject) (complete read through required)

OMG, I overread you use gutsy.. there the iPod / Amarok support is messed up as hell; I did not manage to find a way to get around that f***in bug, except, manually defining the mountpoint everytime I connect my ipod. Sry. the easiest wasy would be to upgrade to hardy, which in general is a step forward.

---

### Post by planejason on 2008-05-23
I had the same problem in Hardy after installing Amarok.  I found that installing kdebase-kio-plugins (sudo apt-get install kdebase-kio-plugins) solved the autodetect problem for me in Hardy.  I found this here ([https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384))

 Detective_Librero wrote on 2008-03-27: (permalink)

I had this same problem and also had to install package kdebase-kio-plugins in order for Amarok to detect my iPod (in [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/66764](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/66764) the package appears to have been set a dependency of Amarok, but it is not now :-S ).

Hope this helps someone.

---

### Post by soxs on 2008-05-23
thx, were not aware of that fact

---

### Post by Ignotser on 2008-06-29
Still looking for a fix, I'm experiencing the same issues with my Ipod and Amarok.

---

### Post by soxs on 2008-06-29
> **Ignotser said:**
> Still looking for a fix, I'm experiencing the same issues with my Ipod and Amarok.

You should add to which post you refer, which problem you have...

---

### Post by edog76 on 2008-07-02
I have found a method for accessing my iPod.  I installed the KDEbase file listed above, and then manually entered my iPod by name, from the Settings >> Confirgure Amarok >> Media Devices.  I left the mount point blank and it worked with no trouble.  I didn't even have to hit the connect button back at the main window.

Still works after restarting, so looks like a permanent fix (for me at least).:guitar:

---

### Post by guyborg on 2008-07-09
Was having the similar problem.  OS sees and mounts IPOD but Amarok does not.  Tried this and it worked for me.

go to Amarok -> settings -> configure Amarok

then

Media device tab

Tried auto detect which did not work so then selected add device.

filled in 3 fields as follows.

Plugin - Apple IPOD media device
Name - IPOD
Mount Point /media/IPOD (copied from /etc/fstab) when IPOD is mounted.

---

### Post by jwalker on 2008-07-15
> **planejason said:**
> I had the same problem in Hardy after installing Amarok.  I found that installing kdebase-kio-plugins (sudo apt-get install kdebase-kio-plugins) solved the autodetect problem for me in Hardy.  I found this here ([https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384))

 Detective_Librero wrote on 2008-03-27: (permalink)

I had this same problem and also had to install package kdebase-kio-plugins in order for Amarok to detect my iPod (in [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/66764](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/66764) the package appears to have been set a dependency of Amarok, but it is not now :-S ).

Hope this helps someone.

Thanks to you guys, I have installed the kdebase-kio-plugins and I could see my iPod straight away. 

Also having this package as a Amarok dependency in the past but not any more (since Gutsy?) would be a PREFECT reason as to why my iPod did not work anymore, when I have not changed my methods from when it did work (Feisty). How that change got approved I could not guess, but hopefully the great people that makes this distro know about it. 

Thanks again!

---

