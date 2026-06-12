---
title: "DVI-out on nVidia card"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by tonyr1988 on 2007-08-17
I recently "converted" my desktop into a media center computer. I initially used the S-Video out to go to my TV, and it worked (although there was a small black border around it, and it was awful bright - still, it worked). I just bought a DVI-to-component cable, turned off the computer, unplugged the S-VIdeo, plugged in the DVI cable, and turned it back on. The screen shows nothing until it logs in. Then, it's messed up. I attached a picture of what it looks like. I have the proprietary nvidia drivers loaded. I'm not really sure what else to do - I haven't messed with DVI before. Any tips?

---

### Post by tonyr1988 on 2007-08-18
I tried using nv instead, and it doesn't work either. I get no picture at all.

---

### Post by tseliot on 2007-08-18
Boot with the additional DVI cable unplugged.

then plug in the cable and type:
```
sudo nvidia-settings
```

and set the tv-out from there.

---

### Post by tonyr1988 on 2007-08-18
Okay, I have the settings window up. When I go to "X Server Display Configuration" and click "Detect Displays," it shows two screens: TV-0 and CRT-1. It has TV-0 set to 1024x768 and CRT-1 at (Disabled). I've tried enabling the second one, but it never works - I'll change it, click Apply, log out, log back in, look at the settings again, and they'll be back to the original. I'm really not sure where to go from here.

---

### Post by tonyr1988 on 2007-08-18
Oops - I was saving the settings the wrong way (there was a dialog box telling me that, but I couldn't read it because I was using my S-Video, which made it really bright and small). Anyways, I've got DVI up and running, but it's still not right.

1) Everything is pinker than it should be. I attached a screenshot. Is this a simple config problem? I didn't see anything in nvidia-settings, and I'm not too familiar with xorg.conf

2) Even weirder: When I select "Watch TV" from the MythTV menu, it cuts out completely. it's as if I just pulled the plug from the computer. When I Ctrl+Alt+Bksp, it goes back to the "normal" (pink) login screen. I know Myth works fine (it did using S-Video and VGA), so I'm assuming it's with DVI. Any ideas?

Thanks a lot for your help so far.

---

### Post by tseliot on 2007-08-18
> **tonyr1988 said:**
> 1) Everything is pinker than it should be. I attached a screenshot. Is this a simple config problem? I didn't see anything in nvidia-settings, and I'm not too familiar with xorg.conf
Use the "X Server Color Correction" section in nvidia-settings (only as regards the TV screen)

> **tonyr1988 said:**
> 2) Even weirder: When I select "Watch TV" from the MythTV menu, it cuts out completely. it's as if I just pulled the plug from the computer. When I Ctrl+Alt+Bksp, it goes back to the "normal" (pink) login screen. I know Myth works fine (it did using S-Video and VGA), so I'm assuming it's with DVI. Any ideas?
I'm not sure I understood what happened.

1) If you select "Watch TV" from the MythTV menu (from the TV screen) which display goes back to the login? Both?

2) Please tell me what happens on both screens

---

### Post by tonyr1988 on 2007-08-18
I'm away from that computer now, but I'll be able to try it within the next hour or so.

> **tseliot said:**
> Use the "X Server Color Correction" section in nvidia-settings (only as regards the TV screen)

Thanks - I was hoping it was something simple.

> **tseliot said:**
> I'm not sure I understood what happened.

1) If you select "Watch TV" from the MythTV menu (from the TV screen) which display goes back to the login? Both?

2) Please tell me what happens on both screens

1) The TV. It doesn't actually go back to the login though - it just cuts off all the video output. I have to Ctrl+Alt+Bksp, and it goes back to login.

2) The TV (DVI) is the only screen I've got set up. It's the only way I could get it to work. Whenever I had 2 screens set up, the DVI one was so insanely messed up, it's indescribable (it would only flicker the screen every 2 seconds, and it was only a small chunk of it, and it was zoomed in, and the color was off). Whenever I disabled my other screen, unplugged everything other than DVI, and rebooted, it worked relatively fine.

---

### Post by tonyr1988 on 2007-08-18
Well, now the DVI cable isn't working at all. I turned on my computer today (I didn't make any changes to anything), and the TV just displays a "NOT AVAILABLE." I know the computer's working, because I can hear the login audio. The video just doesn't work at all.

Whew - I can't believe that a video cable is this hard.

---

### Post by tonyr1988 on 2007-08-18
Also, on a slightly off-topic note, I'm thinking about doing VGA-to-component if I can't get DVI to work.

1) Should that be easier to use? My old monitor hooked up via VGA, and it was plug and play, but I assumed this would be too. :P

2) I've seen VGA, SVGA, and Premium VGA. Is there a difference.

3) I've seen this description on most VGA-to-component cables:

> NOTE: Your display system must support component video (Y, Pr, Pb) signal output function in order for the image to display properly. Please consult with your VGA card's user manual for more information.

Should I have to worry about that with my card?

---

