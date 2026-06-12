---
title: "teamspeak sound"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Caz'ar Xiladys'varion on 2007-11-08
While running teamspeak, no other process is allowed to use any form of sound, so I followed this guide...

> I have problems with a game and the Linux client when using ALSA. How to fix?

This is for those of you that are having problems running the game while TeamSpeak is running (like getting no sound in game or the game refuses to start).

Are you using ALSA (Advanced Linux Sound Architecture)?
First thing to do is check if you are running alsa at all. Try "lsmod | grep snd" in a terminal as root, if you get some lines of output, you are using ALSA, if you dont get anything, you are not.

Any sound daemons running?
Now we check if /dev/dsp is being used by any sound daemon. For this you need the program "lsof". If you dont have it installed you can get it from your distribution cd's. Now issue "lsof | grep dsp". This will list all aplications using the sound, idealy you shouldn't get any ouput, else we need to get rid of that daemon.

Getting rid of the sound daemon
If you got output in then you most probably have arts running. If something else is listed as programme name you have to get rid of that.

Disabling arts
Go to the KDE control center, hit search and type "artsd" this should find a hit "Sound System". In the dialogue you deselect start arts at KDE startup. Then you restart KDE and check if arts is still running. It should be gone.

Disabling other daemons
You can always resort to killing the processes "killall yxz", but the better way is to find where you can set it to not start it.

Finding the process name of your game
For the following steps we need to know what the process is called that runs the game. To find out, you can start your game and switch to a ttySx (press Ctrl+Alt+F2 for example), then type "top", and you should see the name somewhere high up (as your game should use lots of CPU).

Telling ALSA your game only needs playback
Now, to enable your game to play sound you have to tell ALSA that your game will not need to record sound or anything - else ALSA will refuse to give your game the capability to play sounds, since TeamSpeak already has the rights to record, and no two programs should be able to. Issue these commands as root:

echo 'quake3.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'quake3.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss

Now you should be able to play your game with sounds while using TeamSpeak.

Since the /proc filesystem is not permanent you have to issue the commands in every time you rebooted and want to game with TeamSpeak. The sollution is to put those commands in a startup script, which will issue them automagicly at boot-up time. For SuSE its "/etc/init.d/boot.local", for Gentoo try "/etc/conf.d/local.start". Just add those commands somewhere at the bottom of those files.


But it didn't seem to help any. Anyone have any ideas? Thanks a bunch in advance.

---

### Post by Caz'ar Xiladys'varion on 2007-11-09
Any help?

---

### Post by Caz'ar Xiladys'varion on 2007-11-09
anyone?

---

### Post by Caz'ar Xiladys'varion on 2007-11-11
hello? anyone there?

---

### Post by Caz'ar Xiladys'varion on 2007-11-19
wtf is wrong with all of you

---

### Post by Caz'ar Xiladys'varion on 2007-11-30
can someone please help?

---

### Post by warmwaddle on 2007-11-30
> **Caz'ar Xiladys'varion said:**
> wtf is wrong with all of you

Please be patient. This is FREE, no one is payed here. If they help it is of the kindness of their heart, but nobody has to help if they don't want to.

---

### Post by Caz'ar Xiladys'varion on 2007-11-30
well, already waited 'bout a month...

---

### Post by loell on 2007-11-30
how about in the teamspeak forum?

---

