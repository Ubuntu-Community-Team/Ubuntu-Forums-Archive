---
title: "Sound probs with Skype"
date: 2009-03-09
forum: Multimedia Software
---

### Post by old_dope on 2009-03-09
Have installed Skype and my webcam works great and i can hear people talking clearly but they can't understand me because they say it is all garbled. Has anyone had a problem similar to this and is there a solution. Thanks

---

### Post by albandy on 2009-03-09
try loading it throght aoss
aoss skype_command

---

### Post by old_dope on 2009-03-09
Hello Albandy
Don't mean to appear thick (its just old age) but do you mean that i should open a terminal and type: asoss skype_command?

---

### Post by albandy on 2009-03-09
well first you need installed aoss,
so type sudo apt-get install alsa-oss
then simply type aoss skype

---

### Post by old_dope on 2009-03-09
Have opened a terminal and typed: sudo apt-get install alsa-oss but when i typed: assos skype the command was not found?

---

### Post by albandy on 2009-03-09
ok, the command is aoss not assos

---

### Post by old_dope on 2009-03-09
Yes i noticed my mistake and so i opened up a terminal ans typed aoss skype_command and the skype login box appeared but now i can't even hear the 'Make a test sound', or 'Make a test call'? 

The settings i have been using are:
Sound in (Default)
Sound out (Default)

---

### Post by old_dope on 2009-03-09
Have not got any sound on my computer at all now. Help someone please

---

### Post by albandy on 2009-03-09
What version of ubuntu are you using?

Ok, so skype it's using alsa, I remember that exist a parser to make skype work correctly.
aoss simply redirects the old open sound system to alsa (the new sound system of linux).

have you tried to make a sound test of your microphone?

---

### Post by gandaran on 2009-03-09
old_dope
to get sound working in skype you open skype options » sound equipment tab, choose pluse, alsa or oss or your sound card, test every one till you get the best results.
which version of skype did you install? skype uses qt (KDE) libs and is always a problem to set up in the gnome environment, it's best if you use gnome to install the static version.

---

### Post by old_dope on 2009-03-09
After installing 'alsa-oss' i completely lost all sound on my computer. So i un-installed 'alsa-oss' and now at least i can play and hear my cd's.

Have been advise to go here: /etc/pulse/daemon.conf 
and alter these two lines:

default-fragments = 5
default-fragments-size-msec = 25

to read like this:

default-fragments = 8
default-fragments-size-msec = 5

Trouble is i can't find the blooming /etc/pulse/daemon.conf file

---

### Post by old_dope on 2009-03-09
I am running Xubuntu 8.10 and i installed 'Skype 2.0 for Linux'.Please excuse my ignorance but how do i find gnome to install the static version?

---

### Post by albandy on 2009-03-09
sorry I assumed you were using ubuntu not xubuntu, so I understand that xubuntu don't use alsa. 
Try to record something with your microphone

---

### Post by old_dope on 2009-03-09
I can't! When i am in a conversation i can hear whatever my friend has said clearly but when i use the microphone everything is garbled and unintelligible. The same happens when i make a test call.

---

### Post by old_dope on 2009-03-09
Would it be any better if i un-intalled the version i have of Skype at the moment and tried one of the other versions in Synaptic that are not supported my Ubuntu?

---

### Post by old_dope on 2009-03-09
Finally! Got fed up and deleted Skype and then went into Synaptic and installed a different version. Now everything is working great. Just like to say thanks for the help and lots of patience from everyone.

---

### Post by Kewlaid on 2009-04-07
Hi I am a new user and have Xubuntu would love some help step by step how to get my mic to be heard. I have been using it fine until just the other day something seems to have broke. I can hear the other party real clear. The first instances of the problem was I was soon after the install.
 At first the recipient or person on other end of call couldhear me but distant or garbled, then or rather now I can still hear them but nothing of me on my mic. Desperate to use my skype please someone help maye yourself or first person that can. 
May the god of technology be with us God Speed

---

### Post by aonade on 2009-04-15
> **old_dope said:**
> Finally! Got fed up and deleted Skype and then went into Synaptic and installed a different version. Now everything is working great. Just like to say thanks for the help and lots of patience from everyone.

how do i uninstall skype on xubuntu? (i am very new to linux so don't know alot atm but im learning :) )
also i couldn't find any versions of skype on synaptic.

---

