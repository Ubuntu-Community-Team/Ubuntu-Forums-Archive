---
title: "CQ60 laptop wireless problem PLZ HELP"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by breemiller on 2011-03-20
Hello!

Okay so I recently switched from windows 7 to ubuntu 10.10 and really like it.. Except ever since the switch I have had some major issues with my wireless connection. 

Directly following installation my computer would recognize the wireless network in our house and "establish the connection" but when I would try to open a browser or download ne new software screen would appear to be loading for a while (maybe 10-15 seconds)and then inform me connection had failed... it also seems relevant to mention this process seemed to interfere with other wireless devices in the house by temporarily cutting off their connection too.
I finally gave in and connected my laptop directly to the router unfortunately this had same end..:(

Interestingly enough I was able to connect to the internet through the wireless connection at school for a while but have since lost that ability and now it isn't recognizing any wireless networks

This problem has been progressing ever since I installed ubuntu a couple days ago.. I really like the operating system and really want to resolve this problem.

oh! 
PS: it now also seems note-worthy that during installation process my wifi enabler light was blinking on and of, and blue and orange.. i thought nothing of it at the time.. but maybe is relevant now?

~Any and all help is much appreciated and thank you in advanced.. I know there is a way to fix this issue, but I just cant seem to figure it out :P

---

### Post by uncaspi on 2011-03-20
Try sudo rfkill unblock

---

### Post by breemiller on 2011-03-21
options command was brought up but "unblock" command was not found?

---

### Post by uncaspi on 2011-03-21
Try rfkill -help for listing commands.

You can see if the radio is blocked by sudo rfkill list

---

### Post by uncaspi on 2011-03-21
Sorry about wrong syntax. The right is.
sudo rfkill help
sudo rfkill unblock wifi

---

### Post by breemiller on 2011-03-21
okay tried commands and took a screenshot which then uploaded to the computer i'm currently using via flash drive... figured it would be more accurate than typing it all out... so heres the link
[http://i1219.photobucket.com/albums/dd436/breemiller1/rfkill.png](http://i1219.photobucket.com/albums/dd436/breemiller1/rfkill.png)

---

