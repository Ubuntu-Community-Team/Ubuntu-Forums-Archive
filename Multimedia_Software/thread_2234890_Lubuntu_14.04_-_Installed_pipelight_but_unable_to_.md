---
title: "Lubuntu 14.04 - Installed pipelight but unable to stream Netflix"
date: 2014-07-17
forum: Multimedia Software
---

### Post by cdza1971 on 2014-07-17
I installed pipelight from cmd line in Lubuntu 14.04 as per the below   instructions on the pipelight site for ubuntu.

[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

 then enabled silverlight  5.1 as per [http://pipelight.net/cms/installation.html#section_2](http://pipelight.net/cms/installation.html#section_2).

[http://pipelight.net/cms/plugin-silverlight.html](http://pipelight.net/cms/plugin-silverlight.html)



I then installed a user agent switcher addon  in Firefox as per [http://pipelight.net/cms/installation-user-agent.html](http://pipelight.net/cms/installation-user-agent.html)

I verified the pipelight install on [http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html)

   I am able to browse to netflix site and select a movie for  streaming. But then the stream never starts... I just get a circle going  round (like a wait circle) and then I get a netflix error that there  was a connection issue. But I verified that I am able to connect just  fine and even stream video from youtube in another tab. I have tried  both WIFI as well as wired connections but with no success in making  netflix work. Please can you help? If you need any more info from me please let me know.

---

### Post by QIII on 2014-07-17
Hello!

I would highly recommend Andrew's instructions [here]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html").  He does a really good job of testing.

I use Kubuntu and it works like a charm.  I believe Andrew said somewhere on the site that he uses Unity, but I can't say for sure.

Make sure to read all the way through.  I found that enabling widevine caused some real problems, so don't do that.

Also, make sure to install the User Agent Switcher as instructed.

Cheers!

---

### Post by cdza1971 on 2014-07-18
Thank you for your reply. I also should mention that  in frustration I also installed wine separately from the command line. Should I uninstall wine in addition to  pipelight before I start on Andrew's instructions? If so what's the recommmended commands?

---

### Post by QIII on 2014-07-18
Did you install Wine via an Ubuntu package management tool?

If so, you can use that tool or the command line to uninstall it.

Removing it may not be necessary, but Andrew's instructions make it clean and he updates his PPAs as new versions are available.

---

### Post by yancek on 2014-07-18
I don't think it is necessary to remove the original wine if you previously had it installed, before .wine-pipelight.  If I remember correctly from my reading, this was a problem with Netflix Desktop.  You could probably get correct information at the pipelight FAQ site.  You should also be able to get more info at the pipelight diagnotic site at the link below.  If you get an OK for everything, that would complicate things if it shows OK but still doesn't work.  I've got it working on 12.04, 14.04 and Mint 17 although there usually is a problem coordinating sound/video at the start of any movie.

[http://fds-team.de/pipelight/](http://fds-team.de/pipelight/)

---

### Post by cdza1971 on 2014-08-08
Hi I removed wine and pipelight packages and then re-installed them as per Andrew's instructions at [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html) but netflix still does not work . Same issue as before

---

