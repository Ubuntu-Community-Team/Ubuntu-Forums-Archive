---
title: "No sound in Ubuntu 10.04 ..."
date: 2012-02-07
forum: Multimedia Software
---

### Post by syndicate787 on 2012-02-07
so this has been going on for about 3 days now and i have tried everything that ive found on here and im starting to lose hope .. 
im using HP Pavilion ( not sure what model exactly ) and this happened when i was watching a movie online lol and i was using headphones and when i left to get something and came back there was no sound ! i have no idea how this happened ](*,)
i have all volume turned up to the max, and have checked the alsamixer and everything is normal there .. there is no login sound no nothing

---

### Post by malangaman on 2012-02-07
Are you using a laptop? Sounds like your sound card driver might have scrambled or the card died. 
check this helpful link:
[http://lotphelp.com/lotp/the-ubuntu-sound-problem-solution-guide](http://lotphelp.com/lotp/the-ubuntu-sound-problem-solution-guide)

---

### Post by syndicate787 on 2012-02-07
no i have desktop computer and i have already tried that with no luck ... i put the command 
**wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh;](http://www.alsa-project.org/alsa-info.sh;) chmod +x ./alsa-info.sh; ./alsa-info.sh**

and got the info about my computer etc and apparently i have the kernel version 2.6.32-38 
but the alsa driver was 1.0.23 and i upgraded it and it was suppose to bring the sounds back, but it didnt work either
~ BTW i have HP Pavilion 061 
and i tried everything off this page too : h[**ttps://help.ubuntu.com/community/SoundTroubleshootingProcedure**]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

---

