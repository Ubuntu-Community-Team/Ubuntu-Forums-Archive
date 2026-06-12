---
title: "Unable to access mythweb via SSH"
date: 2013-03-21
forum: Mythbuntu
---

### Post by brandonros on 2013-03-21
Hi,
I'm fairly new to mythweb and SSH, but I've set up my port forwarding and I can't access the mythweb page.  I've followed these directions... [http://parker1.co.uk/mythtv_ssh.php](http://parker1.co.uk/mythtv_ssh.php)
I can access the backend page using port "http://localhost:6547", and when I try to access mythweb from the browser using, "http://localhost:18080", I am asked to enter my username and password as I had setup for mythweb.  Once, I enter the correct credentials, the browser is directed to "http://localhost/mythweb" but the page reports that it is not found.  I can successfully access mythweb by port forwarding from my router but no luck with ssh.  Any ideas as to whether I'm being stopped because of a port forwarding issue or mysql or is it even possible to ssh in and use credentials on mythweb?
Thanks!

---

### Post by AlecJ on 2013-03-22
What happens when you point your browser at 
http:/*192.168.1.?/*mythweb/
change the ip address to suit your mythbox's ip address

---

### Post by brandonros on 2013-03-22
Thanks for the reply, Alec.  When I point my browser there from within my home network, it takes me to mythweb successfully.  But when outside the network and using ssh, it times out and says page not found.

---

### Post by AlecJ on 2013-03-22
I have fixed IP address so when I'm outside the local network, so I point my phone browser to that.

Port 6547 and port 80,22 are forwarded in the router to my mythbox internal IP 192.168.1.?

so now* http:/** external-ip*/mythweb/    gets me in

and ssh *external ip *goes to my mythbox

You MUST set a password on Mythweb! else anybody can wondering for a play.

I think in Parkers Guide he tell you how to find your external IP, but that will change unless you pay for a fixed, or set up a DNS as he says.

---

### Post by brandonros on 2013-03-24
Yeah, for some reason, I am able to connect by port forwarding and using my DDNS account.  But just for my own accomplishment, I'm still hoping SSH would work but no luck.  Thanks for the help!

---

### Post by alien878 on 2013-03-25
I suspect what is happening is the login is redirecting you to port 80 because it doesn't know that you are actually using 6547 via ssh forwarding.

I suggest you try forwarding local port 80 to remote port 80.  This should solve the problem of port jumping.  I think mythweb sticks to port 80, so that should be enough.  Sometimes I have to forward several ports to get to a web page via ssh forwarding.

---

