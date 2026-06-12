---
title: "Flash Sound Cuts Out/ Movie Player Sound Stutters"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by JeremiahSD on 2008-01-27
I'm running Xubuntu (Gutsy, AMD64) on an HP Media Center m7640n with onboard sound.  This machine also boots Windows XP.  I have to physically unplug the computer after a Windows session to have any sound at all, a problem others have mentioned.  Inconvenient, but not a big deal.

I have been having other sound problems since I first installed Xubuntu and have gone through many threads attempting to solve them.  Sometimes I think I've fixed it, but the main problem keeps coming back.

Assuming I have remembered to unplug the computer before starting Xubuntu following a Windows session, I generally have sound for at least a few minutes, sometimes over an hour.  Movie Player works fine.  Youtube and other flash sites work fine (I generally use Swiftweasel or Swiftfox as my browser).  Almost invariably, though, Flash will either freeze after some time or Flash will play but with no sound.

At this point, Movie Player will play the file "Experience ubuntu.ogg" in the /usr/share/example-content, but the sound stutters/loops until I exit Movie Player.  However, if I also have a frozen flash video or a silent flash video playing at the same time Movie Player's sound is stuttering/looping, I must close both Movie Player and the browser window to stop the stuttering/looping.

I am still a relative beginner in the Linux world, but I would be happy to try to provide any other information that might be helpful in solving this problem.  I am grateful for any help the community can provide.

(BTW, I also have Xubuntu running on an HP laptop that originally had Vista installed.  This is a single-boot system and I have had no problems with it.)

---

### Post by ubuntu-freak on 2008-01-27
> **JeremiahSD said:**
> I'm running Xubuntu (Gutsy, AMD64) on an HP Media Center m7640n with onboard sound.  This machine also boots Windows XP.  I have to physically unplug the computer after a Windows session to have any sound at all, a problem others have mentioned.  Inconvenient, but not a big deal.

I have been having other sound problems since I first installed Xubuntu and have gone through many threads attempting to solve them.  Sometimes I think I've fixed it, but the main problem keeps coming back.

Assuming I have remembered to unplug the computer before starting Xubuntu following a Windows session, I generally have sound for at least a few minutes, sometimes over an hour.  Movie Player works fine.  Youtube and other flash sites work fine (I generally use Swiftweasel or Swiftfox as my browser).  Almost invariably, though, Flash will either freeze after some time or Flash will play but with no sound.

At this point, Movie Player will play the file "Experience ubuntu.ogg" in the /usr/share/example-content, but the sound stutters/loops until I exit Movie Player.  However, if I also have a frozen flash video or a silent flash video playing at the same time Movie Player's sound is stuttering/looping, I must close both Movie Player and the browser window to stop the stuttering/looping.

I am still a relative beginner in the Linux world, but I would be happy to try to provide any other information that might be helpful in solving this problem.  I am grateful for any help the community can provide.

(BTW, I also have Xubuntu running on an HP laptop that originally had Vista installed.  This is a single-boot system and I have had no problems with it.)


Have you installed alsa-oss? Install the essential packages in my how-to and then reboot. Has helped some with sound issues. 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan
 
P.S. You will have to edit some package names to suit your Xfce system.

---

