---
title: "Saving sound/volume settings"
date: 2009-07-03
forum: Multimedia Software
---

### Post by geovino on 2009-07-03
I recently installed Xubuntu 9.04 and for some reason every time I reboot I have to unmute the master volume and slide the volume up. Why isn't these settings being saved? I've set up Xubuntu and Debian w/Xfce on different PCs and they save the volume settings. 

What needs to be corrected so the settings are saved?

---

### Post by kerry_s on 2009-07-03
in terminal:
**alsamixer**

set your settings.

then run:
**sudo alsactl store**

to make sure it loads, put: 
**alsactl restore &**

in /etc/rc.local

---

### Post by geovino on 2009-07-03
> **kerry_s said:**
> in terminal:
**alsamixer**

set your settings.

then run:
**sudo alsactl store**

to make sure it loads, put: 
**alsactl restore &**

in /etc/rc.local

I ran the commands but it still didn't save it. what do you mean by 
in /etc/rc.local ?

---

### Post by kerry_s on 2009-07-03
> **geovino said:**
> I ran the commands but it still didn't save it. what do you mean by 
in /etc/rc.local ?

press> alt+f2
type> gksudo mousepad /etc/rc.local

see pic.

---

### Post by geovino on 2009-07-04
Thanks, I added that line to /etc/rc.local
but it still doesn't save it.

I get this error:

davek@davek-desktop:~$ sudo alsactl store
[sudo] password for davek: 
E: core-util.c: Home directory /home/davek not ours.
davek@davek-desktop:~$ 

how to correct this?

---

### Post by kerry_s on 2009-07-04
> **geovino said:**
> Thanks, I added that line to /etc/rc.local
but it still doesn't save it.

I get this error:

davek@davek-desktop:~$ sudo alsactl store
[sudo] password for davek: 
E: core-util.c: Home directory /home/davek not ours.
davek@davek-desktop:~$ 

how to correct this?

okay you got a messed up alsa install, go into synaptic & reinstall the alsa parts.

---

### Post by geovino on 2009-07-06
I reinstalled alsa-utils and alsa-base. but it still didn't save the volume settings. 

I have: alsactl restore & in my /etc/rc.local file. Should it be exactly like the line in your rc.local file? 

Which is:

alsactl restore >/dev/null 2>&1 &

---

### Post by kerry_s on 2009-07-06
> **geovino said:**
> I reinstalled alsa-utils and alsa-base. but it still didn't save the volume settings. 

I have: alsactl restore & in my /etc/rc.local file. Should it be exactly like the line in your rc.local file? 

Which is:

alsactl restore >/dev/null 2>&1 &

hmm, that's strange. have you checked your /var/log for any error messages.

no, it doesn't have to be like mine, the ">/dev/null 2>&1 &" just gets rid of any messages, errors or logs it might put out, mine works so i don't need logging. ;)

in the mean time, do you know how to add start up programs? (menu> settings> session & startup> application autostart)
if not let me know & i'll talk u through that.

i want u to add:
**amixer set Master 75% unmute**

to see if that helps.

---

### Post by geovino on 2009-07-06
> **kerry_s said:**
> hmm, that's strange. have you checked your /var/log for any error messages.

no, it doesn't have to be like mine, the ">/dev/null 2>&1 &" just gets rid of any messages, errors or logs it might put out, mine works so i don't need logging. ;)

in the mean time, do you know how to add start up programs? (menu> settings> session & startup> application autostart)
if not let me know & i'll talk u through that.

i want u to add:
**amixer set Master 75% unmute**

to see if that helps.

add to the /etc/rc.local?

I could a bit of help on the start up programs. thanks

---

### Post by kerry_s on 2009-07-06
> **geovino said:**
> add to the /etc/rc.local?

I could a bit of help on the start up programs. thanks

no, i want to try and have it adjusted on login when your desktop starts. it can be done from the gui si it's easy.

so open the **settings manager** & click on "**sessions & startup**", click the "**application autostart**" tab, click "**add**", then just fill in the stuff.
name = can be anything you want
description = again what ever you want
command = this is the important 1, put that command.

remember this is just for the main volume, the Master, if others need adjusting let me know.

some pics to help you along.

---

