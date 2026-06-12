---
title: "[SOLVED] projectM in Amarok...where is the actual config file?"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by bmwman91 on 2007-12-14
I got projectM up & running with Amarok alst night and am greatly pleased about that.  However, I cannot change its settings.

There is the config.inp file located in /usr/share/projectM and I can make the settings to be whatever I like.  However, they do not change anything when i run projectM in Amarok (I do not use XMMS at all, not even installed).

So, is there another config file somewhere that I am unaware of?  Rather than even telling me where it might be, teach me something new.

How do I do a search for files that have been accessed in the last 2 minutes or something similar?  In Windows it was super easy and I really liked not needing to use a terminal.  The file searcher thing with a GUI does not seem to work at all, though I may not be using it right.

Either way, can someone tell me how to find the most recently accessed files ANYWHERE in my filesystem?  That should tell me which files hold the config settings I want to edit.

Thanks all.

keywords: Amarok, projectM, config, configuration, config.inp, resolution, setting, settings, Milkdrop

---

### Post by bmwman91 on 2007-12-14
Oh never mind, I found the operators for "find."  May as well call it solved, I am sure it'll work out when I get home.

I'll search the whole thing with:
$ sudo find / -amin -2 or something immediately after starting Amarok and projectM.

---

### Post by breaking on 2008-02-02
bmwman91,  maybe you could share your findings with the rest of us?  I'm having the exact same problem with projectM in Aramok.  I change settings in ~/projectM/config.inp and they never seem to take effect.  I have the same small window each time.

---

### Post by rama on 2008-02-14
I ll second **breaking**'s request

---

### Post by koolatron on 2008-02-22
little bit of threadcromancy here.  the projectm config file is located in ~/.projectm, it sould be the only file in that directory.  the one in /usr/share/projectm is an example, afaik.

hope this helps.

---

### Post by RedRat on 2008-02-22
You guys have hit on something here. I too am a newbie to Ubuntu and also have tried using the search function in the various file managers. They seem not to work. I think I am doing something wrong also. Is there some trick to finding files among the system files and the "hidden" files? Can you, like in Windows, set parameters for your search. 

Yeah, I know you can use the command line, but what about the GUI approach.

---

