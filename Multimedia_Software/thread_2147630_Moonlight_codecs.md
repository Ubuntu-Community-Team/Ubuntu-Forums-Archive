---
title: "Moonlight codecs"
date: 2013-05-22
forum: Multimedia Software
---

### Post by ThatPoshGirl on 2013-05-22
I'm running Ubuntu 13.04 64-bit. I have Moonlight installed, but every time I try to use it I get prompted to install codecs. When I try to install them I get a message that it failed to download EULA. It just says "network error."This has been going on for months, even before I upgraded from 12.10. I haven't been too worried about it up until now, but now I have an online class that requires it. Is there a way to install the codecs manually?

---

### Post by monkeybrain2012 on 2013-05-23
If you are talking about the open source clone for Silverlight it has been dead for almost a year.  [URL="http://www.omgubuntu.co.uk/2012/06/linux-silverlight-plugin-moonlight-abandoned"]http://www.omgubuntu.co.uk/2012/06/linux-silverlight-plugin-moonlight-abandone 
[/URL]

---

### Post by SeijiSensei on 2013-05-23
If you need to use Silverlight, you need to be running Windows.  Moonlight does not include any of the proprietary parts of Silverlight, particularly the components that handle DRM-encumbered content.

---

### Post by monkeybrain2012 on 2013-05-23
It probably works in wine with the windows version of Firefox. What kind of online classes are still offered in Silverlight? Even MicroSoft closed down the Silverlight site and Netflix is ditching it.

---

### Post by ngunton on 2013-11-25
Many universities have started using panopto for lecture capture, seems it uses silverlight :(

---

### Post by monkeybrain20122 on 2013-11-26
> **ngunton said:**
> Many universities have started using panopto for lecture capture, seems it uses silverlight :(

Not sure if "many" universities use silverlight. Maybe some private colleges..

Anyway, here is a possible solution for those interested. [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

I have just tested it on Fedora 19 and Manjaro Linux 0.88 (a derivative of ArchLinux). In Fedora it works very smoothly in Chrome but in Firefox it just shows a white box (maybe some of the addons I have installed?). In Manjaro it works flawlessly in both Chrome and Firefox. Here is the site I tested 
[http://www.iis.net/media/experiencesmoothstreaming1080p](http://www.iis.net/media/experiencesmoothstreaming1080p)

I haven't installed it in Ubuntu because it is my main system, don't want to risk messing up anything until adequately tested.

---

### Post by sammiev on 2013-11-26
I have been using [Pipelight]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html") for a few weeks now in Ubuntu with Firefox and it seems to run very well with the items I have tested it with.

---

