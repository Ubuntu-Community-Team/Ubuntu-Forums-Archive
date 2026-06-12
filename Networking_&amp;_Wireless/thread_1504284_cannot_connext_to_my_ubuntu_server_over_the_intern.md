---
title: "cannot connext to my ubuntu server over the internet using ssh client (BBSSH)"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by wheresmything on 2010-06-07
i am at wits end.  i have searched long and hard for a solution and i have come up bupkis.
i am trying to set up my server to be accessed via the internet using my blackberry and an ssh client to no avail.
i have managed to get the LAN wifi connection to work, its the WAN connection that fails me.  last year, i was able to do it using another ssh client no problem.  as it is now, i see a number of posts from setting up dhcp, dns, virtual hosts, allowing this or that, etc.  i do not remember this many steps in setting it up previously.  
i have found my external(public) ip address (well, i found 4 or 5 of them actually.  depends on how i get it (whatismyip, whatsmyip, etc) and i have used all of them to try and connect.  
since i am over the internet (effectively) i do it this way (xx.xx.xx.xx:22) (the 'x' represents my external/public ip) if i do :80 it comes back "peer refused connection".
when i try to connect, i get "authentication failure, avaiable methods are publickey, gpi with mic, password." and the thing is, i turned off pubkey authentication, no clue what gpi is and the password is correct (so is the user name) in fact, i turned off all authentication except password and same message.  i have no idea how to get a key (pub/priv) to my bb so that will do me no good. i have heard about using a SD to do it, but that causes mroe problems.  i have done the port forwarding to 22 and to 80 i have set up a DMZ...nothing works. i turned off the ubuntu firewall. nothing. same message.
i have went through and tried the dns thing (no go) and all others and no go.  again, i dont really remember going through this many hoops to get it to work.
can anyone help?

---

### Post by Nesman on 2010-07-22
I had a similar problem.  I've install MidpSSH on my blackberry and it connects.  BBSSH is based on it, so it's very similar.

[http://www.xk72.com/midpssh/](http://www.xk72.com/midpssh/)

Also, port 80 is for the apache web server, not for ssh.  You probably want to stick to 22 for ssh, unless you've changed it in your config.  I suggest testing it with puTTY from a windows computer or ssh from a linux machine, then getting the blackberry connected.

---

