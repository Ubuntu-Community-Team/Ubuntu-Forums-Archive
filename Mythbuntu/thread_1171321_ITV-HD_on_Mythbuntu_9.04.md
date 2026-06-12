---
title: "ITV-HD on Mythbuntu 9.04"
date: 2009-05-27
forum: Mythbuntu
---

### Post by pickledfish on 2009-05-27
Hi. Has anybody got ITV-HD working on Mythbuntu 9.04 (or even 8.10)?
I'm trying to find a pretty straightforward how-to. Any help would be great. Thanks.

---

### Post by Neon Dusk on 2009-05-28
I use itvhd2.diff from [http://svn.mythtv.org/trac/ticket/5388](http://svn.mythtv.org/trac/ticket/5388)

A rough overview of applying a local patch is (which I noted from someone else's post) is :-

1) apt-get build-dep mythtv
2) apt-get source mythtv
3) apt-get install devscripts
4) dch -i (put some comments in about what you changed. In the version number, use the old version number plus a +local1 or something similar. This will make sure that you're version is marked newer, but that if an even "newer" version came out, you can still get it.
5) Try to apply the patch. If it applies cleanly, unapply it and put it in debian/patches.
6) Update the debian/patches/00list to include the patch
7) debuild. You should get some binaries out.
8] use dpkg -i <packagename>.deb to install the binaries


I converted itvhd2.diff to a dpatch not sure if this need but I've attached it here

---

### Post by myfrog on 2009-08-27
Hi, do you have a more detailed description of how to apply the patch? What file do I patch for example?

Kind Regards, Steve

---

### Post by Neon Dusk on 2009-08-29
From within the source directory you would run 
```

patch -p1 < ../27_itv_hd_hack.dpatch

```

To test if the patch applies cleanly. If it does you would then reverse the patch with
```

patch -R -p1 < ../27_itv_hd_hack.dpatch

```

N.B. This is only testing if the patch applies cleanly. The patch still seems to work for the latest 0.21-fixes so you can probably skip this step.

Putting the file in debian/patches and adding it to 00list ensures that the patch gets applied during the debuild process.

It also looks like Mythtv 0.22 will include the ITV HD fix so you won't need to go through this process once 0.22 is released.

---

### Post by red321 on 2009-09-03
"IIt also looks like Mythtv 0.22 will include the ITV HD fix so you won't need to go through this process once 0.22 is released."

Excellent, thats the last patch I need to apply myself :-).

Is it going to be in Mythtv 0.22, or as a patch in mythbuntu build ?

---

### Post by Neon Dusk on 2009-09-03
The fix is going to be part of MythTV 0.22 - If you look at the [ticket](http://svn.mythtv.org/trac/ticket/5388) a fix was comitted to trunk 6 days ago.

---

### Post by red321 on 2009-09-03
Well spotted.

Can confirm its working perfectly in trunk, (not surprising) and is already in the weekly build binaries.

OT : 

There is always good news and bad news :-(

Excellent to see the ITV-HD fix made it, but my old skiploop_filter patch seems to have been bumped to at least 0.23.

It looks as if its dropped out of the mythbuntu patches as well, as although its still in the directory its not being built

Ive just started playing with trunk again, to destroy my perfectly stable 0.21-fixes setup. I assumed the loopfilter patch would still be in there. I guess everybody but me has bought a card that can do VDPAU :-(

---

### Post by RoboNuggie on 2009-10-02
Are you sure ITV-HD is working in Trunk?

I have trunk .22 (22167), and no ITVHD there... it shows up, I can EPG it, but no picture or recording when a program actually is on air.

---

### Post by red321 on 2009-10-02
Works for me :confused:


The "fix" is on the backend, I assume you must have updated that as well ?

currently on mythbuntu binaries -r 22167, but its been working since I upgraded to trunk daily builds.

---

### Post by RoboNuggie on 2009-10-02
backend, frontend both trunk'ed.... 

Oh well, no big deal really, just for completion sake I suppose.... otherwise .22 works like a charm so far.

---

