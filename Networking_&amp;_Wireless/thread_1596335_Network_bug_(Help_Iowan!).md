---
title: "Network bug? (Help Iowan!)"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by relay_man on 2010-10-14
I've found this morning that the session indicator applet I have in my upper panel on my desktop can completely kill the wired connection to my router.  Let me explain further.
Yesterday afternoon I booted my desktop unit and shortly after boot rec'd an error message that an applet in the panel had a problem.  I was asked if the applet should be removed from the panel.  I chose yes.
I finished my session but had to shut down from the command line due to the fact that the session indicator applet had been removed from the upper panel.  Not really a big deal. (or so I thought)

This morning, I booted my desktop unit again and found that the usual network indicator in the upper panel had changed from the up/down arrow to that of a wireless network indication with a red line through it.  hmmmmm...
Of course, there was no active network connection, and I couldn't go to network manager and get things going again either.
For some reason, I remembered the deleted applet and restored it to the upper panel, restarted and networking was restored and operated normally.
To test this, I manually removed the session indicator applet from the upper panel once again restarted the desktop unit.
Sure enough, NO network connection.

My questions are:

1) What is the connection between the session indicator applet and network functions?

2) Are lots of people customizing their panels, removing the session indicator applet in favor of the shutdown button (another option in the panel manager window) and killing their network functionality?

---

### Post by Iowan on 2010-10-14
[s]I'm a bit confused by "session indicator applet". That's different from Network Manager applet?[/s]

Never mind... I found it as Indicator Applet Session. I've never tried removing it.

---

### Post by relay_man on 2010-10-16
My apologies.  You are correct. Indicator Applet Session.

My main concern was that possibly other users are removing this from their panels and experiencing the network connection failure that I've had.

I guess if that were the case however, you would have seen several instances by now.


Thanks

---

### Post by Iowan on 2010-10-16
Might be worth filing (or checking for similar) [bug report]("https://bugs.launchpad.net/ubuntu/").
There used to be a "How to file a bug report" thread - but I can't locate it at the moment.
(:oops: I've never been called out in a title before...)

---

### Post by bkratz on 2010-10-16
> **Iowan said:**
> Might be worth filing (or checking for similar) [bug report]("https://bugs.launchpad.net/ubuntu/").
There used to be a "How to file a bug report" thread - but I can't locate it at the moment.
(:oops: I've never been called out in a title before...)

Is this the one?

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by Iowan on 2010-10-16
:) That's *probably* it :)

---

### Post by relay_man on 2010-10-16
Thanks bkratz and Iowan

I've searched the forums a bit, but I'll look more.
I'll check out launchpad.
If I don't find anything there, I'll attempt to file a bug report

Thanks again

---

