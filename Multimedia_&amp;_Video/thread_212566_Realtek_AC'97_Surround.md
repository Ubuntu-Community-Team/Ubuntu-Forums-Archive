---
title: "Realtek AC'97 Surround?"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by grivad on 2006-07-10
Alls,

I am a recent linux convert.  Gotta say, I _love_ it so far and am still eagerly learning and getting things setup.

Coming from Windows, I was able to get surround from my Realtek AC'97 (ALC658, on [Abit IS7-E2]("http://www.abit-usa.com/products/mb/techspec.php?categories=1&model=164") board) by hooking my fronts to the speaker out and rears to the line in.  I haven't been able to figure out how to do this in Gnome even after digging for info like mad.  It's running off ALSA and have tried different combinations of options and switches to no avail.

Can anyone help me out or point me in the right direction?  Keep in mind that I am still learning Linux, so even though I am an experienced user, my Linux knowledge is basic -- ie: give me directions if need be and I will be able to follow them.

Any help would be greatly appreciated.. TIA!

---

### Post by tommcd on 2006-07-10
Well, I don't know if this will work since I have a simple 2.1 speaker system, but if you right-click on the speaker icon on the upper right corner of your screen and choose 'preferences'  there is an option for 'surround' in the dialog box that comes up. Did you try that?

---

### Post by grivad on 2006-07-10
Yep, tried that.  I have surround on, which gives me a "Surround" volume control, which is unmuted and cranked all the way up.  Same with "Center".  I've tried enabling "Duplicate Front", tried "Shared" and "Independent" for the Surround Jack Mode, changed the channel mode to 4ch, etc. and combinations therein, all to no avail.  I only get sound out of my fronts (Speaker Out), none out of the rears (Line In).

If it is working properly, then I should get sound from all four speakers regardless of the number of channels of what I am playing, right?  I want music, for example, to come from all four speakers at once..

---

### Post by tommcd on 2006-07-10
Try typing 'alsamixer' (without quotes) in terminal. Use the left & right arrow keys to toggle to surround, and use up & down arrow keys to increase/decrease volume. Is surround sound turned off or muted? The 'm' key controls mute.

---

### Post by grivad on 2006-07-10
Same thing -- surround is cranked all the way up, unmuted..

---

### Post by grivad on 2006-07-11
anybody..?

---

### Post by Vlatko on 2006-07-11
> **grivad said:**
> anybody..?
i had the same problem as you, same card as well only different board. i'm afraid there isn't a soultion which will suit you to be honest. i'm a total new linux user and i gave up and returned cause of stuff like this, more than once. right know i am in the process of prepairing for yet another install of linux. anyway, back to topic. here's what i found out, from personal experience, about your issue.

you most likely tried playing mp3s and got only the front two speakers to work. i'm 100% certain that's the best you will get in linux with mp3s. there is a way, rather complicated, of forcing all the channels to play the same sound but i'm afraid i can't help you with that. search the forums for "/.asoundrc". that's some linux method of forcing all the channels to play but it's not the same as it sounds in windows. windows have some drivers that take the mp3(stereo) and emulate it into surround. sounds ok to me but it's not surround.

if you have alsa installed then you most likely have surround but you can't get it from a stereo source. hence you need a dvd or something which is encoded with surround. i tried various programmes and stuff and managed to get surround sound to work from dvd's and surround encoded stuff. i installed the multimedia codecs and dvd files with automatix and it worked. though not in all programmes. i got best results in kaffeine, there in the preferences you could select the output to 5.1, 7.1...and if the source had surround you would get it. i'm afraid that's the best you can do, have surround sound but no way of "emulating" it for mp3s and other stereo sources. you can ask around for the "/.asoundrc" method and try it out, maybe that will suit you. i myself didn't make it.

anyway know i didn't help you out as much but hopefully i shed some light on the issue. ;)

---

### Post by grivad on 2006-07-12
Thanks, that does help!  Very informative.

---

### Post by TOM_C_A_T on 2008-02-03
yeah,

improved gnolej,

but

didn't solved the prob !!

---

### Post by eyeonthewinner on 2008-05-22
I have a realtek ac'97 that I just got to work!

1) Open up volume control, go to prefrences and enable channel mode. put this on 6ch under the options tab
2) Also enable duplicate front and check it under the switches tab

this worked for me, the only thing with no sound is the center, but I have the sub so i'm happy.

Good luck!

---

