---
title: "Rename i386 to i686?"
date: 2010-07-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-07-07
Hi,
since 32 bit Ubuntu 10.10 and later compiles for i686 and above would it be better to rename the i386 token with i686 where it makes sense, for example in the name of the daily builds of Ubuntu at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
I think Fedora and other folks already do so.

---

### Post by endotherm on 2010-07-07
far more people are comfortable with i386 vs x64 than they are with x386/x586/x686 vs x64. for a long time I thought i686's were 64bit since all the intel chips were still "Pentium" implying i586. 

if the name is all that is important, make it meaningful to the widest possible audience.

---

### Post by kahumba on 2010-07-07
I just mean that it's already **wrong** to call it i386 since those builds will run on at least i686, hence it won't run on hw that is not compliant with i686. In other words we're not in Kansas any more.

---

### Post by MacUntu on 2010-07-07
AFAIK i386 is used to express x86/IA-32, so i686 really wouldn't make any sense in that context.

---

### Post by Longinus00 on 2010-07-07
i386 and i686 are options specifying the ABI and available instructions to compile for, they are not just "names".

[http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/i386-and-x86-64-Options.html](http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/i386-and-x86-64-Options.html)

---

### Post by endotherm on 2010-07-07
> **Longinus00 said:**
> i386 and i686 are options specifying the ABI and available instructions to compile for, they are not just "names".

[http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/i386-and-x86-64-Options.html](http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/i386-and-x86-64-Options.html)
very true, but that is under the hood, and already done as I understand it. if you are talking about the name of the file the user downloads however, it is just a name, and recognizably is kind of important.  but that is just my opinion.

---

### Post by mcduck on 2010-07-09
I'd say "i686" would be definitely a wrong name, since Ubuntu is easily able to run on i586/K6 machines. (I've never tried it on i486, so I can't say anything about that).

"x86" would of course be appropriate, if calling it with the familiar "i386" doesn't feel right.

---

### Post by artir on 2010-07-09
> **mcduck said:**
> I'd say "i686" would be definitely a wrong name, since Ubuntu is easily able to run on i586/K6 machines. (I've never tried it on i486, so I can't say anything about that).

"x86" would of course be appropriate, if calling it with the familiar "i386" doesn't feel right.

Wrong.
Ubuntu *was* able to run on i586 and older machines, but now, Maverick only supports i686 and newer. (Suposedly this provides better performance)

---

### Post by Starks on 2010-07-09
I approve of any potential renaming.

32-bit or x86 should always be presented to end-users but technical things like package names or the cdimage page should use i686.

---

### Post by mcduck on 2010-07-09
> **artir said:**
> Wrong.
Ubuntu *was* able to run on i586 and older machines, but now, Maverick only supports i686 and newer. (Suposedly this provides better performance)

No more support for i586? That's sad, I guess I'll have to start looking for another distro for my older machines then. :/

It's even more sad considering that 10.04 runs just great on my old K7 machine. Dropping support for machines that otherwise would be perfectly capable of running the OS isn't very cool thing to do in my opinion.

..not to forget how many times the developers, when talking about optimization, said that compiling for i686 doesn't provide any noticeable performance benefits over compiling for i586.. I guess they changed their mind about that, then. :D

---

### Post by MacUntu on 2010-07-09
I really doubt that i686-optimized binaries won't run on K7 machines. ;)

---

### Post by lisati on 2010-07-09
I highly doubt that changing the name would be appropriate, unless that it was actually compiled for a '686 or better. If it's written and compiled in a way that allows it to run on a '386, then 386 would be more appropriate.

Not all CPUs are created equal. I've already posted elsewhere in the forums about how unwarranted assumptions about what a cpu can do can cause problems - I had to learn the hard way by having to recover from massive data corruption on someone else's machine caused by a seemingly trivial mistake.

---

### Post by Longinus00 on 2010-07-10
> **lisati said:**
> I highly doubt that changing the name would be appropriate, unless that it was actually compiled for a '686 or better.

Please read the original post.

---

### Post by cascade9 on 2010-07-10
> **kahumba said:**
> Hi,
since 32 bit Ubuntu 10.10 and later compiles for i686 and above would it be better to rename the i386 token with i686 where it makes sense, for example in the name of the daily builds of Ubuntu at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
I think Fedora and other folks already do so.

AFAIK, ubuntu will still compile fine on a i386/i486/i586. The reason why Fedora, Arch, etc have changed to i686 is that is the minimum CPU required to run them. 

> **artir said:**
> Wrong.
Ubuntu *was* able to run on i586 and older machines, but now, Maverick only supports i686 and newer. (Suposedly this provides better performance)

I'd like to see your source for that....as far as I can see, the 32bit .isos are still i386- 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I doubt they will change from an i386 base, as that is what debian uses. 

> **mcduck said:**
> No more support for i586? That's sad, I guess I'll have to start looking for another distro for my older machines then. :/

It's even more sad considering that 10.04 runs just great on my old K7 machine. Dropping support for machines that otherwise would be perfectly capable of running the OS isn't very cool thing to do in my opinion.

..not to forget how many times the developers, when talking about optimization, said that compiling for i686 doesn't provide any noticeable performance benefits over compiling for i586.. I guess they changed their mind about that, then. :D

