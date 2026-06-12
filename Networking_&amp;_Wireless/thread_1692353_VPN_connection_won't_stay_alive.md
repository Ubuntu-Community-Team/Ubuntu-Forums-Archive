---
title: "VPN connection won't stay alive"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by Gelupah on 2011-02-21
Hi all,

As part of my transition moving away from Windows altogether, I've been trying to get the VPN to work properly under Ubuntu 10.10 32bit, through the wifi connection. The provider is Ivacy, using PPTP, and the usual instructions (below) are followed:

[http://ivacy.com/en/doc/user/setup/linux]("http://ivacy.com/en/doc/user/setup/linux")

The VPN originally connects fine, browsing etc works all fine, for a limited period of time though. Within roughly 10min the connection stops working; I'm not yet sure whether the determining factor is time or bandwidth, but it remains short-lived... There is no indication of the VPN connection dropping, it seems to remain connected, but no packets are received. To get the internet working again I have to manually disconnect from the VPN; then I can browse without the VPN, or reconnect the VPN and it will work for another small lapse of time.

In addition, I'm not sure if this related, but after reconnecting a few times to the VPN as described above, eventually I get an error message, "failed to start the VPN service" (or words to that effect).

The VPN connection worked very reliably under Windows; I would love to get this working as well with Ubuntu. Any advice on how to fix this would be much appreciated!

Thank you in advance.

---

### Post by SeijiSensei on 2011-02-22
After you have connected, try this.  First, ascertain the IP address of the other end of your VPN connection.  Open a terminal and enter "ifconfig".  You should see an entry for the VPN that lists the IP of the other end.  Once you know that IP, enter this in a terminal:

```
ping -i 30 -c 999999999 ip.of.remote.vpn &
```

That will ping the IP address every thirty seconds.  (The ampersand puts the process into the background.)  It may just be that the connection times out when it's been idle for a while.

There may be some options in the Linux PPTP client that will help maintain the connection as well.

---

### Post by Gelupah on 2011-02-22
Thanks, I'll give that a go, although I fear it won't change much - I've already made sure the connection wasn't left to idle, with downloads running, IMs running; I assume that also would have done the trick?

I also tried ticking the "send PPP echo packets" option in the advanced settings, but to no avail, would that have done the same thing?

---

### Post by Gelupah on 2011-03-03
OK, so I tried this, without the ampersand to keep an eye on things. After a while my downloads all came to a halt, I could not longer browse any Internet page, but the VPN was allegedly still connected, and the ping kept returning normal values... I have to manually disconnect and reconnect each time this happens.

What could be the cause? Any ideas how to get around this?

Thanks!


> **SeijiSensei said:**
> After you have connected, try this.  First, ascertain the IP address of the other end of your VPN connection.  Open a terminal and enter "ifconfig".  You should see an entry for the VPN that lists the IP of the other end.  Once you know that IP, enter this in a terminal:

```
ping -i 30 -c 999999999 ip.of.remote.vpn &
```

That will ping the IP address every thirty seconds.  (The ampersand puts the process into the background.)  It may just be that the connection times out when it's been idle for a while.

There may be some options in the Linux PPTP client that will help maintain the connection as well.

---

### Post by Gelupah on 2011-03-05
Sadly my connection is getting worse and worse. I have to connect many times now, before the internet works, most times I connect I receive no packets; I have to manually disconnect and reconnect, hoping for the best...

Worse still, even without the VPN, the internet connection is getting slower and slower, it is becoming so poor I have had to reinstall windows as a dual boot (shame on me, I know). Sad to say the internet works impeccably under windows, using the same router and wifi card, whilst in Ubuntu I am really struggling to get something reliable...

The wifi card is a D-link with Realtek RTL8168C chipset.

Any help would be greatly appreciated...

---

### Post by frotzed on 2011-09-28
I'm sorry to necro this thread, but I'm experiencing the _exact_ same issue with Ubuntu 11.04.  I'd love to see some activity on this thread. I'm not on wireless and I have kept this vpn connection alive on the same machine for days on end with Windows7.

Why is it that the more I use Ubuntu the more I appreciate how Windows7 "just works"?  Why do I have to deal with stuff like this with an operating system that is supposed to be as strong or stronger than Windows in the Desktop PC market?  Sorry, I'm venting and ranting.  I really just want to know how to keep my VPN alive more than 10 minutes at a time.

Surely the OP and I can't be the only ones experiencing this issue.

---

### Post by frotzed on 2011-09-28
[s]As an update I've used the hack above to, after connecting to the VPN, run this code in a terminal window:

```
ping -i 30 -c 999999999 ip.of.remote.vpn &
```

It does seem to be keeping the VPN alive which makes me happy :)

However, I need a permanent solution to this issue.  Maybe create a script that will execute upon establishing the VPN.  Any ideas? [/s]

I spoke too soon. The connection still died even with an active ping.

---

### Post by frotzed on 2011-09-29
I should add that I'm using PPTP.  Does Ubuntu just not play nice with this?

---

### Post by Scott Deagan on 2011-10-10
I am experiencing the exact same problem using Ubuntu 11.04 (wired connection). I have setup a PPTP VPN connection via the network manager, following my VPN provider's instructions to the letter:

1. input the IP address of the target computer.
2. input your user name. Leave all else blank.
3. hit Advanced button.
4. check: MSCHAPv2
5. check: Use Point-to-point encryption (MPPE)
6. select: 128-bit
7. check: Allow stateful encryption
8. check: Allow PPP echo packets
9. Leave all else blank. Hit OK, OK to save and get out.

