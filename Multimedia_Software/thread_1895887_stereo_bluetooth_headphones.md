---
title: "stereo bluetooth headphones"
date: 2011-12-15
forum: Multimedia Software
---

### Post by sks24 on 2011-12-15
I have an HP DV 1000 (running 11.04) with bluetooth, and some motorola S305 stereo headphones.  I've paired and connected the headphones with the laptop (see screenshot) but no sound comes through the headphones.  

[This thread]("http://ubuntuforums.org/showthread.php?p=11301048") indicates that the headphones should appear in the sound preferences under hardware.  They do not (see screenshot).

This isn't a big deal.  But it would be nice if I could get audio playing through these headphones.  

Thanks,
Scott

---

### Post by hansdown on 2011-12-15
Hi, sks24.

In your sound preferences, click output.

Your headset should be there.

---

### Post by sks24 on 2011-12-15
Thanks Hansdown,

No luck.  (See screenshot)  And I've re-started and tried a few other tricks.  Nothing will get it to show up in the Sound Preferences.  This laptop is from 2004, and I don't have the bluetooth drivers installed on the Windows side of the computer.
(They wouldn't let the computer power put up a black screensaver.)

So, I don't know.  Maybe somebody knows a trick...

---

### Post by hansdown on 2011-12-15
I tried searching for drivers, etc.

Holy smoky bacon!

This particular headset has a number of bug reports.

[http://www.google.com/search?client=ubuntu&channel=fs&q=motorola+S305+stereo+headphones+ubuntu+drivers&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=motorola+S305+stereo+headphones+ubuntu+drivers&ie=utf-8&oe=utf-8)

---

### Post by sks24 on 2011-12-16
(chuckle)  Yeah.  I saw that with my first flyover on this a month or two ago.  Not a big deal.  It's just that this laptop cart has a lip on the front which covers the headphone jack ports, so a physical connection is a pain.  Oh, well.  Thanks anyway, though.

---

### Post by hansdown on 2011-12-16
I'm using a Plantronics BT headset.

Very cheap, and true plug and play.

---

### Post by sks24 on 2011-12-17
I see.  Thanks for mentioning this, because, for a variety of reasons, I should replace these S305s.  They're all but useless for the telephone, as the mic picks up every little sound, and the people on the other end of the line howl in pain every time I drop a pen or peck on the keyboard while talking.  They're awful.
So which model do you have?  Anybody can chime in.
What I would like is something 
1) lightweight on-the-ears with the bar going over the top of my head (instead of around the back of my neck).
2) a mic with a fairly long boom.  or one, anyway, that is very good at filtering out non-voice signals like wind, running faucet water, and keyboard activity.
3) Battery life is not important.  Decent sound would be great, but it's not imperative.  These Motorola S305s, btw, sound fantastic.  

Thanks again,
Scott

---

### Post by hansdown on 2011-12-17
I couldn't find my particular model on plantronic's website.

They have butter soft padding for the headphones,
.

Also very soft padding for the bar that goes over your head.

It has a boom mic, that folds up beside the left earphone.

The sound is very good.

Found it.

Mine are 995 model.

[http://www.google.com/search?q=plantronics+wireless+headphones&hl=en&client=ubuntu&hs=TPm&channel=fs&prmd=imvns&tbm=isch&tbo=u&source=univ&sa=X&ei=u0jtTqifDIHQiAL78Ni-BA&ved=0CNMBELAE&biw=1366&bih=660](http://www.google.com/search?q=plantronics+wireless+headphones&hl=en&client=ubuntu&hs=TPm&channel=fs&prmd=imvns&tbm=isch&tbo=u&source=univ&sa=X&ei=u0jtTqifDIHQiAL78Ni-BA&ved=0CNMBELAE&biw=1366&bih=660)

---

### Post by sks24 on 2011-12-18
Thanks.  Those do look nice.  I think I'll look into whether the newer bluetooth model works w/ Ubuntu: [http://www.amazon.com/Plantronics-Pulsar-Ultimate-Bluetooth-Headset/dp/B000HBPMVY/ref=sr_1_3?s=electronics&ie=UTF8&qid=1324220218&sr=1-3](http://www.amazon.com/Plantronics-Pulsar-Ultimate-Bluetooth-Headset/dp/B000HBPMVY/ref=sr_1_3?s=electronics&ie=UTF8&qid=1324220218&sr=1-3)

---

### Post by kcallis on 2012-02-26
The issue that I am trying to resolve is how to pair my LG HBS-700 headphone to use only the A2DP profile. This headphone will allow me to pair with my laptop for A2DP audio and also pair with my cell phone so that I can listen to a movie on bluetooth, and should my phone ring, it will allow me to access the phone and have a conversation.

I added to /etc/bluetooth/audio.conf the following:

Disable=Headset

But when I take a look at my devices, it still states that the headset profile is being used. Or is that just a generic entry and only A2DP is running?

---

