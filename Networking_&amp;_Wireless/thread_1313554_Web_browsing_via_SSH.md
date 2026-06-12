---
title: "Web browsing via SSH"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by davidfromoz on 2009-11-03
Hi Everybody,

My goal is to make use of my Ubuntu 8.10 PC at home to access a site restricted by my company's firewall policy.  I'm something of a Linux newbie.

I have:

1.) Verified web browsing from my PC at home.
2.) Opened a hole in the firewall (port 443) at my house and forwarded it to my PC (port 22).
3.) Installed Putty on my PC at work (Windows XP).
4.) Configured Putty to create an SSH tunnel starting at a local port on my work PC that goes via my companies HTTP Proxy.
5.) Configured Firefox on my work PC to use a SOCKS5 server at that port.

When I start the tunnel and use Firefox to try to browse the following condition exists.

I can use the Putty terminal session to access my home PC.
I can use Firefox to access web resources delivery by my home PC at home (apache and PhPMyAdmin config page)
I can use Firefox to access web sites by entering an IP address.  Eg. I can access the google site by typing in the IP address of that site.
When I try to access google.com I get "server not found".

I believe that Putty forwards the URL to my Ubuntu box.  So I think that Ubuntu is not performing the DNS lookup.

How should I proceed or what capability of my Ubuntu box should I be learning about in order to take the next step?  Am I correct in thinking that the remote Firefox should work pretty much the same as the local firefox running on my homePC?  Are there services that need to be running on my Ubuntu box to enable this?

cheers,
david

---

### Post by b0b138 on 2009-11-03
While I can't help you exactly as you're currently trying to do, I can offer another possible solution.

Assuming you have successfully established an ssh connection to you home pc, remote control it. Check out this page [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) Theres a section on logging in from a windows pc.  ):P

---

### Post by davidfromoz on 2009-11-04
Thank you for your help.

I now strongly suspect that this issue is not Ubuntu related.  Using Chrome I am able to browse the web via the tunnel.  Just not with Firefox.  I have not been able to establish why this is.  But I think that makes it seem at least very likely that Ubuntu is doing what I expect.  I'll change my direction and try to work out how I can configure Firefox to do the same thing.

cheers,
david

---

### Post by WindPower on 2009-11-04
Try going to about:config and toggle the preference "network.proxy.socks_remote_dns".

---

### Post by davidfromoz on 2009-11-06
That did it!  Thank you very much.  I had been scouring Firefox for that kind of option.

Typing about:config in the address bar allows me to change that and a zillion other options I didn't know about.  This particular setting allows me to browse by the internet via the SSH tunnel.

cheers
david

---

