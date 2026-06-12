---
title: "How to get rid of startup sound?"
date: 2009-11-03
forum: Multimedia Software
---

### Post by donniezazen on 2009-11-03
Hi,

I get this annoying drum sound at startup. How do i get rid of it in Karmic. There was an option to shut if off in Jaunty login screen but login screen has been changed in Karmic. I have already changed the sound preferences.

Thanks,
SK.

---

### Post by sambita on 2009-11-03
Have you tried disabling Gnome Login Sound from System->Preferences->Startup applications (im not sure of the name in english but you can trigger it with gnome-session-properties from Alt+F2). Having disabling that and choosing "No sounds" as my sound theme i hear no annoying login sounds.

---

### Post by Donalb on 2009-11-05
It used to be in System>Administration>Sessions (but that's now gone).

Install Ubuntu-Tweak and you can do there with one click.

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

(I've nothing to do with Tweak, but use it for this kind of thing, actually this exact thing.)

---

### Post by epohs on 2009-11-06
I've installed Ubuntu Tweak, but I don't see a setting to disable startup sound.

---

### Post by Donalb on 2009-11-06
It's in Startup>Autostart>GNOME Login Sound.

---

### Post by epohs on 2009-11-06
Oh, nevermind, disabling Gnome Login Sound in startup applications worked.

Thanks!

---

### Post by Revan13 on 2009-11-16
I do not understand, I disabled the login sound but the system still plays on each startup. Very annoying :( Has anyone encountered the same situation?

---

### Post by donniezazen on 2009-11-17
> **Revan13 said:**
> I do not understand, I disabled the login sound but the system still plays on each startup. Very annoying :( Has anyone encountered the same situation?

I am having same problem. The only way you can shut it down is to mute before you shut down your computer.

---

### Post by johoe on 2009-11-18
the radical way:
sudo rm /usr/share/sounds/ubuntu/stereo/system-ready.ogg

regards,

  johoe

---

### Post by Yellow Pasque on 2009-11-18
johoe, it would be safer to rename the file instead of deleting it.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429)

---

### Post by infestor on 2009-11-20
> **johoe said:**
> the radical way:
sudo rm /usr/share/sounds/ubuntu/stereo/system-ready.ogg

regards,

  johoe


:) i like it. kill the ******!

---

### Post by gobbles414 on 2009-11-22
Turn off the login sound by going System => Preferences => Startup Applications => Startup Programs tab => uncheck GNOME Login Sound option.

To turn off the system ready sound while keeping the ability to turn it on again whenever you wish, enter the following into Applications => Accessories => Terminal: *sudo mv /usr/share/sounds/ubuntu/stereo/system-ready.ogg /usr/share/sounds/ubuntu/stereo/system-ready-off.ogg*

To turn the system ready sound on again, go into Terminal and enter: *sudo mv /usr/share/sounds/ubuntu/stereo/system-ready-off.ogg /usr/share/sounds/ubuntu/stereo/system-ready.ogg*

---

### Post by donniezazen on 2009-12-01
> **gobbles414 said:**
> Turn off the login sound by going System => Preferences => Startup Applications => Startup Programs tab => uncheck GNOME Login Sound option.

To turn off the system ready sound while keeping the ability to turn it on again whenever you wish, enter the following into Applications => Accessories => Terminal: *sudo mv /usr/share/sounds/ubuntu/stereo/system-ready.ogg /usr/share/sounds/ubuntu/stereo/system-ready-off.ogg*

To turn the system ready sound on again, go into Terminal and enter: *sudo mv /usr/share/sounds/ubuntu/stereo/system-ready-off.ogg /usr/share/sounds/ubuntu/stereo/system-ready.ogg*

Sorry Pal, It didn't work.

---

### Post by gobbles414 on 2009-12-04
Please be more specific soham_1207. **Which part of it didn't work? Were you unable to locate certain menus? Did you get error messages during the procedure?** Without more information it will be impossible to tell why the procedure worked perfectly for me but failed for you.

You might have encountered problems: if you "upgraded" to 9.10 from a previous version instead of doing a fresh install, if your computer is running an alpha or beta of 9.10, if your computer is running Kubuntu or Xubuntu, if you'd already tried some of the other advice in this thread (such as completely removing the sound file), or if your mistyped something while inputing the commands.

I and the others here look forward to helping you solve this problem.

---

### Post by donniezazen on 2009-12-04
> **gobbles414 said:**
> Please be more specific soham_1207. **Which part of it didn't work? Were you unable to locate certain menus? Did you get error messages during the procedure?** Without more information it will be impossible to tell why the procedure worked perfectly for me but failed for you.

You might have encountered problems: if you "upgraded" to 9.10 from a previous version instead of doing a fresh install, if your computer is running an alpha or beta of 9.10, if your computer is running Kubuntu or Xubuntu, if you'd already tried some of the other advice in this thread (such as completely removing the sound file), or if your mistyped something while inputing the commands.

I and the others here look forward to helping you solve this problem.

Thanks a lot for you help. Sorry for not being completely clear. I have a fresh install of Ubuntu Karmic with gnome. I entered all the commands as you advised. All executed perfectly but the sound was still there. I have used earlier advice to completely remove sound file. It worked.

Thanks.

---

### Post by gobbles414 on 2009-12-04
Since you didn't encounter any errors, I'm guessing that you accidentally ran all three parts of my procedure. The third part is actually for switching the system ready sound from off to on -- in other words, an undo command for the second part of the procedure. Because you've completely removed the system ready sound, the only way to know if you ran the third part is to review your Terminal history (up arrow).

Anyway, I'm glad that one of the solutions in this thread worked for you. Perhaps you'd like to mark this thread as solved?

---

### Post by donniezazen on 2009-12-04
> **gobbles414 said:**
> Since you didn't encounter any errors, I'm guessing that you accidentally ran all three parts of my procedure. The third part is actually for switching the system ready sound from off to on -- in other words, an undo command for the second part of the procedure. Because you've completely removed the system ready sound, the only way to know if you ran the third part is to review your Terminal history (up arrow).

Anyway, I'm glad that one of the solutions in this thread worked for you. Perhaps you'd like to mark this thread as solved?

Exactly, I ran all three parts. Sorry about that. I am marking this thread solved.

Thanks.

---

### Post by nanonils on 2010-01-03
1st: alt+F2 to open gconf-editor
2nd: untick the active key in order to disable the login ready drums sound in /apps/gdm/simple-greeter/settings-manager-plugins/sound/
3rd: must reboot

---

### Post by fernandoch on 2010-05-10
It did not work for me :(

---

### Post by wojox on 2010-05-10
Go into Login Screen Settings and uncheck the option.

---

### Post by nanonils on 2010-05-10
This is what fixed Karmic for me. Lucid is easy: solved for me as mentioned in wojox's post.

---

### Post by fernandoch on 2010-05-10
> **nanonils said:**
> 1st: alt+F2 to open gconf-editor
2nd: untick the active key in order to disable the login ready drums sound in /apps/gdm/simple-greeter/settings-manager-plugins/sound/
3rd: must reboot

I did that on karmic, but the drums are still there :(

---

### Post by donniezazen on 2010-05-10
> **fernandoch said:**
> I did that on karmic, but the drums are still there :(

This is a long neglected bug. It has been here since Jaunty. The best solution is to permanently remove the sound file as stated above.

---

