---
title: "ogg123 Display"
date: 2012-02-13
forum: Multimedia Software
---

### Post by Rodney9 on 2012-02-13
Hello,

After ogg123 is started in a script through cron, I can't seem to control it.  

I try to use ogg123 -v or ogg123 -@ in a terminal but nothing happens.

How do I get to view what ogg123 is playing ?
Also how do I stop it playing ?

Rodney

---

### Post by Rodney9 on 2012-02-13
This is the the simple script - 

```
#!/bin/sh

ogg123 -z ~/Music/*.ogg
```

Would there be another/better way or program I could use that will let me control it later ?

Rodney

---

### Post by MG&amp;TL on 2012-02-13
AFAIK cron is either executed as root or as one of the many daemon users (?). Therefore, not executed as Rodney. (If you could see other people's apps, it would be a bit creepy :D )

I'm not really sure how to get around this though.

I think "at" might be a better choice, or a really big "sleep" statement.

---

### Post by Rodney9 on 2012-02-14
I use the script in /bin and cron as root.

Is there a better way instead of oog123 and still easy, that I could use to control it later ?


Rodney

---

### Post by MG&amp;TL on 2012-02-14
> **Rodney9 said:**
> I use the script in /bin and cron as root.

Is there a better way instead of oog123 and still easy, that I could use to control it later ?


Rodney

What are you trying to do? I'm guessing you're trying to play a file every so often. Cron is intended for running scripts on a system, rather than on a user. 

Thoughts:

-autostart entry, for LXDE: ~/.config/lxsession/Lubuntu/autostart (at or sleep script)

-you probably shouldn't use /bin, use /usr/bin or ~/bin instead.

-Change user to Rodney in the cron script...is that possible?

Need a bit more info....:)

---

### Post by Rodney9 on 2012-02-14
I use the script as an alarm in the morning

```
#!/bin/sh

ogg123 -z ~/Music/*.ogg
```

added it to cron

```
33 04 * * * /bin/alarm.sh 
```

I use this when I go to bed

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

*rtcwake* wakes my laptop from *sleep* at 4:30am

c*ron* plays my alarm.sh script at 4:33am

*ogg123 -z* plays and shuffles my Music directory.


**It all works perfectly** except for the player, I can not control ogg123, except to use ```
killall ogg123
``` a bit blunt, I would like to see what's playing, skip to the next track, shut it down gracefully etc.


Thanks for your patience
Rodney

---

### Post by MG&amp;TL on 2012-02-14
Hm. You could try using a graphical app, I have no idea if that would appear though. Something like:

```
rhythmbox /path/to/*.ogg
```

Out of ideas, sorry. Hopefully somebody else can help.

---

### Post by Rodney9 on 2012-02-14
> **MG&TL said:**
> Hm. You could try using a graphical app, I have no idea if that would appear though. Something like:

```
rhythmbox /path/to/*.ogg
```

Out of ideas, sorry. Hopefully somebody else can help.

I have tried Guaydeuqe, Pragha, Audacious and Clementine but I can not get them to auto-start playing.

Rodney

---

### Post by Jose Catre-Vandis on 2012-02-14
Try opening ogg123 in a terminal?
(xfce example)
```
xfce4-terminal -x ogg123
```

I don't have oggs but tested with mpg123:

```
xfce4-terminal -x mpg123 -C -z -@ ~/Music/*.mp3
```

The key is to use the "-C" option which allows control by terminal keys: from the mpg123 man pages:

```
-C, --control
              Enable terminal control keys. By default use 's'  or  the  space
              bar  to stop/restart (pause, unpause) playback, 'f' to jump for&#8208;
              ward to the next song, 'b' to jump back to the beginning of  the
              song, ',' to rewind, '.' to fast forward, and 'q' to quit.  Type
              'h' for a full list of available controls.
```

---

### Post by Rodney9 on 2012-02-14
xterm -e /bin/alarm.sh

this will work from run, but I'm confused, if i put it in the alarm.sh , the script will be telling itself to run itself.

---

### Post by Rodney9 on 2012-02-14
Well I have copied my script into /bin/ /usr/bin/ and my home directory but now I can not get it run from crontab, it will run from 'RUN' or a terminal

I set for a few minutes in the future but nothing happena
26 14 15 02 * rodney /home/rodney/alarm.sh

rodney

---

### Post by Jose Catre-Vandis on 2012-02-15
> **Rodney9 said:**
> xterm -e /bin/alarm.sh

this will work from run, but I'm confused, if i put it in the alarm.sh , the script will be telling itself to run itself.

You will need a separate script to call alarm.sh, as per your line above, then alarm.sh can be placed anywhere on your system e.g. home/rodney/alarm.sh

(alarm.sh) - note the **/* allows for recursive playback of all directories in ~/Music
```
ogg123 -C -z -@ /home/rodney9/Music/**/*.ogg
```

(call-alarm.sh) - this is the one you put in cron
```
xterm -e /home/rodney9/alarm.sh
```

This should then give you a terminal window with ogg123 running inside it, and when the window has focus you can use keyboard shortcuts to control it.

---

### Post by Rodney9 on 2012-02-15
Thanks to Cheesehead - 

[http://ubuntuforums.org/showthread.php?p=11691482#post11691482](http://ubuntuforums.org/showthread.php?p=11691482#post11691482)

This script now works perfectly - 

```
DISPLAY=:0.0 /usr/bin/xterm -e ogg123 -z /home/rodney/Music/*.ogg
```

I can see whats playing, skip songs etc.

Thank You Everyone for your help :D

---