Like I said above, i386 is still the base, so it should still run on i386/i486/i586 machines. Sure, they wont ever have the recommended minimum RAM, or the 1GHz CPU for ubuntu 10.04. 

Even if they did move to a i686 base, K7 will still be fine. 

Pentium/Pentium MMX, K5, K6, K6-2, K6-3 = i586
Pentium Pro, Pentium II, Pentium III, Athlon (K7) = i686

Much to my amusment, cyrix 6x86 is sort of i586..but identifies itself as i486 :lolflag:

---

### Post by MacUntu on 2010-07-10
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-686-compile](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-686-compile)

hmm

---

### Post by kahping on 2010-07-10
Just the RAM requirements alone means that those old processors won't be on machines with enough memory to run Ubuntu anyway. 

Besides, I thought currently Ubuntu is optimised for i486 but still runs on i386? So now they're simply optimising for i686 or better which is what most PCs nowadays are, but it'll still run on i386/i486/i586, isn't it?

Update: Nvm, my mistake: [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/587186/comments/7](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/587186/comments/7)

---

### Post by MacUntu on 2010-07-10
> **kahping said:**
> RAM requirements
I guess the lack of CPU power alone makes it unlikely that anyone actually WANTS to run it on such old machines. I ran Xubuntu Hardy on a PIII 500MHz with 512MB RAM and it sucked really big time.

---

### Post by ranch hand on 2010-07-10
> **MacUntu said:**
> I guess the lack of CPU power alone makes it unlikely that anyone actually WANTS to run it on such old machines. I ran Xubuntu Hardy on a PIII 500MHz with 512MB RAM and it sucked really big time.

There  are times.

I am setting up just such a box for my step daughter right now.  She needs a computer and can't afford one.  We can't afford to buy one for her.

Xubuntu has never been that great on old hardware that I have found.  I think she is going to end up with Lubuntu on it.  Right now I have 9.04 on and it runs alright but it is slow.

---

### Post by cariboo on 2010-07-10
I just did an install using the mini.iso to do a cli install, then added the Lubuntu desktop on a 1.8Ghz Celeron with 128Mb ram, I'm surprised how well it runs considering the hardware. It does run better now then it did with XP on it.

---

### Post by kahping on 2010-07-10
> **cariboo907 said:**
> I just did an install using the mini.iso to do a cli install, then added the Lubuntu desktop on a 1.8Ghz Celeron with 128Mb ram, I'm surprised how well it runs considering the hardware. It does run better now then it did with XP on it.

That's simply amazing cariboo :D

Looks good too though I don't much like the Window-ish look myself

---

### Post by lisati on 2010-07-10
> **Longinus00 said:**
> Please read the original post.
Please don't make unwarranted assumptions. I stand by my assertion that labeling something that works on a 386 as 686 is inappropriate.

---

### Post by seeker5528 on 2010-07-10
> **kahumba said:**
> Hi,
since 32 bit Ubuntu 10.10 and later compiles for i686 and above would it be better to rename the i386 token with i686 where it makes sense, for example in the name of the daily builds of Ubuntu at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
I think Fedora and other folks already do so.

Packages are offered by architecture, based on the architecture you have installed.

The end result of providing newer i386 packages that are actually optimized for i686 and upgrading to those might technically be the same as offering i686 architecture packages and upgrading from i386 to i686, but since there is only one x86 architecture supported it's probably more trouble than it's worth to change the identified architecture. If people are installing on hardware that doesn't meet the listed minimum requirement, there is not really a lot of room for complaint if they find out it doesn't work. 

If there had previously been i386 and i686 architecture packages available and they wanted to force everyone over to i686 so they could drop i386, then that would be a different story.

Later, Seeker

---

### Post by krazyd on 2010-07-11
> **lisati said:**
> Please don't make unwarranted assumptions. I stand by my assertion that labeling something that works on a 386 as 686 is inappropriate.

The whole point of this thread is that, **as of 10.10, standard ubuntu packages won't work on i386** - they are being compiled specifically for i686:

> as discussed at UDS we are dropping support for anything older than i686 for maverick.
[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/587186/comments/7](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/587186/comments/7)

I hope this is communicated more widely than it has been thus far, because dropping architecture support is a pretty major change which shouldn't be made lightly.

---

### Post by scheuri on 2010-07-12
> **krazyd said:**
> The whole point of this thread is that, **as of 10.10, standard ubuntu packages won't work on i386** - they are being compiled specifically for i686:


[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/587186/comments/7](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/587186/comments/7)

I hope this is communicated more widely than it has been thus far, because dropping architecture support is a pretty major change which shouldn't be made lightly.

If that is the case (and it appears to be) then packages must not be labled with i386, because that would be utterly wrong (the assumption could be made that i386 are still supported while they are not anymore).

So, while I agree that in some graphical package tool there is no need to show i386 or i686, it still has to in dpkg and maybe even aptitude. Surely the whole 32bit and 64bit thing has to show up in the package tool...

Than again...Ubuntu is not dropping the support for i386 per se.
As long as 10.04 is supported, i386 is supported as well. You just can not use any newer version of Ubuntu on your machine lower than i686. 

cheers
scheuri

---

