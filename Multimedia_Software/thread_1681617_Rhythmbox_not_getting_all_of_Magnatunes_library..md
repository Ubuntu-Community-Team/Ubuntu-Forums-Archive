---
title: "Rhythmbox not getting all of Magnatunes library."
date: 2011-02-04
forum: Multimedia Software
---

### Post by CallsignBaron on 2011-02-04
Hope someone can help. 

Installed Ubuntu 10.10 (32-bit) and as the title implies, Rhythmbox is not fetching all of Magnatunes library. It works, it loads Magnatune and the songs all play, but it only loads 5 artists with a total of 18 albums. I am not sure, but going by the names of the artists, it is possible it is just loading the first 5 artists. Anybody else have this problem? Is there a fix? For the record, Jamendo's catalog loads just fine with 22,636 artists loaded.

Help would be much appreciated, missing Magnatune. Thanks!

---

### Post by Mark Stosberg on 2011-02-05
I am getting the same behavior on 10.04 on two different computers, and have been for about a week. I'm a paying Magnatune subscriber and contacted them about the issue a few days ago, but have not heard back. I'll analyze the network traffic some now and see if I can learn amount what's happening.

---

### Post by Mark Stosberg on 2011-02-05
I used "gksudo wireshark" to what the HTTP requests and responses between Rhythmbox and Magnatune.  What I found was that Rhythmbox was requesting this file, which unpacks to 14 Meg XML file:

[http://magnatune.com/info/song_info_xml.zip](http://magnatune.com/info/song_info_xml.zip)

I can see that the first entry after the one that appears have a XML validation problem. The genre name given as "Rock & Roll", when the XML should be "Rock &amp; Roll". I confirmed this by pasting a chunk of the XML into a XML validation service:

[http://xmlvalidation.com/](http://xmlvalidation.com/)

It clearly shows that the file does have an XML validation problem, and the first problem in the file is exactly as given above-- just after the last file we see loading. 

So, this appears to be squarely a bug with Magnatune, not Rhythmbox. Magnatune is failing to provide valid XML. I'll follow-up with Magnatune.

---

### Post by Mark Stosberg on 2011-02-05
Although this is a bug in Magnatune, I have created a patch for the Rhythmbox Magnatune plugin until they fix the issue properly. 

I've tested this on 10.04, but it should be safe to try on other versions. At worse, uninstall and re-install the rhythmbox-plugins package to undo the patch.

Stop Rhythmbox, save the attached file to your desktop, open a terminal and run this:

sudo patch /usr/lib/rhythmbox/plugins/magnatune/MagnatuneSource.py <Desktop/rhythmbox_magnatune.patch.txt

Now, start Rhythmbox again. The entire catalog should be there.

The patch simply rewrites their invalid XML file to be be valid.

---

### Post by CallsignBaron on 2011-02-05
Thanks Mark! I can confirm your patch works in Maverick! Magnatune is working now with 410 artists and 909 albums.
:guitar:

As a side note, this also restored album artwork which was also not loading. And I don't know if this is a new thing with Magnatune now but commercials are now playing over the song rather than between songs! Very annoying!!! ( I do not remember Magnatune ever doing this!)

---

### Post by aarond25 on 2011-02-06
Thank you for the fix.  This has been bothering me for a few days now and I really appreciate the patch.  I love the open source world!!!  Thanks again.

---

### Post by johnbuckman on 2011-02-06
I've fixed the XML encoding problem with "Rock & Roll". 

Rhythmbox should hopefully now be happy with it again.

- John from Magnatune

---

### Post by ~zenr on 2011-02-06
Thanks Mark!:)

---

### Post by CallsignBaron on 2011-02-07
Thats great John! Thanks for jumping in and fixing this, gonna mark this solved!

Thanks All ~Baron

---

### Post by afrodeity on 2011-05-28
Magnatune is refusing to load the catalogue in Natty. I've tried the patch, no luck.

---

