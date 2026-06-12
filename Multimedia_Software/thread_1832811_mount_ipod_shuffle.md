---
title: "mount ipod shuffle"
date: 2011-08-25
forum: Multimedia Software
---

### Post by beacon on 2011-08-25
Although parts of this problem were discussed earlier in the year, I believe my problem is not quite the same. I am trying to mount an iPod shuffle (4th generation green) and have tried everything I can find in the postings, but with no luck. I think in the process I have made a mess of fstab and who knows what else. 

Following instructions in the early posts I am copying what I get when typing fstab:

# etc/fstab: static file system information
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID="b5decf23-1a5c-474f-8d98-a97bf95bd7a1" TYPE="ext4"    /media/iPod vfat
# swap was on /dev/sda5 during installation
UUID=5512cf09-a099-415e-ae9c-166f1abe9a16 none            swap    sw              0       0

And the following is from 'bilkid':

/dev/sda: TYPE="promise_fasttrack_raid_member" 
/dev/sdb1: UUID="b5decf23-1a5c-474f-8d98-a97bf95bd7a1" TYPE="ext4" 
/dev/sdb5: UUID="5512cf09-a099-415e-ae9c-166f1abe9a16" TYPE="swap" 

I'm probably not including all the relevant information, but I am on ubuntu natty and would appreciate any help in getting the ipod recognised.

By the way, I am very unclear about the whole Ipod issue. Many bugs have been reported, and as far as I can discover, there has been no solution to them. If a bug is the cause, then I have wasted a lot of time trying to do the impossible. On the other hand, some people seem to succeed, so there might be someone who can help.

Thanks a lot.

---

### Post by cottfcfan on 2011-08-25
Hi Beacon.
According to the official Documentation:
[https://help.ubuntu.com/10.04/musicvideophotos/C/music-portable.html](https://help.ubuntu.com/10.04/musicvideophotos/C/music-portable.html)
1st-5th generation ipods should be supported by Ubuntu.
I have read somewhere though that the ipod needs clearing and resseting using windows 1st.
Might be worth a try.

---

### Post by Brad55 on 2011-08-25
Have you tried [gtkpod]("http://gtkpod.org")

---

### Post by beacon on 2011-08-25
Thanks for both replies. I took the ipod to a computer shop where they 'initialised' it with itunes. I hope it isn't the case, but with all the things I have tried, I may well have accidentally reset it. I have tried gtkpod, banshee, amarok, and rhythmbox. The problem, as I understand it,  is that the Ipod has to be mounted before any of those can be used/ and I am unable to mount it.

---

### Post by Hat FM on 2011-08-25
Same problem here, so I hope you find the solution you're looking for.

My 1st gen iPod Shuffle won't correctly mount in Ubuntu 10.04 - so I can't use it at all.
It's my only MP3 player, and I'm lost with out it.

I know it's in good working condition, and USB pen drives work perfectly in the same slot.

And I'm new to Ubuntu, so I'm finding it very difficult to understand some of the  solutions suggested on the web.

---

### Post by Brad55 on 2011-08-27
I have a Apple 120GB Black 7th Generation iPod Classic and it works fine under Ubuntu 10.04 64 bit.

---

### Post by cottfcfan on 2011-08-28
Beacon..
A friend of mine has a 4th generation ipod. He uses Linux Mint.
He opens Banshee 1st. Plugs in his ipod. It automatically shows up in the left hand column after a few seconds, then he just either syncs it, or drags and drops songs onto it.
Nothing else has needed configuring.
What is happening in your case? Anything?

---

### Post by beacon on 2011-08-28
Thanks for the replies, and particular thanks to cottfcfan. The advice looked promising, but I'm afraid my bad luck continues. Perhaps I should fill in what has been happening. Owing to a number of factors I had to get a new computer. The person who built it is quite knowledgeable and even uses Ubuntu (the first person I have known who hasn't simply suggested I use Microsoft Windows because that is all they are familiar with).   Anyway, he installed 11.10, and it is taking me a great deal of time to cope with Unity (which, by the way, I dislike intensely so far). At the shop he inserted the iPod, and Banshee immediately recognised it. He then did all the installation necessary, and things seemed to be going swimmingly until we tried to listen to the iPod, and all we got was the usual message 'please use iTunes to restore the iPod'.   This morning I have followed your suggestion. The ipod shows up in Banshee; although called 'unknown device', the properties show that it is my 4th generation shuffle. Once again I have apparently been able to transfer the music, but when I try to play, there is only the same message to use iTunes.  I recognise that some people, such as Brad55, have succeeded where I have failed, but I really think it is Apple's attempt to make it difficult, if not impossible, to use iPod without going through iTunes. I am more and more disinclined ever to use an Apple product.  I am having yet another problem in that I can't seem to get this message in a form that recognises my paragraphs. I am sorry about that.

---

### Post by cottfcfan on 2011-08-28
Beacon..
You are right about what Apple try to do, and sometimes dual booting Ubuntu with Windows, is the only answer, as there are certain things that will only work with Windows.
 What isn't ideal though is that you have Ubuntu "11.10" installed.
This is still only an alpha version, and will be prone to breakages and problems for a while yet.
11.04 is the current stable release, i'd go with that, then you can use ubuntu classic rather than Unity.

---

