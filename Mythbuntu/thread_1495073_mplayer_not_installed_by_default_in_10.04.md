---
title: "mplayer not installed by default in 10.04?"
date: 2010-05-27
forum: Mythbuntu
---

### Post by SMANN on 2010-05-27
Just did a clean install of Mythbuntu 10.04-amd64 on my separate frontend and backend machines.  For whatever reason, even though the majority of file types in the Videos interface are configured to use it by default, mplayer is not installed by default.  After I installed it manually videos now play as expected.  What gives?

---

### Post by Cavsfan on 2010-05-27
I was involved in testing Lucid and jumped in around beta, but mplayer came installed default on mine. 
Not familiar with Mythbuntu though...

---

### Post by tgm4883 on 2010-05-27
I don't believe mplayer is installed by default as it is an external player.

---

### Post by SMANN on 2010-05-27
Is the default player for files such as .avi and .mp4 not mplayer in 10.04?    I did do a db import from a 8.04 install and am not sure atm if that overwrote the associated player.  I had to look at the log to see that mythfrontend was attempting to open a nonexistent mplayer to play all my downloaded videos.

---

### Post by tgm4883 on 2010-05-27
mplayer was never the default in Mythbuntu. A db import would keep whatever setting you had in that db.

---

### Post by superm1 on 2010-05-27
> **tgm4883 said:**
> mplayer was never the default in Mythbuntu. A db import would keep whatever setting you had in that db.

I think mplayer might have been the default in a much earlier iteration.  But indeed, a db import is the root cause here.  Now upstream (and Mythbuntu) default to Internal.

---

### Post by Cavsfan on 2010-05-28
> **tgm4883 said:**
> I don't believe mplayer is installed by default as it is an external player.

Maybe I did install it myself. Is there any other option? 
Did Lucid come with another program default that could read AVIs. etc?

---

### Post by tgm4883 on 2010-05-28
> **Cavsfan said:**
> Maybe I did install it myself. Is there any other option? 
Did Lucid come with another program default that could read AVIs. etc?

Yea, it's called 'Internal'

---

### Post by Cavsfan on 2010-05-28
> **tgm4883 said:**
> Yea, it's called 'Internal'

Where do I find this infernal, er I mean internal application?

---

### Post by tgm4883 on 2010-05-28
> **Cavsfan said:**
> Where do I find this infernal, er I mean internal application?

[http://www.mythtv.org/wiki/Internal_player](http://www.mythtv.org/wiki/Internal_player)

---

### Post by brian_hammerhead on 2010-05-29
[FONT=Verdana]For what it is worth, I just installed a fresh 10.04.  The Internal player had some problems playing certain .avi files correctly.

  I have a bunch of old .avi files that contain home movies captured from my Powershot G3.  They are low resolution (320 x 240), but that is all that I had back in 2003 when I videoed my kids learning to ski and their birthday parties.  The Internal player would not play these files at all.[/FONT] [FONT=Verdana]

  I also have some other higher resolution home videos that played, but the video and audio would get out of sync when the video displayed still images for a set length of time.[/FONT] [FONT=Verdana]

  In the end, all was fixed by using mplayer.  [/FONT] [FONT=Verdana]


 Utilities/Setup > Setup > Media Settings > Video Settings > Player Settings[/FONT]  [FONT=Verdana]

Default Player:   [/FONT]  [FONT=Verdana]mplayer -fs -zoom -ontop -ao alsa -vf pp=lb -vo vdpau


The "-vf pp=lb" option specifies "linear blend deinterlacing" which really helped my home videos look better.[/FONT]  [FONT=Verdana]

The "-vo vdpau" can be used if you video card supports this feature.  If not, try not including a -vo option, or try "-vo sv"[/FONT] [FONT=Verdana]

By the way, I could never get this to work by specifying this command as the setting for only .avi files.  I had to set the default player as above and then set make sure the .avi file type was set to use the "default" player rather than the Internal player (which I believe is the default setting).

[/FONT][FONT=Verdana]
  Utilities/Setup > Setup > Media Settings > Video Settings > File Types

Scroll to avi

Leave the command blank.

Use default player: CHECKED


  I hope that this helps someone else out.
[/FONT]

---

