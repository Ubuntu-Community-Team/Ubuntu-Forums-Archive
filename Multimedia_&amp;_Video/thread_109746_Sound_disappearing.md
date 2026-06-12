---
title: "Sound disappearing?"
date: 2005-12-29
forum: Multimedia &amp; Video
---

### Post by _Gumby on 2005-12-29
I dont know if anyone else has come across this problem before, but it seems that my ubuntu install seems to 'lose' its ability to play sound. Upon installation the soundcard (A soundblaster live) is discovered properly and registers on my decoder as sending digital data, but it seems that after a while it will just stop outputting sound, even though the modules are all loaded and there are no crashes to speak of. It just decides not to output sound anymore. A reboot wont fix the issue, but a complete re-install will. I know its not a hardware issue, since it works properly with an old debian sarge distribution that i have here. Running a new kernel doesnt seem to fix it, only a different distribution.

I havent changed any settings in alsamixer or any volume controls other than those in xine. The digital out works perfectly from a fresh install, but then just dies after a while for no apparent reason.

It normally registers with the digital decoder when it loads the hotplug service, so i imagine it could be something to do with the way the modules are loaded? I have looked at the scripts, but cant find anything terribly obvious. Is there anything a fresh install does differently?

Im running Breezy Badger 5.10 with a custom 2.6.12 kernel. All my alsa libraries/tools etc seem to be up to date, or at least apt-get tells me this is so. 

I really have no clue as to why it would be losing sound. As far as i can tell, nothing is changing.

Does anyone have any suggestions of where to start looking?

---

