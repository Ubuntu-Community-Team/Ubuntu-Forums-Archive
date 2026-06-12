---
title: "Should I use JACK with my MIDI keyboard?"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by justynbutler on 2006-12-25
Hi,

I've just set up my new USB midi keyboard to play with Rosegarden.

I do this:
* Open up some alsa midi ports with timidity using the line: "timidity -iA -B2,8 -Os &"
* Open Rosegarden and select the new ports as output, and my midi keyboard as input.

It works fine, but there is noticeable latency when I actually try to play anything live.  From some things I've read, I get the feeling I should be using JACK rather than alsa to do this stuff.  But other things I've read suggest that for midi, JACK just acts as a frontend to alsa or something like that, which to me implies that it wouldn't improve the situation.

Could somebody please clear this up for me and suggest what setup I should use for my non-pro desktop setup? Any pointers/URLs to do with this topic are greatly appreciated.

cheers,
Justyn.

---

### Post by foolsh on 2006-12-26
First let me say that I do not have a midi keyboard ,I have been looking at one I think I want, but I have been messing around with midi timidity rosegarden and vkeybd`virtual keyboard.

and I find rosegarden kinda laggy as far as pressing a key and getting sound.
you might want to try the program aconnectgui. Its a graphical way to connect midi devices to different ports.
for instance if i want to play some sounds with my pc keyboard i run vkeybd and aconnectgui
on aconnectgui I click the plug button at the top and connect Virtual Keyboard to TiMidity port 0 like this
[IMG]http://foolsh.home.insightbb.com/snapshot2.png[/IMG]
instead of running through rosegarden and the response is much faster! but if you are trying to record from key presses to music notation by using rosegarden sorry i cant help with that
hope this helps

btw i use alsa not jack

---

### Post by justynbutler on 2006-12-26
Thanks foolsh, that was helpful. I've experimented with aconnect now and it's incredibly easy to use, and does indeed seem to be a little faster.

There is still some latency though, which causes issues for playing faster music. I'm going to read more on JACK and try to find out if it will help in this situation. It's website clearly states that using it will introduce zero latency, but I'm not sure to what extent this applies to midi.

Justyn

---

### Post by ssavelan on 2007-01-15
I have run JACK for a couple of weeks and I am truly blown away....

I don't really like running programs that do not flow into the jack server now.

I run a midi kybd into echo layla... 16 feet of cable and very little latency.

I've never seen a better sound system at any price.

---

### Post by foolsh on 2007-01-16
Is JACK in the repositories?
Or did you compile it from source?

thanks

---

### Post by sgx on 2007-01-16
jackd jackrack jamin qjackctl and ladspa are a good start...

---

