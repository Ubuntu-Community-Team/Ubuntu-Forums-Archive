---
title: "DVD rip does not work...(Music CD rip works...)"
date: 2007-10-13
forum: Mythbuntu
---

### Post by idanag on 2007-10-13
Hi.

Using RC (that was upgraded from Beta). 
64 bit AMD machine.

When I try DVD rip I see  
"No Jobs. Checking and or waiting for a DVD.¨

As I mentioned above Audio disk rip works just fine.

What Am I doing wrong ?

Idan

---

### Post by stevetv on 2007-10-13
are you able to playback copy protected dvds?  or are your problems related only to ripping them.  i believe it is some issue relating to permission restrictions???? but ive never used ubuntu before three days ago so i don't really know.

guess a guess.

---

### Post by superm1 on 2007-10-13
Yeah you probably need to install libdvdcss2.  Look in the mythbuntu-control-centre for how to turn it on.  You need this both for ripping and playing devices.

Also,
You might need to start mtd, but make sure that libdvdcss2 works first, and then starting mtd isn't much trouble at all.

---

### Post by lingenfr on 2007-10-20
You go Ames, IA... I have the same problem. I can play copy protected DVDs just fine, but the ripping fails at some point every time. I have tried it with a couple of DVDs and no joy.

---

### Post by andrewb78 on 2007-12-18
I actually cannot play or rip, but I do have libdvdcss2 installed.  How would I test whether it works?  I am on amd64 using the versions of myth at [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) (because it solved my PVR-350 TV OUT issue).

EDIT: I can play DVDs in VLC, for what that's worth.

---

### Post by andrewb78 on 2007-12-21
OK... I've done some digging here, and it seems that the problem might be with the DVD itself.  Some DVDs apparently use bad blocks as copy protection.  I may have a partial solution gleaned from elsewhere on the Internet, but I can't get the last part of it working.  Here is what I have tried so far.  I'm assuming that the normal things to read DVDs (i.e., libdvdcss2) are installed.

There is a shell script out there that will turn the DVD into an iso file while recovering from bad blocks.  You need to install a couple packages:

```
sudo aptitude install lsdvd gddrescue
```

Then, run the script you find at [http://www.mythtv.org/pipermail/mythtv-users/2007-April/175899.html](http://www.mythtv.org/pipermail/mythtv-users/2007-April/175899.html) (but note that the package you need is gddrescue, NOT ddrescue).  Edit the line starting with DEV to point to your DVD drive device (the provided /dev/dvd may well be correct) and the line starting with DIR to point to the directory where you want to store the iso.

Once the script has finished (which takes a few minutes), you should be able to use the ISO file in your media library as though you created the ISO through MythDVD.  However, I would also like to do the conversion to MPEG-2 (as though I ripped to Perfect quality) to take advantage of my hardware acceleration.  So, I eject the DVD and issue the following (assuming your DVD device is /dev/dvd):

```

sudo mv /dev/dvd /dev/dvd.bk
sudo ln -s /dev/loop0 /dev/dvd
sudo mkdir /dvdmount
sudo modprobe loop
sudo mount -t iso9660 -o ro,user,loop=/dev/loop0 /path/to/ISO/image.iso /dvdmount

```

(When finished with all this, you would:

```

sudo umount /dvdmount
sudo rm /dev/dvd
sudo mv /dev/dvd.bk /dev/dvd

```

but I am still working on this. :) )

The problem now is that going to Optical Disks -> Import DVD just yields the message "No Jobs.  Checking and/or waiting for DVD."

I have also tried changing /dev/dvd to /dev/loop0 in everyplace I could find within setup to do so, then restoring /dev/dvd to its original state (which is just a symlink to /dev/hda).  Same result.  I even tried putting the DVD back in the drive after that and still got the same result.  I have added global read and write permissions on the relevant devices also, which made no difference.

