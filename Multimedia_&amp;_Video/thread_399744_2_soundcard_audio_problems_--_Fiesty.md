---
title: "2 soundcard audio problems -- Fiesty"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by mwolfe on 2007-04-02
i have a dell with a built in soundcard, and i installed a soundblaster 5.1 in it as well.  Back with edgy i could easily switch between soundcards by going to system->preferences->sound
and changing it from HDAIntel to SB Live 5.1


Now though (with fiesty) that doesnt seem to work and i can't figure out why. If i test the output it used to work with OSS with the soundblaster live but now OSS will go to the built in card.Multichannel playback goes to the 5.1 but even after i set it to that my mp3 player programs won't output to the soundblaster.  
The reason i can tell is because i have my headphones hooked up to the built in card. I don't care to disable the built in card because it has the jack up front which makes it more accessible for headphones when i want to use those. I need an easy way of switching between soundcards. 
Is there some command i can run to switch the soundcard manually?  I can't figure this out.

---

### Post by mwolfe on 2007-04-02
using asoundconf i was able to get it working, for some reason the gnome control thing doesnt work correctly.
do

1. sudo asoundconf list

to get a list of soundcards
then do 
2. sudo asoundconf set-default-card [whatever soundcard from steap 1]

3. sudo asoundconf reset-default-card


you might need to set it again as you did in step 2, not sure but i did 
everthing listed here:
[http://ubuntuforums.org/showthread.php?t=331408](http://ubuntuforums.org/showthread.php?t=331408)

and mine works now..

---

