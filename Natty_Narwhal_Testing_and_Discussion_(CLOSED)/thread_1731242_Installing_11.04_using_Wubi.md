---
title: "Installing 11.04 using Wubi"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hybridtheoryb4 on 2011-04-16
I have a hp pavillion dv63010-us and i am trying to install 11.04 within win7 using wubi but ever time i start ubuntu up after installing using wubi it trys to finish off installation and when it gets close to the end it says no root file system is defined please fix this in the partition menu. I have tried both installing from a disc and straight from the iso image. I shrink my windows partition so i  can create a seperate ntfs partition to install it on. i have try just running demo from disc and it runs fine so idk what im doing wrong. My best friend installed it the same way on his desktop without this problem.

---

### Post by sports fan Matt on 2011-04-16
11.04 is a pre-release..I Would not install it, I's go for 10.10 or 10.04 first.

I have never tried wubi.. I'm not sure why people seem to try it rather then taking the "try before you install option" from the cd

---

### Post by hybridtheoryb4 on 2011-04-16
i did try it from cd and i know it is not a final release but the try from cd worked fine so i dont see why im having a problem

---

### Post by idoitprone on 2011-04-16
> **sox fan Matt said:**
> 11.04 is a pre-release..I Would not install it, I's go for 10.10 or 10.04 first.

I have never tried wubi.. I'm not sure why people seem to try it rather then taking the "try before you install option" from the cd


Performance?

---

### Post by hybridtheoryb4 on 2011-04-16
also it is 64 bit version

---

### Post by Elfy on 2011-04-18
moved to natty.

---

### Post by bcbc on 2011-04-18
I've been using natty wubi for a while. It's pretty stable. 

The problem you are finding is likely due to:
1. ntfs issues. Running chkdsk and defragment
2. presence of leftover fakeraid metadata, or some unsupported raid configuration
3. leftover GPT partition table information mixed with an active MBR partition table that Ubiquity doesn't like.

You can rule out the first one if the normal dual boot install failed. This is not likely a problem with ntfs.
For 2 and 3, boot the live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").Usually it gives some good clues.

You can also try installing Maverick and see if it's a Natty issue.

As mentioned before - natty is in beta. So don't use it on production computers.

---

