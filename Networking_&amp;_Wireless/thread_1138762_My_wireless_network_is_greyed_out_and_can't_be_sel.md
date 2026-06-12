---
title: "My wireless network is greyed out and can't be selected, but my neighbours' aren't!"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by nogoodreason on 2009-04-26
Hi guys.  I've just installed Ubuntu 9.04 (x84) and am trying to get my Netgear WG111T dongle to connect to our network.

I began by installing ndisgtk.  Then I copied the drivers from the Netgear CD into a folder and opened them using ndisgtk.  While opening up ndisgtk gives me the error 'Unable to see if hardware is present' it must have at least partially worked, as I am now able to see the available wireless networks in my area.

However, while many of my neighbours' wifi connections are there, my own network (SKY03557) is greyed out, and I'm not able to select it. :(  (screenshot attached)

Now, there is security on my network so people need to enter a network key, but I'm sure the same is true of my neighbours yet they're not greyed out.


I am a complete Linux noob, so please give slow, simple answers, particularly if it involves the Terminal. :)

---

### Post by antikristian on 2009-04-26
Is your wireless network wpa encrypted?

---

### Post by nogoodreason on 2009-04-27
I believe it is, yes.

I tried the same technique with an older dongle we had lying around the house and was able to access all the networks, including my own.  As expected it prompted me for the key and it now works fine.

Although I'm still curious as to why an old dongle made by a relatively unheard of company (PEAK) managed this, while my shiny Netgear one wouldn't.  Weird.

---

### Post by antikristian on 2009-04-27
I think it might have something to do with the drivers you are using. Ndiswrapper is a wraper around windows drivers, so they are sometimes somewhat reduced in functionality.

I haven't tried this out myself, but I found this link about wpa and ndiswrapper [http://ubuntuportal.blogspot.com/2007/03/how-to-enable-wpa-with-ndiswrapper.html](http://ubuntuportal.blogspot.com/2007/03/how-to-enable-wpa-with-ndiswrapper.html)

---

