---
title: "Gnome mplayer Freeze randomly"
date: 2010-03-19
forum: Multimedia Software
---

### Post by margemoosh on 2010-03-19
I use Gnome mplayer but it freeze random when playing videos and just show a black screen without sound and if i simply press backward or forward button to send it 10 sec forward or backward it will continue to play video until it freeze again.
sometimes it takes seconds to freeze and sometimes half an hour or more.

---

### Post by andrew.46 on 2010-04-14
Hi margemoosh,

This sounds a little like an odd problem that has occurred with Karmic and the MPlayer audio out setting. I am not very familiar with the GNOME MPlayer but you could try SMPLayer:
```

sudo apt-get smplayer
```

and if the problem persists change the audio out device to *pulse*. In SMPlayer this setting can be found:

Options --> Preferences --> General --> Audio --> Output Driver

All the best,

Andrew

---

### Post by margemoosh on 2010-04-28
> **andrew.46 said:**
> Hi margemoosh,

This sounds a little like an odd problem that has occurred with Karmic and the MPlayer audio out setting. I am not very familiar with the GNOME MPlayer but you could try SMPLayer:
```

sudo apt-get smplayer
```and if the problem persists change the audio out device to *pulse*. In SMPlayer this setting can be found:

Options --> Preferences --> General --> Audio --> Output Driver

All the best,

Andrew

thanks smplayer works fine but i can't configure my laptop(HP Pavilion dv6000) quick lanch buttons for play/pause on smplayer, quick launch buttons works fine with gnome mplayer.

---

### Post by no2498 on 2010-04-28
just by installing smplayer should fix mplayer 
along with yesterdays update

---

