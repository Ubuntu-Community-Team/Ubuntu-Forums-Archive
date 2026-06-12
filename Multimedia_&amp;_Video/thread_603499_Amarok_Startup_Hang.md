---
title: "Amarok Startup Hang"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by frause on 2007-11-05
I've a fresh :KS :KS ubuntu gutsy installation - nothing special, everything is default... except the need of amarok :guitar:

first everything is fine amarok reads my audio library (which is mounted per samba), submitting my tracks to last.fm, endless playing quality music from the dynamic 'suggested songs' playlist. great :popcorn:
I booted my system several times too. still everything goes fine.

*something-happend-here*

Now - some days of massive usage and fine funtionality - Amarok is broken. on startup it hangs, gets grey and never comes up when I kill the designated processes, my complete system gets instable :confused:
The only thing I did in between is using f-spot pimpup my image collection...

All users on my system have the same problem. 
I got angry :mad: and 

deleted the amarok profile - no change! 
I re-installed several times - no change!
I deinstalled and installed - no change!

I do not want to change to KDE (not sure if it can help) but I need the amarok player!

please I really need some help or a link to a helpfull link (I couldn't find any similar problems)

---

### Post by talmage on 2007-11-05
I have the same problem with my Amarok and gutsy.  I upgraded from Xubuntu feisty to Ubuntu gutsy.

When you start Amarok, two programs run: amarok and amarokapp.  I ran strace on both when the app window turned grey.  amarok spews forth an endless stream of

wait4(8502, 0x7fff82a86798, WNOHANG, NULL) = 0
ioctl(5, FIONREAD, [0])                 = 0
ioctl(3, FIONREAD, [0])                 = 0
select(14, [3 4 5 12 13], [], [], {0, 9483} <unfinished ...>

stracing amarokapp said:

semctl(32768, 0, IPC_RMID, 0)           = -1 EPERM (Operation not permitted)
semget(0x56a4d5, 1, IPC_CREAT|0660)     = 32768
semctl(32768, 0, IPC_STAT, 0x7fff6db3b1e0) = 0
semctl(32768, 0, IPC_SET, 0x7fff6db3b1e0) = -1 EPERM (Operation not permitted)
semop(32768, 0x7fff6db3b290, 2


Note the final '2' -- no closing paren.  Something's hiding there.

---

### Post by talmage on 2007-11-05
Here's what I see when I run amarok in GNOME terminal:

```
talmage@scarlet:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x885f20 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x885f20 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

---

### Post by frause on 2007-11-05
uhhhh, great very similar to mine
> 
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8124ae8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8124ae8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?


so, any idea's :-&

---

### Post by talmage on 2007-11-05
It doesn't hang under XFCE.  

Something that amarok depends on must be out of date.  That's my guess.

---

### Post by frause on 2007-11-06
@ talmage
thx fro your advice but when the dependencies brake the installation it would be fixed after a complete re-installtion or many people more should have the same problem.

so, after a night of waiting, trying and failing ](*,) I have some more information:
 * when I delete the amarok file under .kde/config it will startup :)- and hang afterwards:(
 * when I delete the config file and the complete amarok directory it will startup and work till next boot/startup - Uuuuuhuuuuuuh:)

SO any idea's keeping me stay tuned with amarok?
 Maybe some more information around:
 - my library is readonly mounted per samba in utf8-iocharset
 - and yes I have many many many nice special characters

ok, my best chance is the amarok 2.0 I guess but till that day???????

#@W&(%&#$@^#)_^

---

### Post by frause on 2007-11-06
[He's right!]("http://www.linux.com/articles/53118") Same expierence on Amarok. Sadly :frown:

I will switch to Rhythmbox and give the next version of amarok a try - when it appears....

---

### Post by flash222 on 2007-11-06
I've had the same problem with Amarok. My distribution is PCLinuxOS (based on Debian as so as Ubuntu) and in my case the solution was:

- complete uninstall Amarok (with deleting config files)
- reboot computer
- install Amarok again

And it was done. I can listen music again and I'm listening right now :)

---

### Post by frause on 2007-11-06
@ flash222 :)
happy one - I tried the same (default windows repair procedure) with no effect...

---

### Post by frause on 2007-11-06
Wow this is ugly :-& rhythmbox, he? box - yes but nothing else...

so how can I get amarok running???

PLEEEAASEE HELP ME!

---

### Post by talmage on 2007-11-07
Amarok works again.

As strange as it may seem, Amarok would hang under GNOME but not under XFCE4. This is on the same amd64  laptop (HP Pavilion tx1000)!  Switching from XFCE back to GNOME didn't solve the problem.

Yesterday, the Ubuntu update manager offered a big collection of updates, mostly security upgrades for CUPS, but there were one or two others, IIRC.  Amarok under GNOME began working correctly once I installed the updates.

---

### Post by frause on 2007-11-07
Uhhhhh :|
I had the same cups updates yesterday and after a hard expierence with rhythmbox :shock: I again installed amarok... but with no effect...

@talmage
do you know what updates you had?? I would update for hell to get amarok running?

Any suggestion on repositoy subscriptions with better luck, than default?? :?

---

### Post by captaink on 2007-11-07
> **flash222 said:**
> My distribution is PCLinuxOS (based on Debian as so as Ubuntu)
This is really out of subject, but I noticed some misunderstanding: PCLinuxOS is based on Mandriva, not Debian. If it was Debian-based it would use deb packages instead of rpm, but it uses rpm. Pls check out wikipedia and search for "Linux Distribution" to learn more about distros and forks.

Now, for the problem, i don't have any idea, although it may seem almost solved. A good idea is to submit this problem as a bug at [http://launchpad.net]("https://launchpad.net/ubuntu/+bugs") if not there yet. I'm sure many developers would interest in solving this bug. Just report it!

> Any suggestion on repositoy subscriptions with better luck, than default?? 

Check on System -> Administration -> Installation Sources (or something like that :P ) if all repos are checked. They should be, but just a check :)

---

### Post by frause on 2007-11-07
@captaink
Using the GUI and checking the hell is what I already tried.
As I couldn't find a similar problem I will submit it as a bug - thanks for the site - and will see what happens

:-\"

---

### Post by talmage on 2007-11-09
> **frause said:**
> 
@talmage
do you know what updates you had?? I would update for hell to get amarok running?

Any suggestion on repositoy subscriptions with better luck, than default?? :?

My joy was short lived. Yesterday, after logging in with XFCE, I logged out and then logged in with GNOME.  Amarok, which works flawlessly under XFCE doesn't work *again* under GNOME.   I let it run all night, hoping that it would unhang itself.  No joy.

I looked in /var/log/apt/term.log for the updates that I installed that day when Amarok started working again under GNOME.  These are all of the packages that Ubuntu updated:

```

Preparing to replace libc6-i386 2.6.1-1ubuntu9 (using .../libc6-i386_2.6.1-1ubuntu10_amd64.deb) ...
Preparing to replace libc6-dev 2.6.1-1ubuntu9 (using .../libc6-dev_2.6.1-1ubuntu10_amd64.deb) ...
Preparing to replace libc6 2.6.1-1ubuntu9 (using .../libc6_2.6.1-1ubuntu10_amd64.deb) ...
Preparing to replace libcupsys2-dev 1.3.2-1ubuntu7 (using .../libcupsys2-dev_1.3.2-1ubuntu7.1_amd64.deb) ...
Preparing to replace libcupsys2 1.3.2-1ubuntu7 (using .../libcupsys2_1.3.2-1ubuntu7.1_amd64.deb) ...
Preparing to replace libcupsimage2 1.3.2-1ubuntu7 (using .../libcupsimage2_1.3.2-1ubuntu7.1_amd64.deb) ...
Preparing to replace cupsys-common 1.3.2-1ubuntu7 (using .../cupsys-common_1.3.2-1ubuntu7.1_all.deb) ...
Preparing to replace cupsys 1.3.2-1ubuntu7 (using .../cupsys_1.3.2-1ubuntu7.1_amd64.deb) ...
Preparing to replace cupsys-bsd 1.3.2-1ubuntu7 (using .../cupsys-bsd_1.3.2-1ubuntu7.1_amd64.deb) ...
Preparing to replace cupsys-client 1.3.2-1ubuntu7 (using .../cupsys-client_1.3.2-1ubuntu7.1_amd64.deb) ...
Preparing to replace gnome-system-monitor 2.20.0-0ubuntu1 (using .../gnome-system-monitor_2.20.1-0ubuntu1_amd64.deb) ...

```

---

### Post by slips on 2007-11-20
I had the same problem. Amarokapp hangs, while Amarok keeps going in an endless loop. An strace shows that Amarokapp hangs on an semop call. 

Here's how to fix it:

The last line of the strace output was:
semop(2654209, 0xbfb063ce, 2    <unfinished>

The first argument to "semop" is the Semaphore Array. 

Kill the semaphore array with the command:

# sudo ipcrm -s 2654209

(change the id to whatever your find in your strace output).

Restart amarok and everything should work.

---

### Post by Makc1984 on 2008-01-08
try removing .rcc directory in ~. my amarok runs after that.

---

### Post by djgrant on 2008-02-14
slips' fix worked for me. Will it happen again later? Anyone know why this is happening?

---

