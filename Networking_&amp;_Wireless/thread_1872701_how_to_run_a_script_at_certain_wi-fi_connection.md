---
title: "how to run a script at certain wi-fi connection"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by nicola76b on 2011-10-31
Hi all,
I've installed ubuntu 11.10 64bit on 2 machines (1 used as server, the other as client) for mythtv solution.
I've configured ntfs and I write a simple script to share some resource of the server in the client.
In the client I use many network connection, but when I load WIFI "pippo" connection I need to run this script automatically.
How can I do?
I use network manager and, if I do it by hand (first connect to "pippo" than start the script as a root) all works..
 
Thank you very much,
   
   Nicola

---

### Post by nicola76b on 2011-10-31
I found something here:
[http://www.techytalk.info/start-script-on-network-manager-successfull-connection/comment-page-1/#comment-3498](http://www.techytalk.info/start-script-on-network-manager-successfull-connection/comment-page-1/#comment-3498)

(thank-you Marko)

So now I'm able to run a command when an interface change status.
Does anybody know how to exec a command, not when interface is up, but when certain connection of an interface is up? 
(e.g. not when wlan0 is up, but when wireless connection “pippoWifi” - that it is one of many connection that use wlan0 - is up?

Thank you
   Nicola

---

