---
title: "Is There a Fast Ubuntu-Ubuntu VNC? (or anything else)"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by SedaliaSteve on 2009-07-21
I have a 9.04 alternate Desktop distro that might become something of a music and fileserver since it is peppy and has a 1T RAID 1. I also have a Dell Mini 9 with 9'04. They both work well. They just don't communicate. There are several Windows machines in the house. I've found Real VNC let's them do efficient logons between the Windows boxes and each other.

The Ubuntu boxes even perform well going to windows. They really, really suck at communicating to each other. This remote login is a joke. Screens fail to update, keys rarely make it. The performance is unacceptably slow.

I've tried every variant of vnc and nothing works well. I'm lost. Any suggestions?

Steve?

---

### Post by philcamlin on 2009-07-21
enable remote desktop on buuntu and i use tight vnc on my vista

vnc is only as fast as your internet connection is though 

so if its poor vnc is gona be horrid :popcorn:

---

### Post by slavik on 2009-07-21
freenx?

---

### Post by lykwydchykyn on 2009-07-21
VNC is kind of oldschool.

A few options:

 - XDMCP
This is also kind of old school, but works decently over a LAN.  It's not secure enough for the Internet really, so only use it locally.  See this:
[http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu](http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu)

 - NX
Fast, secure, and pretty reliable.  Slightly a pain to set up.  See [www.nomachine.com](www.nomachine.com)

 - X forwarding over SSH
Instead of doing the "remote desktop" thing, you can just ssh into another Linux machine (doesn't have to be Ubuntu) and launch graphical programs from the console.  They'll appear on your own desktop.

---

### Post by superprash2003 on 2009-07-21
in ubuntu ensure that compiz fusion ( or extra effects ) is disabled as it has some issues with VNC

---

### Post by SedaliaSteve on 2009-07-23
> **superprash2003 said:**
> in ubuntu ensure that compiz fusion ( or extra effects ) is disabled as it has some issues with VNC

Thanks. That really made a huge difference. I guess that going between window & ubuntu this wasn't an issue but it made ubuntu to ubuntu connections awful.

I know that VNC is oldschool but I was looking for something lightweight that would work fine on some very old windows machines. I'll try to come up with something more elegant but this will get me going.

Steve

---

### Post by pricetech on 2009-07-23
> **lykwydchykyn said:**
> VNC is kind of oldschool.

A few options:

 - XDMCP
This is also kind of old school, but works decently over a LAN.  It's not secure enough for the Internet really, so only use it locally.  See this:
[http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu](http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu)

 - NX
Fast, secure, and pretty reliable.  Slightly a pain to set up.  See [www.nomachine.com](www.nomachine.com)

 - X forwarding over SSH
Instead of doing the "remote desktop" thing, you can just ssh into another Linux machine (doesn't have to be Ubuntu) and launch graphical programs from the console.  They'll appear on your own desktop.

I need to pick your brain chykyn.  I wasn't able to make X over SSH work.

---

### Post by lykwydchykyn on 2009-07-23
> **pricetech said:**
> I need to pick your brain chykyn.  I wasn't able to make X over SSH work.

Well, you know where to find me!

I guess I should've mentioned, there are two things that have to be done to make X forward over ssh:

- the server has to have X forwarding enabled.  It's disabled by default (this setting is in /etc/ssh/sshd_config)
- the client needs to have X forwarding enabled.  You can do this when you run it by adding the "-X" switch, or make it default by changing it in the config (/etc/ssh/ssh_config)(note the absence of the "d" in the filename).

the relevant parameter is "ForwardX11"

---

