---
title: "SSH tunnelling (PuTTy?)"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by J-E-N-O-V-A on 2009-03-28
How can I use SSH tunnelling to connect to my home computer when I'm at uni? Basically using it as a proxy so that I have unfiltered internet and don't have to go through the loathsome process of connecting through an organisation's proxy. (finding out my username, password etc and there may even be a quota at the uni I'm going to) =[

I had a friend at school that could do this without having to connect through the school proxy but he never told me how. 

Any ideas?

P.S Both my home computer and laptop (which is what I will use at uni) are running ubuntu 8.10

---

### Post by Hobgoblin on 2009-03-28
Assuming you can ssh out of Uni (you will need an open port) then you would install the ssh server and squid on your home machine and configure your router to pass the port you are to use on to the port which ssh is listening on.  You'll then need Squid on your home machine set up to accept connections from 127.0.1.1

Then when you ssh from uni you will use the -L option to forward a local port to the Squid port.
i.e: ssh *your_home_IP* -L 3128:localhost:3128

If not using the default port (if it is blocked, or to avoid random port scans finding it) then you will also need **-p *your-chosen-ssh-port***

---

### Post by joey on 2009-03-29
I use this dynamic ssh

See this post for details.

[http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

You can use gstm to make the starting of the tunnel a bit easier.

In firefox, foxyproxy or similar can be set to always use the tunnel.

Oh, and you probably want to run denyhosts on your home machine.

---

### Post by smon1 on 2010-01-14
Hi,

I am able to tunnel into my account in uni and able to view some internal only websites from home. That is fine.

My question is I have a streaming server on a dedicated machine in uni and it broadcasts a live video over rtsp port 554. I am able to access it why i am in there using rtsp://mypc.uni.com/mystream.sdp. Also I am able to access the streaming server's control panel while tunneling from home at [http://mypc.uni.com:1220/](http://mypc.uni.com:1220/) .

Can anyone tell me is there a way for me to adapt the info above to allow me to access the live stream through my videoLAN player at home?


Thank you

---

### Post by Lars Noodén on 2010-01-15
There are a number of guides about tunneling with PuTTy

[http://realprogrammers.com/how_to/set_up_an_ssh_tunnel_with_putty.html](http://realprogrammers.com/how_to/set_up_an_ssh_tunnel_with_putty.html)
[http://oldsite.precedence.co.uk/nc/putty.html](http://oldsite.precedence.co.uk/nc/putty.html)

As you can see in the diagrams, you can tunnel as many ports as needed over the connection.

---

