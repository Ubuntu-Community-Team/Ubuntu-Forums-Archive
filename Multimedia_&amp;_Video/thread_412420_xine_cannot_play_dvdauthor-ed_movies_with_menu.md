---
title: "xine cannot play dvdauthor-ed movies with menu"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by didu on 2007-04-18
Hi guys,

I hope this is the right forum to ask questions about dvdauthor and xine. I've been trying to create dvds from my avi files. I've tried the following:

(1) tovid -- this takes forever to run and sometimes doesn't work.
(2) manual work with dvdauthor, transcode, mplex etc.

I've had a some success with the manual way, in which I first use transcode to split the avi files into audio and video parts, then combine them together with mplex, then create the dvd structure using dvdauthor. All is fine except that I cannot get my dvds to have menus, I've read the man page for dvdauthor many times, but as soon as I try to put menus into the xml config file for dvdauthor, the dvd it generates becomes unusable by xine and other dvd players. For example, the following code generates a dvd that works fine:

```

<dvdauthor dest="DVD">
   <vmgm>
   </vmgm>
   <titleset>
     <titles>
       <pgc>
         <vob file="trip1.mpg" chapters="0,5:00,10:00,15:00,20:00"/>
         <vob file="trip2.mpg" chapters="0,5:00,10:00,15:00,20:00"/>
         <vob file="trip3.mpg" chapters="0,5:00,10:00,15:00,20:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>

```

Then the same code, but with "buttons" and menu won't work:

```

<dvdauthor dest="DVD">
 <vmgm>
  <menus>
   <pgc entry="title" >
    <button name="01_Button_1" > { g3=1; jump titleset 1 menu entry root; } </button>
   </pgc>
  </menus>
 </vmgm>
 <titleset>
  <menus>
   <pgc entry="root" >
    <button name="Play" > { jump title 1; } </button>
   </pgc>
  </menus>
  <titles>
   <pgc pause="0" >
    <vob file="trip1.mpg" pause="0" />
    <vob file="trip2.mpg" pause="0" />
    <vob file="trip3.mpg" pause="0" />
   </pgc>
  </titles>
 </titleset>
</dvdauthor>

```

The second code generates a dvd that xine claims to be faulty. Has anyone got any idea what I'm doing wrong?

Thanks a lot.

-D

---

### Post by crispy_420 on 2007-04-19
Try DeVeDe to make a DVD from avi file. Simple and effective.

---

