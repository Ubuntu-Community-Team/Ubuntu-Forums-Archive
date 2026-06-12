---
title: "SSH/VPN HTTP + IM tunneling?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by laeg_ on 2009-07-05
I'm just wondering whether SSH or VPN tunneling would be best for HTTP and IM traffic? Basically I'd like to tunnel this data from a windows machine back to my ubuntu system at home.

Are there any guides on how to do so?

Thanks.

---

### Post by computer13137 on 2009-07-05
Setup a SOCKS5 proxy with your SSH tunnel.  This is relatively easy to do, and most web browsers and IM clients support using a SOCKS5 proxy now.   I use this option to tunnel my Internet traffic all the time.

To setup a SOCKS5 proxy, all you need to do is as follows:

1) In the command line, open up an SSH session to your server.  Setup a Dynamic (-D) tunnel to any port number of your choice.
```
ssh -D 127.0.0.1:1337 username@server.com
```

2) In your application, edit your proxy settings.  The proxy will be SOCKS5, there is no authentication, and it is running on 127.0.0.1 port 1337 (or whatever port you choose).

Most applications support this, and all the data goes through the SSH tunnel.

Cheers,
Kirk

---

### Post by laeg_ on 2009-07-06
From the windows box I replace the 127.0.0.1 with my actual ubuntu IP but do I do the same when I enter the command on the ubuntu box?

Also, shouldn't I setup authentication and can I go over port 80 because it's most likely open?

Sorry, I won't be at the windows box until tomorrow to test this stuff for myself...

---

### Post by computer13137 on 2009-07-06
> **laeg_ said:**
> From the windows box I replace the 127.0.0.1 with my actual ubuntu IP but do I do the same when I enter the command on the ubuntu box?
No matter what machine you're setting up the tunnel on, you are ALWAYS going to be tunneling to 127.0.0.1.  Don't ask why, it's not important. lol.  

OK so here's why.  Your SSH client is setting up a SOCKS5 server listening on that port.  Your computer doesn't have the Ubuntu IP address assigned to it, so it can't listen on that address.  Just set the tunnel to 127.0.0.1.

> **laeg_ said:**
> Also, shouldn't I setup authentication and can I go over port 80 because it's most likely open?
I'm not sure what you mean by that.  I'm assuming when you login via SSH, there is already authentication to login.  If you are running your SOCKS5 proxy on 127.0.0.1, it can only be accessed from the local machine.  Now, if you set it to the machine's LAN IP or something, it would be accessible from anywhere in the network.

I don't like to use port 80 for a SOCKS5, it doesn't make sense to me.  I'll reiterate this, the ONLY REASON you would not be able to use a port is if there is another server, like Apache or something, on your local computer that you are SSH'ing from, that is running on that port.  Otherwise, any valid open TCP port is fine. :)  I guess 80 is OK, but I wouldn't.  lol.  The "standard" port for a proxy is 8080.

> **laeg_ said:**
>  Sorry, I won't be at the windows box until tomorrow to test this stuff for myself...
Don't worry about it, lol.  I'm subscribed to this thread, so whenever you decide to reply next, I'll receive it.

Cheers,
Kirk

---

### Post by laeg_ on 2009-07-06
> **computer13137 said:**
> I'm not sure what you mean by that.  I'm assuming when you login via SSH, there is already authentication to login.  If you are running your SOCKS5 proxy on 127.0.0.1, it can only be accessed from the local machine.  Now, if you set it to the machine's LAN IP or something, it would be accessible from anywhere in the network.Kirk

I've never tried logging into my machine by SSH :) This is the level of my technical understanding of ubuntu!

I don't have a network, I just want to be able to tunnel http and IM traffic from a remove windows machine in another part of the city through my home ubuntu box over the internet? 

Also, I read online OpenVPN is better for this than SSH, is this not the case?

---

### Post by computer13137 on 2009-07-06
> **laeg_ said:**
> I've never tried logging into my machine by SSH :) This is the level of my technical understanding of ubuntu!
Oh, my bad!  To use SSH on your Ubuntu machine, you first need to install the SSH server.  Then, the SSH server will be available on port 22 on your Ubuntu box.  If you're behind a router firewall, you will need to forward port 22 TCP to the Ubuntu box.  Regardless of what port you define for the forward, port 22 is the port that SSH always uses.

> **laeg_ said:**
>  I don't have a network, I just want to be able to tunnel http and IM traffic from a remove windows machine in another part of the city through my home ubuntu box over the internet?
Yeah, SSH can definitely do that. :)

> **laeg_ said:**
> Also, I read online OpenVPN is better for this than SSH, is this not the case?
I don't know, never used OpenVPN.  I've always used SSH for this and been perfectly satisfied, but maybe someone here knows?

