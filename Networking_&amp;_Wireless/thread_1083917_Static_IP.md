---
title: "Static IP"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by ludicrous50 on 2009-03-01
I have a 54G handling DNCP requests. When I allow ubuntu server or desktop to be configured by the router I can ping from windows to ubuntu and back no problem therefore my port forwarding works just fine. I can configure my windows machines with static ips and ping back and forth between them with no issue however when I configure either the server of desktop (ubuntu) with a static ip my windows boxs can not ping to ubunto nos or os and port forwarding will not work because the router can not contact the clients. The static ips I an trying are not in the DHCP scope and I have a printer server on the network out of the scope I can ping therefore there has to be something blocking the ping request on the ubuntu platform. So far the nos is a default load.

I know I am configuring static in windows right because I can ping the win clients and I know I have configured static ips in ubunto correctly so there has to be something else I am missing within ubunto.

I read a thread regading disabling ipv6 but I am not sure I should do this at this time. 

If I can not find the answer I can always start and configure DHCP on the server and that should work however I would like for now to get statics to work.

Any help would be greatly appreciated.

---

### Post by issih on 2009-03-01
Don't really follow where you are on this?

Are all clients (win and ubuntu) connected to one router? if so then port forwarding is not an issue at all, thats to do with connecting to a specific local machine from outside the lan.

Assuming I am right in saying that all machines are connected to one router, then:

1) using dhcp everything works fine, all pcs (win and ubuntu) can access the internet and each other (e.g. ping via ip address).

2) using static ips the windows pcs can see each other but not the ubuntu one.

Is that correct?

Does the ubuntu machine have internet connectivity when set up with static IP?

Can the ubuntu machine ping the router?
Have you made sure that none of the static ips conflict (including your printer servers ip) and that the same subnet mask is used on all machines?

It sounds far more likely that it is a basic networking error than something specific to ubuntu.

Hope that helps

---

### Post by ludicrous50 on 2009-03-01
Thanks for writing.

Ubuntu os and nos can get out to the internet whether dhcp or static however ubuntu static ips can not be pinged from windows and if I can not ping them on the lan I can not access them remotely from the wan after setting up ip forwarding. If I allow windows machines and ubunto machines to be dhcp then everything is fine. The minute I assign a static ip using network config gui in ubunto I can not ping them from windows and I can not connect to them remote from the wan and yes ubuntu can ping the gate way whether dhcp or static. I have been working in the business as an admin for windows for 15 years and this has me stumpted. 

Not noing very much about ubuntu I was thinking that there was something blocking me from pinging the server when static ips are used. Don't know I am very lost.

Thanks:confused:

---

### Post by Iowan on 2009-03-01
Static address in a DHCP network can get tricky - name resolution seems to break (as you've discovered).  There may be options with WINS or Winbind.  One relatively painless option is to use static leases (DHCP server issues address based on MAC address).  Machines get the same address, DHCP gets to manage details, and *might* fix name resolution issue.

---

### Post by issih on 2009-03-02
That is a good point, are you talking about pinging hostnames or ip addresses?

if it is hostnames then it is as has been suggested probably just that windows host name resolution (netbios) is not built into ubuntu by standard. 

if it is ip address then something far more serious is wrong.

Assuming this is a hostname resolutin issue then try doing this:

[http://www.colingodsey.com/resolving-windows-host-names-netbios-samba-in-linux/](http://www.colingodsey.com/resolving-windows-host-names-netbios-samba-in-linux/)

Hope that helps.

---

### Post by ludicrous50 on 2009-03-02
Thank you but no it is not a host name issue but simply pinging static ip set in ubuntu.

---

### Post by ludicrous50 on 2009-03-02
I got it!!!

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/comment-page-2/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/comment-page-2/)

I finally have a static set and I am affraid to restart the server. LOL

Thanks to all for help.:P

---

