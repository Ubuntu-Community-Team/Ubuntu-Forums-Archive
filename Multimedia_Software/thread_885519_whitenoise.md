---
title: "whitenoise"
date: 2008-08-10
forum: Multimedia Software
---

### Post by philmetz on 2008-08-10
Hi i just updated to 8.10 and then when i tried to play a song or even when my ubuntu stated up with its starting up noise you can hardly hear it, i mainly hear whitenoise (well its more like a poor quality sounding) along with the song. It was working before the upgrade fine.

Any ideas?
am thinking i need a new driver but am not sure where to get it from?

thanks

---

### Post by philmetz on 2008-08-10
Anyone have any ideas?

---

### Post by falcon61102 on 2008-08-10
Often times you mic or line in input can generate white noise or static.  Is it possible that you had your mic or line in muted or turned real low before the upgrade and now the settings are different.  

Also what type of hardware you talking about? Run and post the results of:
```
sudo lshw -C multimedia
```

That will help anyone to further help you.

---

### Post by cariboo on 2008-08-11
Have a look at this page, it sounds like your audio is coming out ot the pc speaker:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Follow it step by step and you'll have a working audio system.

Jim

---

### Post by philmetz on 2008-08-15
I followed this guide:
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

But still didnt fix it. Still teh cracking sound.

i ran the command:
sudo lshw -C multimedia

and it said:
PCI (sysfs)

---

### Post by philmetz on 2008-08-16
Anymore ideas?

---

### Post by falcon61102 on 2008-08-16
That means that the command froze after typing it in.  You should have been presented with a list of all your devices dealing with your multimedia.  Try restarting your system and running it right after booting up.  Often times it freezes because another app is accessing the hardware and not allowing the system to so trying it right after restarting should eliminate that hopefully.

---

### Post by philmetz on 2008-08-16
Nope i still get the cracking noise when sound plays.

---

### Post by falcon61102 on 2008-08-16
Have you been able to get the results of:
```
lshw -C multimedia
```
or is it still freezing during the check?

---

### Post by philmetz on 2008-08-17
yes it said this:
and it said:
PCI (sysfs)

And nothing happened after it

---

### Post by falcon61102 on 2008-08-17
Ok, something is causing that command to freeze and that may be related to your problem.  Do you have any startup apps that may want to take control of your sound as soon as you log on?  Even programs like Pidgin or Thunderbird can effect your sound when its not set up properly.  

A way you can lessen the effect of some of your programs on your sound card is to temporarily disable the sounds and see if that helps.  A far as Pidgen and Thunderbird are concerned, you can turn off sounds for sending/receiving messages and emails.  Also, go to System>Preferences>Sound and uncheck the system sounds check box for now.  Then try restarting and running that command again.  Also, try running it as "sudo" that can help too.

---

### Post by Sinkingships7 on 2008-08-17
When you unplug your speakers, does the sound persist? If not, do another pair of speakers work?

---

