---
title: "Where is Unity (in Natty)?"
date: 2011-03-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aisajib on 2011-03-08
I downloaded Ubuntu Natty Narwhal 11.04 Alpha 3 as soon as it was released on Thursday. Yesterday, I tried it on VM Virtual Box. I installed it; but I couldn't find the so-discussed Unity interface (which was the only reason I downloaded the ISO at this early stage of development).

Can anyone tell me how to access the Unity interface in my downloaded Ubuntu 11.04 Alpha 3 ISO?

---

### Post by kerry_s on 2011-03-08
unity requires 3d video acceleration, do you have that in vm ?

if not it defaults to 2d.

---

### Post by Hedgehog1 on 2011-03-08
It's a little tricky, but doable.

1st - Your real hardware must have a 3D graphics card that compiz works with.

2nd, In your 'Display' section (when the virtual machine is not running) the 3D acceleration must be on, and 128 meg allocated to video.

3rd, Run Natty and login.

4th, From the 'Devices' menu on the running Virtual Machine, select 'guest additions'.  This puts an 'iso' in the virtual CD drive

5th, From the 'places' menu, select the CD and run the guest additions. It will install.

6th, From synaptics package manager, search for Unity and check and install unity.  It will be a partial install, that is OK.

7th, reboot natty.  You should be in unity now.

This is this hard because Vbox is just recently begun to support 3D acceleration for Linux Guest OSes

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-08
I should mention that the above requires running Vbox 4.0.4 or higher if Linux/Ubuntu is your host OS.

Here are pictures of Natty running in Vbox on my Ubuntu 10.10 host:

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/2788889.png?872[/IMG]

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/8211882.png?872[/IMG]

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/4778712.png?872[/IMG]

***The Hedge***

:KS

---

### Post by aisajib on 2011-03-09
To everyone above:

I have turned 3D acceleration on on my VM. It's still not there.

Let's talk about my desktop (Live CD or Fresh Install), why will I still have to install Unity while it was supposed to be the default and new interface for Ubuntu? If 3D does not support, why it rolls back to gnome? I mean, I'm okay if certain compiz effects don't work (although I see all the compiz effects are working in my Maverick Meerkat), but what I'm seeing (the panel in the bottom) is not unity at all, not even the 2D one.


I'm lost. Anyone clarify it to me please?

---

### Post by Hedgehog1 on 2011-03-09
> **aisajib said:**
> To everyone above:

I have turned 3D acceleration on on my VM. It's still not there.

Let's talk about my desktop (Live CD or Fresh Install), why will I still have to install Unity while it was supposed to be the default and new interface for Ubuntu? If 3D does not support, why it rolls back to gnome? I mean, I'm okay if certain compiz effects don't work (although I see all the compiz effects are working in my Maverick Meerkat), but what I'm seeing (the panel in the bottom) is not unity at all, not even the 2D one.


I'm lost. Anyone clarify it to me please?

*The issue is _not_ the Natty install.*

The issue is that 3D acceleration is **VERY** new to Virtual Box.  That is where the problem lies.

Install Natty A3 on a real box, and you are up and running in Unity, easy peasy.

But in Vbox it still takes fiddling for 3D to work.  It started working in 4.0.2, and we are now in 4.0.4.  3D has been available in Vbox for about 6 weeks.  The 3D support in Vbox is considered 'experimental'.  The partial support of 3D in Vbox fools the natty installer.

Natty is fine.

***The Hedge***

---

### Post by kerry_s on 2011-03-09
> but what I'm seeing (the panel in the bottom) is not unity at all, not even the 2D one.

that is the fall back, straight gnome with the 2 panels & the single menu in the top left corner.

if your thinking about the qt 2d unity, it's not included in natty 11.04.

---

### Post by aisajib on 2011-03-09
> **Hedgehog1 said:**
> [SIZE=4]*The issue is _not_ the Natty install.*[/SIZE]

The issue is that 3D acceleration is **VERY** new to Virtual Box.  That is where the problem lies.

Install Natty A3 on a real box, and you are up and running in Unity, easy peasy.

