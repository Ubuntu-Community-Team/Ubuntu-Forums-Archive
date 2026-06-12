---
title: "nvidia geforce 6800 ultra breaks X11 after easyubuntu"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by mikecalder on 2006-06-06
Hi, total Ubuntu newbie here, evaluating, thinking of switching, testing using live CD downloaded yesterday. I'm wary because I've had huge hardware compatibility problems with other distros in the past.

My machine is AMD Athlon 64 3400+, A7V600/K8V-X mobo with 2G memory, Nvidia GeForce 6800 Ultra, 2x 400GB IDEs and the usual other stuff.

Ubuntu boots up nice, I like what I see.

So I try easyubuntu to get the nvidia-glx drivers and other stuff.  Seems to work fine.

I run nvidia-xconfig, close down everything, then Ctrl-Alt-backspace.  X won't restart, says there's a problem.

Text mode screens ask me if I want to see the reason and details, I click OK and OK.  Both of these screens just have a couple of lines telling me where the log is, no error or warning messages at all.

Any ideas?

---

### Post by mikecalder on 2006-06-06
OK, colour me naive.

I tried again, and of course the down arrow key gave more details (more than I cared to read).  Why wasn't there an indication, say like "more..."?

Anyway, right down at the bottom, I found:

Failed to load the NVIDIA kernel
Aborting
Unload module nvidia
Unload module randac
Unload module fb
Screens found, but none have a usable configuration
Fatal server error
no screens found.


OK, I can live with that.  Now what does it mean? Why don't my screens have usable configuration?  What do I have to do to make sure that they do?

---

### Post by Vincent_Lin on 2006-06-06
Ahh!  I haven't opened my box of 6800 card yet so I could not tell you what might have gone wrong.  But I did observe one thing that confirms what I have been feeling about the difference between Windows and OSS.

Windows will always tell you what to do when something goes wrong.

OSS software will always tell you what goes wrong.  So it's up to you and the helping community to figure it out what the solution might be.  

So, sometimes Windows (and Windows software that share the same mentality) will simply ask you to close the application, or impolitely close itself without telling you what happen, while OSS application will close the application, and keep a "log" of what happened(be it good or bad).

Functionality design share the same mentality.  Windows way is  - I deside how the application should work, what it should look like, and "let me know waht you think".  OSS way is - I "present" my solution to this problem, and the best I can do to make it work.  You can use it, or let me know what you think about it, and better yet, pick it up from what I have left, and go any further as you like.

So, OSS mementum is not built on "free" concept, instead, out of my $0.02, is built on a much much deeper social concept, which sure enough, can improve our lives.

So, back to you question, those "log" files, are the ones that contain "errors and warnings".  For other more capable persons to help you, you could simply "paste and copy" them to the forum's posting.  They are there.

You can also "copy and paste" those lines more than you care to read over to the forum as well.  Someone, well at least some particular "ones", might be extermely interested why it did not work on your system. 

Regards,

Vincent

---

### Post by sadhaka on 2006-06-06
mc,

I have a similar set-up to yours, and am having similar problems. Just in case you haven't seen this stuff yet, here's a link:

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=nVidia&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=nVidia&titlesearch=Titles)

But maybe that's old news...

<>denis

---

