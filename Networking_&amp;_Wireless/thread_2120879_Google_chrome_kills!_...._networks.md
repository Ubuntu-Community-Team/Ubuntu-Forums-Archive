---
title: "Google chrome kills! .... networks"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by wgw on 2013-02-27
After some kind of update, my Google Chrome got all rascally and now all it does is kill my network connection. That means that even when I have both Firefox and Chrome running, Chrome can somehow screw up the connection so that Firefox doesn't work. So I'm back to Firefox only for the moment. I really want both. 

After much Googling (long discussion here: [http://productforums.google.com/forum/#!topic/chrome/B4k68v6IHxs](http://productforums.google.com/forum/#!topic/chrome/B4k68v6IHxs)), it looks like it is a DNS lookup problem that lies somewhere between my provider, Ubuntu and Chrome. Not sure who is to blame, but I need some advice.  

1) Can I debug the problem using WireShark? And how?
2) I hesitate to ask, since I have tried an array of solutions, but has anyone a fix for Ubuntu? Changing the DNS server seems like the obvious solution, but while I can set that on my computer,  I don't see how to set that on my router and I have the impression that the router is overriding anything I might do on my Ubuntu. 

Thanks!

---

### Post by wgw on 2013-03-10
I'm zeroing in on possible solutions. The first thing is it isn't purely a chrome problem. Firefox is doing the same thing, but it seems less systematic in Firefox. (Will give Opera a try.)

It is most likely this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984552), but my syslog does not have the same messages as most other people. 

In the syslog, I do note some curious entries. The first is postfix mail: 

```
Mar  9 16:09:01 bill-laptop postfix/pickup[5127]: E168C16010C: uid=0 from=<root>
Mar  9 16:09:01 bill-laptop postfix/cleanup[5412]: E168C16010C: message-id=<20130310000901.E168C16010C@bill-laptop>
Mar  9 16:09:01 bill-laptop postfix/qmgr[4036]: E168C16010C: from=<root@bill-laptop>, size=2513, nrcpt=1 (queue active)
Mar  9 16:09:02 bill-laptop postfix/local[5414]: E168C16010C: to=<bill@bill-laptop>, orig_to=<root>, relay=local, delay=0.21, delays=0.13/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar  9 16:09:02 bill-laptop postfix/qmgr[4036]: E168C16010C: removed
```

I have no idea what is going on there, but mail seems to be going somewhere. 

The second is a pair of cron jobs: 
```
Mar  9 15:17:01 bill-laptop CRON[5102]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  9 15:39:01 bill-laptop CRON[5222]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
```

What are those for? 

And the last is 
```

Mar  9 16:50:59 bill-laptop wpa_supplicant[1437]: WPA: Group rekeying completed with 00:26:b8:eb:9a:bc [GTK=CCMP]
```

I do think I should kill those cron jobs if I don't know what they are doing. I'm assuming the WPA supplicant entry is normal, but maybe that is the problem. 

More sleuthing needed!  


A more complete listing here: 

