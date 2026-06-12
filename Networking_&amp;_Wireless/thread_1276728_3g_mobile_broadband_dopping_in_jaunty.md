---
title: "3g mobile broadband dopping in jaunty"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by dj-toonz on 2009-09-27
Hi all, for the past 4 weeks or so the mobile broadband connection keeps dropping every so often here's the log from the dbus log

Sep 27 18:09:51 Pc1 pppd[20216]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Sep 27 18:09:51 Pc1 pppd[20216]: pppd 2.4.5 started by root, uid 0
Sep 27 18:09:51 Pc1 pppd[20216]: Using interface ppp0
Sep 27 18:09:51 Pc1 pppd[20216]: Connect: ppp0 <--> /dev/ttyUSB0
Sep 27 18:09:54 Pc1 pppd[20216]: CHAP authentication succeeded
Sep 27 18:09:54 Pc1 pppd[20216]: CHAP authentication succeeded
Sep 27 18:09:58 Pc1 pppd[20216]: Could not determine remote IP address: defaulting to 10.64.64.64
Sep 27 18:09:58 Pc1 pppd[20216]: local  IP address 92.xx.xx.xx
Sep 27 18:09:58 Pc1 pppd[20216]: remote IP address 10.64.64.64
Sep 27 18:09:58 Pc1 pppd[20216]: primary   DNS address 217.171.135.1
Sep 27 18:09:58 Pc1 pppd[20216]: secondary DNS address 217.171.132.1
Sep 27 18:10:47 Pc1 pppd[20216]: Terminating on signal 15
Sep 27 18:10:47 Pc1 pppd[20216]: Connect time 0.8 minutes.
Sep 27 18:10:47 Pc1 pppd[20216]: Sent 1096 bytes, received 1194 bytes.
Sep 27 18:10:47 Pc1 pppd[20216]: Connection terminated.
Sep 27 18:10:48 Pc1 pppd[20216]: Exit. 

Sep 27 19:58:10 Pc1 pppd[9626]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Sep 27 19:58:10 Pc1 pppd[9626]: pppd 2.4.5 started by root, uid 0
Sep 27 19:58:10 Pc1 pppd[9626]: Using interface ppp0
Sep 27 19:58:10 Pc1 pppd[9626]: Connect: ppp0 <--> /dev/ttyUSB0
Sep 27 19:58:13 Pc1 pppd[9626]: CHAP authentication succeeded
Sep 27 19:58:13 Pc1 pppd[9626]: CHAP authentication succeeded
Sep 27 19:58:16 Pc1 pppd[9626]: Could not determine remote IP address: defaulting to 10.64.64.64
Sep 27 19:58:16 Pc1 pppd[9626]: local  IP address 94.xxx.xxx.xxx
Sep 27 19:58:16 Pc1 pppd[9626]: remote IP address 10.64.64.64
Sep 27 19:58:16 Pc1 pppd[9626]: primary   DNS address 217.171.135.1
Sep 27 19:58:16 Pc1 pppd[9626]: secondary DNS address 217.171.132.1

I've been getting loads of the Could not determine remote IP address: defaulting to 10.64.64.64 & primary   DNS address 217.171.132.1 (should be 217.171.135.1 ) & I have to shut down the connection & try again, this has been going on for 4 weeks now :( before then I could leave it up all day. My network provider is 3UK. How can I get it working proper in jaunty like it was a few weeks ago, If I'm in the middle of a conference call to the boss via either skype or msn (pidgin) the connection drops & then I get a text message from the office (having a go at me). It work's perfect in windows, I can have the connection open all day) but not under Ubuntu  Jaunty at the moment. I know I could install either windows XP professional or Vista Business on the Dell mini 10v for work (but as I haven't used windows for 4 years) just would to have the connection working like it used to be before something broke :( It work's if I have either a download going or I'm streaming a radio station or using the net heavy(as I tested it on my 12 gig, quad core 64 bit machine running Jaunty) and that did the same before I stuck a shoutcast stream on & had it running for more then 10 hours. So it looks like something dropping the connection when it's idol (just surfing or reading a web page) after about (it various in times when it drops), Has anybody got any ideas why network-manager 0.7.0.100 or even network-manager 0.7.99 (0.80) should be playing up (when it used to work a few weeks ago) I've gone on google & searched for hours & days but can't find anything & been on bugzilla for Ubuntu & network-manager & nar nar (if it is my isp what's the problem, is there anything I can do it Ubuntu to counter it?) i'm using opendns servers aswell but in the log above it doesn't show up that I am it shows that primary   DNS address 217.171.135.1 & secondary DNS address 217.171.132.1 but in network-manager when I right mouse & check on connection information it shows up everything bar default route is 10.64.64.64.64 & primary dns is 208.67.222.222 & secondary dns is 208.67.220.220  (so I don't know Log File Viewer is not showing up the new DNS address, some one please help before I get FIRED!!! as this is doing my nut in now HELP, should i post a bug to Ubuntu buzilla & network-manager or what ??? cheers

---

