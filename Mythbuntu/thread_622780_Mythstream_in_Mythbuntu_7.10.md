---
title: "Mythstream in Mythbuntu 7.10"
date: 2007-11-25
forum: Mythbuntu
---

### Post by blahmartinblah on 2007-11-25
Hi
Running Mythbuntu 7.10 on amd64. I have mythstream selected in the Mythbuntu control panel, it seems to work OK.

I suspect however it isn't the latest version. For example, I don't appear to have a youtube parser as described on the Mythstream website under 'New in v0.18_1':
[http://home.kabelfoon.nl/~moongies/streamtuned.html](http://home.kabelfoon.nl/~moongies/streamtuned.html)

How can I prove what version I am using?
How can I upgrade if it is required?

Martin.

---

### Post by superm1 on 2007-11-25
> **blahmartinblah said:**
> Hi
Running Mythbuntu 7.10 on amd64. I have mythstream selected in the Mythbuntu control panel, it seems to work OK.

I suspect however it isn't the latest version. For example, I don't appear to have a youtube parser as described on the Mythstream website under 'New in v0.18_1':
[http://home.kabelfoon.nl/~moongies/streamtuned.html]("http://home.kabelfoon.nl/%7Emoongies/streamtuned.html")

How can I prove what version I am using?
How can I upgrade if it is required?

Martin.
Yes, you are right its an older version.  I'll poke the maintainer for it in Ubuntu to see if he can update the package and then we can a backport.

Hang tight for a few days.

---

### Post by blahmartinblah on 2007-11-30
Hi superm1,
Any news on this?
Martin.

---

### Post by tgm4883 on 2007-11-30
It's in the process of being updated.  I just need to add a get-orig-source and it should be ready.

---

### Post by road2elysium on 2007-12-01
Awesome!  YouTube on Myth!  Can't wait ;)

---

### Post by aidan_curtis on 2007-12-03
as my kids say
Are we there yet?
Are we there yet?

---

### Post by tgm4883 on 2007-12-03
The new version has been uploaded and built for hardy.  Now we are just waiting for a backport to gutsy

[https://bugs.edge.launchpad.net/gutsy-backports/+bug/173684](https://bugs.edge.launchpad.net/gutsy-backports/+bug/173684)

---

### Post by aidan_curtis on 2007-12-07
the kids are still asking

---

### Post by aidan_curtis on 2007-12-11
any sign of the backport?
or would you have instructions for a build from source?

---

### Post by superm1 on 2007-12-11
It was approved by the backporters team yesterday.  It's just a matter of one of the archive admins hitting the "backport" button now, and you will have it.

---

### Post by aidan_curtis on 2007-12-12
thanks

---

### Post by obscure411 on 2007-12-19
Hello,

Couldn't hope but notice that an apt-get upgrade installed a new version of mythstream today, but I'm still not seeing the YouTube parser listed.

As dumb as this sounds, is there a simple way for me to verify what version of mythstream I am running?

Thanks!

---

### Post by superm1 on 2007-12-19
> **obscure411 said:**
> Hello,

Couldn't hope but notice that an apt-get upgrade installed a new version of mythstream today, but I'm still not seeing the YouTube parser listed.

As dumb as this sounds, is there a simple way for me to verify what version of mythstream I am running?

Thanks!
dpkg -l | grep mythstream

---

### Post by obscure411 on 2007-12-19
OK, I show as v. 0.18.1...

Maybe I'm missing something, but where would I find the YouTube parser?

---

### Post by lokimon on 2007-12-20
i have been really impressed with mythstream, but i haven't been able to figure out the interface very well.

i can navigate to shoutcast streams that are listed in their database, yet i don't know how to enter a URL for a station that i already know of.  i also don't know how to bookmark a stream that i like.

with the worldwide media project, i can find TV stations and sometimes get them to play, but i don't know how to make them view full-screen.

i tried googling but haven't found any good info sites that explain the user interface, am i just being dumb?

oh, and bring on the youtube!

---

### Post by lokimon on 2007-12-22
> **superm1 said:**
> dpkg -l | grep mythstream

i'm also running 0.18.1 of mythstream.

[EDIT]

i updated mythtv and now i am able to see youtube most popular videos, but not yet search for youtube videos.  there is a function to search daily motion however.

to get to this screen i had to hit 0 and then 9 on my remote, and then navigate to the right until the "video" section heading appeared at the bottom.

---

### Post by aidan_curtis on 2007-12-23
Im not seeing the upgraded version in the package listings 
can anyone point me where to start looking?

---

