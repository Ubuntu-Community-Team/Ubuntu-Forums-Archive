---
title: "How to show non-English language when using telnet"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by shva on 2009-01-26
I use telnet in Ubuntu terminal to login in a BBS, whose primary language is not English. So what I see in the terminal is bunches of meaningless symbols. I try to change something in the "Preference" of the terminal window, but I can not find anything to change (or how to change). All I want is to show the language in terminal. Can someone tell me how to do? Thank you for help!

---

### Post by dmizer on 2009-01-26
You'll have to create a new terminal profile (Under the File or Edit menu, I think ...) with the correct language settings and character encoding. Then rather than using the default profile to connect, use the new profile.

Sorry for the rough sketch, as I don't have a terminal in front of me at the moment.

---

### Post by floatingpoint on 2009-01-26
File > New Profile

But I don't see any option to change language!

edit: also, you don't need to make a new profile, if you go to Edit > Profiles you can chose to edit your default profile, and it brings up the same menu as when you create a new one (still no language options though).

---

### Post by shva on 2009-01-26
> **dmizer said:**
> You'll have to create a new terminal profile (Under the File or Edit menu, I think ...) with the correct language settings and character encoding. Then rather than using the default profile to connect, use the new profile.

Sorry for the rough sketch, as I don't have a terminal in front of me at the moment.

Thanks for your reply. But I check with "File" and "Edit Menu". All I can think about that is to change something in Edit Menu-> Preference. But I still do not know how to create a new terminal profile... Anything more specific? Thank you.

---

### Post by shva on 2009-01-26
> **floatingpoint said:**
> File > New Profile

But I don't see any option to change language!

edit: also, you don't need to make a new profile, if you go to Edit > Profiles you can chose to edit your default profile, and it brings up the same menu as when you create a new one (still no language options though).


Me either... By the way, I forgot to mention I am using xfce-terminal. But that doesn't matter too much since I can switch to gnome-terminal

---

### Post by dmizer on 2009-01-26
If there are no language preferences, are you sure you have the necessary language packs installed under programs > system > languages?

Also search synaptic for: xfce-terminal languagename

---

### Post by shva on 2009-01-26
> **dmizer said:**
> If there are no language preferences, are you sure you have the necessary language packs installed under programs > system > languages?

Also search synaptic for: xfce-terminal languagename

Thank you dmizer and floatingpoint. I think I have figured it out in gnome-terminal. Terminal-> Set Character Encoding and add languages and it works!

---

### Post by pete.urban on 2009-09-22
Hi there!

Idon't want to open a new topic for my problem, because I have same problem with the gnome-terminal when I'm using telnet.

My problem is, when I use the command:
telnet 10.0.0.1 
I have to change the character encoding from utf-8 to iso-8859-2. I created a new profile too, and a launcher for the above command and the character encoding must be set by manually in:
 Terminal -> Set Character Encoding -> 
here is the "current local (utf-8)" , "Central European (iso-8859-2)" and an option to add or remove...
I can not remove the current local, maybe this is the system default locale?

Any help, how could I set from utf-8 to iso-8859-2?

Regards, 
Pete

---

