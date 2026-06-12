---
title: "gen2 ipod shuffle vs rhythmbox + gtkpod"
date: 2011-03-29
forum: Multimedia Software
---

### Post by 98cwitr on 2011-03-29
After two days of searching I still havent found a resolution that provides easy usability so I decided to post up...two problems:

Task: Get some of the music off my computer onto the ipod and have it play back.

Problem: Once the transfer from Rhythmbox takes place, the ipod will not playback (blinks orange-green-orange-green)

Prereqs: All music is in MP3 format

1) Rhythmbox sees the ipod, will sync with the ipod, but the structure that it creates is similar to a flash drive more than an ipod.

1a) With the ipod in it's current format, gtkpod will not see the ipod.

2) I try to reformat into FAT32, and Disk Utility says that is can't do it, but still blows away the drive. It will reformat in windoze.

Any help much appreciated, I refuse to use iTunes.

---

### Post by ron999 on 2011-03-29
Hi
I have a 2nd generation iPod Shuffle.
It works fine with gtkpod 0.99.14.

If things have got messed up, use the **iPodResetUtility** to wipe it clean then start afresh with gtkpod.
The reset program runs in Windows, it's here:- [http://support.apple.com/kb/ht1238](http://support.apple.com/kb/ht1238)

---

### Post by 98cwitr on 2011-03-30
Initial sync with iTunes (in windoze) got the format back "right" and now gtkpod sees the shuffle.

Had to rename the iTunesStats file in the iTunes folder, but finally got gtkpod to work...guess I'll just use it instead of Rhythmbox.

---

### Post by gvoima on 2011-04-02
Use the pmcenery ppa and remove libimobiledevice0.
Then get the default libgpod library for lucid, that's 0.7.93 and put it somewhere, backup the current library and replace it with a symbolic link to the older one.

This is the only way I got my 2nd gen ipod touch and ipod shuffle 2nd gen working beautifully with rhythmbox.

There's something with libgpod 0.8 (current stable) that breaks the sync and filesystem check on the older ipod shuffle. I didn't have the time and energy to try solving it... So I just replaced it.

Be aware that an older libgpod doesn't support the newer ipods that was added after 0.7.93.

[edit] just restore the ipod in itunes once, no need to do anything else. Should work after that, atleast it did with me. And make sure rhythmbox has the ipod plugin **enabled**[/edit]

---

### Post by __Ryan__ on 2011-04-30
The shuffle is a pain to get working sometimes. The key for me was to remove the directory structure, reinitialize it with gtkpod, then it worked flawlessly with Rhythmbox.

I did a writeup of all the steps here. 

[http://www.wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux]("wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux")

Good Luck!

---

### Post by jjinco33 on 2011-06-16
Thanks. gtkpod did not automatically detect the missing ipod directories, however after I selected the option to Create ipod directories from the menu and saved the changes I have been able to use the ipod shuffle with Rhythmbox.

---

### Post by kioni on 2011-06-23
Hello my name is Lluis, I live in Barcelona, my English is not very good, and took a few days looking for a solution to the problem I have with Rhtyhmanbox to fill with music and play my Ipod Shuffle.
I think the best solution is that proposed Gvoima.
This happens to me since I have Maverick, and did not go as you know, in the Lucid version.

I think the solution you propose is the best I've found, the problem is I can not get to follow your instructions because, as I said before I do not understand English very well: (

Can you explain more clearly step by step, how do I solve the problem?

You need to install the gtkpod? Or you can work only with Rhythmanbox?

Thanks.

---

