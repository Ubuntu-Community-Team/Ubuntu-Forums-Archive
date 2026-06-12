---
title: "Channels restricted to current mux"
date: 2011-10-29
forum: Mythbuntu
---

### Post by fezsteve on 2011-10-29
Hi,


I've installed mythbuntu latest version with all updates. I have 2x haugpauge dvb-s cards.

When one of the cards is recording something, it isn't possible to watch live tv from any channel outsides of the current mux, even if i select the other tuner as the souce.

Can anyone help me?

Cheers
Steve

---

### Post by mvmatch on 2011-10-29
I'm seeing a similar problem and more. I'm running 2 HDHR's and I cannot change channels out of the current MUX. Additionally about half the channels show extreme distortion in both recordings and in live TV. It's not the HDHR's because they worked perfectly befor upgrading to 11.10 and they display perfectly using the HDHR GUI tool.

---

### Post by mvmatch on 2011-10-29
OK, I found the answers to both problems.

fezsteve, start mythfrontend and go to Setup, then Recording Groups. On page 5/8 there is a box to tick called "Save current group filter when changed". That did it for me. Now I'm not restricted to one MUX when I try to change channels.

On my other problem, I was seeing extreme pixilation and pink & green stripes on any HD source. The cure was to set the current profile to VDPAU.

Now life is good again, and my wife has decided not to leave me. :P

---

### Post by krisbee2000 on 2011-11-01
Always remember for any digital tv, to allow multirec so you can watch any of the subchannels on the same card (I allow 2 per card) and this is setup in mythbackend.
 
As for live tv, there is a priority/livetv setting in mythFRONTend that allows the cards to be reordered by the frontend, and to always use the LAST card for livetv (opposed to the recording by the backend which always prefers the FIRST card).  At work right now, so I can't tell you exactl what it says, but you will find it!
 
That did the trick for me, and really it always should be the default (and not sure why it isn't).

---

