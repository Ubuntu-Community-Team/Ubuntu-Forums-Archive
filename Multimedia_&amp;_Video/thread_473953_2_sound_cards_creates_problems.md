---
title: "2 sound cards creates problems"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by tvpind on 2007-06-14
I have 2 sound cards in my Dell Dimension 2400 which is giving me a headache. 

When ever I reboot my computer the active sound card changes to the one where my speakers is not connected to, so that I have to manually change the speakers to the other sound card. 

The 2 sounds cards that I have is: 

Intel - 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
Cirrus Logic - CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]

Info taken from my Device Manager. 

How can I change this behaviour or disable one of the devices?

Thomas

---

### Post by dannyboy79 on 2007-06-14
it's your lucky day, I just found out how to fix this, it was provided by mercals from this forum. he stated:

"asoundconf - This will list commands to use with asoundconf.

asoundconf list - This will list your cards by name.
(my output was)
Names of available sound cards:
rev20
Live

asoundconf set-default-card CARD - Card being the name of the sound card you wish to use. In my case it was Live.

Then right click on the volume controller on the taskbar and select prefrences. Selecte your card from the drop down list and select master.

This worked for me and I hope it does for you!"

let me know  if this works.

---

### Post by Strep on 2007-07-15
Thank you so very much for this post. I have 3 soundcards in my machine. I disabled my onboard AC97 in the bios and managed to get sound until I rebooted again. I couldn't understand what the problem was. I needed to make my 'Live' card the default instead of my Terratec.

Now happily typing whilst listening to some LTJ Bukem in Amarok.    Awesome!!!!:guitar:

---

