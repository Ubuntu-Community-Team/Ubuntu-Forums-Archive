---
title: "Linux-headers show as New In Repository"
date: 2010-12-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-12
Version 2.6.37-9
But not as upgrades in Synaptic! Is this normal?

---

### Post by ScislaC on 2010-12-12
Yes that is normal... after the meta-packages make it to your mirror it will show in upgrades. It shows as New because the name is different due to the revision number being part of the name. It's recommended to NOT manually mark these for install and wait until the proper files to upgrade are in place at which time these will be marked by the meta-packages.

---

### Post by Quackers on 2010-12-12
> **ScislaC said:**
> Yes that is normal... after the meta-packages make it to your mirror it will show in upgrades. It shows as New because the name is different due to the revision number being part of the name. It's recommended to NOT manually mark these for install and wait until the proper files to upgrade are in place at which time these will be marked by the meta-packages.
Thank you, I'll do just that :-)
In fact, after the disaster from 6 to 7 I think I'll wait a while :-)

---

### Post by autocrosser on 2010-12-12
I'm already running -9....working very nice here. If the truth be said, I really like being on the edge :)  (it really helps that I have multiple installs ;)  )......The Nvidia blob is working well with this one also.

If things break I can fix them---BRING ON THE BREAKAGE!!!!!!!

---

### Post by Quackers on 2010-12-12
What's a blob? :-)

---

### Post by autocrosser on 2010-12-12
> **Quackers said:**
> What's a blob? :-)

Binary code that is closed-source (Generally acknowledged as a bad thing---I need it to run my SLI system until Noveau can do it) :)

---

### Post by Quackers on 2010-12-12
Oh right! I thought it was a mysterious monster of the deep :-)

---

### Post by autocrosser on 2010-12-12
AHHH--- The Blobness monster of Six-mile deep (in THX 3D!!!)---in theatres Jan 1, 2011!!!!!!!  May the Blob be with you.......

---

### Post by ronacc on 2010-12-12
The Blob , really hokey 1950s horror flick . ( I saw it as a kid )

---

### Post by autocrosser on 2010-12-12
Ya---I remember it---was a VERY B- movie. How so many people could be absorbed be something that was 1~2 mph at best.......:D  (& looked like animated jello)

---

### Post by ronacc on 2010-12-12
the teenagers in that diner were too busy screaming to run :lolflag:

---

### Post by autocrosser on 2010-12-12
Wow---vision of screaming teens being engulfed by slime-green jello........:p:p:p

Burning question is how did this come out of a -9 kernel?????  Linus--please help us!!!!

(talk about threads gone astray....)

Must be alpha-testers stir0crazy with no BREAKAGE!!!!!!

---

### Post by kyleabaker on 2010-12-13
> **autocrosser said:**
> (talk about threads gone astray....)

Must be alpha-testers stir0crazy with no BREAKAGE!!!!!!

Bingo :P

---

### Post by Harry33 on 2010-12-13
> **ScislaC said:**
> Yes that is normal... after the meta-packages make it to your mirror it will show in upgrades. It shows as New because the name is different due to the revision number being part of the name. It's recommended to NOT manually mark these for install and wait until the proper files to upgrade are in place at which time these will be marked by the meta-packages.

Actually the new kernel subversion 2.6.37-9 (which is rc-5) has already been accepted and done (uploaded into repositories). The fact that there are not yet meta-packages around does not make these kernel packages a bit more unstable.
Meta-packages are only used to help beginners get necessary and also useful packages easily and automatically installed and updated.

I do not use meta-packages (like linux-generic, linux-headers-generic, linux-image-generic, ubuntu-desktop, ubuntu-standard etc.) because of the dependency-hell they create. I want to decide myself what applications I need.

As far as this rc-5 kernel is concerned it is already fine and installable:
linux-headers-2.6.37-9
linux-headers-2.6.37-9-generic
linux-image-2.6.37-9-generic

---

### Post by autocrosser on 2010-12-13
> **kyleabaker said:**
> bingo :p

lol!!!;)

---

### Post by ScislaC on 2010-12-13
> **Harry33 said:**
> The fact that there are not yet meta-packages around does not make these kernel packages a bit more unstable.
Meta-packages are only used to help beginners get necessary and also useful packages easily and automatically installed and updated.


Of course you can install them w/o the meta-packages. But if people are asking about the upgrade path for kernels while using an unstable distro, it's probably best that they ease into things to play it safe. I'm not saying I never jump the gun and install before the metas are available, but just trying to give "safe" advice to someone to help them avoid breakage and understand how the upgrade process works.

---

### Post by Quackers on 2010-12-13
Available in updates now :-)
Installed and running fine!

---

### Post by chrismine on 2010-12-13
And I thought I was clever by installing new header files manually, because nvidia and vbox drivers not installing!

This happened with previous kernel -8 too, I thought I have borked my system in some way, because my system wasn't working properly with earlier kernels so I removed them and I resigned myself to install new kernel's manually in future.

2.6.37-9 works fine on my PC.

---

### Post by Harry33 on 2010-12-13
> **ScislaC said:**
> Of course you can install them w/o the meta-packages. But if people are asking about the upgrade path for kernels while using an unstable distro, it's probably best that they ease into things to play it safe. I'm not saying I never jump the gun and install before the metas are available, but just trying to give "safe" advice to someone to help them avoid breakage and understand how the upgrade process works.

Meta packages do not make the actual kernel packages in any way safer.
The actual packages are in no way changed after they have been accepted and marked as "done". Note, that I was not talking about the "new" state.
It only takes time to wait for the upload and build of meta packages.

But using unstable dev state distro is not safe for beginners, so a safe advice is not to use them at all. Installation of new kernels is not at all unsafe, unless you go and delete the old versions completely.

But as I already said, meta packages are for beginners. Dev state distros are not.

---

### Post by seeker5528 on 2010-12-13
> **ronacc said:**
> The Blob , really hokey 1950s horror flick . ( I saw it as a kid )

There was a remake in 1988...

[http://www.imdb.com/title/tt0094761/](http://www.imdb.com/title/tt0094761/)

Later, Seeker

---

### Post by ronacc on 2010-12-13
> **seeker5528 said:**
> There was a remake in 1988...

[http://www.imdb.com/title/tt0094761/](http://www.imdb.com/title/tt0094761/)

Later, Seeker

yeah I saw when they remade it but that one I didn't bother to go to , mabye catch it one staurday on Elviras midnite horror flicks .:lolflag:

---