### Post by geovino on 2009-07-06
Thanks, I added: amixer set Master 75% unmute  as you said, but it still doesn't save the volume settings. I don't get it? It should save the settings without doing anything. I've used Xubuntu three other times in the past and never that this problem. I'll just live with it for now. It takes two seconds to unmute the volume. but it's still very strange. maybe one day I'll figure it out.

Maybe I should erase the: alsactl store & line out of the rc.local file?

---

### Post by kerry_s on 2009-07-06
> **geovino said:**
> Thanks, I added: amixer set Master 75% unmute  as you said, but it still doesn't save the volume settings. I don't get it? It should save the settings without doing anything. I've used Xubuntu three other times in the past and never that this problem. I'll just live with it for now. It takes two seconds to unmute the volume. but it's still very strange. maybe one day I'll figure it out.

Maybe I should erase the: alsactl store & line out of the rc.local file?

yes, you can remove that line in /etc/rc.local

that command doesn't save your setting, what its suppose to do is when you log in to your desktop, it should set the volume to 75% & unmute it, so you shouldn't have to.

is it not doing that? if so we can try putting the command in the ~/.profile file instead.

---

### Post by geovino on 2009-07-06
> **kerry_s said:**
> yes, you can remove that line in /etc/rc.local

that command doesn't save your setting, what its suppose to do is when you log in to your desktop, it should set the volume to 75% & unmute it, so you shouldn't have to.

is it not doing that? if so we can try putting the command in the ~/.profile file instead.

the command:  amixer set Master 75% unmute 

where would I place the command in the ~/.profile ?

---

### Post by kerry_s on 2009-07-06
> **geovino said:**
> the command:  amixer set Master 75% unmute 

where would I place the command in the ~/.profile ?

at the bottom.

---

### Post by geovino on 2009-07-06
> **kerry_s said:**
> at the bottom.

added to ~/.profile... thanks

---

### Post by kerry_s on 2009-07-06
> **geovino said:**
> added to ~/.profile... thanks

did it work?
you can remove the 1 in autostart to, just click on it, then select remove.

---

### Post by geovino on 2009-07-07
> **kerry_s said:**
> did it work?
you can remove the 1 in autostart to, just click on it, then select remove.

No, nothing works no matter what I do. maybe alsa has a bug in it. who knows. I give up on this one. it would be nice if the program had a save button that might save settings. I don't know what I'm doing wrong at this point if anything.

davek@davek-desktop:~$ sudo alsactl store
[sudo] password for davek: 
E: core-util.c: Home directory /home/davek not ours.
davek@davek-desktop:~$ 

this may have something to do with it. I can't save the command, alsactl store

what does it mean, E: core-util.c: Home directory /home/davek not ours ?

---

### Post by kerry_s on 2009-07-07
try removing pulseaudio with synaptic.

---

### Post by geovino on 2009-07-07
> **kerry_s said:**
> try removing pulseaudio with synaptic.

That worked!! 

Now Streamtuner won't play streams with Audacious, maybe it needs pulseaudio, but I'm using movieplayer to play the streams so it's OK.

Thanks :D

---

### Post by kerry_s on 2009-07-07
> **geovino said:**
> That worked!! 

Now Streamtuner won't play streams with Audacious, maybe it needs pulseaudio, but I'm using movieplayer to play the streams so it's OK.

Thanks :D

did you remove all the pulseaudio-module junk to?
i doubt it needs pulseaudio & don't see it in the depndencys.

---

### Post by geovino on 2009-07-07
> **kerry_s said:**
> did you remove all the pulseaudio-module junk to?
i doubt it needs pulseaudio & don't see it in the depndencys.

you mean files like libpulse and pulseaudio-utils ?

---

### Post by kerry_s on 2009-07-07
> **geovino said:**
> you mean files like libpulse and pulseaudio-utils ?

the libpulse0 is okay, i have that one, but the pulseaudio-* you don't need.

---

### Post by torfason on 2009-08-27
This solution worked for me as well. However, I would recommend that those afflicted by this issue try the following solution before uninstalling pulseaudio, since it is much less invasive, and seems to have worked for those who tried it.

[http://ubuntuforums.org/showthread.php?p=7818030](http://ubuntuforums.org/showthread.php?p=7818030)

---

