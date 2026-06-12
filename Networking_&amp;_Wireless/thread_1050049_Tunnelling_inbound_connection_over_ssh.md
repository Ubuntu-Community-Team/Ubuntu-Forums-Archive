---
title: "Tunnelling inbound connection over ssh"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Dooley on 2009-01-25
Hey all,

Basically I have a setup as follows.
Xbox Media Centre is connected to my laptop via an ethernet cable and the laptop is connected to the wifi. 
Xbmc is connected to the internet just fine, however I'd like to be able to tunnel xbmc connections over an ssh socks proxy running on the laptop, say on port 7070.
Is this possible and if so any chance of a link to a tutorial?

Thanks!
Dooley

---

### Post by Dooley on 2009-01-26
Can anyone help? I assume the solution would involve tunnel the inbound connection to a socks proxy but I'm not sure how, google has turned up very little.

Thank,
Dooley

---

### Post by kevdog on 2009-01-26
Something like this?:[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

### Post by Dooley on 2009-01-26
Sort of kevdog. The ssh part is fine, but as the thread shows, Firefox has socks 5 support in-built. 
What I want is an inbound connection to be tunneled over this SOCKS 5 proxy. I'm not sure if this is implicitly supported.
I do know there is an application called tsocks that allows non-socks applications to implement SOCKS proxies, so say if you used opera you can just run "tsocks opera" and it will run via socks just fine. 
A solution like this might exist, I'm just not sure how to go about it.

Thanks for the reply!

---

### Post by kevdog on 2009-01-26
I guess you are asking for an inbound SOCKS5 proxy rather than an outbound SOCKS5 proxy?  I thought ssh was bidirectional.  Maybe I just don't understand SOCKS5 well enough, but lets say your client uses a SOCKS5 proxy over ssh with firefox, the communication has to be bidirectional!  I guess I'm still not clear on what you want to do.

---

### Post by Dooley on 2009-01-26
The setup should "hopefully" look like this.

Xbox ----(via ethernet)------>laptop-----(via wifi)------->internet.
                              (Port 7070 on laptop has SOCK5 configured)

At the moment there is already a tunnel between the laptop and the internet on port 7070 via ssh. So I can already tunnel firefox and other applications on the laptop over the SOCKS 5 proxy ssh -D creates. 
However, I just don't know how to setup an inbound connection(from the xbox to tunnel over this port). As it stands the xbox can use the internet normally.
So if I could create a "rule" that says all inbound traffic from the xbox's ip address should be routed over port 7070, that would solve all my problems. I'm just wondering if a iptables/tsocks setup or any other possible solution could be done.

---

### Post by Dooley on 2009-01-26
Actually XBMC has http proxy support, if anyone knows of a way to tunnel a http_proxy over a socks proxy, that too would be awesome. :D I actually know of a tool called corkscrew that will do the opposite, ie socks proxy over http.

---

### Post by kevdog on 2009-01-26
Just to confirm before I go on a wild goose chase -- you kind of want a "double jump" with the ssh connection received from one connection to be forwarded to another ssh connection?

---

### Post by Dooley on 2009-01-26
The laptop would take in the connection from the xbox then tunnel instead of doing a straight connection to the internet, it would tunnel the connection over the socks proxy.

---

### Post by kevdog on 2009-01-26
Do you have ssh capabilities on the Xbox -- or do you simply want http traffic (port 80) forwarded.  I guess there are a couple of ways to accomplish this
#1. Use ssh forward and reverse tunneling throughout.  
#2. Configure firewall port forwarding rules for something like internet connection sharing (which I assume you already have ICS setup)?

---

### Post by Dooley on 2009-01-26
The xbox doesn't have ssh capabilites(that would be handy). So it's a straight port 80 request to the laptop.
Yes I have ICS setup, this is done using firestarter.
What exactly is ssh reverse tunnelling? I may not be entirely clear, if I'm not sshing into the xbox how would I set this up?

---

### Post by kevdog on 2009-01-26
If you don't have an ssh client on the Xbox then I guess ssh tunneling wouldn't help, and re-reading your original post it seems like some of the applications you want to run over port 80 don't have built in socks5 capabilities, hence the link to the other program you listed.  Hmm, that's a tough situation.  Even if the ipchains were setup to forward port 80 to the outbound socks proxy, your programs would need either intrinsic or extrinsic socks capabilities.

---

### Post by Dooley on 2009-01-26
When I get home, I'll try using tsocks to setup a rule that forwards all traffic to a specific ip through the proxy. I'll post the results if I have any luck.

---

### Post by kevdog on 2009-01-26
Let me know what you find -- I can even try on my end later however it probably wont be until tomorrow.

---

### Post by Dooley on 2009-01-27
Didn't get a chance to do it yesterday but I will today.

---

