---
title: "Can't access entire shared folder"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by motorcity909 on 2009-09-06
Hi all, apologies for re-asking this question.  I had previously posted it as part of a larger networking issue which Dmizer very kindly helped me with.

I have a Music folder totalling 84gb on my Ubuntu machine.  The entire folder is shared on my network.  When I access the folder on an XP machine, you can successfully see all 186 folders (one per artist, alphabetical).

You can access files within all the folders named A to L (total 35.2gb) but when trying to access folders M to Z (total 45.8gb) , access is denied.

The strange thing is the XP machine shows all folders M to Z as being empty. The two screengrabs (music_share1 and music_share2) show the Properties of the last L folder and then the Properties of the first M folder. 

As you can see, the first correctly shows over 1gb of Lucinda Williams, the second shows 0kb of Machine Head, even though there is definitely an album in that folder.

I wondered if there was a maximum size to a shared folder but I've recently added 2gb of music to the A to L folders and those are still accessible.

I've also shared a couple of individual M folders to see if files can be accessed -  they still can't be accessed on the XP machine.

I renamed an M folder with 'aaa' at the front of the name and it still couldn't be accessed.

Any help will be much appreciated.

As an aside; in his answer to the broader networking problem, Dmizer suggested I use gnump3d to shared the Music folder - I tried it, installed it and got it to show in a browser on the XP machine but couldn't get it to see my Music collection.

---

### Post by motorcity909 on 2009-09-07
Hi again.  I've managed to fix this.  I suddenly realised why Music letters M to Z weren't appearing in the share on XP (although I don't know the technical reasons for this).

Back at the end of July, my main XP machine got a trojan, which ultimately is what led me to dump XP and install Ubuntu.  

That XP machine held all my music and one thing I made sure I did before saying bye to XP was to transfer the music off it - I put artist letters A to L onto an external HD and then onto my wife's XP laptop - then artist letters M to Z went onto that same external HD (there wasn't space on either the laptop or the ext HD for the complete music collection, hence the split).

Once Ubuntu was up and running, I transferred the music back onto that PC, via the network from my wife's laptop and via the ext HD.

I suddenly realised tonight that all the folders that wouldn't share properly were those that had been put solely onto the ext HD - letters M to Z.

Obviously something had 'tainted' those files - I wouldn't use the word corrupted as the files played fine on the Ubuntu machine.  The only thing I can think of is that the ext HD is formatted as FAT32, whereas my wife's XP laptop is NTFS - no doubt a more technical person could explain/confirm that.

Anyway, tonight, I slowly copied all those files onto my wife's XP laptop, then back to Ubuntu via the network and now the entire Music folder is fully shared, from ABC to ZZ Top!!

:guitar:

---

