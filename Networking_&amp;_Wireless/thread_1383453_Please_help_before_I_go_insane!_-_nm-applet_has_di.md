---
title: "Please help before I go insane! - nm-applet has disappeared."
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by eakergd on 2010-01-17
I have been trying to figure this out for several days now.  BLUF: the Network Manager applet has disappeared, and I can no longer log on to my network.  I made sure that the notification area on the panel is there -- I un-installed and re-installed Network Manager several times (had to download the deb file and install with a usb key, since I don't have a network anymore) -- I checked to make sure network manager is in the startup applications, and I even added a separate entry in startup apps with the command line "nm-applet --sm-disable".

The thing that baffles me the most is that everything else about Network Manager seems to be running fine.  When I open a console and type nm-tool, I see the interface and I can even see my wireless router.

ps -ef | grep nm-applet returns the following:

eakers    14605 13955  0  16:35 pts/0    00:00:00 grep nm-applet

(I have no idea if that means it is running or not.).

While I'd like to get all this running back to normal, I'd be satisfied with a work-around that gives me back my network.

I'm running xubuntu 9.04 on an old shuttle that I built.  The wireless card is a Hama wireless 54G that has been working fine for about 2 months.  Oh, I did take it all apart last night and re-seat all the cards in the motherboard, but that didn't help anything.

PLEASE SOMEONE HELP BEFORE I HAVE TO CHECK MYSELF IN TO A PSYCH HOSPITAL!

---

### Post by alexfish on 2010-01-17
if your sure that the applet has been put back in the menu bar / have you rebooted the computer

---

### Post by eakergd on 2010-01-17
Yes, tried just a logoff and a logon, then tried a full reboot.  Still not working.

---

### Post by eakergd on 2010-01-17
Bump - please -- someone??

---

### Post by pastalavista on 2010-01-17
I believe nm-applet is a gnome package and you're probably missing some dependencies. You might try [installing wicd]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wicd").

---

### Post by eakergd on 2010-01-17
Thanks for the reply.  I'll try it.  Don't know how the dependencies could be missing when it was working fine for 2 months, but I'm so frustrated with it that I'll try anything.

---

### Post by eakergd on 2010-01-18
Thanks Pastalavista -- WICD works.  Not quite as smooth of an interface as NM, but right now I couldn't care less.  WICD works while NM failed.  I guess that is a good thing about using Linux -- there's always more than one way to skin a cat -- not always the case with the competition.  :-)

---

