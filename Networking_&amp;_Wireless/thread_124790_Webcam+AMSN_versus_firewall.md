---
title: "Webcam+AMSN versus firewall"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by g2devi on 2006-02-02
Hi. I managed to get my webcam working yesterday using these instructions:
[http://homes.esat.kuleuven.be/~decockd/wiki/bin/view.cgi/Main/InstallingQuickCamMessengerTOC](http://homes.esat.kuleuven.be/~decockd/wiki/bin/view.cgi/Main/InstallingQuickCamMessengerTOC)

I also got the latest aMSN which has webcam support. It appears to work (I can see myself in the test module). My problem comes when I try use AMSN to share webcam sessions with anyone else -- I can't. When I try to confure the webcam, I get the following message: "You are firewalled or behind a router".
From the help, I see the following comments:
[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN#firewalled](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN#firewalled)

I'm not sure if the problem is Firestarter or my ADSL modem and I don't know the techniques to find out where it's being blocked or how to fix it.
I've tried pressing the "Stop Firewall" button on Firestarter before trying to connect the AMSN webcam, but it doesn't seem to help. However, I don't know if "Stop Firewall" opens up all ports on my system, so it is still possible that I need to configure firestarter. I've always kept my home system completely locked down, so while I understand what the instructions are trying to say, I don't know how to implement it.

Could anyone provide any pointers or hints on what I can do next? Any help would be much appreciated.

Thanks.

---

### Post by az on 2006-02-02
[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN#firewalled](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN#firewalled)

---

### Post by g2devi on 2006-02-02
Hi, I actually pointed out that link in my original post, but I wasn't sure where the change should be applied or how to determine the problem exists. If the problem exists in the Firestarter/Ubuntu firewall, then I'm not sure what I need to do with the information on the website.

If the problem exists in the ADSL modem, I'm pretty much on my own. The ADSL modem that came with my ISP (Sympatico), didn't come with an instruction manual that mentioned the webserver for the modem.  The modem used microsoft specific software to do the configuration. I remember finding a reference to the modem configuration URL on google several months ago, but it took a while to find. Unfortunately, I've misplaced this information so I'll have to dig it up again.

---

### Post by az on 2006-02-02
Sorry.  I didn't realise it was the same link.

If your modem has a firewall, you need to forward those ports to your box, as described.  Anything that is sent to your modem/router through those ports will get sent to that one box.

You need to open those ports (allow in) in firestarter on your box.

---

### Post by lf82 on 2006-02-08
> he ADSL modem that came with my ISP (Sympatico), didn't come with an instruction manual that mentioned the webserver for the modem.

Here are some other options:

1) Delete Firestarter. If it solves your problem, then you'll know your modem isnt the problem.

2)Call tech support. I think they're opened 24/7. It shouldn't be a problem to show how to manually open ports.

3)Do you dual-boot with windows?? If yes, then try you webcam under it. If it works, then your modem probably isnt the problem....

I'm with sympatico too. I have a "base" connection ("intermédiaire" in french). I did not use the install cd, and everything worked right out the box.

---

