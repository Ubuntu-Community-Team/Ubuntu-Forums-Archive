---
title: "Slow internet in 8.10"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by mrrix32 on 2008-12-18
Since upgrading to 8.10 when it came out, I have found my Internet Speed noticeably slower. I have not changed my hardware, and am Dual-Booting with Vista. I ran a speed test on both OS and have posted the results below. My PC has a wireless connection to a router.

**Ubuntu 8.10**
294 Download
44 Upload

**Vista**
3825 Download
372 Upload

Any ideas?

---

### Post by Ben Page on 2008-12-18
I am having simillar internet speed probs, too, but only when dnlding torrents, http is allright, same system ubuntu 8.10

---

### Post by _Smiler_ on 2008-12-18
I'm having ridiculous problems too - my connection is supposed to be 10mp/s, my router is capable of 270mp/s (Edimax 6504n). When I right-click network manager and click connection info, it tells me my connection is only 1mp/s! This is the same when I do iwconfig. Another problem I'm having is when I put sudo /etc/network/interfaces into terminal, it gives back "no such command". I've read that my interfaces file should include eth0, which it doesn't, just:

auto lo
iface lo inet loopback

If anyone finds any info on how to fix this...loads of people seem to have the same problem!!

---

### Post by jonobr on 2008-12-18
It would appear all three are different problems.
AS a result Im sure people answering this post would have to answer all 3 questions... 


Here's what I recommend

_Smiler_ open a thread for yourself if you haven't already,
and post the results of ifconfig and lshw into the thread,
explain your problem.....

Ben Page I saw your post elsewhere and it appears you are just having problems with torrents, this is different to this post.
This indicates an application issue as opposed to anything ubuntu related.
I would recommend bumping your post later (24hrs is usual) and during a busy period to get most attention.
I would recommend in your bump adding the config file for the application which shows the setup of your torrent client, as well as your connection type to your ISP, is it cable/dsl? does it operate differently at different times of the day, (again, please put it in your other post after the bump.)

 
mrrix32 - this is your post, so I would recommend you repost here and enter results of ifconfig, also any more information, i.e. is this only for certain downloads? certain sites?
What is downloading ftp vs http etc.... have you tried a torrent client etc?
Have you tried a wired connection and seen if that is better or the same as the wireless connection?

---

### Post by duanedesign on 2008-12-18
Here are some of the more common solutions.

turn off ipv6 in browser
[http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html](http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html)

turn off ipv6 in system
[http://www.youtube.com/watch?v=Sd8nHsUevAY](http://www.youtube.com/watch?v=Sd8nHsUevAY)

add DNS entries to system or router if your behind one (see post #3)
[http://ubuntuforums.org/showthread.php?t=536](http://ubuntuforums.org/showthread.php?t=536)

This bug has alot on the subject.
[https://bugs.launchpad.net/ubuntu/+bug/155393](https://bugs.launchpad.net/ubuntu/+bug/155393)



good luck

---

### Post by IQRules on 2008-12-19
auto lo
iface lo inet loopback

Try this,
# ifconfig eth1 up
# ifconfig eth1 down

---

### Post by mrrix32 on 2008-12-23
After trying the methods linked to and having no luck I decided just downgrade to 8.04, and now I am back to my normal speed.
Thanks anyway

---

### Post by jonobr on 2008-12-23
Hello

Recommend you marked this as solved-ish

---