I am disconnected at seemingly random periods of time after connecting. Sometimes the connection might stay open for 2 hours, but most of the time I am disconnected within 5 minutes. Once disconnected, the network manager shows that I am still connected. I have to select VPN CONNECTIONS > DISCONNECT VPN, and then connect again.

I have written to the systems administrator who replied with:

**"According to our debug log the disconnections are caused by malformed  GRE packets. We have a lot of bad checksums on your connection."**

I can stay connected for indefinitely when using Mac OS (Lion) or Windows 7, so I very much doubt it's my hardware or my ISP.

I'm guessing that there aren't that many Ubuntu Desktop users out there who use a PPTP VPN connections, hence this problem is either not confirmed and very low on the priority list. Unfortunately for me, the problem is so annoying that I can't use Ubuntu (a reliable VPN connection is essential for me).

Update: this is what is reported in my /var/log/syslog after the disconnection occurs:

```
Oct 10 05:44:27 iMac-Ubuntu pptp[11871]: nm-pptp-service-11745 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Oct 10 05:44:27 iMac-Ubuntu pptp[11871]: nm-pptp-service-11745 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Oct 10 05:44:27 iMac-Ubuntu pptp[11871]: nm-pptp-service-11745 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Oct 10 05:44:27 iMac-Ubuntu pptp[11871]: nm-pptp-service-11745 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Oct 10 05:44:27 iMac-Ubuntu pptp[11871]: nm-pptp-service-11745 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Oct 10 05:44:27 iMac-Ubuntu pppd[11861]: Modem hangup
Oct 10 05:44:27 iMac-Ubuntu pppd[11861]: Connect time 22.6 minutes.
Oct 10 05:44:27 iMac-Ubuntu pppd[11861]: Sent 36219320 bytes, received 1371467319 bytes.
Oct 10 05:44:27 iMac-Ubuntu pppd[11861]: MPPE disabled
Oct 10 05:44:27 iMac-Ubuntu pppd[11861]: Connection terminated.
Oct 10 05:44:27 iMac-Ubuntu NetworkManager[806]: <info> VPN plugin state changed: 5
Oct 10 05:44:27 iMac-Ubuntu NetworkManager[806]: <info> VPN plugin state changed: 6
Oct 10 05:44:27 iMac-Ubuntu NetworkManager[806]: <info> VPN plugin state change reason: 0
Oct 10 05:44:27 iMac-Ubuntu NetworkManager[806]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Oct 10 05:44:27 iMac-Ubuntu pppd[11861]: Terminating on signal 15
Oct 10 05:44:27 iMac-Ubuntu pppd[11861]: Exit.
Oct 10 05:44:28 iMac-Ubuntu NetworkManager[806]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Oct 10 05:44:28 iMac-Ubuntu NetworkManager[806]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 10 05:44:33 iMac-Ubuntu NetworkManager[806]: <info> VPN service 'pptp' disappeared
```

---

### Post by frotzed on 2011-10-10
Mine is 11.04 wired connection as well.  I'm wondering if this is an issue with the driver for this NIC.  I have 11.04 installed on my laptop and connected it to the same VPN from the same network (albeit wireless) and it didn't have any issues at all... VPN stayed alive all night.

---

### Post by Scott Deagan on 2011-10-11
frotzed: I am reluctant to dismiss it as the NIC as I have 3 Ubuntu computers (1 x laptop, 2 x desktops) and it occurs on all 3, weather connected via wireless or wired. Also, everything works fine if I boot into Mac OSX or Windows 7. I will buy a new NIC later on today and see if that makes a difference on my desktop.

11.10 is due in the next couple of days, so I'll install 11.10 and see how that copes with VPN connections. At the moment, I simply cannot use 11.04 because of this issue.

I have checked the Ubuntu bug reports, and there are a number of people who have reported the same symptoms (dating back to 2008).

---

### Post by frotzed on 2011-10-17
Well, problem is solved.  I installed Linux Mint and the VPN works flawlessly.  Not sure what's _that_ different between Mint and a stock install of Ubuntu, but it must be significant.

---

### Post by jaqob on 2012-05-16
Waking an old thread, but having the same problem in 12.04.
Anyone solved it, without switching dist? 

My connection dives faster if I'm using torrents, but will fail anyways after a while. It is working flawlessly in Win7 on the same computer.

---

### Post by frotzed on 2012-05-16
> **jaqob said:**
> My connection dives faster if I'm using torrents, but will fail anyways after a while. It is working flawlessly in Win7 on the same computer.

This is my exact problem.  Still haven't found a solution to it.  It happens on my desktop as well as my laptop so I'm confident it's not a problem with the NIC or its drivers.  Windows machines stay connected to the same VPN for days without a hiccup; Ubuntu, Fedora, Mint, they all can't handle it.  Just evidence of an unpolished OS, in my opinion.  

I mean, it's PPTP for goodness sake.  It's been around for decades and no Linux distro I've tried can make it work.  It really may be operator error, but I've followed the tuts exactly and no one seems to want to address this issue.

---

### Post by powerofpi on 2012-12-20
This problem is still present for me in Ubuntu 12.04 and 12.10. My VPN connection works flawlessly for about 5-10 seconds, then all traffic seems to grind to a halt, then about 60 seconds later I get a "VPN Connection Failed" message. I also use PPTP, as others have mentioned.

---

