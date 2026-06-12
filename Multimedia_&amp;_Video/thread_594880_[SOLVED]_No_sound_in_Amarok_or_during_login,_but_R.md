---
title: "[SOLVED] No sound in Amarok or during login, but Rhythmbox and Exaile work?"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by kexodusc on 2007-10-28
I'm out of my element here -  Installed Gutsy this week, and did all the usual software downloads.  For some reason amarok won't play any sound, and I've lost sound on my login.  
I can test my sound quard in the System --> Preferences -> and get the test tone, Exaile and Rhythmbox play my music - but Amarok won't.  Got a feeling it's a gstreamer vs xine issue, but that's just a guess.

I'd like the login sounds back but I can live without those - losing amarok would be a minor blow though.

is there a logical process I should go through to trouble shoot this?  Maybe an online guide or something?  Thanks for any help.

---

### Post by kexodusc on 2007-10-30
Well, not sure what I did excatly but I solved it.

I made an asound.conf file and set my av710 card to PCM out as described here:
[http://ubuntuforums.org/showthread.php?t=187920&highlight=av710+s%2Fpdif](http://ubuntuforums.org/showthread.php?t=187920&highlight=av710+s%2Fpdif)

Then I made sure to configure it as my default card so it wouldn't switch on me as described here (several steps down):
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem)

I had been getting sound just by selecting the IEC958 option in the sound properties window instead of Autodetect or Alsa, but I guess that wasn't enough to get Amarok or my system sounds on board?  Oh well..works now. Thanks.

---

