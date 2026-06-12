---
title: "Calling all Printer Sharing Experts"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by lakelovers on 2006-03-10
Does anybody have a solution for my print sharing dilema. If this is the wrong sub-forum, I apologize. And I confess that I have posted my problem more than once which I understand is frowned upon. I apologize for that too, but I am at my wits end. Nothing has worked so far.

My question this time is do Samba and Cups configurations conflict. I've tried configuring Samba (no good) and I have configured Cups (no good), but does one interfer with the other?

My setup: Ubuntu 5.10 on Desktop, Canoni560 with TurboPrint driver. I want to share that printer with a WinXP, laptop, on a wireless home network (Linksys router).

I have perused as many print sharing posts that I can find, and I have followed the cups config instructions on OCCY's blog.

I have posted my cups conf file before but nobody responded. So here it is again:

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.2.*
</Location>

<Location /jobs>
uthType BasicAuthClass User
/Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

The IP for the laptop is 192.168.2.101, the default gateway is 192.168.2.1. I've used both; neither have worked.

When I print from the laptop, it sees the printer and it says it's printing, but the job does not show on cups and, of course, nothing prints.

By the way, the laptop is my wife's. If I don't find a solution soon, she's going to either throw the laptop out. . . or me.:???:

---

### Post by lakelovers on 2006-03-10
I looked at "http://127.0.0.1:631" on the XP laptop and it brought up the cups page and I was able to do a test print from that source on the laptop. I don't know what that means other than, perhaps it shows that the laptop and sees the printer though I guess that address is an internet address. When a do the same with the laptop ID "http://192.168.1.101:631" I get "permission or access denied." I went to WinXP firewall and made an exception for port 631, but it didn't help.

Any ideas? I can sure use some help.

---

### Post by lakelovers on 2006-03-10
Sorry about this double post. How do I delete a message posted by error?

---

### Post by bobpaul on 2006-03-20
First off, I've never had experience with this route. I've always done the other way (print from linux to a machine running windows) but let me see if I can't help a little bit, though. 

AFAIK cups and samba should *not be able* to conflict in any way. Samba allows for communication with the Windows File and Printer sharing protocol on windows machines and other *nix machines with Samba, that's it. In /etc/samba.conf you can setup file and printer shares. These are files hosted on that linux machine you want to give other people access to. You can also list printers attached to that local machine that you want others computers to be able to print to. Since you want the WinXP machine to print to a printer on your Ubuntu desktop, this would be configured in there. If the printer is properly configured on Ubuntu, then you should be able to share it with samba.

Secondly, 127.0.0.1 is a special ip address. In fact, any IP that starts with 127. is special. These addresses (127.0.0.1 through 127.255.255.255) all refer back to your computer. They're called loopback addresses. Regardless of the machine you're on, if you type 127.0.0.1 you'll end up trying to connect to yourself. Therefore this:
> I looked at "http://127.0.0.1:631" on the XP laptop and it brought up the cups page is just impossible, unless you're running Cups on your laptop via cygwin or something, so I'm sure you just mispoke.

You want to print from your laptop, not control the cups web interface via your laptop.

[LIST]
[*]From Ubuntu, can you print from Firefox, etc?
[*]Please post your /etc/cups/printers.conf
[*]Please post your /etc/samba/smb.conf
[*]Please post the result of *sudo ifconfig*
[/LIST]

**EDIT:** 
It seems I'm partially wrong about the needing to use samba.
The Ubuntu wiki explains how to do what you want:
[https://wiki.ubuntu.com/NetworkPrintingFromWinXP](https://wiki.ubuntu.com/NetworkPrintingFromWinXP)
I also have access to a Gentoo print server at work that shares to Windows using cups/samba that I can look at as an example to try to help.

---

