---
title: "AUDIO CD Playback / VLC"
date: 2010-08-18
forum: Multimedia Software
---

### Post by maclenin on 2010-08-18
To Whom It May Concern!

I have tried loading/playing (many different) audio cds via VLC / new install of 10.04 (on a laptop through which I had been able to play / burn / rip audio cds until I "upgraded")...this is what transpires:

```
Your input can't be opened:
VLC is unable to open the MRL 'cdda:///dev/sr0'. Check the log for details.
```

Any wisdom?

---

### Post by sydbat on 2010-08-18
> **maclenin said:**
> To Whom It May Concern!

I have tried loading/playing (many different) audio cds via VLC / new install of 10.04 (on a laptop through which I had been able to play / burn / rip audio cds until I "upgraded")...this is what transpires:

Errors:
Code:

```
Your input can't be opened:
VLC is unable to open the MRL 'cdda:///dev/sr0'. Check the log for details.
```

Any wisdom?Just to clarify - how are you doing this?
1) You put a CD in and it asks you what to do with it and you ask it to open with VLC? 
2) The CD is in and you open VLC, THEN try to open/run the CD?

Have you checked the log files? Perhaps VLC is looking for the CD drive in the wrong place? Or the drive is/has failed?

---

### Post by maclenin on 2010-08-18
Essentially:

1. I put an audio CD into the drive and vlc does not open it, automatically (as it's set to do) and

2. (then) when I try to open the CD "manually" via vlc (Meida / Open Disc / Audio CD) the error reveals itself.

I had a similar issue with DVDs (and vlc) - the contents of this thread resolved the DVD issues:

[http://ubuntuforums.org/showthread.php?t=1548993](http://ubuntuforums.org/showthread.php?t=1548993)

Thanks for the help....

---

### Post by mc4man on 2010-08-18
Do you see an icon on the desktop for the audio cd?

With the cd in the drive what does this show in a terminal

```
ls -l -R ~/.gvfs/
```

Ex.
> doug@doug-desktop1:~$ ls -l -R ~/.gvfs/
/home/doug/.gvfs/:
total 0
drwx------ 1 doug doug 0 1969-12-31 19:00 cdda mount on sr0

/home/doug/.gvfs/cdda mount on sr0:
total 328486
-r-------- 1 doug doug  43759072 1969-12-31 19:00 Track 1.wav
-r-------- 1 doug doug  27972448 1969-12-31 19:00 Track 2.wav
-r-------- 1 doug doug  33250336 1969-12-31 19:00 Track 3.wav
-r-------- 1 doug doug  71183392 1969-12-31 19:00 Track 4.wav
-r-------- 1 doug doug  31952032 1969-12-31 19:00 Track 5.wav
-r-------- 1 doug doug 128249968 1969-12-31 19:00 Track 6.wav


---

### Post by maclenin on 2010-08-18
Thanks.

```
ls -l -R ~/.gvfs/

```
...reveals:

```
total 0
```

---

### Post by mc4man on 2010-08-18
If you did have an audio cd in the drive while running that command (and can confirm no icon shows up - 

Then there are several possibilities - assuming your drive is detected and working with dvd's then the most likely is it may be dying.

Otherwise, some have had good drives not work right in lucid - you'd need to search out some threads and see if there are any solutions.

You could post this though unlikely the reason
```
cat /etc/fstab
```
and
```
sudo lshw -C disk
```

---

### Post by maclenin on 2010-08-18
sudo lshw -C disk reveals:

```

*-cdrom                 
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open

```

fstab does not list the the DVD-RAM writer....

and, now, for some reason the DVD playing part does not work - the computer is not more than 2 years old - the drive should be in fine condition....

hmmm....

it's as if the drive has stopped mounting - for some reason....

---

### Post by maclenin on 2010-08-18
...though I am using a laptop, this bug report seems to speak (directly?) to my issue:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092)

any thoughts?

...am continuing to read - why oh why does this recurring problem have to sully what is otherwise a hands-down winning alternative to the other OS's lurking out there???

---

### Post by maclenin on 2010-08-18
Back in action, for now (i.e. BOTH DVDs AND Audio CDs are "seen" and working via the DVD-ROM)....

I have no idea what I did fundamentally - HOWEVER - what I THINK I did to seemingly resolve the "issue" was to toggle the BOOT ORDER in the BIOS....

First, I:

```
Toggled the BOOT order to make the "USB CD-ROM" (boot) "Second"

and

Toggled the BOOT order to make the "Laptop HDD" (boot) "First"
```

...this caused the CD-ROM to disappear, entirely, from lshw -C disk.

Then, I:

```
Toggled the BOOT order to make the "USB CD-ROM" (boot) "First"

and

Toggled the BOOT order to make the "Laptop HDD" (boot) "Second"
```

...and...bang - upon next start-up I ran lshw -C disk and the DVD-ROM had returned and I was able to fire up both a DVD and an Audio CD - without issue....

Hmmm?

[Related: [http://ubuntuforums.org/showthread.php?t=1548993](http://ubuntuforums.org/showthread.php?t=1548993) ]

---

