---
title: "SSH Port Forwarding to Multiple IPs"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by drmrgd on 2012-10-16
I'm really uninformed when it comes to networking, and I have what is probably a very simple question:  how can I have my router forward traffic from SSH requests to 2 IP addresses?  

Here's the situation.  I have a 12.04 box with OpenSSH installed.  Let's say that the public IP address for that box is 123.456.78.9.  It's behind a router that's giving it IP address (let's say): 1.1.1.2.  So, under normal circumstances, I would just have the router forward traffic coming in at 123.456.78.9:22 to 1.1.1.2:22, right?  

The complication comes as I have virtual machine running a test server on that box, which has IP address (let's say) 1.1.1.3.  I mainly need to SSH into that VM.  So, in that instance I can forward to the VM IP address instead, and then in the event that I need to access the host machine, I can just ssh from the VM...no problem.

However, I'd like to be able to just launch the VM remotely as needed, which would require me to SSH directly into host and then launch the VM.  However, once the VM is launched, I now need *all* traffic coming over 22 to be routed to the VM SSH server (this is because of the way the API I'm using is written, and I'm not quite sure how to modify it).  

So, what's the best solution here?  I can't quite grasp how I might have the same IP direct traffic to the correct server depending on my needs.  Can someone enlighten a complete networking dunce on how to get around this?

---

### Post by SlugSlug on 2012-10-16
Setup your host to use a different port for ssh (say 10022) its in /etc/ssh/sshd.conf


then forward port 10022 in router


to ssh in to host you now use

ssh -p 10022 user@host

---

### Post by drmrgd on 2012-10-16
Ahhhh!  I figured it must be really simple and I was just missing something obvious.  

So, when I need to ssh into host, the address is 123.456.78.9:10022 and when I want to directly ssh into the VM, the address is 123.456.78.9:22.  And I can specify alternative ports by using the '-p' option of ssh.  Why didn't I think of that?!

Thank you for your help!

---

### Post by SlugSlug on 2012-10-16
no prob

---

### Post by Lars Noodén on 2012-10-16
Edit: never mind.

---

### Post by ahallubuntu on 2012-10-16
I prefer to keep the port number the same (22) on the machine but change the port number in the router, when forwarding.  So, I might forward port 10022 of my IP to port 22 of the IP of the client box.  That means I only have to change one thing (the router config) and not the ssh config of the machine.

Some router configs may not support this, though.

---

### Post by drmrgd on 2012-10-16
This is how I understood SlugSlug's advice (maybe I misunderstood though).  So, what I thought is that OpenSSH on the VM Server and the Host Server will be listening for traffic on 22.  The router will direct traffic coming over 22 to the VM and coming over 10022 to the Host.  In that case, I don't need to change anything on the server, and just need to be sure that I specify the port I want to use when connecting to the server from the client (i.e. 'ssh -p 10022 123.456.78.9' when I want to connect to the Host Server and 'ssh 123.456.78.9' when I want to connect to the VM (guess I don't need to specify a port if it's 22).

---

### Post by SlugSlug on 2012-10-16
Yes that will work as long as your router supports port mapping (send incoming port 10022 to local port 22)  if your router does not allow this then you'll need ssh to listen on 10022 - and that can be done in the config

---

### Post by drmrgd on 2012-10-16
> **SlugSlug said:**
> Yes that will work as long as your router supports port mapping (send incoming port 10022 to local port 22)  if your router does not allow this then you'll need ssh to listen on 10022 - and that can be done in the config

Yes, I think that's no problem.   I'll have to wait until I get home to double-check.  But, I'm almost positive I can do this on my router.

---

