---
title: "set up injection on iwlgan"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by philipballew on 2011-01-01
i need to make my wireless driver (iwlagn on ubuntu 10.10 64bit) able to inject packets and i belive this is the what i am supposed to do [http://www.aircrack-ng.org/doku.php?id=iwlagn](http://www.aircrack-ng.org/doku.php?id=iwlagn) can anyone tell me if this looks good and what out of here i need to do.or if there is a better way? thanks

---

### Post by PatchesTheCaveman on 2011-01-01
That is the official website of the aircrack-ng developers.  I don't think anyone would lnow better than them.  :-)

If you have further questions regarding aircrack-ng, consider asking on their forum:  [http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)

As its solely dedicated to their software, members there will probably have considerably more experience, though there are many aircrack-ng users here as well.

---

### Post by philipballew on 2011-01-01
what on this guide will i not be required to do because i run Ubuntu? and how does patching drivers affect my system when i update things?

---

### Post by philipballew on 2011-01-03
hello?

---

### Post by bhadotia on 2011-01-03
> **philipballew said:**
> i need to make my wireless driver (iwlagn on ubuntu 10.10 64bit) able to inject packets and i belive this is the what i am supposed to do [http://www.aircrack-ng.org/doku.php?id=iwlagn](http://www.aircrack-ng.org/doku.php?id=iwlagn) can anyone tell me if this looks good and what out of here i need to do.or if there is a better way? thanks

I iwlagn on ubuntu has injection enabled by default. Last year when I tried aircrack for a college project my I was using iwl3935 and on another laptop and worked out of box without the need for patching. And I think iwlagn also should work as well. Their are some posts on this for explaining aircrack usage try searching them out and I think you will be fine on your own..

---

### Post by philipballew on 2011-01-03
thats wgat u fugures to, however when i test injection by tpying

 aireplay-ng -9 wlan0
it says i should get this:
16:29:41  wlan0 channel: 9
 16:29:41  Trying broadcast probe requests...
 16:29:41  Injection is working!
 16:29:42  Found 5 APs
 
 16:29:42  Trying directed probe requests...
 16:29:42  00:09:5B:5C:CD:2A - channel: 11 - 'NETGEAR'
 16:29:48  0/30: 0%
 16:29:48  00:14:BF:A8:65:AC - channel: 9 - 'title'
 16:29:54  0/30: 0%
 16:29:54  00:14:6C:7E:40:80 - channel: 9 - 'teddy'
 16:29:55  Ping (min/avg/max): 2.763ms/4.190ms/8.159ms
 16:29:55  27/30: 90%
 16:29:55  00:C0:49:E2:C4:39 - channel: 11 - 'mossy'
 16:30:01  0/30: 0%
 16:30:01  00:0F:66:C3:14:4E - channel: 9 - 'tupper'
 16:30:07  0/30: 0%
however i get this:philip@philip-laptop:~$ sudo  aireplay-ng -9 wlan0
13:57:24  Trying broadcast probe requests...
13:57:26  No Answer...
13:57:26  Found 2 APs

13:57:26  Trying directed probe requests...
13:57:26  00:23:51:D4:C6:B1 - channel: 10 - 'BALLEW'
13:57:32   0/30:   0%

13:57:32  00:1B:2F:F6:01:B4 - channel: 11 - 'dan'
13:57:38   0/30:   0%
aby help would be hot?

---

### Post by bhadotia on 2011-01-03
> **philipballew said:**
> 
aby help would be hot?

Actually I also never got exactly the same output as was indicated on the tutorials I read at that time. But in the end it all just worked out. Try googling and reading a variety of tutorials especially ones directed to ubuntu and you might just succeed.

---

