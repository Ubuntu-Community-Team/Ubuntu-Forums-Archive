---
title: "Diskless client different version than backend - Possible?"
date: 2009-07-07
forum: Mythbuntu
---

### Post by MonkeyKnifeFight on 2009-07-07
So I just got my new Zotac IONITX board and I was wondering if it's possible to set up the diskless server to use a newer Mythbuntu version than what's running on the backend.

I mean, I know you can have a, say, (disk based) Jaunty frontend with a Hardy backend, but can you set up the diskless Hardy server to create a Jaunty client image?

How would you do that? I'd like the newer kernel for the more up to date hardware support, but don't want to have to upgrade my backend right now.

---

### Post by MonkeyKnifeFight on 2009-07-07
I found the --dist param for ltsp-build-client. I decided to try it on a VM I have at work, but it did not seem to change the distribution as it was building the image. Am I missing something?

I've got a Jaunty machine trying to build a Hardy client (I know it's backwards from what I originally said, I just wanted to see if it would work).

```

root@andrew-vm:~# /bin/sh -c /usr/sbin/ltsp-build-client --mythbuntu --mythbuntu-copy-user-credentials --copy-sourceslist --arch i386 --dist hardy --pin-dist hardy --base /opt/ltsp/ --accept-unsigned-packages
NOTE: adding default dist and components to security mirror:
http://security.ubuntu.com//ubuntu **jaunty** main restricted universe multiverse

```

Do I need to change my apt sources?

Also I see the following process going when ltsp-build-client is running, so I know it's not looking in the right place.
```

/bin/sh -e /usr/sbin/debootstrap --arch i386 jaunty /opt/ltsp/i386 http://archive.ubuntu.com/ubuntu

```

---

### Post by MonkeyKnifeFight on 2009-07-07
Ok. Nevermind, just figured out that if I take the
```
/bin/sh -c 
```
off the front of the command it accepts my params. Looks like it should work. I'll give it a try tonight on the real systems tonight.

---

### Post by ian dobson on 2009-07-07
Hi,

As long as the frontend and the backend are running the same version mythtv (0.21) then you shouldn't have any problems.

I'm running 0.21-fixes on my backend and the VDPAU backports on my frontend and haven't seen any problems for the last 6 months or so.

Regards
Ian Dobson

---

### Post by MonkeyKnifeFight on 2009-07-07
Yes. I've had the same experience. I just needed to know how to set up a diskless image that was not the same mythbuntu version as the Mythtv backend.

I'm pretty confident the image creation should work like I'm hoping.

---

