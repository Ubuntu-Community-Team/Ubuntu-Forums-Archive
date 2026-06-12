---
title: "JACK question"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by jdix123 on 2008-02-06
This seems like elementary to me -- 

But how the crap do you start JACK?

I just installed the Ubuntu Studio packages and all of the audio apps depend on JACK.  Ok, that's nice.  How do I start it?

---

### Post by el murciélago veloz on 2008-02-06
Hello, try to type " qjackctl " in the terminal, for example.

You can access this command too in the "Applications" menu ----> "Sound and Video" (it depends on your install) ------> JACK Control

 ....... " User interface for controlling the JACK sound server
Qjackctl offers a user interface for controlling the JACK sound server
daemon. At the same time it figures as a JACK patch bay and monitoring
tool. ...... "  [ extract from Synaptic description of _qjackctl_

I hope it will be useful to you !!

---

### Post by jdix123 on 2008-02-06
right.  I get a pretty long error message.

Looks like where it goes wrong is this:

```

control device hw:0
the playback device "hw:0" is already in use.  Please stop the application using it and run JACK again.

```

---

### Post by el murciélago veloz on 2008-02-07
Hi. Maybe these trheads can help you : 

[http://ubuntuforums.org/archive/index.php/t-450336.html]("http://ubuntuforums.org/archive/index.php/t-450336.html")

[http://ubuntuforums.org/archive/index.php/t-221534.html]("http://ubuntuforums.org/archive/index.php/t-221534.html")

Bye.

---

### Post by jdix123 on 2008-02-07
So...basically I have to restart.

What am I, a windows user?

Anyway, thanks for the info.  Maybe I'll just turn hibernate off?

---

