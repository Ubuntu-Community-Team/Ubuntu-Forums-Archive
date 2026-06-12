---
title: "No internet over wired connection"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by markling on 2013-04-30
Problem: No internet connection over ethernet

Internet provider: Post Office
Operating system: Xubuntu 12.04

The connection works fine over wireless.

The wired connection works when I run it to a Windows 7 computer.

It's just not working when I try and connect the same line (same ethernet cable, even), to Xubuntu.

This problem is verified on two separate Xubuntu machines: A) Xubuntu Laptop and B) Xubuntu Desktop. A third machine worked fine using the same equipment / cable / connection: C) Windows 7 Desktop.

The problem is also verified using two routers:
1. ZyXEL router : AMG1202-T10A, supplied by the ISP
2. BT Home Hub 3 : my old router that worked fine before.

The Post Office cannot help because it does not support Linux.*

Both computers, A & B, worked fine over wireless and wired ethernet connection to the BT Home Hub, using a BT ADSL line. They worked on this basis without problem for the last year. Prior to that they worked over a Virgin connection without problem.

What's changed: new house, new ISP.

Same computers. Same cables. Same operating systems. The Post Office got my broadband connected this morning. They resell a BT ADSL line. So it's effectively what I had before.

The Xubuntu Laptop has been connected during the last three weeks to a friendly neighbour's wireless BT ADSL router.

I connected the ZyXEL router to the Post Office ADSL line this morning. Everything online: looking good. All green lights. But wired connection was not possible to either Xubuntu Laptop or Xubuntu desktop.

Using the same cable, a Windows 7 machine got a Post Office internet connection via the same ZyXEL router without a problem.

Using wireless, the Xubuntu laptop was able to get a Post Office internet connection via the ZyXEL router. It just can't get a wired connection.

Connected the the Linux Desktop and the Windows 7 Desktop to the old router: the BT Home Hub 3. The Xubuntu Desktop was not able to access the router settings page (192.168.1.254). The Windows 7 Desktop was able to access the Hub settings.

Both Xubuntu computers go through the motions of making the wired connection to both routers. Each displays a connected status in the network indicator, indicating that the computer is connected over ethernet to the router. But neither machine can connect to an internet server when attempt made through web browser.

All of the connections here were tested by opening Firefox. All installations have worked fine on other connections. I tried Chrome on the Xubuntu desktop as well. That also failed to get a connection.

When attempting a connection through the ZyXEL roueter, Firefox said: "Server not found. Firefox can't find the server at ..."

When attemting a connection to the BT Home Hub settings, Firefox said: "Unable to connect. Firefox can't establish a connection to the server..."

Both these computers worked fine at the last address and with the last ISP, which was BT. But they also both connected to BT via the BT Home Hub. Now they can't even access the BT Home Hub settings.

*  (Bad choice of ISP, you might say - they do seem good in many other ways though. And their tech support guys do all they can to help, even if they don't have a single resident Linux expert. And they were more helpful than BT used to be. BT doesn't support Linux either. This doesn't look like an ISP problem anyway. But still, you'd think if you were forking out £30-a-month for an internet connection the least they could do is make sure that in their entire 24-7 support department there might just be one linux expert, no?)

---

### Post by Iowan on 2013-04-30
Do(es) the Xubuntu machine(s) get an IP address? Can you ping the router settings page, or another machine on the network?  I presume you were using the IP Address (192.168.1.254) when attempting access.

---

### Post by markling on 2013-05-07
Thank you, Iowan. I was using 192.168.1.254 when attempting access. Would you please give me specific instructions if you want me to test anything on the command line.

Some new developments. Bought a wireless card for the desktop (Xubuntu 12.10 i686). That connected to the ZyXEL router immediately. The same machine will still not get a connection if I try it over the wire. Wired connection is preferable. Interestingly: disconnected wireless, failed attempt at wired connection, then failed to reconnect wireless; had to restart machine to get wireless connection up again.

Reinstalled Xubuntu 12.04 i386 on the laptop. Now that gets a wired connection to the router just fine. + wireless connection. Both seem fine.

The windows machine is still connecting over the wire as it was before.

---

### Post by anspectrum on 2013-05-07
Haven't used Xubuntu, but networking rules remain the same. 

Try to give a static IP to the internet settings (Network Manager or if there is any alternate in Xubuntu), alongwith subnetmask. Then using ping command, see if you can ping the gateway (your broadband router / modem). If you can then check your Connection settings again and see if manual DNS entries help.

Alternatively you can have a list of IP Address, Subnetmask, Gateway and DNS once your wireless is connected. You can give the same settings on your Ethernet connection (but disconnect wireless first) and hopefully you will be all set.

Cheers.

---

### Post by markling on 2013-05-07
Thanks, anspectrum. All very helpful suggestions, I am sure. I'm afraid you would 1. need 2. to 3. spell 4. it 5. out 6. if I was to follow them.

---

### Post by anspectrum on 2013-05-07
Please go through [URL="http://askubuntu.com/questions/187306/applying-configuration-from-networkmanager"]http://askubuntu.com/questions/187306/applying-configuration-from-networkmanager

[FONT=arial]and[/FONT]

[http://ubuntuforums.org/showthread.php?t=2029931](http://ubuntuforums.org/showthread.php?t=2029931)
[/URL]

---

### Post by markling on 2013-07-20
Dear anspectrum

Thanks for your help with this. Sorry to have neglected your kind reply - I have been waiting for enough free time to jump into this jungle and start hacking. Alas, free time is lacking.

I've been surviving with the wireless connection in the meantime. This is not ideal. But it works. I shall let you know what happens when I do get back to this.

---

### Post by edwingeorge44 on 2013-07-20
Hey no idea about this.

---

### Post by praseodym on 2013-07-20
Please check the outputs of
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
```

---

