---
title: "flash work-around plugin for youtube etc. possible?"
date: 2008-06-10
forum: Multimedia Software
---

### Post by Dr.Ninethousand on 2008-06-10
I am having troubles with slow flash on youtube etc., and I know I'm not alone..  sites like keepvid.com exist, so it's obviously possible to go straight to the source video file..  and I can play saved .flv files in vlc and other players, so I was wondering.....

would it be possible to create some kind of plugin that would open youtube videos in an embedded vlc window instead of flash?.  or even in a separate window for that matter?.

---

### Post by wdaniels on 2008-06-10
> **Dr.Ninethousand said:**
> would it be possible to create some kind of plugin that would open youtube videos in an embedded vlc window instead of flash?.  or even in a separate window for that matter?.

Possible, yes. Likely that anyone is going to do it, no. Have you tried that [flash 10 beta]("http://ubuntuforums.org/showthread.php?p=5150877#post5150877") yet? Apparently it's an improvement.

---

### Post by Tomatz on 2008-06-10
> **wdaniels said:**
> Possible, yes. Likely that anyone is going to do it, no. Have you tried that [flash 10 beta]("http://ubuntuforums.org/showthread.php?p=5150877#post5150877") yet? Apparently it's an improvement.

Flash 10 works better.

You could try turning off hardware acceleration in flash 9 (the flash you have installed). Just r-click on the flash animation you are trying to view, click settings, uncheck hardware acceleration.

---

### Post by Dr.Ninethousand on 2008-06-10
yeah I had installed 10 just before making this thread, and it didn't seem to make a difference..  about to go back to 9, since right-click>settings gave me the little window but no text is displayed..

---

### Post by gandaran on 2008-06-10
totem has a youtube plugin, you can search and watch any youtube video in totem, just enable the plugin in totem » plugins

---

### Post by ruha on 2008-06-10
you can wait until youtube is fully loaded, and then copy the .flv from /tmp/ to videos and watch it with vlc

---

### Post by Dr.Ninethousand on 2008-06-10
thanks for the tip Tomatz, but that didn't help either..


Gandaran, thanks a lot for that info, seems to work pretty well, as long as I'm not doing anything else at the same time..  :p   sometimes it stops to buffer, but it's pretty usable..


it's too bad I'll still have the same problems for awful myspace pages and other flash pages, but being able to browse youtube is a major success..  :)

---

### Post by Tomatz on 2008-06-10
Give this a try:

[http://www.ubuntugeek.com/how-to-get-flash-working-in-opera-920.html](http://www.ubuntugeek.com/how-to-get-flash-working-in-opera-920.html)

;)

---

### Post by Dr.Ninethousand on 2008-06-10
> **ruha said:**
> you can wait until youtube is fully loaded, and then copy the .flv from /tmp/ to videos and watch it with vlc

yeah that's kind of what I had in mind - a plugin/script to automate that..

edit:  if only the temp file had the same name every time..  :(

---

### Post by Dr.Ninethousand on 2008-06-10
hmm, youtube is fine. but myspace videos from /tmp play terribly in totem and vlc..

---

### Post by Dr.Ninethousand on 2008-06-10
ok, from command line I can do:

totem /tmp/Flash*

to play whatever flash movie just loaded in a browser (so far they have all been named something like FlashGHvbsK).  However, I'm unable to create a taskbar button to do the same command (using xfce).  Totem starts but then says /tmp/Flash* doesn't exist.  I get the same results with vlc in place of totem.  I also tried checking the 'run in terminal' box in the button settings..  :confused:

---

### Post by Tomatz on 2008-06-10
Open a terminal and type:

```
sudo touch /usr/bin/flashack

sudo gedit /usr/bin/flashack

```
Then type this into the file:

```
totem /tmp/Flash*
```

Save

In a terminal type:

```
cd /usr/bin

chmod a+x flashack
```



Now create a launcher with the command **flashack** ;)

---

### Post by Dr.Ninethousand on 2008-06-10
lol, thanks again, but I already worked around it in a similar way, by creating flasher.sh in /usr/

:p

for anyone wanting to do the same, flasher.sh contains one line:

totem /tmp/Flash*

(you can use any other .flv player instead)

and my panel link command is just /usr/flasher.sh

oh and I had to set the permission on flasher.sh to executable..



dunno why you can't use wildcards in xfce panel though..

---

