---
title: "VNC localhost refuses connection"
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by dakkerd on 2012-07-29
I try to setup a VNC with only localhost connections. This so I could tunnel it through SSH and securely control my server remotely. I can connect when accepting all connections (so not only localhost). That works like a charm.

I try to add however localhost by firing x11vnc with the following command:
```
x11vnc -forever -rfbport 5905 -usepw -localhost
```
The result is then:
> The VNC Desktop is:      localhost:5
PORt=5905

So I would presume it all works by using in my chickenof the vnc the following:
host: localhost:5
pass: the pass

OR
host: 127.0.0.1:5
pass: the pass

However, connecting it says 'Connection refused: connect()'. So for some reason it won't work. What did I do wrong?

---

### Post by dakkerd on 2012-07-30
[U][B]What DOES work
[/B][/U]So both computers are connected to the same router. One cable (the VNCserver), one wireless.
I got the local IP from the VNCserver through ifconfig and is something of the kind xxx.xxx.xxx.xx. Verifying this with the site 'What is my IP' I get the same IP, presuming the IP is the external one. 
I fire up the VNC directly from the VNCserver typing:
```
x11vnc -forever -rfbport xxxx -usepw
```
I connect using VNC (the previous IP, hence xxx.xxx.xxx.xx:5905)

**Works like a charm
[U][B]

What does NOT work
[/B][/U]So both computers are connected to the same router. One cable (the VNCserver), one wireless (the client).
fire up VNC using ```
x11vnc -forever -rfbport xxxx -localhost
```

I would think, for I am connected to the same network that the following ought to work
host: localhost:5905

Yet, I get 'connection refused'. Tunneling to another comp and then tunneling back to the vncserver and trying to connect does not work neither. 

[U][B]Pinging
[/B][/U]- pinging the xxx.xxx.xxx.xx does work (while not tunneled AND when tunneled), I do receive packages. 
- when tunneled and on the local machine I ```
ping name-vnc-server.local
```, I indeed receive packages. 
- when not tunneled and ping the vncserver using ```
ping name-vnc-server.local
```, I get that > ping: unknown host

Anyone can help me out here?

---

### Post by steeldriver on 2012-07-30
Adding the localhost flag to x11vnc doesn't set up the tunnel for you - it just instructs the server not to accept remote connections - you must then set up the tunnel yourself, e.g. on the client machine

```
ssh -L 5905:localhost:5905 -N xxx.xxx.xxx.xxx
```

or (if your login name is different on the remote machine)

```
ssh -l user -L 5905:localhost:5905 -N xxx.xxx.xxx.xxx
```

where xxx.xxx.xxx.xxx is the IP of the server.

**Then** you can connect using your VNC viewer on the client machine by putting localhost:5905 in the 'remote' host field.

Your 'name-vnc-server.local' name resolution is a separate issue - I would stick to IP addresses for now.

---

### Post by dakkerd on 2012-07-30
Thanks for the reply! Works just fine.

For me to understand, when I use ```
ssh -l user -L 5905:localhost:5905 -N xxx.xxx.xxx.xxx
``` do I bind the port of the ssh to the port of the x11vnc? Or what does one do using the command above?

---

### Post by steeldriver on 2012-07-30
The command is creating an ssh tunnel from port 5905 on remote machine xxx.xxx.xxx.xxx (-L 5900) to port 5905 on the local machine (localhost:5905) 

Remember 'localhost' isn't an alias for a particular machine. When you start x11vnc with '-localhost' it means only accept connections from the server's own IP xxx.xxx.xxx.xxx . Then when you start your VNC viewer on the client with 'localhost:5905' it is resolving to the client's IP yyy.yyy.yyy.yyy . The tunnel is what makes the data that x11vnc sends to xxx.xxx.xxx.xxx:5905 appear (to the VNC viewer) to be coming from yyy.yyy.yyy.yyy:5905 (most likely through the loopback interface i.e. as 127.0.0.1:5905).

Hope that helps

---

### Post by dakkerd on 2012-07-30
Thanks for the clarification. So here is where I'm at:

