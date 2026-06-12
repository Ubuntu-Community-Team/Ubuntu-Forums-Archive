---
title: "MythWeb"
date: 2008-10-04
forum: Mythbuntu
---

### Post by Buschbarber on 2008-10-04
I am using Ultimate 1.9 and MythTV. MythWeb is installed, but when I click on it, it wants me to add links.

How can I set MythWeb up so I can use it?

I am not very Linux literate, so be gentle!!

---

### Post by newlinux on 2008-10-04
do you mean mythbrowser?

---

### Post by Buschbarber on 2008-10-04
It is called MythWeb on my system. I do not know how that differs from Myghbrowser. If you Google search for MythWeb, you will see.

---

### Post by Buschbarber on 2008-10-05
The icon in the MythTv Frontend is titled MythWeb, but when I click on the icon, a blank window appears with "MythBrowser: Select a group or single site to view" listed at the top.

I am not sure what I need to add, via the MythWeb Utilities

---

### Post by paulg on 2008-10-09
Just looked this up today for myself. See here:

[http://svn.mythtv.org/trac/browser/branches/release-0-21-fixes/mythplugins/mythweb/INSTALL](http://svn.mythtv.org/trac/browser/branches/release-0-21-fixes/mythplugins/mythweb/INSTALL)

---

### Post by newlinux on 2008-10-09
Mythweb is the web server that allows you access your myth installation over the web.

[http://www.mythtv.org/wiki/index.php/MythWeb](http://www.mythtv.org/wiki/index.php/MythWeb)

Mythbrowser allows you to browse the web from inside myth. I don't use mythbrowser (I do use mythweb) but I think you need to configure it with some links first

[http://www.mythtv.org/wiki/index.php/MythBrowser](http://www.mythtv.org/wiki/index.php/MythBrowser)
[http://www.mythtv.org/wiki/index.php/MythBrowser/Readme](http://www.mythtv.org/wiki/index.php/MythBrowser/Readme)

Both are available as plugins that can be installed via apt.I think you are talking about mythbrowser if what you want to do is browse the web from inside mythfrontend. I think you need to add some links first... Have you tried adding links?

---

### Post by Buschbarber on 2008-10-09
If MythWeb is supposed to be a way of Remote Controlling the MythWeb machine, then what is the MythWeb icon for in the MythTV Frontend? When I go into Settings, for MythWeb, in the MythTV Frontend, it is looking for links to be set up. What should go in there?

---

### Post by newlinux on 2008-10-09
I would guess you put links in there... I don't know why they call it mythweb in the frontend icon - I don't use it, not sure how many people do. When I want to browse the web on my myth machines I just fireup firefox and use a wireless keyboard. I tried mythbrowser way back and found it cumbersome. That's probably why it's due for a re-write in the next version of myth.

Have you gone into the settings to configure it yet? Maybe you have to input some links in the settings first.

---

### Post by Buschbarber on 2008-10-09
I use Firefox, as well.

Despite the MythWeb Icon, it does call it MythBrowser in the Settings screen.

I looked over the Apache config file and it is configured for some settings.

The directory is /var/www/mythweb

What does it mean when a folder has a Bent Arrow attached to the top? It reminds me of the Shortcut icon in Windows.

---

### Post by newlinux on 2008-10-09
> **Buschbarber said:**
> I use Firefox, as well.

Despite the MythWeb Icon, it does call it MythBrowser in the Settings screen.

I looked over the Apache config file and it is configured for some settings.

The directory is /var/www/mythweb

What does it mean when a folder has a Bent Arrow attached to the top? It reminds me of the Shortcut icon in Windows.


Sounds like you have mythweb and mythbrowser installed (/var/www/mythweb is the default directory for mythweb). Not sure what bent arrow you are referring to (probably because I barely ever use file browsers - I'm mostly a commandline guy for file browsing). Where do you see it (in what application for what folder?)

---

### Post by Buschbarber on 2008-10-09
/var/www/mythweb

The mythweb folder, in Icon View, has an arrow attached to the upper right corner of the folder that is bent to the left.

/cdrom has an arrow that is in the bottom left corner of the cdrom folder and it curves down, at a 45 deg angle, to the right.

These are just examples

Some folders have a Red X on the corner.

---

### Post by Buschbarber on 2008-10-09
How do I access MythWeb from another PC?

---

### Post by newlinux on 2008-10-09
If you have installed and configured to the defaults:

[http://master_backend_machine/mythweb](http://master_backend_machine/mythweb)

So my master backend is named evangemyth:

[http://evangemyth/mythweb](http://evangemyth/mythweb)

On a LAN. Or you can use the IP address of the master backend instead of the machine name.

---

### Post by Buschbarber on 2008-10-09
I am not sure what userid and password it wants.

By the way!!

I have a USB box attached to my Ubuntu machine. The USB box has an HD with an XP OS (NTFS). I cannot connect to it to extract files.

Do you know how?

---

### Post by newlinux on 2008-10-09
do you use mythbuntu-control-centre? In there you can configure the username and password for mythweb.

Your external drive should automatically mount. What happens when you try to connect to it? how are you trying to connect to it.

---

### Post by Buschbarber on 2008-10-09
I do have the Mythbuntu Control Center. I will give that a try.

I have two 160Gb IDE drives that I used to have XP on. I am using them with an External USB box that I have used in the past to copy files to and from my Windows machine. This is the first time I have used it with Ubuntu. When I install an HD, in the box, and plug the USB cable into my Ubuntu machine, I get an error message - Cannot mount volume - Unable to mount volume. Under Details, it says - $LogFile indicates unclean shutdown (0, 1) Failed to mount '/dev/sdb1'; Operation not supported Mount is denied because NTFS is marked to be in use 

It says to type in

mount -t ntfs-3g /dev/sdb1/media/disk -o force

Ubuntu apparently does not like the syntax

---

### Post by Buschbarber on 2008-10-09
I might have made a syntax mistake. It is hard to discern spaces when code is printed out in small letters.

sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force

It returns an error - fuse; failed to access mountpoint /media/disk: no such file or directory

---

### Post by newlinux on 2008-10-09
try:
```

sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force

```

Sounds like the NTFS drive was shutdown "uncleanly" with a flag set that is interfering with mounting.

---

### Post by Buschbarber on 2008-10-09
I did that and now I have an icon on the desktop labeled "Disk". When I try to Open it, an error message comes up stating that it "Cannot open /media/disk as there is not application installed for this file type"

When I plug in the USB cable for the HD box, a 160Gb Media icon appears, however, when I open it, only a folder is there labeled "System Volume Information"

---

