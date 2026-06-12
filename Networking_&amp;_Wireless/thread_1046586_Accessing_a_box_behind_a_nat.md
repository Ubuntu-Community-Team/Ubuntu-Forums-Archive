---
title: "Accessing a box behind a nat"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by GLMnet on 2009-01-21
Hi people
Is there anyway to connect to a computer without having a port forwarded? 
Id like to open a SSH tunnel to my linux at home using putty at work, but at home I can't forward a port, my isp doesn't give me public ip so I cant have dyndns or something like that.

Thank you.

---

### Post by Kebabman on 2009-01-21
You won't be able to ssh to your home machine in that situation. Unless obviously your ISP would forward the port for you which i very much doubt. 

What exactly is it you wish to achieve with your ssh tunnel and does your work computer have a globally accessible IP address?

---

### Post by GLMnet on 2009-01-21
Yes, my work has a public address wich I am "network admin"
I guess I could setup an always on connection in the xubuntu to my work's vpn.
I have no idea how to do that.

---

### Post by jimv on 2009-01-21
You can setup an SSH server at work, and use the -R option when you SSH into it from your home machine to create a tunnel back to your home machine.

Then you use that tunnel from work to ssh into your home machine.

SO from home, the command would look like this:

ssh workserver 12345:homeserver:22

Then from work, you'd do this:

ssh localhost -p 12345
Someone correct me if I'm wrong, but I'm pretty sure that will do it.

---

