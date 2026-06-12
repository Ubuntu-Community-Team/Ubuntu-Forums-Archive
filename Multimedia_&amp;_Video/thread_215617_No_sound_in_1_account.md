---
title: "No sound in 1 account"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by Hij on 2006-07-14
I'm using Xubuntu (Drake 6.06), and everything is working perfectly expect the sound.
Before I used Ubuntu (Breezy), and I had sound.
On start up I here sound (log-in screen)
If I log in as root user (first account) there is no problem
If I log in as seccond user (no root) there is no sound.
I get this message with BMP: 
> 
Coeldn't open audio
Please check that:
1. You have the correct output plugin selected
2. No other programs is blocking the soundcard
3. Your soundcard is configured properly

VLC plays the music, but I can't hear anything.

Please help, because I don't wound to use my root account for my daily use.

I hope this is enough info, and sorry for my bad english!

edit more info: System->Preferences->Sound has no cards listed in the default card pulldown
In the root account is default selected, but there is a pulldown with this two options:
1 VIA 82C686A/B REV40
2 VIA 82XX Modem

---

### Post by bikeboy on 2006-07-14
Try looking at the contents of /etc/group . Check to see that your normal user is a member of the audio group.

---

### Post by Hij on 2006-07-14
Thanks for your reply!
My normal account doesn't stay in the list
> audio: x:29:laptop Laptop is my root account
What do I have to type to get this working in my other account?
I ask this because when I look at CDROM there stands:
> cdrom: x:24:haldaemon,laptop
But haldaemon isn't the user name of the account. Can I just put the same in the audio?
And I can't save the changes, do I have to open it with the terminal?
I used "nano etc/group" but then I get a empty file. When I open it with thunar I can't save it (I'm in the root account)
I have also tryed with sudo before nano, but in the terminal I get a empty (new) file.

---

### Post by Hij on 2006-07-14
I have fixed the problem.

---

### Post by bikeboy on 2006-07-15
Glad you got it fixed. I gather you were missing the / from before /etc. If that wasn't your problem let us know how you fixed it.

---

