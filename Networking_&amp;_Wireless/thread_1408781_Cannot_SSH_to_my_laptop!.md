---
title: "Cannot SSH to my laptop!"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by crowhill on 2010-02-16
Hi there

I have a laptop at home (A) and a PC in my office (B). I can SSH from A to B but not from B to A.

Both A and B run Ubuntu 9.10 and have openssh-server installed.

My laptop at home (A) is behind a router and I read somewhere that this could be the reason why my connection times out when I try

ssh my_username_on_my_laptop@the_WAN_ip_address_of_my_router.

The error I get is "ssh: connection to host the_WAN_ip_address_of_my_router port 22: Connection timed out". Therefore, I logged into my router and enabled the service "SSH(TCP/UDP:22)", typed my DHCP gateway ip address (also the DNS proxy ip address) into the entry for the LAN server ip address and made sure that the remote ip address is the_WAN_ip_address_of_my_router.

I'm sure I don't know the meaning of what I just wrote. I just looked that stuff up after having logged into the ip address of my router.

A first question I have is whether I was supposed to use my personal ip address that I have inside the network at home (figured it out by staring at the output of ifconfig) in place of the DHCP gateway ip address (also the DNS proxy ip address) when filling out the LAN server ip address.

Then, of course, I wonder what is still going wrong. Sitting at B, I'm able to ping the_WAN_ip_address_of_my_router but I cannot ssh into my laptop (A) that is behind the router.

The router allows me to change about 1000 settings but I have no clue what to do with them.

The following seems important in this context too: As I already said, I can ssh from A to B but not the other way round. Now, assume I change settings in the router. Can I test the usefulness of these settings by ssh-ing into B (from A), from which I then try to ssh into A (from B). Does this circular ssh-ing make sense? It would provide a (geographically) convenient way to test my changes.

Thanks so much for any advices on this.

I really need to be able to get from B to A but I fail.

Cheers,
crowhill.

---

### Post by amac777 on 2010-02-16
Hi, yes, you should forward the SSH port (22) from your router to your internal LAN ip address for the server. 

Here's a web page that has some information that should walk you through how to do it:

[http://portforward.com/](http://portforward.com/)

Also, yes, the circular sshing should work. So you can ssh from A->B and then test your router settings by trying to ssh from B back to A again. (all while sitting at A)

---

### Post by crowhill on 2010-02-16
Thanks a lot for the very quick answer!

I checket out the link you provided. What they suggest to do is, first, to set up a static ip. I tried to do that by first disabling DHCP in the router. Then, I lost the internet connection and had to call the provider to perform a reboot.

They told me that they do not allow having static ip addresses. 

How can i forward a port to a dynamic ip address? Is that even possible?

Thanks a again,
cheers,
crowhill.

---

### Post by amac777 on 2010-02-17
Yes, it's still possible. First, a little theory since I think you may be misunderstanding a bit. 

1. Your router is assigned your public IP address by your provider. You can check to see what your public IP address is by browsing to a website like this: [http://whatismyipaddress.com/](http://whatismyipaddress.com/). Since your provider does not give you a static IP address, this address may change periodically. This is not a problem.

2. Your ubuntu server should have a static *private* IP address on your LAN, for example, set it to have 192.168.0.100 or something like that. You can use network manager or any of your favorite setup on Ubuntu to configure this private IP address. Remeber, your private IP address is not related to your public IP address provided by your provider. You can check what your private IP address on your LAN is by running 'ifconfig' in the terminal of your ubuntu server.

3. You need to setup your router to forward packets to incoming port 22 of your public IP address to the same port of your Ubuntu server's private IP address on your LAN. What this means is that when someone on the Internet tries to access port 22 of your public IP address, your router will automatically forward the request to port 22 of your private IP address so your Ubuntu server can handle it. This forwarding is invisible to the external user and they won't even know it's happening.

So once you have all that setup, you should be able to test it and confirm it works (ie, you can use ssh in both directions without problem).

4. The last step is that because your public IP address may change sometimes due to your provider, you shoudl sign up for something called a "dynamic dns". This can be done for free using a service like [http://www.dyndns.com/](http://www.dyndns.com/), for example. It involves running a small program on your server that will periodically report your public IP address to a DNS server, and then you always access your server via a URL like my-url.something.com. That way, it doesn't matter if your public IP address changes because the url will be automatically updated to point to the new public IP address.

---

### Post by crowhill on 2010-02-17
Great! I'm starting to know what I have to do. I'll check out the link you provided and I'll let you know. Thanks a lot for that!

Cheers,
crowhill.

---

### Post by crowhill on 2010-02-17
OK, I logged once again into my router (SMC8014WG) and went to the port forwarding option. There, I can do the following

> Users can configure the SMC8014WG to provide the port forwarding services which allow the Internet users to access local services such as the Web server or FTP server at your local site. This is done by redirecting the combination of the WAN IP address and the service port to the local private IP and its service port. The maximum total number allowed for predefined and customer-defined services is 100.

So I try to add a "Predefined Service Table" by setting the service to SSH(TCP/UDP:22). For the "LAN Server IP" I use my private IP (192.168.0.xxx) and for the "Remote IPs" I choose a "Singe address", namely, the public IP of my router (looked it up on the linke you provided). I then log out, ssh to to my office machine but, still, get a "Connection timed out error" when trying to ssh back to my laptop.

Any ideas?

Thank you so much for your help!

Cheers,
crowhill.

---

### Post by amac777 on 2010-02-17
I don't think you should limit the remote IPs to the single IP address of your router. This will not allow any traffic into your server. What that remote IPs setting actually refers to is which remote IP address do you want to allow to connect to your ssh server. It's a security setting. For example, if you knew you only wanted to ssh into you ssh server from your office computer, you could limit the remote IPs to your office computer's public IP address. Any other computer that attempts to connect will time out.

In your case, and especially while you are still testing things, you should leave the remote IPs set to "Any" so that all remote computers can access your ssh server.

---

### Post by crowhill on 2010-02-20
Thank you very much! It is now working. All I had to do was to use the IP address of my office machine as "Remote IP". That did the trick.

Cheers and thx again,
crowhill.

---

