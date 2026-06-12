---
title: "DAAP problems on 9.10/Mac iTunes"
date: 2010-01-02
forum: Multimedia Software
---

### Post by the_jest on 2010-01-02
I see that there have been several threads on this in the past, but none of them offer a solution.

My main music library is running on iTunes on a Mac (iTunes 9.02, so it's not the iTunes 7 bug). I have the library set up to be shared on the local network, with no password. I'm trying to access this library on a machine running a new install of Ubuntu 9.10. When I open Rhythmbox, the library is visible, but I can't connect to it; I get the "Retrieving songs from music share" message that hangs forever. Despite this, in iTunes it does show that there is one user connected.

As an experiment I installed Banshee, which also shows the share, but when I try to connect to it, it instantly returns an "Unable to connect to music share" message; the "Common reasons" it gives do not apply to me.

The Mac running this has no firewall, and the router isn't blocking any ports internally. I would have assumed that the fact that the library is visible means that it can be reached, in any case.

I'd be grateful for any suggestions. The music library itself is available on an NFS share, but for various reasons (mainly that it's a large library that changes regularly, and I don't want to maintain versions in each potential media player I connect to it with) I don't want my clients to access the files directly. Thanks.

---

### Post by the_jest on 2010-01-02
I'm sorry, I did some more reading, and realized that the iTunes DAAP server doesn't work with any _post_-7 iTunes version. I had originally thought that only iTunes 7 was affected.

Yet another reason to hate Apple. 

Looking into other solutions now. I'd prefer to keep using iTunes to manage the music (among the reasons is that I have a lot of AppleScripts that I use to edit/manage imports), but perhaps using a separate player that'll also work as a server is the thing to do.

---

