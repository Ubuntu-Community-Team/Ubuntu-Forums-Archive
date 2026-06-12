---
title: "VPN - how to set up?"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by dunbrokin on 2012-10-16
What I want to do is to have my home system i.e. behind the router, as a VPN that I can tunnel into from outside by either my table or laptop. In the VPN there should be a mail server and web browser server that I can link to by tablet or laptop. I envisage just having a vpn name etc that I can put into the Network Manager and go from there (my wife is not going to use the command line with her pc).

How do I go about achieving this? What are the steps?

Thanks in advance!

---

### Post by ahallubuntu on 2012-10-16
I use OpenVPN.  It works very well to do exactly what you say.  I have OpenVPN installed on my router, which uses DD-WRT (Linux-based) firmware.  But if you are willing to leave a Linux machine on 24/7 on your home network, you can install OpenVPN server there too instead.

VPN would not include a web or mail server.  If you want those things, set them up on your home network.  All VPN does is connect you from outside to your home network via a tunnel.  

There are plenty of tutorials on the web for setting up OpenVPN.

---

### Post by dunbrokin on 2012-10-16
Thank you for that, I understand about OpenVPN...but I need it to work in combination with a web server and mail server....and set it up so that all I have to do is to enter the remote ID into the Netowrk Manager VPN set up.

---

### Post by ahallubuntu on 2012-10-16
OK, let me give you an example: I host my own web and email server at home off of my internet connection.  My server is an Ubuntu server box.  It has no VPN built into it and I wouldn't want it built in.  But I can access it remotely via router which has an OpenVPN server installed on it.  Yes, I have the OpenVPN add-on installed for Network Manager on my Ubuntu laptop.  I choose my saved VPN connection from a list when I'm out in the world somewhere online, and after about 5-10 seconds I am connected.  Now I can access my home server as if I were at home.

(In my case, I also allow public access to my web and email server by opening ports 25 and 80.  You  may not.  But to get ssh access to my server, I must connect via VPN first.)

I have the OpenVPN server installed on my router/firewall.  I can access anything on my home network when I'm connected via VPN, including my web server and any other computer on my network.  I could certainly have chosen to install the OpenVPN server on my web/email server and just forward the VPN port through my router, but I found it better in my case to have it installed on my router.  That way, I can get VPN access no matter what the state of my server.  My router will always be on.

I also had to install OpenVPN on my laptop plus that Network Manager add-on.

Otherwise, I guess I'm not clear what you are trying to achieve  different from what I do?  The purpose of a VPN is to connect you remotely to a local network.  The server you want to access would be connected to your local network.

---

### Post by dunbrokin on 2012-10-16
Thank you for that, I think we are very much on the same wavelength. I just worry that setting up the VPN/ssh may require command line input...and that is not going to work for my wife. I could probably get her to use the VPN in Network Manager...but that would be her limit I am guessing. Maybe I am misunderstanding the connection procedure that you are suggesting?

---

### Post by ahallubuntu on 2012-10-16
You will certainly need to do some command line stuff to SETUP your OpenVPN server.  If you really want a secure setup, you would want to use certificates not just a simple passcode.  It takes a little bit of time to understand which certificate files to copy where, but there are good guides online with examples of how to do this.

But once you are DONE setting it up, you or your wife could just click on "Network Connections" in Network manager on the laptop and choose the profile you want to connect to.  No command line required for that, any more than it would be to connect to some random wireless network with Network Manager.

I just googled for some OpenVPN examples for setting up OpenVPN on Ubuntu, and honestly they aren't as easy to use as I recalled.  I guess I hadn't looked at them in a while.  They don't even mention Network Manager for the client.  (one reason: there's an old bug in network manager where the "connect automatically" feature doesn't work if you *ALWAYS* want to connect to your VPN whenever you get on the internet.  I'm used to connecting manually each time, and I'm not always on my VPN.)

Anyway, if you can install OpenVPN on your Ubuntu server, on your Ubuntu laptop just install "network-manager-openvpn" which will add an OpenVPN widget to Network Manager's VPN setup.  Then when you try to setup a VPN connection within Network Manager, choose OpenVPN, and then you can point to the certificates and the config file suggested by the Ubuntu OpenVPN tutorials.

You'll also need to forward port 1194 through your router to your server with OpenVPN running on it.

---

### Post by dunbrokin on 2012-10-16
Great, thanks for that, I really appreciate it. I guess then I have to set up an old PC as a Ubuntu Server and then set it up to act as a mail server and a web server and then put OpenVPN on it so that I can access it remotely. I presume my Android Table will also be able to access the VPN in the same way.

---

### Post by ahallubuntu on 2012-10-16
I don't know why you need to have a web and email server - but that seems unrelated to whether or not you have a VPN.  I use my web server to host websites I maintain.  If I didn't host at home, I'd still have a VPN today, just to get into my home network now and then.  I hosted a web server at home before I had a VPN.  To me, they are unrelated.  Perhaps you have some need to have a web/mail server for something else?

I believe there is an OpenVPN app for Android - not 100% sure but I imagine there is.