But in Vbox it still takes fiddling for 3D to work.  It started working in 4.0.2, and we are now in 4.0.4.  3D has been available in Vbox for about 6 weeks.  The 3D support in Vbox is considered 'experimental'.  The partial support of 3D in Vbox fools the natty installer.

Natty is fine.

***The Hedge***


I was talking about my desktop, this time not virtual box. When I load from live CD, does not seem to be working on Unity interface (the panel on left).


> **kerry_s said:**
> that is the fall back, straight gnome with the 2 panels & the single menu in the top left corner.

if your thinking about the qt 2d unity, it's not included in natty 11.04.


Um, what is qt? That left side panel?

---

### Post by uRock on 2011-03-09
Moved to NNT&D.

---

### Post by aisajib on 2011-03-09
> **uRock said:**
> Moved to NNT&D.

Thanks. Did not find that forum when posting.

By the way, I was wondering why you are still with 9.10 :D :o:o

---

### Post by kerry_s on 2011-03-09
> Um, what is qt? That left side panel?


there's actually 3 versions of unity.
in ubuntu 10.10 unity was built using mutter.
in 11.04 the standard version is built using compiz.
there is also a 2d version built using qt, kde's main library.
i'm going to point you to youtube to see it in action:

[http://www.youtube.com/results?search_query=ubuntu+unity+qt&aq=f](http://www.youtube.com/results?search_query=ubuntu+unity+qt&aq=f)

---

### Post by oregonbob on 2011-03-09
Thanks Hedgehog. I've been running Natty on VirtualBox 4.0.4 for several days and didn't know what I was missing. All I did was checkbox 3D. When I reboot it came up with the new Unity menu. The first reboot hung and reported errors running compiz, then the second reboot came up fine.

---

### Post by zenwalker on 2011-03-09
Yes me to having problem with natty on Vbox 4.0.4 here over Xp host.

---

### Post by aisajib on 2011-03-09
> **kerry_s said:**
> there's actually 3 versions of unity.
in ubuntu 10.10 unity was built using mutter.
in 11.04 the standard version is built using compiz.
there is also a 2d version built using qt, kde's main library.
i'm going to point you to youtube to see it in action:

[http://www.youtube.com/results?search_query=ubuntu+unity+qt&aq=f](http://www.youtube.com/results?search_query=ubuntu+unity+qt&aq=f)


Now I kind of understand it. How do I get 2D working on my machine?

---

### Post by Hedgehog1 on 2011-03-09
> **aisajib said:**
> I was talking about my desktop, this time not virtual box. When I load from live CD, does not seem to be working on Unity interface (the panel on left).

Ahh - sorry about the confusion on that.

Unity requires compiz.  The LiveCD Natty is using during the development phase is a modified 10.10 without compiz.  The development priority is the release at the moment.

I don't know if a liveCD with functioning Compiz will make it out with 11.04, or if we will not see it until 11.10.

***The Hedge***

:KS

---

### Post by kerry_s on 2011-03-09
> **aisajib said:**
> Now I kind of understand it. How do I get 2D working on my machine?

it's in the repo, but the last time i tried it, it was very bad.

---

### Post by Hedgehog1 on 2011-03-09
> **oregonbob said:**
> Thanks Hedgehog. I've been running Natty on VirtualBox 4.0.4 for several days and didn't know what I was missing. All I did was checkbox 3D. When I reboot it came up with the new Unity menu. The first reboot hung and reported errors running compiz, then the second reboot came up fine.

Glad you are working in Unity now, OregonBob!

Hey - where are you located?  Am I allowed guess? :D

---

### Post by aisajib on 2011-03-09
Thanks everyone. I think I now get it. I still love Ubuntu 10.04 LTS. :D Honestly.

---

### Post by QwUo173Hy on 2011-03-10
This explains how to get Unity 3D working on virtualbox:

[http://www.youtube.com/watch?v=Ukvlzyr81Wk](http://www.youtube.com/watch?v=Ukvlzyr81Wk)

---

### Post by aisajib on 2011-03-10
> **jarlath said:**
> This explains how to get Unity 3D working on virtualbox:

[http://www.youtube.com/watch?v=Ukvlzyr81Wk](http://www.youtube.com/watch?v=Ukvlzyr81Wk)


Thanks for the link. :)

---

