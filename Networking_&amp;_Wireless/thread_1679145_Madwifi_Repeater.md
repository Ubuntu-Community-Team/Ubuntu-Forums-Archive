---
title: "Madwifi Repeater"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by AlexQM on 2011-01-31
Hello,

I'm hoping I can a hand with the set up of Madwifi as a repeater?
I've searched the Ubuntu forums and the madwifi website to get as much info on how to create the setup but I've had <edit>NO</edit> luck!

There are two main different ways of setting up; The first sets up an AP (Access Point) followed by a STA (station VAP), adds WDS to both, set the name and channel of the AP that you've created, associate the STA with the network that you whttp://madwifi-project.org/wiki/UserDocs/UsersGuideExamplesant to extend and then  set up a bridge between the two virtual wifi connections you've created.
The second way sets up an AP followed by a connection in WDS mode and uses the MAC address of the target access point of the network you're trying to extend.

Try as I might, I am unable to get this to work. I have the most success with the first way as I am able to get the AP up and the STA connects to the desired network but the AP has WPA/PSK given to it when I didn't even specify it!

The second way doesn't communicate with the desired network currently, not sure why but that could be me not getting the instructions correct.

This is what I'm following: [http://madwifi-project.org/wiki/UserDocs/WDSBridge](http://madwifi-project.org/wiki/UserDocs/WDSBridge)
as well as: [http://madwifi-project.org/wiki/UserDocs/UsersGuideExamples](http://madwifi-project.org/wiki/UserDocs/UsersGuideExamples)

I hope somebody can give me some advice with this!

Alex

---

### Post by AlexQM on 2011-01-31
Ok, have found documentation that helps me turn off WPA but am still not being allocated an IP address meaning that the connection isn't being passed on to my network's router which is handing DHCP?
Any ideas people?

---

### Post by AlexQM on 2011-02-02
any ideas? has anyone else successfully set up a repeater bridge?

---

### Post by AlexQM on 2011-02-16
bump

---

