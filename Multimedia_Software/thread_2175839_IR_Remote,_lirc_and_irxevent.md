---
title: "IR Remote, lirc and irxevent"
date: 2013-09-21
forum: Multimedia Software
---

### Post by CJfbQdF on 2013-09-21
Hello,

I tried to use my Apple remote on 13.04 (64bit) having installed lirc, lirc-x, inputlirc, xautomation and so on but unfortunately it doesn't work:

irw shows that the remote works and that the signals are received (I used the macmini profile): 
```
0000000087ee810b 00 KEY_VOLUMEUP Apple_A1156
[and so on]
```

but even the simplest lircrc code doesn't show any reaction of irxevent (example just for illustration):
```
begin         
prog = irxevent         
button = VOLUMEUP         
config = Key F5 CurrentWindow 
end
```

and when I try
```
begin
prog = irxevent
button = VOLUMEUP
config = xte 'key XF86AudioPlay'
end
```

there's a syntax error message by irxevent.

Does anyone have an idea where the error may be?

What I would like to achieve is to map the following IR remote keys to the Hotkeys (as on the Mac keyboard):

VOLUMEUP = XF86AudioRaiseVolume (F12 Mac keyboard), VOLUMEDOWN = XF86AudioLowerVolume (F11), FORWARD = XF86AudioNext (F9), REWIND = XF86AudioPrev (F7), PLAYPAUSE = XF86AudioPlay (F8)

Many thanks

---

