---
title: "CD Player Troubles"
date: 2010-08-31
forum: Multimedia Software
---

### Post by jkoutsky on 2010-08-31
I am trying to get several old (2001-2002) CD-RW's to operate on my system. I can run many old DVD players with no problem. What happens...The computer recognizes the CD player. I can SEE it in the computer window. When I go to PLAY the CD I lose the icon for the player. I am using Ubuntu 9.10.

johnk

---

### Post by varunendra on 2010-09-01
A minor confusion here:
> **jkoutsky said:**
> I can run many old DVD players with no  problem.
Do you mean DVD discs, or DVD player programs (like vlc, mplayer,...)?

> **jkoutsky said:**
> What happens...The computer **recognizes the CD player**. I can SEE  it in the computer window.
..CD player- you mean the media player program? or the CD disc loaded on the drive?

> **jkoutsky said:**
> When I go to PLAY the CD I lose the icon for  the player. I am using Ubuntu 9.10.
I don't think ubuntu places any media player's icon on desktop. So I guess you mean the icon of the drive in Places>Computer or the icon of the cd on the desktop (created when it is loaded) or the graphical interface of the media player program. Which icon- please confirm.

Now a few suggestions totally based on guess unless you make things more clear:

[LIST=1]
[*]If it is the drive or CD icon that disappears, please load a cd, wait until its icon appears, run it to make the icon disappear again, then open terminal (**Applications>Accessories>Terminal**) and enter this command:```
dmesg | tail
``` Post here the output of the command.
[*]If it is the icon or the graphical interface of the media player program that disappears, please mention the name of that program. If it is the default player of ubuntu (**Applications>Sound & Video>Movie Player**), then instead of opening it from the menu icon, open it from terminal. To do so, open terminal as told above, type **totem**, press 'enter'. This would open the GUI of totem player (leave the terminal open in the background). Now do whatever makes it disappear abruptly. There should be some error messages left in the terminal. Copy them & post back here.
[/LIST]
If you have doubts, please post screenshots before & after the "disappear" events. (press "print screen" button on the keyboard to take the screenshot)

---

### Post by jkoutsky on 2010-09-01
Hi, I am sorry that I am not as clear as you would like me to be. Windows has clouded my past computing experiences.

When I look at COMPUTER I get an icon for my drive and CD player. When I go to play the CD player the icon dissapears and nothing happens. I CAN play music on DVD players with no problems. Here is what came out after I entered the given command:

john@john-desktop:~$ 
john@john-desktop:~$ dmesg | tail
[  907.785216] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  907.785227] end_request: I/O error, dev sr0, sector 0
[  907.785936] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  907.785942] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  907.785948] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  907.785956] end_request: I/O error, dev sr0, sector 0
[  907.786708] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  907.786714] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  907.786720] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  907.786729] end_request: I/O error, dev sr0, sector 0

Thanks!

---

### Post by varunendra on 2010-09-01
No problem with the clarification. It's common to take a few initial posts to clear up things. Now further on your problem:

Is it happening only with audio CDs or with all kind of CDs (like data, video, MP3s,.. etc.).

The message you posted seems common with audio CDs. See if [this]("http://ubuntuforums.org/showthread.php?t=1329530") helps. As suggested in the linked thread, please check if the cd is mounted in  .gvfs/cdfs.... folder (you will have to 'tick' View > Show Hidden Files option in nautilus- the file browser- window).

Post back, & we may proceed as needed.

---

### Post by jkoutsky on 2010-09-01
Thanks,

I found the .nautulis folder and it is empty.

---

### Post by varunendra on 2010-09-01
> **jkoutsky said:**
> Thanks,

I found the .nautulis folder and it is empty.

Not .nautilus, see in .gvfs as the linked post says.


PS:
Please post the output of
```
mount
```

(place your output within [ code] ..... [ /code] tags by highlighting pasted result, then clicking on # icon on editing panel)

---

### Post by jkoutsky on 2010-09-01
This is all new to me. I don't understand everything clearly but I put "mount' in my terminal and got the following:

john@john-desktop:~$ mount
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
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
john@john-desktop:~$

---

### Post by varunendra on 2010-09-01
> **jkoutsky said:**
> This is all new to me. I don't understand everything clearly but I put "mount' in my terminal and got the following:
Again, no problem. :) See the attached images to see which folder you've to look in & how to place your outputs in tags (it's not necessary, just makes the codes more readable).

---

### Post by jkoutsky on 2010-09-01
.gvfs is empty

```
john@john-desktop:~$ mount
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
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
john@john-desktop:~$ 

```

---

### Post by varunendra on 2010-09-02
Sorry, I'm having a bad internet connection issue (for months!!), got disconnected.

Your problem is most probably a bug similar to what is reported [here]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/419124") or [here]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/469179"), however, I'm trying to find if someone has found any workaround for it.

One more thing, as I asked earlier- is it happening with only Audio CDs, or with all kind of CDs (for example, if you put an Ubuntu installation CD or a CD that contains videos or photos, etc., does it disappear then too? Or are they accessible?) Because the bug is apparently prevalent with audio CDs only as far as I've found so far.

---

### Post by jkoutsky on 2010-09-02
Data CD's like the ubuntu CD work.

What is "Quick Thread"?

---

### Post by varunendra on 2010-09-02
> **jkoutsky said:**
> Data CD's like the ubuntu CD work.

What is "Quick Thread"?
I've no idea about "Quick Thread". Where did you find this term?

