---
title: "Can't play audio cd with movie player"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by new2linux411 on 2006-08-15
Hello, i was wondering if anyone knew why I'm unable to play audio cd's with the movie player? When I insert a cd, sound juicer starts by default and works ok. I close sound juicer and open movie player, cuz I would prefer to use that if I could. When I click the movie tab to view the drop down contents, the option to play an audio disc is there, but unable to select. Does this mean that the movie player doesn't recognize my cd-rom? If so, how can I get it to? I'm using Dapper, I installed Breezy a while back for a short period of time, and I thought I could play cd's with Totem.(isn't totem the same as the movie player?) If anyone could help me out with this it would be much appreciated. I can play mp3's and ogg files, just no audio discs. Thanks for any help resolving this.

---

### Post by IdoMcFly on 2006-08-16
same problem here: the entry is avalaible but greyed out any solution?
found out another thread with same problem: [http://www.ubuntuforums.org/showthread.php?t=191200&highlight=cdda+valid+URL](http://www.ubuntuforums.org/showthread.php?t=191200&highlight=cdda+valid+URL)

---

### Post by Echo35 on 2006-08-16
apt-get gstreamer0.8-cdio

I downloaded it in Synaptic along with a bunch load of other gstreamer plugins and it works great. Yes, Totem is the same thing as movie player, but it isn't Totem's fault. Totem (by default) uses gstreamer, so as long as gstreamer has support for certain audio/video fromats, Totem will too.

---

### Post by new2linux411 on 2006-08-17
Thanks to everyone for chipping in regarding this, but that plug-in alone didn't do the trick. I installed gstreamer0.8-cdio using Snaptic, then tried to play a cd, still greyed out the option. Tried rebooting, still can't play it. Anymore ideas, maybe more gstreamer plug-ins? Thanks

---

### Post by Echo35 on 2006-08-17
Hmm. I just took a look at mine and realized I can't either. That's kind of odd. I usually just use Ryhtymbox or the default CD Player. I'll have to look more into this.

---

### Post by new2linux411 on 2006-08-17
Also I noticed, which is strange I might add, is that if there is no disc in the drive it gives you the option to play a cd. In my particulat case it says  play disc cd-rw drive. When a cd is inserted it greys out the option, so I guess that tells me it's not an issue with the movie player not recognizing my cd-rw drive. Kinda stumped with this right now, hopefully we can figure out what the problem is. I remember playing cd's with Totem using Breezy out of the box, I wonder what's the deal??

---

### Post by Echo35 on 2006-08-18
Same thing happens to me, but I can play DVD's just fine, so I know it isn't the drive not being recognised. I'll have to investigate this. ](*,)

---

### Post by dwblas on 2006-08-28
Use one the mixers to check that PCM is not muted and the PCM volume control is not off.

---

### Post by edcrfv on 2006-09-04
Same here. Using Totem/xine.
Rythmbox, SoundJuicer and vlc play cd without any problem while the "play disc" is grayed in Totem
When I launch ```
totem /dev/hdc
``` it plays perfectly.

---

### Post by new2linux411 on 2006-09-05
Thanks again for everyone chipping in, but I'm not exactly sure what this means. I'm still fairly new to ubuntu, and linux in general. To edcrfv, is this code something I need to do from the command line? I've been using Rythmbox for the meantime, which I'm starting to like by the way.. But if this is something easy I can do to get that working in Totem, I will do it. I'm just not clear on what exactly I need to do. Thanks for any assistance.

---

### Post by edcrfv on 2006-09-06
I wouldn't say it's easy nor it's better cause it doesn't show the album and tracks title.

My point was just that if you type **totem /dev/hdc** in a console, totem plays cd's. So totem can do it...

---

### Post by IdoMcFly on 2006-09-12
any news of this problem?

---

