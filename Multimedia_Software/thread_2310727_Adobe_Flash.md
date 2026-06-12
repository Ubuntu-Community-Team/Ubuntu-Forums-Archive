---
title: "Adobe Flash"
date: 2016-01-21
forum: Multimedia Software
---

### Post by heroquestelf on 2016-01-21
I wasn't sure if this was the right place to post this, but Adobe Flash has stopped working on my laptop. 

I'm running 14.04. I'm using the Firefox browser with the Adobe Flash add-on installed via the Ubuntu Software Center. It worked yesterday, but now when I go to a site that uses Flash I get a notification that I need to update it. Any ideas? I tried uninstalling the plugin then reinstalling it and that did not seem to work.

---

### Post by kc1di on 2016-01-21
I'm afraid Firefox no longer is going to support an udated flash plug in , the only alternative is either chromium or chrome browser with Pepper flash. 
you can try installing pepper flash from the repositories but don't think FF will recognize it.
I believe opera can also use pepper-flash , but not sure.

---

### Post by Dennis N on 2016-01-21
> **heroquestelf said:**
> I'm running 14.04. I'm using the Firefox browser with the Adobe Flash add-on installed via the Ubuntu Software Center. It worked yesterday, but now when I go to a site that uses Flash I get a notification that I need to update it...

What flash player version (if any) is detected at this Adobe page? See the little box titled "Version Information". Does it match the latest available version from the table below that? 

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

---

### Post by heroquestelf on 2016-01-21
It says, "You have version 11,2,202,559 installed", and that's the current Linux Version.

I got Chromium up and running... that is at least a fix of some kind.

---

### Post by Yellow Pasque on 2016-01-21
You can try Fresh Player, which allows you to use PPAPI/Pepper Flash in Firefox. There is a packaged version here: [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)
Make sure your remove your current Flash install first. I use/build it myself and find it works well on my Debian system.

---

### Post by Dennis N on 2016-01-21
You should be able to use that version in Firefox without any blocking. I have the same version, and haven't seen any warnings or blocking. Could it be a problem with a particular web site?

Could you possibly give an example of a web page URL which is telling you the player is outdated, so we can see if the web page is somehow at fault?

---

### Post by monkeybrain20122 on 2016-01-21
> **Temüjin said:**
> You can try Fresh Player, which allows you to use PPAPI/Pepper Flash in Firefox. There is a packaged version here: [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)
Make sure your remove your current Flash install first. I use/build it myself and find it works well on my Debian system.

+1 for freshplayer, it works seamlessly here, though need to disable vaapi and vdpau on some sites (I compiled it myself, not sure whether webupd8's build has hardware acceleration enabled)

You don't need to remove anything, Firefox automatically chooses the highest version.

---

### Post by monkeybrain20122 on 2016-01-21
> **Dennis N said:**
> You should be able to use that version in Firefox without any blocking. I have the same version, and haven't seen any warnings or blocking. Could it be a problem with a particular web site?

Could you possibly give an example of a web page URL which is telling you the player is outdated, so we can see if the web page is somehow at fault?

A few websites require up to date flash. 11.2 doesn't work on those. 11.2 is pretty useless now with freshplayer except maybe for some streaming sites which require flash + hal to work (e. Hulu according to other threads, hal is not officially supported and works only with 11.2), then there is also pipelight flash (Windows flash working in a wine wrapper)

---

### Post by Dennis N on 2016-01-21
> **monkeybrain20122 said:**
> A few websites require up to date flash. 11.2 doesn't work on those. 11.2 is pretty useless now with freshplayer except maybe for some streaming sites which require flash + hal to work (e. Hulu according to other threads, hal is not officially supported and works only with 11.2), then there is also pipelight flash (Windows flash working in a wine wrapper)

Interesting. As I said, I have yet to encounter any warnings or failure of regular flash to work. Do you have an example? I'm interested to see one. Thanks. Probably those sites are using some new features not in 11.x flash.

Anyway, I need the Firefox with hal-flash as you mention. Otherwise, I cannot log-in to take advantage of my cable TV tie-ins.

---

### Post by monkeybrain20122 on 2016-01-21
> **Dennis N said:**
> Interesting. As I said, I have yet to encounter any warnings or failure of regular flash to work. Do you have an example? I'm interested to see one. Thanks. Probably those sites are using some new features not in 11.x flash.

Anyway, I need the Firefox with hal-flash as you mention. Otherwise, I cannot log-in to take advantage of my cable TV tie-ins.

Hi, some news or TV sites require up to date flash. e.g [cp24.com]("http://cp24.com")

---

### Post by Dennis N on 2016-01-21
Yes, I see the problem with the front page video in Firefox. I then tried to view it in Chromium Browser, but I was again informed I needed to update Flash. I have 20.0.0.267, which was the latest on the Adobe page several days ago, but the latest is now 20.0.0.286, and that has not been offered by updates of adobe-flashplugin yet. That site seems to have little margin for getting behind. I'll try again after the next update of the plugin.

Update: (20 minutes later). I tried my Chrome Browser, which was just updated, and it now has flash 20.0.0.286. The web site video on Kyle Lowry of the Raptors (and the following news videos) worked fine with that.

---

### Post by heroquestelf on 2016-01-21
FRESH PLAYER FTW!!!
[IMG]http://i64.tinypic.com/33olbgz.jpg[/IMG]

---

