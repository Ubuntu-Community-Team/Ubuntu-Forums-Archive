---
title: "mythbuntu download issue?"
date: 2008-04-15
forum: Mythbuntu
---

### Post by jmverner on 2008-04-15
I am trying to download mythbuntu and the download links do not work for me.  I have tried Firefox and IE both on two different systems.  In all cases the result is a completely blank screen with the url to the iso file shown in the location:
[http://mythbuntu.org/download/?file=mythbuntu-8.04-beta-desktop-i386.iso](http://mythbuntu.org/download/?file=mythbuntu-8.04-beta-desktop-i386.iso)

This happens whether I am downloading 7.0 or the beta.  Any idea why this would be happening?  Is there an alternative mirror I can go to to get the iso?
Thanks,
Matt

---

### Post by tgm4883 on 2008-04-15
Do you have javascript enabled?

---

### Post by superm1 on 2008-04-15
You need to have javascript turned on and not be block google analytics (it's how we track our usage)

---

### Post by jmverner on 2008-04-16
In my Firefox browser I have the NoScript extension but both google-analytics and mythbuntu.org are whitelisted.  In my Internet Explorer of course this does not apply.  I even added [www.mythbuntu.org](www.mythbuntu.org) to my "trusted sites" in IE.  Still get exactly the same behavior.  On three different computers here in my house!
Any other ideas?

---

### Post by superm1 on 2008-04-16
> **jmverner said:**
> In my Firefox browser I have the NoScript extension but both google-analytics and mythbuntu.org are whitelisted.  In my Internet Explorer of course this does not apply.  I even added [www.mythbuntu.org]("http://www.mythbuntu.org") to my "trusted sites" in IE.  Still get exactly the same behavior.  On three different computers here in my house!
Any other ideas?
When you get this fully blank blank page, look at the source of it (View->Source), you will see the mirror that you were allocated in the javascript redirect.

---

### Post by jmverner on 2008-04-16
I did that and copied and pasted the URL:
*url removed.  Please don't link directly to our mirrors.  Thanks*
into the location field and that did the trick.  Still don't understand why but it worked.
Thanks!
Matt

---

### Post by Harridu on 2008-05-22
I ran into the same problem. Sorry to say, but this is sick.Why do I need to enable some Javascript spy software provided by a multi-billion $ company to download free software? I would prefer to keep my browsing history private.

The other *ubuntus are available via torrent. This is smart.

---

### Post by tgm4883 on 2008-05-22
> **Harridu said:**
> I ran into the same problem. Sorry to say, but this is sick.Why do I need to enable some Javascript spy software provided by a multi-billion $ company to download free software? I would prefer to keep my browsing history private.

The other *ubuntus are available via torrent. This is smart.

Mythbuntu is available via torrent also.  Look a little before you criticize.

:EDIT:

And to answer your question, because they track how many downloads for us.  It's nice to know if people are using what you are making available.  If we didn't know that people were using Mythbuntu, then maybe Mythbuntu would cease to exist to do lack of support.

---

