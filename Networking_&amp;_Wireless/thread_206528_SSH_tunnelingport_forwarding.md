---
title: "SSH tunneling/port forwarding"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by cougem on 2006-06-30
Hi!

I'm trying to port forward in SSH so I thought I'd give it a go by testing the direct connect protocol over it; ive got my ubuntu 6.06 box running an ssh server, and i've got my windows client running putty set up so connections to a local port 8989 are routed to <address of a direct connect hub i knowort>. I then connect to my dapper box via normal ssh.

I open up my direct connect client and then try to connect to 127.0.0.1:8989 but it says the server actively refused the connection. i try to open a raw connection on the windows client to 127.0.0.1:8989 and says 'connection refused'. So something doesn't seem to be working.....

I'mm pretty sure the forwarding's alright as when i change the target of the port forwarding to 127.0.0.1 and then get the client to ssh to itself, it tries to connect to the dapper box, implying it's working.

Has anyone got any idea what's wrong? I mean surely all linux box is doing is sending on packets like a normal router to the direct connect server, so there shouldn't be a problem....?

Thanks so much guys

---

### Post by steve.horsley on 2006-06-30
When putty is connected to the Ubuntu box, the command **netstat -an** on the Windows box should show both the ssh connection to port 22 and a listening socket on port 8989. If you don't see this then putty is not configured right. 

If you do see that, then I guess you will have to use Ethereal to see what's going on. Ethereal on Ubuntu will tell you if Ubuntu tries to connect to the hub (and if the hub refuses the call). Ethereal on windows might show you something - you would hope that after receiving the client connection, there would be some SSH traffic to Ubuntu.

---

### Post by cougem on 2006-06-30
OMG! It's suddenly decided to start working. Oh well that's good news anyway! Thanks so much for the help though!

---

### Post by cougem on 2006-06-30
Ooo I've realised the problem. It's so stupid. I was setting up the port forwarding then loading the settings for my connection to my computer. I didn't know that loading settings for your ssh session over-rode your port forwarding settings, so just before I kept connecting it kept wiping all the rules!

---

### Post by steve.horsley on 2006-06-30
LOL. A little gotcha. 

Thanks for posting the solution - others can learn from it too.

---

