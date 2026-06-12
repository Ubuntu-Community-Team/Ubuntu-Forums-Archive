---
title: "Problems to install SLCREATOR"
date: 2008-07-01
forum: Multimedia Software
---

### Post by testnet on 2008-07-01
Hi,
 When a install "slcreator" i got the message

Status: Error: Dependency is not satisfiable: gambas-runtime

All install all the package of gambas.

What do I wrong?
How can i solve it?

Thanks for your attention
Jan

---

### Post by Achilles124 on 2008-07-13
I have the same problem when trying to install linux-firewall.org.

I installed gambas-runtime but the problem remains. The same error-message.

---

### Post by Achilles124 on 2008-07-24
Okay, solved it myself.

---

### Post by Turpin on 2008-12-04
And then, 6 months later, I'm coming along and asking "Great, solved it yourself!  How?"  
I've been trying to get linux-firewall installed on Intrepid.  I found a way to install some version of Gambas and related files in there, I think by using dpkg with --force all option, but then after I get linux-firewall.org installed, the popups don't work.  In Hardy, the popups do work.  I was going to stick with Hardy just so I could use this firewall with application-specific rules, but why should I have to?  There must be some way to make it work.

---

### Post by linuxbastard on 2008-12-23
And here I am two weeks after turpin and lookin around for some documentation on how this issue got solved.

Anybody?

---

### Post by glantucan on 2009-01-07
I got the same problem with slcreator 0.7.1-1.
It seems it was developed for an earlier version (1) of gambas. 
Ubuntu is now shipped with version 2 of gambas so i don't see an easy solution. Anyone who knows of any, please, post it here.
Thanks

Glantucan

---

### Post by zero244 on 2009-01-25
I have the same problem.......any solution.
Hardy went to gambas2 which doesnt seem to work.

---

### Post by luangwa on 2009-01-26
I can see I'm not alone. I too have installed all gambas... still the same error message.

---

### Post by jeffos on 2009-08-04
Anybody come up with the answer to getting slcreator running on Jaunty?

The dependency issue with gambas seems to be the problem.

Come on men, I have holiday snaps to process!

---

### Post by punong_bisyonaryo on 2009-08-26
Came upon this thread coz I wanted to give slcreator a try. The only solution I can think of is to file it in launchpad to provide us with a gambas-runtime metapackage (not likely to happen) or to create an update slcreator package.

Anybody know how?
Maybe we can put out a bounty for an updated SLCreator package?

---

### Post by punong_bisyonaryo on 2009-08-27
I've requested for packaging SL Creator in Launchpad.
Check it out [here]("https://bugs.launchpad.net/ubuntu/+bug/419115")

Thanks!

---

### Post by Heroshinator on 2009-09-15
K I got it installed by downloading the packages from the link below but im having trouble getting it to launch.

[http://packages.ubuntu.com/search?keywords=gambas&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=gambas&searchon=names&suite=all&section=all)

---

### Post by irwand on 2010-05-14
I too was really interested in getting slcreator running, but it didn't seem easy, and I wasn't about to install gambas1 from old ubuntu into my machine.

So I set out to create a GUI for dvd-slideshow myself:
[http://code.google.com/p/dvd-slideshow-editor/](http://code.google.com/p/dvd-slideshow-editor/)

It is based of wxPython, so it should just run fine on your machine <cross-fingers>. Feedback is appreciated. Thx.

---

### Post by Klympf on 2012-02-06
Here's a solution to get slcreator running. I use karmic, which is already outdated. It might work in newer ubuntus, too. 

Open "Administration > Software Sources" and add the old gutsy repositories:

  deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe

Close and reload package information. Gutsy included gambas 1.0.18. 

Open slcreator-0.7.1-1_all.deb with the package manager (right click). It is now possible to install the old gambas dependencies before installing slcreator.

Don't forget to install dvd-slideshow e.g. with synaptic!

---

### Post by CJS23 on 2013-01-20
> **Achilles124 said:**
> Okay, solved it myself.

Wow - that's great . . you were ready to accept help, but not share the solution, is that it?

---

