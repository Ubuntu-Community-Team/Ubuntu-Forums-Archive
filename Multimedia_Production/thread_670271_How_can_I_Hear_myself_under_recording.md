---
title: "How can I Hear myself under recording?"
date: 2008-01-17
forum: Multimedia Production
---

### Post by Eyvind on 2008-01-17
Hello there!
I'm going record som guitarriffs that I'm playing, but I can't hear myself when I'm recording. It's impossible to play good when I don't hear myself.
When I first installed Ubuntu without any thing else on my harddisk (I run dualboot now), I heard myself all the time when I plugged my amp into my pc. But after several time of formating, I can't... :(
How can I hear what I'm playing?

I'm using Ubuntu 7.10 (not studio)
I've got a Tundra 1032x pc.

---

### Post by BobSongs on 2008-01-17
[FONT="Verdana"]Greetings.

Looks like no one has answered you.

I know what you are talking about. Getting the "monitor" to work: hearing your "input" as you record.

I am not sure, personally, if this can be done, or done easily. Since I dual-boot from Linux occasionally back to Windows for that. Recording music isn't amazing at the moment, and Ubuntu Studio is still in its infancy.

What software are you using. I see you're using Gutsy Gibbon. You may wish to consider Ubuntu Studio for its low-latency kernel.[/FONT]

---

### Post by Stochastic on 2008-01-18
Probably your issue lies in the software not making a connection for you to hear things.  If you're running qjackctl when you record (something you probably should be doing), then you just need to link the input channel to the output channel in the connections window.  You will notice some latency with what you're playing though as you'll be hearing a signal that has been digitized then undigitized unless you're using a low latency or realtime kernel (ubuntu studio ships with one).

Some higher-end soundcards have the option of direct hardware monitoring to avoid any latency when recording.  If that's the case for you, then it's probably an issue of drivers working/not working or even just a switch that you've forgotten to flick on the card.

---

### Post by motin on 2008-01-20
> **Eyvind said:**
> Hello there!
I'm going record som guitarriffs that I'm playing, but I can't hear myself when I'm recording. It's impossible to play good when I don't hear myself.
When I first installed Ubuntu without any thing else on my harddisk (I run dualboot now), I heard myself all the time when I plugged my amp into my pc. But after several time of formating, I can't... :(
How can I hear what I'm playing?

I'm using Ubuntu 7.10 (not studio)
I've got a Tundra 1032x pc.

Right-click the volume meter in the top panel and choose open volume control -> Edit -> Settings -> Tick all the check-boxes next to "Capture" items. 

Then go back to the volume control mixer, choose Recording tab and increase the volume of the Capture meter. 

I have everything in Swedish so the exact items to click and choose may be different in english, but it should give you enough guidance I hope.

Btw, are you using JACK and Creox (guitar effects box) for this? Read [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) to get you started with a Real Time kernel and JACK.

Cheers!

---

### Post by Eyvind on 2008-01-21
Thanks for answers :D

I've been using Audacity and the deafult recorder in ubuntu. Not very advanced I know.

Motin: You can write it in swedish. I'm from norway and understand swedish, so that shouldn't be a problem :)
I'll see what I can do.

Edit:It worked motin :) thanks!!

---

