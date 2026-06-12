---
title: "Gui stalling, has been fixed. Can we get the patch set into maverick"
date: 2010-08-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xir_ on 2010-08-04
There has been a long standing problem with the Gui freezing under high IO which appears to have been fixed.

Here's a link to an article with more info: [http://www.phoronix.com/scan.php?page=news_item&px=ODQ3Mw]("http://www.phoronix.com/scan.php?page=news_item&px=ODQ3Mw")

here's a link to the patch itself: [http://lkml.org/lkml/2010/8/1/40]("http://lkml.org/lkml/2010/8/1/40")

Where do we start with getting this into maverick, even just as a backport?

---

### Post by gnomeuser on 2010-08-04
First order of business would be to produce a build of the kernel with these patches applied to confirm that it does indeed fix the performance issue but also to ensure that it does not cause any regressions.

---

### Post by Mr. Picklesworth on 2010-08-04
:O !

Okay, if that patch works, we need to start a pool and buy that man a reward. It is *THE* bug which has loomed over me for years.

It's amazing how things like this ultimately resolve to such small patches, too&#8230;

---

### Post by hikaricore on 2010-08-04
Yes!

---

### Post by gnomeuser on 2010-08-05
Latest updates indicates that this is insufficient at addressing the entire stalling issue. Also we still don't have any word on regressions caused by this.

Never the less Wu seems to be on the hunt so at least we have some progress. Of course the bug report is now nearly 500 comments and surely encompasses more than one bug so it is likely that Wu's patch actually does improve the situation for some cases.

