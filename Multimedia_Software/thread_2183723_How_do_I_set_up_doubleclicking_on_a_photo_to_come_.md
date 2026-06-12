---
title: "How do I set up doubleclicking on a photo to come up in &quot;feh&quot; for fast access?"
date: 2013-10-26
forum: Multimedia Software
---

### Post by Jim_Granite on 2013-10-26
How do I set up doubleclicking on a photo to come up in "feh"?

[LIST]
[*]What I want is the FASTEST photo viewer to pop up the photo when doubleclicked.
[*]And, then to be able to STEP through the photos, by pressing a single keyboard key.
[*]And, for each of the photos to fit in the viewing window.
[/LIST]

Here are my rough results from a quick test:

[LIST=1]
[*]Gimp = 7 seconds, asks to rotate, autofits, does not step with spacebar
[*]ImageViewer = 2 seconds, auto-rotates, autofits, does not step with spacebar
[*]KolourPaint = 2 seconds, not auto-rotated, does not auto-fit, does not step with spacebar
[*]Shotwell Viewer = 2 seconds, auto-rotates, autofits, steps with space bar
[*]Image Magick = 1 second, does not auto-rotate, does not auto-fit, does not step with spacebar
[*][feh -F *]("http://feh.finalrewind.org/") = 1 second, auto-rotates, steps with spacebar
[/LIST]

Given those tests, "feh" seems like a good bet; but using "feh" is not an option from the GUI.
[ATTACH=CONFIG]247245[/ATTACH]

**QUESTION**: 
How would I set up Ubuntu 13.10 so that doubleclicking on a picture in Nautilus/Files brings up Feh in this format?
$ feh -F filename.JPG

Note: The ultimate goal would be feh, with some keyboard shortcuts defined, e.g., 
$ feh -F filename.JPG --action1 "mv %f ./save/." --action2 "mv %f ./trash" --action3 "cp %f ./copy"

---

### Post by jewisharific on 2013-10-26
Here's what worked for me.

I made a script named [FONT=Fixedsys]**fehsh**[/FONT] in my home directory:
```

#!/bin/bash

feh -F $1 --action1 "mv %f ./save/." --action2 "mv %f ./trash" --action3 "cp %f ./copy"
```

Then I used [Ubuntu Tweak]("http://ubuntu-tweak.com/") to associate *.JPG's with the script.
The file association editor in Ubuntu Tweak is under **Admins > File Type Manager**.

**Edit:**  You will need to make the script executable before changing the association:

```
$ chmod +x fehsh
```

---

### Post by Jim_Granite on 2013-10-27
> **jewisharific said:**
> Here's what worked for me.

Following in your footsteps, here's what I did:

1. I determined what my path was:
$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

2. I put the fehsh script in the path:
$ sudo vi /usr/local/bin/fehsh
#!/bin/bash
feh -F $1 --action1 "mv %f ./save/." --action2 "mv %f ./trash/." --action3 "cp %f ./copy/."
exit 0

3. I changed the permissions to be executable:
$ sudo chmod u+x /usr/local/bin/fehsh

4. I checked permissions:
$ ls -l /usr/local/bin/fehsh
=> -rwxr--r-- 1 root root 111 Oct 27 06:06 /usr/local/bin/fehsh

> **jewisharific said:**
> Then I used [Ubuntu Tweak]("http://ubuntu-tweak.com/") to associate *.JPG's with the script.
Is this better than the Unity Tweak tool for this purpose?
$ sudo apt-get install unity-tweak-tool
$ /usr/bin/unity-tweak-tool

> **jewisharific said:**
> 
The file association editor in Ubuntu Tweak is under **Admins > File Type Manager**.

