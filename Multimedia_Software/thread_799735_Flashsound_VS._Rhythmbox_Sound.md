---
title: "Flashsound VS. Rhythmbox Sound"
date: 2008-05-19
forum: Multimedia Software
---

### Post by Fireworm on 2008-05-19
I have a problem with my sound.

I can't seem to get sound from both Firefox (Flash-players) and programs like Rhythmbox on the same boot.

I can turn the sound on/off in flash with the session:

ln -s /tmp/.esd-1000 /tmp/.esd

(No idea what it does, found it on another forum)

However I don't feel like logging in and out everytime I want sound from Youtube.

The problem wasn't there when I first installed Ubuntu :S

I run 8.04, Firefox 3b5 and Flash 9.

I'm kinda a n00b to Ubuntu, so please go easy on me :)

---

### Post by hermes0710 on 2008-05-19
The problem exists since hardy was released. Make sure you have libflashsupport **uninstalled** (if not execute ```
sudo apt-get purge libflashsupport
``` from a terminal) and go to firefox options, in the security tab and make sure you do **not** have ticked "Tell me if..." options

---

### Post by Fireworm on 2008-05-19
> **hermes0710 said:**
> The problem exists since hardy was released. Make sure you have libflashsupport **uninstalled** (if not execute ```
sudo apt-get purge libflashsupport
``` from a terminal) and go to firefox options, in the security tab and make sure you do **not** have ticked "Tell me if..." options

Didn't have that installed. Ticked all of them off. Same result.

---

### Post by cor2y on 2008-05-19
try using this method.
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
It may have something to do with how pulse audio is configured, it helped me.

---

### Post by Fireworm on 2008-05-19
> **cor2y said:**
> try using this method.
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
It may have something to do with how pulse audio is configured, it helped me.

I don't have pulse Audio, so it does not have anything to do with that. I have no intention of installing it, as it may screw even more with my audio.

---

### Post by wolfen69 on 2008-05-19
unless you manually removed pulse audio, you have it. it comes by default in Hardy.

---

### Post by wolfen69 on 2008-05-19
i just tried the method in the link posted and it works. i was having a similar problem, but it wasnt a real big deal. glad i got it fixed though.

---

### Post by Fireworm on 2008-05-19
Didn't know that.

However I do not have the files mentioned in the guide linked to.


Does anyone have another solution?

---

### Post by Fireworm on 2008-05-19
> **wolfen69 said:**
> i just tried the method in the link posted and it works. i was having a similar problem, but it wasnt a real big deal. glad i got it fixed though.


Could not save the file /etc/asound.conf.
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

How did you get past this?

---

### Post by cmlewin on 2008-05-19
fireworm make sure you're editing that in sudo as administrator

also,
i had the same problem and i don't know where the thread is nor the full solution (though there is a thread on it in ubuntuforums).. it definitely is something to do with pulse audio. i had to install the pulse audio engine and device chooser and run that panel applet on each startup.. and make sure all the devices under system-pref-sounds were set to pulseaudio.

hope thats of at least a little help.

---

### Post by cmlewin on 2008-05-19
fireworm make sure you're editing that in sudo as administrator

also,
i had the same problem and i don't know where the thread is nor the full solution (though there is a thread on it in ubuntuforums).. it definitely is something to do with pulse audio. i had to install the pulse audio engine and device chooser and run that panel applet on each startup.. and make sure all the devices under system-pref-sounds were set to pulseaudio.

hope thats of at least a little help.

---

### Post by cor2y on 2008-05-19
Its this link [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
And everything you need should be available in synaptic, if some needed software is listed as not found via apt-get then make sure all the  ubuntu repos are enable (multiverse, universe and restricted)

---

