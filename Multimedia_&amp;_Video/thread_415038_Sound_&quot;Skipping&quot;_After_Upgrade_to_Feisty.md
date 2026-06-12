---
title: "Sound &quot;Skipping&quot; After Upgrade to Feisty"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by killerds on 2007-04-20
After upgrading to Feisty I have been having a weird sound skipping problem in all applications, system sounds, streaming, mp3's, movies, etc.  It is not specific to any one application.  I am use a USB Headset that uses the C-Media chipset for sound control.  I was not having these problems in Edgy.

The problem seems to happen every 10-15 seconds when lisetning to an mp3 or watching a movie.  it will occur Randomly during system sounds (startup/shutdown/events).  Anyone have any suggestions?

Fyi, I do have a modified .asoundrc if that makes any difference.  I use it in order to switch between my internal soundcard and the headset.  Can't post it now as I'm at work :-k

Edit: I also have a Sound Blaster Live! card that appears to function properly, no skipping, maybe a little crackling but nothing major.  It appears that some of the newer alsa drivers are not functioning properly.

---

### Post by killerds on 2007-04-24
This is driving me crazy, has anyone else had this problem?

Edit: I timed it, it happens every 30 seconds like clockwork.

---

### Post by Nyr on 2007-04-24
Not going to be of much help, I'm afraid, but I just wanted to say that after upgrading to Feisty I experience a similar problem. Interestingly enough, the problem is with my Soundblaster Live. The skipping occurs at a much greater frequency, though, and after timing it, it seems I get a major skip every 6 seconds and a minor one (it is less noticeable, but still there) every 3 or 4 seconds. Needless to say, this is driving me crazy too. 

At first I couldn't get any sound, and after playing with things a bit, I managed to get the Soundblaster Live working... except it is now skipping. Maddening. In any case, will keep investigating...

Cheers,

Nyr

EDIT: Well, It seems that the skipping occurs when playing files with the Movie Player. When playing files with Rhythm Box, it doesn't skip... it crackles. So, yeah... I'm not quite sure what that means, but I guess I'll try to resolve the problem in Rhythm Box first. Although I don't know, maybe both problems are related. Argh. Anyone knows? (I know, I'm a newbie, so apologies for any stupid question).

---

### Post by sam hassell on 2007-04-24
Ive got the same issue with the  sound skipping. To me it is most noticable when playing mp3s in any player, although other strange stuff occurs with sound elsewhere.

When I first installed Herd 4 or 5 (cant remember which) I didnt have this problem - it only surfaced in the week or two before feistys launch.

seems to occur with OSS and ALSA, but im no pro when it comes to linux audio.

---

### Post by Drew_Blood on 2007-05-05
Sorry, just another "me too" reply. I'm brand new to Linux so I won't be much help. 

I'm on a Dell Latitude c600 with an ESS Maestro 3i sound chipset running Ubuntu Feisty. I haven't even messed with playing mp3s yet because the skipping is so noticeable with everything else, from the startup sound, Gaim notifications, embedded Flash in Firefox, everything that has sound. One thing I'm noticing that no one else has mentioned is it's not *just* sound, as my trackpad actually stops responding for a couple of seconds as well. If I didn't know better I'd think it was the hard drive cacheing but on a 1 Ghz system with 512 MB of RAM it doesn't seem like it should be happening every minute or so like it is.

---

### Post by Drew_Blood on 2007-05-10
Has anyone had any luck with this issue yet?

---

### Post by killerds on 2007-05-11
As of yet, have not found a solution.  I'm going to be filing a bug report shortly.

---

