---
title: "Remote login to Ubuntu"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by nimajiman on 2009-10-15
Hi all,

Once Ubuntu Karmic launches at the end of the month, I will be doing a fresh install on my machine. My brother (who lives in a different suburb) also wants to try Ubuntu after seeing me run it. I have been using it for a couple of years now, but this will be his first time after being eternally frustrated with his XP setup. 

What I want to be able to do though is once I've put a fresh install on both his and my machines, be able to set them up so I can do a remote login to his machine from my house, in case I need to help walk him through any of the basics as he learns how to use Ubuntu. I'm not talking command-line ssh etc, as this will just freak him out and probably put him off. In my opinion Ubuntu has progressed enough by now that I'm hoping I can do this graphically, I just don't know where to start.

I'm wondering whether there is an easy way to do this, and if so what programs should be installed on each machine and how to set them both up to enable this. Remember we're in different houses not on the same LAN.

Anyone have any suggestions or know where to point me? 

Cheers

---

### Post by tim_wright on 2009-10-15
On the host machine: System --> Preferences --> Remote Desktop
On the client machine: Applications --> Internet --> Remote Desktop Viewer

That should get you going :)

---

### Post by nimajiman on 2009-10-15
> **tim_wright said:**
> On the host machine: System --> Preferences --> Remote Desktop
On the client machine: Applications --> Internet --> Remote Desktop Viewer

That should get you going :)
Cheers, thanks for that.

When I open System->Preferences->Remote Desktop on my current machine (running Jaunty) it says my desktop is only reachable over the local network.

I'm guessing this has to do with port forwarding. Do you know what ports would have to be forwarded for this to work outside of the local network?

---

### Post by fishy6969 on 2009-10-15
port 5900 

Regards

---

### Post by nimajiman on 2009-10-15
Thanks.

One last question. When I open Remote Desktop Viewer and click Connect, there is a field to enter 'host'. Do I just put in the external IP of the computer I want to connect to like:

124.159.XX.XXX ?

Or is it more complicated than that. Not sure if I have to specify ports etc myself, or whether vinagre already looks at port 5900 automatically.

---

### Post by fishy6969 on 2009-10-16
Yes. Put the external host IP in. The port should be set automatically.

---

### Post by fela on 2009-10-16
Just a thought: isn't it incredibly risky forwarding the VNC port? I can't begin to imagine how many security flaws forwarding VNC to the outside world would bring in...

---

### Post by fishy6969 on 2009-10-16
Forgot to add - any problems with this approach have a look at [gitso]("http://code.google.com/p/gitso/").

---

### Post by CharlesA on 2009-10-16
> **fela said:**
> Just a thought: isn't it incredibly risky forwarding the VNC port? I can't begin to imagine how many security flaws forwarding VNC to the outside world would bring in...

This. You'd could probably SSH over and tunnel VNC over it.

---

### Post by fishy6969 on 2009-10-16
Re Security

True it's a potential problem. It can of course be password protected and the router set up (if it supports it) to only accept connections from a specific IP. Other solutions would include tunneling over ssh [https://help.ubuntu.com/community/VNC#SSH%20port-forwarding](https://help.ubuntu.com/community/VNC#SSH%20port-forwarding), or install FreeNX (which is my perferred option) - [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by CharlesA on 2009-10-16
> **fishy6969 said:**
> Re Security

True it's a potential problem. It can of course be password protected and the router set up (if it supports it) to only accept connections from a specific IP. Other solutions would include tunneling over ssh [https://help.ubuntu.com/community/VNC#SSH%20port-forwarding](https://help.ubuntu.com/community/VNC#SSH%20port-forwarding), or install FreeNX (which is my perferred option) - [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

I could never get NX to actually work. I think I gave up on it after trying to get it running after about 2 hours. Went back to regular VNC after that.

---

### Post by fishy6969 on 2009-10-16
I found that at first, but I'd highly customized my sshd_config file which it didn't like. Use it all the time now and it's useable even over a slow (128k) link.

---

### Post by CharlesA on 2009-10-16
> **fishy6969 said:**
> I found that at first, but I'd highly customized my sshd_config file which it didn't like. Use it all the time now and it's useable even over a slow (128k) link.

Did you have to install it when SSH was running on port 22? I remember some errors that told me to change the conf file with the correct port number.

I might try to install it on VB to play around with it, since I don't want to screw up my production server.

---

### Post by fishy6969 on 2009-10-16
I've currently got it installed on a 8.04 Desktop in a VM (openvz but KVM/Virtualbox should work OK). I installed it on a 'vanilla' install. I have found problems with 8.10 and 9.04 though.

I should contribute and put up an openvz freenx/8.04 image on the openvz website. Maybe next week...

---

