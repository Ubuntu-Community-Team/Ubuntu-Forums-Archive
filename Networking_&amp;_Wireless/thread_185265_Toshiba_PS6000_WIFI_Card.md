---
title: "Toshiba PS6000 WIFI Card"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by nilsh on 2006-05-31
[http://www.ubuntuforums.org/gallery/showimage.php?i=2761&original=1&c=2]("http://www.ubuntuforums.org/gallery/showimage.php?i=2761&original=1&c=2")

Hello! That link is for a screenshot of my lspci, and my network settings.

It says that WIFI is active, but when I try to only use that one (I unplug my ethernet cable) it still wont connect to my unsecure philips network. Every other pc connects, so I dont know what to do.  Any suggestions?

---

### Post by evandec on 2006-05-31
I am atually having a similar problem. It says that my card is active and can see the networks but when I go to open firefox all it says it "looking for xxx.com"

---

### Post by jml on 2006-05-31
rather than just unplugging the ethernet card, go into the networking utility and actually deactivate it.  Then reboot the system.  Linux does not handle multiple active network cards (wired or wireless) very well.  Hope this idea is of help.

Joe

---

### Post by nilsh on 2006-05-31
Thanks, I'll try that!

---

### Post by nickm on 2006-05-31
I googled your Pc make and didnt find anything, what wireless card does it use? 
If it is a broadcom chipset you might find my guide useful [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
If not, you may still find it useful :)

Jml, i'v never seen the issue you speak of, i think your confusing ubuntu with windows...

---

### Post by nilsh on 2006-06-22
Well I have no idea what Wireless card this pc use, but I made a screenshot of my device manager if that helps. Just tell me what to do, I am quite the nooblet!

[IMG]http://student.umb.no/~nilsh/temp/Screenshot.png[/IMG]

---

