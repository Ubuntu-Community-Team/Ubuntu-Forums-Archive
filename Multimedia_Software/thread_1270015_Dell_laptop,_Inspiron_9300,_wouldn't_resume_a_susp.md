---
title: "Dell laptop, Inspiron 9300, wouldn't resume a suspend under Ubuntu 9.04"
date: 2009-09-19
forum: Multimedia Software
---

### Post by aaronchall on 2009-09-19
Greetings, I'm a new Ubuntuan. I installed it a few days ago and discovered to my horror that it wouldn't resume a suspend.  I think I have resolved the suspend issue, but it may have created another one.

My machine is a Dell laptop, a Dell Inspiron 9300. I had XP pre-installed, then using a live-cd of Ubuntu 9.04, Jaunty Jackalope, that I burned myself, I partitioned the hard drive, and did a permanent install.  I am loving my new OS.  However I do find a bug from time to time.  The inability to resume a suspend was killing me, because I could find many similar questions online, with almost no responses.

I deduced that it was likely to be a video driver problem, but I was not sure how to figure out exactly what device I had and what driver specifically I needed without opening Windows (oh the horror.)  

So a quick search found EnvyNG, a program that purports to tell you the best driver for your system.  I installed it, and selected the driver it recommended, and after rebooting, suspend not only worked properly, but I seem to have better visual effects when making general use of my system.

So my first problem was solved, :guitar:, but I seem to recall EnvyNG taking up a lot of space on my hard drive, :confused:.

My question is, can I uninstall EnvyNG with no problems, and what's the command line instruction to do so?  Is there a GUI solution for these types of issues?  How do I know where EnvyNG is on my drive?  If I can just search and find it, is it ok to just delete it?  (I'm sure the command line approach is superior, but I'm just learning about Ubuntu and GNU/Linux/Debian/etc...)

Thanks!

Aaron

---

### Post by HappyFeet on 2009-09-29
Go to system>administration>synaptic package manager and full screen the window. Using the search button (not quick search) search for envyng. Simply click it and select completely remove.

---

### Post by aaronchall on 2009-11-29
Thanks Happy, and now for something entirely different.  

No, actually, just the same, only I've installed 9.10, and I had new problems with envyng. 

My initial problem was the fail to suspend and resume, it would just hang with a black screen instead of coming up.  I remembered it being the video driver, so I downloaded the one in Software Center that I believed I was using before.  That didn't work, so I looked up this thread, said "aha!" and went looking for envyng again. I found it also in the Ubuntu Software Center.  Downloaded it, double clicked it, and nothing.  Fail to resume error still happening.  Removed the driver I had installed in software center, and it still wouldn't come up.  I removed envyng, reinstalled it, double clicked, and still nothing.  

So I finally went to the command line.  Ran "man envyng", and not sure what to do, ran it with the uninstall command.  Then I ran it with the text command.  I selected nVidia, selected the recommended, and it finally worked.  Rebooted, and was able to resume a suspend.  

I'm leaving this log of my travails for any other beleaguered Ubuntuan, that he (or even she, should she exist...) might find respite in this message.

Aaron Hall

---

