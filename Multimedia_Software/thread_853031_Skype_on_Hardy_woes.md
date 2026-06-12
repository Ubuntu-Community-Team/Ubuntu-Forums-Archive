---
title: "Skype on Hardy woes"
date: 2008-07-08
forum: Multimedia Software
---

### Post by FFighter on 2008-07-08
To be honest, I've had all sort of issues and nasty problems with sound ever since I updated to Hardy. I got it managed to some level, getting PulseAudio to (kind of)  work, but only after endless hours of googling and messing up with my system, not that this is bad, sometimes it is fun to mess with a Linux system, but **certainly NOT your production workstation!** So, I was very disappointed.

The sound was half-working, only one application at a time could use the sound, but I left it that way.

Yesterday I needed to use Skype, and to my surprise (even though no other application was using sound at the time) sound output and input (mic) was simply not working! Oh god... let's google. 

Among the endless not so useful posts regarding Ubuntu and Skype problems, I then found out this article that seemed to be relevant:

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

He kindly shares his experiences and tells how to get a "full PulseAudio system"... now this really got me angry - **Shouldn't Ubuntu 8.04 come with the PulseAudio thing all set and ready to rock?**

Ok, I then installed all those million packages and did what he told, but couldn't really get the sound working with skype. Then googled again and found out about the "pasuspender" command. By starting skype like this:

```
$ pasuspender skype
```

Which suspends pulseaudio, so no music or any other audio but the ones from skype, I got sound kind of working. Only one channel though, don't know why.

So, I'm really disappointed on this whole PulseAudio thing. I remember using Skype in Gutsy with no problems and now, I have an half-***** skype working, but only after using a hack. 

Please, note, I do like the configurability of Linux, but if I wanted to loose my time with low level stuff I would have chosen slackware or gentoo.

For now, I'm using Skype on my XP desktop, which, not surprisingly, works very well.

So, please, share your experiences on getting Skype to work smoothly under Hardy. I hope to see better experiences.

---

### Post by grashdur on 2008-08-06
I share your frustrations (especially as I see nobody has responded to your sound questions). On my laptop I had to give up on Hardy altogether, because of problems like yours, and revert to Gutsy. On my desktop computer I've gotten sound to work out with Hardy. But for a while I was totally unable to get Skype to ring for incoming calls. I fiddled with all the sound settings, had no results, later fiddled with them all over again and for whatever reason it seems to ring correctly now.

---

### Post by polki@mac.com on 2008-08-07
This is what turns people away from Ubuntu/Linux, and it makes me so sad :-(

---

### Post by joshzam on 2008-08-08
I could not have written it better myself. Thank you for posting my exact experience. Now let's see if anyone is able to give some sound advice (sorry). And I'm with you whole-heartedly about my disappointment at Ubuntu not working correctly out of the box. I love me some fiddling, but this should be trivial.

---

### Post by halln on 2008-08-08
> **joshzam said:**
> I could not have written it better myself. Thank you for posting my exact experience. Now let's see if anyone is able to give some sound advice (sorry). And I'm with you whole-heartedly about my disappointment at Ubuntu not working correctly out of the box. I love me some fiddling, but this should be trivial.

I had this problem before when i installed hardy the first time on my new laptop, I was thinking that I made something wrong so I reinstalled hardy again then the sound works perfectly after.

---

### Post by markbuntu on 2008-08-09
If you look in the stickies at the top of the Multimedia and Video Forum, there is a easy solution to the skype problem.

---

### Post by crazy ivan on 2008-08-28
Could you post the link please?

---

### Post by habtool on 2008-08-28
Honest answer. IMHO, after much messing around with pulse-audio and trying the long perfect pulse-audio thread, is just remove it altogether..

[http://ubuntuforums.org/showthread.php?t=876594](http://ubuntuforums.org/showthread.php?t=876594)


I guess hw:0 is occupied by PulseAudio.

Removing PulseAudio is simple:

1. Disable Gnome system sounds. (important)
2. Remove "pulseaudio" and "pulseaudio-esound-compat". Optionally
install "esound" for applications that need it.
3. Reboot.

---

### Post by grashdur on 2008-09-20
I'd like to offer a few ideas, for anyone else having these problems: 

[http://ubuntuforums.org/showthread.php?p=5826629#post5826629]("http://ubuntuforums.org/showthread.php?p=5826629#post5826629")

---

