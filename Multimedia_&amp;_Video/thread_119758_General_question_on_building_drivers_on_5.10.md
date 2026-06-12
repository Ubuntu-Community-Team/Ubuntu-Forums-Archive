---
title: "General question on building drivers on 5.10"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by rps63ifid on 2006-01-20
In a separate thread (see [http://ubuntuforums.org/showthread.php?t=77864](http://ubuntuforums.org/showthread.php?t=77864)) related specifically to getting a Matrox driver to work with my P650 video card, I posted some information on problems that I was having in getting the Matrox driver compiled for use with 5.10. That thread is a couple months old and languishing, but based on other events, finding a solution to that problem is a little more important to me.

In doing some poking around on the forums, I came across a couple of postings that lead me to believe that in 5.10, the kernel itself is built using gcc3.4 while most (all?) of the applications are built using gcc4.

Questions:
1) Is that true?
2) Probably more important, if true, is whether that means I should be using gcc3.4 to build the Matrox video driver module for use by the kernel?

If someone with more knowledge on this would be willing to share, this seems like it could be at least one step toward getting the Matrox driver I need to run the P650 dual-headed again (I previously had it working flawlessly under 5.04). I won't be back at the system with that card until Monday morning to try anything, but would really like to make some progress on getting this problem solved.

Thanks in advance!

---

### Post by MartinG on 2006-01-20
[QUOTE=rps63ifid]In doing some poking around on the forums, I came across a couple of postings that lead me to believe that in 5.10, the kernel itself is built using gcc3.4 while most (all?) of the applications are built using gcc4.

Questions:
1) Is that true?
2) Probably more important, if true, is whether that means I should be using gcc3.4 to build the Matrox video driver module for use by the kernel?

If someone with more knowledge on this would be willing to share, this seems like it could be at least one step toward getting the Matrox driver I need to run the P650 dual-headed again (I previously had it working flawlessly under 5.04). I won't be back at the system with that card until Monday morning to try anything, but would really like to make some progress on getting this problem solved.

Thanks in advance![/QUOTE]Yes to both your questions. I would have expected the build script (or whatever) to have complained about the wrong compiler, so I'm slightly surprised you got as far as you did:) 

I see from the other thread that you installed make directly.  It's generally regarded as a good idea to install the whole suite of compiling tools that the ubuntu team have labelled "build-essential" (sudo apt-get install build-essential).  This includes other things besides make, though you may well have them all installed already, in fact.

Once you've installed gcc-3.4, I'm sure you know you need to run the following just before you begin your compiling;```
export CC=gcc-3.4
```

---

### Post by rps63ifid on 2006-01-20
Martin,

Thanks for the quick response. In looking back through the output stream I saved, the installation script did indeed complain about not being able to find gcc3.4, but I either assumed at the time that, as the script kept going, that wasn't going to be a show-stopper OR (more likely) I just didn't see the complaint about the compiler version. So, thanks for the confirmation on that...

... and thanks for the pointer on how to define which version of the compiler I wish to use. I had seen other threads indicating that it wasn't an issue to have both gcc4 and gcc3.4 installed side-by-side, but that was indeed a question I would have had to track down an answer to.

I just yesterday came across a reference to the 'build-essentials' package, as well, when I was pulling an entirely different (but related, as it turns out) thread. So, thanks for the pointer to that, too!

Come Monday morning, I will continue down the path of getting the driver functional again.

Do I remember seeing somewhere that the differing compiler versions (kernel vs. applications) will no longer be an issue when have all migrated to the next version?

Thanks again for your help! Just one more instance where this community has proven invaluable...

-- 
Ron

---

### Post by MartinG on 2006-01-20
[QUOTE=rps63ifid]Do I remember seeing somewhere that the differing compiler versions (kernel vs. applications) will no longer be an issue when have all migrated to the next version?[/QUOTE]Yes, you're quite right.  Apparently the maintainers just did not have enough time to recompile the kernel using gcc-4, which they used for everything(?) else. So rather than delay the release date (one of the Ubuntu team's commitments) they issued it as we have it.

Dapper Drake (6.04), which I have on a VMWare installation alongside Breezy, uses gcc-4 all through.

All the best for Monday, I *hope* we've covered everything!

---

