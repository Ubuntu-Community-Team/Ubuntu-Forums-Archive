---
title: "How to setup MythTV for remote access?"
date: 2011-02-21
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-21
I have a laptop that I use only as a FE and it can access my Mythbox (FE & BE) from anywhere on my home network. Works great.

I can also add that I have successfully used MythWeb remotely (outside my home network) using a Windows Laptop. So everything works - MythTV, port forwarding, etc.

Now I would like to use my FE only laptop remotely (outside of my home network)...

1. what ports do I need to open to the outside?
2. what settings need to be changed in FE & BE?

PS - let's forget about bandwidth issues for the sake of this discussion. I just would like to know how to use a FE outside of my home network.

---

### Post by nickrout on 2011-02-21
> **nhtrader said:**
> I have a laptop that I use only as a FE and it can access my Mythbox (FE & BE) from anywhere on my home network. Works great.

I can also add that I have successfully used MythWeb remotely (outside my home network) using a Windows Laptop. So everything works - MythTV, port forwarding, etc.

Now I would like to use my FE only laptop remotely (outside of my home network)...

1. what ports do I need to open to the outside?
2. what settings need to be changed in FE & BE?

PS - let's forget about bandwidth issues for the sake of this discussion. I just would like to know how to use a FE outside of my home network.

This is seriously not recommended. mythbackend is not designed to be secure on untrusted networks.

If you insist on this then create a VPN tunnel.

---

### Post by tgm4883 on 2011-02-21
> **nickrout said:**
> This is seriously not recommended. mythbackend is not designed to be secure on untrusted networks.

If you insist on this then create a VPN tunnel.

Seconded. Create a secure tunnel. Don't open up ports you don't need to

---

### Post by nhtrader on 2011-02-22
> **tgm4883 said:**
> Seconded. Create a secure tunnel. Don't open up ports you don't need to


I understand that it's a security risk. Now consider this question as a theoretical one. Barring this risk, what do I need to do to connect remotely?


(NOTE: I just enabled mythweb's new flash video feature and it works beautifully in the small preview player. This feature in MythTV 0.24 is great. I didn't know that it could convert *.mpg files on the fly into flash video. But I'd like to explore all that is possible with MythTV - with your help of course.)

---

### Post by tgm4883 on 2011-02-22
> **nhtrader said:**
> I understand that it's a security risk. Now consider this question as a theoretical one. Barring this risk, what do I need to do to connect remotely?


(NOTE: I just enabled mythweb's new flash video feature and it works beautifully in the small preview player. This feature in MythTV 0.24 is great. I didn't know that it could convert *.mpg files on the fly into flash video. But I'd like to explore all that is possible with MythTV - with your help of course.)

Create a VPN/SSH tunnel so it looks like you are on the same network. 

I'm not going to help you make your network less secure, it's obvious that if you don't already know how to do this that you shouldn't be making decisions about the security of your own network.

---

### Post by nhtrader on 2011-02-23
> **tgm4883 said:**
> Create a VPN/SSH tunnel so it looks like you are on the same network. 

I'm not going to help you make your network less secure, it's obvious that if you don't already know how to do this that you shouldn't be making decisions about the security of your own network.


I understand your position. I'll figure out if VPN is possible with my router. Not all routers support this feature.

---

### Post by winewood on 2011-02-24
[]("http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/2-configure-putty-ssh-tunnel-ssh-server.shtml")I found some instructions for creating a secure tunnel to forward the ports of your choice to your internal box.  You do not have to open any ports external EXECPT SSH.

On your unix box, simply install squid (the proxy) and make sure the SSH has good security on it.

[Heres the link]("http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/2-configure-putty-ssh-tunnel-ssh-server.shtml")

My client side machines are Windows, but the idea / concept should be very much the same for a linux laptop im guessing.

---

### Post by nhtrader on 2011-02-24
> **winewood said:**
> I found some instructions for creating a secure tunnel to forward the ports of your choice to your internal box.  You do not have to open any ports external EXECPT SSH.

On your unix box, simply install squid (the proxy) and make sure the SSH has good security on it.

[Heres the link]("http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/2-configure-putty-ssh-tunnel-ssh-server.shtml")

My client side machines are Windows, but the idea / concept should be very much the same for a linux laptop im guessing.


Thanks for the tip. I'll try this out and get back to you.

---

### Post by winewood on 2011-02-28
I confirmed tihs on an Ubuntu laptop that I can download Putty server and this works just like Windows.

---

### Post by nickrout on 2011-03-03
> **winewood said:**
> I confirmed tihs on an Ubuntu laptop that I can download Putty server and this works just like Windows.

putty is a client not a server.

---

### Post by winewood on 2011-03-03
Thanks for clarifiying nickrout. I was viewing the 2 downloadable putty clients, via doanload manager, and one has 2 computers connected with a lightning bolt as an icon.  The name beside that distro was Putty Server, but I know its just a repeat of the windows client.  Don't know why they named it such.  Thats the one you want. 
Using this, I have only 1 port open to the outside, and my connection via openSSH is as safe as I think I can get.

---

### Post by Vojta01 on 2011-03-09
Can anyone please advise which port/-s has to be forwarded when using MythtTV remote access?

---

### Post by winewood on 2011-03-09
The SSH port is 22 if you are doing it that way.  
The mythweb http port is 80, but only open that up if you have security enabled via apache such as .htaccess.

---

### Post by Vojta01 on 2011-03-09
And what ports needs to be forwarded, when I want to connect with Mythfrontend to Mythbackend remotely over the internet (not mythweb)?

---

### Post by winewood on 2011-03-09
The most obvious would have to be the connection options that are already in your current front end connections to the database. If you have a current front end setup, see what the IP and the port your frontend talks to your backend on. Open up that port. As for other ports, I can not say.
 
Note: Anything under a 20 Megabyte connection upstream from your router (lan speed), I forsee as nothing but pausing, errors, and look like junk on HD size stream. A good test would be to connect remotely and using mythweb, download the program you want to see. If it takes 25 minutes to download a 30 minute show it *could* work. If the download time of your show is greater than the length, you should avoid this. Remote access is one thing, but the frontend wasn't designed to be used over the internet. I would love to be proven wrong if you get it working though. 
 
Why not just get a slingbox and connect to a TV remotely? It can do it on a 3-5 meg connection with its compression algorithims?? Only 1 port is needed to open and it saves you a TON of work. I will note that linux clients via the web frontend to the slingbox aren't supported.

---

### Post by nickrout on 2011-03-09
> **Vojta01 said:**
> And what ports needs to be forwarded, when I want to connect with Mythfrontend to Mythbackend remotely over the internet (not mythweb)?

it is ***_Highly_*** undesirable to open a myth backend to the internet at large. It is not designed to be secure, it is designed for private LANs only.

So your best bet if you want to persist, and assuming you have a very large bandwidth, is to create a secure tunnel using one of the standard tools like openvpn etc.

If you really want to expose yourself to the dangers of not doing this securely, you will need at least mysql access (port 3306), and the ports that mythbackend use, 6547 plus another (I think) for streaming. Try using tcpdump on your system to check.

---

