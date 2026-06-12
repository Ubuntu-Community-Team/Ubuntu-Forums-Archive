---
title: "Gpodder mangles podcast titles/metadata"
date: 2012-01-21
forum: Multimedia Software
---

### Post by bailewen on 2012-01-21
Looking for any suggestions on how to work out this bug/issue with Gpodder. I like to load up a lot of podcasts on my cellphone and in general gpodders seesm to be the top podcast aggregator but it has one major problem...while the podcasts show up with proper titles in Gpodder, when you synchronize, or even just export the file to your desktop, the .mp3 or Mp4u or whatever ends up with a garbage file name which prevents my phone or other device from sorting the podcasts by title. I generally end up with file name that is just the date + some sort of abbreviation of the title. So maybe the filename is write and it's missing some metadata. 

By way of example, I just downloaded "Defending Climate Science's Place In The Classroom" from NPR. With itunes, the file name in my MP3 player would be ""Defending Climate Science's Place In The Classroom" and the metadata would show that it was downloaded on such and such date from "NPR: Talk of the Nation".

With Gpodder, I end up with a file called "20120120_totn_01" and no metadata beyond the fact that it's a3.9 mg mp3. ](*,) That means that when transfered to a player all of the Gpodder files, when sorted by podcast title, show up as "Unknown" and if you just go by individual file titles you get a bunch of 10 digit number followed by some obscure abbreviation. 

Any suggestions other than going back to Miro/Rythmnbox/Amarok? None of them download and sort podcasts to my laptop very smoothly compared to Gpodder. . .

p.s. Ocelot/Gpodder 2.6
p.p.s. I just figured out that it's only happening on *some* podasts and not on others. ???

---

### Post by dwick on 2012-05-04
Try using the hook "tagging_hook.py", which fills the IDE tags. You can find it here: [https://github.com/gpodder/gpodder-hook-scripts/blob/master/tagging_hook.py](https://github.com/gpodder/gpodder-hook-scripts/blob/master/tagging_hook.py)

Then change gpodder config to enable "custom_sync_name_enable" and use "episode.title" for the custom sync name. This should then retitle your file on your player when you do the sync.

---

