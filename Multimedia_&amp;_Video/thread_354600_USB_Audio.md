---
title: "USB Audio"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by nw_raptor on 2007-02-06
Greetings!

Last night I was watching a movie at a friend's house (as usual). I had my laptop which runs Edgy. With no internet and no codecs, my friend's computer (which runs Windows) couldn't play the movie file at all. So we tried hooking up his monitor (since it was big enough :D) to my laptop. Even on full blast, my laptop's speakers were just not good enough, so we figured we could hook his own speakers. Trouble was, he had no ordinary speakers! Instead he used his Hi-Fi. Not only that, but this Hi-Fi was not connected using ordinary RCA or even Minijack. It was USB! At first I thought we're doomed.

When I hooked the Hi-Fi on my laptop, Ubuntu gave me a little bubble about a new audio device and asked me if I'd like to open Audio Preferences. Since sound was still coming from my laptop, I figured I'd go and change the defaults. Instead of Autodetect for Music and Movie playback and Sound Events, I selected "USB Audio". The test button would actually beep from the Hi-Fi speakers! I thought "great". Well, too bad none of the other applications agreed. Xine, Totem (totem-xine) actually, VLC, all kept using my laptop's speakers and not the HiFi! On the second tab, I saw an option for the default sound card. It now had two options. My onboard card, and the HiFi. I selected the HiFi, exited. Still no go. I reopened Audio Preferences only to see that my default sound card was set back to my onboard one! :S

Since reboots didn't seems to help, We eventually hooked up the laptop to my friend's monitor's speakers, which although were louder than my laptop, were utter crap too.

The HiFi was some Philips, I'll try to get the model number too later.

Any ideas?

---

### Post by ssavelan on 2007-02-18
I feel that in the system>preferences>sound

changing the default there seems useless at best and dangerous at worst.  i have never seen that drop-down work and it seems that it has crashed my (sound) system before.

It is best to edit the conf files manually.  I am working on a similar issue, trying to get and iMic usb audio up.

too tired to make sense....

:neutral: :neutral: :neutral:

---

