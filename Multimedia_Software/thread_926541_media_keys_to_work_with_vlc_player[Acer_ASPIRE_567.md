---
title: "media keys to work with vlc player?[Acer ASPIRE 5672WLMi]"
date: 2008-09-22
forum: Multimedia Software
---

### Post by macvr on 2008-09-22
hi, 

1>i'm trying to make my laptop's[Acer ASPIRE 5672WLMi] media keys work with vlc player...

the media keys work with rhythm box[all except the previous key , which works only randomly, i dont know y?] and Totem... 

the hot key settings in vlc player are set as in pic>
i'm not sure how ELSE to set it up!!!

the[COLOR="Red"] xev [/COLOR]output is as below:
volume up>
```

FocusOut event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```  
volume down> 
```

FocusOut event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```   
play/pause>
```

FocusOut event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```   
stop>
```

FocusOut event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```  
next>
```
FocusOut event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   1   0   0   0   0   0   0   0   0   0   0   0   0   0   


```
previous>[this is the key which works randomly with rhythomBox]
```
FocusOut event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   1   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 31, synthetic NO, window 0x2a00001,
    root 0x87, subw 0x2a00002, time 201106835, (34,58), root:(717,92),
    state 0x0, keycode 144 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

2> can we get vlc 0.9.2 for ubuntu[the version which is available for windows it has a nice interface]

3> i would also like to know how to make the previous key work for rhythm box

---

### Post by macvr on 2008-09-22
bump

---

### Post by e-dard on 2008-09-24
Am afraid that I am not here to help, but to join in the fun of trying to work out why the multimedia buttons don't have keycodes!

I have the apple slim keyboard and the buttons work fine for rhythmbox etc, but I only get the same KeymapNotify events like you do when I use xev to try and find the keycodes.  I need the keycodes to map the multimedia keys to other scripts I want to run. 

I suspect if you could assign keycodes to your multimedia keys rather than the weird situation of having keys with no keycodes your problem would be solvable...


Edit-- I just looked at your screenshot, I suspect that the button vlc calls "media stop" is probably the button with KeySym "XF86AudioStop" or something similar.  However, if that symbol is not mapped to a keycode it will need to be.  Of course, since you can't get at the keycodes of your multimedia keys you can't do that.
e-dard

---

### Post by macvr on 2008-09-28
> **e-dard said:**
>   Of course, since you can't get at the keycodes of your multimedia keys you can't do that.
e-dard

so it is not possible to use media keys with vlc player

if so ... atleast how do i make my previous media key to work constantly?

---

### Post by macvr on 2008-09-30
bump?

---

### Post by macvr on 2008-10-15
bump

---

### Post by ckempo on 2008-11-04
> **e-dard said:**
> Am afraid that I am not here to help, but to join in the fun of trying to work out why the multimedia buttons don't have keycodes!

Me too, but [this looks interesting]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/198786")... am going to try it when I get home.

---

### Post by macvr on 2008-11-06
i tried >
sudo modprobe acerhk force_series=6000

i now dont have functionning of any of the hotkeys...[only the volume hkeys work]

it was either the command or the upgrade to 8.10 that killed the keys!

[COLOR="DarkRed"]how do i reverse the command?[/COLOR]

---

### Post by Bln on 2011-03-27
[LIST=1]
[*]Unset the keys you want to use in *System > Preferences > Keyboard Shortcuts*
[*]Open VLC, and set keys to "Global" field in VLC menu *Tools > Preferences > Hotkeys*
[*]**[COLOR=Red]Restart VLC.[/COLOR]**
[/LIST]
That worked for me.

---

### Post by sillyxone on 2011-08-08
> **Bln said:**
> [LIST=1]
[*]Unset the keys you want to use in *System > Preferences > Keyboard Shortcuts*
[*]Open VLC, and set keys to "Global" field in VLC menu *Tools > Preferences > Hotkeys*
[*]**[COLOR=Red]Restart VLC.[/COLOR]**
[/LIST]
That worked for me.

worked for me too (10.10, Dell E6420)

thanks

---

### Post by richcocoa on 2012-02-23
> **Bln said:**
> [LIST=1]
[*]Unset the keys you want to use in *System > Preferences > Keyboard Shortcuts*
[*]Open VLC, and set keys to "Global" field in VLC menu *Tools > Preferences > Hotkeys*
[*]**[COLOR=Red]Restart VLC.[/COLOR]**
[/LIST]
That worked for me.

Works for me too. Thumbs up

---

