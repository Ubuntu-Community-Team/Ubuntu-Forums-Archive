---
title: "Help Setting up Remote"
date: 2008-09-08
forum: Mythbuntu
---

### Post by false_apology on 2008-09-08
Hey Folks,

I'm just starting to get my hands dirty with Mythbuntu and I must say I'm learning a lot. I've got everything going, except I can't seem to get my remote to function at all. What I'm trying to do is use the remote bundled with the XBOX 360 HD DVD drive.. This is a MCE compatible remote. I have a USB MCE receiver I am using this with as well. I wasn't entirely sure which driver to use from lirc. I tried both with no luck. I'm tinkering around with the "old" version at the moment.

I must also say I'm still learning Ubuntu and Linux. I have some UNIX experience so I know the CL fairly well, at least well enough to get around and execute commands.

Anyway, I know the IR receiver works with the remote. The receiver lights up when I press keys on the remote. The other promising thing is that the mode2 command outputs information when I run:
```
sudo mode2 -d /dev/lirc0
```
and press on the remote keys.

However, when I run irw I get nothin. Nothing responds in mythtv frontend either no matter how hard I mash the keys. I thought it was my config file, so I did some google searching and found a config file that was supposedly specifically for this remote.
So I put it in /usr/share/lirc/remotes in a new directory I created. I then put an "include" line pointing to the new file in the /etc/lircd/lircd.conf. Restarted lircd and still nothing. 

Like I said, i'm still learning here, and I know i'm missing something simple, especially since mode2 can report the raw information from the receiver.  Any suggestions from the gurus out there?

Thanks!

---

