---
title: "Waiting For Sound System to Respond Lucid Lynx"
date: 2010-06-18
forum: Multimedia Software
---

### Post by Meganehmbee on 2010-06-18
I'm running Lucid Lynx in a dual boot with Vista on a Gateway M6319. My volume control icon has "---" instead of the volume level indicator, and when I click preferences it says "Waiting for sound system to respond." 
I've spent a good part of my day searching through the forums, so far no luck. I tried deleting the .pulse file and restarting, no change.

Please help me figure out what is wrong with my sound.

Edit: I tried this: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) But I can't get past step 4, since this is my problem to begin with.

---

### Post by prshah on 2010-06-18
> **Meganehmbee said:**
> "Waiting for sound system to respond." 

It is likely the pulseaudio daemon is not running (very likely if you have recently upgraded). You can start it with either of these commands from the terminal (Applications-Accessories-Terminal)```
pulseaudio --start
#or
sudo service pulseaudio start

```

You can try both these commands in order, it will not harm any configuration on your system.

If it works, your volume icon should change within 2-3 seconds, there is no need for a reboot/logoff.

Please post back with results.

---

### Post by Meganehmbee on 2010-06-18
Thanks for the help. Still no change.  

```
pulseaudio --start
E: main.c: Daemon startup failed.
``````
sudo service pulseaudio start
* PulseAudio configured for per-user sessions
```

---

### Post by Yellow Pasque on 2010-06-18
Sigh. Try:
```
pulseaudio --kill
pulseaudio --start --log-level=4 --log-target=syslog
cat /var/log/syslog
```
Post the output of the last command.

---

### Post by waveswell on 2010-06-19
I have a Plantronics GameCom Pro1 headset.  The volume control works but there is no sound.  I tried the following:

[code]pulseaudio --kill
pulseaudio --start --log-level=4 --log-target=syslog
cat /var/log/syslog

System responded with a long list of actions ending with:

[code]pulseaudio[2017]: pid.c: Daemon already running.
 rtkit-daemon[1433]: Sucessfully made thread 2018 of process 2018 (n/a) owned by '1000' high priority at nice level -11.
 rtkit-daemon[1433]: Supervising 4 threads of 2 processes of 1 users.
 pulseaudio[2018]: pid.c: Daemon already running.

Still no sound.

---

### Post by yvesg on 2010-06-19
I am having a similar problem (the problem appeared yesterday). It seems that pulseaudio is trying to start again and again, leaving a zombie process. The command ''ps -el | grep pulse'' shows a process ID that is growing ever and ever:

```
$ ps -el | grep pulse
0 S  1000 12778  5036  0  80   0 -  4595 pipe_w ?        00:00:00 pulseaudio
1 S  1000 12780 12778  0  80   0 - 21093 hrtime ?        00:00:00 pulseaudio
1 Z  1000 12786 12780  0  80   0 -     0 exit   ?        00:00:00 pulseaudio <defunct>
```

one minute later...

```
$ ps -el | grep pulse
0 S  1000 12912  5036  0  80   0 -  4595 pipe_w ?        00:00:00 pulseaudio
1 S  1000 12914 12912  0  80   0 - 21093 hrtime ?        00:00:00 pulseaudio
1 Z  1000 12918 12914  0  80   0 -     0 exit   ?        00:00:00 pulseaudio <defunct>

```

Maybe my problem is different. My syslog shows:

```
Jun 19 12:51:35 pc-manou pulseaudio[13246]: module-jack-sink.c: jack_client_open() failed.
Jun 19 12:51:35 pc-manou pulseaudio[13246]: module.c: Failed to load  module "module-jack-sink" (argument: "channels=2"): initialization failed.
Jun 19 12:51:35 pc-manou pulseaudio[13246]: main.c: Module load failed.
Jun 19 12:51:35 pc-manou pulseaudio[13246]: main.c: Échec lors de l'initialisation du démon
Jun 19 12:51:35 pc-manou pulseaudio[13244]: main.c: Échec lors du démarrage du démon.
Jun 19 12:51:35 pc-manou rtkit-daemon[4919]: Failed to make ourselves RT: Invalid argument
Jun 19 12:51:35 pc-manou rtkit-daemon[4919]: last message repeated 2 times
Jun 19 12:51:35 pc-manou rtkit-daemon[4919]: Warning: Reached burst limit for user '1000', denying request.
Jun 19 12:51:41 pc-manou rtkit-daemon[4919]: last message repeated 7 times
```

This shows that my problem in an interaction between ''pulseaudio'' and ''jackd''. It is not the same as the problem initially posted in this thread. Sorry!

---

