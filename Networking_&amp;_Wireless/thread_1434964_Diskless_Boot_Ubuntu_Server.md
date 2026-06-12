---
title: "Diskless Boot Ubuntu Server"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by Happybattles on 2010-03-20
I'm a computer teacher at a residential treatment center.  I just started about two weeks ago and have been going through training, and writing the courseware.

I've decided, with the support of my boss, to switch all of our computers out from Windows XP Pro to Linux.  This will save us a ton of money, lots of tech time and possibly fines since nobody is sure how many CD keys are actually being used (could just be one as far as we know).

I've decided to set up the computer lab as a Linux Ubuntu cluster.  I've done the research and am confident that I can make it work.  In fact, we have had some net-boot computers donated to us from our State.  They're used, but are 1.5ghz and 500mb ram - so they should be just fine.

I'd like to cram as many workstations into our classroom as I can, but here's what I need to know...

Chances are the computer I'll be using will (at max) have a 1.5ghz processor and 1.5gb of RAM.  I'd like to run 24 computers in a private network off of this one computer.  The applications we'll be running are:

1. OpenOffice
2. FireFox
3. GIMP

That's pretty much it.

If I understand how a cluster works, the parts of the operating system the workstation will need are downloaded through the network and exist in ram.  When we open a program, like OpenOffice, the necessary parts of the program are also sent to ram, or are dumped into swap to make up for the lack of ram... but it's the swap of the server, since the workstation will be diskless.

So, my questions:
1. Will 1ghz processor and 500mb ram work as a workstation if we run the nice GUI?
2. Will the computer mentioned earlier be enough for 24 workstations?
3. If yes to both, all I have to do is add a user to the server for that user to be able to log in and use the system with the permissions I allow?
4. If I install some parental control software at the server, that'll manage the websites the users can go to as well from their workstations?

Thanks in advance.  And if you have any tips or items for me to note, please don't hesitate.

---

