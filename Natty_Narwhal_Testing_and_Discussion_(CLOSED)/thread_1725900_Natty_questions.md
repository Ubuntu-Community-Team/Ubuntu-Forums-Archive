---
title: "Natty questions?"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VanR on 2011-04-10
A few Natty AMD 64-bit questions.

1. How much RAM will Natty support? Is there a limit like in Windows 32-bit? Thinking of adding 4 more gigs.

2. If my computer has 4 GB of RAM, how come Ubuntu 11.04 says I only have 3.9 GB?
And no, none of it is shared by the video. Or at least shouldn't be. I have a stand-alone Nvidia 512MB video card.

3. How come i now have 2 different versions of System Monitor?
1 is found under System>Administration>System Monitor
The other under Applications>System Tools>System Monitor

---

### Post by TomAnkcorn on 2011-04-10
the max it supports is 64gb of ram i think :)

---

### Post by fjgaude on 2011-04-10
> **VanR said:**
> A few Natty AMD 64-bit questions.

1. How much RAM will Natty support? Is there a limit like in Windows 32-bit? Thinking of adding 4 more gigs.

It handles as much as your motherboard handles.

2. If my computer has 4 GB of RAM, how come Ubuntu 11.04 says I only have 3.9 GB?
And no, none of it is shared by the video. Or at least shouldn't be. I have a stand-alone Nvidia 512MB video card.

That's close enough, depends on what kind of memory handler the motherboard uses, which chipset.

3. How come i now have 2 different versions of System Monitor?
1 is found under System>Administration>System Monitor
The other under Applications>System Tools>System Monitor

Gosh, I can't say... one is good as another?

Enjoy!

---

### Post by MAFoElffen on 2011-04-10
> **VanR said:**
>  If my computer has 4 GB of RAM, how come Ubuntu 11.04 says I only have 3.9 GB?

[COLOR=Red]And no, none of it is shared by the video.[/COLOR] Or at least shouldn't be. I have a stand-alone Nvidia 512MB video card.

I have 4GB onboard, 2 x nvidia bridged SLI's w/ 2GB video RAM between them ...and reports less than yours and has done such since 64bit versions of 9.04.

As it was explained to me when I asked about that, it was "how" video is addressed.  If I had only one card, it would report more memory address space available, since I have 2... It takes some more of the memory "space" to address the video.

That may be wrong now... but that is how it was explained to me back then and I just excepted it as how things worked.  MS Win Vista 64bit and Win7 Pro 64bit report the same memory available on this same box.  As an "Aside,"  I slam this box and I don't notice the "missing" memory "it" says is not there.

As was said by [fjgaude]("http://ubuntuforums.org/member.php?u=236865"), and it was also previously mentioned to me-- that if my mobo had a different chipset that addressed the memory differently, that it would be different for me... But that is something by me just researching more and getting another mobo just to address that purpose.

I forgot to mention-- I use overclocker's chips for memory.  Even though I don't overclock, the speed of the memory does seem to make a big difference. (and it's lifetime guaranteed) Just as the speed of the video cards (GPU's and Video RAM) does allot in the way of performance.

---

### Post by VanR on 2011-04-10
Well no biggie. Was just curious. Windows 7 reports the whole 4 GB, that's all. Chipset  is the Nvidia 6150SE/430. So it's an older chipset I'm sure. Just don't want to invest in 4 more gigs of RAM if I'll get no benefit from it with Ubuntu.

---

### Post by CaptainMark on 2011-04-10
64 bit rigs can handle waaaay more than 64gb of memory, its somewhere in the 1000's of gigabytes by design limitations, obviously your only real limitation is how much you can fit in your computer

and the reason for seeing 3.9gb is probably to do with the dual definitions of 1gb, it can be either 1000mb or (around) 1024mb depending on which notation is used by the program your running, so if your memory is 4000mb but your system thinks 4gb is 4098mb, it will report that your a little short of 4gb

edit: this sounds about right, done some quick sums, 1000/1024 = 0.9765,  0.9765 x 4000 = 3904mb

---

### Post by KegHead on 2011-04-10
Capt Mark

+1

Monitors  I checked both sources and it's the same monitor...go figure?

11.04b/classic/2.6.39-999

KegHead

---

### Post by Longinus00 on 2011-04-10
> **VanR said:**
> Well no biggie. Was just curious. Windows 7 reports the whole 4 GB, that's all. Chipset  is the Nvidia 6150SE/430. So it's an older chipset I'm sure. Just don't want to invest in 4 more gigs of RAM if I'll get no benefit from it with Ubuntu.

If you use 32bit Windows it'll report the full 4GB as well. Just because it says it's there doesn't mean you'll be able to use it.

---

