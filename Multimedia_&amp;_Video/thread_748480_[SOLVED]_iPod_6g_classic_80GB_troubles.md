---
title: "[SOLVED] iPod 6g classic 80GB troubles"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by psylocat on 2008-04-07
Howdy all, \

After trying coutless how to's posted on these forums and elsewhere, all of which were awesome but none of which worked for me in the end, I've decided to try posting to see if anyone can think of a solution. I'm running gutsy, I have an iPod classic 6g 80GB, and I've tried using Rhythmbox, Amarok, and GKTpod to no avail. The main how-to's I've been refering to are:



**1.**

> This is an addon to the previous instructions.
This is what it took to get the new iPOD nano (3rd gen) working on my system. [Kubuntu 7.10]

EDIT//NOTE:
After trying the instructions from the original post, the 'ipod-read-sysinfo-extended' command would not work (command not found).
I would uninstall libgpod ('sudo apt-get remove libgpod2') first before re-trying. Then continue w/ the following steps:

1. Download libgpod-0.6.0.tar.gz
Code:

cd ~/Desktop
wget [http://superb-east.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.6.0.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.6.0.tar.gz)

2. Uncompress libgpod...
Code:

tar -zxvf libgpod-0.6.0.tar.gz
cd libgpod-0.6.0

* Don't change out of this directory 'till we're done.

4. Attain dependencies before install:
Code:

sudo apt-get install build-essential libglib2.0-dev libgtk2.0-dev libsgutils1-dev checkinstall

5. Build dependencies for libgpod, but don't install libgpod:
Code:

sudo apt-get build-dep libgpod2

6. Compile libgpod!
* should still be in ~/Desktop/libgpod-0.6.0/ directory
Code:

./configure 
make

7. Now we build a debian install:
Code:

sudo checkinstall

You'll get a prompt that says: "should I create a default set of package docs?"
Just press Enter to say YES.
On the next screen, type "Compiled libgpod-0.6.0".
Press enter again. This is what will show up:

Code:

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ you@yourcomputer ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ libgpod ]
3 -  Version: [ 0.6.0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libgpod-0.6.0 ]
9 -  Alternate source location: [  ]
10 - Requires [ ]

Enter a number to change any of them or press ENTER to continue:

Type 2, (to edit Name) press Enter.
Enter "libgpod2" at the prompt (w/o Quotes). It should now look like this: 2 - Name: [ libgpod2 ]

Press Enter to commit the changes. The package will get automatically installed.

