---
title: "Ubuntu 13.04 64-bit Harmony 650 remote - how do I set it up?"
date: 2013-12-09
forum: Multimedia Software
---

### Post by squakie on 2013-12-09
I've searched on the web and the only things I found out are:

(1) Logitech's site for programming the remote doesn't work wih this version of FIrefox

(2) Something call Congruity.

I installed congruity and now have no clue what I'm supposed to do. 

What I was *hoping* I could do:

- set the Logitech Harmony 650 remote to control my Pi media center (MS xbox dvd remote def works in XBMC with other remote), my TV, my Comcast DVR cable box and my surround sound/dvd piece of equipment.  I say "my", but this is for my sister and brother in-law.  I've got the Pi media center working great now, so I want to give them a universal remote that does everything.  The 650 seems like it would be ok for them to use, and it will replace a wireless mouse and 3 other remotes.

I was hoping this meant just looking a piece of equipment, like the TV, up on Logitech's site and have it give me a code or do whatever to program the remote.

Perhaps this is beyond what I was thinking?  I am a total novice at this remote also.

Thanks.

---

### Post by Kirboosy on 2013-12-09
Congruity is apparently a replacement for the Logitech plugin for Firefox.

[Logitech Harmony One]("http://ubuntuforums.org/showthread.php?t=1704890&p=10951949&viewfull=1#post10951949")

See if that post helps you at all. I don't personally own a Harmony remote but my father does. I am sure I could snag his for a few hours to play with it one weekend.

Hope that helps!
~Caboose

---

### Post by SeijiSensei on 2013-12-09
I've only been able to program my Harmony 700 successfully from Windows.  I tried once using a Windows VirtualBox VM to program it, but I could never get the application to see the remote over the USB connection, even with the proprietary extensions for VirtualBox installed.  I eventually just booted a copy of Windows and ran Firefox from there.

Logitech used to distribute a Windows application to program their remotes, but they have switched to an entirely web-based approach.

---

### Post by squakie on 2013-12-09
Hummmm.....don't see Congruity in the add-on list in Firefox, and I don't know how to add it.  It doesn't show in a search of the add-ons stie either.

I would try my small XP install I've been using to scan in videotapes, but there seems to be a problem with it.  I had to completely wipe my PC in order to make room for XP (didn't see anyway to shrink the linux partition(s) and no way to make the Windows partition the primary).  After doing so, I did the typical install Windows, defrag a couple of times, then install Ubuntu with no problem.  Went back to the bare XP SP2 install, added SP3 then added my wifi driver and then the fun started.  The very first thing I did was make sure the skimpy windows firewall was at least running, then downloaded Microsoft Security Essentials for XP only to have it hang when it was updating the database.  Can't run Windows update anymore either.  If I didn't know better I'd swear something happened to the activation but yet no messages or that silly little gold key show.  Think I'm going to completely reinstall again and see if it works or not.

Maybe I'll just try the VM thing first - I think the current downloads with the add-ons pack for virtualbox support USB so I'll see.  I know I have other devices that don't work through the USB on virtualbox because of the way they manipulate things at the low level.  I've done some coding with libusb-dev in Ubuntu myself and can see how it could be a challange to implement via a VM.

EDIT:  I should add that when I try to start Congruity gui there is nothing in the Unity menus for it even though I installed it.  If I start congruity via the command line it wants a file name - I assume the binary file to actually program the remote with, which is rather difficult to get considering I can't get logitech's site to work with the linux version of Firefox (the site is expecting Windows or Mac).

---

