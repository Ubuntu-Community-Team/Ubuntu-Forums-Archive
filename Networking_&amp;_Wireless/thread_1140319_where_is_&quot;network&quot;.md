---
title: "where is &quot;network&quot;"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by newuser-umesh on 2009-04-27
i recently got desktop ubuntu 8.10 by post.
i installed it without any trouble.

i have a dialup connection. and i want to connect internet with dialup ....

the ubuntu documentation says. 
click on   System/Administration/Network .... but i don;t see any network link to click on,.. 

but instead. i got the link  System/Administration/Network Tools

i google the pages to connect the dialup and all the sites says the same thing with the figure... but i don't have the link Network alone to click on.

i am a begineer to it. help me out on it

---

### Post by newuser-umesh on 2009-04-27
5. Modems 
Identifying your modem 
Connecting with a modem


i already did the first step

Identifying your modem 

since there is no option of clicking system/networking...

i am stuck there.

---

### Post by Loosewheel on 2009-04-27
Hi newuser-umesh

the "Network' they refer to is 'Network-Admin' I believe, and it is not installed by default on 8.10.
Try right click on the 'Network-Manager' icon located next to the clock, and set it up from there.

---

### Post by ddrichardson on 2009-04-27
It isn't in the current help system but we couldn't raise an SRU for Intrepid because the community wouldn't reach a consensus on what to put in it.

[https://bugs.launchpad.net/ubuntu-doc/hardy/+bug/310331](https://bugs.launchpad.net/ubuntu-doc/hardy/+bug/310331)

The application you refer to is called network-manager-gnome and was removed in Intrepid the steps I suggested are:

Install the network-manager-gnome package (sudo apt-get install network-manager-gnome
Open System->Administration->Network
Click Unlock
Enter your password and click authenticate
In the connections tab, click point to point connection and click properties
Tick  "Enable this connection"
Choose Serial Modem from the connection type drop down
Under internet service provider data, enter the phone number and dial prefix
Under account data enter your password and username
Click the modem tab
Choose the modem settings you require
Click OK
Click Close


This requires you to get the package from the Internet of course.

---

