---
title: "Major package loss with VPN pptp"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2009-02-04
I trying out VPN with pptp and it's working that to these forums :) but I got major package loss, the syslog is flooded with this message

```

20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444300 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444301 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444302 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444303 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444304 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444306 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444307 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444308 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444310 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444311 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444312 (expecting 444292, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444313 (expecting 444305, lost or reordered)
20:30:11  pptp[22491]: nm-pptp-service-22488 log[decaps_gre:pptp_gre.c:414]: buffering packet 444314 (expecting 444305, lost or reordered)

```
the syslog is on 50mb after using VPN in about 1h, I found this bug report [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/292799](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/292799) and tried the tip with changing the mtu but it didn't work. I tried a few different sizes 1500,1496, 1460. 1300, 1200 with no difference. Someone that understand what can cause this, it might even be that easy that I got the wrong settings (check attachment)

```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:*  P-t-P:*  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1200  Metric:1
          RX packets:396954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:*  TX bytes:*


```

Sorry about the text in the attachment is in swedish, I can try to get it in english if you need.

---

### Post by theNthDoctor on 2010-08-22
My research on this problem shows me it's definitely an upstream issue, so I hope you'll forgive me for posting about a Fedora bug in an Ubuntu forum.

Since the updates applied to my Fedora 12 x86_64 system on Sat, Aug 21, 2010, my VPN (with MPPE) connection has shown horrible performance.

Pastebin of yum history info for that update:

[http://pastebin.com/XQtWbk4H](http://pastebin.com/XQtWbk4H)

The problem:  my internet connection is great when not connected to a VPN, but when connected through the VPN (with MPPE), any large transfers cause the errors pasted below to spam my syslog.  (And the whole point of my VPN access is to do my job, which requires many large transfers each day.)  The end result: good VPN internet performance for a few seconds, then zero tx/rx for the rest of that transfer, and sluggish response when I attempt to restart the transfer.  Smaller web pages will occasionally be reliable, but large transfers exhibit the behavior described below, and result in the syslog spam shown at the bottom of this post.

Adjusting MTU on the interfaces eth0 and ppp0 have no effect at all.  I've tried specific recommended values like 1440, 1438, 1418

Running a continuous ping does not help.

I have seen many threads about this bug, and it's been claimed that NetworkManager 0.8 solves the problem, but for me, 0.8 was the first time this problem arose.

So I did this:

$ sudo yum downgrade NetworkManager NetworkManager-gnome NetworkManager-vpnc NetworkManager-pptp

The final output was this:

Removed:
  NetworkManager.x86_64 1:0.8.1-3.git20100813.fc12           NetworkManager-gnome.x86_64 1:0.8.1-3.git20100813.fc12     
  NetworkManager-pptp.x86_64 1:0.8.0-1.git20100411.fc12      NetworkManager-vpnc.x86_64 1:0.8.0-1.git20100411.fc12      

Installed:
  NetworkManager.x86_64 1:0.7.996-6.git20091021.fc12         NetworkManager-gnome.x86_64 1:0.7.996-6.git20091021.fc12   
  NetworkManager-pptp.x86_64 1:0.7.996-4.git20090921.fc12    NetworkManager-vpnc.x86_64 1:0.7.996-4.git20090921.fc12    

Dependency Installed:
  NetworkManager-glib.i686 1:0.7.996-6.git20091021.fc12

Sadly, this did NOT help.  Despite having great performance before Saturday, downgrading now results in the instant message, VPN connection failed due to invalid secrets.  Rebooting didn't help, nor did creating a new VPN entry from scratch with identical settings.  So, back to the new version...

$ sudo yum update

Output:

Updated:
  NetworkManager.x86_64 1:0.8.1-3.git20100813.fc12          NetworkManager-glib.i686 1:0.8.1-3.git20100813.fc12          
  NetworkManager-gnome.x86_64 1:0.8.1-3.git20100813.fc12    NetworkManager-pptp.x86_64 1:0.8.0-1.git20100411.fc12        
  NetworkManager-vpnc.x86_64 1:0.8.0-1.git20100411.fc12     bsnes.x86_64 0:0.067-1.fc12                                  
  kernel-debuginfo.x86_64 0:2.6.32.16-150.fc12              kernel-debuginfo-common-x86_64.x86_64 0:2.6.32.16-150.fc12   
  xulrunner-debuginfo.x86_64 0:1.9.1.11-2.fc12

The upshot: My VPN connection returned to its new, half-useable state, with hundreds of "lost or reordered" entries spamming syslog within the first minute of a big transfer.

It's worth noting that in the 2 days this has been a problem, there have been periods where the VPN was reliable.  However, my non-VPN internet speed is much better than my VPN internet speed; when I have these problems, then detach from the VPN and surf large files, it works great.

If you need additional information, please do us all a favor by giving me exact commands to type, as I'm pretty lame.  Also, and I only point this out because it seems weird to my uneducated eye... I do NOT have PPP Echo packets turned on, in nm-applet > VPN > Advanced, yet there are Echo Reply lines in my syslog.  

Aug 22 16:45:37 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 9142 (expecting 9141, lost or reordered)
Aug 22 16:45:45 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 9338 (expecting 9337, lost or reordered)
Aug 22 16:45:45 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 9363 (expecting 9362, lost or reordered)
Aug 22 16:45:57 bst pptp[20815]: nm-pptp-service-20805 log[logecho:pptp_ctrl.c:677]: Echo Reply received.
Aug 22 16:46:02 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10293 (expecting 10292, lost or reordered)
Aug 22 16:46:02 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10380 (expecting 10379, lost or reordered)
Aug 22 16:46:03 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10432 (expecting 10431, lost or reordered)
Aug 22 16:46:03 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10546 (expecting 10545, lost or reordered)
Aug 22 16:46:03 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10596 (expecting 10595, lost or reordered)
Aug 22 16:46:03 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10621 (expecting 10620, lost or reordered)
Aug 22 16:46:03 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10746 (expecting 10745, lost or reordered)
Aug 22 16:46:03 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10771 (expecting 10770, lost or reordered)
Aug 22 16:46:03 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10796 (expecting 10795, lost or reordered)
Aug 22 16:46:04 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10856 (expecting 10855, lost or reordered)
Aug 22 16:46:08 bst pptp[20809]: nm-pptp-service-20805 log[decaps_gre:pptp_gre.c:414]: buffering packet 10942 (expecting 10941, lost or reordered)

---

