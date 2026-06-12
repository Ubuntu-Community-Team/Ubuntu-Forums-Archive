---
title: "Can't hear myspace music player on any browser"
date: 2008-11-23
forum: Multimedia Software
---

### Post by louisp on 2008-11-23
Have tried multiple browsers, they all have the same problem. Music from other sources work.

Anybody know why this is? 

cheers

---

### Post by james_mcl on 2009-07-11
Hi,

I've just fixed a similar problem on my Hardy installation and wondered if this fix might work for you:

1.) Go into your home folder. Go to View and choose "Show Hidden Files".

2.) Delete the .macromedia folder. Flash uses this in pretty much the same way the browsers use whatever folders they store cookies in. I know that if a particular subfolder is read-only, it breaks Myspace Music Player but not YouTube or Google Mail. Perhaps the folder permissions have become corrupted on your system?

3.) Reopen your browser and try again. (It'll create a new .macromedia folder when you get to the page.)

Hope it works! By the way, I strongly advise deleting that folder every session - I personally have a shell script that runs at login and deletes it. Otherwise it's like a folder full of persistent tracking cookies that can't be deleted via the browser.

James.

---

### Post by caio2112 on 2010-03-03
Did not work for me. I am using Firefox 3.6 and Chrome 5.0.307.11 beta and both freeze after I click the play button.

---

### Post by sam.reader on 2010-03-03
The reason for myspace music player for not working on any browser is because of the audio renderer used by myspace.
The reason for this problem is Linux or Ubuntu can't decode the audio signals that are sent by myspace whose servers actually run on windows and this is a big problem they haven't able to rectify this from a long time.

---

### Post by caio2112 on 2010-03-03
That's odd. A previous version of Chrome (4 dot something, actually it was Chromium, I think) seemed to be working, although I've only entered MySpace a couple of times. Unfortunately now I've upgraded it and cannot test it anymore.

---

