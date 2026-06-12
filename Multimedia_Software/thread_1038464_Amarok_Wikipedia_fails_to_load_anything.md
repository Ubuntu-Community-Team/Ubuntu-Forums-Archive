---
title: "Amarok Wikipedia fails to load anything"
date: 2009-01-12
forum: Multimedia Software
---

### Post by domurai on 2009-01-12
Hi, is anybody experiencing any problems with Amarok 1.4.10? The KDE release is 3.5.10.

Whenever I open the Wikipedia Tab, it always tries to fetch the information but nothing is displayed and I always get the language selections. When I click on something (for example French), I get the language selection again (this time without French and the option to choose English).

Anybody?

---

### Post by mitch.c on 2009-01-14
Seeing in 1.5.8 on Gutsy as well. Just starting to check into it, this is my first stop.

---

### Post by VastOne on 2009-01-14
> **domurai said:**
> Hi, is anybody experiencing any problems with Amarok 1.4.10? The KDE release is 3.5.10.

Whenever I open the Wikipedia Tab, it always tries to fetch the information but nothing is displayed and I always get the language selections. When I click on something (for example French), I get the language selection again (this time without French and the option to choose English).

Anybody?

Ditto for me here too...Started 2 days ago and have not been able to find a solution.  I have gone through some of the language selections and the only one to display anything was a Peruvian, I believe it was...Weird and must be on the Wiki redirect end...?????

---

### Post by domurai on 2009-01-14
Someone on the amarok forums was getting it as well.
[http://amarok.kde.org/forum/index.php/topic,12523.0.html]("http://amarok.kde.org/forum/index.php/topic,12523.0.html")

lewulff mentioned it could be the change on wikipedia's end that might be causing the problem.

---

### Post by VastOne on 2009-01-15
> **domurai said:**
> Someone on the amarok forums was getting it as well.
[http://amarok.kde.org/forum/index.php/topic,12523.0.html]("http://amarok.kde.org/forum/index.php/topic,12523.0.html")

lewulff mentioned it could be the change on wikipedia's end that might be causing the problem.

I have now checked 15 installations of Ubuntu and Amarok and all are failing and none are on the same network....

Just an FYI

---

### Post by v6lur on 2009-01-22
Wikipedia has changed their page code a bit, so now Amarok don't know how to parse it. Launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/)

---

### Post by skajoeska on 2009-02-04
There is a [fix]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/comments/9") from the launchpad site.

Change line 4192 in contextbrowswer.cpp
from: m_wiki = m_wiki.mid( m_wiki.find( "<h1 class=\"firstHeading\">" ) );
to: m_wiki = m_wiki.mid( m_wiki.find( "<h1 id=\"firstHeading\"" ) );

I can't confirm this works because I have no idea where contextbrowser.cpp is located. Can anyone help me with that?

---

### Post by Gavin77 on 2009-02-04
I'm pretty sure you need to edit that source file and recompile amarok.

---

### Post by skajoeska on 2009-02-04
That makes since. Someone posted a .deb of the re-compiled amarok with the fix.

[Link]("http://janitux.boaboa.org/etc/amarok_1.4.10-0ubuntu3_i386.deb")

I guess i'll just have to reinstall amarok then. o-well.



edit: it worked for me and only took a minute.

---

### Post by SushiR on 2009-02-19
Will there be - by any chance - an update with the fix for Hardy?

---

### Post by SushiR on 2009-03-04
If someone has build a deb for Hardy with the patch, it would be nice if he oder she can upload it.

---

### Post by Tryfon on 2009-04-16
Bumb!

---

