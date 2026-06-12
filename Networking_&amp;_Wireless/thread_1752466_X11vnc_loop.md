---
title: "X11vnc loop"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by SubCool on 2011-05-07
Hey everyone,
i was looking for some help on something. 
i am trying to setup x11vnc on startup, by following this guide: 

*[http://ubuntuguide.org/wiki/Ubuntu:Natty#X11VNC_Server](http://ubuntuguide.org/wiki/Ubuntu:Natty#X11VNC_Server)*


using this line:
[I]
echo "/usr/bin/x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0" > ~/.config/autostart/x11vnc.sh
chmod +x ~/.config/autostart/x11vnc.sh
[/I]
I attempted to accomplish my task.
But- it loops, and causes my computer to be overun by thousands of instances of x11vnc. 
When i test the command:
[I]
x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0
[/I]
Or run the script.

the following occurs:

[I]
 ~/.config/autostart/x11vnc.sh 

 --- x11vnc loop: 1 ---

 --- x11vnc loop: waiting for: 10656

enabling -bg in -loopbg mode
PORT=5900

 --- x11vnc loop: sleeping 500 ms ---


 --- x11vnc loop: 2 ---

 --- x11vnc loop: waiting for: 10658

enabling -bg in -loopbg mode
PORT=5900

 --- x11vnc loop: sleeping 500 ms ---


 --- x11vnc loop: 3 ---

[/I]


Please help.

Ty.

SubCool

---

### Post by SteveDee on 2011-05-08
I have a few simple servers running Lubuntu. I auto-start x11vnc by running a script like this:-
```

 #!/bin/sh
 x11vnc -forever -display :0

```

I think you need to take a closer look at the -loopbg option. Maybe take it out. Or maybe start with my simple script and add your password commands.

---

### Post by krunge on 2011-05-08
I think you want "-loop" not "-loopbg". (read the -loop help output for more info)

Make sure there is no other VNC server listening on port 5900, otherwise it will continously fail to listen on that port...

I don't think "-forever" makes any sense in this mode of operation. OTOH, you might do better to keep "-forever" and get rid of "-loop/-loopbg" (the loop stuff is kind of a hack to keep restarting itself in a loop...)

---

### Post by SubCool on 2012-01-11
I have tried the suggested fix- and it works on boot. but after you log out- the session ends and you cant log back in.

---

