---
title: "Annoyance connecting to hidden wireless networks"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by schongal on 2009-09-14
First of all, my wireless setup generally works fine.  I'm mostly asking this question for my own enlightenment, since it seems more like a bug in NetworkManager.  But I'm kinda linuxretarded and I couldn't say for sure.

At school, I have access to a WPA2 Enterprise network with TLS authentication.  I boot up my laptop (Dell InspironE1505 with Jaunty), the wifi card gets off it's lazy butt and sees which SSIDs are being broadcast.  "Dartmouth Secure" pops up, I select it, connects fine.  End of story, right?

BUT...

Sometimes my wifi card is very slow to detect the local networks.  And sometimes I'm absurdly impatient.  Sometimes, I want to force NetworkManager to connect to "Dartmouth Secure" before the SSID is detected.  I do this all the time with open networks, and some WEP networks.  I left-click on NM, select "Connect to Hidden Wirless Network..." then select my network of choice.

But when I try this with my secure school network, the dialog box "Connect" button is grayed out.  Presumably because the "Password" box is empty.  But, the "Password" box is also grayed out, and I can't type in the password.  If this isn't very clear, please see the attached screenshot.

There's no other WPA networks I can test things out on.  But I can't see why NM is preventing me from changing any of the settings for THIS particular connection.  What I'd like to know, is how I can over-ride NM's retardedness and force it to connect.

It feels silly that I always have to wait for the SSID to be picked up by my wifi card, when I know good and well that I should be able to connect.  But the practicality of this solution is a distant second to my curiosity of what is going on in NetworkManager's little brain.

Thanks for any insight you may have!

---

### Post by i.r.id10t on 2009-09-14
Uhh... NM sucks.  My opinion, but it seems broken for me.  On the other hand, wicd works like a champ, unencrypted, WEP, WAP, it Just Works for me on my laptop (ancient thing with a first gen Cisco/Aironet card).

---

### Post by HunkirDowne on 2009-11-22
> **i.r.id10t said:**
> Uhh... NM sucks.  My opinion, but it seems broken for me.  On the other hand, wicd works like a champ, unencrypted, WEP, WAP, it Just Works for me on my laptop (ancient thing with a first gen Cisco/Aironet card).

Just about everything you said, I could reverse NM and Wicd.  Don't get me wrong, Wicd works great for my wired connection.  But I have yet to be successful at connecting to a hidden WEP.  Granted, I'm off in the weeds with my card (Linksys-N PCMCIA) but it works great in Ubuntu (NM) but not Kubuntu (KNM) or Xubuntu (Wicd).  In both (three, counting Mint xfce) cases using non-gnome, I've had to install the gnome solution to get it working.

I've perused the fora pretty good (Ubuntu, Mint, Debian, Wicd).  I've seen lots of ideas but so far I haven't found solutions (that are documented well enough to be useful).

No worries here -- I'm working.  One day I'd like to learn the command line solution and just write my own but I have a day job that doesn't involve Linux.

---

### Post by imac_89 on 2009-11-22
You have the same issue with the dialogue box as I do. And it is with hidden networks. I make my network visible and I am able to connect. But when it is hidden, I may as well be trying to break into my own network.

---

