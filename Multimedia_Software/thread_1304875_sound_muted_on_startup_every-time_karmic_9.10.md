---
title: "sound muted on startup every-time karmic 9.10"
date: 2009-10-29
forum: Multimedia Software
---

### Post by dj-toonz on 2009-10-29
Hi all, does anybody know how to get sound to unmute on start up in Karmic? I've just installed it 5 hours ago as a dual boot system with Jaunty (just to see what karmic is like before I deiced to remove Jaunty, but every time I boot the system up, theres a red x in the speaker & no sound (but in jaunty it works great , cheers

---

### Post by lovinglinux on 2009-10-29
Perhaps you could try this:  [http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

It is related to sound clicks, but I think it also prevented my sound card from starting muted.

---

### Post by loseby on 2009-10-29
> **dj-toonz said:**
> Hi all, does anybody know how to get sound to unmute on start up in Karmic? 

same here but it was good that sound worked "out of the box"

[COLOR="Red"]edit: now its not a problem at all...[/COLOR]

---

### Post by jrrader on 2009-11-04
Dj-toonz, did you ever solve this?  I am having the same problem.  I am also having a problem with terrible audio (in Virtualbox and Sauerbraten).  I tried the fix above but no luck.

---

### Post by jrrader on 2009-11-04
Okay, so I found your post through google so I didn't see that big sticky thread about sound. [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

"Using Alsamixer" and then "saving" right below it got sound working at start up.  Haven't found anything to fix the awful sounds yet...

---

### Post by garble on 2009-11-10
I also had a problem with my sound being muted on startup. Take a look at the following page. The solution described in comments 38 and 67 worked for me. Good luck!

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732)

---

### Post by darthmob on 2009-11-11
> **garble said:**
> I also had a problem with my sound being muted on startup. Take a look at the following page. The solution described in comments 38 and 67 worked for me. Good luck!

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732)That fixed it for me as well. Thanks a lot for posting the link! :)

---

### Post by Maxei on 2009-11-11
I have Ubuntu 9.10 karmic and Kubuntu 9.10 installed. Sound muted happens in this situation: First, once I login into KDE, then I halt the computer. Next, switch on the computer and login to Gnome is when I always find the sound has been muted. It is no big deal, just go to System-> Preferences-> Sound then unmute the sound and set again volume to 100 %. But this solution needs to be done each time and is not ideal.

The solution reported by some in this thread (to edit /etc/init.d/alsa-utils and change some line) is not useful for me because the line in question is correct (from install). So, there must be another place to look at. Anyone?

---

### Post by tiggsy on 2009-11-23
Don't know if you found this thread, but it might solve your problem: [http://ubuntuforums.org/showthread.php?t=818333](http://ubuntuforums.org/showthread.php?t=818333)

---

### Post by biodiesel-bri on 2009-12-04
Here's how I fixed my problem, hp dv9610us with an intel hda card:

```
sudo apt-get remove alsa alsa-utils
```
```
sudo apt-get install alsa alsa-utils
```
```
sudo apt-get install pulseaudio
```

Click the Volume control applet on the taskbar, then Mixer and unmute anything checked to mute.

Then I went into system settings/multimedia/music and made sure pulse audio was set to prefer.

I haven't checked if this survives a reboot.

---

### Post by delphiexile on 2010-09-07
ok, i suffered from this problem, but the solution is so easy, 
1- press Alt+F2
2- enter gconf-editor in the command box
3- go to /apps/indicator-sound
4- check the volume-mute option.

that's all !!

---

