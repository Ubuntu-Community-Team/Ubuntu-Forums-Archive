---
title: "Need help with kdenlive"
date: 2008-05-11
forum: Multimedia Software
---

### Post by theophiles on 2008-05-11
I am about 3/4 through a project using kdenlive and I can't get it to open. Here is what happens:
```
bcline@dell:~$ kdenlive
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
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
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
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
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
KCrash cannot reach kdeinit, launching directly.
bcline@dell:~$ 

```

---

### Post by theophiles on 2008-05-12
I found the answer to my problem here:
[http://ubuntuforums.org/showthread.php?t=791355&highlight=kdenlive](http://ubuntuforums.org/showthread.php?t=791355&highlight=kdenlive)

---

### Post by theophiles on 2008-05-12
Nope,

That fix only helped for about an hour.

Here is some new readout of my crash can anyone help me!!
```

bcline@dell:~$ kdenlive
kbuildsycoca running...
Reusing existing ksycoca
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
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
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
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
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
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kdenlive: WARNING: KdenliveDoc::loadFromXML() document element has unknown tagName : kdenlivedoc
kdenlive: // DOCUMENT: /home/bcline/Videos/liberalarts.kdenlive, version: 0.6
kdenlive:  + + RESET CONSUMER WITH PROFILE: atsc_1080i_60
kdenlive:  + + RESET CONSUMER WITH PROFILE: atsc_1080i_60
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
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
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
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
kdenlive: *** DOCUMENT adding clip: Screenshot-1.png
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive: //////  LENGTH: 621
kdenlive: //  SCREEN length update: 621
kdenlive: *** DOCUMENT adding clip: primary-page-header.jpg
kdenlive: *** DOCUMENT adding clip: peasants.jpg
kdenlive: *** DOCUMENT adding clip: Laurentius_de_Voltolina_001.jpg
kdenlive: *** DOCUMENT adding clip: freedom.jpg
kdenlive: *** DOCUMENT adding clip: Arithmatic.jpg
kdenlive: *** DOCUMENT adding clip: Astronomy.jpg
kdenlive: *** DOCUMENT adding clip: Geometry.jpg
kdenlive: *** DOCUMENT adding clip: Gramar.jpg
kdenlive: *** DOCUMENT adding clip: Logic.jpg
kdenlive: *** DOCUMENT adding clip: manteg3.jpg
kdenlive: *** DOCUMENT adding clip: Music.jpg
kdenlive: *** DOCUMENT adding clip: phillibarts.gif
kdenlive: *** DOCUMENT adding clip: philosophy.jpg
kdenlive: *** DOCUMENT adding clip: Poetry.jpg
kdenlive: *** DOCUMENT adding clip: rhetoric.jpg
kdenlive: *** DOCUMENT adding clip: theology.jpg
kdenlive: *** DOCUMENT adding clip: 056 Fur Elise.mp3
kdenlive: *** DOCUMENT adding clip: Color black
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Many schools
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text freedom
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Arts
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text originally
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text trivium
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text grammar
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Rhetoric
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text logic
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text quadrivium
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Geometry
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Astronomy
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive:  / / /TITLE SIZE: 1920x1080
kdenlive: *** DOCUMENT adding clip: Text Clip
kdenlive: //  CLIP PRJECT LENGTH IS: 4308
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kdenlive:  + + +  Loading Time : 29544ms
kdenlive: **********  FREED MEM FOR: 056 Fur Elise.mp3, COUNT: 0
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
bcline@dell:~$ ICE default IO error handler doing an exit(), pid = 8690, errno = 11
```

:frown:](*,):confused:

---

### Post by Creative2 on 2008-05-15
first idea

mm you have used high resolution video ? try  to resize them if you have..

another idea

i don't know but i have this package too 
dvgrab.... if you want try without it you could lauch kdenlive from a terminal by typing 


kdenlive --nograb

or 

kdenlive --dograb

---

### Post by interglossa on 2008-05-15
I did the install of libxcb1-dbg and libxcb1-dev but I keep getting the same crashes you do (with or without --nograb).  When I get a chance I will post to the kdenlive.org forum.  BTW they seem to be recommending that we build from source.

---

### Post by theophiles on 2008-05-27
Thanks for the suggestion, but that didn't really work. I really would like kdenlive to work for me. 

```
bcline@dell:~$ kdenlive --nograb
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
Launched ok, pid = 16474
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
Unable to start Dr. Konqi
Could not find 'drkonqi' executable.
bcline@dell:~$ ICE default IO error handler doing an exit(), pid = 16471, errno = 11
```

](*,)

---

