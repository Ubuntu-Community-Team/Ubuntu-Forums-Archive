---
title: "No sound after switching user or locking screen."
date: 2010-10-30
forum: Multimedia Software
---

### Post by JimJam707 on 2010-10-30
Hey there. My problem started when I updated Ubuntu 10.10 developer release (or whatever it's called :)) to Ubuntu 10.10 Final. When I switch user or lock the screen and log back in, my computer makes no sound. I know it's not muted since I can see that in the volume control. The only way I can fix it is by restarting my computer.
Any help?
If you need any more info please ask :(

---

### Post by JimJam707 on 2010-10-30
I hate to bump but.
BUMP

---

### Post by JimJam707 on 2010-10-31
Sorry but this is annoying me.
Bump.

---

### Post by mashedbear on 2010-11-07
I have a similar problem.

The scenario I have is that sound works fine for the first user who logs onto the system, but when the session is switched to another user they often are unable to hear any sound. 

The applications typically being used where the problems are experienced are banshee and Firefox (browsing iplayer, you tube or similar). 

It appears if one user is using / has used sound and their session is still active - then no other users can have sound ... I know this shouldn't be the case!

A not very good workaround is to either log out other users, or force reloading alsa using ```
sudo alsa force-reload 
``` 

Am using Ubuntu 10.10 64-bit (I had the same problem in Ubuntu 10.04 as well). I think I am running alsa version 1.0.23 (at least this is what alsactl --version returns), and pulse audio pulseaudio 0.9.21-63-gd3efa-dirty (found by running pulseaudio --version).

Would appreciate help if there is a known fix or some guidance on steps to try and work through, as this issue doesn't appear to be covered in Ubuntu community sound documentation.

Thanks

---

### Post by ricardisimo on 2011-01-17
I have to assume that the problem is with pulseaudio. I had zero problems before pulseaudio became the default sound server.

It never fails. I log in and my sound is fine. Then my wife switches users to check her email. I log her out, and bye-bye sound. The only way to get it back is to restart the computer.

Is there a command-line shortcut for getting control of the sound back? What sort of a crazy sound server lets whole-system sound be taken over by a secondary user?

---

### Post by Troilus on 2011-04-02
I have the same problem, but it appears to be linked in someway to either Gmail or facebook on Firefox.  I'm not sure how, but ...

Example: 

My wife and I are both logged in.  She has facebook and gmail open.

I log in.

I try to play some audio, no sound comes out.
My volume indicator shows that my volume is turned up.
I log into my wife's user ID and find that she has muted her volume.
I un-mute her volume control and return to my user.  
Still no sound.
I run 'ubuntu-bug audio'; it hangs at the point that it is supposed to be playing a sound test. I leave it running then log into my my wife's ID. 

I start closing her open firefox tabs one by one.  After I've closed her open facebook and gmail tabs the sound test starts to play (even though I'm running it under my id, and I'm still logged into her id.)  
I return to my user and try to play audio.  It works.

I have no idea what the cause of the problem is, but it is a consistent fault.  Anyone know how to log it as a fault?

---

### Post by jacanterbury on 2011-04-21
same problem - very annoying - 

the ....force-reload command suggested above sadly makes no difference for me (the other user had already logged out)

any other work arounds apart from rebooting??

---

### Post by n2uad on 2012-06-07
When another person logs in they get no sound. Only the first login gets sound. Everyone else gets no sound. We have 3 users and one common way we use the system is to use the console to log in while leaving the prior users still logged in. Only the first user logged in gets sound.

Now I see this problem goes back a while. And a while back I tried Ubuntu and found it was not ready for prime time. And I see it's still not ready!

Ubuntu 64bit 12.04

---

### Post by francisco2007 on 2012-06-29
Very annoying issue.

Had on my old computer with x86 and now on a new computer with x64.
I had ubuntu from 7.04 and I can't tell when this switch user no sound bug entered...

I'm trying to have ubuntu as my main desktop, and I can't ask my wife to run sudo whenever she switches to her account, right?

---

### Post by oldos2er on 2012-06-29
Please start a new thread, this one's two years old.

---

