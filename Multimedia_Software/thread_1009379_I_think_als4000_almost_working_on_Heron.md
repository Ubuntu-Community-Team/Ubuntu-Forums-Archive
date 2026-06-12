---
title: "I think als4000 almost working on Heron"
date: 2008-12-12
forum: Multimedia Software
---

### Post by xylene2301 on 2008-12-12
The speakers "bong" when heron boots up but then no sound.
I have checked and I am in the audio group.  
I get this from the terminal.  It doesn't look right but I'm not sure what to do about it:

sudo modprobe snd-
FATAL: Module snd_ not found.

I'm using the als4000 card and it shows uo when I 
cat /proc/asound/modules

I think I'm close to getting it working but there are just too many ins and outs and yes, I have referred to
Comprehensive Sound Problem Solutions Guide v0.5e
but would really appreciate it if someone would do some hand holding.

I am a pretty novice ubuntu user and would appreciate it if any tips assume only moderate understanding.

**Thanks so much!**
Xylene

---

### Post by markbuntu on 2008-12-12
Go here, it starts with very basic troubleshooting and goes on from there:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by xylene2301 on 2008-12-12
Thanks!
I consulted the info from your link and added a new user.  The new user's sound works nicely.
The article indicates that I should now amend the differences between the previously-existing hidden sound files and the ones that were just created (that work).

Is there a list of these files somewhere?

Thanks for your patience!
Xylene

---

### Post by markbuntu on 2008-12-12
Wow!! That does not work for a lot of people so consider yourself lucky.

Anyway this does tell you that your sound is not broken. YAY!!

There is no actual list but there are configuration files in your user home directory that are "hidden". You can view them by selecting View/Show Hidden Files in the Nautilus file browser. These are the only files that will be different between the two users. One file in particular is important and that is 

asoundrc.asoundconf

If you have this file in your old user and not the new one, you can try just renamining it to asound.asoundconf.bak to let the system defaults work. There are also some files in the ./pulse directory which you can do the same. If that does not help or makes things worse, you can always restore their original names back.

Also, many people just abandon their previous user name since this generally is a problem before they have put a lot of stuff in their home directory and it is a tedious task to try to find what the differences are.

My own home directory is a mess, I just looked in it. LOL!!

---

### Post by xylene2301 on 2008-12-12
I set Nautilus to show hidden files and searched the entire filesystem for asoundrc.asoundconf; it doesn't appear to be there.
But the good news is that heron has healed itself with a little encouragement! Banshee, Totem and the CD player now all have sound.

...and my boss used to insist that these machines could not have personalities...(He's out of the tech industry and is now a rabbi. For real!)

Thanks for all your help.

---

### Post by markbuntu on 2008-12-12
Always be nice to the machinery, it is trying as best it can.

---

### Post by xylene2301 on 2008-12-13
This machine may be my fave.  It's made from gifted and legacy parts.  It runs great with Heron and now Banshee 1.4 is running.
Banshee fired up, found my 30G video Ipod and said it couldn't open it because the Ipod's database was a version it couldn't read.  I turned my back on it for about 2 minutes and now it's read the Ipod and everything appears to be working!

I'm a little afraid that managing the Ipod's data with Banshee may cause trouble though; any experience with Ipods and Linux/Ipod managers?  I've seen a few alarming posts to various fora.

---

### Post by xylene2301 on 2008-12-13
Actually, I guess I spoke too soon:
With the dawn of the new day, My Heron comp has decided to be difficult.
I get sound on the Guest account (newly created) but not on the accounts created before the new sound card was installed. 
 
So what sound config files am I looking for and where would they be?  There don't appear to be any files on this computer with asound in the name.

Also Banshee no longer reads my Ipod on any of the accounts although it did yesterday; weird.

---

