---
title: "VNC not tunnelling over SSH correctly Ubuntu 9.1"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by Slates on 2010-02-07
I started another thread on this ([http://ubuntuforums.org/showthread.php?p=8787010#post8787010](http://ubuntuforums.org/showthread.php?p=8787010#post8787010)), but the topic was not specific to what I now know the problem to be. So Ive started a more appropriately titled thread.

In summary :

In my local network I SSH (via Putty) to my Ubuntu 9.1 server and the tunnel a VNC connection through to it. No problems at all. I forward port 5900 through SSH to do this. My local servers have port 5900 blocked, so I know it is tunnelling correctly without trying to access port 5900. I cannot VNC directly to port 5900, as I would expect. Everything works just as expected. 

When I SSH external to my router a I use a virtual server connection through port 22. This works just fine.

I then start a VNC session, in the exact same way as I do localy, tunnelled through port 5900. Specifically I tunnel port 5900 to my.router.public.ip port 5900. 

However when I start up VNC it times out. The reason is that my firewall blocks a request to my routers public IP address from port 5900 on the server running SSH as follows :

Feb 08 08:20:18 home.gateway:firewall:info: 525284.488 Blocked Prot=6, 192.168.1.3:57217 > 123.243.**.**:5900, S Seq=1821339514, Ack=0 -Default Defense 

Now the only difference here is the request is coming from externally to my router, specifying its public IP and a forwarded port of 22 for SSH. 

So my first thought is why would SSH be trying to access my public IP on port 5900 ? Wouldnt this imply its not working correctly ? Can anyone explain why its doing this ?

And as per the other thread and suggestions there, I have tried this both with the Ubuntu built in desktop and with x11vnc. Both give identical results. 

When I start x11vnc I tell it to listen on port 5900. This, as explained above, wokrs just fine in my internal network and does NOT put out any requests on port 5900.

Does anybody have any thoughts ?

---

### Post by krunge on 2010-02-07
> 
I then start a VNC session, in the exact same way as I do localy, tunnelled through port 5900. Specifically I tunnel port 5900 to my.router.public.ip port 5900.
I don't think you want to do this.  The SSH has already gotten inside your firewall so a port redirection to my.router.public.ip is not correct. By doing this you are making the port redir go "back out" through your router! I believe the firewall log you pasted shows the packet originated from inside your firewall.

I'm pretty sure you want to tunnel port 5900 to localhost:5900 This is the normal situation done all the time for VNC. (I assume x11vnc is running on the same machine you log into by SSH, if not ask for the additional details).  

So, e.g. on the unix cmdline, the ssh command would look something like this:
```
external-box>  ssh -L 5900:localhost:5900  username@my.router.public.ip
``` By "external-box> " I just mean the shell prompt on the machine external to your firewall.

If you are not using a cmdline to run ssh, e.g. Putty on windows, just replace "my.router.public.ip port 5900" with "localhost port 5900" (or whatever the format is; I don't use putty)

Using localhost:5900 will work inside your LAN too. You can test that way if you want to before making a connection from outside.

---

### Post by Slates on 2010-02-08
Thanks Krunge. You will not be surprised to know you are absolutely correct. I have hit my head on the wall as punishment for not realising this myself ! I think part of the problem was Id googled so many SSH tutorials some of them did have a setup not using localhost.

Of course the real answer is to fully understand what's going on, and then it'll be obvious ! Bit of a contradiction for a noob !

Many thanks....

---

### Post by Menthu_Rae on 2010-02-10
> **Slates said:**
> Thanks Krunge. You will not be surprised to know you are absolutely correct. I have hit my head on the wall as punishment for not realising this myself ! I think part of the problem was Id googled so many SSH tutorials some of them did have a setup not using localhost.

Of course the real answer is to fully understand what's going on, and then it'll be obvious ! Bit of a contradiction for a noob !

Many thanks....

Hrmm that's interesting - the commands by Krunge look very similar to:

[http://ubuntuforums.org/showpost.php?p=8780896&postcount=9](http://ubuntuforums.org/showpost.php?p=8780896&postcount=9)

;) :p

---

