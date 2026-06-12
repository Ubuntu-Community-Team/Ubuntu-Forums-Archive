---
title: "Dam movie players &lt;.&lt;"
date: 2008-09-10
forum: Multimedia Software
---

### Post by del_diablo on 2008-09-10
I am using Ubuntu, just installed. I followed several tutorials and stuff, but i cannot still play .AVI files that i downloaded and i want to play. It keeps telling me some kind of error with the sound.

Totem says:
"An error occurred:
Could not determind stream."

Avidemux cannot open the file.

Gnome player says it plays, but it got no visual and sound(trust me, there MUST be sound z.z)

MPlayer gets Fatal Error: "Error opening/initializing video_out (-vo) device."
And Error: "Cannot find codec for audio format 0x56444152"

If this keeps going on i think i might switch back to a windows installation and use K-Lite(it works dam it!) <.<

---

### Post by ad_267 on 2008-09-10
VLC should definitely work for anything if nothing else will.

Have you installed ubuntu-restricted-extras? That's all I needed to play anything.

Also is this only for one file that you're having problems? Do all other avis play ok?

---

### Post by del_diablo on 2008-09-10
None of the .AVI files work, but .MKV works for some reason.

"Have you installed ubuntu-restricted-extras?"

Maybe...... i am not exactly sure.

---

### Post by ad_267 on 2008-09-10
Ok well install it (System - Administration - Synaptic Package Manager and search for it) and if that doesn't work then try VLC.

---

### Post by amersault on 2008-09-10
VLC is my player of choice - AVIs will open w/ no problem.

---

### Post by del_diablo on 2008-09-10
Attempted in VLC, and got a funny error. Loads no screen, no sound, plays trough the 21min long file in 5 sec.

---

### Post by eotakos on 2008-09-10
actually .avi files were playing for me out of the box!
i haven't messed with anything from the multimedia side of ubuntu yet. i plan to, in order to have more control over what's happening, but for now everything works somehow...

the only thing i did was... when i first tried to play mp3 files with totem, it automatically asked me to install some proprietary stuff -because it couldn't reproduce at the moment -  i answered ok, and after the extra (but automated) installation, everything works.

this stream error you're mentioning appeared to me too for some reason earlier today. Everything was working fine ( my pc is running from early morning) and at some point about an hour ago i tried to open video/music and nothing would work (neither with totem nor with rythmbox) - totem displaying that message you're saying. after that, when i closed transmission and pidgin, totem would open stuff, but the videos were running extremely slowly, and music wouldn't reproduce - the visualisation would move slowly too.

i know this is not a solution, but the error message was the same - so the symptoms could help someone who knows how this things work.

Anyway; any help would be appreciated by me too :-)

---

### Post by Vivaldi Gloria on 2008-09-10
Start

system menu > admin > synaptic

Enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies. Also install gnome-mplayer and gxine which are good video players.

---

### Post by del_diablo on 2008-09-10
> **Vivaldi Gloria said:**
> Start

system menu > admin > synaptic

Enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies. Also install gnome-mplayer and gxine which are good video players.

Allready did, and it did not work.

---

### Post by Vivaldi Gloria on 2008-09-10
> **del_diablo said:**
> Allready did, and it did not work.

Have you tried all of vlc, gnome-mplayer, gxine? 

Did you download all your avi files from the same place? Maybe something is wrong with them.

---