(I'm on the same network)

1. ssh on the remote server using the following (using a specific port for the ssh namely xxx1)
```
ssh -p 1xx1 user@mydomain.dyndns.org
```_*result: *_connected to remote server

2. start x11vnc server
x11vnc -forever -rfbport xxx5 -usepw -localhost
_*result: *_x11vnc server starts, all seems well

3. get the IP of server just to make sure, so in the ssh connection user@... type
ifconfig
_*result: *_xxx.xxx.xxx.xx

4. use the above to tunnel ssh
ssh -l user -L xxx5:localhost:1xx1 -N xxx.xxx.xxx.xx

5. connect using chicken of the vnc
localhost:5 and the appropriate pass
_*result:*_ connection refused. 

I 'worked' before, yet now it does not. So I must be doing something different and not understand what. Would it be because I am connected to the same network? Apologies for the newbie confusion...

---

### Post by steeldriver on 2012-07-30
If your x11vnc rbfport is xxx5 and you want to tunnel that to local port nnnn then I think you want

```
ssh -l user -L nnnn:localhost:xxx5 -N xxx.xxx.xxx.xx
```(honestly you are making this hard for yourself by using non-standard ports - I may have explained it the wrong way around in my previous post)

Then you probably need to tell the VNC client 

```
localhost:nnnn 
```since it likely won't understand the host:display format if you aren't using the default port numbering scheme (it's based on the formula local port = 5900+display I think)

---

### Post by dakkerd on 2012-07-31
Thanks for the insights. So I stopped using the funny port and set the VNC to the standard one. So VNC went:
```

x11vnc -forever -usepw -localhost
```This made the x11vnc listen to 5900, display 0


Then I tried the above, using 

```
&#65279;ssh -p xxx5 user@xxx.xxx.xxx.xx -L5900:localhost:5900 -N xxx.xxx.xxx.xx
```xxx.xxx.xxx.xx is the IP of the server, 5xx5 is the port of the ssh. It worked and I can get access. 



It did NOT work using
```
&#65279;ssh -p 5xx5 user@xxx.xxx.xxx.xx -L5xx5:localhost:5900 -N xxx.xxx.xxx.xx
``````
&#65279;ssh -p 5xx5 user@xxx.xxx.xxx.xx -L5900:localhost:5xx5 -N xxx.xxx.xxx.xx
```So the -L5900:localhost:5900 has nothing to do with my 5xx5 port I use to start the SSH. Thanks for the patience, and will go read why my current setup actually works.

---

### Post by steeldriver on 2012-07-31
wait... are you trying to set the ssh port to the same port as the VNC tunnel? I don't think that's going to work

ssh -p **5xx5** [EMAIL="daki@xxx.xxx.xxx.xx"]daki@xxx.xxx.xxx.xx[/EMAIL] -**L5xx5**:localhost:5900 -N xxx.xxx.xxx.xx

you should either keep ssh on the default port (22) or if you insist on security-by-obscurity then move it to a high number - outside the port range of regular services (e.g. 2xxx2)

---

### Post by dakkerd on 2012-07-31
> **steeldriver said:**
> security-by-obscurity  was indeed what I was trying to do. Sorry, thought that would have been obvious.

So to summarize:
1. I initially connect to the remote server through SSH on a specific port namely 5xxx5.
2. I then (after login on the remote server) start the X11VNC server using the following command ```
sudo x11vnc -localhost -usepw -auth /var/run/lightdm/root/:0
```.
3. I then use ```
ssh -p 5xx5 user@remote-server.org -L5900:localhost:5900 -N remote-server.org
```
4. start the VNC viewer using localhost and 5900

This works, but I understand that this is not good practice then. Why not and where am I wrong.

Later, I would like to write a small script executing the above so I don't have to retype it all each time I want to control the screen.

---

### Post by steeldriver on 2012-07-31
I'm not an expert but I don't see anything wrong with what you are doing - afaik you are tunneling the traffic securely as-is - changing the port numbers on the ends of the tunnel doesn't really make anything more secure because the only externally open port is the ssh port anyhow

To automate it (assuming you are using lightdm not gdm) you could use the 'start on login-session-start' signal as described here

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

DO keep your current x11vnc -localhost flag and ssh tunnel setup though

---

