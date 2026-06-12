---
title: "Problems with Sony  mp3 player"
date: 2008-08-12
forum: Multimedia Software
---

### Post by Iceman512 on 2008-08-12
Hey all,

I've recently bought the Sony NWZ-A826 mp3 player but I'm having problems putting my files on it from ubuntu. When hooked up to the PC, it does not automount. It shows up as 'USB drive' but upon double-clicking it, it says: "Can't mount file"

I've tried using XP on my laptop and that works perfectly but the same cannot be said about ubuntu, so I'm pretty sure that the player itself and the cable and usb ports are ok.

So, I've tried searching for a solution on the net but there wasn't much out there. The only thing I found that may be remotely useful is the output of sudo lshw, which is:

 *-disk
             description: SCSI Disk
             product: WALKMAN
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdd
             version: 1.10
             serial: 3
             size: 3664MiB (3841MB)
             capabilities: removable
           *-medium
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 0
                logical name: /dev/sdd
                version: FAT32
                serial: 0000-0002
                size: 3663MiB
                capacity: 3664MiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat label=WALKMAN

I've taken out the info about my other disks, seeing that this is the only part that mentions sony. If the other sections are required, I will gladly post it.

Thanks in advance.

Regards,

Iceman512

---

### Post by Marat89 on 2008-09-16
Push!
Any solution yet?

---

### Post by Vryko Lakas on 2008-09-16
Hello, Iceman512. Hope you're still watching. 

I've been looking into the issue regarding the compatibility of Sony products with Ubuntu. 

This recent thread:  
[http://ubuntuforums.org/showthread.php?t=787041&highlight=Sony+mp3+linux]("http://ubuntuforums.org/showthread.php?t=787041&highlight=Sony+mp3+linux")
... suggests to try using Amarok to transfer the files, perhaps because the issue seems to be with Gnome and not KDE. If all goes according to plan, one of the simple solutions in this thread will solve your problem. 



If not, a quick search of the Ubuntu forums turns up a couple of other threads offering different answers which may or may not work for you. Other solutions including installing some Java programs, but those only seem to work if you can successfully mount the device. You might also have some luck using Gnomad2 to transfer the files.

---

### Post by Marat89 on 2008-09-17
I read that ubuntu 8.10 will support the NWZ Series natively, I don't know where I read it (launchpad?!), can anyone verify that,? and I have an additional question: if I buy a Sony NWZ-826 (4Gig), will be the Ubuntu problem still exist, because its a series-problem, or could it be support natively?.
Amarok is a KDE Player, can anyone say about the upcoming Banshee 1.4 release, can banshee support the nwz series? (i will ask them now, and post their answer) :popcorn:

---

### Post by Vryko Lakas on 2008-09-17
I wouldn't know. I try to stay away from Sony and other players that work on proprietary formats. The Net Walkman series, like the old Net MD minidisk players, actually tend store music in Sony's ATRAC format rather than MP3. The Windows-Only software they use to manage what goes onto the players converts between formats before transfer. I'd rather use something where I can just drag-and-drop files regardless of what operating system I'm using, without any hacks or work-arounds. 
But that's just my personal preference. Maybe I'm a bit jaded since my minidisk player became almost useless with the switch to Linux.

---

### Post by Marat89 on 2008-09-17
yes you are right, BUT the NWZ series is compared to e.g. Ipod nano a lot better (design/soundquality/price) and its sony-->perfect mp3 player (except the ubuntu usb support , mtp has to work ;-), Intrepid will be support these player a lot better (usb mode), Banshee should recognize this sony nwz player in MTP Mode, But I dont find a option in the player where to set the Transfer Mode-USB/MTP, has this player these options??, I googled and found out that it has not a USB Mode, Only MTP Mode, because of that Ubuntu cant mount it as a usb devive, you have to use it with Rhythmbox/Amarok/Banshee or Gnomepad, But Banshee is for Gnome the best, especially the new 1.2.1
PUSH PUSH

---

### Post by bete on 2008-09-18
Well, i cant get my 826 player to work with neither Banshee 1.2.1 nor amarok, even in MTP mode. 

Just stays at "connecting" on my mp3 player's screen :(

---

### Post by Marat89 on 2008-09-18
oh noooooooooooooo
:-( oh god i thought it will be working cry...
mhhh what now, have u tried gnomepad?
has the player the option to switch between the modes /usb/mtp???
Please watch this thread, there is now a solution for the mounting problem: [http://ubuntuforums.org/showthread.p...Sony+mp3+linux]("http://ubuntuforums.org/showthread.p...Sony+mp3+linux")

---

