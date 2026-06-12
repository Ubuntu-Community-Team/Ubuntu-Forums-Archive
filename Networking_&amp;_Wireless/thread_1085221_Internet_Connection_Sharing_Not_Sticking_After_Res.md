---
title: "Internet Connection Sharing Not Sticking After Restart"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by naddix on 2009-03-02
I have managed to get Internet Connection Sharing running with this howto [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) but the problem is I cant get this to stick after reboot. What happens is my computer that is doing the sharing loses internet and so does the computers im sharing to. The only way That I could get internet back was to # apt-get remove iptables and than reinstall iptables. I Done this ICS many times and it works fine until I reboot. I have worked on this years ago than gave up and now im back thinking that a newer version of ubuntu would have helped but did not. Any help would be great. Thanks.

---

### Post by dmizer on 2009-03-02
You're looking at an ancient tutorial from Breezy. Try this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by naddix on 2009-03-05
yes I did end up going off of the link you provided and still had no sharing after a restart, but I did figure out how to make it work and someone should make a note about this. after I did the tutorial mentioned above I had to add  

sudo iptables -A POSTROUTING -t nat -j MASQUERADE

to /etc/rc.local

After I did that everything worked after restarts and shut downs.

Dmizer if you might know what causes this to happen after restart I would really like to know, I have gotten ICS working before and always had this restart issue and now im glad to say that I have it working, but I would still like to know the cause of the problem rather than just the lucky guess I took at it. I would guess something else is clearing something in iptables.

---

### Post by Xipher on 2009-03-06
netfilter rules (those put in place by iptables) aren't persistent, meaning that each reboot they must be reinstated. By adding that line to your rc.local you're just setting up the NAT table again so you can masquerade traffic as needed once the machine has booted up.

---

