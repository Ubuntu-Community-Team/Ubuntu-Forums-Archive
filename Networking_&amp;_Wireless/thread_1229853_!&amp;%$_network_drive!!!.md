---
title: "!&amp;%$ network drive!!!"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by Danimal411 on 2009-08-02
First off, I'm an Ubuntu newbie, a recent convert from Vista.  All I have to say about Ubuntu is positive, double thumbs up, except for getting my hardware to work.  Two issues:  my Lexmark printer, (please hold your laughter until the ceremonial printer burning scheduled for next week, you're all invited if you bring beer).  Printer problems: SOLVED!

I also have a Maxtor Central Axis hooked up to my wireless router.  I've managed to get access it via Samba, but some programs are not able to see it.  Some are.  For instance, if I wanted to save a text file from text editor, I can do it without any problems.  The program is able to see the drive without any issues.  If I want to use Picasa for instance, or save my an encrypted version of my work files, I cannot access the drive with Picasa or truecrypt.  Cannot create, cannot open a file, the programs just don't see it.  

Why is it that some programs can see the drive and some cannot, and how can I fix this?  

Thank you all in advance.

---

### Post by Danimal411 on 2009-08-02
Oh, and I'm on Jaunty 9.04

---

### Post by dmizer on 2009-08-03
If you mounted your NAS drive via Places > Connect to server, then that is why some programs can see it and others cannot.

Please see this tutorial: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by Danimal411 on 2009-08-03
Thanks for that link!  I hadn't been too keen on the idea of editing fstab to mount my shares at startup, and that was a way better method.  This didn't solve my problem of only some programs being able to see the drive, though.

---

### Post by dmizer on 2009-08-03
> **Danimal411 said:**
> Thanks for that link!  I hadn't been too keen on the idea of editing fstab to mount my shares at startup, and that was a way better method.  This didn't solve my problem of only some programs being able to see the drive, though.

It should. If it's not, I suggest you post a reply in the tutorial for more help (I don't personally know much about GVFS). Otherwise, the only thing I can do is point you to the second link in my sig.

---

