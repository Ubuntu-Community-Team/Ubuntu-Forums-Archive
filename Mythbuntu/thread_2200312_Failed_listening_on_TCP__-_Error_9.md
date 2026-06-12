---
title: "Failed listening on TCP  - Error 9"
date: 2014-01-18
forum: Mythbuntu
---

### Post by Senkoboy on 2014-01-18
I have a new clean install of mythbuntu 12.04.3, .25 Myth.  I cannot get my backend to start, even with the command line from the terminal.   Here is a sample of what I get when I run mythbackend from the terminal.

> 2014-01-18 11:46:34.858114 N  MythBackend: Starting up as the master server.
2014-01-18 11:46:35.229572 I  Found 0 distinct programid authorities
2014-01-18 11:46:35.229765 I  New static DB connectionSchedCon
2014-01-18 11:46:35.233964 I  Listening on TCP 127.0.0.1:6544
2014-01-18 11:46:35.234045 I  Listening on TCP [::1]:6544
2014-01-18 11:46:35.234126 E  Failed listening on TCP [fe80::22cf:30ff:fea2:66b%wlan0]:6544 - Error 9: The address is not available
2014-01-18 11:46:35.234235 E  MediaServer::HttpServer Create Error
2014-01-18 11:46:35.235403 I  Listening on TCP 127.0.0.1:6543
2014-01-18 11:46:35.235474 I  Listening on TCP [::1]:6543
2014-01-18 11:46:35.235539 E  Failed listening on TCP [fe80::22cf:30ff:fea2:66b%wlan0]:6543 - Error 9: The address is not available
2014-01-18 11:46:35.235585 C  Backend exiting, MainServer initialization error.
 

Where do I start?  Disable disable IPV6?

---

### Post by sandyd on 2014-01-18
[http://code.mythtv.org/trac/ticket/11030](http://code.mythtv.org/trac/ticket/11030)

---

### Post by Senkoboy on 2014-01-18
I had to do this and reboot.  [http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html]("http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html") 

 >  Follow this to Disable IPv6, So we have to edit the sysctl.conf file.

To do this open Terminal (Press Ctrl+Alt+T) and copy the following commands in the Terminal:
Terminal Command:
sudo gedit /etc/sysctl.conf



Now add these lines at the end of file:

# IPv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Now Save sysctl.conf file and close.

I got it going, thanks

---