I'd rather use apt-get to install, but I couldn't figure out how.
1. So I installed by going to [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
2. I downloaded ubuntu-tweak_0.8.6-1_all.deb
3. I installed the deb package:
$ sudo dpkg -i ubuntu-tweak_0.8.6-1_all.deb
4. I checked the installation:
$ which ubuntu-tweak
=> /usr/bin/ubuntu-tweak
5. I ran the application:
$ ubuntu-tweak

Drat!
What did I do wrong?
```

$ ubuntu-tweak
[DbusProxy][ERROR] org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1 (dbusproxy.py:43)
ERROR:root:Could not find any typelib for GConf
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 92, in on_startup
    from ubuntutweak.main import UbuntuTweakWindow
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 36, in <module>
    from ubuntutweak.preferences import PreferencesDialog
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/preferences.py", line 32, in <module>
    from ubuntutweak.factory import WidgetFactory
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/factory.py", line 24, in <module>
    from ubuntutweak.gui.widgets import *
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/gui/widgets.py", line 9, in <module>
    from ubuntutweak.settings.gconfsettings import GconfSetting, UserGconfSetting
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/gconfsettings.py", line 4, in <module>
    from gi.repository import GConf
ImportError: cannot import name GConf
TypeError: can't convert return value to desired type
/usr/bin/ubuntu-tweak:123: Warning: g_value_copy: assertion 'G_IS_VALUE (src_value)' failed
  app.run(sys.argv)
/usr/bin/ubuntu-tweak:123: Warning: g_value_reset: assertion 'G_IS_VALUE (value)' failed
  app.run(sys.argv)
/usr/bin/ubuntu-tweak:123: Warning: g_value_unset: assertion 'G_IS_VALUE (value)' failed
  app.run(sys.argv)

```

---

### Post by jewisharific on 2013-10-27
[QUOTE=Jim_Granite]Is this better than the Unity Tweak tool for this purpose?[/QUOTE]
I don't think that has a file type manager.

[QUOTE=Jim_Granite]I'd rather use apt-get to install, but I couldn't figure out how.[/QUOTE]

First, get rid of the package you installed:
```

$ sudo apt-get purge ubuntu-tweak
```

Then add the repository and install from there:

```

$ sudo add-apt-repository ppa:tualatrix/ppa
$ sudo apt-get update
$ sudo apt-get install ubuntu-tweak
```

---

### Post by Jim_Granite on 2013-10-27
> **jewisharific said:**
> I don't think that has a file type manager.
Thanks for explaining that!
I don't know HOW Ubuntu figures out which application to execute when one doubleclicks on it.

> **jewisharific said:**
> get rid of the package you installed
OK. I don't know how you know this stuff, but, your instructions worked fine to install the application without error:
```

$ sudo apt-get purge ubuntu-tweak
$ sudo add-apt-repository ppa:tualatrix/ppa
$ sudo apt-get update
$ sudo apt-get install ubuntu-tweak
```

Then, I ran the ubuntu-tweak tool, and it already knew about feh (but not about fehsh), so I made the association (to feh) as shown below:
$ /usr/bin/ubuntu-tweak
  [ubuntu-tweak]Admins->System->File Type Manager->Image->JPEG Image->
  Open with = Feh
[ATTACH=CONFIG]247312[/ATTACH]

---

### Post by Jim_Granite on 2013-10-27
Setting the file association to "feh" seemed to work, but I wanted the extra capability of the custom command, which failed. 
I need to debug further, but, here's how I tried to get the custom command to work when a JPG is doubleclicked:
```

$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
$ sudo vi /usr/local/bin/fehsh
#!/bin/bash
feh -F $1 --action1 "mv %f ./save/." --action2 "mv %f ./trash/." --action3 "cp %f ./copy/."
exit 0
$ sudo chmod 755 /usr/local/bin/fehsh
$ ls -l /usr/local/bin/fehsh
=> -rwxr-xr-x 1 root root 111 Oct 27 06:06 /usr/local/bin/fehsh
$ ubuntu-tweak
$ /usr/bin/ubuntu-tweak
  [ubuntu-tweak]Admins->System->File Type Manager->Image->JPEG Image->
  [Edit]->[Add]->Use a custom command->/usr/local/bin/fehsh

```

[ATTACH=CONFIG]247313[/ATTACH]

---

### Post by Jim_Granite on 2013-10-27
I tried again, and this time it worked, I think. 
At least I now have a new custom command, named "fehsh" as an option.
[ATTACH=CONFIG]247321[/ATTACH]
[ATTACH=CONFIG]247322[/ATTACH]
The JPG files are coming up in Feh using fehsh, but, I can't step through them with the space bar yet, so, something is amiss in the script itself.

---

### Post by jewisharific on 2013-10-29
Looks good!  Yeah, you'll have to alter the script.  I'm not familiar with feh's options, I just used when you gave me.

**Edit:** Alright, I got curious and took a look.  When you target a file (feh foo.jpg), it does not start in slideshow mode.  For that, you need to target a directory.  You can use the "--start-at" flag to pick which file to start the slideshow at.

So your script should look like this:
```

#!/bin/bash

feh -F --start-at $1 * --action1 "mv %f ./save/." --action2 "mv %f ./trash" --action3 "cp %f ./copy"
```

HOWEVER, this doesn't work.  It works from the terminal (fehsh foo.jpg), but I get odd behavior when I double click.
If I click on a GIF, it'll open, but it isn't fullscreen.  Nothing happens when I click on JPGs.  I'm not sure why this is.

---

### Post by Jim_Granite on 2013-10-29
> **jewisharific said:**
> you need to target a directory.  You can use the "--start-at" flag 

That's interesting. Thanks for trying. I tried for a while, but, in the end, I just gave up and put it back to the default. 
We can't win every battle. 
I do appreciate the help!

---

### Post by mc4man on 2013-10-30
It may work if you r. click, open the dir. with fehsh, however by default nautilus no longer allows  'open with' on folders from the context menu
(this presumes that your tweak tool created a .desktop for fehsh, likely in .local/share/applications, though for inculsion in the context menu the Exec= line in that .desktop must end in %<letter>, U or F would be okay

Other file managers still allow this or it's simple to return to nautilus, have so in a few ppa builds though re-enabling 'open with on folders' isn't the only changes in those builds.

---

### Post by mc4man on 2013-10-30
Opps - forgot I did, on request, create a standalone nautilus ppa for the open with fix sans my other changes
[https://launchpad.net/~mc3man/+archive/nauty-open](https://launchpad.net/~mc3man/+archive/nauty-open)

Edit: saucy needed a new build, ordered, sched. in 6 hrs or so (both i386 & amd64 must complete for amd64 use as nautilus-data is i386

---

