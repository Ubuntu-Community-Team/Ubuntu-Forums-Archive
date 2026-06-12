---
title: "Realplayer browser plugin after upgrade to Edgy"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by dolphinholmer on 2006-10-27
After upgrading to Edgy I discovered that I could no longer play videos from the bbc website. Clicking on Video links opened a new window in which literally nothing happened. I eventually found a new arrival in /usr/lib/firefox/plugins ,namely libtotem-complex-plugin-so and deleted it.(I would have uninstalled the Totem-Mozilla plugin but this apparently would have meant the uninstallation of the ubuntu-desktop package!) I then deleted mplayerplug-in-rm-so (mplayer plugin is crap at playing realplayer video) and this way got the realplayer plugin to play the desired video. Only the video is unwatchable as it constantly flashes green! ugh! It was fine before the upgrade. Any Ideas? Thanks.

---

### Post by chippy99 on 2006-10-27
There is a new version of Automatix that supports edgy. You could try downloading that from [here]("http://www.getautomatix.com/wiki/index.php?title=Automatix2_for_(K%2CX)Ubuntu_6.10_i386")

---

### Post by srt4play on 2006-10-27
The uninstallation of ubuntu-desktop is not a problem and it can safely be removed since it is just a meta-package.

I agree with you that using the mplayer plugin for real content results in well, crap. 

What I usually do for realplayer is download and install it from real.com.  Then delete the plugins in /usr/lib/firefox/plugins that have 'rm' in their names. Then go to a site that has real content and when firefox asks what to do with it, point it to /usr/bin/realplay and tell it to open with that every time.

That is just personal preference though and it's what works best for me.

---

### Post by dolphinholmer on 2006-10-27
That's pretty much what i've done too, srt4play, except that you need the plugin for certain real content, as not all will play in the standalone player. I just can't understand the sudden poor quality playback when it was fine before the upgrade. It's like every third frame is just a green screen.

What can the latest Automatix do to help chippy?

---

### Post by srt4play on 2006-10-27
Is it all videos on the bbc site or just certain ones? 

I'd like to test it when I get home today to see if I get the flashing green problem too.

---

### Post by dolphinholmer on 2006-10-27
i've just discovered that the weather forecast is ok (playback of it that is!) the buferring strip at the bottom flashes but that's all. This is the only video I've found that plays back ok. The others all flash green.

---

### Post by Argos_Bling on 2006-12-05
Finally tracked this down - I had exactly the same problem with green flashes, until I fired up the standalone RealPlayer application (Kmenu>Multimedia>RealPlayer), and went to Preferences>Hardware and removed the tick from "use XVideo". No more green flashes on BBC Real content!

---

