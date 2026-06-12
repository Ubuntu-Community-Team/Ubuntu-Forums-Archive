---
title: "No sound after Install"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by th3gh05t on 2006-06-02
Hi, 

I have just upgraded from Breezy and when I finally finished the upgrade, and rebooted, I noticed that sound does not work at all. I have tried XMMS and Banshee, and even the system sounds aren't working.

Please note that I did have some trouble with the upgrade process. You can read that thread [here]("http://ubuntuforums.org/showthread.php?t=186219") and [here]("http://ubuntuforums.org/showthread.php?t=186125").

I have made sure to check that there are no external obvious issues. (Speakers on, connected properly, etc.)

Has anyone else encountered this issue?

Thanks, th3gh05t

---

### Post by joshyf on 2006-06-02
i have found this problem too, although i had no problems with the installation (installed from the beta and updated from there), but i'm recently new to linux in general so don't really have a clue...

any help??

thanks, joshyf

---

### Post by th3gh05t on 2006-06-02
Help please!!

---

### Post by linuksamiko on 2006-06-02
Saluton everyone,

I gues I found the problem to "no sound after installation". I don't have sound myself and now I know why. My first soundcard is my onboard soundcard. Every sound is played over it.

I don't know how to change that your second soundcard should be the major card (maybe somebody else does) but a work-around migth be turning off your onboard soundcard (I couldn't test it myself yet but it is very likely that it works).

linuksamiko

---

### Post by th3gh05t on 2006-06-02
well, I only have one sound card (onboard), so I don't think that is the solution.

In fact, what kind of solution did you provide?

---

### Post by linuksamiko on 2006-06-02
at least I tryed! how should I know that you only have one soundcard if you don't post your system!
I gave a solution (a work-around migth be turning off your onboard soundcard). I know it is not quite the best but your answere could have been a little more polite!

---

### Post by joshyf on 2006-06-02
thanks for trying, but i too have an onboard soundcard (using a compaq laptop), so turning it off isn't a solution.

does anyone else have any ideas?

---

### Post by fishmorg909 on 2006-06-03
I have no sound either -- though everything else is so good. I'm on a Dell Optiplex GX1 (onboard sound, no card) that had the sound missing from Breezy until I did this:

Adding the following line to /etc/modules
```
snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5
```

I added that to to the /etc/modules file, and I had sound after rebooting. I tried this with Dapper upgrade, but it didn't help. 

(ALSO: I now get a PCMIA 'fail' notice in the bootup sequence, and the occasional message in terminal that ALSA can't find any PCMIA activity.) :confused:

---

### Post by deodatus on 2006-06-04
I found something like this on a Fedora forum.
Open terminal:
#*sudo alsaconf*
follow instructions, then:
#*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted.

---

### Post by joshyf on 2006-06-06
there is no "aslaconf" for ubuntu... is there somewhere i can get it?

---

### Post by th3gh05t on 2006-06-06
Is this a widespread problem? Or only a few people not getting any sound?

Any Ubuntu gods out there that would like to help us out?

---

### Post by Rzulf on 2006-06-06
I had this problem but after a reboot everything worked fine.

EDIT: Well it doesn't work again. :(

---

### Post by longinus on 2006-06-06
[QUOTE=th3gh05t]Is this a widespread problem? Or only a few people not getting any sound?

Any Ubuntu gods out there that would like to help us out?[/QUOTE]

Same problem here... had sound on Breezy, now that I upgraded to Dapper it stoped working. :( 

Onboard sound, on some old dell pc.

---

### Post by Rzulf on 2006-06-06
On my PC OSS works but ALSA doesn't :/

---

### Post by Ekin on 2006-06-06
So I am joining this NO-SOUND community too.
I do not have any sound after upgrade. Every application (including alsamixer, or sound control in gnome) generate error message about not devide detected or bad plugin. It seems that sound card is not detected. NEED HELP! BROWSING FORUMS AND NET FOR 2 DAYS AND STILL NOTHING!

BTW: I am running Ubuntu since Hooray (and I am still linux NOOB), and I've managed to do all the fixes myself (most time from various how-to's on this forum). But in this case I am really annoyed and desperate (even so desperate I started tkinking about getting W XP). 

HEEEEEEELP MEEEEEEE!!!!!!!!!

---

### Post by ricardo06 on 2006-06-06
Hi everybody,
Right after i upgraded from breezy to dapper I had sound in xmms and VLC but not in rythmbox. 
But i could not burn an audio CD. So I  went to the online manual and followed the instructions on Music and Audio. I installed Gstreamer packages. After this I could burn a CD but no more sound.
I removed the packages that i had installed, but the sound never came back !!!
I do think there is something wrong with dapper and the sound.
Hope someone will find a fix

Richard

---

### Post by ricardo06 on 2006-06-06
I Hope this will work for You.

I installed gnome-alsa-mixer with synaptic.

PCM was checked Mute. I unchecked Mute and now the sound is back.

8)

