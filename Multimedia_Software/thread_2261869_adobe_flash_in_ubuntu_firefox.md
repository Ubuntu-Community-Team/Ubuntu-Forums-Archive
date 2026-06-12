---
title: "adobe flash in ubuntu firefox?"
date: 2015-01-21
forum: Multimedia Software
---

### Post by anbu-s on 2015-01-21
I can't seem to play live tv streaming from the following websites using firefox on my ubuntu laptop.

[http://www.tsn.ca/tv#/](http://www.tsn.ca/tv#/)
now.sportsnet.ca

Both websites need adobe flash player and even though i have installed adobe flash on my ubuntu laptop and enabled firefox addons, it still doesnt work. For tsn website it keeps saying i need the latest version of adobe and for sportsnet i can't go past the login screen.

Other sites such as ctv.ca work for live streaming which also uses adobe flash.

Can anyone help me here please?

I dont have any script blocker or other services that blocks streaming.

---

### Post by sudodus on 2015-01-21
How did you install flash?

```
sudo apt-get install flashplugin-installer
```

is the best way to do it in Ubuntu unless you also want other restricted software and install all the 'restricted extras' with

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by anbu-s on 2015-01-21
I did it using the same command.

Just noticed, the tsn website streaming works with google chrome browser. Not with Firefox
For sportsnet streaming, even with chrome it cannot get past the login screen - after keying in the username and password its supposed to unlock the content and start playing. But it always goes back with a lock on the program you want to watch.

---

### Post by sudodus on 2015-01-21
There are probably some non-standard or new hand-shaking at those web sites, that are not implemented in the linux versions of flash. I think it could a problem because flash is proprietary software, and the linux community cannot do much about the problem. The linux versions lag behind the versions for Windows and MacOS for commercial reasons.

---

### Post by raptir on 2015-01-21
> **sudodus said:**
> There are probably some non-standard or new hand-shaking at those web sites, that are not implemented in the linux versions of flash. I think it could a problem because flash is proprietary software, and the linux community cannot do much about the problem. The linux versions lag behind the versions for Windows and MacOS for commercial reasons.

Unfortunately it's not just that they lag behind... support for the NPAPI flash plugin (which Firefox uses) has been discontinued under Linux.

[http://www.adobe.com/devnet/flashplatform/whitepapers/roadmap.html](http://www.adobe.com/devnet/flashplatform/whitepapers/roadmap.html)

Flash in Firefox is stuck on 11.2, which many sites are starting to see as outdated. The sites will work in Chrome because Chrome bundles the PPAPI Flash plugin which is kept up to date.

---

### Post by monkeybrain20122 on 2015-01-21
You can try Chrome which is bundled with its own flash (pepper flash) Without switching browser you have two options: use pipelight flash or pepper flash on Firefox

[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)
[http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html](http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html)

pipelight flash is basically Windows' flash running in wine. Install pipelight by running the commands from first link. 
To enable flash, close Firefox and run 
```
pipelight-plugin --enable flash
```
and restart Firefoxtions.

to revert to system flash (which works better if it works)
close Firefox and run
```
pipelight-plugin --disable-flash
```

(no need to run with sudo as instructed in pipelight's site)

The fresh-player-plugin is a wrapper for Chrome's pepper flash. It worked very well in Fedora 20 but I have experienced some glitches after installing from git yesterday on Fedora 21. I have not used it in Ubuntu.


**Edited:** for some streaming sites even Chrome's flash doesn't work as the Linux version it ships is stripped of drm support. In that case pipelight flash would work and is probably the only (or easiest) way at the moment. (the developer of freshplayer-pluggin claims that instead of using flash from Chrome you can extract it from a Chromebook image and it would work with drmed streams, but I have tried that and got only black screens and audio, maybe I did something wrong)

---

### Post by anbu-s on 2015-01-21
Why is the now.sportsnet.ca stream not working in any browser? That's the most puzzling aspect of this. It works fine in windows and OSX

---

### Post by monkeybrain20122 on 2015-01-21
Because it is drmed? pipelight flash would work.

---

### Post by anbu-s on 2015-01-21
> **monkeybrain20122 said:**
> Because it is drmed? pipelight flash would work.

That worked !!
You guys are amazing..Thanks a lot.

The only complaint now is the screen automatically goes blank after a few minutes (my laptop is set to go blank after 10min of inactivity) even when its playing a video in firefox or chrome. Windows will not activate the screensaver if a video is playing. With linux, i guess this is the default behaviour.

---

### Post by monkeybrain20122 on 2015-01-21
Well video players such as vlc and mplayer disable screensaver. I don't know whether native flash does that. Never watch anything long with flash. Pipelight is not able to disable screensaver as far as I know (e.g watch netfix on Chrome screensaver is disabled, but not on Firefox with the pipelight silverlight plugin) You may want to ask the developers. [https://answers.launchpad.net/pipelight](https://answers.launchpad.net/pipelight)
You can log in there with you Ubuntu forum login credentials.

---

### Post by vinnywright on 2015-01-22
this may work as well [https://www.kubuntuforums.net/showthread.php?66849-HOW-TO-Use-the-latest-version-of-Flash-with-Firefox&highlight=amazon](https://www.kubuntuforums.net/showthread.php?66849-HOW-TO-Use-the-latest-version-of-Flash-with-Firefox&highlight=amazon) ,,,,,,,,,,,se post #30

VINNY

---

### Post by ericbradshaw on 2015-01-23
I know of three different remedies for the screen blanking. I've looked at this only from Lubuntu, but you should be able to utilize any of these with minor changes. The most drastic, is [deactivating the screen lock altogether]("http://lnbu.jimdo.com/turorials/lubuntu/screen-lock-deactivation/"). The next solution would be sort of [replacing Light Locker with XScreenSaver]("http://askubuntu.com/questions/502942/lubuntu-enforces-screen-lock"). Finally, my favorite - vasa1 developed the following script using xdotool by Jordan Sissel to move the mouse if CPU usage exceeds 5%; which is what normally happens when watching video via Netflix, or YouTube, etc. He was helped greatly by Vaphell on these forums and terdon on StackExchange. Here's my step-by-step for this one I call Mouse Mover:
1. sudo apt-get install xdotool
2. sudo leafpad /usr/bin/batinfo.sh
3. Copy and paste the following:

```
#!/usr/bin/env bash

sleep_period=8m 

while true; do
  if ps -eo %C --sort -%cpu | head -2 | awk 'NR==2 { exit !($1>10); }'; then
      xdotool key shift
  fi
  sleep ${sleep_period}
done
```

4. Save.
5. Open PCManFM as root
```
gksu pcmanfm
```
6. Navigate to /usr/bin/batinfo.sh,
7. Right-click and choose "Properties" from the drop-down. Click the "Permissions" tab and then choose "Anyone" from the Execute dropdown. Click the "OK" button.
8. Make a "mouse-mover" folder, put a "mouse-mover" icon called mouse-mover.png inside and place the folder in /usr/share/icons.
9. Place a shortcut named mouse-mover.desktop with the following contents in /usr/share/applications:

```

[Desktop Entry]
Type=Application
Name=Mouse Mover
GenericName=Mouse Mover
Comment=Mouse Mover
Icon=/usr/share/icons/mouse-mover/mouse-mover.png
Exec=sh -c "cd /usr/bin/; ./batinfo.sh"
Categories=GTK;Qt;AudioVideo;Player;Video;

```

Before watching Netflix, YouTube videos, etc., select Menu --> Sound & Video --> Mouse Mover

vasa1 later shared with me he replaced the mouse movement with a [Shift] key press. You may need to adjust the %CPU usage depending on how fancy the computer is. Here's the modified code:

```
#!/usr/bin/env bash

sleep_period=8m

while true; do
  high="$(ps -eo %C --sort -%cpu | awk 'NR==2')"
  if ps -eo %C --sort -%cpu | awk 'NR==2 { exit !($1>5); }'; then
      xdotool key shift
  fi
  sleep ${sleep_period}
done
```

---

### Post by Nutria on 2015-01-24
> **ericbradshaw said:**
> 
1. sudo apt-get install xdotool
2. sudo leafpad /usr/bin/batinfo.sh


Very, very clever!

A bit lubuntu specific, though.  Better to have them use the system default editor:
```
sudo **editor** /usr**/local**/bin/batinfo.sh
```

Note that /usr/bin, /usr/lib, etc are only for files installed by "the system".  Home-grown s/w and stuff installed from source must go in /usr/local.

(Too bad there's not a /usr/bin/x-editor corresponding to /usr/bin/editor like there is /usr/bin/x-www-browser corresponding to /usr/bin/www-browser (all of which are symlinks into /etc/alternatives).

> 
```

[Desktop Entry]
Type=Application
Name=Mouse Mover
GenericName=Mouse Mover
Comment=Mouse Mover
Icon=/usr/share/icons/mouse-mover/mouse-mover.png
Exec=sh -c "cd /usr/bin/; ./batinfo.sh"
Categories=GTK;Qt;AudioVideo;Player;Video;

```


Why "cd /usr/bin/; ./batinfo.sh" instead of directly executing "/usr/local/bin/batinfo.sh"?

---

### Post by ericbradshaw on 2015-01-24
*Very, very clever!*
Thanks, but it was [vasa1]("http://ubuntuforums.org/member.php?u=449866") who did all the work. I just stumbled upon his initial scripting efforts while searching for a solution on behalf of someone else. I tested it out on my own computer and liked it so much, I made a Mouse Mover [icon]("http://webpages.charter.net/ericebradshaw/img/mouse-mover.png") and that shortcut above.
*A bit lubuntu specific, though.  Better to have them use the system default editor:*
I agree. Your suggestion is pretty progressive though. I'm not sure too many people here will start replacing **gedit** with **editor** anytime soon.
*Note that /usr/bin, /usr/lib, etc are only for files installed by "the  system".  Home-grown s/w and stuff installed from source must go in  /usr/local.*
Good to know.
*Why "cd /usr/bin/; ./batinfo.sh" instead of directly executing "/usr/local/bin/batinfo.sh"?*
No idea. Copied and pasted from (an)other source(s). It worked, so I didn't think about it again.

---

### Post by ericbradshaw on 2015-01-27
*An unfortunate follow-up for the screen blanking thing*. The "Mouse Mover" script didn't work for the lady I had originally made it for and neither did completely removing Light Locker (at least not by following the directions linked previously). Her screen still blanked every 10 minutes no matter what. She had a Dell OptiPlex 210L. I ended up moving her HDD into a Dell OptiPlex GX520, but had the same results. The only way I could get her screen to *not* blank every 10 minutes, was install XScreenSaver and then disable it! *XScreenSaver will also work to set the screensaver to come on at any interval as far as I can tell. Like 120 minutes, or 240 minutes. However, the lady I was setting this up for didn't want any screensaver.*

*Apologies in advance for the non-generic instructions.  I use Lubuntu exclusively*.

So, first I removed the Light Locker shortcut.

```
sudo rm /etc/xdg/autostart/light-locker.desktop
```

installed XScreenSaver

```
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra xscreensaver-screensaver-bsod -y
```

went to Menu --> Preferences --> Default applications for LXSession, choose the Autostart tab and added

```
xscreensaver -no-splash
```

into Manual autostarted applications, restarted and then went to Menu --> Preferences --> Screensaver and in Display Modes tab made sure the Mode was set to Disable Screen Saver.

---

### Post by anbu-s on 2015-06-22
I installed pipelight and enabled the plugin as per this thread in my new installation of gnome 15.04. But the flash doesnt work in both firefox and chrome. Not sure why? Any ideas?

---

### Post by Matejko on 2015-06-24
For me it isn't working, but... I don't think that is problem. Today we have html5 with video support and amazing possibilities of 2d/3d canvas, so why use old fashioned, poor, unsafe and problematic flash plugin?

---

