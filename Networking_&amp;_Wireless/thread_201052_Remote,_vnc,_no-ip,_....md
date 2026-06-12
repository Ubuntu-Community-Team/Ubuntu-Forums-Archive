---
title: "Remote, vnc, no-ip, ..."
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by chloraldo on 2006-06-21
I can reach my other machine (192.168.1.43) with vncviewer when I'm in the home network. Problem is I want to access the PC when I'm not at home. And I don't have a fix IP.

Is there a way to access one particular home PC remotely? All have Ubuntu Dapper.

It doesn't have to be vncviewer. That's just the only thing I now. Would be nice if it was graphical though...

Thanks

---

### Post by digitalpardoe on 2006-06-21
You could forward the X Server to another computer, or the most common method for Linux is to login using SSH to give command line control of the computer.

To try and fix VNC;

Make sure that the firewall is configured correctly to allow connections to the port that you have the VNC server enabled on, usually 5800 and that the computer that the VNC is installed on can access itself to make sure the VNC server is correctly configured (but don't use full screen mode or you will stuck in a endless loop).

If you want to access the computer when you do not have a static IP address sign up for a [http://no-ip.com]("http://no-ip.com") account. Set up a host/redirect. Then on the computer do;

```

# sudo apt-get install no-ip
# sudo no-ip -c

```

Run through the configuration process and the no-ip servers will be updated on a regular basis with your computers external IP addess and you will have a simple non-changing domain name through which to access your computer.

---

### Post by disturbed1 on 2006-06-21
You would have to enable DMZ (or just port forwarding/triggering) for the PC you want exposed to the outside world. The setup is inside your routers configuration, usually under applications and gaming.

[www.dslreports.com]("http://www.dslreports.com") has a great networking forum, if you need help setting up your router, and you don't get an answer here, I'd check out that forum. I'm sure your question has been asked and answered before over there.

---

### Post by chloraldo on 2006-06-21
> **digitalpardoe]To try and fix VNC said:**
> http://no-ip.com[/URL] account. Set up a host/redirect. Then on the computer do;

I tried but without success...

My no-ip settings...
[[IMG]http://img73.imageshack.us/img73/3394/screenshot19qf.png[/IMG]](http://imageshack.us)

On my router I made a pinhole entry like this:
[[IMG]http://img63.imageshack.us/img63/1811/screenshot5po.png[/IMG]](http://imageshack.us)

Using [www.canyouseeme.org]("http://www.canyouseeme.org") with port 5800 gives me this error:
```

Error: I could not see your service on 83.xx.xxx.xxx on port (5800)
Reason: Connection refused
```

I tried using port 22 and i got a success message on [www.canyouseeme.org]("http://www.canyouseeme.org") but nothing else...

Using vncviewer mything.no-ip.org doesn't work, just hangs, no error message...

Any ideas what I'm doing wrong?

---

### Post by duffydack on 2006-06-22
this might help.
you dont need to redirect with no-ip, and port 5800 is the default for Vnc web/java based, 5900 (5901 for X :1 session and so on) for the "proper" vnc.. so open port 5900 (if using default) and 5901 if you use another X session as well)

connect to :0 session with vncviewer whateva.no-ip.org
connect to :1 session with vncviewer whateva.no-ip.org:1
what vnc do you use btw?  ive had a hard time getting one that will for one, work, and another, perform as well as the windows vnc4
ive ended up with x11vnc as i cant get the others to let me control the first (:0) session (im not into runnin a terminal server )

---

### Post by chloraldo on 2006-06-22
[QUOTE=duffydack]this might help.
you dont need to redirect with no-ip, and port 5800 is the default for Vnc web/java based, 5900 (5901 for X :1 session and so on) for the "proper" vnc.. so open port 5900 (if using default) and 5901 if you use another X session as well)[/QUOTE]

What do you mean I don't have to redirect with no-ip? How would I connect to my home IP if it's dynamic?

> connect to :0 session with vncviewer whateva.no-ip.org
connect to :1 session with vncviewer whateva.no-ip.org:1

I don't understand the above... Could you give some more info what o do where?

> what vnc do you use btw?  ive had a hard time getting one that will for one, work, and another, perform as well as the windows vnc4
ive ended up with x11vnc as i cant get the others to let me control the first (:0) session (im not into runnin a terminal server )

I tried tightVNC, vncviewer, xvnc4viewer, ... all with the same results: In my home network they worked as expected.

---

### Post by duffydack on 2006-06-22
you dont setup port redirects with no-ip, no-ip is just a dynamic ip to static domain name service.. the no-ip service you install updates the servers with your ip address so it always points to yourname.no-ip.org (whatever youve chosen)
you port forward 5800 or 5900 in your routers config  and point to the internal lan address of the machine you run vnc on..
leave the no-ip settings alone (dns host type - dns host (A) )
and ip address blank, it will update that field when the program sends an update of your ip address.
also, if ya goin to connect to vnc server on 5800 using the vncviewer program and not a web based viewer then you need to add :5800 to your connection details.   you.no-ip.org:5800

---

### Post by chloraldo on 2006-06-22
[QUOTE=duffydack]you dont setup port redirects with no-ip, no-ip is just a dynamic ip to static domain name service.. the no-ip service you install updates the servers with your ip address so it always points to yourname.no-ip.org (whatever youve chosen)
you port forward 5800 or 5900 in your routers config  and point to the internal lan address of the machine you run vnc on..
leave the no-ip settings alone (dns host type - dns host (A) )
and ip address blank, it will update that field when the program sends an update of your ip address.
also, if ya goin to connect to vnc server on 5800 using the vncviewer program and not a web based viewer then you need to add :5800 to your connection details.   you.no-ip.org:5800[/QUOTE]
Well, I think my problem starts before I even get to no-ip...

If I use the following code (in my home network) then it works:
```
vncviewer 192.168.1.43
```

Why doesn't this work?
```
vncviewer 85.0.xxx.xx:5900
```

---

### Post by duffydack on 2006-06-22
what port is your vnc server running on?  defaults are 5800 for web browser based and 5900 for standard vnc server....

do you have firewall settings in router? you may need to open there too..

---

### Post by chloraldo on 2006-06-22
[QUOTE=duffydack]what port is your vnc server running on?  defaults are 5800 for web browser based and 5900 for standard vnc server....[/QUOTE]
I don't know. How can I find that out? I just enabled the "Remote Desktop" with "System > Preferences..."

> do you have firewall settings in router? you may need to open there too..

I'm not sure, didn't find anything. I have a netopia cayman 3351. In the menu I can have stuff like "Network configuration (IP static Routes, ARP)", NAT (pinholes, default server)...

BTW, I have a wireless access point between the PCs and the router. But that shouldn't make any trouble...

---

### Post by decoyoct on 2006-06-22
[QUOTE=chloraldo]Why doesn't this work?
```
vncviewer 85.0.xxx.xx:5900
```[/QUOTE]

That tells vncviewer to use display 5900, not port 5900. I don't have access to my Ubuntu machine now so I can't test it out, but try using "::" instead of ":".

---

### Post by chloraldo on 2006-06-22
[QUOTE=decoyoct]That tells vncviewer to use display 5900, not port 5900. I don't have access to my Ubuntu machine now so I can't test it out, but try using "::" instead of ":".[/QUOTE]
I tried that now and I got the message "Connection timed out" after some minutes...

---

### Post by duffydack on 2006-06-22
[QUOTE=decoyoct]That tells vncviewer to use display 5900, not port 5900. I don't have access to my Ubuntu machine now so I can't test it out, but try using "::" instead of ":".[/QUOTE]

worked with mine, i must be using some other version.

try installin x11vnc, works for me.

---

