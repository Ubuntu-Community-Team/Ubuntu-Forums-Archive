---
title: "Reverse Proxy setup shellinabox"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by amlwwalker on 2013-05-20
Hi I haven't been using Linux all that long comparatively, but I have been quite full on with it since I have been using it.
I have put this here because I have followed alot of online material about doing this and it doesnt seem to work so I wondered whether something has changed in ubuntu (server) to stop this technique working like it is described.
I am trying to learn about apache reverse proxy setup so that I can access shellinabox from outside my home network.
I have got shellinabox working insecurely fine and I've been following this tutorial on securing it:
[http://www.linuxplained.com/increase-shellinabox-security/](http://www.linuxplained.com/increase-shellinabox-security/)

Ive got on fine until step 4 - reverse proxy. My proxy.conf file looks like:

```

<IfModule mod_proxy.c>


# If you want to use apache2 as a forward proxy, uncomment the
# 'ProxyRequests On' line and the <Proxy *> block below.
# WARNING: Be careful to restrict access inside the <Proxy *> block.
# Open proxy servers are dangerous both to your network and to the
# Internet at large.
#
# If you only want to use apache2 as a reverse proxy/gateway in
# front of some web application server, you DON'T need
# 'ProxyRequests On'.


#ProxyRequests On
#<Proxy *>
#        AddDefaultCharset off
#        Order deny,allow
#        Deny from all
#        #Allow from .example.com
#</Proxy>


Proxyrequests off
<Proxy *>
    AddDefaultCharset off
    Order Allow,Deny
#    Order Deny,Allow
    Allow from all
</Proxy>


<Location /shell>
Proxypass  http://localhost:PORT/
#ProxyPassReverse  http://localhost:PORT/
Allow from all
</Location>
#    ProxyPass /remote/  http://localhost:PORT/
#    ProxyPassReverse /remote/ http://localhost:PORT/


Redirect permanent /shell/ https://www.mysite.co.uk/shell/
# Enable/disable the handling of HTTP/1.1 "Via:" headers.
# ("Full" adds the server version; "Block" removes all outgoing Via: headers)
# Set to one of: Off | On | Full | Block
ProxyVia On

```
where PORT is the port I have moved shellinabox to.
restarted apache and have tried connecting to both [https://192.168.1](https://192.168.1).[server]/shell/ and [https://192.168.1](https://192.168.1).[server]/
to no avail.

I have tried following a lot of online tutorials about setting up reverse proxies but I cant find one that is correct. Some mention httpd.conf - which didnt exist before I created it - but that didnt work either.

Any help would be greatly appreciated


EDIT: Maybe Im editing the wrong file and should be doing what this says:?
[http://juhap.iki.fi/webdev/apache-reverse-proxy-on-ubuntu/](http://juhap.iki.fi/webdev/apache-reverse-proxy-on-ubuntu/)

---

