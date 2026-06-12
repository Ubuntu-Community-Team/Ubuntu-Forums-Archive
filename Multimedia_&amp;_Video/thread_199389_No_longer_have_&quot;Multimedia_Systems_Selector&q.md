---
title: "No longer have &quot;Multimedia Systems Selector&quot; in System/Preferences"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by iambrian on 2006-06-18
I'm a reasonably newbie so not sure where to look for helpful logs etc for this.

I have 6.06 Ubunto with the KDE installed  (through aptitude not Kubuntu). I had a Geoforce MX440 card and an old WinTV card working together so TVTime worked AOK from an external TV tuner through composite in. Wanted to upgrade to a card that supported S-Video rather than just composite in so installed an old 3DFX Vivo graphics card. Managed to get the card to work AOK for X but could not set up multimedia - so played with settings in "Multimedia Systems Selector"

Today found a TV card (Avermedia not sure of model) with s-video in. So added it and now I have no "Multimedia Systems Selector" in my System Preferences (actually I suspect it was gone before I added the card - my playing around trying configs last session must have screwed something)

Have put the MX440 back (restoring old Xorg.conf) but don't know how to config multimedia anymore to see if the Avermedia card is gonna work.

Any idea how to restore "Multimedia Systems Selector" to System/Preferences?

Thanks Brian

---

### Post by Bd0g on 2006-06-18
Hmm.. /Bd0g strikes comment. (wasn't helpful in this case, unfortunatly..)

---

### Post by wgandhi on 2006-06-18
Same thing happened to me..Dont know why I lost the Multimedia System Selector.

However, if I type gstreamer-properties at the command prompt I get a similar looking dialog.

Hope this helps:)

---

### Post by Turin Turambar on 2006-06-18
Go to Applications/Accessories/Alcarte Menu editor. Then just select "Multimedia SS" in Preferences and it should be ok.

---

