---
title: "VLC 2.1.4, autoplay, track order and media keys."
date: 2015-03-01
forum: Multimedia Software
---

### Post by hey2 on 2015-03-01
Hi.

First and foremost i like to apologize for my English level. I will try my best to describe my problem.

I'm a new Ubuntu user and I'm having problems when i insert a audio CD in my computer.

When VLC opens, the tracks appear in a weird order and have no names. This doesn't happen when i  open the disk in the media menu. 

When i choose Rhythmbox to perform similar task, the program opens, the tracks have names and are in order. The only thing that i don't like is that the CD doesn't start playing, i have to press the play button.

I also notice that in VLC, on the left panel, in the Devices part, when i click Disk, it doesn't show anything.

Another problem that i have is that unlike Rhythmbox, VLC doesn't seem to recognize my media keys. Is this normal?

Can somebody say if this is just normal in the 2.1.4 (Software Center) version?

Thank you very much.

---

### Post by Portaro on 2015-03-01
Maybe you VLC dont have all plugins and maybe the cd uses (third party plugins).

Take a look on - [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

My version of VLC is 
$vlc --version
VLC media player 2.1.4...

---

### Post by hey2 on 2015-03-01
> **Portaro said:**
> Maybe you VLC dont have all plugins and maybe the cd uses (third party plugins).

Take a look on - [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

My version of VLC is 
$vlc --version
VLC media player 2.1.4...

Hi. Thanks for the response.

Isn't the VLC (Software Center) supposed to come with everything? 

Since you have the same version as me, does this happen to you?

What i find strange is that when i open the disk from the menu, everything works, but when i choose VLC to be the program that starts when i insert a CD , it shows all the problems that i reported above.

Já agora muito obrigado. ;)

---

### Post by mc4man on 2015-03-02
To use vlc on audio cd's with 'autoplay' & get proper cddb/trackname info you need to create an additional .desktop to do just that. The reason is the command to start vlc in the default  vlc.desktop is not  right for cdda  playback & the command for cdda is not good for normal use.

So it would look like in the screens, I name it Vlc Cd Player & it's just for autoplay, nothing else. If you want to pursue shouldn't be hard with a few copy & paste commands.
The command or script to use for the cd .desktop could vary depending on whether you have just one cd device or more. The later requires a script, the former can use either same script or a simple command.
So let me know...

---

### Post by hey2 on 2015-03-02
Hi.

Thank you very much for your time and help.

Since it's a bug and it seems to be easily resolved do you know if it got fixed in later versions?

Althought in Software Center the only version available is 2.1.4, i've seen that is possible to install the later version (incluiding 2.2.0). Do you know if this was fixed?

Could this also be the cause that i don't see nothing (VLC) in the left panel when i click Disks (Devices)?

Thank you very much once again.

---

### Post by mc4man on 2015-03-03
> Since it's a bug and it seems to be easily resolved do you know if it got fixed in later versions?
I wouldn't call it a bug, more a feature that is unlikely to be provided. So it falls under *if you want it changed you do it for yourself***.**

---

### Post by hey2 on 2015-03-03
> **mc4man said:**
> I wouldn't call it a bug, more a feature that is unlikely to be provided. So it falls under *if you want it changed you do it for yourself***.**

Hi. 

Thank for your response.

I think that the program should behave in the same way if you insert a CD and it starts playing it or if you open the CD in the media menu. 

If i do this in windows they both do the same thing, so there's definitely a problem in the Ubuntu version.

Thank you once more.

---

### Post by mc4man on 2015-03-03
> **hey2 said:**
> 


If i do this in windows they both do the same thing, so there's definitely a problem in the Ubuntu version.

.
Don't see the connection, how windows works is not the same as linux or in this case possibly linux distros that use .desktop files to launch apps.

In any event - how to do using small script that accounts for up to 10 cd devices
Using a local bin, any other bin in $PATH can be used or any location if full path is specified on the Exec= line, maybe chmod +x if root owned location?
using gedit as text editor..
Noting again this .desktop is only for autoplay, nothing else.
```
cd && mkdir -p bin

```
```
gedit ~/bin/vlccd
```

copy & paste this in, save, close gedit - 
```
#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(sr[0-9]\).*/\\1/"`
vlc cdda://$CD



```
```
chmod u+x ~/bin/vlccd
```

```
gedit ~/.local/share/applications/vlc-cd.desktop
```

c&p this, save, close gedit

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Vlc Cd Player
Comment=Auto plays audio cd's
Exec=vlccd %U
Icon=vlc
Terminal=false
Categories=AudioVideo;Player;
NoDisplay=true
MimeType=x-content/audio-cdda;
```

Then do a restart & see if Vlc Cd Player is an option for autoplay in system settings > details > removable media > cd audio (probably other application section

If not it will appear at some point or just 'force' it
```
gedit ~/.local/share/applications/mimeapps.list
```

In [Default Applications] section look for line - 
x-content/audio-cdda=
If there remove current .desktop, add vlc-cd.desktop, if not there add new line
ex.
> x-content/audio-cdda=vlc-cd.desktop
(if there was no [Default Applications] section  then just add it or set something as default for any mime, ect.

---

### Post by hey2 on 2015-03-03
Oh man :D

Thanks a lot for all your time, but you're speaking with a real noob here :D

One thing that made me decide to install Ubuntu was that unlike other Linux OS this is so approachable. Everything works just by clicking in some buttons and there's no need for terminal stuff.

I just think that if in windows, Ubuntu Rhythmbox and VLC itself (Media menu), everything works, then this has to be bug.

If it's possible to change this by ourselves and it's logic, why not make it default?

Thank you once more for your time.

---

