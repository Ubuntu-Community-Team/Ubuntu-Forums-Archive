---
title: "Brief Wireless connection then disconnection"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by danipoak on 2009-05-07
This is my first forum post here.  I used to use Linux quite a bit and then switched over to OSX for awhile so I am relatively familiar with Linux.  I want to put the new Ubuntu on my wifes laptop since neither of us can stand Windows.  I am currently running a live dvd on it because I want to make sure everything works well before I go ahead with the install.  Here's as much info as I can give:

Its a gateway laptop and the wireless card is detected on start up.  I can see all kinds of wireless networks as well.  My network is a hidden network and it is on an Apple airport express router.  I click on the wireless icon in the top right corner, go to connect to hidden wireless network then select the connection type as new, put in the wireless network name and choose the security type as wpa/2 personal and put in my wireless network key.  It turns to to led type looking lights with a thing circleing them.  One is green, then eventually the other turns green with the thing still circles them for a good 30 seconds to a minute after which a box pops up that says disconnected and then goes back to the wireless bars with an x in the corner.  There is one unprotected network that I can pick up and I have had success with connecting to that network, it's just mine that I cannot get to work.

---

### Post by CyanideSyntax on 2009-05-07
check the encryption settings.
most base stations (im not familiar with an Airports,) use either AES or TKIP.

most default to AES, but if your Airport is on TKIP, then youll have to edit your network settings to change it on your ubuntu machine.

---

### Post by danipoak on 2009-05-07
> **CyanideSyntax said:**
> check the encryption settings.
most base stations (im not familiar with an Airports,) use either AES or TKIP.

most default to AES, but if your Airport is on TKIP, then youll have to edit your network settings to change it on your ubuntu machine.

That fixed the problem thanks.  Turns out WPA is defaulted to TKIP whereas WPA2 is defaulted to AES, I just switched to WPA2.

---

### Post by bfr420 on 2009-07-15
Where do I find the setting to change from AES to TKIP?

---

