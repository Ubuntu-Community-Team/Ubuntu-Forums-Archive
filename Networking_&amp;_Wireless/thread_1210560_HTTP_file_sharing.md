---
title: "HTTP file sharing"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by fireaddict on 2009-07-11
Hi there,

The other day when i was browsing for useful linux one liner commands i seen something to do with a program that turned a folder into a http file sharer. Basically like running apache but just to be used temporarily. Anyway, i didnt catch the name of the utility and cant for the life of me find the site again, its become lost in my browsing history.

Does anyone have any idea what program i'm talking about?

edit: this was a command line util, i've seen a windows based one that apparently works on wine but its not really what i was after

---

### Post by The Cog on 2009-07-11
I have a feeling that Dolphin (the KDE file explorer) has such a command built in. But anyway, this is the script I use. I created a file called wwwserver - here are its contents:
```
#!/usr/bin/python
import SocketServer, SimpleHTTPServer, BaseHTTPServer, CGIHTTPServer, os

#------- Configuration ----------

wwwroot = "/home/cog/wwwroot"
server_address = ('', 8000)
cgi = True
multiThreaded = True

#--------------------------------

class ThreadingHttpServer(SocketServer.ThreadingMixIn, BaseHTTPServer.HTTPServer):
    pass

if multiThreaded:
    server_class=ThreadingHttpServer
    descr = "MultiThreaded "
else:
    server_class=BaseHTTPServer.HTTPServer
    descr = ""

if cgi:
    handler_class=CGIHTTPServer.CGIHTTPRequestHandler
    descr += "CGI "
else:
    handler_class=SimpleHTTPServer.SimpleHTTPRequestHandler
    descr += "HTTP "

os.chdir(wwwroot)
httpd = server_class(server_address, handler_class)

print descr + "Server listening on", server_address
print "-----------------------------------------------"
httpd.serve_forever()

```
I created a folder called wwwroot that I use as the root of the web server. If you leave cgi enabled, it will use scripts in wwwroot/cgi-bin.

---

### Post by fireaddict on 2009-07-11
That'll do nicely, thanks for being kind enough to share it.

---