### Post by squakie on 2013-12-09
I just tried the user agent switcher and setting to IE 8.  That at least got me so I could set up an account.  The next step was to download and add Silverlight and some other .exe for their browser externsion.  Looks like I will need to use Windows ;(.  Oh well.  Someday the vendors will catch up.

---

### Post by SuperFreak on 2013-12-09
Congruity is in Software Centre.

---

### Post by squakie on 2013-12-10
> **SuperFreak said:**
> Congruity is in Software Centre.

Se post #1 = "installed Congruity"........

---

### Post by squakie on 2013-12-10
Well, I'm batting 1000.  Installed Virtualbox from Oracle's site, made in XP Pro SP3 VM, installed the additions "pack", but still can't enable USB 2.0, and it appears the device or their add-on or something must require it.  Ubuntu sees the device via lsusb as:```
Bus 007 Device 003: ID 046d:c122 Logitech, Inc. Harmony 700 Remote
```
even though it is a 650, but Ubuntu does see it on the USB.

I have an empty filter in the USB setup for VirtualBox as when I've used it in the past that was all I needed.

Logitech's add-on to Firefox just isn't finding it.

Back to the drawing board or write it off as a big chunk of change down the toilet?  ;)

---

### Post by squakie on 2013-12-10
Ok. one boo-boo.  Installed add-ons but not the extension pack.  Installed the extension pack - now the USB 2.0 controller is recognized.  However, the Harmony plugin never finds my remote yet.  I bought it used so I didn't get a cable with it, but I'm using a micro-usb cable that I assume must be more than just a "power" cable in that Ubuntu sees the device.  Back to more hunting, but I'm not really sure where else to look.

---

### Post by squakie on 2013-12-10
Okay, here I sit.  Ubuntu 13.04 64-bit host, Windows XP Professional SP3 running in the latest Virtualbox from Oracles' site.  Installed the guest additions, installed the extension pack.  USB 2.0 controller is enabled. vboxuser group is there and I am a member of the group.  The PC was restarted after adding me to the group.   For the running VM, the USB inidicator says "no captured devices".

I've looked online, I've looked at the vbox site, I've looked in the forums, but can't figure out what I haven't done that this isn't working.  I have seen it in many threads but they always say to make sure you are part of the vboxusers group (and rebooting - when a log off/log on would work) after adding your userid to the group.

I tried adding a filter with the manufacturerid and productid from lsusb - still no go.

Can anyone help me out here?

Thanks.

---

### Post by squakie on 2013-12-10
Got the device recognized.  3 reasons why it wasn't being found:  (1) I'm a bone head (2) I'm a bone head and (3) see 1 and 2.

Now I think I know why the person was selling the remote:  gets to 66% of the sync (actually writing from the web to the remote) and errors out.  Each time - 66%.  Hum....66%........probably bad memory (eprom or whatever they're using).

At any rate, I'm marking this as solved, as the only way to get to it was indeed to install XP in a VM, and im my case the update to IE 8 wouldn't finish, so I installed Firefox 25 in Windows as well, installed Silverlight, installed the Harmony software add-on to Firefox, made sure to allow the device by right-clicking the USB icon on the VM and clicking the device (ahem ;) ).

Not a problem with Ubuntu.

Now the problem is with the remote itself.

---

### Post by squakie on 2013-12-10
Okay, it worked!   Had to use a short USB cable to connect the remote to the PC.  This remote could grow on me - some day if I can afford one fo myself I'm going to get one.

---

### Post by Kirboosy on 2013-12-10
Awesome, glad it worked and you posted your steps along the way. I think they are fabulous remotes if you want a very nice all in one control for your media center. My dad loves his. (He uses Windows so he didn't have to use any wizardry to get it working)

Maybe you could edit your original post to make it easier for people to know what steps you took?

Thanks!
~Caboose

---

### Post by squakie on 2013-12-10
Had to use XP in a VM to do it - is it okay to post those instruction here since they aren't really ubuntu?

---

### Post by Kirboosy on 2013-12-12
I don't think anyone would have a problem with it. Especially since your host OS is still Ubuntu. The thread could get moved after you update it but it shouldn't get deleted. 

~Caboose

---

### Post by swt2c on 2014-04-04
Hi,

For future reference, you can use congruity/mhgui to update your Harmony 650 under Ubuntu without using a Windows VM.  If your remote uses members.harmonyremote.com, just go to the website, and when it downloads a file (Connectivity.EzHex or Update.EzHex) just open that file with Congruity.  If your remote uses myharmony.com, instead just run 'mhgui'.

---

### Post by cecilx22 on 2014-07-10
I can't seem to find 'mhgui' anywhere, even though I have congruity installed... help?

**edit**: never mind, I'm a twit...

---

