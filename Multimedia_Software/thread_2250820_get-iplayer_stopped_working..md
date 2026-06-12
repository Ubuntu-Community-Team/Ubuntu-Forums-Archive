---
title: "get-iplayer stopped working."
date: 2014-10-31
forum: Multimedia Software
---

### Post by ajgreeny on 2014-10-31
I use the ppa version of get-iplayer quite a lot and it has been terrific, but suddenly it has stopped working; it will not even update the cache-list of programmes.  I even went to [get-iplayer]("http://git.infradead.org/get_iplayer.git") , downloaded the latest version of archive available, extracted the perl script and replaced the script in /usr/bin with this newer one, just four days old, but still no go.

I understand the BBC has made some changes to to the underlying way it deals with the programme metadata.  There is a workaround at [https://answers.launchpad.net/ubuntu/+source/get-iplayer/+question/256372](https://answers.launchpad.net/ubuntu/+source/get-iplayer/+question/256372) but that means it's such a palaver to get any programmes downloaded that it becomes more of a chore than a pleasure.

Anyone know any more about the likelyhood of an update to get-iplayer?

---

### Post by majabl on 2014-11-03
It looks like the get_iplayer community is already finding ways of working around the problems. There is a workaround of sorts for the TV cache, though I'm trying to make it work on my Windows laptop without success at present.

See some of the threads at [https://squarepenguin.co.uk/forums/forum/general-topics/](https://squarepenguin.co.uk/forums/forum/general-topics/) for more information. [https://squarepenguin.co.uk/forums/topic/webscrapping-tvradio-cache/](https://squarepenguin.co.uk/forums/topic/webscrapping-tvradio-cache/) seems to be the most promising yet.

---

### Post by ajgreeny on 2014-11-03
There is s new version available from the ppa now 15:04GMT Nov 3 2014, which appears to have put right the problems.

Many thanks to the person or persons who have done the coding for this; Impressively quick work!

---

### Post by matt_symes on 2014-11-03
> **ajgreeny said:**
> There is s new version available from the ppa now 15:04GMT Nov 3 2014, which appears to have put right the problems.

Many thanks to the person or persons who have done the coding for this; Impressively quick work!

Thanks for this update.

---

### Post by ajgreeny on 2014-11-04
In fact there is now yet another version in the ppa, 2.90, which seems to working fine again.  It's available for 14.04 but not yet for 12.04 on my two machines, but you can get the updated version from [http://git.infradead.org/get_iplayer.git](http://git.infradead.org/get_iplayer.git) and install it manually, as I have done.
See my original post for how to do this if you don't know.

Isn't open-source software brilliant, and all the great coders, of course!

EDIT:
Just for info, the 2.90 version for precise (12.04) is available in the "testing" ppa.

---

