---
title: "Empathy does not show Google Talk contacts"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by Smartflight on 2010-10-12
Google Talk logs in fine using Empathy. The problem is, that I see no contacts at all, even when I have checked 'Show offline contacts'. I do know people could message me since one of my friend messaged me last night, until my net connection gave up.

I'm on Ubuntu 10.04.1 LTS.

---

### Post by yarozar on 2010-11-24
I have the very same problem under Ubuntu 10.10

Subscribing to a thread.

---

### Post by Smartflight on 2010-12-15
I can't remember properly, but I think this was fixed when I reinstalled Empathy and set up a Google Talk account on default settings. Or maybe it was no more an issue when I set my internet connection's MTU to 1454.

I'm on Ubuntu 10.10 (amd64) now. No issues.
Try reinstalling, or changing the MTU.

---

### Post by ankurwidguitar on 2011-01-22
Hi! I too have the same problem. It was working fine until a couple days ago. And now I don't see any gtalk contacts, though I can chat when somebody messages me. 
I reinstalled Empathy and it worked fine for the first time. When I restarted, it turned to its old self. Also changing the access point MTU isn't working for me.
I'm on a 32-bit system with Ubuntu 10.10

---

### Post by Smartflight on 2011-01-24
> **ankurwidguitar said:**
> Hi! I too have the same problem. It was working fine until a couple days ago. And now I don't see any gtalk contacts, though I can chat when somebody messages me. 
I reinstalled Empathy and it worked fine for the first time. When I restarted, it turned to its old self. Also changing the access point MTU isn't working for me.
I'm on a 32-bit system with Ubuntu 10.10

I have no idea man.
Reinstalling and changing the MTU solved the issue for me.

---

### Post by pus on 2011-10-13
Same here 8-[

Anything new on this?

---

### Post by zole052 on 2011-10-13
> **pus said:**
> Same here 8-[

Anything new on this?

Same here on 10.04 :(

---

### Post by BigBaka on 2011-10-13
There must have been a recent update of empathy, because all of a sudden it seem a bunch of people have the same problem.

Hope they fix soon. I used software center to remove application and then reinstalled, but same issue. Maybe I need to try a kill command in terminal?

---

### Post by ksrini on 2011-10-14
+1. same here. probably after a recent update I took.

---

### Post by matzi11a on 2011-10-14
wow old thread back to life, i dont think its the same problem as original poster! something changed yesterday. pidgin unaffected.

[update] installing Telepathy from ppa fixes the issue for me.

---

### Post by flintdragon on 2011-10-14
just wanted to add that I have this issue now.  No contacts listed but people can IM me still.

---

### Post by achilleas.k on 2011-10-14
This appears to be the related bug:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/676828](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/676828)

---

### Post by achilleas.k on 2011-10-14
Tried killing several times to no avail. You can give it a shot though.

---

### Post by achilleas.k on 2011-10-15
I'd rather wait for an ubuntu update rather than flood my PPAs. I've gone down that path before and I don't like it, having a separate PPA for each piece of software that once had a bug. I'll probably move to Pidgin until it gets fixed.

Just my 2p.

---

### Post by rodrigoguarischi on 2011-10-17
I had the same problem here and after waste a couple of hours I founded a solution and posted at my blog, try it:

[http://rodrigoguarischi.wordpress.com/2011/10/17/fixing-empathy-bug-gtalk-contact-doesnt-appear/](http://rodrigoguarischi.wordpress.com/2011/10/17/fixing-empathy-bug-gtalk-contact-doesnt-appear/)

Rodrigo

---

### Post by MeskZ on 2011-10-18
Same here. I am using 10.04.
Contact list does not show gTalk contacts, but if they message me I get the notification and I can reply.
Anyone with reason for this defect?
Or I should just switch to pidgeon :P

---

### Post by clevertomato on 2011-10-18
Same problem here recently. I decided to use Telepathy PPA per post #16 by [rodrigoguarischi]("http://ubuntuforums.org/member.php?u=1472292") and it fixed things.

---

### Post by carmelogiar on 2011-10-19
I fixed on ubuntu 10.4 following this

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg558160.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg558160.html)


But now it seams that msn has problem to login

---

### Post by d3ngar on 2011-10-19
Took me a while, but after a few removals I finally managed to install the required files from the PPA. 

This all works nicely again.

I'm not sure if this bugs will be fixed, but here are the links for you to monitor:

[Empathy Bugzilla]("https://bugs.freedesktop.org/show_bug.cgi?id=40276")
[Launchpad Bug]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/676828")

---

### Post by wackawacka on 2011-10-21
> **achilleas.k said:**
> I'd rather wait for an ubuntu update rather than flood my PPAs. I've gone down that path before and I don't like it, having a separate PPA for each piece of software that once had a bug. I'll probably move to Pidgin until it gets fixed.

Just my 2p.


don't give up.  just my 2p.

---

### Post by d3ngar on 2011-10-21
I thought a fix has already happened? Everything works fine here. 10.4 and 11.10.

---

### Post by achilleas.k on 2011-10-22
> **wackawacka said:**
> don't give up.  just my 2p.

I didn't give up and it got fixed a couple of days ago, so all in all I'd say it worked out great! :)

---

### Post by ifree on 2011-10-22
Hi all ,I just get it fixed by rm .purple/blist.xml~ 
hope it work for you:P

---

### Post by Monkey_Trainer on 2011-12-19
I was having the same problem. Under the advanced options I checked the box "Use old SSL"  it connected and my google talk contacts now show.

Thanks,

Robert

---

### Post by newb85 on 2012-06-23
> **Monkey_Trainer said:**
> I was having the same problem. Under the advanced options I checked the box "Use old SSL"  it connected and my google talk contacts now show.

Thanks,

Robert

I'd like to try your solution, but I can't seem to find the advanced options.  I'm running 12.04, so I hope they haven't removed them.

---

