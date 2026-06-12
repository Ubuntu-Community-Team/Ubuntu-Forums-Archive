---
title: "OpenVPN issue"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by chamm on 2010-10-13
I downloaded and installed 10.10 when it came out. I installed network-manager-openvpn and it worked pretty easily to connect to my office router, which is an Astaro firewall/router. So yesterday, I was monkeying with the install, which was working fine, and I clobbered something. It was pretty experimental, so I didn't give it much thought. I just decided to reinstall.

Since the reinstall, I can't get VPN connectivity working to save my life. I've done just the desktop install, sudo apt-get install network-manager-openvpn, and run through what I think are the same steps I ran through before. (The firewall spits out an ovpn file along with the keys and certs you need to connect.) I've done nothing else. I even tried a fresh install before running the update utility.

Here are the symptoms: The VPN connects, but once it does, all IP traffic stops. I can't ping the firewall across the VPN, or even Google/Yahoo, etc. I CAN ping local LAN resources. The routing table looks correct, but the connection acts as if it has no default route.

If I try to connect from a command line, I seem to connect just fine.[FONT=Courier New][SIZE=1][FONT=Tahoma][SIZE=2] I use[/SIZE][/FONT][SIZE=2] sudo openvpn --config configfile.ovpn[/SIZE] [/SIZE][/FONT]When I attempt to connect using network-manager, the tunnel stays up. If I check /var/log/messages, I just get a single line:
[FONT=Courier New]
[SIZE=2]Oct 13 21:26:43 chnet123 kernel: [ 1209.172788] tun0: Disabled Privacy Extensions[/SIZE][/FONT]

I do not know if that is relevant or not. I also get this message when I successfully connect via the command line, so it's probably irrelavent.

To my knowledge, nothing has changed on my firewall, which I manage. It's an Astaro firewall, which is Linux based, and it's using OpenVPN as well for the firewall on that end. I've got several Windows clients that can connect just fine, and haven't had any change in connectivity in teh last couple days. I can also connect to a PPTP VPN just fine, it's only OpenVPN that seems to be broken. I've got to think that I'm missing something, but I can't figure out what it is.

---

### Post by chamm on 2010-10-13
Got it. More info for anyone else running into this problem:  in /var/log/daemon.log I found the following error message:  

[FONT=Courier New]write to TUN/TAP : Invalid argument (code=22) [/FONT]

Some google-fu pointed me to a similar thread talking about LZO compression. Went into advanced settings for the VPN connection, and enabled LZO data compression, and voila. It works fine now.  What I'll never understand is why this setting changed. I'm 100% sure I never enabled LZO compression before, but maybe some default setting changed somewhere. All I know is, it's working now!

---

### Post by chamm on 2010-10-13
OK, I want to do the right thing and mark this thread as [SOLVED] but I'm obviously too much of a noob to figure out how to do that. Any pointers?

---

### Post by bu3askoor on 2010-11-09
thanks chamm, enabling lzo compression also fixed my issue.

---

