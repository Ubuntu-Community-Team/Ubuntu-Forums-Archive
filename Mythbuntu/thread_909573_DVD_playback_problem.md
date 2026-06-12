---
title: "DVD playback problem"
date: 2008-09-03
forum: Mythbuntu
---

### Post by Sengkim on 2008-09-03
Hi,

I'm running Mythbuntu 8.04.1 and have an issue when playing a DVD (either from a real DVD disc or from a folder containing the VIDEO_TS folder).

The problem is that using the internal player, all sound is really messed up (like water gurgling and such). However, when I play the file using VLC (from the Applications button) the sound is really nice.
So I wanted to use VLC but can't seem to manage it.

Anyone has an idea? Thanks!!

BB
Peter

---

### Post by Sengkim on 2008-09-05
Hi....no one can help me?

BB
Peter

---

### Post by newlinux on 2008-09-05
I have no idea about the audio except to look at the frontend logs if you are using the internal player. What do you mean by you can't seem to manage using VLC?

---

### Post by Sengkim on 2008-09-05
I've checked the logs and can't seem to find anything unusual...certainly no errors.

Well, I start VLC through the application menu and from there everyhting works. So I wanted to changed the preferences in mythbuntu to use VLC instead of the internal player but I can't manage it (like in I don't know the command line params and all...).
The thing is, there is a file type VIDEO_TS but for that you need to be able to pass a directory to VLC.

Of course, if the bloody sound from the internal player would just work :(

BB
Peter

---

### Post by MikeNick42 on 2008-09-05
Change the dvd player command from Internal to something along the lines of vlc dvd://{your device}

Look at the Customize: line when you open a dvd with vlc and use that as a base for the cli options. You may need to add --full-screen or something and maybe vlc:quit.

Don't forget to set up vlc in lirc.

---

### Post by newlinux on 2008-09-05
make sure you turn up to verbosity in the logs (-v playback will give you a lot more information).

Seems like:
```


vlc -intf=dummy --fullscreen file://%s vlc:quit

```
would work in mythvideo, but I don't have any video_ts folders to play with anymore...

---

### Post by gardengxc on 2008-09-06
you could also try installing libdvdcss to fix the problem.
I was told by kaffeine to enter in terminal:
sudo /usr/share/doc/kaffeine/install-css.sh
and it fixed the error on all media players.

---

### Post by &lt;mike&gt; on 2009-12-20
for ripped dvds, i've often found that i need to do this as a custom play command.
usually 
```

cvlc --no-video-deco --no-fullscreen --width 890 --height 750 --video-x 59 --video-y 0 --no-osd --play-and-exit dvd:///mnt/a/dvds/ABC2

```

the 'cvlc' means that the player uses the version without the frontend; 
the no fullscreen and the width, height, video-x (horizontal offset), and video-y (vertical offset) are to do with my tv not showing the whole of my screen (that is, I'm mirroring my mythtv playback settings); 
the no-osd option suppresses the text which otherwise appears every time you change files/chapters; 
the play and exit command is especially important, as it returns you to mythtv on exit;
the dvd:// tells cvlc that this is a dvd, and the bit following it is the path to your ripped dvd root folder (i.e., the one which contains VIDEO_TS and AUDIO_TS).

---

