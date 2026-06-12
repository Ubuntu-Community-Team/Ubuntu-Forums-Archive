---
title: "In need of help with Ubuntu updates behind a proxy"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by ready4thebreak on 2010-12-07
I believe we're using Windows proxies, but I can't be for sure(as the admin is never around anymore, nor is he very open to sharing his network setup). 

Like most people having issues with their proxy, the Internet works perfectly fine and I'm able to use Firefox with no issues. Our network isn't the slightest bit strict in what we can do(it's an IT school), but I can't resolve this issue. I'm attempting to update Synaptic or anything OS related(like drivers and core OS updates) and I've had little luck in my many attempts. I've attempted to edit and add lines to my /etc/bash.bashrc file and /etc/apt/apt.conf as well as the GUI solution in Synaptic and Update Manager(although I'm actually using Mint, but it shouldn't matter).

I think issue lies in the syntax of my login for the proxy. I haven't been about to find anyone with quite the same login as myself, so maybe someone here can help me. An example of the layout is : Login: [email]JohnSmith1234@us10.thisplace.edu[/email](the whole thing) using (again examples,not my actual IP) 87.147.56.7 port 8080 as the proxy address.

I've tried rearranging the information in a few different ways. 
> 
1)http://JohnSmith1234:[/url] [email]password@us10.thisplace.edu[/email]:8080/
2)http://us10\\JohnSmith1234:[/url] [email]password@thisplace.edu[/email]:8080/
3)http://us10.thisplace.edu\\JohnSmith1234:[/url] password@87.147.56.7:8080/

Whenever I refresh my Update Manager or Software Sources, I receive a "(407) Proxy Authentication Required" error. Synaptic usually just hangs(though it still is responding), it just sits there and continually tries to update. Maybe I'm confused or completely missing the point. I've looked around online, but no one had the same layout for the login and using the things that worked for them haven't worked for me.

Can anyone help? I'd appreciate any help! Thanks so much in advance.

---

### Post by viralmeme on 2010-12-07
> **ready4thebreak said:**
> Whenever I refresh my Update Manager or Software Sources, I receive a "(407) Proxy Authentication Required" error

Set the proxy in Synaptic: Settings, Preferences, Network ..

---

### Post by SlugSlug on 2010-12-07
I've never been able to get it to work behind SQUID authentication was ok but I then got size mis-match.

I have to use a direct connection (via gateway but not squid)

---

### Post by ready4thebreak on 2010-12-07
> **viralmeme said:**
> Set the proxy in Synaptic: Settings, Preferences, Network ..

I've already done that(hence why I said I've used the GUI in my original post).

@SlugSlug
How do you know it's a Squid proxy and exactly how did you get it to work?

---

### Post by SlugSlug on 2010-12-07
I know mines a squid proxy as its on one of the servers I look after.. 
I got round it by adding a iptables rule for a block of internal IP's to bypass the routing through squid, so if I need apt-get I can use one of these 'setup IPs'

---

