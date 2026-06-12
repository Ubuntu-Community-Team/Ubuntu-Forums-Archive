---
title: "[SOLVED] rhythmbox always removing songs..."
date: 2008-05-18
forum: Multimedia Software
---

### Post by Nebelhom on 2008-05-18
Hi,

I've a curious problem with rhythmbox. everytime I start it, I can see it "removing" (it is a very quick countdown of number of songs I have) the song files from the playlist.

so far, I was always able to put them back in, but sometimes I need two or three times to make it "understand" I want them back in.

when adding the files, it always wants to look for a specific codec that it can't find. the first time I did it, it added lots of other codecs (I cant remember how many), but one it couldnt find.

system wise I am dual booting XP and hardy. my song files (mostly mp3s and some other formats) are on a windows NTFS partition.

This is more a nuisance than anything else really.

does anyone have a potential explanation for this? if so, could you give me easy to follow instructions to remedy this issue (sorry, I'm new to linux and the ubuntu community)? Thanks a lot guys.

Nebelhom

---

### Post by Nebelhom on 2008-05-19
Hi,

I've been watching this little quirk for awhile now.

everytime I want to add something to the list, it states that it cannot find my windows partition, just to show it to me right after.

Is it possible, that ubuntu has to recognise the windows partitions new each time it boots which then in turn leads to recognition of the song files used from there to be invalid, because they were used by a software on the windows partition? (man this sentence made my head spin)

does that sound plausible and if so, how to remedy, without moving my mp3s across?

thanks for any suggestions

Nebelhom

---

### Post by fontenot_1031 on 2008-05-19
Do you have the ntfs drivers installed?  Do you have the partition set to mount on boot?
I've had a lot of problems with rythmbox before so I've just been using xmms.  Old but great.

---

### Post by Nebelhom on 2008-05-19
hmmm... by the fact that I have no clue, that would potentially mean no ;).

I was hoping that would be automatic ;).

could you give me easy instructions on how to check that? 

what would be the advantage of it not mounting on boot up?

I see, I am assuming too many things :KS

---

### Post by perhhk on 2008-05-19
I think we'll be able to tell if you posted the contents of fstab

```
sudo gedit /etc/fstab
```

Add a line similar to:
```

/dev/hdb1 /mnt/share ntfs-3g defaults,locale=en_US.utf8 0 0
```

but /dev/hd  - make sure it is the correct letter and number for your ntfs partition.

"Once you edit your fstab file just type on the command line "mount -a". Be sure to create a directory for the mount point."

---

### Post by Nebelhom on 2008-07-01
sorry for the very late reply. busy few months ;(

Huge big thank you goes to perhhk. I still don't quite know why but it worked! 

In case anyone has a similar problem to mine, here is what I did, maybe it is a general solution

All I did was create a folder in /media in my case Barad-Moll

then followed perhhk's instructions. (for me the hdbl was sda5, but I think for most it is sda1)

it did the trick ;)

---

