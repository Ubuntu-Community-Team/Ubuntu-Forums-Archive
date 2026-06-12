---
title: "Zoneminder - Installation Vivotek IP camera"
date: 2014-07-20
forum: Multimedia Software
---

### Post by daniele4 on 2014-07-20
I ask for help to install an IP Camera Vivotek fd6122
[COLOR=#000000][FONT=Ubuntu]([/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]**[manual]("https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/zoneminder/telecamere/vivotek%20fd6122.pdf")**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu] a pag. 62 URL syntax: [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]*http://<servername>/cgi-bin/video.jpg*[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu])

[/FONT][/COLOR]The camera works perfectly.
When I run his browser access: 192.168.xy: 8088/cgi-bin/video.jpg, 
ask me 
user:** root **
password: **mypassword **
and I see the cam on quietly browser. 

These are the settings of password security panel of the cam Vivotek
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/zoneminder/telecamere/vivotek%20Security.png[/IMG]


where you can see the infrmazioni parameters USER and PASSWORD:
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/zoneminder/telecamere/vivotek%20password.png[/IMG]

The cam VIVOTEK also works great from your panel: [http://192.168.xy:8088/snapshot.vspx](http://192.168.xy:8088/snapshot.vspx) 
and android phone.

when instead 
Zoneminder in the settings of your monitor, voice **Remote Host Name** 
I added **root: miapassword@192.168.x.y** 
and the rest of the Source tab as follows:


[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/zoneminder/telecamere/monitor%20vivotek_source.png[/IMG]
and General:
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/zoneminder/telecamere/monitor%20vivotek_general.png[/IMG]
but does not want to operate 
with a blue screen!


Curious clues are: 
1) The behavior of browsers not working only in the VIVOTEK, only on Firefox 
by directly entering USERNAME and PASSWORD (method working on other IP cameras) 
[B]root: [EMAIL="miapassword@192.168.xy"]miapassword@192.168.xy[/EMAIL]: 8088/cgi-bin/video.jpg
[/B]
2) I finally noticed that 
Zoneminder not like USERNAME and PASSWORD empty 
it is advisable to always use these two data otherwise, as happened in the other cam ip, 
does not display and shows the usual blue screen with timer and date working!

[COLOR=#333333][FONT=UbuntuRegular]3) I did not find the model here Vivotek in Zoneminder. 
I tried the settings for the similar model (**Vivotek FD8134**) at the [site of zoneminder]("http://www.zoneminder.com/wiki/index.php/Vivotek#FD8134")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]recommended settings Zoneminder (Vivotek FD8134):[/FONT][/COLOR]
Remote Protocol: RTSP 
Remote Method: RTP/RTSP 
Remote Host Name: Put in the cameras IP or hostname 
Remote Host Path: /live.sdp
[COLOR=#333333][FONT=UbuntuRegular]and both Zoneminder, both from the browser, but without success in both cases.[/FONT][/COLOR]

As soon as I entered USERNAME and PASSWORD Enchanted other ip cam worked 
However, except for the "squeamish" Vivotek! 
Help!

---

### Post by daniele4 on 2014-07-22
I disabled all other cam except VIVOTEK. 
I viewed the **log** window and gives me:
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/zoneminder/telecamere/zoneminder%20log%20finestra.png[/IMG]

help me!

---

### Post by info-velthuizen on 2014-12-05
Same problem here with Level One FCS1010 it's a similair cam as vivotek

---