Cheers,
Kirk

---

### Post by laeg_ on 2009-07-08
Okay, I've installed ssh and openssh-server via synaptic and I was told on #ubuntu that doing so will open port 22.

I have no physical firewall or router, instead a direct connection to the internet via my ISP.

I've entered the following:

ssh -D 127.0.0.1 [email]laeg@my.internet.ip[/email]

but it returns:

Bad dynamic port '127.0.0.1'

---

### Post by laeg_ on 2009-07-08
```
laeg@skyrocket:~$ ssh 127.0.0.1 [email]laeg@xx.xxx.xx.xxx[/email]
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is <left this hex out in case i'm not supposed to share it>
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
Write failed: Broken pipe

laeg@skyrocket:~$ ssh [email]laeg@my.internet.ip[/email]
The authenticity of host 'my.internet.ip (my.internet.ip)' can't be established.
RSA key fingerprint is <left this hex out in case i'm not supposed to share it>.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'my.internet.ip' (RSA) to the list of known hosts.
[email]laeg@my.internet.ip[/email]'s password: 
Linux skyrocket 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

laeg@skyrocket:~$
```

Is this good so far? Is there anything else I need to do ubuntu side to allow http/im tunneling and what do I need to do windows side?

---

### Post by computer13137 on 2009-07-08
> **laeg_ said:**
> ssh -D 127.0.0.1 [EMAIL="laeg@my.internet.ip"]laeg@my.internet.ip[/EMAIL]

but it returns:

Bad dynamic port '127.0.0.1'

Yeah, you have to assign a port for the SOCKS5 to run on.  Then, set all other programs to use this port.

So try like...
ssh -D 127.0.0.1:8080 [email]laeg@my.internet.ip[/email]

-Kirk

---

### Post by laeg_ on 2009-07-08
> **computer13137 said:**
> Yeah, you have to assign a port for the SOCKS5 to run on.  Then, set all other programs to use this port.

So try like...
ssh -D 127.0.0.1:8080 [email]laeg@my.internet.ip[/email]

-Kirk

Do I need to remove what I entered already or will the above just overwrite it?

---

### Post by laeg_ on 2009-07-08
Also, what about adding -C?

---

### Post by laeg_ on 2009-07-10
Have it sorted.

Only ssh and ssh-server needs to be installed for the tunnel to work.

No commands need to be entered.

All I did was ssh to it with PuTTY on port 22 after configuring the tunnel to be dynamic on port 5555.

I then pointed Firefox at the proxy which was 127.0.0.1

---

### Post by televisi on 2009-07-15
Hi All,
I've **been able to do VNC/TightVNC** tunneling from work through ubuntu server box at home. 
As well as **http tunneling using _webmin_** installed in the Ubuntu server at home too.

But when it comes to tunneling using normal Dynamic port / socket 5 combination (as explained in the following [_[COLOR="Blue"]site[/COLOR]_]("http://www.laboit.net/2009/05/15/implement-a-http-tunnel-on-a-linux-server/")), my [COLOR="Red"]work browser unable to display any site[/COLOR].

_Current configurations:_
- Ubuntu server (at home) with local ip address = 192.168.0.2; internet ip = w.x.y.z
- Webmin installed @ ubuntu server with port 10000
- SSH server listening on port 443
- to connect to internet in office, we need to connect to office proxy = a.b.c.d

_These are working http tunneling configurations using Webmin & SSH (using Putty):_
- From office computer, SSH to Ubuntu server using office proxy a.b.c.d and configure the Putty Tunnel configuration:
[LIST]
[*]Local tunneling
[*]Source port = 10000
[*]Destination = 192.168.0.2:10000
[/LIST]
- Set my office browser to "No Proxy"
- go to webmin site ==> [https://127.0.0.1:10000/](https://127.0.0.1:10000/)
- go to Http tunnel 'module' and load any site from there
[U]
Downside of using above steps:[/U]
- All links I opened will have "https://127.0.0.1:80/tunnel/link.cgi/" prefix
- I won't be able to open all my favorite sites, because of above issue (need to add prefix)
- Webmin gives timeout, and need to relogin every now and then

_Now, when I use the dynamic port & SOCKS5 setting:_
- From office computer, SSH to Ubuntu server using office proxy a.b.c.d and configure the Putty Tunnel configuration:
[LIST]
[*]Dynamic tunneling
[*]Source port = 9999
[/LIST]
- Set my office browser SOCKS host to "127.0.0.1:9999"
- Browse any site: BLANK / "Unable to show site" error

Do you think my company block Dynamic HTTP tunneling?, can they do that although the fact I've been able to do VNC tunneling and webmin tunneling?

Thanks

---

