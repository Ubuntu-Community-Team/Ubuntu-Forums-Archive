---
title: "Can't Connect, Already Port Fowarded"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by icecube45 on 2012-06-26
Hello, this is now my first post on Ubuntu forums, and im sorry it had to be for support.
First of all, sorry if this is in the wrong place
I am trying to set up a minecraft server on my ubuntu laptop, which is running off of my flashdrive (No, its not for installation, i installed to the flashdrive) i port forwarded the port 25565 with my ubuntu laptop's internal ip, and i can connect fine using that internal ip, however, using tools like canyouseeme.org, it shows up as offline, i have added the port all ready to ufw, can anyone help, and has anyone had this before? i have portfowarded many times on different computers fine, just ubuntu doesnt seem to be working for it...

---

### Post by icecube45 on 2012-06-26
Can anyone help? Please? I'm very stumped, I have port fowarded many times before, and this is just wierd

---

### Post by efflandt on 2012-06-27
You do not say what the rest of your network is like or path to internet.  Is your laptop directly connected to the internet with a public IP address, or behind a router on a private IP?

When you successfully connect to the minecraft server, is the client on the same computer or a different computer on a LAN?  What does **netstat -ltn** on the server show?

If your laptop is directly on a public IP with firewall enabled, you would not forward port 25565, but just let it in with ufw.

If your laptop is on a private IP behind a router that has a public IP, on the router you need to forward TCP port 25565 to the LAN IP of your laptop.  If your router is another Ubuntu computer, that one is the one you would use ufw on to forward.

I have played around with minecraft servers on my LAN, and the server alone works fine even using a 1 GHz 2 core tablet PC booting 64-bit Ubuntu from SD.  In server.properties it is best not to set anything for server-ip= (leave it blank, so it can bind to any IP).

Note that if you are trying to enable LAN play from the integrated client/server in a snapshot of the next version, that does not automatically work properly in Linux yet (without modifying /etc/hosts and figuring out what random port it is using).

---

### Post by icecube45 on 2012-06-27
Thanks for the responce, My laptop is a private ip, behind a router with a public ip, it is wireless, but i have set a static ip on it, and everything should be working fine, just in case, i have set ufw to allow all incoming connections, but it still isnt working my client is on a different computer, (i get a blackscreen booting minecraft up on ubuntu, another mystery, for i allreayd updated lwgl) everything works fine inside the network, and i can connect to it using the internal ip, but not with the external, and canyouseeme.org doesnt say that it is up, etc. Also, the port is set to 31415, but i have configured it for that, and it works fine on internal ip, my netstat -ltn shows ```
tcp6       0      0 :::31415                :::*                    LISTEN 
```

I dont know what is wrong with it, if this matters at all, the hard drive blew out on this computer, so im running off a USB that has ubuntu installed to it (not the installer)

---

### Post by icecube45 on 2012-06-27
If we can get this to work, I'll invite you to play on the Tekkit server if you would wish

---

