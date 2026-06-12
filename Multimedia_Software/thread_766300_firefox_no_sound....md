---
title: "firefox no sound..."
date: 2008-04-25
forum: Multimedia Software
---

### Post by guy.thingy on 2008-04-25
hi i just got my sound working on amarok and everything but i cant seem to get my sound working on firefox anyone could help me?

---

### Post by orre64 on 2008-04-25
I have the same problem, Firefox just calls the system beep as soon as there's any sound.

---

### Post by guy.thingy on 2008-04-25
funny mind doesnt even beep..well maybe because i got the beep disabled..but it took me almost the whole day to get my sound working right it works fine on amarok but the moment i wanted to watch a youtube video it had no sound..

---

### Post by aeiah on 2008-04-25
are you both using hardy? there used to be a bug a few years back where this happened. obviously, i cant remember how to solve it, or whether its the same problem or not. have you tried searching the forums? are you using alsa, or pulse?

---

### Post by ferdinand1978 on 2008-04-25
> **guy.thingy said:**
> hi i just got my sound working on amarok and everything but i cant seem to get my sound working on firefox anyone could help me?

hi i hope this help

click system-->Preference-->Sounds-->device tab-->choose ALSA - Advance Linux Sounds Architecture

then click test see if you hear the sounds

that's how i fix mine

if you have a sounds card

double click on the speaker icon on the top left
file-->change device into (your sounds card name)

then..

left click on the same speaker icon on the top left
choose preference again choose the name of your sounds card
so that you can control the sound form the keyboard button

again this might not help you but give it a try, you'll lose nothing

ferd

---

### Post by guy.thingy on 2008-04-25
lol it took me 5 hours to configure my sound to work, i didnt want to touch that i managed to use pulseauio not alsa..anyways sounds work now all i did was install a  "flashlib" or something..the sound worked before just not in ff

---

### Post by clarezoe on 2008-08-19
I have the same problem. I can play music with mplayer, amarok, audacious etc. except firefox. For example, I can play youtube video but no sound.

The sound properties test works works fine too.

I'm running hardy.

Thanks!

---

### Post by Yellow Pasque on 2008-08-19
Go to System -> Preferences -> Sound and set it to playback through PulseAudio
then:
```
sudo apt-get install libflashsupport
```

---

### Post by clarezoe on 2008-08-20
I followed [http://ubuntuforums.org/showpost.php?p=3633218&postcount=4]("http://ubuntuforums.org/showpost.php?p=3633218&postcount=4")
```
mv ~/.asoundrc .asoundrc.old
mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

And works by me now.

Thanks Temüjin,I have libflashsupport installed already, and I don't want to use pulseaudio, because I have problem with it when I use Skype.

---

