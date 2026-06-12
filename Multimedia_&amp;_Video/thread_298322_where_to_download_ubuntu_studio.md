---
title: "where to download ubuntu studio?"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by egoldtech on 2006-11-12
where to download ubuntu studio?
or is a concept?
and I have to create it, installing ubuntu, and then each application??

---

### Post by nalmeth on 2006-11-12
It was formerly just a wiki, it is now a concept, to be a distro by time of Feisty's release.
The official website is [http://ubuntustudio.org/](http://ubuntustudio.org/)
but it only leads to the ubuntustudio project page, which then links to:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
For now, thats where you'll find instructions on setting up a studio environment, including recommended apps, configuration tips, links to manuals etc

Here's the StudioPreparation link, found on the Sound wiki:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[ ]("https://help.ubuntu.com/community/Sound")

---

### Post by marker4x4 on 2006-11-13
I can't seem t obe able to install the following packages:

mark@mark:~$ sudo apt-get install ardour-gtk hydrogen jackd jackeq jack-rack jamin qjackctl qsynth seq24 vkeybd zynaddsubfx

Password:*********

Reading package lists... Done

Building dependency tree... Done

E: Couldn't find package ardour-gtk

mark@mark:~$

What gives? I've installed the same things just few weeks ago on my other desktop... this is my laptop; I was hoping to get portable music studio!
Any help will be appreciated. Thanks,
-mark

---

### Post by Sef on 2006-11-13
Could be you need to [enable]("https://help.ubuntu.com/community/Repositories/Ubuntu") the repositories for access to multiverse or universe.

---

### Post by MetalMusicAddict on 2006-11-13
marker4x4. If you follow the [http://ubuntustudio.org/](http://ubuntustudio.org/) link there are details about our repo and metapackages we set up.

Look [HERE]("https://wiki.ubuntu.com/UbuntuStudio#head-b0184357fd100c228e325b824648047407122b68"). This is based off of Edgy. There are bugs in individual packages that will cause problems. It isnt the metas.

We are currently working on fixing simple bugs and looking toward feisty. We should have a base disk (OS only. no apps) to test based off of Edgy soon and a Feisty disk when they release a beta.

More info in the coming weeks.

-Cory

---

### Post by marker4x4 on 2006-11-15
> **Sef said:**
> Could be you need to [enable]("https://help.ubuntu.com/community/Repositories/Ubuntu") the repositories for access to multiverse or universe.

That's it! Geez, it's been a looooong time since I've been UNIX'ing :) :) :) 

But it's all coming back to me; slowly but surely. Thanks for the help, I'll let you know how it worked.

-mark

---

