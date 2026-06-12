---
title: "How can I connect to my ssh server from outside the lan?"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by kj17x0 on 2011-03-08
Hi, 

I just setup sshd server on my ubuntu server 10.10 today. I then tried to connect to it with putty on my windows laptop outside the lan but failed. I entered the ip address as my wan ip address and the port as 23 (same port on the ssh server. I also have port forwarding enabled. 
The connection timed out every time. There are a lot of guides about ssh reverse tunneling but none works. 

Please help!!

Thanks!

---

### Post by annoyingrob on 2011-03-08
It's possible that your ISP blocks ports like that.

You could try opening a different port on your WAN side, and forward it to the server's SSH port.

---

### Post by kj17x0 on 2011-03-08
well i have also tried ports 22, 81, and 1234. (Any ports to suggest?)

Is there a great risk involved if i put the server in DMZ? (Demilitarized Zone, put server outside of the router firewall in the public internet)
Or can i enter the address as wan ip slash lan ip?

Thanks!

---

### Post by annoyingrob on 2011-03-08
Hold on a second. Your SSH server is running on port 23, not port 22?

---

### Post by kj17x0 on 2011-03-08
yes. I changed it to port 23 because my ddwrt router uses port 22 for ssh as we. To eliminate conflicts i changed the ubuntu ssh server port to 23.

---

### Post by n~kf)}BW% on 2011-03-08
Perhaps port 23 isnt the best choice. Use ports greater than 1024.

---

### Post by kj17x0 on 2011-03-08
i have tried port 1024 and 1025 with no success.

---

### Post by n~kf)}BW% on 2011-03-08
Then you're doing something wrong :/ Tell me how did you connect and set up the server?

---

### Post by kj17x0 on 2011-03-08
the ssh server came with the ubuntu server installer. I didn't change anything in the config file except the port value. 
Just to clarify, i CAN connect to it inside my lan network. 

Ok so what i did was I first enabled port forwarding on my router which forwards port 23 to my router's address, then I disabled the router firewall. 
In putty, I entered my wan address as the target ip. It always returns connection timed out. I can however connect to my router's ssh server when I enter 22 as the port #. (that's why i changed the ubuntu ssh port to 23). 

Thanks for trying to help me!

---

