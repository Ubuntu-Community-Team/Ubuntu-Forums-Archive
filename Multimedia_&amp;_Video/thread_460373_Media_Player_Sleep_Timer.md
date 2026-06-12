---
title: "Media Player Sleep Timer"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by Bohlio on 2007-05-31
Does anyone know of a media player that has a sleep timer?? Or a program that can shut off another program after a certain period of time?? I want to be able to listen to my MP3 collection while going to bed, then have it shut off after a while. I'm a little angry that all media players I've had, (WMP11, Zune, Itunes, Rhythmbox, VLC) none of them have a relatively simple feature. if anyone knows of anything, it would help me alot :-)

---

### Post by bom28 on 2007-05-31
You can do it very easily.
In a shell, there is the "sleep" command, that will wait for a specified amount of time, for example "sleep 10m" will wait for 10m.
After the sleep you must find a command to shut down your media player, some media player can be commanded with a command line, for example with rhythmbox, "rhythmbox-client -quit" will make a running rhythmbox quit, ( "rhythmbox-client --help" for a list of command).
If the media-player can't be controlled this way, you can use the killall command, for example "killall rhythmbox" will kill all processes named "rhythmbox" (you have to find the right process name). Note that a program terminated by a kill will probably not save its options or whatever it does when shut down normally.

Now to combine the 2 commands, "sleep 10; rhythmbox-client -quit" will terminate rhythmbox after 10 minutes. (the variant "sleep 10m && rhythmbox-client -quit" can be aborted with a ctrl-c in a shell, a crtl-c with the ';'-variant will run the command immediately )

And if you don't want to use the command-line, you can create a custom application launcher, just put
```

sh -c "sleep 10; rhythmbox-client -quit"

```
(with the quotes) as the command to launch.

The downside is that you have no visual feedback.

---

### Post by Bohlio on 2007-06-02
Thank you very much. Dang i love how useful the terminal is :-)
I cant thank you enough :-)

---

### Post by Bohlio on 2007-06-03
Oh, I just noticed, You have to type
```
sleep 10; rhythmbox-client --quit
```
instead of
```
sleep 10; rhythmbox-client -quit
```

If you dont have two dashes, you get an error message.
Thanks again for your help :-P

---

