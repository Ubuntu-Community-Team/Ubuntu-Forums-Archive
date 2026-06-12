---
title: "How to Allow Permissions in Microphone Settings"
date: 2009-03-19
forum: Multimedia Software
---

### Post by flylehe on 2009-03-19
Hi,
I am trying to search a song on midomi.com by singing. However I got this message:
"You must first 'Allow' permissions in 'Microphone Settings' to use Voice Search."
Anyone knows how to set it up?
Thanks!

---

### Post by Chris Musampa on 2009-03-19
This also happens to me with Flash 10 in Opera and Firefox, both browsers lock up and have to be killed when trying to adjust mic settings.

---

### Post by Podex on 2009-09-03
Well, I was hoping anyone would have an answer for this. I've tried Firefox, Opera and Chromium and [Midomi](http://www.midomi.com) just gets stuck after clicking "Click and Sing or Hum". A window with "You must first "Allow" permissions in "Microphone Settings" to use Voice Search." appears but you can't click the "Microphone Settings" button. Annoying.
It works fine on Firefox on Windows 7.

---

### Post by karlstad on 2009-09-05
Personally, I used Opera to go to e.g. [www.midomi.com/ajfaoi](www.midomi.com/ajfaoi) and then view the page's source code. Then I pasted a modified HTML-snippet with the <object> and <param>-elements to insert the same flash-element that records your voice. (see [http://paste.ubuntu.com/265724/](http://paste.ubuntu.com/265724/))

Then I clicked on "Save changes" or something in the source code viewer, and the page would update. Now I was able to enable the mic and stuff, and the changes made in Flash Player are probably global since I didn't get the annoying box asking me to let Flash access my mic from this site when I tried it in Firefox later.

---

### Post by Chris Musampa on 2009-09-08
[http://kubuntuforums.net/forums/index.php?topic=3105958.0](http://kubuntuforums.net/forums/index.php?topic=3105958.0)

---

### Post by jperelli on 2010-11-04
> **Chris Musampa said:**
> [http://kubuntuforums.net/forums/index.php?topic=3105958.0](http://kubuntuforums.net/forums/index.php?topic=3105958.0)

yeah!!
that solves the problem!!
this is the link to the settings manager, where you can change the settings [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

Thanks!!

---