[https://bugzilla.kernel.org/show_bug.cgi?id=12309](https://bugzilla.kernel.org/show_bug.cgi?id=12309)

---

### Post by xir_ on 2010-08-05
> **Mr. Picklesworth said:**
> :O !

Okay, if that patch works, we need to start a pool and buy that man a reward. It is *THE* bug which has loomed over me for years.

It's amazing how things like this ultimately resolve to such small patches, too&#8230;

Yea, I've already been looking to see if he had a webpage with a beer button.


I think that the patch set applies to the 35 kenrel, which is why i suggested maverick.  The question is how to make a quantitative analysis of this under maverick. For me this bug is killer when I start to push RAM. but I'm not sure how I would graph it.

Any suggestions?

edit i found this a suggestion on the bug tracker

> Hi ANdrew,

Very simple testing procedure:

Launch Firefox

Run  'stress -d 1'

Try open some websites

Machine hangs

Thanks

---

### Post by gnomeuser on 2010-08-05
All the low latency synchrounous lumpy reclaim patches have now been ACKed by several people, it is looking good for mainlining.

I asked on #ubuntu-kernel today if it was going into Maverick to provide more feedback but it sounded like there was a desire to wait for the debate to settle. As it now seem to have happened hopefully it can go into Maverick and be backported for Lucid.

[http://lkml.indiana.edu/hypermail/linux/kernel/1008.0/02107.html](http://lkml.indiana.edu/hypermail/linux/kernel/1008.0/02107.html)

---

### Post by xir_ on 2010-08-06
> **gnomeuser said:**
> All the low latency synchrounous lumpy reclaim patches have now been ACKed by several people, it is looking good for mainlining.

I asked on #ubuntu-kernel today if it was going into Maverick to provide more feedback but it sounded like there was a desire to wait for the debate to settle. As it now seem to have happened hopefully it can go into Maverick and be backported for Lucid.

[http://lkml.indiana.edu/hypermail/linux/kernel/1008.0/02107.html](http://lkml.indiana.edu/hypermail/linux/kernel/1008.0/02107.html)

Ahh i didn't think of #ubuntu-kernel, i did ask in ubuntu+1 without response.

phoronix used a couple of patches and has suggested the there is an improvement ([here]("http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ")). I think that they found an improvement with just two patched but haven't yet managed to apply the other 5.

But thanks for asking, if this patch set gets in it will make my life (and research) a lot easier.

---

### Post by psyke83 on 2010-08-06
I haven't tested any of the proposed patches, but I did take a look at the upstream bug report ([#12309]("https://bugzilla.kernel.org/show_bug.cgi?id=12309")).

I tried setting /proc/sys/vm/dirty_bytes to 8192 (comments #476, #477), and system stalling appears to be eliminated.

A simple test is to leave Firefox open, run "stress -d 1", and browse the internet normally.


[LIST]
[*] With the default settings (dirty_bytes = 0, dirty_ratio = 20), I experience a lot of stalling.
[*] With the proposed settings (dirty_bytes = 8192, dirty_ratio = 0), I experience very little stalling (or perhaps none at all).
[/LIST]
  
N.B. It appears that dirty_bytes and dirty_ratio are exclusive parameters; setting a value to one will clear/disable the other.

---

### Post by kj74 on 2010-08-09
> **psyke83 said:**
> I haven't tested any of the proposed patches, but I did take a look at the upstream bug report ([#12309]("https://bugzilla.kernel.org/show_bug.cgi?id=12309")).

I tried setting /proc/sys/vm/dirty_bytes to 8192 (comments #476, #477), and system stalling appears to be eliminated.

A simple test is to leave Firefox open, run "stress -d 1", and browse the internet normally.


[LIST]
[*] With the default settings (dirty_bytes = 0, dirty_ratio = 20), I experience a lot of stalling.
[*] With the proposed settings (dirty_bytes = 8192, dirty_ratio = 0), I experience very little stalling (or perhaps none at all).
[/LIST]
  
N.B. It appears that dirty_bytes and dirty_ratio are exclusive parameters; setting a value to one will clear/disable the other.

I tried the patch and it didn't help at all. Setting dirty_bytes = 8192 is much better solution. It might have side effects but at least it helps.

---

### Post by xir_ on 2010-08-09
> **kj74 said:**
> I tried the patch and it didn't help at all. Setting dirty_bytes = 8192 is much better solution. It might have side effects but at least it helps.

Did you apply all 7 patches?

---

### Post by kj74 on 2010-08-09
> **xir_ said:**
> Did you apply all 7 patches? 7? I didn't even know there is 7 patches. That is just crazy, i highly doubt anyone have actually tried them all. Everybody is talking about just one patch. If it takes 7 patches forget about backporting them to older kernels and let's just wait for maverick+1 and see what happens.

---

### Post by hexsel on 2010-08-09
> **kj74 said:**
> I tried the patch and it didn't help at all. Setting dirty_bytes = 8192 is much better solution. It might have side effects but at least it helps.

Wow, I tried this and it KILLED my system, to the point where I had to restart it repeatedly since I had no idea why it wasn't doing anything.  HTOP showed no CPU usage, but nothing started, and any access to the disk seemed deadlocked.  I had changed it in /etc/sysctl.conf, ended up having to wait for GDM on a subsequent reboot, switch to VT1 and manually change it back, rebooting again.

Apparently, not a very good setting in some systems...

---

### Post by psyke83 on 2010-08-09
> **hexsel said:**
> Wow, I tried this and it KILLED my system, to the point where I had to restart it repeatedly since I had no idea why it wasn't doing anything.  HTOP showed no CPU usage, but nothing started, and any access to the disk seemed deadlocked.  I had changed it in /etc/sysctl.conf, ended up having to wait for GDM on a subsequent reboot, switch to VT1 and manually change it back, rebooting again.

Apparently, not a very good setting in some systems...

Yes... further testing has confirmed the same for me. Another case: when updating the repository information, the "Reading package lists" stage is extremely slow. I have a feeling that the slowdown is caused specifically by the write operations (a low dirty_bytes value will kill write throughput).

---

### Post by hexsel on 2010-08-09
> **psyke83 said:**
> Yes... further testing has confirmed the same for me. Another case: when updating the repository information, the "Reading package lists" stage is extremely slow. I have a feeling that the slowdown is caused specifically by the write operations (a low dirty_bytes value will kill write throughput).

Yes, I agree (so does the bug the other posters pointed to).  I actually found out that lowering swappiness and dirty_ratio mostly fixed it for me, to maybe a small performance drop.  

An old legacy build for the software I work (hundreds of MB copied, filtered, etc) went from about 4m45s to 5m9s, but the streaming radio doesn't jitter anymore and I can still browse the web, a more than worthy trade-off.

To those interested, I have 4GB ram, 15GB swap, and set the following:
sudo sysctl vm.swappiness=20 (ubuntu default is 60)
sudo sysctl vm.dirty_ratio=5 (ubuntu default is 20 I think)

---

### Post by xir_ on 2010-08-10
> **kj74 said:**
> 7? I didn't even know there is 7 patches. That is just crazy, i highly doubt anyone have actually tried them all. Everybody is talking about just one patch. If it takes 7 patches forget about backporting them to older kernels and let's just wait for maverick+1 and see what happens.

There was originally one patch which had been improved and expanded, the others need backporting to the relevant kernels as far as i know. The was some work done in the phoronix forums getting the patched to work with .35 .

---

### Post by xir_ on 2010-08-27
looks like there are some new updates.

[http://www.phoronix.com/scan.php?page=news_item&px=ODU0OQ]("http://www.phoronix.com/scan.php?page=news_item&px=ODU0OQ")

last time i talk smack about Nokia.

---

