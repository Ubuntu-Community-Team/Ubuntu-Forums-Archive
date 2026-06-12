---
title: "Google Earth Can't Connect to Server(s)"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by jman82s on 2007-05-30
Heya folks,

I'm having trouble getting Google Earth to connect to Google's servers. Everytime I start Earth, I get an "error code: 29; can't connect to server". I am relatively new to Ubuntu, but not new to Linux. I was previously a SuSE user, and had no problems before. 

I'm not using a firewall or proxy, and can connect to google.com without a hitch. The only thing that comes to mind is the newer kernel:

openSuSE 10.2 = 2.6.18
Ubuntu 7.04      = 2.6.20

I've searched far and wide, and beyond various oppressive governments blocking access to Earth, I can't seem to find anyone with similar issues.

Any thoughts/suggestions?

-Thanks! 

Gateway m360
Intel Celeron M (1.4 GHz)
768 MB Ram
Intel 82852 integrated graphics

---

### Post by gwm on 2007-06-10
I've just searched the forums for **google earth proxy server** and found some answers.

This one was the clearest:

[http://ubuntuforums.org/showthread.php?t=195651&highlight=google+earth+proxy+server](http://ubuntuforums.org/showthread.php?t=195651&highlight=google+earth+proxy+server)
:popcorn:

---

### Post by gwm on 2007-06-10
I've jus been and tried this solution:

> sudo gedit ~/.bashrc

then I went to the end of the file and added

> export http_proxy=192.3.4.5:8081

It didn't work, so I added http:// in front of the address

Still no change to google earth. Rebooting (to restart whatever) didn't make any difference either.

:popcorn:

---

