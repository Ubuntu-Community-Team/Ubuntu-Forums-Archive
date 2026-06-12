---
title: "Can't get netflix to work"
date: 2014-05-10
forum: Multimedia Software
---

### Post by Ben_Cook on 2014-05-10
I just installed xubuntu on my inlaws pc since windows was full of problems and had a lot of viruses.  I'm trying to make everything as user friendly as possible - the only things they really use it for are email, pictures and streaming shows, including netflix.  I've got silverlight working, and I'm pretty sure I have the user agent overide turned on. It streams fine using this test recommended in another post  [http://www.iis.net/media/experiencesmoothstreaming1080p](http://www.iis.net/media/experiencesmoothstreaming1080p)

I've also done the bubble test, so it seems like everything is as it should be.  But when I go to start up netflix, it simply doesn't work.  I can sign into my account, see the shows, then it tells me to check the minimum specs (in firefox) or that silverlight is installed (in chromium).  I've installed the restricted extras, if that makes a difference.  I need to return this computer to them tomorrow so any help would be appreciated

---

### Post by SeijiSensei on 2014-05-10
Netflix requires Microsoft Silverlight which can be added via a very clever browser plugin for Firefox called pipelight.  I believe I mentioned that in our earlier discussion.

Quick installation guide: [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

The Pipelight site: [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

You'll need to use a browser plug-in to spoof your "User-Agent" header.  I use [UAControl](https://addons.mozilla.org/en-us/firefox/addon/uacontrol/).  I told it to use this Agent string for netflix.com:
```
Mozilla/5.0 (Windows NT 6.1; rv:29.0) Gecko/20131011 Firefox/29.0
```

Glad to hear everything is running fine with this machine now, Ben.

---

### Post by Ben_Cook on 2014-05-10
Haha! It was the string on the UAcontrol.  Computer illiterate me didn't  realize that I needed to put something in there.  I just put it as the  default...I assume that will work fine?  Or should I make it for netflix  only? (which I'm not sure how to do).  Anyway, the main problem is  solved.  Thank you again for your help.

---

### Post by SeijiSensei on 2014-05-10
Tools > Add-ons > Extensions.

In the entry for UAControl, click preferences, then Add Site.  You'll be prompted for a site ("www.netflix.com" in this case) and a UA string.  Netflix is the only site for which I use a custom string.

I'd leave the default alone.  Always good to add more Linux entries to sites' agent logs!

---

### Post by Ben_Cook on 2014-05-10
Perfect!  Even though I still have a lot to learn about linux, I am  enjoying it.  Especially when it involves making a new convert haha.   Again thanks for all the help.  Everything is working great now.

---

