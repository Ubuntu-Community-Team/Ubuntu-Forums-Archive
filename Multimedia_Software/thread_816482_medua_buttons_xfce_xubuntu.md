---
title: "medua buttons xfce xubuntu"
date: 2008-06-02
forum: Multimedia Software
---

### Post by sephirothsigep on 2008-06-02
I have a laptop that has three media buttons volume up,volume down, and mute. I am running xUbuntu and would like to know how i can get these buttons to work. they work under Ubuntu. 

Another note my screen bright and dim buttons work. but not my sound buttons 


any help would be nice.

---

### Post by sephirothsigep on 2008-06-02
After Some more looking around i found this link with a little more help but this did not work for me but odds are it will work for most. 

[https://help.ubuntu.com/community/XfceMultimediaKeys](https://help.ubuntu.com/community/XfceMultimediaKeys)

also if anyone want to try to figure out what i got going on here is the output from xev
> RaiseVolume pressed 
-----------------------------
KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   32  0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   32  0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  



LowerVolume pressed 
-----------------------------
KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  4294967176 0   0   0   0   0   0   0   0   0   0   0   32  0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 28, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 28, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   32  0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


Mute pressed 
-----------------------------
KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   32  0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 28, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 28, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   32  0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  


---

### Post by redseventyseven on 2008-06-16
I am having the same problem re: the Volume Up/Down/Mute keys, using an Emprex 9019 RF Wireless keyboard.

---

### Post by redseventyseven on 2008-06-16
update.

I've noticed a similar, but controllable, behaviour with my Previous and Next buttons.

In my setup, these buttons are not assigned to anything in the Xfce Keyboard Shortcuts dialog. When I run xev, pressing the "Previous" button produces a KeyPress and KeyRelease event as expected.

However, when I open Rhythmbox, these buttons work as they should (i.e. they skip to the previous and next tracks), even though I haven't actually set them up that way in Keyboard Settings! Upon further inspection, xev shows that they produce FocusOut and FocusIn events in exactly the same way as my volume buttons do. If I quit Rhythmbox, they revert to producing KeyPress and KeyRelease events as before.

So, it appears as though another process is briefly preventing X from seeing the keypress, processing it itself, and then giving control back to X afterwards. Rhythmbox appears to do this for the Previous and Next buttons. I wouldn't know where to begin looking for what's doing this to the volume buttons.

---

### Post by redseventyseven on 2008-06-17
I think I'm getting somewhere!

For reference, see this Gentoo howto: [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

Originally I had used this tutorial to produce the file **~/.Xmodmap** which contained a list of keysyms (see section 3 of the above howto). This is how my Xmodmap file looked before:

```
! Xmodmap file for UK Emprex 9019 RF keyboard

keycode 178 = XF86HomePage
keycode 230 = XF86Favorites
keycode 229 = XF86Search
keycode 236 = XF86WWW

keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute
keycode 144 = XF86AudioPrev
keycode 179 = XF86AudioPlay
keycode 110 = XF86AudioPause
keycode 153 = XF86AudioNext
keycode 164 = XF86AudioStop

keycode 223 = XF86PowerOff
```

After doing this, and restarting X, the volume up and down buttons stop being recognised by xev as KeyPress and KeyRelease events (as described before). Something else is grabbing their attention away from X. However, I noticed that when I logged in as a different user, for whom no .Xmodmap file had been set up, the buttons produced KeyPress and KeyRelease events again.

Anyway, here's my suggested solution (which might or might not work):

1. See if you have an **.Xmodmap** file somewhere. I created mine myself (as my keyboard wasn't automatically recognised) following the howto I mentioned earlier, so it was in my $HOME directory. If your keyboard was automatically detected, the .Xmodmap file might be somewhere else. If someone could shed some light on this it'd be helpful!

2. Save a backup copy!

3. Change the keysyms (the codes that start with XF86 that describe the buttons) to something else. A list of valid keysym codes for your own system can be found in the file **/usr/share/X11/XKeysymDB** (on Xubuntu - other distros may vary, see section 3 of the howto for alternative locations). I changed all the audio codes to non-sensical codes which I guessed would have very little chance of being grabbed by other applications:

```
! Xmodmap file for UK Emprex 9019 RF keyboard

keycode 178 = XF86Phone
keycode 230 = XF86Support
keycode 229 = XF86Search
keycode 236 = XF86WWW

keycode 174 = XF86Book
keycode 176 = XF86Calculator
keycode 160 = XF86DOS
keycode 144 = XF86Market
keycode 179 = XF86Finance
keycode 110 = XF86Shop
keycode 153 = XF86Meeting
keycode 164 = XF86Community

keycode 223 = XF86PowerOff
```

4. Restart X.

5. Assign your keyboard shortcuts using **Settings > Settings Manager > Keyboard** as usual. If all is well, your new (non-sensical) keycodes should appear when you assign your shortcuts.

Hope this helps someone! Please add to this if your system works a different way.

---

