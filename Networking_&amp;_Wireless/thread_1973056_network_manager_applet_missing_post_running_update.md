---
title: "network manager applet missing post running update"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by beopen on 2012-05-04
hi all,

my system : Ubuntu lucid 10.04
 
I today updated the system through the update manager. System is up-todate. Post update, I find the network manager icon is gone. Not only that, I cant find it in the ‘add to panel’ section either. I tried all the measures mentioned on this forum post [link]("http://ubuntuforums.org/showthread.php?t=1469625&highlight=network+manager+icon+missing")  but none of that works now. Now I am without acess to internet from this ubuntu installation.
Pls help me solve this or any other way to connect to the internet. I use ADSL Broadband.


Regards.

---

### Post by beopen on 2012-05-05
hi all,
just now i got this solved. The Network manager applet on the panel which i said vanished post the  update did not require any of the commands of the link which i gave  above. Rather i found that the** &#901; Notification Area applet' **has to be enabled and the network manager applet automatically gets seen on the panel. 
Balance all those commands etc mentioned in that link of my previous post was not at all necessary in this case.
 1. Because in the  system -->>preferences ---> startup  applications  , the network manager is shown as installed under startup  programs
2. secondly in System Monitor---> Processes i could also see the nm-applet loaded.

This solution i got on this [link]("http://askubuntu.com/questions/1974/how-can-i-add-the-network-manager-applet-to-the-panel-after-removing")
But nevertheless it is a fact that something or other gets blown away on  the panel after an upgrade. why i dont understand, maybe the developers  should look again to the stability factor.

So i conclude hereby my problem is solved.

regards

---

