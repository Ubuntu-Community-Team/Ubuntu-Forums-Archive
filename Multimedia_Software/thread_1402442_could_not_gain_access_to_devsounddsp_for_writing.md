---
title: "could not gain access to /dev/sound/dsp for writing"
date: 2010-02-09
forum: Multimedia Software
---

### Post by Paresh on 2010-02-09
I have installed transcriber from the ubuntu repositories the version is listed as 1.5.1.1-3

I am trying to use this program on Ubuntu 9.10 (64bit), and when attempting to play the audio file (standard mp3 format) I get the error message: > could not gain access to /dev/sound/dsp for writing

Everything else I have tried for sound works fine and The mp3 file I'm transcribing plays fine in any other application eg movie player and rhythm box etc.

the full error message is:
```
Could not gain access to /dev/sound/dsp for writing.
Could not gain access to /dev/sound/dsp for writing.
    while executing
"player play -start [expr int($begin*$rate)] -end [expr int($end*$rate)]"
    (procedure "PlayRange" line 56)
    invoked from within
"PlayRange $pos $end $script"
    (procedure "Play" line 64)
    invoked from within
"Play"
    (procedure "PlayOrPause" line 10)
    invoked from within
"PlayOrPause"
    invoked from within
".menu.item9 invoke 0"
    ("eval" body line 1)
    invoked from within
"eval $menu_id invoke $item_id"
    (procedure "invoke_from_bind" line 7)
    invoked from within
"invoke_from_bind .menu.item9 0"
    (command bound to event)

```

anyone know a work around I can use while the developers hopefully fix this ?

---

### Post by lilmissdids on 2010-04-12
I'm having the same problem.... Does anyone know how to fix this?

Thanks in advance!!

---

### Post by foldingstock on 2010-04-12
Paresh, is your user in the 'pulse' and 'audio' groups? To check, open up a terminal and run the command "groups," all groups you are a member of will be displayed.

---

### Post by lilmissdids on 2010-04-12
I just typed in groups and audio is listed.

---

### Post by lilmissdids on 2010-04-12
[http://wiki.restfarbe.de/doku.php?id=nerdpol:transcriber_sound](http://wiki.restfarbe.de/doku.php?id=nerdpol:transcriber_sound)

There we go, all fixed.

For those who don't know German, I typed in

sudo ln -s /dev/snd /dev/sound 
sudo ln -s /dev/dsp /dev/snd/dsp

Thanks!

---

### Post by Paresh on 2010-04-12
Cheers, that worked.

Unfortunately, the project is completed now, I had to make do with the windoze version, where the audio sync was more than a bit off.  anyhow, I now have a working version for next time

Thanks

---

### Post by cantillon on 2011-04-11
The previous solution did not work for me in Ubuntu 10.10, but I found a workaround on this website (in German): [http://forum.ubuntuusers.de/topic/probleme-mit-audioausgabe-von-transcriber/#post-2754661](http://forum.ubuntuusers.de/topic/probleme-mit-audioausgabe-von-transcriber/#post-2754661)

You have to start transcriber with this command:

```
padsp transcriber
```

The padsp command redirect audio devices to pulseaudio.

If you don't want to type the command in the terminal every time you want to start the programme you can do the following:

1. Go to System > Preferences > Main Menu

2. Select Transcriber from the Sound & Video submenu.

3. Click on Properties to open "Launcher Properties" window.

4. In "Launcher Properties" window, in the field "Command", write: padsp transcriber.

I hope this helps.

---

