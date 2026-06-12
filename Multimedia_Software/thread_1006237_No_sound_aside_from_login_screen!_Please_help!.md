---
title: "No sound aside from login screen! Please help!"
date: 2008-12-09
forum: Multimedia Software
---

### Post by paintedbull on 2008-12-09
Not sure what to do but I know many people have had this same problem before me and there seems no clear solution.

First of all, I've got Ubuntu 8.10. I have an Intel ICH8 soundcard, which is integrated into my motherboard and is also one of the few soundcards not supported with a driver in ALSA.

here is a bunch of information about my system as diagnosed by ALSA:
[http://www.alsa-project.org/db/?f=a6498f1dc4f08df6bb95528db11f49a391992461]("http://www.alsa-project.org/db/?f=a6498f1dc4f08df6bb95528db11f49a391992461")

When i installed my Ubuntu, everything was working perfectly. my sound stopped working after i installed audacity. I messed around with it for about 3 hours last night and got it to work again. it was working this morning, now after a reboot it has gone down once more.

I currently can hear test sounds in the preferences>sounds tests if I set it to OSS, but all i can hear is the test sounds. Sounds on the internet don't work.

Amarok will play my sound now because I've set it to output through OSS.

the sound at the login screen works, as well as the "login succesful" sound.

nothing else works.

I dont know how to get it to work now. i've done all sort of things to try and fix it, followed everybody's solutions, and I just can't get it to work. I had to disable sounds in pidgen because when I tried to send a message, it would crash because it was trying to play a sound.

why doesn't alsa support my card? it seems so common...

anyways, any help would be greatly appreciated. i dont know what to do here. this is quite frustrating.

thanks in advance, any tests you need me to run i will gladly do. just hope i don't have to guy buy a soundcard just to sort this out.

---

### Post by paintedbull on 2008-12-09
bump because i know this will disappear once i go to sleep and i need some sound...thanks guys

---

### Post by goffman on 2008-12-09
Hi

I too would like some assistance on this.  I suppose I am a bit of a noob when it comes to Linux (although I first ran linux back in 1998 and have recently come back) so if anyone can help in easy terms it would be appreciated.

I have searched on here and Google but haven't managed to turn anything up.  Apologies if I have missed something obvious but I did search and found plenty of questions, but precious few answers.

I believe I have the same integrated soundcard as the other poster, and am also running 8.10.  I get the drums/system start sound.  If I go to sound test I get the sound test playing and MP3's play ok in Amarok but no system sounds (just that darn annoying PC speaker... now disabled).  I know it is a little thing, but the little things can be annoying.

Very frustrating as it appeared to work under Fedora, however not much else seemed to, hence back to Ubuntu.

---

### Post by philetus on 2008-12-09
Did ya'll try the:
  Comprehensive Sound Problem Solutions Guide
at the top of the forum page?

---

### Post by paintedbull on 2008-12-09
> **philetus said:**
> Did ya'll try the:
  Comprehensive Sound Problem Solutions Guide
at the top of the forum page?

yes

"Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)"
it is apparent that there is no driver for my chipset, as stated earlier.
my question is: why did sound work 100% for me when i first installed, and how do i get back to that?

---

### Post by markbuntu on 2008-12-09
Try this first,

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

if that does not work go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If your sound worked at all, for anything, that means there is a working sound driver, you were using it.

---

### Post by paintedbull on 2008-12-09
> **markbuntu said:**
> Try this first,

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

if that does not work go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If your sound worked at all, for anything, that means there is a working sound driver, you were using it.

thanks mate. yeah i actually installed a fresh kernel and it's working again, but i'm not sure if it'll go down again. it's done this a few times already. i really appreciate the help. thanks

---

