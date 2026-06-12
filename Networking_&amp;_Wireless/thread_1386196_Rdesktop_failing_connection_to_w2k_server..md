---
title: "Rdesktop failing connection to w2k server."
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by aldobenart on 2010-01-20
I'm trying to connect via krdc or rdesktop to a windows 2000 server from my kubuntu karmic box..

I always receive: "ERROR: recv: Connection reset by peer", whichever combination of switches I put on the command line (included -n clientname).

I can see the Event Register of the server: on every connection attempt, an error "termservice 1004" (The terminal server cannot issue a client license.) is logged.

I could find many and many suggestions, telling to use -n switch, but this isn't working for me.

Moreover, if I start Virtualbox on the same machine where I get the problem and from a windows XP instance I use "Remote Desktop Connection", all is working nicely.

Any suggestion?

---

### Post by dhurler on 2010-01-22
First off are you using Terminal Services in remote admin mode or in terminal server mode? I was getting a similar error with a number of servers that are running in remote admin mode so I can't say if this fix will work for you.

Usually a failure to connect to a Windows box with rdesktop happens because the security level is set to high on the Windows machine. By default Windows server OSes have more sturdy default security settings for RDP than the client OSes do. This is why connection errors are usually seen when connecting to server boxes and not XP or Vista machines.

Navigate to "control panel" --> "administrative tools" --> "terminal services management" (or whatever it's called in W2K) and find the default RDP connection. There should only be one listed. Right-click and select "properties".

You should then see a bunch of tabs and under the first one ("general")of them you will see some options regarding connection security. Make sure you set "security layer" to "negotiate" and that for "encryption" "client-compatible" is ticked and that you are not requiring "FIPS level security" for incoming RDP connections. I may have the exact layout all wrong as I haven't used Windows 2000 for ages. I am going off my memory of Windows 2003 and 2008.

Newer versions of Windows extend this security further by allowing you to require "Network Level Authentication" and certificates but I don't think that is an option in 2000 Server.

You should be able to make things work by playing with those options on the Windows machine.

---

### Post by aldobenart on 2010-01-22
Sorry, dhurler, but I haven't the authority for modifying server settings, also if I can see event register.

I can't reply to your question: "are you using Terminal Services in remote admin mode or in terminal server mode? "; I'm only running the command: rdesktop host.domain. I can connect many other hosts on the same domain, running w2003 or w2008.

Taking in account that running windows "Remote Desktop Connection" client  in a virtual machine under Virtualbox in the same phisical box is working nicely, I think that linux rdesktop is a poor implementation of rdp protocol. Do you agree?

---

