---
title: "remote control without ip/port access"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by P3t3r on 2012-04-28
I want to access an ubuntu machine behind a rooter which doesn't forward any ports, how should I do this? Ssh and vnc are not possible because of this.

Is there a simple web service which would allow to e.g. reboot this machine (i.e. the machine polls a website every X seconds to see if I sent it a command or reboot signal)? 

I'm currently using TeamViewer, which is a complete remote control package using this method, but it's a windows program via wine and it's not really stable (I often lose keyboard and mouse -- and then I can't reboot anymore).

---

### Post by SeijiSensei on 2012-04-28
You can set up OpenVPN as a client on the machine behind the router and have it connect to a machine you can control.  The easiest method is to use a [static-key configuration]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  Have the machine behind the firewall use the "remote" directive to start the tunnel with the host you control.

---

### Post by P3t3r on 2012-04-29
> **SeijiSensei said:**
> and have it connect to a machine you can control.And what if I don't have a machine that I control 24/7? The machine I'm trying to connect to is doing stuff for which it needs to be connected to the internet 24/7.

I had already thought of making a webpage that displays a number like "201204291112" and then letting the machine wget the page every minute and reboot if and only if the date/time is "2012-04-29 11:22AM". But that seems rather complicated for just sending a reboot signal every now and then. 
(And even then I'm not aware how to write such scripts properly.)

---

### Post by SeijiSensei on 2012-04-29
The machine on your end need not be up all the time.  As long as the remote client can see your machine it will connect whenever that machine is available.

It's difficult to do what you want with a web server because the server software would need to run with root privileges in order to execute a reboot.  Most servers like Apache run as an unprivileged user so that a compromise of the server won't give the attacker root.

I've gotten around this problem by using a "semaphore" method where you connect to the webserver and hit a button to schedule a root-only process.  The web application writes a file somewhere when the reboot is requested.  A separate script running from cron with root privileges then checks for the presence of the file once each minute and reboots if it discovers the file.

---

### Post by P3t3r on 2012-04-29
> **SeijiSensei said:**
> The machine on your end need not be up all the time.  As long as the remote client can see your machine it will connect whenever that machine is available.Oh? That's interesting. And what if there is already some OpenVPN running? As my remote machine needs VPN to be connected to the internet anyways.

> **SeijiSensei said:**
> It's difficult to do what you want with a web server because the server software would need to run with root privileges in order to execute a reboot.  Most servers like Apache run as an unprivileged user so that a compromise of the server won't give the attacker root.I don't care about security, actually, it's not a web server. I already modified sudo to run without asking the password, so apache can just run "sudo reboot" without problem. But I have no idea how to make apache execute something when I can't directly access the machine in the first place?

> **SeijiSensei said:**
> I've gotten around this problem by using a "semaphore" method where you connect to the webserver and hit a button to schedule a root-only process.  The web application writes a file somewhere when the reboot is requested.  A separate script running from cron with root privileges then checks for the presence of the file once each minute and reboots if it discovers the file.As mentioned, the root isn't a problem. The problem is that the machine is behind a router (of a public OpenVPN service if that matters) and hence cannot host the actual webpage. So I assume it'd have to poll actively somehow.

---

### Post by SeijiSensei on 2012-04-29
> **P3t3r said:**
> Oh? That's interesting. And what if there is already some OpenVPN running? As my remote machine needs VPN to be connected to the internet anyways.

Configue it to use a different UDP port than the one you use now.

---