### Post by prshah on 2010-06-19
There is never any point to the pulseaudio --kill command in the usual system. Pulseaudio is set to autospawn (by default) which means that the very next second after you use the --kill command, (or kill the pulseaudio process), it restarts immediately; which is the same action by the (safer) restart / start command.

Please post your /etc/pulse/client.conf and /etc/pulse/daemon.conf files, eg```
cat /etc/pulse/client.conf
cat /etc/pulse/daemon.conf
```

---

### Post by couzin2000 on 2010-06-20
I've been having a problem with Pulseaudio as well, this since installing Lucid.

Lucid is on a laptop, which I connect to my TV using HDMI. This works well, and I can definitely hear the sound correctly through this output. I can also hear the sound correctly through the built-in system speakers. But when I try to listen thru the headphones, I can only hear the background surround track - I cannot hear middle, voice is only at a ultra-low volume and garbled, and I need to be able to hear full volume thru headphones.

I've followed the Alsa upgrade script, I've gone thru this thread as well ([http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")), yet nothing seems to work. At this point I'm now experiencing the same problems as above - "**Waiting for sound system to respond**" is the only message I get now, even though I CAN STILL HEAR SOUND. But now, even the sound device chooser (which was available 5 minutes ago) is gone and unavailable, I only have the error message.

I've gone through a dozen threads, nothing is working... Help!

---

### Post by lidex on 2010-06-22
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by couzin2000 on 2010-06-22
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

It would help me to know why I would be removing these files... for now, I HAVE audio - I wanna ensure I'm keeping it!

---

### Post by lilychef on 2010-06-22
I'm right there with couzin2000, except headphones work fine...  As I've said in my other threads, this happened immediately after an UPDATE to Lucid... It worked like a CHARM right after I Upgraded....but the update definitely screwed thing up... I finally had sutrround sound after three previous Ubuntu versions without it!  Sound works fine now in Totem, VLC, flash, etc, but I cannot access the sound preferences menu or use volume control.... "Waiting for sound system to respond".... Surely this a bug?  I just keep waiting for another update to come out that fixes it...  No logical explanation for it to work then not work like that...  Does Ubuntu not have moderators/developers who monitor these forums?

---

### Post by lidex on 2010-06-25
> **couzin2000 said:**
> It would help me to know why I would be removing these files... for now, I HAVE audio - I wanna ensure I'm keeping it!

That just removes configuration files, which has been an issue of late with cruft remaining on an update. Also I would check permissions of home/user folders.

---

### Post by lilychef on 2010-06-25
> **lidex said:**
> That just removes configuration files, which has been an issue of late with [COLOR="Red"]cruft[/COLOR] remaining on an update. Also I would check permissions of home/user folders.

Uh.... What's "cruft"?  And didn't I just post that this problem started with an update?  Ain't no way in hell I'm going to mess with code unless I know it's going to fix the problem and reverse whatever was messed up by the update in the first place....  I have neither the time nor the energy to reinstall Ubuntu...  I sure wish there were active developers on hand monitoring the forums....  Much of the suggestions found here are vague, ambiguous, or open-ended....

---

### Post by couzin2000 on 2010-06-26
Same thing here, lilychef, too vague for me. I have everything running properly - I'm looking at Pulseaudio monitoring, everything works great - except now I get no sound through the HDMI,*and get the same problematic crap through the headphone jack.

Can someone PLEASE point me to the right direction? Need any info, like ls | grep audio or something like that? Help us out here, this is ridiculous. I'd love to finally watch movies on my plasma tv!

---

### Post by lilychef on 2010-06-27
Now I'm getting sporadic functionality.  Flash and streaming works, but not my regular MP3's!! UGH!!  This happened suddenly and not after a reboot.  What's so ridiculous is that I had such an AWESOME sound system with full control of my speakers, etc. when I first upgraded to Lucid, and now it's gone!  That's just NOT RIGHT.  I'm going to try to keep this thread open until somebody comes along with a fix.

Oh - and did I mention that when the problem first appeared, all system sounds disappeared?  Is that a clue?  Couzin2000 - are you getting system sounds?

---

### Post by couzin2000 on 2010-06-27
Yes, I do have system sounds, though they are turned off. I turn them off systematically every time I reinstall, as it just gobbles up more CPU cycles.

Now, for no reason I can understand (as I've made no modifications to my last know config), I'm getting no sound through the HDMI.

When I look into Pulseaudio I can see the VUmeters and I AM getting signal - I checked out absolutely everything, and the only thing I can think of is that there is a switch somewhere in this software that I'm not getting at.

Again, more help needed, perhaps by a developer or someone who truly know his way around all this?

---

### Post by lilychef on 2010-07-01
Still waiting for support here... Two updates have come and gone with no help...  Is nobody listening?

---

