---
title: "help with wireless file sharing server and router"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by catgrepuniq on 2012-08-09
I have a server running lighttpd with files on it that a lot of people use. 

Currently, they have to connect to a wireless router, which is not connected to the internet, and then type [http://192.168.0.2 ]("http://192.168.0.2--local")--the local ip address of the server--  in their browsers to connect to the server and download files. Technically, it is working well and is extreamly fast; however, it is also difficult and annoying for the users to type in the local ip address. I want to find a better solution.  

(wifi users) - > (wifi routher) -> (ubuntu  with lighttpd serving files) 

My goal is to make it so the users do not need to type in a local IP address. When they connect to the wireless router, they should automatically see the files, regardless of the URL of their browser's homepage. 

Does anyone know how to redirect everything to the server? 

I can plug the server into the Wide Area Network port on the router if needed.

---

### Post by bakegoodz on 2012-08-12
You need some type of Local DNS server on the network so they can access the server by name. There are many ways you can enable this. You can probably do it with the wireless router. I have a DD-WRT router and use Local DNS and static leases options, so I can access a computer just with "XBMC" instead of the IP address.
[IMG]http://i48.tinypic.com/sdfs44.png[/IMG]

---