Richard

---

### Post by Rzulf on 2006-06-07
That is odd. When OSS works then ALSA doesn't and when AlSA works then OSS not. :(

---

### Post by tiger338 on 2006-06-07
My system is Dell Optiplex GX1 with on-board sound card.

I installed Dapper from the scatch and I got no sound.

I read this thread and edit my /etc/modules file by adding the following line.

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

it did not work!

But when I added one word, snd-cs4236, it works on my system, somehow.

Therefore, Just add following one word into /etc/modules and reboot.

**snd-cs4236**

Make sure your BIOS turn on on-board sound card.

I know it is not professional help. I want to share my experience.

---

### Post by mitiu on 2006-06-07
Thanks! It works for me on Dell Optiplex GX110 with onboard sound.

---

### Post by th3gh05t on 2006-06-08
Hi, 

I finally got the sound working on my system.

It was a combination of installing "gnome-alsamixer", and editing your "/etc/modules" file. (See above post)

Also, I right clicked on sound icon in taskbar, and clicked on "Open Volume Control". Then, from here, I clicked on "Edit > Preferences".

For some reason, PCM was the only one checked. I started to check all of the options, and I found that my "Surround" was muted. This is what caused the problem.

---

### Post by homicidalmo0se on 2006-06-09
ah! thank you! it works! but all i did was do the last step in your post. i didn't install alsamixer or edit my modules file.

---

### Post by joshyf on 2006-06-10
I installed the 'gnome-alsamixer' and also edited the /etc/modules file, and then the sound worked. yay! :)

---

### Post by leimus on 2006-06-10
I just went into Edit > Preferences and for some reason there was an option for Sigmatel 4 Channel Surround. 

I checked this box and then checked another box for a new tab that appeared in the audio manager and now I have sound.

---

### Post by Jerim on 2006-06-10
Just to add another possible solution.

I double clicked on the speaker icon on the taskbar. I got a slider menu. From there I clicked on File and went to "Change Device." I noticed there were two options. The one that was selected was not my sound card.

See if there is any other device listed and if so click on it to see if that fixes the problem.

---

### Post by jobyjoby on 2006-06-11
Update:  Used the 1.011 alsa files on Zenwalk linux and have sound.

