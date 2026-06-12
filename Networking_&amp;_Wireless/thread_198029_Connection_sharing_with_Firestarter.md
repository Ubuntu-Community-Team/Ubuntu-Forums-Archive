---
title: "Connection sharing with Firestarter"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by pfadfinder on 2006-06-16
Good evening,
I am cracking up configuring connection sharing with Dapper Drake. I am using two Dapper-Drake machines connected by a LAN. My LAN-Device is eth0, my Internet-Device (ISDN with Fritz!Card if that matters) is ppp0 (or it is not- see some lines down). I used the manual found on [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php) and configured all settings as suggested. 

>    
 * The firewall machine should be able to reach the Internet
 * The clients and firewall should be able to ping each other
 * The clients should be able to reach the Internet if the Internet connection sharing option is enabled in Firestarter.


First: OK, 2nd: OK.
3rd point: I enabled connection sharing in firestarter (under eth0), but the client does not seem to get any connection.

Did i do anything wrong? Something appears strange to me: I am (in firestarter settings) just able to chose 3 connections: eth0, ppp0, sit1. I assumed ppp0 was the internet connection, but when I look at the "Networking" - GUI, ppp0 is disabled. For setting up my connection with ISDN, I had to configure some things manually- maybe that does the trick?

---

