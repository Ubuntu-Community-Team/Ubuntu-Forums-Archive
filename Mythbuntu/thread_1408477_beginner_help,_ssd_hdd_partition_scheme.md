---
title: "beginner help, ssd hdd partition scheme"
date: 2010-02-16
forum: Mythbuntu
---

### Post by drmax on 2010-02-16
Good morning,

I am setting up my first myth machine.  I just built a new computer this weekend, and plan to install ubuntu, and work with it for a while.  I would then like to add the myth package, and use the machine as a fe/be combined.  I have an old hauppauge 500, to catch my analog signal.  This machine will only be for surfing and tv use (recording and live tv, commercial dropping), so I figure if I bugger things up, I can always just reinstall and start over.

I have several questions:

1.  Does this seem like a good strategy, or should I just install myth right away and    learn it  all at once?
2.  Does the ssd need any special formatting or attention?
3.  What would be a good way to partition the ssd and the hdd?  Or should I even            worry about it?

I have spent many hours over the last few months reading and learning for my build, but I thought if any of the more expeienced users could kindly give me some advice on proper setup, I will get started out on the right foot.

Specs:
9500gt
4g ram
haup 500
amd regor 250
antec fusion 350 with remote
wireless network
antec 350w psu
ozc 60g ssd
wd 1.5 terabyte hdd


Thank you,
Max

---

### Post by laffinet on 2010-02-16
I would jump straight into a mythbuntu install.

It's not any more complicated than a normal ubuntu install, yet adding myth later can be a bit more work. Installing mythbuntu straight away means that some of the settings, setup etc. is taken care of.

Partitioning:
I would put /var/lib (this is where all your recordings, videos etc. are kept, amongst other things) on a separate partition (not sure if the installer does this automatically when you select "entire disk")

---

### Post by drmax on 2010-02-18
Thank you Laffinet for your reply.

I am assuming from what I've read I should put the os on the ssd, and all of the recordings on the hdd.

I will definitely just go directly to mythbuntu, again I appreciate your help.

Max

---

### Post by Al_Vampyre on 2010-02-18
> **drmax said:**
> 
I am assuming from what I've read I should put the os on the ssd, and all of the recordings on the hdd

That should work great, and it does mean easy re-installs if you eed to for any reason.

---

### Post by drmax on 2010-02-20
Thanks Al-V, for your response. I just got my system together, and it actually booted first try!!!
 
I'm now installing ubuntu from the live cd I got in a magazine. I did not see an option to go directly to mythbuntu on it, so I guess it will be ubu first, then mythbu.
 
I'm reading up on ssd and hdd partitioning and formatting. Still sort of flying blind, but perhaps the default partitioning will be ok. As I said above, if I bugger it up, or figure out a better scheme, I'll just start over, as this will be a dedicated FE/BE myth machine only, no other data or OS to worry about.
 
Appreciate the help,
Max

---

### Post by laffinet on 2010-02-21
Mythbuntu is a separate distro, which you would have to download from here: [www.mythbuntu.org](www.mythbuntu.org)
Ubuntu + adding mythbuntu later will work just fine, probably means a bit more work in terms of configuring

Regarding ssd formatting: I think there might be an issue with aligning partitions to physical sector boundaries. I stumbled upon this when researching how to format Western Digital EARS drives, which use 4k sectors instead of 512.
There's an article about SSDs here: [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)
And something about WD drives which 4k sectors here: [http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/m-p/9854#M534](http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/m-p/9854#M534)

---

### Post by drmax on 2010-02-21
Laffinet,
 
Thanks for the links, I sure have a lot to learn. I got ubuntu working and now I'm trying to get my internet connection going. Ubuntu installed on my ssd, and did not appear to do anything with the 1.5t hdd. Will start researching that once I have the wireless working. I enjoy learning this stuff, kind of like a big puzzle, and a treasure hunt combined, and I like puzzles! Your help is much appreciated.
 
Cheers,
Max

---

### Post by laffinet on 2010-02-21
No worries.

> **drmax said:**
> did not appear to do anything with the 1.5t hdd. 

Didn't think it would, so should all be good (for now).
Once you're ready with myth and want to use the 1.5TB for recordings you will have to mount it. One way of doing it is to mount it as /var/lib (which at the moment would be on your ssd). There's an excellent guide about mounting from boot [here]("http://ubuntuforums.org/showthread.php?t=283131"). Just report back here once you get there ore have problems.

Is the 1.5TB a EARS (advanced format) drive ? If so then it does have 4k sectors and you should make sure that the partition is aligned with the physical sector (as described [here]("http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/m-p/9854#M534")).

---

