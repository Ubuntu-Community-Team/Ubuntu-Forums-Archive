---
title: "say-epos"
date: 2008-09-10
forum: Multimedia Software
---

### Post by Mariane on 2008-09-10
Could someone please give me the settings of alsamixergui 
so I can get say to function properly? 

I don't seem to be able to tune it, it starts OK but then 
goes bzzzt towards the end of the sentence. 

Example:
eposd & (return)
say out of the blue (return)

is nearly OK but 
say out of the blue blue blue (return)

sounds like waouaouaou at the end

say hello (return)

sounds like hellokzzzt

Mariane

---

### Post by Mariane on 2008-09-11
Actually this seems to have been sound-card related, because 
when I plug in a set of usb-connected headphones with an 
integrated driverless sound card, the sound is much better. 

Staccado, still. It does not say
"out of the blue."
It says:
"out. of. the. blue."

Mariane

---

### Post by Mariane on 2008-09-11
Ooops, no. It works just as well now when I unplug the 
headset with the integrated sound card. So I don't know 
what fixed it, I tried so many commands trying to get the 
headset to function... 

Anyway, if someone has a problem with "say hello" going bzzzt 
and outputting a lot of ###### on the terminal, this should 
be good news: it shows there is a way to fix it without 
buying any extra stuff. 

The most radical thing I tried was:
sudo apt-get install module-assistant
sudo module-assistant a-i alsa-source

This rebuilds all sound drivers from scratch, by the look of 
it. So I copy these commands here only because they come from 
another forum, and I am not advising anyone to actually use 
them without asking someone with more knowledge than me first. 
It is not because it worked for me that it'll work for you, 
and for all I know you may end up with no sound at all... 

ASK FIRST, PLEASE! I MEAN IT. 

Mariane

---