> When I go into bios I do not see anything about enabling/disabling onboard sound? (I want to make sure it's enabled)

And I don't understand how to download those 1.011 files from [http://www.alsa-project.org/](http://www.alsa-project.org/)


So far I've tried:
- adding snd-cs4236 /etc/modules file
- unmuting everything and cranking up all the volumes by clicking the panel icon (and going through alsamixer)
- using xfce desktop environment
- running automatrix
- all of the above while playing the experience ubuntu ogg file that is included and while playing music videos via internet browser and still no sound.

I have no alsaconf file.
Gnome Alsa mixer main tab says my conexant id 30 chipset (oss) chipset so I shall assume it's supposed to do that.

I just have the following onboard soundcard (on a Gateway pentium4 laptop):
cat /proc/asound/cards
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with unknown codec at 0xe02ff800, irq 169
I am assuming that unknown codec part isn't anything to worry about.


So I'm completely lost right now, can someone spell out how to use the bios or 1.011 files so I'll have more to try?

---

### Post by Michael Matthews on 2006-06-14
Install gnome-alsamixer app and it might give you a view of what volumes and mutes are set. I have different sound card so I can't give specifics.

Not sure why this app is not installed by default for desktop.

---

### Post by Michael Matthews on 2006-06-14
Install gnome-alsamixer app and it might give you a view of what volumes and mutes are set. I have different sound card so I can't give specifics.

Not sure why this app is not installed by default for desktop.

---

### Post by plumcreek on 2006-06-15
One thing that has worked for others in getting the sound to work is this:

upgrade your kernel

During the upgrade process, the kernel is sometimes left alone. I don't know if this is the case for all upgrades, but it is the case for some. If you have a 2.6.12 (or lower) kernel then you have a kernel from breezy or before. The kernel that ships with dapper is 2.6.15-23-386.

All of the drivers (for things like network and sound cards) are included with the kernel package and for some reason some of the sound card drivers from breezy-era kernels stop working under dapper.

Upgrading to the dapper version of the sound card drivers (which happens when you upgrade your kernel) will fix many of the sound issues people are having.

To upgrade your kernel, open synaptic and search for "linux-image-2.6.15" and then choose the appropriate one to install (probably linux-image-2.6.15-23-386 or linux-image-2.6.15-23-686). Restart your computer after it is installed and you should hopefully have sound when it comes back up.

I hope this helps.

P.S. alsamixer is installed by default, just open up a terminal and type in 'alsamixer' and you can get to it. gnome-alsamixer is basically a pretty front-end.

---

### Post by ViperAFK on 2006-06-15
I had a fresh install of dapper and the sound didnt work, and ive tried playing with alsa mixer, i hope editing the ect/modules files will work

---

### Post by disk11 on 2006-06-16
No go with updating the kernel to 2.6.15-35-386 and the edit of /etc/modules. I am using an onboard Realtek ALC650 with my Shuttle SB75G.

Edit:tiger338, how did you figure out what value to use in /etc/modules?  I see nothing like that in my device manager for my sound card.

---

### Post by disk11 on 2006-06-16
Apparently the ALSA that dapper comes with doesn't work quite right, update to ALSA 1.0.11 using the directions here: [http://ubuntuforums.org/showthread.php?t=187156](http://ubuntuforums.org/showthread.php?t=187156)

Make sure you either omit or modify the ./configure line in alsa-driver folder.

---

### Post by matjaz_pirnovar on 2006-06-18
I have Dapper for a week now, but yesterday sound suddenly stopped working. When I turn on the computer, default sound setting is MUTE (when changing that still no sound).

Moreover, Gnome alsa mixer doesn't wan to run after installation. The window is empty with File and Help tollboxes at the top.

When I try to open it in File -> Preferences it reports an error (The device quitted unexpectedly. Please report the bug to the developers...) and the following bug report is:

Backtrace was generated from '/usr/bin/gnome-alsamixer'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1223436064 (LWP 7348)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb74bd463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f728e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0804cae1 in ?? ()
#5  0x080a0d20 in ?? ()
#6  0x082965ac in ?? ()
#7  0xbf9c8428 in ?? ()
#8  0x08051366 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1223436064 (LWP 7348)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74bd463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f728e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0804cae1 in ?? ()
No symbol table info available.
#5  0x080a0d20 in ?? ()
No symbol table info available.
#6  0x082965ac in ?? ()
No symbol table info available.
#7  0xbf9c8428 in ?? ()
No symbol table info available.
#8  0x08051366 in ?? ()
No symbol table info available.
#9  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

The Bug Buddy opens and suggests to report the 'bug'.  Have a funny feeling that content of the mixer is somehow empty...
Sound and video devices run, but there is no sound. And when I run Mplayer it says 'no sound. It couldn't be initiated'

Any clues?

Thanks.  :)

M

---

### Post by digitalghost1 on 2006-10-30
> **tiger338 said:**
> My system is Dell Optiplex GX1 with on-board sound card.

I installed Dapper from the scatch and I got no sound.

I read this thread and edit my /etc/modules file by adding the following line.

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

it did not work!

But when I added one word, snd-cs4236, it works on my system, somehow.

Therefore, Just add following one word into /etc/modules and reboot.

**snd-cs4236**

Make sure your BIOS turn on on-board sound card.

I know it is not professional help. I want to share my experience.

That worked like a champ! :cool: 
I have a couple of DELL OptiPlex GX1s that are laying around at end of hardware
life cylce, but they will be re-allocated for Ubuntu workstation duty. 
On one of the machines the sound was disabled in BIOS 
which can drive you insane ](*,) if you don't happen to look there.

---

### Post by Duffman2010 on 2006-11-03
What worked for me:
·Install gnome-alsamixer (you will need universe/multiverse repositories to be activated).
·Run gnome-alsamixer and un-mute Surround, that's all.


[ATTACH]18803[/ATTACH]

---

