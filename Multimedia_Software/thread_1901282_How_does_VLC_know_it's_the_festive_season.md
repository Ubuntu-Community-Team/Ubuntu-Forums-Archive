---
title: "How does VLC know it's the festive season?"
date: 2011-12-28
forum: Multimedia Software
---

### Post by Handssolow on 2011-12-28
I happen to open VLC Media Player and see the normal orange and white stripped traffic cone has a red hat on top. How does VLC know it's the festive season? By what pathway has this modification appeared?

---

### Post by haqking on 2011-12-28
its an easter egg been there for a few years.

as for how it knows, you realise you have a system clock right ? ;-) either that or it is updates from vlan at this time of year. I remember a couple of years ago people complaining about it, but it is just a hat.

---

### Post by andrew.46 on 2011-12-28
I have not tracked down all instances but an example is in modules/gui/qt4/main_interface.cpp:

```

[B][COLOR="Red"]    if( QDate::currentDate().dayOfYear() >= 354 )
        iconVLC =  QIcon( ":/logo/vlc128-christmas.png" );[/COLOR][/B]
    else
        iconVLC =  QIcon( ":/logo/vlc128.png" );

```

If you grep the source for *christmas.png* and variations the rest of the puzzle should become clearer :).

---

### Post by chrinabuntu on 2011-12-29
Wonder why anyone would complain? I think it's awesome. I LOVE the VLC Christmas hat! It always pleasantly surprises me because I always forget about it til it shows up again. 

;O)

---

