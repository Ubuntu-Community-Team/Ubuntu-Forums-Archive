---
title: "Strange computers showing up in /var/log/samba"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2011-12-30
The title pretty much says it all. I'm seeing what appears to be over a hundred other machines in this directory. They all have the same format in the file name, such as: log.gregspc. I don't know anyone named Greg. I do a cat on the file and get something like: 

"getpeername failed. Error was Transport endpoint is not connected" and "read_fd_with_timeout: client 0.0.0.0 red error = Connection reset by peer."

Is the computer basically looking up all the other computers on it's current network (say, a public access point) and listing them in the log? The error seems to indicate that it's checking for public shares and not finding any. Am I correct?

Also, even more strange, is when I open Thunar and then click the Network icon, I see two other computers I do not know: "JOHN-PC" and "OWNER-PC". I normally see only my other networked machine, called "MAIN" but it does not appear. I have to navigate through "Windows Network" to get to it. I spent the past couple of nights in a motel out of town so I'm guessing the computer saw those two machines and made some kind of sharing association (!) but I never did connect to them. Also, neither of those machines show up in the log directory I mentioned above.


Anyone know what the hell is going on here?

---

### Post by 2F4U on 2011-12-30
How are you connected to the network when you are seeing that two other  machines "JOHN-PC" and "OWNER-PC"? If it is a wireless connection, maybe  it is not your own network but some other?

---

### Post by scottbomb on 2011-12-31
I'm connected with a wired connection, that makes it even more strange. Even today, the day after I have returned home, I still see those other machines in Thunar and I don't see my own machines unless I go through the Network icon. I cannot access those machines though: "Failed to retrieve share list from server." Perhaps this is a Thunar bug, reporting these other machines even though they are no longer within the same network (as I assume they were when I was staying at the motel a couple of days ago). I'm curious to see how I can look up this information on the command line. I'll be learning how to do that over the next day or so.

---

