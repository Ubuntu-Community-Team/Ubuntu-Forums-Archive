---
title: "Rhythm Box doesn't keep changes I make to artist names and such."
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by sroark on 2008-02-02
Here is what I am doing, I use the 800+ albums from my Windows partition which are all perfectly organized in my iTunes library and the ID3 tags match, but the problem is that in Rhythmbox, a few artists appear more than once. An example is "Jacks Mannequin" and "Jack's Mannequin" which appear twice because of the apostrophe difference. It is just annoying. I change the information and it forms one artist, but next time I restart Rhythmbox it will revert. It only does this with a few artists, but I'd really like to fix this. Also, when I am using Ubuntu, I can't edit the file names on the Windows partition because I don't have permission, perhaps this is the problem? Because in Ubuntu the names (such as Jacks Mannequin) aren't the same, but in Windows the are. 

Any ideas are greatly appreciated, I'm still getting used to all this, but I'm making progress, this is really the last stumbling block (as of right now :D)

---

### Post by BennBuntu on 2008-02-03
Haven't got much experience working with NTFS,  but here's some ideas

To tackle the whole library at once, use easytag, a program made just for ID3 tags, pretty easy to use.

in terminal type
```
sudo apt-get install easytag 
```

now if you can't write to the NTFS partition, It's probably to do with permissions. 
I'm not sure what changing permission of the folders will do on the windows side, so if you're not sure either, just run easytag as root for now, although it's a bad habit.

> gksudo easytag

---

