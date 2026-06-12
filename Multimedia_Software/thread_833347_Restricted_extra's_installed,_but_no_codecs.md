---
title: "Restricted extra's installed, but no codecs"
date: 2008-06-18
forum: Multimedia Software
---

### Post by Snader on 2008-06-18
Hello,

My sound system is working, but it is unable to play audio cd's, mp3's and possibly other formats. Amarok gives me errors like: "Amarok currently cannot play mp3 files." or "No suitable input plugin." in the case of audio cd's. The problem also occurs on other media players, like: Totem and VLC. Those programs fail without an error.

Odd thing is, my system was able to play those formats (a week ago). ubuntu-restricted-extra's and libxine1, libxine1-bin, libxine1-console, libxine1-ffmpeg, libxine1-misc-plugins, libxine1-plugins and libxine1-x are installed.

I'm puzzled, so any help would be appreciated. :)

Sander

---

### Post by prshah on 2008-06-18
> **Snader said:**
> 
My sound system is working, but it is unable to play audio cd's, mp3's and possibly other formats. Amarok gives me errors like: "Amarok currently cannot play mp3 files." or "No suitable input plugin."

Open Amarok from a terminal, and post back error messages if you get any.

This is meant to be a troubleshooting step, but surprisingly, just opening it from a terminal has fixed sound problems for some.. see [http://ubuntuforums.org/showthread.php?t=825439](http://ubuntuforums.org/showthread.php?t=825439)

If that doesn't work out (none or irrelevant error messages) try reinstall the restricted extras module```
sudo apt-get install --reinstall ubuntu-restricted-extras 
```

---

### Post by Pjotr123 on 2008-06-18
Check if you've got them all:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by Snader on 2008-06-18
Something tells me that my problems are related to the insane amount of updates we had recently. It seems that someone else has the same problem:
[http://www.ubuntu-forums.com/showthread.php?t=833322](http://www.ubuntu-forums.com/showthread.php?t=833322)

Reinstalling ubuntu-restricted-extras had already been tried, but it had no succes. Still, thanks for the idea. :)

This is the output of my console when I: startup Amarok, add mp3's (giving errors) and then I close the program.

```
XXX-XXX:~$ amarok %U
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bd58 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bd58 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
XXX-XXX:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3c008a9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3c008a9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3c008a9
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
ICE default IO error handler doing an exit(), pid = 7446, errno = 11
```



P.S. The forum logs me out immediately after I log in. I have deleted the forumcookies and checked "remember me", but the problem persists.

---

### Post by prshah on 2008-06-18
> **Snader said:**
> 

```
XXX-XXX:~$ amarok %U
ICE default IO error handler doing an exit(), pid = 7446, errno = 11
```


What are the permissions for user on ~/.ICEauthority ? ```
ls -l ~/.ICEauthority
``` should show "-rw-------", and should be user'd and group'd by your username. if it isn't, try granting rw permissions to the file for your user```
chmod +r +w ~/.ICEauthority 
```

---

### Post by Snader on 2008-06-18
@Pjotr: It seems that I have all the listed software installed, except:
- Mplayer Movie player
- gxine
- Audacious
- mozilla-plugin-vlc
My substitutes for these programs are: Amarok and VLC.

On the second page they list: w32codecs. Searching for w32codecs gives me no result in Synaptec. Searching in Medibuntu is not (yet) possible. I have not installed this on my system, because I'm used to installing everything manually.
As far as I know, w32codecs is installed on my system. Besides, it's only needed to play some video formats.

If you think that I might solve the problems by installing some or all of the above software, I will do so. :)

---

### Post by Snader on 2008-06-18
It looks like the permissions are allright:
```
-rw------- 1 XXX XXX 867 2008-06-18 20:56 /home/sander/.ICEauthority
```
Also, it is user'd and group'd by my username. Is replaced it by XXX for security reasons.

---

### Post by prshah on 2008-06-18
> **Snader said:**
> It looks like the permissions are allright:
```
-rw------- 1 XXX XXX 867 2008-06-18 20:56 /home/[color=red]sander[/color]/.ICEauthority
```
Also, it is user'd and group'd by my username. Is replaced it by XXX for security reasons.

Try this```
sudo apt-get install --reinstall gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly-multiverse
``` to install various codecs.

btw, im psychic: XXX=sander.

---

### Post by Snader on 2008-06-18
You're good... :p Ok, it was quite silly to mask my username if it's that simple. Although, I saw someone doing this on the forum and it seemed a good idea.

I installed or actually reinstalled those codecs, but with no result. Again, thanks for your patience.

P.S. My login problem just disappeared without a reason.

---

### Post by prshah on 2008-06-18
> **Snader said:**
> 
I installed or actually reinstalled those codecs, but with no result. 


Amarok can work with two backends; gstreamer is one, and xine the other. Since you've already said that you don't have xine installed, I assumed that reinstalling the gstreamer backends would do the trick.

Now, maybe you should switch to xine/Amarok. I've never had to go so deep into this kind of problem, so I'm a little hesitant to give info on something I've not done myself. I _assume_ that installing libxine or something will give you xine backend, and then some options in Amarok will enable it. You can feel free to futz around with the above, and, in the meantime, I'll fiddle about a bit too and see what develops.

---

### Post by Snader on 2008-06-19
After some fiddeling around, I managed to get Amarok working (with Xine) again. Actually, I don't really know how I solved it, but my last changes were: configuring all my sound settings to ALSA and deleting the home folders of Amarok and Xine. I guess the last one did the trick. :)

This remains me with one last question: Can you explain me what ICEauthority does? Aside from a lot of ownership problems, I can't find any information on that.

Again, thanks for all your time and thoughts. :)

---

