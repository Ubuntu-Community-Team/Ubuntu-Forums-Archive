---
title: "VLC -  Giving me two problems"
date: 2010-10-26
forum: Multimedia Software
---

### Post by TBerk on 2010-10-26
1) Somehow I set my main menu behavior to open any of the folders under 'Places' pull-down menu in VLC. By that I mean if I choose 
  
PLACES from the upper left of the screen ad ,over the mouse down to DOCUMENTS it open (or tries to open) the folder withing the VLC program. If there is a video in the given folder it will start paying, otherwise I get an error message.

If I knew where those 'things' where to right click and choose Nautilus to open them with, I'd likely be OK.

2) VLS used to behave but now when I toggle from Full Screen mode back to adjustable size window mode the program extends off the screen, including the top row w/ the window controls.  I can get the mouse pointer to an edge to resize the window.

I've taken a 1st look over in VideoLan's forums/ticket tracking system

[http://trac.videolan.org/vlc/report](http://trac.videolan.org/vlc/report)

 but haven't yet found this particular problem, let alone a solution.

btw- I'm running Ubuntu 10.10 w/the Studio version's Audio and Video sections installed, plus Medibuntu as well. VLS's current installed version is 
1.1.4 .

Thx,
TBerk

---

### Post by garvinrick4 on 2010-10-26
open terminal and 
```
nautilus
```
right click on documents and choose open with and go to other applications go to File Browser and choose it and make sure the box is checked "remember to use this for"
Will now open all in file browser that is in your drop down menu places. Remember this
it will happen aqain if you right click on music folders or video folders and say open with vlc or mplayer or so on and so on. if you open the vlc and open directory and go to the one you want it will not happen.

---

### Post by TBerk on 2010-10-26
Having taken all of ten seconds to fix this, I feel very much the idiot; (I kept banging my head on 

- Right Click on DOCUMENTS
- Properties
- "what?, no 'Open With' ...?"


Thx, now, I can get it to show the upper menu bar when not in full screen mode...



TBerk

---

### Post by garvinrick4 on 2010-10-26
> **TBerk said:**
> Having taken all of ten seconds to fix this, I feel very much the idiot; (I kept banging my head on 

- Right Click on DOCUMENTS
- Properties
- "what?, no 'Open With' ...?"


Thx, now, I can get it to show the upper menu bar when not in full screen mode...



TBerkThe reason I new this fix was because I was in same position you were once so do not feel silly. I think the learning curve is pretty consistent with us users. Read these forums, google, google and google somemore and keep notes, what else can we do. Ubuntu Linux is just about the greatest OS there is. If you use Debian based apt-get for a while and then try out the yum and RPM's Ubuntu is like a Corvette vs a Volkswagen bug. OpenSUSE uses zypper and RPM's. zypper???
Any newcomers out there got to have this pdf book it is free download it.    [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by TBerk on 2010-10-28
> **TBerk said:**
> 

2) VLS used to behave but now when I toggle from Full Screen mode back to adjustable size window mode the program extends off the screen, including the top row w/ the window controls.  I can get the mouse pointer to an edge to resize the window.

I've taken a 1st look over in VideoLan's forums/ticket tracking system

[http://trac.videolan.org/vlc/report](http://trac.videolan.org/vlc/report)

 but haven't yet found this particular problem, let alone a solution.

btw- I'm running Ubuntu 10.10 w/the Studio version's Audio and Video sections installed, plus Medibuntu as well. VLS's current installed version is 
1.1.4 .

Thx,
TBerk

Still having a strange situation where it's other than Full Screen mode is extended up off the screen.

Oh; running ver 173 of the NVidia 'additional drivers'.

---

