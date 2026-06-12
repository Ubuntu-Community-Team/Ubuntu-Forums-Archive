---
title: "NO way fo get the microphone working :X:X"
date: 2010-01-05
forum: Multimedia Software
---

### Post by residentevil on 2010-01-05
Dear all

I was trying the get the microphone working for 2 days, unfortunately I failed.

The strange think is that when I booted sabayon linux the microphone was working absolutely fine.

Some tips: pulse-audio - removed 

I am really desperate !

---

### Post by duanedesign on 2010-01-05
You could tell us a bit more about the type of hardware and version of Ubuntu you are using. Could you also please post the output from the following command.

```
head -n 1 /proc/asound/card0/codec*
```

In the meantime have a look at these:

[Here is a guide]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") for troubleshooting sound in Karmic.

[This thread]("http://ubuntuforums.org/showthread.php?t=789578") is also a good resource for sound problems

[This thread]("http://ubuntuforums.org/showthread.php?t=843012") takes you through many problems and has a section on microphones specifically.
-
-
-

---

### Post by residentevil on 2010-01-05
~

---

### Post by residentevil on 2010-01-05
a

---

### Post by buntunub on 2010-01-05
Your using Xubuntu. Xubuntu is not so forgiving to newbies to Linux. If you like Xfce/Xubuntu then you need to up your Linux game and learn how to do things on your own. I would start by doing some searches for your problems on these forums and put Google hard to work too. Then, read, read, read, and then.. read some more! The command line is your friend, and I don't mean any of this in a facetious way. Using Linux implies that you wish to do things the "Linux way". This means that you must learn about your hardware, and learn at least the basics of Linux so that you can master your computing experience. Give it a go and you will quickly discover why us Linux geeks love our OS so friggin much!

Most the time, everything works like a charm OOTB. Sometimes, things dont. Thats just how it is with Linux. Your experience with it will drastically improve the more you learn however. Big hurdles like what your experiencing now will become childs play simply by learning a few simple and very basic commands like:

lspci
lsusb
dmesg
cat /var/log/messages
cat /var/log/syslog
cat /var/log/daemon.log
cat /var/log/auth.log
cat /var/log/kernel.log

Lastly, try using man alot.

man lspci
man lsusb
man dmesg
man man

You can use man for pretty much everything. If I dont know what command to use to do what I want I use apropos xxxxxxx -

apropos find
apropos logs
apropos mic
apropos who am i

In your case, you need to find (1) What is your hardware setup. How does Linux "see" what stuff your computer has, and (2) how did Linux configure it? Lastly, once you have that figured out, then (3) how can you modify settings to make it all work?

---

### Post by kingbaboune on 2010-01-06
I am having the exact same problem...  The Realtek microphone is simply not working anymore.

It did work when I installed Ubuntu about 3 weeks back.

Same
0-0/0: Realtek ALC850 rev 0
I am running Ubuntu Karmic

---

### Post by Slayer. on 2010-01-06
My microphone also isn't working on Karmic. I used the code, and got "Codec: Conexant CX20561 (Hermosa)"

---

### Post by kingbaboune on 2010-01-07
> **Slayer. said:**
> My microphone also isn't working on Karmic. I used the code, and got "Codec: Conexant CX20561 (Hermosa)"

Can you explain?

---

### Post by kingbaboune on 2010-01-09
Hi,

I got it to work...

Followed this: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

And installed the gnome alsa mixer.  For some reason the front mic input was disabled and the mic muted.

```

sudo apt-get install gnome-alsamixer

gnome-alsamixer

```

---

