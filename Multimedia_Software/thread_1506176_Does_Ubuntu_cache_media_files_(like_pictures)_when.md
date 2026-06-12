---
title: "Does Ubuntu cache media files (like pictures) when viewing them?"
date: 2010-06-10
forum: Multimedia Software
---

### Post by Asagrim on 2010-06-10
I am just asking because i want to be sure, that sensitive data can not be extracted from my computer unencrypted, using cached files. For instance i would not want my girlfriend's picture to be uploaded to some random site, whereas it normally stays on an AES encrypted volume, but i viewed it once, so it was available in some cache folder, unencrypted - yea, sadly, it happened in windows -.

---

### Post by Rhubarb on 2010-06-10
Ubuntu would cache in viewed pictures into RAM, and if that gets full it may get cached into a swap partition.

Thumbnails do get saved into your **/home/yourusername/.thumbnails** directory.
- These could be easily deleted, but note that it would be possible to resurrect these thumbnails with a tool like photorec (found in the testdisk file recovery package).

If you want more privacy, I suggest you look into full disk encryption, which can be enabled when you install from the Ubuntu alternative install CD.

---

### Post by Asagrim on 2010-06-10
Thank you!

Fortunately i have 2 GB of RAM, so it is not likely to get full at my average usage.

Unfortunately i have ubuntu netbook remix - since a couple of days -, because this machine is a netbook, and i like this OS very much, so changing OSes is not an option.

I have heard that you can change settings of the swap file, in a way that Ubuntu _only_ uses the swap if it cannot use any more RAM, and not until that point. Where can you set that?

Alternatively, is there a shredder program - or an embedded command line option - which i could use to safely erase the contents of that .thumbnails folder?

---

### Post by Rhubarb on 2010-06-11
> **Asagrim said:**
> I have heard that you can change settings of the swap file, in a way that Ubuntu _only_ uses the swap if it cannot use any more RAM, and not until that point. Where can you set that?
I think that's a kernel parameter, I'm not too sure how / where to set this, but I think it's called "**swapiness**" or similar.

> **Asagrim said:**
> Alternatively, is there a shredder program - or an embedded command line option - which i could use to safely erase the contents of that .thumbnails folder?
Yes there is :)
There's 2 packages that you could use, one is easy to use and the others are simple command line tools.

The easiest would be bleachbit, once installed you'll find it in:
Applications --> System Tools --> BleachBit
BleachBit allows you to clean up most cache files and stuff left behind in a nice GUI interface.

The other more powerful tools (and hence can also be more dangerous) would be the collection of tools found in the **secure-delete** package
The tools include the following command line apps:
**sdmem, sfill, srm, sswap**

**bleachbit** and **secure-delete** package can be installed easily with the Synaptic Package Manager.

Thats one of the great things about Linux, is that you can customise it the way that you want :)

Note: I used the srm command on around 100GB of files on an old hard disk.  
It took quite a long time to delete as I made it do a very secure delete operation, but unfortunately after around 8 hours of srming, the hard drive got completely corrupted.
As I couldn't revive the hard disk myself, I took it to a disk recovery service, who told me after a month that they were unable to recover any information from the disk.
So, because my hard disk was in a rather poor shape, doing a very intensive srm operation killed the hard disk completely, and hence turned it into an expensive paper weight.

It's possible achieve all this with other methods as well, such as by using separate accounts with a more restricted access, using ram disks mounted in different places (a good example of a ram disk can simply be found in your /tmp directory).

Let me know if you wish to know any more, as there's plenty of fun and practical ways to help secure a system.

---

