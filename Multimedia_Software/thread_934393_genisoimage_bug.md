---
title: "genisoimage bug"
date: 2008-09-30
forum: Multimedia Software
---

### Post by cotcot on 2008-09-30
I am not able to burn a video dvd that can play on a stand alone dvd player. As recommended in another thread here (january) i tried to install a more recent (1.1.8) version of genisoimage (that seems to cause the problem and is described in bugreports) and an earlier version (1.1.2). The earlier version had dependency problems. So I quit. The more recent version caused a broken package. I repaired this. But the result is the still the same. The dvd player (liteon) gives 'datadisk' or 'file' and does not load the video. My burner is NEC ND 3500AG. I tried several makes of dvd disks.
I tried the same on fedora9 with version 1.1.7 and that worked. 
Is there anybody who can burn dvd video in hardy that can play on stand alone players ? And if so what is the trick ? (changing to mkisofs ?)

---

### Post by prshah on 2008-09-30
> **cotcot said:**
> 
Is there anybody who can burn dvd video in hardy that can play on stand alone players ? And if so what is the trick ? (changing to mkisofs ?)

Are you bent on using command line tools? Then I can't help out; but otherwise I've had [great success with DeVeDe]("http://ubuntuforums.org/showthread.php?t=802542"). It's in the repos, and the finished disc works great on standalone (generic) DVD players.

---

### Post by cotcot on 2008-09-30
No I am not bent on command line tools. It does not matter as long as the result is fine.
Devede did not work in hardy (it did on fedora). Qdvdauthor neither. Kdenlive also does not work. (all same error 'datadisk' or 'file'.
Do you burn the dvd with devede or do you make the iso with devede and burn the iso with another app ? What is the genisoimage version you have installed ?

---

### Post by wetinwales on 2008-09-30
I'm using Tovid in Ubuntu 8.04 Ripping in Thoggen. Both on repositories.
Thoggen is slow but seems robust.
Tovid has been problematical but I now have it working with a slight sync error.
I'm burning to Phillips DVD+RW on a cheap LG DVD burner

Try Tovid.

Wetinwales

---

### Post by wetinwales on 2008-09-30
Sorry... the relevant answer is that Tovid is burning DVD which works on the most awkward DVD player I've ever met. It rejects most home and commercially burned DVDs It only plays imprinted movie DVDs (Shop DVDs)

But it plays Tovid burned DVDs with good picture quality.

Wetinwales

---

### Post by prshah on 2008-09-30
> **cotcot said:**
> 
Devede did not work in hardy (it did on fedora). 

Do you burn the dvd with devede or do you make the iso with devede and burn the iso with another app ? 

What is the genisoimage version you have installed ?

It works great for me, on Hardy.

I created the ISO, then used GnomeBaker to burn the ISO.
```

Wed Oct 01 01:30:44 temp:$ genisoimage --version
genisoimage 1.1.6 (Linux)
Wed Oct 01 07:34:45 temp:$ 

```

---

### Post by cotcot on 2008-10-04
> **wetinwales said:**
> Sorry... the relevant answer is that Tovid is burning DVD which works on the most awkward DVD player I've ever met. It rejects most home and commercially burned DVDs It only plays imprinted movie DVDs (Shop DVDs)

But it plays Tovid burned DVDs with good picture quality.

Wetinwales

I tried Tovid. Same result. Tovid under hardy fails. Tovid under Fedora is ok.

---

### Post by cotcot on 2008-10-04
[SOLVED]
I tried other suggestions from the bug report.
Installing genisoimage 1.1.6.3 with the .deb from Gutsy solved the problem. Devede was not installable from the repos because it wanted to reinstall genisoimage as well. So I installed it with the tarball from the website of devede.

---

