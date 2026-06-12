---
title: "Intel HD Audio Utility"
date: 2012-02-09
forum: Multimedia Software
---

### Post by Jornux on 2012-02-09
I just installed Lubuntu, and I must say it works very well. There is only one thing that bothers me: the sound card.

The audio card in my laptop is a Realtek HD one, with the standard three connectors: headphones, mic and line. There is no problem at all (any more) with the drivers, everything is correctly loaded. I have sound coming from my laptop speakers, the headphone channel outputs sound and the line and mic input channels also work perfectly.

In Windows I installed Realtek HD Audio Manager (together with driver), which allows to set input channels (line, mic) as output channels (front, rear). This is very useful for setting up surround audio. For example, it is possible to define both input channels as front speakers, or as front and rear, really all combinations are possible, while in Linux they are fixed to mic and line inputs.

My problem is now that I cannot seem to find an equivalent utility for Linux; alsamixer has a lot of options, but cannot set the input channels to output.

So, it's not really a 'problem', but think it is an inequality with respect to Windows. Also, this reconfiguring of audio channels can be very handy :-), for the moment I'm obliged to use Windows to view videos with surround sound.

---

### Post by MoreOrLess on 2012-02-09
It's called jack retasking. See: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

### Post by Jornux on 2012-02-09
Thank you very much! :-D I was hoping for such a simple tool, but somehow I could not find it.

Now testing it, and it works perfectly!

---

