---
title: "[SOLVED] ipod is detected, now how do I get gtkpod to launch instead rhythmbox?"
date: 2008-12-18
forum: Multimedia Software
---

### Post by Ehtetur on 2008-12-18
How can I make gtkpod launch when I attach my ipod?

Rhythmbox launches, but I want to manage my ipod with gtkpod...
I'm running Hardy x64_86...

I looked in the place where the option was in Edgy, but it's not in Hardy:
> System --> Preference --> Removable Drives and Media

I started gconf-editor and changed the value in /desktop/gnome/volume_manager/autoipod_command to gtkpod... Rhythmbox still launches.

Help! :twisted:

---

### Post by mc4man on 2008-12-18
Pretty simple to do though I don't have gtkpod atm so I'm not sure if it's default launch command will work right for auto run. (can be worked out if needed.

To make this simple and so I don't have to write out complete intrs. from scratch do this first.

If you don't have 'file management' enabled in System -> preferences then right click on 'Applications' -> edit menus. Scroll down to preferences and enable file management in the right colunm.

Then open file management from preferences menu -> media and in the 'music player' tab switch from rhythmbox to 'open folder'. _Close file management_, then reopen and switch back to rhythmbox and close out again. ( you should also under the 'views' tab enable 'show hidden files..'

Then just to ck. go to home folder -> .local -> share -> applications and open mimeapps.list.
You should see a line in there - x-content/audio-player=rhythmbox.desktop;

**If so** close out mimeapps.list and here you go

In a terminal (one at a time

```
cp /usr/share/applications/gtkpod.desktop ~/.local/share/applications/gtkpod1.desktop

```

```
gedit  ~/.local/share/applications/gtkpod1.desktop


```

On the line name=gtkpod  add a 1 to it ( name=gtkpod1 ) Save and close 

```
gedit  ~/.local/share/applications/mimeapps.list
```

add gtkpod1; to line mentioned above, should look like this

```
x-content/audio-player=rhythmbox.desktop;gtkpod1;
``` (no spaces, ends with ; Save and close

Now go open file management -> media and choose gtkpod1 from the music player box

The reason for changing the name is to separate it from the default gtkpod in case you need to change the launch command, and give it a separate entry in applications menu ( maybe unnecessary, doesn't hurt in any case.

If it doesn't connect properly on auto launch maybe you'll need to do something like this 
what I do for ipod and amarok

[http://ubuntuforums.org/showthread.php?p=5562637#post5562637](http://ubuntuforums.org/showthread.php?p=5562637#post5562637)

---

### Post by Ehtetur on 2008-12-18
> **mc4man said:**
> Pretty simple to do... 
simple, eh? like differential equations with imaginary numbers simple :twisted:

Actually mc4man, that's good stuff.... I followed your steps and now I got gtkpod launching when I attach my ipod...

Thanks!

I know this is an issue with gnome and not ubuntu, but it's still funny that what took 3 clicks in Ubuntu 7.x now takes 10 clicks in 8.x...
I can't wait to see what 9.x brings.. :evil:

---

### Post by mc4man on 2008-12-18
Glad it worked, just tried here and it seemed ok, though having never used gtkpod didn't realize it's best to eject the ipod from gtkpod first before closing gtkpod (ended up with 2 ipods next time I coonected.

> but it's still funny that what took 3 clicks in Ubuntu 7.x now takes 10 clicks 

That's what I first thought, now i see how modifiable hardy is, you can use mimeapps.list and thr r. click to do a lot.

here's a few things
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

