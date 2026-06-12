---
title: "i want to use global key for play/pause on nvlc   any ideas how to do this?"
date: 2012-06-14
forum: Multimedia Software
---

### Post by shantiq on 2012-06-14
i play music files in nvlc often this way


[ATTACH]219673[/ATTACH]



now what i want to do is to be able to minimize the terminal window


and    from a key like F1 or F4         activate pause and play   



i have this set up for Deadbeef and Xmms   but fail to understand how to do this with nvlc



nvlc --help    show this

> --global-key-play-pause <string>      Play/Pause
                   --key-play-pause <string>                     Play/Pause



i do not understand how to do this


with Deadbeef and Xmms    i use ccsm      with a command and a key binding   but fail to see how to control nvlc in the same way


i do not think that the fact that it is command line should be the reason since i do not manage it either with vlc



so how does one use these


> --global-key-play-pause <string>      Play/Pause
                   --key-play-pause <string>                     Play/Pause




```
nvlc --global-key-play-pause <string>

```

what do i put in string  the key i want to use to pause and play    ?    


i am stumped here   :KS   [ATTACH]219674[/ATTACH]   Please   a little help needed....

---

### Post by mc4man on 2012-06-14
Global hotkeys in vlc can be a bit tricky at times but they will be used by nvlc

As far as setting, - 
some single keys will not work, some will. Generally not the greatest idea to use a single key
As far a using a single FX key probably F5 would work, shouldn't cause any issue elsewhere though didn't test fully

Just set in global hotkeys as in screen

It will override the existing vlc hotkey of F5 but likely you don't use

---

### Post by shantiq on 2012-06-14
well hi Mc4man 

so no need for ccsm with [n]vlc     


excellent..   as you rightly point out single keys maybe not that good an idea... with vlc     so picked Shift+Home       since already got Home for Deadbeef...


thanx


ps  hotkeys make life so much more simple :::]]] once worked out......

---

### Post by mc4man on 2012-06-14
Ot - 
been trying the latest RubyRipper 0.7+ which has some underthe hood advances & interesting enough now supports neroAacEnc natively - 
(0.7 can't be installed, just run though have worked out a couple of methods to add to unity launcher or launcher icon quicklist

---