---

### Post by dunbrokin on 2012-10-17
My idea was that while you are away from home and using public systems, the information that you are transmitting (browsing and email) are not secure....whereas if you were to use a VPN to your home system using ssh then your information is encrypted and secure.

---

### Post by ahallubuntu on 2012-10-17
VPN is encrypted just like ssh.  You can use either one; you don't have to use both just for security.  Any normally open email or web activity is secure when done over a VPN, as secure as if you were on your home network.

---

### Post by dunbrokin on 2012-10-17
Hmmm!...thank you for your continued input....I seem to have hte wrong end of the stick here. My idea was that I vpn/ssh to my home system as that would then act as web server and mail server....but you are saying that I can vpn (when remote) to any server and it will be encrypted....so, I can see how to VPN to my static home address...but how would I VPN to the X hotel web and mail server for instance?

---

### Post by ahallubuntu on 2012-10-17
Let's back up here a bit.

What's your goal in setting up a VPN at all?  Are you trying to be more secure in your web browsing and email downloading when you are out in the world on some random public wireless network?  That's the only reason I can gather from what you have posted.  Is that it?

(That's not the only reason to use a VPN.  I use my VPN to access computers on my home network.  I also use it to fool websites into thinking I'm home when I'm really overseas.  Some websites like Hulu and Google Voice don't work if you aren't in North America.)

I think you're still a little confused about how these things work.

When you're home, how do you browse the web?  You don't worry about it, because you feel secure on your home network, right?

All a VPN does is PUT YOU on your home network, securely, when you're at a hotel or a coffee shop or something.  When you go to a website when you're connected to your VPN somewhere, the request doesn't go directly to the website - it goes over your VPN  (through a "tunnel") as through your home network and then goes to the website, AS IF YOU WERE HOME.  That's all the VPN does.  Every website you visit while on your VPN is viewed through your home network.

Pretend you have a really powerful wireless card in your laptop that can pick up  your home wifi network from miles away, from wherever you happen to be.  If you could do that, you would not worry about security, right?  Because you believe your home network is secure.  You could visit hotel websites, whatever without worry.  That's basically what a VPN does: it "tunnels in" to your home network through whatever internet connection you are now on.

You set up a web server to SERVE web pages to other people out in the world.  You don't use a web server to VIEW the web.  I do have a web server that  people visit.  It sounds like you don't need to do that, so there is no reason to setup a web (or email) server.  I think you are just not clear on the lingo here.

---

### Post by dunbrokin on 2012-10-17
You are correct in your analysis....all I am wanting is more security when I am remote for web browsing and email delivery.

I appreciate that that is not the only reason to use VPN - but currently that is all I need it for.

It may well be that my solution is far too elaborate for the problem I face....but I am not aware of any other (than, perhaps, a commercial VPN system) solution.

---

### Post by ahallubuntu on 2012-10-17
Great.  So dig through the OpenVPN tutorials you find on Google and set up a VPN.

---

### Post by lmm5247 on 2012-10-17
> **ahallubuntu said:**
> I use OpenVPN.  It works very well to do exactly what you say.  I have OpenVPN installed on my router, which uses DD-WRT (Linux-based) firmware.  But if you are willing to leave a Linux machine on 24/7 on your home network, you can install OpenVPN server there too instead.

VPN would not include a web or mail server.  If you want those things, set them up on your home network.  All VPN does is connect you from outside to your home network via a tunnel.  

There are plenty of tutorials on the web for setting up OpenVPN.
I just setup a PPTP VPN server on my DDWRT router, very useful :) But, I need to upgrade to OpenVPN like you have...

---

### Post by ahallubuntu on 2012-10-18
I do recommend using OpenVPN within DD-WRT if you can, but not all versions of DD-WRT include an OpenVPN server.  Your router has to have enough RAM and flash to handle an image big enough to have that feature built in.

If you can pick up an old Linksys WRT54G router cheap (version 4 or older), you can run a full version of DD-WRT with OpenVPN.  (You could disable the wireless and use it as a pure gateway.)  Some newer routers that can handle the large image can be had cheaply, too, and also have N wireless.  I use an Asus RT-N13U B1 for my home DD-WRT router/firewall with OpenVPN, and I got it for only $15 USD after rebate.  The GUI interface to the newest versions of DD-WRT allows for a much easier OpenVPN server setup than in the past, too.

OpenVPN in Linux has been awesome for me.  I set up a connection between two offices with it and it is very solid and reliable.  OpenVPN connections via my Ubuntu laptop are very reliable too.  I have noticed that the free Windows OpenVPN client is not very good, though, if you ever want to connect with Windows clients.  There is a cheap but not free OpenVPN Windows client that may be better.

---

### Post by dunbrokin on 2012-10-18
> **ahallubuntu said:**
> Great.  So dig through the OpenVPN tutorials you find on Google and set up a VPN.


Will do, thank you so much...just one question....I was thinking that the VPN was only for linking back to my home sysem....Can I also use it to link to Hotel X's server when I am remote from home.

---

