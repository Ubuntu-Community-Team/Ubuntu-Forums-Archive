---
title: "The &quot;non-interactive&quot; boot revisited, MAYBE"
date: 2010-05-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-05-24
Sometime ago I posted this:

[http://ubuntuforums.org/showthread.php?t=1482615](http://ubuntuforums.org/showthread.php?t=1482615)

To deal with this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

Well, I'm finally getting things going on Ayatana. 

My original post:

> As I found out iso-testing prior to Lucid Beta 1 the Live CD now requires user interaction to display menu options:


[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)


At first this seemed fine but having used this more and more I find it to be only annoying. Consider the following:


1) It creates confusion for those who are new to Ubuntu. I've seen this a lot at the forums.


2) We've only moved the interactive part to a later point in the boot cycle because you still must choose whether to just "run" Ubuntu or install Ubuntu, so this really did not result in a faster boot.


3) With that "move" all we've done is "remove" the options to check CD for defects, adjust boot parameters, etc. without an otherwise unnecessary reboot which only results in frustration.


4) Even after learning of the new "boot behavior" the option to press any key passes so quickly that even an unplanned phone call or some other interruption can cause me to miss the opportunity, and increasing that "time out" would only increase the boot time.


I'm curious what others think about this. We could possibly plan changes for the first "point release" of Lucid and I'd think certainly for Maverick, and no time like the present ;^)

Then Mark Shuttleworth's response:

> Michael Forrest, cc'd, is the right person to chat with about the install CD experience. Michael, could you reply on-list for everyone's benefit?

Mark

I was patient, taking into consideration UDS and the "afterburn" and today this from Michael Forrest:

> There are two important reasons for this change.
1. To create a consistent look-and-feel across the entire Live CD / Installation experience
2. To distill the options presented to an Ubuntu newcomer down to the one real decision: 'Try Ubuntu' or 'Install Ubuntu'

Thanks
Michael

then my reply:

> Thank you for your reply Michael.

Regarding your reason #2: "To distill the options presented to an Ubuntu newcomer down to the one real decision: 'Try Ubuntu' or 'Install Ubuntu'", I have always felt, and therefore recommended, that the very first decision should be to "Check disc for defects".

Otherwise if the Live Desktop fails to run properly or, even worse, if an installation fails the first question I always ask is if the CD passed the integrity test. I'm unsure if you saw my original message so I'm pasting it below. I'd certainly appreciate it if you'd take a few minutes to review some of the more inflammatory recent posts at launchpad (I'm Erick Brunzell)

And so far only one comment:

> I don't think anyone would ever argue that we shouldn't be intergrity checking boot media (or at least presenting the option); while I never considered it a pain point, I guess I could see a new user getting confused and giving up. Maybe the solution is to have the FIRST menu a user sees be "boot or install", and *then* ask whether or not to check the cd for defects (before any booting or installing happens). That way, the user at least knows that the cd check is a normal part of the process; that they are on the right track.

Thoughts?

-- Alex



So .................. here's the deal/options:

#1) If you like the new non-interactive live boot do nothing.

#2) If you don't like it get involved like I did! Ayatana is less than "straight-forward" for us average end users, but IMO worth the effort.

#3) Create a new poll. (I personally don't like polls) 

#4) Do nothing and just complain!

Where do you stand?

---

### Post by ranch hand on 2010-05-24
Boy, you do ask the tough questions.

I think options 3 and 4 are probably the best way to go as they are easy and we know how to do them.

Besides, we need more DSPs (Damned Silly Polls).

---

### Post by kansasnoob on 2010-05-24
The problem with DSP's is they're often worded poorly, eg: which leg would you prefer to lose, and they hit too small of a fraction of the Ubuntu community.

Hey, I put a lot of effort into this. I realize not everyone agrees with me and that's cool.

But believe me, I'll do some "told you so" if someone complains about this feature not being changed, unless they get involved.

I think I've gone my extra mile on this one, now if we could get this fixed:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by dagrump on 2010-05-24
Do you mean they are resisting change from putrid purple w/ strange symbols intro, something the  uninformed won't understand, back to something straight forward. 
Yes, we must have a poll, A poll we must have. That or complain, a lot.
Okay, now I have that out of my system:)

I personally feel the first option presented should be the disk integrity check. I always want to check it, I hate getting part why thru an install & it fails to install.
The installer now doesn't feel noob friendly, but I don't see them reverting, to the old lay out. It seems to always be damn the torpedos & full speed ahead. I'll go subscribe to your bug & wish you luck. 
Also, what is the deal with installing grub on all partitions? I could of sworn that was what it offered as an option.
On second thought just everybody just disregard this, it's just that old mumbling fool grumbling in his yard.

---

### Post by ronacc on 2010-05-24
added a comment to the 2nd bug you reference . Why did they even bother to have the  install or try menu , the install icon is right there on the live desktop .

---

### Post by ranch hand on 2010-05-24
> **ronacc said:**
> added a comment to the 2nd bug you reference . Why did they even bother to have the  install or try menu , the install icon is right there on the live desktop .
Ha, beat me to it.

I am really getting sick of trying to enable folks to boot to an OS that I;
A>will not have in contact with my box
B>know little about and what little I know I would like to forget
C>think should be deleted from the poor saps box - end of problem

All this because they are DIRECTED to do this  to themselves.  It is hard to be civil when you think they deserved it but it is their box after all.

---

### Post by cariboo on 2010-05-25
I actually like the way the Live CD works, I very rarely check disk integrity, as I don't think I've ever burned a bad cd, about the only thing I do is check the md5sum. I've actually had more problems with Live usb devices.

---

### Post by 23meg on 2010-05-25
> **ronacc said:**
> added a comment to the 2nd bug you reference . Why did they even bother to have the  install or try menu , the install icon is right there on the live desktop .

The "Install" option takes you to a stripped down X session that's geared towards running the graphical installer only, whereas "Try" takes you to a full live session. The direct installation option enables the graphical installer to run on some older machines with less RAM that can't run the live session.

---

### Post by kansasnoob on 2010-05-26
Well, I'm actually getting some responses. IMHO the best thing is that SABDFL has not said, "there will be no change"! At least not yet :)

It's also obvious that Mark really does listen and care. That's pretty cool. Just watching him "connect" with people it becomes obvious why he's been so successful.

So we'll see how this goes. I think it's just awesome to know that even a dummy like me can garner this level of attention :)

---

