---
title: "VNC and Apache through firewall via proxy"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Paerez on 2009-01-30
Hey guys,

First off, I am not trying to tunnel vnc to my home computer. I cannot use an SSH tunnel. That said, here is my issue:

User: A person in an unknown environment, probably behind a firewall blocking everything but 80/443. Assume they are so dumb they can only browse the web and click around.

Server: My server that is running Apache and many instances of VNC on 5901-5910.

Apache is set up so that it embeds the VNC java applet so that a user can just view a page and get vnc access.

What I would like to do is set up some kind of proxy on port 80 of my server. Then I could use some apache virtualhosts to do something like this:

I have DNS for *.example.com

[www.example.com](www.example.com) => localhost:8080 (I'll put apache here)
vnc01.example.com => localhost:5901
vnc02.example.com => localhost:5902
...
vnc10.example.com => localhost:5910

I have tried using mod_apache but I'm having a bit of trouble.

Anyone know if squid could do this?

I've hacked into the Java applet so I replaced this:
```
sock = new Socket(host,port)
```

with this:

```
SocketAddress addr=new InetSocketAddress("http://proxy.collab.slsdev.net", 80);
Proxy proxy = new Proxy(Proxy.Type.HTTP, addr);
sock=new Socket(proxy);
InetSocketAddress final_addr=new InetSocketAddress(host, port);
sock.connect(final_addr);
```

But it gives me:
```
Error: Invalid Proxy
java.lang.IllegalArgumentException: Invalid Proxy
	at java.net.Socket.<init>(Socket.java:140)
	at RfbProto.<init>(RfbProto.java:171)
	at VncViewer.connectAndAuthenticate(VncViewer.java:323)
	at VncViewer.run(VncViewer.java:156)
	at java.lang.Thread.run(Thread.java:636)
```

Maybe Squid can help? Or another type of proxy?

Thanks for any help you can provide.

---

### Post by sedawk on 2009-01-30
There is a proxy module for apache, what I have used some time ago.
It works somehow like this, if [www.example.com](www.example.com) is your apache web server

[www.example.com/vnc01](www.example.com/vnc01) => localhost:5901
[www.example.com/vnc02](www.example.com/vnc02) => localhost:5902

(I also needed some other mod to edit replies on the fly to
 fix the links inside of html pages. Not sure you need it too).

You might think about doing this on the "ssl channel", not
the "http channel" (security).

---

### Post by Paerez on 2009-01-30
Thanks sedawk. I plan on moving it all to 443, just wanted to handle one problem at a time.

I have tried using mod_proxy, but I am having trouble. My VHosts look like this:

```
NameVirtualHost *:80

<VirtualHost *:80>
  ServerName proxy.collab.example.com

  ProxyRequests On

  <Proxy *>
    Order deny,allow
    Allow from all
  </Proxy>
  <directory "/var/www/html">
    Order deny,allow
    Deny from all
  </directory>

</VirtualHost>

<VirtualHost *:80>
    # Rails Server
    DocumentRoot /var/www/html/collaboration/public
    ServerName collab.example.com
    RailsEnv development
    RailsAllowModRewrite off
    <directory "/var/www/html/collaboration/public">
      Order allow,deny
      Allow from all
    </directory>
</VirtualHost>
```

I am using passenger to serve the rails app, and I am trying to run the proxy on proxy.collab.example.com. Then when I try to connect with java I get the errors in my first post.

Thanks.

---

