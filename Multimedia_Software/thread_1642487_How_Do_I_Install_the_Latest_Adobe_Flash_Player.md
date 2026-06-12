---
title: "How Do I Install the Latest Adobe Flash Player?"
date: 2010-12-10
forum: Multimedia Software
---

### Post by light-vessel on 2010-12-10
It should be easy, but Adobe's page for Linux downloads has a choice of about five different downloads. I tried one and it gave me some files I don't know what to do with. I do already have Flash on my computer, which I got from the Ubuntu software centre, and it works for most things but some things tell me I need a newer version.

---

### Post by cchhrriiss121212 on 2010-12-10
You should just have an .so file, all you need to do is put it in the right folder:
/home/yourusername/.mozilla/plugins
Then restart firefox. Type about:plugins into the address bar to check that it is in use. 

The mozilla folder has a dot in front of it which means it is a hidden folder, use ctrl+h to see hidden folders.

---

### Post by ajgreeny on 2010-12-10
So what version of flash do you have?  You can find out by typing ```
about:plugins
``` in the addressbar of FF and seeing what it reports.  If you see v10.1.102, you already have the stable updated version.

There is a beta version of 10.2 available as well which is very good, in my experience.  That is on the adobe site [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/) as a tar.gz file and unpacked to a libflashplayer.so which you will have to manually move to the same place as your current libflashplayer.so, after renaming that as a backup.  Let me know if you wish to try that and I can give you full details, but frankly, it should not really be needed, the version from the repos is the current stable version and also good.

---

### Post by light-vessel on 2010-12-10
That is the version of Flash that I have. This is a little embarrassing because I have to admit that I'm trying to play Pet Society on Facebook. It tells me that I need to update my Flash.

I can't remember which download I tried, but it didn't give me an .so file. If I understood ajgreeny's answer correctly, I should go for the tar.gz download, or completely ignore this whole story because my current Flash player is the latest good working one anyway.

I had got used to just using the Ubuntu Software Centre and I had managed to install one or two things from repositories that I had added, but as soon as a piece of software wants you to behave like you're using Windoesn't (ie. download then install), I get confused.

I'll give that beta version of 10.2 a try if I can. Thanks for your answers.

Edit:
I should admit that I discovered that I was blocking Flash from the site and their standard response to this isn't "You don't have flash installed" or "Stop blocking flash from our site" but "Your flash isn't good enough"! I think I've learnt one or two lessons anyway.

---

