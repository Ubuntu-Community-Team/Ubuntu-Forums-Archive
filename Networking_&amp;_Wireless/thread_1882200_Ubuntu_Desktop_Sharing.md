---
title: "Ubuntu Desktop Sharing"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by GoFishy on 2011-11-16
So i went into Desktop Sharing and checked allow users to view your desktop and allow others to control your desktop.. Also put in a password

Whenever i try to connect with VNC viewer i just get a Connection timed out (10060)

It doesnt matter if i try it on my local network from a windows computer or i try externally. For externally i setup port forwarding for 5900 .. But would be happy to just get it working from my own network first...

The only other information i have is that i can successfully PING my Ubuntu 11.10 machine from Windows 7.

Any ideas on what im missing?

---

### Post by exup1000 on 2011-11-18
hi sorry no fixes but also have the same issue, for me it was not working in 10.10 and upgraded to see if would fix it.

I have had a bit of a dig around the forums and this is the only thing I can add.

In 10.10 you should see an address in the Desktop sharing GUI, but mine just kept saying local host. I dont get any message in the newer version.

Also following other forums I ran "netstat -antpe" and it does not show anything relating to desktop sharing or port 5900. Ditto if I run "nc -zv localhost 5900"

I can ping my machine via ip and host name both respond.
I have tried various flavours of remote control viewer mainly VNC.

I am not sure how to see if it is running as a service at all.

Hopefully someone can help us.

Cheers.

---

### Post by GoFishy on 2011-11-18
Yeah its the same story for openssh-server.

I have enabled both openssh-server and remote deskop sharing before and they worked out of box without doing anything on my local network.

I have tried installing a VM on one of my SSDs and it works fine, something is funky with my machine. This was a fresh install so maybe ill just try installing again.

---

### Post by exup1000 on 2011-11-20
I hope I dont have to do that as this machine has been running fine for a couple of years now.

If anyone know where to go for more detailed support on remote desktop please let me know, I think its called Vino?

Also where in Ubuntu you can see services running/disabled etc

---

