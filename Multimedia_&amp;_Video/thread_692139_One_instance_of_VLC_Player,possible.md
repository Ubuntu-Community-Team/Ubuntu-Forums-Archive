---
title: "One instance of VLC Player,possible?"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by StOoZ on 2008-02-09
is it possible to run only one instance of VLC player for a given time?
it makes me nervous when I listen to a song, and then pressing on another one , and I ear both of them at the same time...
I still have the winamp habits.. :)

---

### Post by mc4man on 2008-02-09
That option should be available in ver. 0.9, maybe with hardy? You could compile 0.9 from source or install a .deb from nightly builds but they are flaky at best - tried both for the hell of it (the 1 running instance worked), but went back to 0.8.6 for stability

---

### Post by xen-uno on 2008-03-01
The Windows build has the option to force 1 instance, 0.8.6c Linux doesn't.

---

### Post by victor.zamanian on 2008-04-30
> **xen-uno said:**
> The Windows build has the option to force 1 instance, 0.8.6c Linux doesn't.

Darn! I assume it will be the same for all VLC revisions of 0.8 until 0.9. :-/ (As of this writing the latest version of VLC is 0.8.6f and the version in Ubuntu 8.04 repositories is 0.8.6e.)

---

### Post by fede on 2008-04-30
This is possible using a shell script.
(BETTER SCRIPT BELOW, READ MY NEXT POST. If in doubt, use the one below)

```

#! /bin/bash
# this script ensures that only 1 instance of vlc is running at a given time.
# It uses wmctrl. Make sure you have wmctrl installed, if not issue:
# sudo apt-get install wmctrl

WIN_ID_LINE=$(wmctrl -l | grep "VLC media player")
if [ -n "$WIN_ID_LINE" ]; then
	WIN_ID=${WIN_ID_LINE:0:10}
	wmctrl -i -R $WIN_ID	
else
	vlc $1
fi

```

You need to save it where the system will find it (ie in your path); I just saved it to /usr/bin. Like this

```
gksu 'gedit /usr/bin/vlc-start'
```
<paste script text>
Now, make it executable
```
sudo chmod +x /usr/bin/vlc-start
```

Now, edit the vlc shortcut in your menus to use vlc-start as command instead of vlc.

Finally, as I wrote in the script, you need to install wmctrl:
```
sudo apt-get install wmctrl
```

You may also be interested in [this thread]("http://ubuntuforums.org/showthread.php?t=770970&highlight=vlc+replace+totem") to set vlc as your default media player in gnome. (Use vlc-start instead of vlc, obviously). Finally, you can also change your default media player in system > preferences > preferred applicatons to use vlc-start as default.

---

### Post by fede on 2008-04-30
I edited the script to allow to pass command line arguments if there is not another instance running.

There are 2 problems with the previous script:
1. if an instance of vlc is already running, it will not pass arguments to it. This means that if you setup nautilus to use vlc as default, clicking on a media file when an instance is running will not open the new file, only bring the old file to the front. Fix for this below:

```

#! /bin/bash
# this script ensures that only 1 instance of vlc is running at a given time.
# It uses wmctrl. Make sure you have wmctrl installed, if not issue:
# sudo apt-get install wmctrl

WIN_ID_LINE=$(wmctrl -l | grep "VLC media player")
if [ -n "$WIN_ID_LINE" ]; then
	WIN_ID=${WIN_ID_LINE:0:10}
	wmctrl -i -c $WIN_ID	
fi
vlc $1

```

Here I close the older insance of vlc and start a new one each time the script is called. The only problem might be that vlc has a nasty tendency to not die completely (in my system at least, sometimes the process is not killed when I close vlc, sound goes on); I don't know if there might be a way around this

2. if there is another window containing the string "VLC media player" in its title - ie, you might be browsing a vlc page -, the script might not work at all, since it assumes that what has this string in the title is a vlc instance. This is not a big problem for me, I think it is extremely rare.

PS: [bash scripting is fun]("http://www.linuxcommand.org")!

---

