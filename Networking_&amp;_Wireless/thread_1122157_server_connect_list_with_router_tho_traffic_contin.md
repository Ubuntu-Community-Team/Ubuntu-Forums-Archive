---
title: "server connect list with router tho traffic continues to pass thru"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by linuxnovicefan on 2009-04-10
I need help understand what's happening with my server and router. I operate a server behind a home router to which several other computers are attached. 

The router logs show occasionaly that various traffic overflows or network attacks cause the router to reset. 

But when I check to see what computers remained attached to the router - then I see only the windows computers are connected yet. The linux server almost never resets. 

However, I see that the linux server is serving its' traffic anyway. When I restart the networking using /etc/init.d/networking restart then it relists with the router. What is happening here?

---

### Post by Kulgan on 2009-04-10
The server may not have "noticed" the router resetting, or for some reason not re-announced itself to it. The router doesn't list it because it hasn't had a DHCPRequest from the server, but allows traffic to flow because it is on the right side. So long as no other devices take the server's IP, you should be fine - and as most routers have assign semi-static IPs, the probablity of that is low. 

So traffic is flowing despite the router being reset. That doesn't seem too bad to me ^^
I think you should be more worried about the router's condition than what is happening between it and the server...

-K

---

