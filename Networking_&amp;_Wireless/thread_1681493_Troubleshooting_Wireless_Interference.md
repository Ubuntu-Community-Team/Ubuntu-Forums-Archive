---
title: "Troubleshooting Wireless Interference"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by tenbob1 on 2011-02-04
I've just spent several hours trying to debug my wireless connection. In the end, the problem was easy to fix. A video sender in another room was jamming the radio signal.

I'm posting this because I found it very difficult to understand what was happening. Perhaps forum users could suggest other tools I should have used to find the solution quicker.

The symptoms of the fault were as follows. When the jamming signal was present there was no communication at all between my netbook and the wireless router. Firefox could not load any pages from the internet and displayed "Server not found".

Network Manager on the other hand showed a completely different picture. It thought that the network was still connected. The little beacon icon continued to flash its waves as normal. In fact you could use network manager to disconnect and reconnect to the wireless network and it behaved as if there was no problem whatsoever. 

Logging on to the wireless router displayed the true picture. When the interference was present all the existing connections were dropped. 

I tried all sorts of tools including netstat, ifconfig, etc, but none seemed to give me a clear indication of whether the connection was working or not. I couldn't see any errors or bad packets or anything like that. So why is it so difficult to tell whether a connection is working or not?

Eventually I found the answer through iwconfig. In the output from iwconfig the field "Access point" seems to be the true indicator of whether the connection is up or down. When the connection is working normally Access point shows the MAC address of the router. When the connection has failed, Access point shows "Not associated".

So I hope that's helpful to others. But I found it really difficult to discover what was going on. Network Manager claims to be the one tool you need to set up your network. Yet it kept telling me that a connection was working even though it clearly wasn't. And it wasn't just a marginal case of interference. The channel was completely blocked and no data was getting through at all. The router knew the connection had been dropped, but Network Manager didn't. 

If anyone knows any better debugging techniques, please let me know. Sorry for the slight rant. Thanks, tenbob

---

### Post by grahammechanical on 2011-02-04
An interesting post. Would you have believed it, if anyone on the forum had suggested interference as the problem?

What do you think would happen if several computers were connecting through wireless to the same modem/router at the same time? Would that not effect download speeds and connection stability? Telephone line quality can also have an effect on connection stability and download speed.

Would anyone accept these things as the reason for their problems with getting a wireless connection?

It seems to me that Network manager was doing what it was designed to do. As the name suggests it manages networks. It is not a diagnostic tool.

Regards.

---

