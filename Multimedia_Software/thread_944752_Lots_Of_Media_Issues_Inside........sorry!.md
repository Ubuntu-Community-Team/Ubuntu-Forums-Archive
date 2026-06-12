---
title: "Lots Of Media Issues Inside........sorry!"
date: 2008-10-11
forum: Multimedia Software
---

### Post by Maheriano on 2008-10-11
1. No sound when playing video in Firefox.
2. Video VERY choppy when playing in Firefox.
3. Everything very choppy when using GNOME. I try to move the mouse across the screen or open a menu in an application or play a video in any application and it's always choppy.
4. Is there a guide for getting Dolby Digital working via SPDIF? Do I need special hardware other than the jack and the cable?
5. Is there a list of webcams which will work in Linux?
6. Is there any security software with motion detection and recording that I can run with multiple webcams?
7. When playing music in Audacious, it'll play a few songs fine but then it'll just stop at the end of a random song and not play the next. I have to click >> (next track) and then click > (play) again to get it to start playing again. Happens every 5-10 songs.

Thank you a bunch! Should I make separate threads?

---

### Post by Maheriano on 2008-10-31
Looks like a solved a few of these and am working on the rest.

1. Still working on sound via SPDIF with flash in Firefox.
2. Choppy video fixed, I had to load the drivers for my video card. They wouldn't automatically install because my video card was too old so I picked up a newer one (Vista compatible) off a guy for $20, popped it in and everything installed automatically. After a reboot...and another reboot....it worked great. Could even play videos in Firefox without issue.
3. See above.
4. Still working on this. Proving very difficult.
5. Chucked that webcam and got a new one. Loaded Cheese and it worked automatically.
6. On hold.
7. No idea how to fix this.

---

### Post by Maheriano on 2008-11-07
I got the sound fixed, now I want to test it with a DVD. But when I try and play a DVD in any application it gives me a different error. Which application should I be trying to play DVD in so I can test them?

---

### Post by zero777zero on 2008-11-07
VLC player is fine, make sure you have libcss2 installed

---

### Post by Maheriano on 2008-11-07
Cool, VLC is working....kind of. I can't play copyright media even though they're movies I bought from the store. It opens the player like it's going to work, then it just shrinks down to the controls again without any message. Plus when I do manage to play a DVD that's not protected and the camera pans fast, the video gets blurry until the camera slows down again.

And how do I install libcss2? I couldn't find it in the package list.

---

### Post by mc4man on 2008-11-07
that's libdvdcss2
go here and add repo for your version and then key
After that look in synaptic or ```
sudo apt-get install libdvdcss2
```
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

or go here for latest (works on all ubuntu versions
[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)


edit: medibuntu can prove useful for other packages, particularly on Hardy

---

### Post by Maheriano on 2008-11-07
Cool, thanks. I got it installed and now I can play copyright DVD which is the way it should be...I paid for them. But still when I play them and the camera moves fast, it's blurry.

---

### Post by mc4man on 2008-11-07
You could try changing your video output (module

Open vlc -> tools (in 0.9.x) or settings (in 0.8.x) -> preferences.
Enable advanced options ('show settings' -all in 0.9.x) or click 'advanced options' box in 0.8.6

Expand Video and highlight 'output modules' and  in the drop down on right
Try X11 first ,if no change try gl
It doesn't hurt to go back and try Xv (default, preferred

Make sure you click save between changes

If your running **hardy** doesn't hurt to do the same for audio, move the output module off of 'default' and pick something, alsa is good choice.

The reset button will always return you to defaults if things get 'borked'
As will (or if 'something' breaks down the road
In 0.8.6 - home dir. - delete .vlc
In 0.9.x - home dir. - delete vlc folder in .config

---

### Post by Maheriano on 2008-11-08
Thanks, it's working better now and my roommate can't really notice a difference but I can see it's not as good as my DVD player. If anyone has more suggestions send them along.

---

