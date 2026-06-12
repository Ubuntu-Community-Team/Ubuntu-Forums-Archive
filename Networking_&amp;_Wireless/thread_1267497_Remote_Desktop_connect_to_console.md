---
title: "Remote Desktop connect to console"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-09-15
So I have a computer running Windows server 2003 and when I connect it creates a new session. I found [this]("http://operation420.net/forum/viewtopic.php?f=22&t=784") information and discovered I can use the "/console" use the existing session.

When I type "servername /console" it the Terminal Server client it gives a connection error and when I run the terminal services client with "tsclient /console" it runs but when I connect it still opens a new session.

How do I connect to a computer running Server 2003 and use the existing/console session?

---

### Post by gte731 on 2009-09-17
Being a newbie to all of this Ubuntu stuff, I usually don't find any topics where I can be of help, but I currently am able to connect to Server 2003 from 9.04's built-in Terminal Server Client by checking Attach to Console on the Performance tab.  This appears to be the equivalent of MSTSC /console in Windows.

My problem is that I'm running TSC in full-screen mode, but can't switch back to my 9.04 Desktop if I need to.

Hope this helps!

---

### Post by RealG187 on 2009-09-17
I'm on Windows now (dual boot still set to Windows and I wasn't there to pick Ubuntu, so I just started using Windows.

I'll check when I reboot...

---

### Post by uoirej on 2010-01-13
> **gte731 said:**
> Being a newbie to all of this Ubuntu stuff, I usually don't find any topics where I can be of help, but I currently am able to connect to Server 2003 from 9.04's built-in Terminal Server Client by checking Attach to Console on the Performance tab.  This appears to be the equivalent of MSTSC /console in Windows.

gte731, thank you very much. That was exactly what I've been looking for.

> **gte731 said:**
> My problem is that I'm running TSC in full-screen mode, but can't switch back to my 9.04 Desktop if I need to.

Did you try Ctrl+Alt+Enter?

---

### Post by RealG187 on 2010-02-26
Also found this way:

computername -0

Now to figure out how to do it from my Windows Mobile phone...

---

### Post by capede on 2010-12-08
is that possible if only i would like to share any device ( such as : USB, wifi, or even webcam ) or just remotely running some 'AT' command on neighbor's modem ?

---

