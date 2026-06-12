---
title: "SSH Questions"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by dvdhaar on 2009-07-26
Hope this is better off being here then in the AB section.

I've discovered the amazing SSH protocol and have been using it ever since. I just got a couple of questions. I've been reading up on the SSH manual and various articles on the internet but still have some questions;

1. I've messed around with setting up a tunnel and using it as a proxy in Firefox to surf the web securely when I'm at work etc. I've followed a youtube tutorial on this, which told me to use port 7070 for the 'Source Port' and set Destination to Dynamic in Putty. I understand 7070 is just a random port which is not being used at the moment, but why Dynamic? I don't understand the logic behind it, i'd love to understand why it works. Basicly all trafic on port 80 will be forwarded on port 7070 on the SSH server right?

2. Is it secure enough to use the default port 22 for SSHing? Or is random port more secure?

3. On my server, besides having an OpenSSH server running, I've got a WinXP VM which I can connect to remotely on my internal network. Is there a way to tunnel the trafic for remote desktop (port 3389 I believe)? So I can create a tunnel when I'm somewhere else and connect to the VM securely?

Thanks in advance

---

### Post by dlmarti on 2009-07-26
> **dvdhaar said:**
> Hope this is better off being here then in the AB section.

I've discovered the amazing SSH protocol and have been using it ever since. I just got a couple of questions. I've been reading up on the SSH manual and various articles on the internet but still have some questions;

1. I've messed around with setting up a tunnel and using it as a proxy in Firefox to surf the web securely when I'm at work etc. I've followed a youtube tutorial on this, which told me to use port 7070 for the 'Source Port' and set Destination to Dynamic in Putty. I understand 7070 is just a random port which is not being used at the moment, but why Dynamic? I don't understand the logic behind it, i'd love to understand why it works. Basicly all trafic on port 80 will be forwarded on port 7070 on the SSH server right?


I'd have to see the command syntax your using to answer the question.

> **dvdhaar said:**
> 
2. Is it secure enough to use the default port 22 for SSHing? Or is random port more secure?


I use the default port, its much easier for day to day work.  I would suggest running denyhosts (apt-get install denyhosts), it will lock down your ssh if someone tries to hack you.

> **dvdhaar said:**
> 
3. On my server, besides having an OpenSSH server running, I've got a WinXP VM which I can connect to remotely on my internal network. Is there a way to tunnel the trafic for remote desktop (port 3389 I believe)? So I can create a tunnel when I'm somewhere else and connect to the VM securely?

Thanks in advance

If it were me I would just tunnel the linux remote desktop, that should also export the VM guests (I think, never tried it).  Other than that, you could tunnel a host port to a guest port.

---

### Post by dvdhaar on 2009-07-26
Thanks for the reply :)

> **dlmarti said:**
> I'd have to see the command syntax your using to answer the question.


I'm using putty to setup the tunnel. Via this tutorial [http://www.youtube.com/watch?v=EUplDL4hSuc](http://www.youtube.com/watch?v=EUplDL4hSuc)

> **dlmarti said:**
> I use the default port, its much easier for day to day work.  I would suggest running denyhosts (apt-get install denyhosts), it will lock down your ssh if someone tries to hack you.


Thanks for the tip. I will read up on this :) I've had some issues with data strangely disappearing.. ([http://ubuntuforums.org/showthread.php?t=1188242](http://ubuntuforums.org/showthread.php?t=1188242)) So I changed the SSH port. I'm pretty much a noob still with all of this so I'm not sure!

> **dlmarti said:**
> If it were me I would just tunnel the linux remote desktop, that should also export the VM guests (I think, never tried it).  Other than that, you could tunnel a host port to a guest port.

You mean setup a VNC server on the host and than launch the VM remotely? Won't this be laggy? 
I'm still reading and learning about SSH but is it true that you can prevent opening ports in your router and instead forward the port through SSH?

---

### Post by dlmarti on 2009-07-26
> **dvdhaar said:**
> Thanks for the reply :)



I'm using putty to setup the tunnel. Via this tutorial [http://www.youtube.com/watch?v=EUplDL4hSuc](http://www.youtube.com/watch?v=EUplDL4hSuc)



Thanks for the tip. I will read up on this :) I've had some issues with data strangely disappearing.. ([http://ubuntuforums.org/showthread.php?t=1188242](http://ubuntuforums.org/showthread.php?t=1188242)) So I changed the SSH port. I'm pretty much a noob still with all of this so I'm not sure!



You mean setup a VNC server on the host and than launch the VM remotely? Won't this be laggy? 
I'm still reading and learning about SSH but is it true that you can prevent opening ports in your router and instead forward the port through SSH?

I'm not watching that video  :)

This will tell you if someone is getting in on your ssh connection:
"cat /var/log/auth.log | grep ssh"

---

### Post by dvdhaar on 2009-07-26
> **dlmarti said:**
> I'm not watching that video  :)

This will tell you if someone is getting in on your ssh connection:
"cat /var/log/auth.log | grep ssh"

Thanks :) Didn't know about that!

Well basicly in Putty I'm connecting to my server and under SSH > Tunnels I'm using 'Source Port' - 7070 and Destination is left blank and 'Dynamic' is selected. Now I connect and login. In Firefox Preferences, under Advanced > Network. Manual proxy is selected and for SOCKS Host I use '127.0.0.1' and its port is 7070. 

This works fine, but I just want to know the logic behind it :)

---

