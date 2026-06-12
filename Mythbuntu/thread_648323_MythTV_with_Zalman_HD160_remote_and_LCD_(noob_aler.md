---
title: "MythTV with Zalman HD160 remote and LCD (noob alert)"
date: 2007-12-23
forum: Mythbuntu
---

### Post by Danbc on 2007-12-23
Hey all

Well, hardcore MS fanatic finally  went to the dark side to see what the hype was about, and I must admit I´m fairly impressed :D

Generelly I have no problem getting everything to work as I want with help from the different forumposts etc I can find around the net, but 2 problems I just can´t get to work and it´s SO annoying :(

Anyways, I have thrown the MC in a Zalman HD160 casing wich both has a front LCD thingy and a remote. I´ve installed Mythbuntu and have tried several times to set the remote in the control panel where I´m told the remote should work with the "old MS MCE remote" setting should work, but no dice :(

Everything else is working sweet!

So does anyone has a completely noob guide how to get my remote to work because it´s quite annoying it doesn´t work, and generally the features on MythBuntu and the load time are so nice that I would rather not go back to MS MCE, but using the remote is sorta "mission critical".

Please, if anyone knows about this, keep it simple because I have not passed the "copy/paste" barrier on this Linux stuff yet :D  (And yes I have tried searching forums and have tried several "guides" on the subject, but couldn´t find anything that worked :( )

---

### Post by straightv6 on 2007-12-24
Have you tried this [http://ubuntuforums.org/showthread.php?t=304807&highlight=hd160](http://ubuntuforums.org/showthread.php?t=304807&highlight=hd160)

---

### Post by Danbc on 2007-12-25
Yeah tried that also, it gives me this error on the initial error line:

E: Couldn't find package ia32-libs

And then it sorta goes on with errors from that point, I guess the guide is good for Ubuntu, but not maybe for MythBuntu?

---

### Post by superm1 on 2007-12-25
> **Danbc said:**
> Yeah tried that also, it gives me this error on the initial error line:

E: Couldn't find package ia32-libs

And then it sorta goes on with errors from that point, I guess the guide is good for Ubuntu, but not maybe for MythBuntu?
Any *gutsy* guides usable for ubuntu will be fine on mythbuntu.  Remember that all of the mythbuntu packages (except the theme) are available on the gutsy repositories.  That guide is just for an old ubuntu release (edgy I think it was).

---

### Post by Danbc on 2007-12-25
> note: all the commands below are for Debian based distro

So Ubuntu is Debian based and all Debian guides should work for Ubuntu and related or am I totally off track?

---

### Post by superm1 on 2007-12-25
> **Danbc said:**
> So Ubuntu is Debian based and all Debian guides should work for Ubuntu and related or am I totally off track?
Normally commands can work across different releases.  I can tell you that there have been some fairly significant library changes across edgy,feisty,and gutsy with changing library package names, as well as changes in the functionality of such packages.

Some time back someone did bring up that irtrans stuff however.  If your zalman hd160 needs to use that, then it WONT work with the MS MCE remote (unfortunately).  That is a different IR software suite that doesn't mix and match with lirc well.

Sorry that's about all I can comment on it though.

---

### Post by straightv6 on 2007-12-26
> **superm1 said:**
> Normally commands can work across different releases.  I can tell you that there have been some fairly significant library changes across edgy,feisty,and gutsy with changing library package names, as well as changes in the functionality of such packages.

Some time back someone did bring up that irtrans stuff however.  If your zalman hd160 needs to use that, then it WONT work with the MS MCE remote (unfortunately).  That is a different IR software suite that doesn't mix and match with lirc well.

Sorry that's about all I can comment on it though.

Not sure why you won't say it won't work. After following the previously posted link I got mine to work.

---

### Post by Danbc on 2007-12-27
Thanks for the inputs guys :)

One of my former colleagues was the one who got me on Ubuntu (MythTV) because I was bitching too much about Vista MCE. He showed me a working MythTV on Zalman but on Kubuntu and told me I should install the whole thing as a old MCE remote, but since the guides doesn´t work for Mythbuntu (or doesn´t work for noobs :D) I´m kinda lost, and ofc my former collegue is out of contact now :(  But both the LCD and the remote worked on his setup.

---

