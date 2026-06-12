---
title: "Bittorrent slow in both Ubuntu/XP"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by sirdeets on 2006-07-10
Could this be a problem with my ISP? I'm using Comcast, and get 6Mbps downstream. My torrent DL's never go above 30 kb/s, in Ubuntu or in XP. How can I speed this up? Does Comcast have a policy of capping BT dls? Thanks!

---

### Post by kris2pe on 2006-07-10
You said both right? Yup!!! Well lucky 4 u guys in america you switch ISPs! You can encrypt you download but won't worry really do much good!

---

### Post by mishimasan on 2007-05-14
I would recommend first checking your firewall settings.  And then in the port forwarding section of your router - to enable the ports that you want to use.  I am using ports 45001 - 45100.  This is easier than it sounds if you haven't done it before.  Just go to the router security tab, or look for anything to do with either services or port forwarding.  In this section, you will have the ability to add a service - using a start port and an end port.  Voila - once you have enabled a TCP service from a start to finish port (45001 - 45100) then you will be able to restart the router and see if it has made any difference.  It did for me.

The reason behind this is due to the fact that many trackers don't accept the default port allocation of bittorrent as it is known torrent traffic.  Many believe that they wish to dilute the torrent traffic over different ports making it harder to detect.  I have not read up on this and only join the speculation.  Feel free to correct me.

Next, if that doesn't work - go to [www.canyouseeme.org](www.canyouseeme.org) and type in anywhere between the start port and the end port to see if you are visible - i.e. opened.  If not, seek other advice.

---

