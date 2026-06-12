---
title: "kdenlive keeps crashing."
date: 2008-06-13
forum: Multimedia Software
---

### Post by srikar on 2008-06-13
i installed kdenlive , i didnot get its menu entry.
When i launch it from the terminal it crashes.



```
srikar@srikar-desktop:~$ kdenlive
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
Launched ok, pid = 7360
kdenlive: //  INIT EFFECT SEARCH
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Mlt inited
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: WARNING: KdenliveDoc::loadFromXML() document element has unknown tagName : kdenlivedoc
kdenlive: // DOCUMENT: /home/srikar/.kde/share/apps/kdenlive/recovery.kdenlive, version: 0.6
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive: KdenliveDoc in closeDocument()
kdenlive: deleting contents...
kdenlive: //  CLIP PRJECT LENGTH IS: 0
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kdenlive:  + + +  Loading Time : 407ms
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

```

---

### Post by srikar on 2008-06-13
any kinda fix???

---

### Post by srikar on 2008-06-13
??

---

### Post by Miki_Loz on 2008-06-25
I have the same problem, I have installed it from the official repositories, trying with apt-get and aptitude but nothing seems to work, it keeps at the start.
Ive heard about some option you could try to get it on, just add "-nograb" after kdenlive like this: "kdenlive -nograb".
However it's not working for me and I doubt it'll be for you.

---

### Post by sblanzio on 2008-07-08
> **Miki_Loz said:**
>  just add "-nograb" after kdenlive like this: "kdenlive -nograb".



this worked for me. tnx!

I heard someone saying to disable compiz, but mine was disabled!

however thank you!

---

### Post by eks on 2008-08-17
> **srikar said:**
> i installed kdenlive , i didnot get its menu entry.
When i launch it from the terminal it crashes.


I have the exact same crash, with the same log.

The "kdenlive -nograb" worked for me but... isn't there a more... "elegant" solution? :)

This is on an AMD64, maybe that's why there's not much people complaining?

Googling about this gives the same post on Ubuntu forums for many different languages.

There's also [this bug on kdenlive mantis]("http://www.kdenlive.org/mantis/view.php?id=138") that might be related (?).


eks

---

### Post by dantienn on 2008-09-17
kdenlive -nograb did not work for me. also using amd64... 

sometimes kdenlive takes down the whole system, and i have to log in again.

I will try to disable compiz and report back if it works.

---

### Post by lubeck on 2008-09-17
I have found KDENLIVE to be horribly buggy and best for insuring crashes as of late (past 4-6 months.)  Have tried everything and it is disappointing.

I had used KDENLIVE for 1 year prior and it was wonderful, but it got weird in Hardy.  I am much more impressed these days with the less capable but very stable Open Movie Editor.  Just an opinion. 
l

---

