---
title: "Enabling wireless hardware in Lubuntu"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by komarx6 on 2012-10-20
It is rare situtuation when my PCI wireless card works, it's Linksys card that should be plugged in side port of my laptop. I also have less powerful built-in card.
It happends very often that Linksys card  does not work. There are 2 lights and only one is on. When it is connected to net both lights blink. And when that card does not work, another one makes problems to. There is only 2 networks available and there should be at least 6, and there are problems establishing connection.
When Linksys card works than built-in card works also and I can choose what card to use and have all networks available in networks menu.
It happened few times that cards work instantly and connect to internet when I start computer, but it's been a while.
I now that is not hardware problem because both cards work OK when I start them manually in puppy linux, and, puppy and Lubuntu are using same drivers.

I'll try to give few screenshots if i can, because my english is bad.
To explain situation more:
 When I start Puppy from usb, Linksys card behaves just like in Lubuntu, only one light is on, and it does not blink. But than I go to Intertnet Connection Wizard and activate them manually. And than corresponding interfaces appear when I run ifconfig. So I think that I just should  activate cards some how.
Drivers are loaded, so ```
modprobe ath5k
```  does not solve the problem.

Does anyone knows how to do it?

---

