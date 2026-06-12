---
title: "Multiple Monitor Definitions/Switch based on session"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by pdxplorer on 2007-06-05
Greetings,
I shall get right to the point ;) Here is my goal:

I want to be able to boot up Ubuntu FF and be presented with a login screen.  I want to be able to login using the default session at the default resolutions.  Here is where things get tricky... I want to be able to select a different session at the login window and have it log me in using a different monitor/screen definition.

In other terms I have a machine that is sometimes connected to a standard display, and sometimes connected to a projector that requires some tweaking in the monitor/screen sections of the xorg.conf file to make the display work correctly.  I want to be able to use the sessions concept to switch between the two settings.

I have looked into the ServerLayout of the xorg.conf file and see that as a possible path to my solution but I do not know how to specify which ServerLayout gets used via the /usr/share/xsessions/projector.desktop and Exec-ed script defined within it.

Any assistance in this matter would be most appreciated.  If I have left out any critical details please let me know and I would be happy to supply them!

-Gadi

---

