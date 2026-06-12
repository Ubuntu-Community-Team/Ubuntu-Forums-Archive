---
title: "no sound on internet"
date: 2008-11-11
forum: Multimedia Software
---

### Post by SyntaxMage on 2008-11-11
Alright, I've been all over the forums looking for a solution to my problem, but I have found nothing that works, so if anyone can help it would be greatly appreciated. Here's the problem: I just upgraded to Ubuntu 8.10 a few days ago and it was running great so far. I re-installed my plugins for firefox because i got the prompt when i visited youtube. The sound was fine both online and on my desktop. Now, for some reason, I logged on the other day and none of my sound was working. After searching through the forums here for a while i found a solution and went to System>Preferences>Sound and changed them from "Autodetect" to "HDA Intel ALC 268 Analog (OSS)" because no others worked except that and "OSS Open Sound System". So now Rhythembox and Movie Player have sound just fine, but youtube and any other video site still gives me nothing but static (so does my startup sound, which is an intro to an evanescense song). It's all just fuzz. I've tried installing a different flash player, i've installed the latest update of adobe flashplayer, restarted the system several times, went to the synaptic package manager and installed libflashsupport or whatever that was called and still nothing. Not sure what to do at this point, I have been searching around for a solution on the boards but haven't found anything yet. If anyone knows either how to fix this problem, or could direct me to a forum I may have missed that will fix the problem, it would be greatly appreciated. Thanks to all.

---

### Post by gandaran on 2008-11-11
I believe flash doesn't support OSS, maybe thats why you get no sound from youtube videos, if it worked before, I would recommend to set up sound to original settings and try find out where is the problem.
can you post the output of **locate libflash**
and type this code in firefox url bar
```
about:plugins
```

---

### Post by psyke83 on 2008-11-11
You're probably suffering from an ALSA bug where your PCM or Master mixer gets muted or set to 0% (it seems a common problem for many on Intrepid).

Check the volume levels via:

```
$ alsamixer -Dhw
```

You should also follow steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") guide.

---

### Post by SyntaxMage on 2008-11-11
syntaxmage@SyntaxMobileMage:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so
syntaxmage@SyntaxMobileMage:~$ 

there's the output for you.

---

### Post by SyntaxMage on 2008-11-11
> **psyke83 said:**
> You're probably suffering from an ALSA bug where your PCM or Master mixer gets muted or set to 0% (it seems a common problem for many on Intrepid).

Check the volume levels via:

```
$ alsamixer -Dhw
```

You should also follow steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") guide.

I just checked and you're right, the PCM Volume is set to zero.

---

### Post by SyntaxMage on 2008-11-11
> **psyke83 said:**
> You're probably suffering from an ALSA bug where your PCM or Master mixer gets muted or set to 0% (it seems a common problem for many on Intrepid).

Check the volume levels via:

```
$ alsamixer -Dhw
```

You should also follow steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") guide.

alright, i did the steps 2-5 and it did nothing for me. Still no sound on the internet and i also had no sound anywhere else until i changed the "Autodetect" in sound options back to what it was before. Now i'm back to square one, but at least we know my PCM volume is muted, i just went to volume control and put the volume up, i'm going to try that i suppose.

---

### Post by SyntaxMage on 2008-11-11
Alright, PCM Volume back up, and everything working just fine. thank you all for all of your help. I learned something new. lol. Thanks again everyone.

---

