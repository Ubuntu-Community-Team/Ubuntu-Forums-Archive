---
title: "Apache Behind Nat setup"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by SoftwareExplorer on 2009-01-20
Well I set up a Ubuntu machine at school to filter the web with Dansguardian which worked great. Then we had some XP computers with activation cracks start whining, so I got to setup two more Ubuntu computers. All my classmates have a blast with the desktop effects too. So I would say so far yaayy!! My teacher wanted to setup moodle which he uses as a student in college. So we got Apache, MySQL, and PHP working. However, apache only serves pages to inside the network that is attached to the internet via a Actiontec router using NAT. I tried setting the router to forward port 80, 8080, 8087 and Apache to use those ports. My problem is for the life of me I can't seem to get past that NAT to access it from the internet. We also have a Dynamically assigned web ip address, so it would be helpful if someone could tell me how to do the dynamic dns thing, though I can live with without it.

---

### Post by dmizer on 2009-01-20
Well, I'll start with your question on dynamic dns because it's easier. Most routers come with the ability to automatically update your dynamic domain when a new DHCP lease is discovered. Check that first. If not, then you should look into ddclient (in the Ubuntu repositories). ddclient references here:
[https://help.ubuntu.com/community/DynamicDNS#ddclient](https://help.ubuntu.com/community/DynamicDNS#ddclient)
(if you use dyndns) [http://www.dyndns.com/support/tools/clientconfig.html](http://www.dyndns.com/support/tools/clientconfig.html)


Regarding not being able to view the server externally, are you sure you cannot reach the server from outside the LAN? Many routers are not capable of looping. So if you try to browse to [http://mydomain.dynamichost.com](http://mydomain.dynamichost.com) from inside the LAN, you'll get a failure unless:
1) You have a local domain controller which redirects the request to the server
-or-
2) You have a correctly configured hosts file on the client.

More information on hosts here: [http://ubuntuforums.org/showthread.php?t=1010466](http://ubuntuforums.org/showthread.php?t=1010466)

---

### Post by SoftwareExplorer on 2009-01-21
Thanks dmizer for helping me :)  I got the Dynamic dns working and you were right about the router not being able to see itself correctly. I tried looking at the web address of my router through a proxy and it worked like a charm.

---

### Post by dmizer on 2009-01-21
> **SoftwareExplorer said:**
> I tried looking at the web address of my router through a proxy and it worked like a charm.
Ha! Looks like I need to add another item to my "you'll get a failure unless" list ;)

Glad we got you going!

Basically what happens here is that the router sees a request which appears to be coming from both external and internal. This causes the router to curl up in a ball and mumble to itself until your request times out. lol

---

