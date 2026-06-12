---
title: "Rhythmbox fails to start - segmentation fault."
date: 2008-10-23
forum: Multimedia Software
---

### Post by malworthy on 2008-10-23
Hi,  Rhythmbox no longer starts up at all on my system at all :(. If I run it from the terminal it just says "Segmentation Fault".  I installed the debug symbols and ran it in GDB, with output below.   I have tried totally removing it from my system and re-installing but no luck.  Can anyone please help? 


Starting program: /usr/bin/rhythmbox 
[Thread debugging using libthread_db enabled]
[New Thread 0xb6552740 (LWP 7485)]
[New Thread 0xb59feb90 (LWP 7489)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb6552740 (LWP 7485)]
0x080a7842 in rb_python_module_init_python () at rb-python-module.c:174
174	rb-python-module.c: No such file or directory.
	in rb-python-module.c

---

### Post by malworthy on 2008-10-27
Update,

If I start Rhythmbox in any other folder except for my home folder (even in sub folders off home folder), it works! Yay.  I'm sure with a bit of poking around I can find out what's happening, but at least I can get it running.

---

### Post by Jorge_C on 2008-10-28
Hi,

The very same thing happened to me today, I tried reinstalling, but it didn't work.
Though, starting it from terminal and changing directory does the trick, thank you!

I don't remember any updates related to rhythmbox lately...Whay may have broken it in such a way?

---

### Post by malworthy on 2008-10-30
I have finally solved the mystery.  I was playing around with some python scripts and i created one called gtk.py, which also created a compliled gtk.pyc file.  It seems that rhythmbox didn't like the gtk.pyc file in my home folder, so I deleted it and it all works fine now.

Jorge_C, I think it's unlikely you would have created a gtk.py file, but it may be worth cleaning out any files you don't think you need out of your home folder or moving them somewhere else.

---

### Post by Jorge_C on 2008-10-30
Wow, what a coincidence! I was playing with some python scripts, too, and I had pygtk.py and the byte-code compiled pygtk.pyc in my home folder. Moving them both solved the problem.

Though, I have another python script in my home folder (not related to gkt at all) which doesn't affect rhythmbox.

---

### Post by spoilingmyself on 2010-03-03
Now this is super coincidence.. Same problem and same solution.. I was also playing around with python.. and thus rhythmbox was not happy ;) wel now I shifted all the python scripts to other folder and it works but there is one error it gives with every song switch..

Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request

Can you please suggest why is this happening?

---

### Post by spoilingmyself on 2010-03-03
guys one more thing now though rhythmbox and totem may work from terminal but they are still not working from Applications->sounds and videos->rhythmbox.
I am now aware of why this is happening? Any help??
thanks in advance and anyways it is working... coz of you people..

---

