---
title: "Dans Guardian and tinyproxy Install Process Question!"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-05-05
Hi.
I am following this [guide]("http://www.instructables.com/id/Set_up_web_content_filtering_in_4_steps_with_Ubunt/") on installing Dans Guardian.

Everything was going smoothly until [step 3]("http://www.instructables.com/id/S2I9GKLFKD1KHZT/").

These are the outputs of the two lines of code:

```
$ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                           Error connecting to parent proxy
```

```
$ sudo /etc/init.d/tinyproxy start
Starting tinyproxy: tinyproxy.

```

As you can see, tinyproxy seems fine but why is there a problem with Dans Guardian?

---

### Post by Rytron on 2009-05-06
I've tried some of these :

[http://ubuntuforums.org/showthread.php?t=226298&highlight=dansguardian+gui](http://ubuntuforums.org/showthread.php?t=226298&highlight=dansguardian+gui)
[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)
[http://ubuntuforums.org/showthread.php?t=237355](http://ubuntuforums.org/showthread.php?t=237355)
[http://www.instructables.com/id/Set_up_web_content_filtering_in_4_steps_with_Ubunt/](http://www.instructables.com/id/Set_up_web_content_filtering_in_4_steps_with_Ubunt/)

Is there a straightforward way to get and install software for Parental Control over internet use?

I tried this:[http://ubuntuforums.org/attachment.php?attachmentid=13495&d=1154337298](http://ubuntuforums.org/attachment.php?attachmentid=13495&d=1154337298)
but it messed up my connection. I couldn't access any web pages. I had to uninstall dansguardian,firehol & tinyproxy to get back to using the internet.

---

