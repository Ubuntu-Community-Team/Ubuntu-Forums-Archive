---
title: "Writing .ISO to CD Freezes / Crashes Entire System"
date: 2008-10-21
forum: Multimedia Software
---

### Post by jrg3 on 2008-10-21
First, I'm using Hardy Heron.

Second, the .iso's I'm trying to burn are the newest Kubuntu and Xubuntu Live Disc distros.

Third, quick preface: For weeks I've been having several problems with two different machines regarding CD/DVD ROM's and I've searched for the answers daily - obviously to no avail. I'll start with the first machine because it seems to be the easiest of the problems to solve (in theory).

Ok.

I can read discs just fine but when I try to write the .iso's my system completely freezes. 

I've tried:

[LIST]
[*]Right-clicking (Write To Disc)
[*]From command line (wodim)
[*]Brasero (Burn Image)
[*]K3b (Burn CD Image)
[/LIST]

All have the same result, except K3b which shows me the point it seems to be freezing at: the CUE file.

Any ideas?

---

### Post by mocha on 2008-10-22
Sounds like a hardware fault, memory fault, IDE controller fault, etc.  Are you overclocking?  Could also be an interrupt issue.  In my expereince Linux doesn't hard lock unless there is a hardware problem.  Overclocking stresses components and will cause hard locks when the stressed components are heavily utilized.

---

### Post by jrg3 on 2008-10-28
semi-solved.

Hardware issue.

Being I only had one cdrom on that machine, removing the jumper seemed to fix the problem.

Although now my bios reads it as a slave.

But, it burns just fine so I'm cool with that.

I'm going to call this solved because it's clearly not Ubuntu related.

---