```
Mar  9 15:17:01 bill-laptop CRON[5102]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  9 15:39:01 bill-laptop CRON[5222]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar  9 15:39:01 bill-laptop postfix/pickup[5127]: AFB1316010C: uid=0 from=<root>
Mar  9 15:39:01 bill-laptop postfix/cleanup[5232]: AFB1316010C: message-id=<20130309233901.AFB1316010C@bill-laptop>
Mar  9 15:39:01 bill-laptop postfix/qmgr[4036]: AFB1316010C: from=<root@bill-laptop>, size=2513, nrcpt=1 (queue active)
Mar  9 15:39:01 bill-laptop postfix/local[5234]: AFB1316010C: to=<bill@bill-laptop>, orig_to=<root>, relay=local, delay=0.24, delays=0.13/0/0/0.11, dsn=2.0.0, status=sent (delivered to mailbox)
Mar  9 15:39:01 bill-laptop postfix/qmgr[4036]: AFB1316010C: removed
Mar  9 15:51:02 bill-laptop wpa_supplicant[1437]: WPA: Group rekeying completed with 00:26:b8:eb:9a:bc [GTK=CCMP]
Mar  9 16:09:01 bill-laptop CRON[5402]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar  9 16:09:01 bill-laptop postfix/pickup[5127]: E168C16010C: uid=0 from=<root>
Mar  9 16:09:01 bill-laptop postfix/cleanup[5412]: E168C16010C: message-id=<20130310000901.E168C16010C@bill-laptop>
Mar  9 16:09:01 bill-laptop postfix/qmgr[4036]: E168C16010C: from=<root@bill-laptop>, size=2513, nrcpt=1 (queue active)
Mar  9 16:09:02 bill-laptop postfix/local[5414]: E168C16010C: to=<bill@bill-laptop>, orig_to=<root>, relay=local, delay=0.21, delays=0.13/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar  9 16:09:02 bill-laptop postfix/qmgr[4036]: E168C16010C: removed
Mar  9 16:17:01 bill-laptop CRON[5446]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  9 16:39:01 bill-laptop CRON[5569]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar  9 16:39:02 bill-laptop postfix/pickup[5127]: 25D1A16010C: uid=0 from=<root>
Mar  9 16:39:02 bill-laptop postfix/cleanup[5579]: 25D1A16010C: message-id=<20130310003902.25D1A16010C@bill-laptop>
Mar  9 16:39:02 bill-laptop postfix/qmgr[4036]: 25D1A16010C: from=<root@bill-laptop>, size=2513, nrcpt=1 (queue active)
Mar  9 16:39:02 bill-laptop postfix/local[5581]: 25D1A16010C: to=<bill@bill-laptop>, orig_to=<root>, relay=local, delay=0.21, delays=0.14/0.01/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar  9 16:39:02 bill-laptop postfix/qmgr[4036]: 25D1A16010C: removed
Mar  9 16:50:59 bill-laptop wpa_supplicant[1437]: WPA: Group rekeying completed with 00:26:b8:eb:9a:bc [GTK=CCMP]
Mar  9 17:09:01 bill-laptop CRON[5746]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar  9 17:09:01 bill-laptop postfix/pickup[5687]: 58AC516010C: uid=0 from=<root>
Mar  9 17:09:01 bill-laptop postfix/cleanup[5756]: 58AC516010C: message-id=<20130310010901.58AC516010C@bill-laptop>
Mar  9 17:09:01 bill-laptop postfix/qmgr[4036]: 58AC516010C: from=<root@bill-laptop>, size=2513, nrcpt=1 (queue active)
Mar  9 17:09:01 bill-laptop postfix/local[5758]: 58AC516010C: to=<bill@bill-laptop>, orig_to=<root>, relay=local, delay=0.21, delays=0.14/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar  9 17:09:01 bill-laptop postfix/qmgr[4036]: 58AC516010C: removed
```

---

### Post by OSIsOpenSource on 2013-03-10
Have you tried Re-installing Chrome? Or if you want to change your Router settings, here are the URL's.

[Http://192.168.1.254](Http://192.168.1.254) (Most Common)
[Http://10.0.0.1](Http://10.0.0.1) (Comcast)

---

### Post by wgw on 2013-03-10
Thanks for the suggestion -- since I finally see that this affects Firefox, I decided a Chrome reinstall wouldn't help. 

My newest fix is to give a: 

```
sudo modprobe iwlwifi  11n_disable=1
```

I did this about an hour ago, and so far no disconnect. :P 

I will give it a day of working correctly before claiming victory over this bug, but I am optimistic. 

(The real glitch in all this is really me: that fix was given in the bug report and I did not try it, mainly because in the bug report they said the bug was fixed. But it isn't. Warning: old bugs linger, for some reason.)

So, I am itching to put solved on this thread -- time will tell... :-k

And I will make a conf file to make it permanent (as per [http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards](http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards)) :

```
gksudo gedit /etc/modprobe.d/iwlwifi-disable11n.conf
and add:
options iwlwifi 11n_disable=1
```

Thanks for your suggestion -- in general, a quick reinstall is often the best place to start for this kind of thing.

---

