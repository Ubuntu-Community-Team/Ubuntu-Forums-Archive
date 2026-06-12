---
title: "automatic remote logins with vnc - is it possible?"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by jcmm33 on 2009-02-20
We have followed the instructions on this site to successfully setup ubuntu 8.04 to allow users using vnc on pcs to connect to a ubuntu machine and (on differing ports) to then be presented with the login greeter.

However our requirement is that we dont want the user to be presented with a logon screen but rather the user to be automatically logged on and the relevant application started for them.  It isn't important to us who the user is as such.  

So the question(s) is /are :

1.  It is possible for the remote login to happen automatically - i.e. user fires up vnc on their pc, specifies the address and they are automatically connected to a desktop on the ubuntu box without having to login
2.  If the user has to be authenticated in some way, is it possible for this to happen with the vnc connection supplying the username / password.
3.  we are currently using different ports for each user connection (e.g. 5900,5901,5902...), it is possible for multiple users to be able to connect via the same port and new instances for the connecting user are automatically created?
4.  We are currently logging onto the desktop, is it possible that when the user logs on, they ONLY get a single GUI application that is shown across vnc - i.e. like a kiosk application?  Please note that users will be connecting from pcs running vnc, this isnt a terminal server environment (but if things from it are required to do this then please le us know)

Thanks in advance


Jamie

---

