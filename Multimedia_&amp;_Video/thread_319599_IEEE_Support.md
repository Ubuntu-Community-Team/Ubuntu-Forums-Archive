---
title: "IEEE Support?"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by vv88 on 2006-12-15
Your project looks fantastic, if I could help...I would (unfortunately I am another former windows user).  Anyway, a couple of questions I thought could/would be best answered here:

1) I have an IEEE sound card (FCA202 specifically..yeah, I know, big bucks :-D ) and I was wondering if there are any suporting drivers available.  I've tested a couple of packages out on the "line in" and "mic" jacks, but I would like to use the card b/c it just seems like it did a better job on my old sys.

 2)As for partitioning, I have set up a main 40 GB IDE for the root/home drive.  After that, I mounted a 120 GB SATA II for storage.  Is this the best setup as far as storage and transfer are concerned, or could I do better?

3) This relates to the last question and the storage device.  I am connected to the net through a router and didn't set the SATA II up for limited access (not root).  Is there a security risk by doing things this way?  I am the only person on my network so I assume this isn't an issue.

I am in the beginning stages of looking for a good software program so I'll do my research and keep up with the threads on this forum.  A very big thanks to the developers that are taking part in such a great idea.   btw, like most of you, I also tinker around with video...I'm hoping to use iEEE for that also, but that will be something I'll give more thought to in the distant future.

---

### Post by doobit on 2006-12-15
> **vv88 said:**
> Your project looks fantastic, if I could help...I would (unfortunately I am another former windows user).  Anyway, a couple of questions I thought could/would be best answered here:

1) I have an IEEE sound card (FCA202 specifically..yeah, I know, big bucks :-D ) and I was wondering if there are any suporting drivers available.  I've tested a couple of packages out on the "line in" and "mic" jacks, but I would like to use the card b/c it just seems like it did a better job on my old sys.

 2)As for partitioning, I have set up a main 40 GB IDE for the root/home drive.  After that, I mounted a 120 GB SATA II for storage.  Is this the best setup as far as storage and transfer are concerned, or could I do better?

3) This relates to the last question and the storage device.  I am connected to the net through a router and didn't set the SATA II up for limited access (not root).  Is there a security risk by doing things this way?  I am the only person on my network so I assume this isn't an issue.

I am in the beginning stages of looking for a good software program so I'll do my research and keep up with the threads on this forum.  A very big thanks to the developers that are taking part in such a great idea.   btw, like most of you, I also tinker around with video...I'm hoping to use iEEE for that also, but that will be something I'll give more thought to in the distant future.

I think you are refering to ieee1394 standard, or Firewire. The drivers for your card probably depend on the manufacturer to make them. As far as I can tell, they don't. There are some things that just work with the ieee 1394 drivers in Linux and other things that don't. You can capture and edit 25 mbps video with some software, like Kino and Cinelerra ( [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3) )

As far as the router goes, you might explain more about your setup. How did you install the operating system, are you using a firewall, etc. In Ubuntu, you are not in root unless you specifically enter root in a terminal, or by using recovery mode on boot up. So you are protected in that way.

---

### Post by vv88 on 2006-12-16
Yeah, it's IEEE 1394.  As far as I can tell, there are no drivers for this card.  I guess I'm just going to have to wait and see if something shows up.  Line in and mic won't be to bad (with some tweaking).

I have a router w/ firewall and recently installed firestarter on that system.  As you've stated I've set up the storage drive (mounted) in terminal using root.  However, I was prompted with a question that asked if I wanted to share the drive or limit it to root (something like that).  I answered "no" and continued on.  Maybe this was a mistake?.

EDIT:  I decided to reformat/reinstall and start the process over...no biggy, but I'm planning on setting things up different.  Thanks for the info.

---

