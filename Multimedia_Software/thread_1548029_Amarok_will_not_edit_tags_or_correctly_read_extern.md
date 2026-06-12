---
title: "Amarok will not edit tags or correctly read externally edited tags"
date: 2010-08-07
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2010-08-07
Hello,

I'm using Amarok  2.3.0 and am having trouble editing tags.

For some of my music the tags can be edited normally, however for some of my other music the tags appear "greyed-out," and cannot be edited, and this is sometimes intermittent.  I have tried using standalone applications, such as; EasyTag, Audio Tag Tool and kid3.  These all work correctly and my changes are correctly read in each of these apps; however, Amarok will not even read the new changes, such as "Track" and "Title" and organizes and plays these files according to what must be an "original" image of these tags, which can somehow NOT be updated.  I have tried deleting the "amarokrc" file and relaunching Amarok, but the "images" of the original tags remain unchanged.

I suspect that there is a configuration file, other than "amarokrc" that contains a database where these "images" are stored.  I also suspect that this database requires "root" permission in order to update this file.  I have experienced a similar problem in other apps, such as "Tork," which when running the configuration wizard, will ask for my root password to alter the "Privoxy" configuration file, but never does it, or reports an error.  I eventually overcame this problem by changing the owner of this file, from "root" to "user," which I should never have had to do.  This "hack" makes apparent that there is a very basic flaw in the "root vs user" file ownership system and the handshake between this and the affected applications.  IMHO, "all" applications should have a reporting mechanism for this error as a core design feature.  I've experienced this problem as far back as "Feisty Fawn," and  I'd really like to see it fixed.

In Amarok I suspect both issues are present but, IMHO, if you fix the file ownership problem first, a lot of wierd buggy BS will magically disappear.


Respectfully, Hannibal


Any help appreciated

---

### Post by coljohnhannibalsmith on 2011-05-17
I haven't tried this in a while; but I'm wondering what would happen if I configured the laucher, in the main menu, to launch Amarok with ***gksudo***:

[COLOR=Blue][B][I][COLOR=Black]gksudo[/COLOR] amarok %U
[/I][/B][/COLOR]
instead of

[COLOR=Blue]***amarok %U***[/COLOR]

**Comments???**

[IMG]http://www.funphotoart.com/wp-content/uploads/2007/12/website-blog-comment-icon17.gif[/IMG][COLOR=Blue][I][B]

Hannibal[/B][/I][/COLOR]

---

