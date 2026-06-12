---
title: "[SOLVED] How do I run a command at startup?"
date: 2008-06-02
forum: Mythbuntu
---

### Post by teet on 2008-06-02
I just upgrade to mythbuntu 8.04 and I'm having trouble figuring out how to run a command at startup.  I created a simple script that runs a nvtv command to "oversize" the svideo output so mythtv fills my screen (no ugly black/blue edges).  I made the script executable and put it in /usr/local/bin.  After a fresh reboot, I just have to go to the command line and type "nvtv-alex" and it works perfectly.

How do I make this "nvtv-alex" command run at startup?  In the past, I just added it to the "session", but that option seems to be gone in 8.04???

-teet

---

### Post by superm1 on 2008-06-03
Is this is using nvidia-settings?  

If so, when you save settings, the file will be sourced on boot (~/.nvidiasettingsrc or something like that)

If not, then add a symlink to ~/.config/autostart

---

### Post by teet on 2008-06-03
> **superm1 said:**
> Is this is using nvidia-settings?  

If so, when you save settings, the file will be sourced on boot (~/.nvidiasettingsrc or something like that)

If not, then add a symlink to ~/.config/autostart

Nope.  This is using nvtv (it's an older Geforce 2 MX card that uses the nvidia-legacy drivers).

I'll try the autostart thing in the morning.  Thanks for the reply :)

-teet

---

### Post by teet on 2008-06-03
The autostart thing doesn't seem to be working.

Using this page ( [http://lurker.gentoo-wiki.com/HOWTO_Autostart_Programs](http://lurker.gentoo-wiki.com/HOWTO_Autostart_Programs) ) as a guide, I made a file called 'nvtv-alex' in the .config/autostart folder.  The contents of the file are as follows:

```

#!/bin/bash
nvtv -t -r 640,480 -T BROOKTREE -S NTSC -C SVIDEO -s Huge

```

I then ran 'sudo chmod +x nvtv-alex' to make the file executable.  I rebooted, but the command did not run.

I also have the same nvtv-alex file in the /usr/local/bin folder so I tried modifying the .config/autostart/nvtv-alex as follows

```

#!/bin/bash
/usr/local/bin/nvtv-alex

```

I rebooted and it still didn't work.

After a fresh reboot, if I exit from mythfrontend, open a terminal, and type 'nvtv-alex' and then hit enter the screen resizes properly.  What am I missing here?

-teet

Edit:  I also tried using thunar to make a link from /usr/local/bin/nvtv-alex to ~/.config/autostart/nvtv-alex.  If I double click on the ~/.config/autostart/nvtv-alex file the screen resizes properly.  However, it doesn't do it automatically at boot!

---

### Post by fenian on 2008-06-03
You can try this open a terminal and enter...

> sudo gedit /etc/rc.local

after all the commented out lines (lines with a # at the beginning) add the line...

> nvtv-alex

---

### Post by superm1 on 2008-06-03
Ah I think I realize what the issue was.

You need a .desktop file in the ~/.config/autostart.

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=ma magic app
GenericName=magic
Comment=does stuff
Exec=nvtv-alex
Type=Application
```
something like that should do

---

### Post by teet on 2008-06-04
> **superm1 said:**
> Ah I think I realize what the issue was.

You need a .desktop file in the ~/.config/autostart.

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=ma magic app
GenericName=magic
Comment=does stuff
Exec=nvtv-alex
Type=Application
```
something like that should do

It works!  Thanks superm1!

-teet

---

