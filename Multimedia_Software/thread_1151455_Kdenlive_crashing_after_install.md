---
title: "Kdenlive crashing after install"
date: 2009-05-06
forum: Multimedia Software
---

### Post by clevefan on 2009-05-06
I just installed kdenlive from the package manager. It never showed up in the menu so I launched from terminal. this is what I get when it starts.it crashes.


clevefan@laptop:~$ kdenlive
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
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
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
Unable to start Dr. Konqi
clevefan@laptop:~$

---