What can I do to get the ripper to recognize /dev/loop0 as the DVD device?  I know the major, minor numbers are different; does MythDVD check?  Is there some other workaround?  Can I just get mtd to rip from something besides /dev/dvd without even going through the menus?

---

### Post by andrewb78 on 2007-12-22
For anyone finding this thread via Google, I never got this to work using MythTV's ripper (mtd).  What I did instead was to mount the ISO image on /dev/loop0:

```

sudo modprobe loop
sudo mkdir /mnt/dvdmount
sudo mount -t iso9660 -o ro,user,loop=/dev/loop0 /path/to/ISO/image.iso /mnt/dvdmount

```

You will need to make your username part of the "disk" group:

```
sudo adduser `whoami` disk
```

Then, in a new terminal window (otherwise you won't be part of the disk group yet):

```
sudo aptitude install mencoder
mencoder -oac twolame -ovc copy -of mpeg -o /path/to/myth/videos/outputfile.mpeg -dvd-device /dev/loop0 dvd://
```

I think the normal path to myth videos is /var/lib/mythtv/videos, but it might vary on your configuration.

Now, you have to add the video to your library.  In Myth, go to Utilities/Setup -> Video Manager.  If you put the file in the right directory, it should show up.  You can then search for it in IMDB, etc., using the menu (right arrow on the keyboard when you have the movie highlighted, not sure how to do it on the remote).  If you skip this step, the movie won't be in your library.

You can watch the movie now by going to Media Library -> Watch Videos.

I hope this helps someone!

---

### Post by aj_watts@optusnet.com.au on 2008-01-01
> **superm1 said:**
> Yeah you probably need to install libdvdcss2.  Look in the mythbuntu-control-centre for how to turn it on.  You need this both for ripping and playing devices.

Also,
You might need to start mtd, but make sure that libdvdcss2 works first, and then starting mtd isn't much trouble at all.

Hi,

My first post and a relative newcomer to Linux, so please bear with me.

I installed libdvdcss2 and playback from the DVD now works. (having language selection probs, but that can wait for another post). How do we check for, and subsequently start MTD?
:confused:

Anthony

---

### Post by superm1 on 2008-01-01
> **aj_watts@optusnet.com.au said:**
> Hi,

My first post and a relative newcomer to Linux, so please bear with me.

I installed libdvdcss2 and playback from the DVD now works. (having language selection probs, but that can wait for another post). How do we check for, and subsequently start MTD?
:confused:

Anthony
mtd starts when you press a number key in mythdvd's rip section.

Additionally you can start it from a command line if you would like.

---

### Post by aj_watts@optusnet.com.au on 2008-01-02
> **superm1 said:**
> mtd starts when you press a number key in mythdvd's rip section.

Additionally you can start it from a command line if you would like.

Thanks,

Tried as you suggested but the screen returned is that there is no jobs and nothing else to RIP. You can "view" from within the RIP setup screen OK, but I'm not sure if thats what is needed to be done or not?

BTW, this is being done purley via kbd, not via remote.

---

### Post by Lido on 2008-01-28
I've got a similar problem. I have the dvd device set up so all can read from it, I have the temp directory and target directories set so everyone can write to them, I've got mtd running as root (used sudo to start it). But when I select "Import DVD" all I ever get is the "No jobs. Checking and/or waiting for DVD" message. It doesn't even seem to be trying to look for the dvd. The dvd plays fine though. Anyone have any guidance?

---

### Post by Trollslayer on 2008-05-24
> **superm1 said:**
> Yeah you probably need to install libdvdcss2.  Look in the mythbuntu-control-centre for how to turn it on.  You need this both for ripping and playing devices.

Also,
You might need to start mtd, but make sure that libdvdcss2 works first, and then starting mtd isn't much trouble at all.

I had the same problem - instead of the DVD drive showing as **/dev/dvd** in 8.04 is it showing as **/dev/dvd1** so I changed the media settings and have just done my first rip. :)

---

