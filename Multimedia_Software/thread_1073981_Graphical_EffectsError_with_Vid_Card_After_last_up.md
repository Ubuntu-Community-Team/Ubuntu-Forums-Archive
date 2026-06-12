---
title: "Graphical Effects/Error with Vid Card After last update"
date: 2009-02-18
forum: Multimedia Software
---

### Post by Misterbadexample on 2009-02-18
When I was running 8.04 it installed the restricted driver for my Radeon 3870 512MB 256-bit GDDR4 PCI Express video card.

When I upgraded to 8.10 it continued working just fine. No hitches.

For some odd reason, I downloaded new updates from the update manager and now I can't enable the graphical effects. As far as I can see the same restricted driver is installed. I've reinstalled the restricted drivers and nothing has changed. It doesn't surprise me that it's not that easy.

Where should I start troubleshooting this problem? What information should I find to post here?

---

### Post by Misterbadexample on 2009-02-21
I'd just like to add that this problem, which sounds identical, has a solution that I've now tried.

[http://ubuntuforums.org/showthread.php?t=1004332](http://ubuntuforums.org/showthread.php?t=1004332)

This has not solved my problem.

If anyone has any insight, I would appreciate it.

---

### Post by Misterbadexample on 2009-02-21
Well, I spoke a little too soon, although I still have the same issue. Here's what I did.

I removed all fglrx drivers through synaptic.
I checked them with dpkg --get-selections 'fglrx* and they all came up purged.

Then I removed the ATI folder from the /etc directory, like the other thread says.

What I have now is sort of a halfway better but doesn't fix the problem.

I have the drivers reinstalled but they start up unactivated because there is no profile for them. It brings up a low-graphics troubleshooter that tries to create a new profile and fails. The only way I can get to Ubuntu is through using the "default" video profile. For some odd reason, a few of the problems I was having with the video are gone, but nothing else has changed. I can't use my 3d card and it simply will not load anything graphics intensive like Sauerbraten.

---

