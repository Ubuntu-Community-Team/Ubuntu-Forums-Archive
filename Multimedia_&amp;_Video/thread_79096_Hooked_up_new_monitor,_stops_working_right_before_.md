---
title: "Hooked up new monitor, stops working right before I get to the login screen"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by PropheticSong49 on 2005-10-19
I set up a pc with Ubuntu 5.10 and it works perfectly. When I hooked up another monitor to it, it booted normally, went through the initialization, and as soon as it is ready to go to the login screen the monitor shuts off. I have never had this problem with any linux distro before. Does anyone have any ideas why this is happening? Any help would be greatly appreciated.


-Eric
[[IMG]http://www.christhouse.com/images/christhousebanner_w407px.jpg[/IMG]]("http://www.christhouse.com")

---

### Post by metoo on 2005-10-20
May be your XServer is set to a resolution/frequency not suitable for you monitor (e.g. replacing a CRT with a TFT screen). Then the monitor shuts down to protect itself.

Boot into recovery mode (text mode) or use the old monitor and check your /etc/X11/xorg.conf file.

In the 
Section "Monitor"

See if the settings for HorizSync (kHz) and VertRefresh (Hz) matches those from you new monitor. Get them from the manual.

Another possibility:

In the
Section "Module"
there can be a line
Load "ddc"
this is AFAIK the module which reads your monitor and sets the limits according to what the monitor says it supports.
If it isn't in there, add it.
If it is in there and you are sure about the rates set in 'Section "Monitor" ' above, set an # at the begin of the line, so it will not be loaded. Could be, that the monitor reports back bogus values to the xserver.

Do the max. resolution of the 2 monitors differ?

In
Section "Screen"

you have a line "Default Depth" 24
24 is an example, can be differ on your system.
This is the default colour depth when starting X.
Look below under this figure (here for 24):
SubSection "Display"
 Depth 24
 Modes  ....
The first resolution in the Modes line is the one which the xserver starts with. Make sure, that you monitor supports this.

Be careful, even if today most monitors shut of to protect themself if they get ranges over their limits.

Is there an error message from the xserver in  /var/log/Xorg.0.log ?

---

### Post by roberto guimaraes on 2005-10-20
I have the same problem. I d'ont know whats happen.
When I try:

sudo startx 

grafical mode is ok.

---

### Post by roberto guimaraes on 2005-10-20
My solution:
Delete in /home/"username" .ICEauthority and .Xautority solve my problem, but I don 't know why this happened.

---