### Post by MrVining on 2009-05-10
I can not play DVDs or rip them...
Very fresh 9.04 install picking Backend/Frontend option. I went into "Mythbuntu Control Centre" and checked "Enable Medibuntu Proprietary Codec Support" and then "Enable libdvdcss2" hit Apply, even restarted and still no playback or rip.  Any thoughts? At this point all I really want to do is rip my DVDs and Blu-Rays, thinking Mythbuntu is a good place to start.

---

### Post by MrVining on 2009-05-11
> **Trollslayer said:**
> I had the same problem - instead of the DVD drive showing as **/dev/dvd** in 8.04 is it showing as **/dev/dvd1** so I changed the media settings and have just done my first rip. :)

Okay so I guess mine showed up as /dev/dvdrw I don't even remember where I found that, but I did. Now I'm at least getting into the rip menu, no successful rips yet. Having fun picking from one of the 100 different titles on a Disney DVD.

I don't suppose there is a guide for this someplace, I haven't found a whole lot of info on this that makes any sense to a non Linux guru.

---

### Post by moseleyb on 2009-05-31
I am having a similar problem. I can play dvd's but the rip process chokes at some point and never completes. If anyone has suggestions I would love to hear it. 


Moseleyb

---

### Post by ahood on 2009-05-31
In the past, I have had to troubleshoot DVD Rip. A couple of suggestions below.

**Possible causes for the 'No Jobs' message**
A. MTD not running
B. Library for reading encrypted DVD's is either old or not loaded
C. Path to DVD drive is incorrect

**Possible causes for rip to stop or hang**
A. Library for reading encrypted DVD's is old
B. Rip resolution is set to something other than 720x480 (see [http://ubuntuforums.org/showthread.php?t=728747](http://ubuntuforums.org/showthread.php?t=728747) )

[B][I]
When troubleshooting, I highly recommend ripping an older DVD or an unencrypted DVD. Some newer DVDs are very difficult to rip.[/I][/B]

**Device Path**
An easy way to determine the device path for the DVD drive is to use VLC. First, use VLC to play a DVD disc to make sure that (a) the library for playing encrypted DVDs is present and (b) VLC can access the DVD drive.

1. Exit out of the MythTV frontend and start VLC
2. Press Ctrl+d to open a DVD disc
3. The path to the DVD device will appear in the **Customize** box at the bottom of the window will appear.

**Refer to Log Files for Critical Info**
mythburn.log
progress.log

If the location of these log files are unknown, then execute the following command...

> find /home -name mythburn.log

---

### Post by AlecJ on 2009-05-31
[I]
                Nothing new, one solution is to delete .ICEauthority and add the delete line to the script as this thread shows 
[http://ubuntuforums.org/showthread.php?p=6320530](http://ubuntuforums.org/showthread.php?p=6320530) 
 
And for now its the best on offer,,...             [/I]

---

### Post by ###Nick on 2009-07-18
I've recently tried to shrink my dvd archive from iso images to vob's by trying to loopback the iso images into mythtv's and re-transcode them but get the same "no jobs found" error tried above.

However i did find a way to extract the vob file from the iso outside of mythtv using info from here [http://dominia.org/djao/dvdsub.html]("http://dominia.org/djao/dvdsub.html")
Just import the newly created vob into mythvideo.

its part of the transcode package

    tccat -i /dev/dvd -T A,B-C,D > video.vob

where

    * A is the title that you want to rip
    * B is the chapter that you want to start from
    * C is the chapter that you want to end with
    * D is the angle that you want (typically, 1)
    * video.vob is the file where you want the ripped output to go
 
I mount the iso image via loop back (need to create directory to mount iso image to first) then rip the vob file from the iso image.
check what title & chapter numbers you need from vlc or similar.


```

# create dir for iso
sudo mkdir /mnt/dvd
#mount iso
sudo mount -o loop /path/to/iso /mnt/dvd
#rip vob from iso, title 5, chp1-12, angle=1 to video.vob
tccat -i /mnt/dvd -T5,1-12,1 > video.vob

```

---

