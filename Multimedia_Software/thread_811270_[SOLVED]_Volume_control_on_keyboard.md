---
title: "[SOLVED] Volume control on keyboard"
date: 2008-05-29
forum: Multimedia Software
---

### Post by willthebold on 2008-05-29
Hey all, I have a volume knob on my keyboard that used to control the master volume, but since I've been messing around with Ardour and installing Jack and whatnot, it's stopped working right. The icon still pops up like it's adjusting the volume but nothing actually happens to the volume. Where are the settings to mess with this kind of stuff? I can't seem to figure it out. Thanks.

---

### Post by ndrone1 on 2008-06-11
> **willthebold said:**
> Hey all, I have a volume knob on my keyboard that used to control the master volume, but since I've been messing around with Ardour and installing Jack and whatnot, it's stopped working right. The icon still pops up like it's adjusting the volume but nothing actually happens to the volume. Where are the settings to mess with this kind of stuff? I can't seem to figure it out. Thanks.

I could also really use this information. I'm searching and not finding much. If I find anything, though, I'll let you know. In the meantime, can someone please help us out? Thanks.

...wait, this is SOLVED? How? There's no solution! Help! lol..

---

### Post by ingrid_ozikem on 2008-06-11
Yeah, I have this problem too sometimes.. I don't know how to solve it quite yet but I think it is related to having two different sound drivers on your system -- ALSA and OSS. I think the keyboard is set up to change the volume in one of them and if your program is using the other, well, there is no effect.

Try running alsa-mixer in a terminal and then using the keyboard to see if it changes the volume in that.. it does for me (a Dell XPS M140 system).

---

### Post by markbuntu on 2008-06-11
Jack can cause all sorts of trouble with your other sound users. Change the System/Preferences/Sound to alsa or pulseaudio instead of automatic and make sure the jack driver is set to the same. ALso, when you are done with the app that uses jack make sure jack is killed. You can do this with jack control.

Realistically, you dont want to use pulseaudio when using jack as it adds another layer of control and increases latency. So, set everything to use alsa and your alsa default sound to your sound card.

You could also read the guides in the Multimedia and Video forum or do a forum search for jack and find out just how much trouble you can make for yourself fooling around with jack.

---

### Post by ndrone1 on 2008-06-11
Well this solution works half-way for me. What I mean is that I can now use the keyboard glow buttons to change the volume, etc... 
What does NOT work however is the full range of volume. I have only 50-100% volume adjustment. Below 50%, it's silent... meaning I lose half the range. Still working on repairing that. In the meantime, the workaround I used for the Dell XPS M1330 is:

Open System>Preferences>Sound
Under "Default Mixer Tracks," I selected both Master and Front by holding down the control key. This allows the buttons to work on the keyboard, but as I said, not fully. I only get half the range I usually would... 

Anybody have any help on that issue?

---

### Post by HyperHacker on 2008-06-11
I have a similar problem; my keyboard has volume control buttons, but the Up button doesn't respond, and the Down button is slow (it takes about a second to respond, and if I press it 3 times quickly, it still only moves one notch). The adjustment is also quite a bit less precise than I'd like it to be. It's a Compaq SK-2800C keyboard.
If there were some way to assign commands to those other useless buttons like Internet, Shop, etc that'd be nice too. Programs like CompizConfig don't respond to most of them, and the ones that do are wrong (i.e. Search is "Calculator"); Windows actually had that problem too (needs drivers?), but the volume buttons worked.

---

### Post by Unix_Slayer on 2008-06-11
System Settings - / - Keyboard & Mouse - / - Keyboard shortcuts

You can fix it in there. Mine works fine.

---

### Post by matyasfalvi on 2008-09-26
Hi I had the same problem in my case the error was resolved by doing the following:

Go to: System > Preferences > Sound

Make sure your sound settings are as on the picture attached!

And make sure that at Default Mixer Tracks > [COLOR="Red"]Master[/COLOR] is highlighted.

---

