---
title: "iPhone as wireless based input to lirc"
date: 2008-06-02
forum: Mythbuntu
---

### Post by stueng on 2008-06-02
Does anyone know of a method, application, project which would enable the iPhone (hacked) to run a client/server application which would send commands to a MythTV front-end over wi-fi/lan. 

I was thinking that there might be some kind of application that can be installed on the iPhone which would send via wifi commands to a server which would then in turn send commands to the MythTV front-end - injecting into irexec or something?

Stu

---

### Post by uopjohnson on 2008-06-03
If you only want to hit the frontend you can leave lirc out of it entirely.  Every mythfrontend has an option to take commands over telenet.  I believe that Mythweb in .21 has an example remote that may or may not work with an iphone, but it would give you an idea of how to build your own.  

Telnet socket info:
[http://mythtv.org/wiki/index.php/Telnet_socket](http://mythtv.org/wiki/index.php/Telnet_socket)

---

