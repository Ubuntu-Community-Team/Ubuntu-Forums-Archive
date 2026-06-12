---
title: "burn multiple discs at once"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by stlouis1 on 2007-10-01
anyone here know if theres any linux software that can burn to two drives at once. cuz i burn off dvd's like a machine and i have 2 drives for that reason. well, i only make 2 copies of everything, one is an actual backup, the other is the copy ppl can watch, no one takes care of anything around here so i have to keep backups of backups

in windows i could use nero to burn 2 at a time, only it took twice as long even though each drive has its own ide channel since my hard drives are all sata. alcohol worked too, but it can only burn iso's, and i dont necessarily want to have to make iso's of what i want to burn.

just want to be able to burn 2 copies at once. havent seen an option in K3B.....which reminds me, kde based apps would be preferred, but not necessary at all cost

---

### Post by kidders on 2007-10-02
Hi there,

> **stlouis1 said:**
> i dont necessarily want to have to make iso's of what i want to burn.Technically, you don't have a choice about that. You can't really burn an optical disc without converting what you want to put on it into some sort of disc image first.

Anyhow, why not just use cdrecord? Most disc burning apps use it anyway, under the hood, so you might as well cut out all the user interfaces & invoke it directly yourself. Just be careful not to overload your computer's I/O buses ... when burning multiple discs simultaneously, you may want to use a slightly lower record speed than your drives are capable of, to ensure that there are no bottlenecks.

---

### Post by stlouis1 on 2007-10-02
i just want to be able to burn data from my hard drive to 2 drives at once, it shouldn't have to be in an iso form to do that. nero can in windows, but im not buyin nero for linux, i dont even like it in windows. 

im not worried about overloadeding i/o buses, i built my system to handle that kind of stress. i have each dvd drive on its own ide channel cuz all my hard drives are sata, there only 2, but occasionaly i connect an external sata / ide adapter to backup ppls stuff

---

### Post by kidders on 2007-10-02
> **stlouis1 said:**
> i just want to be able to burn data from my hard drive to 2 drives at once, it shouldn't have to be in an iso form to do that.Generally, it does. Without generating an ISO, an application would have no way of figuring out what to write onto a disc. Almost all software prepares the ISO asynchronously, although I suppose it would be possible to burn the disc image as it was generating ... if you didn't mind throwing away CDs every time any sort of processing error cropped up in the middle of the burn ... by piping the output of mkisofs directly to cdrecord.

When burning the same data to multiple discs, surely it would be silly *not* to prefabricate the disc image though.

---

### Post by Magnentius on 2008-04-20
We're missing the point here. So is it possible to burn to multiple devices in Linux or not?

(twin threads @ [http://ubuntuforums.org/showthread.php?t=420573](http://ubuntuforums.org/showthread.php?t=420573) and [http://ubuntuforums.org/showthread.php?t=443364](http://ubuntuforums.org/showthread.php?t=443364))

---

