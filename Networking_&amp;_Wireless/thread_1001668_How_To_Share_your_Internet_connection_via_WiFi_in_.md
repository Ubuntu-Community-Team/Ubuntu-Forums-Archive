---
title: "How To: Share your Internet connection via WiFi in Intrepid"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by elyase on 2008-12-04
I never got working methods based on Firestarter or iptables, dont know why, but I think this is the easiest and probably the Gnome´s intended way of getting the job done. As you probably know Fedora 10 brings the new [[COLOR="Navy"]ConnectionSharing[/COLOR]]("https://fedoraproject.org/wiki/Features/ConnectionSharing") feature. I was wondering why this doesn't work in Ubuntu Intrepid, even when nm-applet has a similar "Shared Connection" option. So here is the answer:
First and most important thing:
```
sudo apt-get install dnsmasq-base
```
(you dont have to do this in Fedora, lets hope in the next Ubuntu Jaunty we wont have to either).

Then left-click on the Network Manager Applet-> Create new wireless connection, put a name "xxxx", click on "Create" button, wait some seconds and if everything goes well, it will display a message like "Now you are connected to xxxx wireless Network". Thats all!! Now your wireless devices (friends/second laptop, Iphone, Ipod Touch,...) will be able to see and connect to your Internet connection.

There are also video instructions of the second part [[COLOR="Navy"]here[/COLOR]]("http://www.redhatmagazine.com/2008/10/16/video-fedora-10-connection-sharing/").
Bye

---