Also, if you can, please try a normal video DVD (or a VCD if it is not a DVD drive) and see if that works too. If it does, then it most probably is the infamous bug with audio CDs that is haunting you :(.

Anther output please ;) :-
```
lshw -C disk
```
(This will give me details about your cd/dvd drive)

---

### Post by jkoutsky on 2010-09-02
You do not need to be sorry for your internet problems. I live in Alaska! 

john@john-desktop:~$ lshw - C disk
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

```
format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)
```

---

### Post by varunendra on 2010-09-02
> **jkoutsky said:**
> You do not need to be sorry for your internet problems. I live in Alaska! 
Couldn't follow you! Do you mean your conn. is worse than mine???? :lol:

> **jkoutsky said:**
> john@john-desktop:~$ lshw [COLOR=Red]**- C**[/COLOR] disk

A small correction needed! There should be no space between - and C. Try copy-pasting the command I gave in my previous post. The output should be something like:
```
varun@lucidVM:~$ lshw -C disk
WARNING: you should run this program as super-user.
  *-cdrom                 
       description: SCSI CD-ROM
       product: DVD RW AD-7240S
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       serial: NECVMWarVMware IDE CDR101.00
       capabilities: removable audio
       configuration: ansiversion=5 status=nodisc
```
(ignore the first warning line)

And by the way, unless I get something important, I'll take a break now and get back to this thread later in the evening or tomorrow (it is 11am here). Meanwhile, you may try googling for the error messages you found by the dmesg command.

Let's hope someone with a positive experience picks up your problem.

---

### Post by jkoutsky on 2010-09-02
Audio CD's only, other types are fine. Also, I can use audio CD's in a DVD player with no problem.

---

### Post by jkoutsky on 2010-09-02
Here's the mess I tried.

```
john@john-desktop:~$ lshw-C disk
lshw-C: command not found
john@john-desktop:~$ lshw -C disk
WARNING: you should run this program as super-user.
john@john-desktop:~$ -cdrom
-cdrom: command not found
john@john-desktop:~$ lshw-C disk
lshw-C: command not found
john@john-desktop:~$ lshw -C disk
WARNING: you should run this program as super-user.
john@john-desktop:~$ *-cdrom
*-cdrom: command not found
john@john-desktop:~$ 
john@john-desktop:~$ lshw -c disk
WARNING: you should run this program as super-user.
john@john-desktop:~$ * -cdrom
Desktop: command not found
john@john-desktop:~$ *-cdrom
*-cdrom: command not found
john@john-desktop:~$ ^C
john@john-desktop:~$ 
```

---

### Post by varunendra on 2010-09-03
No updates on the problem yet.

As for the command, it seems both interesting & strange to me that you are getting no results at all! Two possible reasons may be- 1) Either your cd/dvd drive is not detected by the OS, and, 2) You terminated the command immediately without waiting for results (which is unlikely if you've copied the whole terminal output without editing here).

Accordingly a few suggestions (stepwise):

[LIST=1]
[*]Make sure your drive is detected by the system (see if its icon is in the 'Places>Computer'). If another (non-audio) cd runs, then it obviously is recognized.
[*]Try the same command with sudo ```
sudo lshw -C disk
``` Also, make sure to run this command when the drive is recognizable (i.e., no audio cd is in the drive, and its icon is there in Places>Computer)
[*]If still the drive is not recognized by the command, restart, then issue the command again (with sudo, & without trying anything else with the drive).
[/LIST]
If still no output occurs, enter the following two commands & post back the results:-
```
dmesg | tail -20
``````
sudo lshw > ~/Desktop/hardware.txt
```The last command will show nothing in the terminal. Instead, it'll generate a "hardware.txt" named file on your desktop. Just open it and post its contents here. If there's problem in opening it, just attach the file itself in your post.

This is just with consideration to all the possibilities, otherwise I think all you need is to just issue** sudo lshw -C disk** and wait a few seconds. ;)

---

### Post by jkoutsky on 2010-09-03
Thanks, see the following:

```
john@john-desktop:~$ sudo lshw -c disk
[sudo] password for john: 
Sorry, try again.
[sudo] password for john: 
  *-disk                  
       description: ATA Disk
       product: WDC WD400BB-75CA
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 16.0
       serial: WD-WMA8H3634282
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=34bd0efd
  *-cdrom
       description: SCSI CD-ROM
       product: CD5233E
       vendor: CREATIVE
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 2.02
       capabilities: removable audio
       configuration: ansiversion=5 status=nodisc
john@john-desktop:~$ 

```

---

### Post by jkoutsky on 2010-10-05
I don't appreciate that no one helped me. Eventually I put in a newer CD player. Thanks for nothing,.:sad:

---

### Post by Chris7 on 2011-10-06
I'm wondering why this thread is marked as solved although I cannot see any solution - moreover that I do have this problem :(


[LIST=1]
[*]I have installed Ubuntu 8.04 (Hardy Heron) and Ubuntu 10.04.3 (Lucid Lynx) in parallel.
[*]Inserting an audio CD in the tray (but not mounting it) under 10.04.3 gives me a repeating block of error messages while this works flawless under 8.04: ```
sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current]
sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
end_request: I/O error, dev sr0, sector 0

```
[*]Inserting a data DVD+RW that has been burned under 8.04 works fine. Burning it under 10.04.3 and inserting it afterwards, gives me the error messages again.
[/LIST]
Kernel is 2.6.32-34-generic.

Browsing through this forum and checking different settings hasn't helped so far. Any ideas?

---

### Post by nothingspecial on 2011-10-06
Please don't bump old threads to the top.

Start a new one instead.

Closed.

---

