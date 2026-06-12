---
title: "Iptables forwarding question"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by levicivita on 2010-11-27
Hey fellow Ubuntu-ers,

1) THE SETUP: I have a home set-up with 3 Ubuntu computers, including an HTPC which is always on, plugged into a Verizon FIOS router.  I also have a web based cam (TrendNet TV IP422W).  The cam has an ethernet jack so it plugs in directly to the router.  It has a simple firmware that allows users to log in via HTTP.  It is also managed via HTTP.  

2) THE PROBLEM: the cam does not keep logs.  So I never know who is logged in at any one point.  It's not a big deal, but it is annoying.  I want to fix that.  The router does not keep logs either.  I was told I can get a linux based router to replace (or plug in) to the default FIOS router, but I am looking for something simpler and cheaper.

3) THE FAILED SOLUTION: my idea was to set up the Ubuntu HTPC to always forward a given port to the webcam via the LAN.  I tried to follow the instruction from [http://www.hackorama.com/network/portfwd.shtml](http://www.hackorama.com/network/portfwd.shtml) as best I could, see below.  6666 is the port that the cam is listening to (the router is set to forward that port to the cam's LAN IP 192.168.1.30).  5555 is the port that I am trying to forward through the HTPC (ubuntu.local or 192.168.1.130 below, and the router is set to forward any 5555 TCP packets to the HTPC at 192.168.1.130).  The iptables commands below where run on the HTPC.

```

$ sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       tcp  --  anywhere             ubuntu.local     tcp dpt:5555 to:192.168.1.30:6666 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             TV-IP422W.local 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

```

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             TV-IP422W.local tcp dpt:6666

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

To be clear, here's how the HTPC networking is set up:

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:2a:11:13:a4:a4  
          inet addr:192.168.1.130  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6325194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4549784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6117114269 (6.1 GB)  TX bytes:371418459 (371.4 MB)
          Interrupt:32 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:494412 (494.4 KB)  TX bytes:494412 (494.4 KB)

```

```

$ ip route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.130 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  metric 100 

```

However when I use a remote computer to log in to port 5555 it doesn't work - nothing happens to be exact.  Port 6666 is still very much up and running as usual.  I am not a networking expert by any means.

Any ideas?  I have spent countless hours on this... 

THANKS!

---

### Post by fwre01 on 2010-11-28
Hi levicivita. 

Is this connection failing when initiated from inside or outside the LAN?

If traffic is initiated inside your LAN the connection will fail, because the host initiating the connection will expect to see a return packet from the HTPC, but it will actually receive a return packet from the camera. 

The way to do setup this connection correctly would be to Source NAT the address to the HTPC.

You mentioned you are already port forwarding 6666 to the camera, and 5555 to the HTPC. Most routers can do the DPORT translation as well as the forwarding. Perhaps using the HTPC is not necessary? 

Is this connection to access the logs on the camera? Does the camera not have the ability to output the logs to a host on the network?

---

### Post by SeijiSensei on 2010-11-28
I'll toss out another option.  You may decide it's beyond your current level of networking skills, but here it is:

Run the Apache web server on the Ubuntu box in so-called "[reverse proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html")" mode.  Forward incoming requests for the camera to Apache and have it proxy them to the camera.  You can add "[basic]("http://httpd.apache.org/docs/2.2/mod/mod_auth_basic.html")" authentication to the configuration so that every person would need to log in with a username and password to access the proxy and use the camera.  Every request will be logged by Apache with the usernames included.

---

### Post by levicivita on 2010-11-28
Hey fwre01, thanks for your detailed reply.

Q: Is this connection failing when initiated from inside or outside the LAN?
A: After setting up the HTPC as described in the original post, I ssh'd into a remote computer (located in a different city, over internet), and then attempted to telnet as well as use firefox to connect to my home IP on both the 5555 and 6666 port.  The 6666 connection (direct to webcam) worked.  The 5555 port timed out - nothing happened.  I had read about the NAT forwarding not working locally which is why I tested it this way.

Q: The way to do setup this connection correctly would be to Source NAT the address to the HTPC.
A: I just semi-blindly copied the iptables set up from the link provided in my original post.  My understanding of iptables is minimal.  Can you help explain what you mean, ideally include the iptables comamnd(s) required to set it up?  Thanks!!

Q: You mentioned you are already port forwarding 6666 to the camera, and 5555 to the HTPC. Most routers can do the DPORT translation as well as the forwarding. Perhaps using the HTPC is not necessary?
A: Yes, the router can translate the port if needed.  However that is not the issue (I can easily instruct the webcam to listen on an arbitrary port as well).  The reason I chose a separate port for the test is to explicitly test the two connection paths (router(6666)->webcam(6666) or router(5555)->HTPC(5555)->webcam(6666)).

Q: Is this connection to access the logs on the camera? Does the camera not have the ability to output the logs to a host on the network?
A: A most natural question, and my first instinct.  However, according to the TrendNet TV IP422W user manual, there is no explicit user access and activity logging functionality in their relatively simple firmware.  I can send you the link to the documentation if you'd like.  It's a great camera - but this is one annoying oversight.

---

### Post by levicivita on 2010-11-28
Hey SeijiSensei, 

That sounds like a solid option.  I am trying this now.  I will report back!

---

### Post by levicivita on 2010-11-29
SeijiSensei,

I spent another 4h trying to implement your solution.  It kind of works!  I am now redirecting all traffic through my apache2 reverse proxy on the HTPC!!  I set LogLevel debug and wrote some silly scripts (sed and grep) to show some stats on the currently logged in users.

Here are the issues I'm having:

1) If I try to set AuthType to Digest, AuthDigestFile is not a recognized option.
```

Invalid command 'AuthDigestFile', perhaps misspelled or defined by a module not included in the server configuration

```

From googling this, it appears it has been replaced by the usual AuthUserFile.  However when I set AuthType to Digest and I use AuthUserFile pointing at the digest password file generated with htdigest, none of the passwords actually work: "authentication failure for "/": Password Mismatch".  I of course used the same AuthName in proxy.conf as when running htdigest.  I may just upgrade to SSL based authentication if I can get myself to spend yet more time on this.

2) I don't have a good server monitoring solution.  Ideally I'd like to see who is logged in at any one time, and upon request, a history of logins (i.e. 'user XYZ was logged in from 1PM to 3:24PM today').  

I found out about mod_status, and I turned it on as a test.  It sort of works, but I wonder if there is something better.

3) Also I wonder if I have opened up any security holes, e.g. left open a forward proxy, etc.  Here are the main config files:

```

$ cat /etc/apache2/mods-enabled/status.conf  | grep -iv "#" | grep -iv "^$"
<IfModule mod_status.c>
<Location /server-status>
    SetHandler server-status
    Order deny,allow
    Deny from all
    Allow from localhost ip6-localhost 192.168.1.130 192.168.1.2 192.168.1.123 192.168.1.3
</Location>
</IfModule>

```

```

$ cat /etc/apache2/mods-enabled/proxy.conf  | grep -iv "#"
<IfModule mod_proxy.c>
        ProxyRequests Off
        <Proxy *>
                AddDefaultCharset off
                Order allow,deny
                Allow from all
		AuthType Basic
		AuthName "webcam"
		AuthDigestProvider file
		AuthUserFile /usr/local/apache2/passwords
		AllowOverride none
		Require valid-user
        </Proxy>
	ProxyPass /tv/ http://192.168.1.30:6666/
	ProxyPassReverse /tv/ http://192.168.1.30:6666/
        ProxyVia On
</IfModule>

```

```

$ cat /etc/apache2/httpd.conf  | grep -iv "#" | grep -iv "^$"
ExtendedStatus On

```

```

$ ls /etc/apache2/mods-enabled/
alias.conf            authz_host.load  deflate.conf  negotiation.conf  setenvif.conf
alias.load            authz_user.load  deflate.load  negotiation.load  setenvif.load
auth_basic.load       autoindex.conf   dir.conf      proxy.conf        ssl.conf
auth_digest.load      autoindex.load   dir.load      proxy_http.load   ssl.load
authn_file.load       cgid.conf        env.load      proxy.load        status.conf
authz_default.load    cgid.load        mime.conf     reqtimeout.conf   status.load
authz_groupfile.load  cgi.load         mime.load     reqtimeout.load

```

I tried to do as much work as I could on my own so that I would not harass you with newbie questions.  At this point I've reached the limits of my networking knowledge (in fact I've gone far beyond them :).

---

### Post by SeijiSensei on 2010-11-29
> **levicivita said:**
> SeijiSensei,

I spent another 4h trying to implement your solution.  It kind of works!

Kind of glad to hear that, I guess.  I assume you can see the camera via the proxy?

> If I try to set AuthType to Digest, AuthDigestFile is not a recognized option.

I've never used digest authentication.  In cases like this I'd use basic authentication with an htpasswd file.  On complete sites, I'm usually running PHP scripts with authentication against a database.

> 2) I don't have a good server monitoring solution.  Ideally I'd like to see who is logged in at any one time, and upon request, a history of logins (i.e. 'user XYZ was logged in from 1PM to 3:24PM today').

A clunky but simple solution is to use tail:

```
tail -f /var/log/apache2/access_log
```

and leave it running in a terminal window. (See edit below on apache-top.)

> 3) Also I wonder if I have opened up any security holes, e.g. left open a forward proxy, etc.

Well, you've specified the list of permitted hosts so that's a good start, though they're limited to the status page.  If you know what hosts are allowed to see the camera, you can add a similar access control block to the definition of the proxy.  You might also consider installing **nmap** from the repositories and scanning the Ubuntu box from a variety of both permitted and blocked machines.

> **levicivita said:**
> I tried to do as much work as I could on my own so that I would not harass you with newbie questions.  At this point I've reached the limits of my networking knowledge (in fact I've gone far beyond them :).

You've come far, my son.  Go and bask in the glory of your new-found net-fu.

You might want to take a look at [apache-top]("http://freshmeat.net/projects/apache-top/"), a monitoring tool for the apache server.  It's in the repositories.  It doesn't seem to report usernames, but since it's open-source and written in Python, you might be able to figure out how to add that feature yourself.

---

### Post by levicivita on 2010-11-29
> **SeijiSensei said:**
> Kind of glad to hear that, I guess.  I assume you can see the camera via the proxy?

Yes, sort of.  I can authenticate.  I am taken to the main camera web page (served through the proxy).  However the main Java applet does not load.  It just times out.  Out of desperation I looked at the HTML.  I think there's a link in there that is not properly recast to look as if it actually resides on the proxy (highlighted in red below).  Remember, 192.168.1.30 is the local cam address.  It really should not appear anywhere since the proxy should be pretending to be the server.

```

 <!--"CONVERTED_APPLET"-->
   <!-- HTML CONVERTER -->
   <object 
      classid = "clsid:CAFEEFAC-0015-0000-0012-ABCDEFFEDCBA"
      codebase = "http://java.sun.com/update/1.5.0/jinstall-1_5_0_12-windows-i586.cab#Version=5,0,120,4"
      WIDTH = "640" HEIGHT = "480" NAME = "ucx" >
   <PARAM NAME = CODE VALUE = "ultracam.class" >
   <PARAM NAME = ARCHIVE VALUE = "ultracam.jar" >
   <PARAM NAME = NAME VALUE = "ucx" >
   <param name = "type" value = "application/x-java-applet;jpi-version=1.5.0_12">
   <param name = "scriptable" value = "false">
   <PARAM NAME = "accountcode" VALUE="bW9tbXk6bWFtaWNh" />
**[COLOR="Red"]   <PARAM NAME = "codebase" VALUE="http://192.168.1.30:8888/users" />[/COLOR]**
   <PARAM NAME = "mode" VALUE="0" />
</object>
<!--"END_CONVERTED_APPLET"-->

```


> **SeijiSensei said:**
> 
I've never used digest authentication.  In cases like this I'd use basic authentication with an htpasswd file.  On complete sites, I'm usually running PHP scripts with authentication against a database.

Makes sense.  If I ever get this to work, I will try to use SSL with a self-signed certificate (it's for family only anyway).

> **SeijiSensei said:**
> A clunky but simple solution is to use tail.
Thanks, that makes sense.  I wrote a simple script that parses the logs and tells me who logged on when.  It works quite well (if the proxy itself works that is).

> **SeijiSensei said:**
> You've come far, my son.  Go and bask in the glory of your new-found net-fu.
Dude this is fun.  I'm really trying to get your idea to work.  I feel like I'm really close, like one more line of code and it will all work!

---

### Post by levicivita on 2010-11-30
> **levicivita said:**
> I think there's a link in there that is not properly recast to look as if it actually resides on the proxy (highlighted in red below).  Remember, 192.168.1.30 is the local cam address.  It really should not appear anywhere since the proxy should be pretending to be the server.

The documentation actually explicitly mentions this: 

*[INDENT]Only the HTTP response headers specifically mentioned above will be rewritten. Apache will not rewrite other response headers, nor will it rewrite URL references inside HTML pages. This means that if the proxied content contains absolute URL references, they will by-pass the proxy. A third-party module that will look inside the HTML and rewrite URL references is Nick Kew's mod_proxy_html.[/INDENT]*

I tried using mod_proxy_html, but it didn't seem to do anything.  So I ended up going with mod_substitute.  It's very simple and it did the job.  I recast [FONT="Courier New"]http://192.168.1.30:6666/users[/FONT] into [FONT="Courier New"]http://home.dyndns.org:6666/cam/users[/FONT].  Now the Java hourglass vanishes, but I still don't see the video feed.  error.log keeps saying: 

```

[Tue Nov 30 00:31:08 2010] [error] [client 12.34.56.78] File does not exist: /htdocs

```

I am stuck again.  :( 

This is so tantalizing!!  Every time I feel "I got it!" it slips again.

---

### Post by levicivita on 2010-11-30
I got it!!!  

Looking at other_vhosts_access.log, it is apparent that the request that was formed (presumably via the Java code that was referred in my fix above) assumed the camera is hosted at the root level:

```

$ tail -f other_vhosts_access.log
apacheserver:80 12.34.56.78 - - [30/Nov/2010:00:38:22 -0500] "GET /cgi/mjpg/mjpeg.cgi HTTP/1.1" 404 302 "-" "Mozilla/4.0 (Windows 2003 5.2) Java/1.6.0_22"

```

Unfortunately I have no idea how to substitute these strings since they likely live in the compiled Java bytecode (is there a way?).  As such I just pointed the reverse proxy map to the root level, and now it WORKS!!  Of course now I cannot use for example mod_status, since every request will get redirected to 192.168.1.30.  A small price to pay.  

```

ProxyPass / http://192.168.1.30:8888/
ProxyPassReverse / http://192.168.1.30:8888/

```

This was not easy, I confess.  But here we are.  Our journey is over.  Sort of.

---

### Post by SeijiSensei on 2010-11-30
> **levicivita said:**
> Unfortunately I have no idea how to substitute these strings since they likely live in the compiled Java bytecode (is there a way?).

I'm not sure I followed all of this.  You might look into rewriting URI's with mod_rewrite and see if that could help.

---

