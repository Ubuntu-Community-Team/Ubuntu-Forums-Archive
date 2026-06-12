---
title: "mp3 id3 tags missing but nautilus audio tab has correct album info"
date: 2008-11-15
forum: Multimedia Software
---

### Post by han555 on 2008-11-15
I have a bunch of mp3s that i loaded into both amarok and rythmbox and they are organized fine (proper artist, album, track, etc.).  I try to load these into an mp3 player and they all go under Unknown. I was curious so I took a look at the files in Windows and noticed there was no id3 info listed.  When I look at them via nautilus, however, the audio tab lists all of the proper information.  I was still curious so i did an 'apt-get install id3v2' and listed the files.  No id3v1 or id3v2 tags were found.  If there are no id3 tags on these files, how is nautilus listing meta data about them?  I renamed the containing folders to make sure it wasn't inferring the info from the directory structure. nope, even with the files under different folders, the audio tab lists the correct info.  Is there a way to convert whatever it is that is supplying this data into id3 tags so all of my media players can read this info??

---

### Post by kostkon on 2008-11-15
> **han555 said:**
> I have a bunch of mp3s that i loaded into both amarok and rythmbox and they are organized fine (proper artist, album, track, etc.).  I try to load these into an mp3 player and they all go under Unknown. I was curious so I took a look at the files in Windows and noticed there was no id3 info listed.  When I look at them via nautilus, however, the audio tab lists all of the proper information.  I was still curious so i did an 'apt-get install id3v2' and listed the files.  No id3v1 or id3v2 tags were found.  If there are no id3 tags on these files, how is nautilus listing meta data about them?  I renamed the containing folders to make sure it wasn't inferring the info from the directory structure. nope, even with the files under different folders, the audio tab lists the correct info.  Is there a way to convert whatever it is that is supplying this data into id3 tags so all of my media players can read this info??
Since you say that *Amarok* and *Rhythmbox* were able to see the tags, I assume that the files indeed have ID3 tags. It's just that your MP3 player may only recognise a specific version(s) of ID3 tags.

You could read the documentation for your MP3 player to see what version of IDE3 it needs. For example, maybe your MP3 files have IDE3v2.4 and your player can only see IDE3v2.3 (or lower version) tags.

You could also install *EasyTag* to see what version of IDE3 your files have (since *id3v2* had problems reading them) and if needed change their ID3 version according to the one that your MP3 player can recognise.

---

### Post by han555 on 2008-11-15
Installed EasyTag but it is also telling me there are no tags.

---

### Post by han555 on 2008-11-23
Is there a plugin for amarok or some other software that can copy the meta data into multiple tags?  So far no tagging program has been able to recognize any tag on these.

---

### Post by mpstump on 2008-11-25
I had this same problem, where Amarok didn't see tags, but other players (exhaile) did. I also had a problem where the tags in Amarok were chopping off the first and last letter in my tags, so I'd have artist like ixie (instead of Pixies, etc) It was a id3v1/v2 thing, and there was a program I found that allowed me to tag v2 from v1, or vice versa, whatever. Unfortuntately, I don't remember what that program was, as it's on a crashed disk from a recent failed upgrade (a whole other story). It wasn't Cowbell, or Picard. I'll figure it out and repost.

####  edit   ####

I think I found it, it was kid3, so ```
sudo apt-get install kid3
```, it should be in the repositories.

---

### Post by han555 on 2008-11-25
thanks man.  i'll check this out when i get home from work tonight and let ya know.

---

