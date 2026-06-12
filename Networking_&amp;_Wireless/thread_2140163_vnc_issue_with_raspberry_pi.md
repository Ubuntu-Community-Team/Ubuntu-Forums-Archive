---
title: "vnc issue with raspberry pi"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by richpants on 2013-04-28
I am trying to connect with a raspberry pi via remote desktop viewer, and through the terminal. In remote desktop viewer, I get an error stating the connection was closed. In the terminal I get: 
[COLOR=#333333][FONT=Helvetica Neue]rich@rich-computer:~$ vncviewer raspberrypi:1[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Couldn't convert 'raspberrypi' to host address[/FONT][/COLOR]

[FONT=Helvetica Neue][COLOR=#333333]I have tightvnc installed on the pi, and have been following a tutorial at [/COLOR][/FONT][http://learn.adafruit.com/adafruit-raspberry-pi-lesson-7-remote-control-with-vnc/overview](http://learn.adafruit.com/adafruit-raspberry-pi-lesson-7-remote-control-with-vnc/overview), however strangely with the raspberry pi being Linux based all of the tutorials are for pc's and macs. 
I posted this as well on a raspberry pi forum. I am a noob, and have never used VNC for anything else, so I might just not being doing some sort of simple configuration or other step which would seem second nature to someone who knows what they are doing. Any help would be appreciated.
Thanks

---

### Post by richpants on 2013-04-29
[COLOR=#333333][FONT=Helvetica Neue]This worked! solved
Try using the IP address of the raspberry pi (lookup from the router), and try[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]% vncviewer <IP address of the pi>:1[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]How do you ssh into the pi from putty? Do you use the name raspberrypi, or the IP address.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]When you ssh using putty the IP address of the pi is also shown in the title bar of the ssh window.[/FONT][/COLOR]

---

