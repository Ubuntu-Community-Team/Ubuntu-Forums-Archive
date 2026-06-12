---
title: "WICD error after upgrading to 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by leeds on 2009-04-24
Upgraded to version 9.04 - now WICD cannot find wireless connection. I'm new to Linux and require urgent help to get this to work. Thank you in advance.

---

### Post by rlzyoner on 2009-04-24
Maybe try reinstall wicd.
NetworkManager and wicd don't get along to the best of my knowledge, maybe the upgrade installed some network manager stuff

---

### Post by leeds on 2009-04-25
Thank you. That is correct, when I first installed WICD I had to remove network manager completely. The problem on my system (after the upgrade) seemed to be that I needed to use a proprietary driver. This has worked (for now): Going into "System" > "Administration" > "Hardware drivers" - in my case only shows the wifi driver. I enabled the proprietary driver and after rebooting wireless is working fine.

---

### Post by skatebiker on 2009-04-25
Same with me, wicd was even uninstalled after upgrading to 9.04 so I reinstalled it and started wicd-client. Then it constantly tried to connect with my router until it crashed.
I restarted the computer and tried connecting again with wicd but no wireless connection. So I plugged in the ethernet cable and then even it was unable to connect to wired.

---

### Post by antonym on 2009-04-28
Hi,

I'm having a different problem, but still after upgrade to Jaunty.
Wicd won't start up on my laptop -- I've tried uninstalling and reinstalling, with no success. If I try to run it from the menu nothing seems to happen; running it from the terminal gives the following error:

```

antonym:~$ wicd
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-daemon.py", line 55, in <module>
    import wicd.path as wpath
ImportError: No module named wicd.path

```

anyone have any idea what this might mean, or why it persists even after reinstalls in jaunty when it's always worked fine in intrepid?

Thanks in advance.

---

### Post by leeds on 2009-04-28
Sorry if you have already tried this. Maybe try a clean install of WICD with the instructions in: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by markstj on 2009-04-30
I found a workaround in the Wicd forums and it worked perfectly. I am pasting it here. If you run *python -c "import sys; print sys.path" *and the path is different from Python2.6 you would need to change to the correct one when you enter the command in terminal.
 
Here you go:
 
The problem was wicd had installed its self in in a different folder to where the path variables were pointing:
wicd had installed it self in:
**/usr/lib/python2.5/site-packages/wicd**
however running
*python -c "import sys; print sys.path"*
in a terminal gave me:
**'', '/usr/lib/python2.6', '/usr/lib/python2.6/plat-linux2', '/usr/lib/python2.6/lib-tk', '/usr/lib/python2.6/lib-old', '/usr/lib/python2.6/lib-dynload', '/usr/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages/Numeric', '/usr/lib/python2.6/dist-packages/PIL', '/var/lib/python-support/python2.6', '/var/lib/python-support/python2.6/gtk-2.0'**
nowhere in that list is 
**/usr/lib/python2.5/site-packages/**
however:
**/usr/lib/python2.6/dist-packages**
is.
now I don't know how to add a path/system variable so I did the following:
again in console: (you will likely have to be root or use sudo)
[I]
mkdir /usr/lib/python2.6/dist-packages/wicd
cp -s /usr/lib/python2.5/site-packages/wicd/* /usr/lib/python2.6/dist-packages/wicd
[/I]
this will create links to the real files in the correct folder and wicd will be none the wiser to the fact.  It works fine.

---

### Post by antonym on 2009-04-30
thanks, markstj!

I had actually found that same thread last night, and that worked for me :D
I had to restart before it seemed to be effective, but when I did wicd was there in the taskbar.

the other solution I'd come across that would likely accomplish something similar would be to install the testing version manually through python (I found a separate thread detailing that). Thankfully the method above worked though and I didn't need to download anything else.

---

### Post by markstj on 2009-05-01
Jaunty is worthy the effort. It is very responsive -- overall I am very pleased.

---

