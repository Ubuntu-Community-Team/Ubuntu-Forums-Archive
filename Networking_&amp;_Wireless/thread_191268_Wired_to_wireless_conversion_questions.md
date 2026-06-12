---
title: "Wired to wireless conversion questions"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by djsroknrol on 2006-06-07
Yesterday I was given a Linksys router and PCI card and I'm considering getting 2 more cards to change the LAN over to wireless.

My question(s) is(are), what will I need to change, if anything in my Ubuntu 'puter to make the transition to WLAN? Will Ubuntu see the card when I change it?...I don't have the model numbers of the items handy, but is Linksys pretty reliable to use in Ubuntu? 

Thanks for all the help in the past...I know someone will come thru for me...

---

### Post by Dr. Nick on 2006-06-07
unfortuantely you cant get anywhere model numbers. I have a linksys wireless usb. The model I had has atleast 4 revisions but the same name, Linksys and others are notiorious for switching chipsets but not renaming the cards, so you could get lucky or unlucky.

Depending on chipsets of the cards ubuntu may see it easily out of the box , or you may have to play a bit to get it going.

---

### Post by djsroknrol on 2006-06-07
The NIC card is a Linksys Model WMP54G....Now that I'm looking at it, it's hard to tell what chipset is inside as it appears to be a sealed unit....anyone with any experiences with this model NIC ?...The router shouldn't be a problem, but the card, who knows...I guess it's easier to get 3 new NIC's than to go thru grief trying to configure this one if it's not compatable...

---

### Post by Dr. Nick on 2006-06-07
you can look here
[http://www.ubuntuforums.org/showthread.php?t=161376]("http://www.ubuntuforums.org/showthread.php?t=161376")

a few instruction on how to set it up. I have no personal expierence with it though. Usually alot of wireless cards will work if you use ndiswrapper (tons of info on the forums for it) so if it doesnt work natively you still have a good shot at getting it with ndiswrapper+windows drivers. You may just start with 1 and see how it goes, then if its good grab  afew more, just make sure they are the same version if applicale. The chipset isnt marked on the box or card, you may see mention in a file on the cd, or just do what i did and look at the version online where other people already know :)

---

