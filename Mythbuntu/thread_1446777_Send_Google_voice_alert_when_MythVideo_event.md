---
title: "Send Google voice alert when MythVideo event"
date: 2010-04-04
forum: Mythbuntu
---

### Post by frego on 2010-04-04
I would like to be sent an alert via email or ideally, google voice to call my phone upon certain videos being watched in MythVideo.  I've set my log file up and I can grep for a certain keyword.  Does anyone know how to send something by google voice?  I imagine I need a service which watches the log file and then sends the message.  Does anyone know of a similar example I could start with?

---

### Post by superm1 on 2010-04-04
This is what you'll want to integrate with:

[http://code.google.com/p/pygooglevoice/](http://code.google.com/p/pygooglevoice/)

Get it working on the command line and then you can hook it up to your monitoring system.

---

