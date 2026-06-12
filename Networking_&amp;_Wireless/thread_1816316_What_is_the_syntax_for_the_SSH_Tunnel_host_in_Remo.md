---
title: "What is the syntax for the SSH Tunnel host in Remote Desktop Viewer?"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by bwallum on 2011-08-01
I have succeeded in using Remote Desktop Viewer to make a VNC connection to a remote WAN computer and it was quick enough to manipulate the remote computer in real time.

I found the host name by getting the remote target computer to put the following url into a browser - [http://www.showmyip.com/](http://www.showmyip.com/) - It returned the address for the router which I put into the Host: text entry box in the Remote Desktop Viewer window. 

E.g. for my computer at the time of submitting my enquiry the address was 'host81-129-54-226.range81-129.btcentralplus.com'

The remote router that I connected to needed to have the port 5900 forwarded to the remote target computer.

I now want to progress to running VNC through a SSH tunnel for additional security. In the Remote Desktop Viewer there is a configuration line 

'use host' <text box to enter host name> 'as a SSH tunnel'

What is the correct syntax to enter in the text box? It would help my  understanding if you used the example address above as a basis for a  response.


EDIT

Many unexpected connection attempts reported on my router, if that was you, thank you for the novel way in responding to the question and providing the syntax.

The 'bible' on syntax appears to be found here:- [http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh+1](http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh+1)

---

### Post by Herman on 2011-08-20
hello bwallum,
I am still experimenting with this myself, but I think I have found an answer.
I think the correct syntax for that field is something like:
```
joe@192.168.1.5
```for within a protected LAN, or over the internet if you have a ddns, 
```
joe@some.ddns.com
```and if it needs to be forwarded by a non-standard ssh port, try using a semicolon before your port number, like
```
joe@some.ddns.com:5432

```Where" '5432' is your alternative ssh port number forwarded from your router.
I accidentally discovered this after noticing a black text balloon containing that information after inadvertently leaving my mouse hovered over the field while I was searching the internet in the other computer for the answer, (and thus happened to find your question).

It seems to be working for me within my LAN. I now would now like a way to confirm the connection is definitely encrypted so I can progress to trying this out over the internet too.

---

### Post by Herman on 2011-08-20
> It would help my  understanding if you used the example address above as a basis for a  response.Okay, try <username>@<hostname>:<port-range>, like this,
```
bwallum@btcentralplus.com:81-129 
```Assuming btcentralplus.com will be linked to whatever your router's current IP address is now.
Otherwise, (if your ddns isn't working, then try,
```
bwallum@81-129-54-226:81-129
```and it should work if you still have that IP address.

---

