---
title: "tethering combined with internal network question"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by fhomasp on 2012-02-17
Hey,

First of all, I've been using Ubuntu for a few weeks and that's it, never really used another version.  It's rather fair to say that I'm a n00b :)

Here's my problem.

At work I've got 2 workstations.  One is for internal network resources and a way too restricted internet connection.  There's also a virusscanner running 24/7 and I can't install, copy, delete or any other useful action on the device.  It's greatly insufficient to try and do my work (I'm a software developer).

Luckily I've been able to get an Ubuntu based machine on which I've got full control but it's totally disconnected from everything, except for another internal network and the first restricted machine.  To allow easy switching between the two I've been using "QuickSynergy" that allows me to use mouse and keyboard on both machines on the same time "as though it's all one machine".  The Ubuntu machine runs the server and has the mouse/keyb connected, the restricted machine connects using a client.

But..  In order to be able to get past the internet restrictions (I do need it it to download external software and libraries) I've set up my smartphone (galaxy S) to tether on my Ubuntu machine.  This was a pain due to some bug in my firmware but it's working now using an app and a driver.  That said.

Now I've got 2 network connections, wired.  I want to use the tethering connection when I try to access the internet, the other when I need to use internal resources.  I already tried several approaches but none has been the situation that I want.

. I tried setting the internal network connection in Network Manager to "use this connection only for resources on its network".  This has been the best result so far, but I can't use quicksynergy anymore.  The other restriced machines client can't access the server on Ubuntu anymore.
. I tried changing the metric on both of the connections but that never works.  It always gives some kind of error message, even if I try using root access.  Then I tried ifmetric for that, which had the same result.

So here I am with the question.  I pretty much invested several hours into it and I don't have a good solution.  Maybe you guys can help me out ? :-)


Restricted machine runs Win Vista (...)
Dev machine is Ubuntu 11.04


Thanks

---

