---
title: "Digital output broken :("
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by Jabone on 2007-02-12
I just installed my ubuntu from scratch and broke my digital output somehow. I had to install again couse i couldn't get it solved. 

Now I know when it broke digital output:

I used Xine to play movie with ac-3 sounds. Then i tried to load external subtitles and xine got stuck. After this I had to force xine to shutdown and the sound were gone from my amplifier. Reboot doesn't help. 

Strange is that I can still use analog output to my headphones, only digital output doesn't work.

My soundcard uses emu10k1 module if that helps. 

Any solutions? 

Jabone

---

### Post by firefreak on 2007-04-07
> **Jabone said:**
> I just installed my ubuntu from scratch and broke my digital output somehow. I had to install again couse i couldn't get it solved. 

Now I know when it broke digital output:

I used Xine to play movie with ac-3 sounds. Then i tried to load external subtitles and xine got stuck. After this I had to force xine to shutdown and the sound were gone from my amplifier. Reboot doesn't help. 

Strange is that I can still use analog output to my headphones, only digital output doesn't work.

My soundcard uses emu10k1 module if that helps. 

Any solutions? 

Jabone

Exact same problem with yesterdays release of Kubuntu Feisty. Everything was working just fine a minute ago. Forced a shutdown of VLC playing back AC-3 sound. No I have no sound on my digital output. Analog still works though...

Heeeeeeeeeeeeeeeeeeeelp !

---

### Post by larasoft on 2007-04-26
Hey,

I got the same problem.

Played a DVD wit xine-ui and ac3 and now only ac3 sound works.

No stereo (e.g. amarok, system sounds).

My Soundcard: Intel Onboard (snd-intel8x0)

---

### Post by larasoft on 2007-04-27
I have posted a bug.

[http://sourceforge.net/tracker/index.php?func=detail&aid=1708595&group_id=9655&atid=109655](http://sourceforge.net/tracker/index.php?func=detail&aid=1708595&group_id=9655&atid=109655)

---

### Post by larasoft on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/25632](https://bugs.launchpad.net/ubuntu/+bug/25632) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recoverd my system from a backup and sound works fine again.

But if someone got this problem and have no backup try the following:

[https://bugs.launchpad.net/ubuntu/+bug/25632]("https://bugs.launchpad.net/ubuntu/+bug/25632")

> 
 Bernard van der Velden said on 2006-05-30: (permalink)

I managed to find a workaround:

- I uninstalled ld10k1 and qlo10k1
- sudo mv /etc/init.d/alsa-utils /etc/init.d/alsa-utils.GONE
- shutdown and turn on the PC
*** the default values for alsa should be loaded now ***
- sudo mv /etc/init.d/alsa-utils.GONE /etc/init.d/alsa-utils
- use your mixer to restore your volume

The digital out produces PCM output again. It would be nice if alsa could detect it when the DSP of the emu10k1 gets screwed-up.


---

