---
title: "Sound for me, but not for the 2nd Ubuntu account, why?"
date: 2016-09-09
forum: Multimedia Software
---

### Post by javierdl on 2016-09-09
In my account, I have sound playback for everything. But when going into my wife's account, there is none. What could it be? 
I created a new account and it worked there, but only while I was there. Then I went to my account, and went back to the new account only to find that the sound no longer worked :(

Thanks, guys.

JDL

---

### Post by TheFu on 2016-09-09
Could be permissions on the audio device(s).  Compare the groups your userid is in with those of your wife.  Used to be something like **plugdev** was needed.

---

### Post by javierdl on 2016-09-09
Thanks TheFu.
I did try including my wife's account into my group to test it. But it didn't help.
Do you mind elaborating about plugdev?

JDL

---

### Post by TheFu on 2016-09-09
open a terminal.
type '**id**'

Those are groups.  plugdev is a group that I think still exists and allows userids locally logged in to access things like sound.

---

### Post by javierdl on 2016-09-09
[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1473475524751/temp/id_results.jpg[/IMG]

It does show 29 (audio) for me too.

---

### Post by TheFu on 2016-09-10
If that isn't it, I'm clueless.  On my system, I'm not a member of "audio", just plugdev and sound works.
Perhaps working through the **ubuntu sound troubleshooter** is needed? Google finds it.

BTW, if your wife isn't technical, I'd remove her from the adm and sudo groups.

---

### Post by Yellow Pasque on 2016-09-10
> **javierdl said:**
> It does show 29 (audio) for me too.

Is there a reason for that? It may be blocking other users. Normally, your user shouldn't be in the audio group on a system with pulseaudio:
[http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

>  plugdev is a group that I think still exists and allows userids locally logged in to access things like sound.

I've never heard plugdev used in relation to sound card permissions. Debian wiki says plugdev is for users to mount removeable storage: [https://wiki.debian.org/SystemGroups](https://wiki.debian.org/SystemGroups)

---

### Post by javierdl on 2016-09-10
>  It may be blocking other users.
[Temüjin]("https://ubuntuforums.org/member.php?u=327594"), thanks for replying.
Assuming that's the case, how do I fix this?

---

### Post by TheFu on 2016-09-10
I was under the impression that plugdev was for access to local hardware that shouldn't be available remotely, not just storage. That would usually include dsp, speakers, scanners, and other specialty devices.  Don't recall where/why I learned that or if it was on a Linux or Unix system. After all, why should a remote userid be able to run a music player?  Ok, sure there are reasons for that (and I've wanted it), but most people wouldn't.

This doesn't mean that plugdev actually does what I thought it did. Just explaining my thought process.  

There is a good uubntu sound troubleshooter available.  I needed help, followed the instructions, posted the output and within a few hours, someone replied with exactly the correct solution. Should also say that the solution didn't make any sense to me, a 25+ yr Unix admin.  Just sayin'.

---

### Post by Yellow Pasque on 2016-09-11
> **javierdl said:**
> Assuming that's the case, how do I fix this?

Remove yourself from the audio group and reboot:
```
sudo vim /etc/group
```
(If you don't like vim, use the text editor of your choice.)

The only thing that should be in the audio group is 'pulse' on most systems. Of course, that doesn't answer the question of why you put your user in the audio group in the first place. Maybe there was a good reason for it?

---

### Post by Yellow Pasque on 2016-09-11
Oh, I see. You're using Ubuntu Studio, which has actually has the user in audio group "out of the box" (for purposes of using JACK I guess).
Then I'm not sure exactly how to handle this because I've never used UbuntuStudio or JACK. I think I'd still try to remove the user from the audio group to see if that solves the issue. If it does and you want your user in the audio group, maybe ask in UbuntuStudio forum to see if there's a workaround.

---

### Post by javierdl on 2016-09-11
YYYYEEEESSSS!!!!!!
Editing the group did it!!!!
Thank you so much, Temujin :)

I wonder how we ended up in that group on the 1st place?
Is there any other group we shouldn't be part of?

---

### Post by Yellow Pasque on 2016-09-11
From your post history, it looked like you were using UbuntuStudio, which has the user in 'audio' to allow some features of JACK (low-latency/realtime audio) and possibly some other things I'm not aware of.

---

