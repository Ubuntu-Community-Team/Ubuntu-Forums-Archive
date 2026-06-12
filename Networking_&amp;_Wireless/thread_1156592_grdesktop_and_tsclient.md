---
title: "grdesktop and tsclient"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Azzurri10 on 2009-05-11
I am brand new to Ubuntu and so far I like what it has to offer, however, I have tried and failed to connect to my work terminal server client using both grdesktop and tsclient.  

There was one post I read that could have been helpful only I was not allowed to post a reply.  It was related to using an Aventail type program.

My company set up a direct connection to the domain, which no longer necessitates Aventail, but when I try entering all the proper info into grdesktop, I receive the following error:

"ERROR: getaddrinfo: Name or service not known"

I have contacted my IT department to see whether they can provide me with the actual IP address so as to enter that into the "Computer" field because as of now, the host name is not working.

CAN ANYONE HELP.. I DO NOT WANT TO GO BACK TO WINDOWS!!!
THANK YOU IN ADVANCE

---

### Post by Azzurri10 on 2009-05-12
Got the IP address from the IT department and tried a multitude of ways to connect to my work terminal server client with grdesktop and tsclient and no matter what I did, it did not work.

The error message basically said it can not connect to the IP address.

Has anyone had success in this process?

I can really use some guidance on this.

Thanks

---

### Post by Brandon Williams on 2009-05-12
First, verify that you can actually connect to the rdesktop server on the correct port. On the command line, run 'telnet <ip address> 3389', where <ip address> is the address provided to you by your IT department.

If you see 'telnet: Unable to connect to remote host: Connection refused', that means you have the wrong IP address, because no-one is listening for rdesktop connections on that machine.

If the connection hangs, that probably means that you can't get to the address you specified. Try using traceroute to figure out what is happening to your packets.

If you get a response that looks something like:
```
Connected to <ip address>.
Escape character is '^]'.
```
it means that you can connect to the server on the correct port, so you are probably filling in some field incorrectly in the tsclient gui.

---

### Post by Azzurri10 on 2009-05-12
I was assuming that grdesktop or tsclient would replicate the request for connection like a windows computer would.  

I did run telnet <ip address> 3389 and did get the "Unable to connect... host" error message.

At this point, I assume there is no other way?  

Appreciate your support and replies.

---

### Post by Brandon Williams on 2009-05-13
What do you mean "replicate the request for connection"?

If you are getting a "Connection refused" error when you attempt to telnet to that port, it means that a server with that IP address exists but it is not accepting remote desktop connections. Most likely, you have the wrong IP address.

Once you solve that problem and you can connect to the server using telnet, then go back to tsclient or grdesktop and try again to get a real remote desktop connection.

---

### Post by Azzurri10 on 2009-05-13
I have the proper IP address because I pinged the host name using my work laptop, which runs Windows XP.  I have no problems whatsoever connecting from an xp computer to my work terminal server.

---

### Post by Azzurri10 on 2009-05-15
Let me preface this with saying I did not have all the facts and I'm retarded.

I need a VPN client like Aventail to connect to my work network.  

I will do some research online to see what I can find, but if anyone has a simplified tutorial or any comments, please feel free to share.

Thanks for your help ahead of time

---

### Post by Brandon Williams on 2009-05-15
I have never been able to find a freely available Aventail client. I think you're expected to get it from your company's IT department, possibly just by connecting to the Aventail server itself. I believe Aventail SSL VPN boxes usually have multiple ways to connect, and if you connect using standard HTTPS access, the page you get to will give you access to the client.

It's been a long time since I used one of these, so I might be remembering wrong.

---

### Post by Azzurri10 on 2009-05-15
I have spent the past 4 hours trying to figure out how to use Network Manager and vpnc.  At this point, I do not know what I have downloaded in the terminal but am beginning to think that I am not smart enough for Linux. 

I downloaded Network Manager in the terminal, but do not see the icon anywhere.

If anyone can assist I would appreciate it.

---

### Post by cosmicharade on 2009-08-02
Anyone know how to specify a computer name?  I can connect from Windows XP although I need to specify the computer name on the work network.  The only option I can see is 'domain'.

---

