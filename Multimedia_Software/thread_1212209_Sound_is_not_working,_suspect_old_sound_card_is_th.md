---
title: "Sound is not working, suspect old sound card is the culpret"
date: 2009-07-13
forum: Multimedia Software
---

### Post by pwhipped on 2009-07-13
I have a old computer that I just dropped 9.04 on to learn ubuntu. This is my first linux installation so I am still in the process of learning the ins and outs of the OS. Everything but sound is working great. The sound card in the computer is a Creative Labs 4740. I've read everything I can find on the subject, messed with alsamixer, and gone through the troubleshooting (how to sound). I've also read old threads that say Creative Labs is largely unsupportive of their cards in regards to linux. :/

If I turn up the sound real loud while playing music and other sounds I can hear it. I really have no clue what that means, but I thought I'd mention it. 

aplay -l outputs card0 as AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 etc etc.

I am very confused to say the least. Any help or direction would be greatly appreciated. Thanks!

---

### Post by igorzwx on 2009-07-13
You see, some people upgrade ALSA (today) and it works for them.

I changed to OSS4

It works well on my notebook, and on the old box (of 2001).
On the old box I have now many things installed.
Now I am experimenting with Ubuntu Lite Beta netboot

---

### Post by pwhipped on 2009-07-13
I've tried switching to OSS through System>Pref>Sound


I saw no change. :/

---

### Post by igorzwx on 2009-07-13
Your OSS is perhaps ALSA emulation of OSS.
It should be the same, otherwise it is not a good emulation.

---

### Post by pwhipped on 2009-07-13
I'm not sure I understand what you're saying.

---

### Post by igorzwx on 2009-07-13
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

---

### Post by pwhipped on 2009-07-13
Ok I read that. How would I go about using OSS4 or any of the OSS's?

---

### Post by igorzwx on 2009-07-13
[http://ubuntuforums.org/showthread.php?t=1211713](http://ubuntuforums.org/showthread.php?t=1211713)

---

### Post by pwhipped on 2009-07-13
Thanks. I'll try that and post my results.

---

### Post by igorzwx on 2009-07-13
Good luck!

If I am not in the forum, and you need help,
you can send e-mail.

---

### Post by pwhipped on 2009-07-13
Here's the update. I got OSS4 installed. I still don't have sound. The odd thing is though, right when the installation of OSS4 it said it recognized the card and i heard a thump in my speakers, almost as if it had been recognized by the computer. I don't know what to do anymore. If anyone has any more suggestions I'd be more than happy to try them out.

---

### Post by igorzwx on 2009-07-14
By your descriptions, it looks like installation was succesful.

Just a few simple things to do, perhaps.

Open terminal, type:

ossxmix

And the mixer GUI should start.

Open another terminal, type:

osstest

it should play sounds

I want to see results of these commands:
ossmix
ossinfo -v3

Execute them, and copy the listing on terminal (Ctrl+C)
and post it here.

more info:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
If you have OSS installed properly, but still have issues, the OpenSound project has free user support forums and an IRC channel. Be sure to include the output from these commands so the experts don't have to prompt you for them 



ossmix 
ossinfo -v3

Also, you'll want to note if the osstest command works and plays sound. 
 
**Forums**

 You can make a thread on [the OpenSound user forums]("http://www.4front-tech.com/forum/index.php").  
 
**IRC**

 [Freenode]("http://freenode.net/irc_servers.shtml") hosts the OSS support channel (#oss). You can paste your support information from the aforementioned commands [here]("http://oss.pastebin.com/")

---

### Post by igorzwx on 2009-07-14
System -> Preferences -> Sound
change everything to OSS4

read the pdf manual of OSS4
hope you downloaded it too, 
together with deb

---