8. For some reason this didn't seem to install the package for me.
( 'ipod-read-sysinfo-extended' command not found -- wasn't installed w/ libgpod2)
So i had to run the following command to really install it apparently
Code:

sudo make install

9. Okay one last thing: we link the libraries:
(it is right: .3 -> .2 and .3 -> .3 )
Code:

sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3

Now your system has libgpod v0.6.0 installed!!

10. Remove/Install Amarok (to be safe):
Code:

sudo apt-get remove amarok
sudo apt-get install amarok

or
Code:

sudo aptitude reinstall amarok

if you have aptitude installed

11. Plug in your iPod. Wait for it to be recognized (ie shown on desktop)..
(If the icon on the desktop doesn't show a small triangle in the corner, right-click the icon and select 'Mount'.)
Code:

df

Find your ipod in that list. Mine looked like this:

    /dev/sda1 /media/IPOD

(Mine actually was /media/iKJK from naming it as such when restoring it with iTunes)

12. There's a slick little script you have to run that came with libgpod:
Code:

ipod-read-sysinfo-extended /dev/sda1 /media/IPOD

**Make sure you swap out /dev/sda1 with whatever your ipod is actually connected to!**
This script will add an XML file called sysinfo-extended onto your ipod's config directory; it's what libgpod uses to 'see' your ipod's firewire device ID, serial number, etc.


    In my case I entered
    Code:

     ipod-read-sysinfo-extended /dev/sda1 /media/iKJK

    and got an error that it couldn't mount Device

    But entering the same with an appended / worked!
    Code:

     ipod-read-sysinfo-extended /dev/sda1 /media/iKJK/


13. On my system this worked perfectly.
On a friends system i had to 'sudo' that last command -- unsure why.

14. Start Amarok.
i. Devices tab (bottom left usually)
ii. Near top of Devices Panel, select IPOD (may be hidden w/ >> arrows) & select your iPod model.

15. Transfer songs to iPod.
Click-Drag-Drop songs to playlist or directly to Devices tab and from playlist to device.
This will Queue the songs for transfer.
Click the Transfer button.

16. Disconnect iPod from Amarok
the disconnect command wouldn't unmount my iPod, so i right-clicked the desktop icon and 'Safely Remove' it.

17. Phyiscally remove iPod from USB.

You should see your tracks on your iPOD now!!




**2.**

> here's how to get it working (type this into terminal one line at a time, use the same terminal session for all):

Code:

sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
aptitude install libgpod3 libgpod-common

if you use rhythmbox:
Code:

aptitude install rhythmbox

if you use amarok:
Code:

aptitude install amarok

if you use gtkpod:
Code:

aptitude install gtkpod

then:
Code:

aptitude remove libgpod2

this may prompt you to remove the ubuntu-desktop package, don't worry - it's only a meta-package

then check if it works. if it does run
Code:

rm /etc/apt/sources.list
mv /etc/apt/sources.list.tmp /etc/apt/sources.list
apt-get update

Banshee not supported (it uses it's own library rather than libgpod)



So, the error message I'm getting in Rhythmbox when trying to transfer music to my ipod is as follows:
Could not open file "/media/PSYLOPOD/iPod_Control/Music/F36/01 Losin You.mp3" for writing.

And in Amarok, when trying to connect to iPod:

Media device: Failed to create lockfile on iPod mounted at /media/PSYLOPOD: Read-only file system

Thanks!!

---

### Post by cozmicharlie on 2008-04-07
I hate to point you to another How To but I will anyway - maybe this has something that will help you.

[http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/](http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/)

---

### Post by psylocat on 2008-04-07
Thnks for the reply cozmicharlie, 

I tried this, managed to successfully follow all the instructions, but in the end, when trying to transfer music, gtkpod gave a similar error message:

"Transfer of 'Losin You' failed. Error opening '/media/PSYLOPOD/iPod_Control/Music/F17/gtkpod097942.mp3' for writing (Read-only file system)."

Could this have something to do with the fact that the iPod was originally formatted using an iBook??

Thanks again!

---

### Post by cozmicharlie on 2008-04-07
It could - I found this on another thread with a person getting the same error message. Iit sounded similar to what you are experiencing.  

[COLOR="Navy"]"fIgured this one out the other day...
What worked for me was...
I was using my mac to sync with my ipod
I plugged it in to my Windows I-tunes and clicked "restore"
that restores the ipod's software (or firmware?) to what it was originally shipped with.
i don't know that the "windows" part was required or if doing the same thing on your mac would work but i do know that a windows ipod is different than a mac ipod for some reason.
hope this helps"[/COLOR]

---

### Post by psylocat on 2008-04-08
Wooohhhhoooooo. Thanks cozmicharlie, michele, and Digitallysick. After about 20 hours of sweat and toil, I now have a functioning iPod classic sixith generation 80GB. Just to throw it out there, the combination that worked for me was:

1. Follow the steps here: [http://www.soccio.it/michelinux/2008...-gutsy-gibbon/](http://www.soccio.it/michelinux/2008...-gutsy-gibbon/)

2. Use a mac computer to restore iPod to factory settings, then use the terminal to do the following
> 
diskutil disableJournal /dev/diskXs3 where /dev/diskXs3 is the device assigned to the iPod. The "diskutil list" command shows you which device it in OS X the iPod is using. In my case, it was /dev/disk1s3.  ---thanks to Digitallysick  

I really appreciate all the help, and raise an extended middle digit to apple (although I love the ipod itself)

Cheers!

---

### Post by godd4242 on 2008-04-15
> **psylocat said:**
> Wooohhhhoooooo. Thanks cozmicharlie, michele, and Digitallysick. After about 20 hours of sweat and toil, I now have a functioning iPod classic sixith generation 80GB. Just to throw it out there, the combination that worked for me was:

1. Follow the steps here: [http://www.soccio.it/michelinux/2008...-gutsy-gibbon/](http://www.soccio.it/michelinux/2008...-gutsy-gibbon/)

2. Use a mac computer to restore iPod to factory settings, then use the terminal to do the following
  ---thanks to Digitallysick  

I really appreciate all the help, and raise an extended middle digit to apple (although I love the ipod itself)

Cheers!

That link is no longer active.

---

### Post by cozmicharlie on 2008-04-16
Try this [http://www.soccio.it/michelinux/category/linux/](http://www.soccio.it/michelinux/category/linux/)

Enjoy

---

