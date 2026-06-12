---
title: "bt_audio_service_open: connect() failed: Connection refused (111)"
date: 2010-05-22
forum: Multimedia Software
---

### Post by sunnyengineeer on 2010-05-22
Hello,
          Today I upgraded from 8.10 to 10.04..7 then I installed mplayer thru terminal..
But the mplayer is not showing in the menu under Applications>Sound & Video..
& if I try to run it from terminal..it shows error:-

[COLOR=Red]bt_audio_service_open: connect() failed: Connection refused (111)[/COLOR]

than nothing appears..except some commands realted to mplayer...like opening the file etc..

Somebody plz help me out..

Thnx
Sunny Sharma

---

### Post by mc4man on 2010-05-22
> But the mplayer is not showing in the menu under Applications>Sound & Video..

That's because the lucid mplayer package is command line only.

If you wish a gui then install a frontend such as smplayer and or gnome-mplayer.

(medibuntu has a mplayer package for lucid that is the old gmplayer frontend - though I'd think you'll find the above more suitable 

> .it shows error:-

bt_audio_service_open: connect() failed: Connection refused (111)

Can be ignored - all svn. builds of mplayer on lucid show that, personally don't have a clue - bt = bluetooth...?

> 
than nothing appears..except some commands realted to mplayer...like opening the file etc..

Post the complete terminal output inc. command in a quote box. (though do try a frontend first

---

### Post by andrew.46 on 2010-05-22
Hi Sunny,

```
bt_audio_service_open: connect() failed: Connection refused (111)
```

There was some discussion on this the other day on #mplayer. Does your computer have some bluetooth packages installed but no actual bluetooth devices operating or available? Have a search on Synaptic...

Andrew

---

### Post by mc4man on 2010-05-22
> Does your computer have some bluetooth packages installed ...

There are quite a number of bluetooth related packages installed in lucid whether you have bluetooth devices or not or have them disabled.

(there is only 1 -dev package

I remember trying quite some time ago removing all that where possible though a couple are dependencies of packages one probably doesn't want to remove.
(libbluetooth3 was the main one that would be difficult to remove

The git mplayer does not show this...

Edit: 
managed to get rid of it..., now to see what was causing

doug@doug-desktop:~/mplayer$ ./mplayer '/home/doug/Desktop/01 - Sympathy For The Devil.m4a' 
MPlayer SVN-r30856-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory.

Playing /home/doug/Desktop/01 - Sympathy For The Devil.m4a.

---

### Post by mc4man on 2010-05-22
The messages are caused by the bluez-alsa package. It has nothing to do with the build - uninstall that package and the messages go away, re-install and they return.

---

### Post by andrew.46 on 2010-05-22
Hi mc4man,

> **mc4man said:**
> The messages are caused by the bluez-alsa package. It has nothing to do with the build - uninstall that package and the messages go away, re-install and they return.

I think you have solved one of the more irritating error messages under Lucid :).

Andrew

---

### Post by sunnyengineeer on 2010-05-22
Thnkyou guys for solving my problem,Now my problem is gone after I reinstalled Mplayer & now im using SMplayer,So no problem in either Mplayer or SMplayer....

Thanx once again
Sunny Sharma

---

### Post by mc4man on 2010-05-23
> solved one of the more irritating error messages under Lucid 

maybe... but tonight this one takes the cake - relating to the braero, copy cd deal
And this is on a straight up, no mods lucid.

After installing the libs it wanted and having to do a reboot for them to be recognized (another karmic, lucid 'issue'), this is what shows up...
(possibly 'irritating' is an understatement

---

### Post by bdd4bdd4 on 2010-09-22
SOLVED: I lost sound in lucid 10.04. I removed bluetooth audio within synaptic and got it back.
THANKS! bdd4bdd4 - 9-22-10

> **mc4man said:**
> There are quite a number of bluetooth related packages installed in lucid whether you have bluetooth devices or not or have them disabled.

(there is only 1 -dev package

I remember trying quite some time ago removing all that where possible though a couple are dependencies of packages one probably doesn't want to remove.
(libbluetooth3 was the main one that would be difficult to remove

The git mplayer does not show this...

Edit: 
managed to get rid of it..., now to see what was causing

doug@doug-desktop:~/mplayer$ ./mplayer '/home/doug/Desktop/01 - Sympathy For The Devil.m4a' 
MPlayer SVN-r30856-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory.

Playing /home/doug/Desktop/01 - Sympathy For The Devil.m4a.

---

### Post by georgezenios on 2011-06-12
magic solution, this has bugged me for ages noe problem solved not getting this error meesage with SKYPE after removing bluettoth in synaptic.

---

### Post by morteza1991 on 2011-06-29
I also receive same message but when I run Espeak
```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

```
and Festival doesn't work. when I click on pronounce the word in StarDict
hear a sound like beep and when select Espeak TTS it doesn't pronounce word completely. Why ?

---

### Post by Pletched on 2012-10-06
Me too. I have same failed messages. Is BlueZ-ALSA package the problem?

```
Pletch $ espeak -v en "I have errors\!"
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

```

---

### Post by overdrank on 2012-10-06
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

