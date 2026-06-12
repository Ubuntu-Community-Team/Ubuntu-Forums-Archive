---
title: "VPN Diagnostics"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by asearle on 2010-05-13
Hi everyone,

I am trying to create a VPN connection between an Ubuntu 9.10 system and a Windows server.

So far I have been able to connect via windows and have found the Wiki for connecting with Ubuntu ...

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

I followed the wiki instructions (setting up a network connection and attempting to connect via the network applet) and my password was requested but the system (after trying for about a minute) gave the message that the connection had failed.

What I really need to know now is how to diagnose why it failed and what I need to change.

Maybe someone can help me here?  Or maybe there is an alternative HOWTO explaining connecting Ubuntu to Windows via VPN?

I have googled and there is an enormous amount of information on this subject:  So much that I really don't know where to start!

Any tips would be a great help.

Regards and thanks,
Alan Searle

---

### Post by arkham on 2010-05-13
Hi Alan,

Having set up quite a few VPNs (though mainly Cisco/Juniper based) on Ubuntu, they can be tricky beasts.  Can you clarify what version of Ubuntu you are using and what you are connecting to?

I think, given your post it is most likely 9.10 and you are following "PPTP VPN Configuration" in that section, but before we go down any rabbit holes I'd like to be sure....

A.

---

### Post by adelricbilly on 2010-05-13
The best way to vpn connections debug [URL="http://www.vistax64.com/#"]_[COLOR=Black][/COLOR]_[IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL] is watch the traffic.  Some
vpn clients have very extensive diagnostics.  See if yours has a debug or
diagnostic window to bring up. As it turns out, the VPN information is scattered in the registry and in some bizarre XML-like format it doesn't appear to be XML exactly deep in the depths of Windows - one of the areas with really long file names.  I found it by doing a scan of System32 using ExamDiff Pro.

---

### Post by asearle on 2010-05-14
Hi Guys,

Thanks for the feedback.

Yes, I am using Ubuntu 9.10 with all settings set as described in the Wiki:

- PPTP
- MSCHAPv2
- Point to Point encryption
- allow stateful encryption

But I don't have a client:  I simply use the Network Connection Applet which tries to connect and then says that a connection couldn't be established.

Any ideas on this?

Should I change my settings?

What VPN Client should I install/use in order to get maximum transparency regarding what is happening with the connection?

If I could get this working, then it would mean that I could take another big step away from Windows.  That would be great !!!

Many thanks,
Alan Searle

---

