---
title: "Remote Desktop Ubuntu from Windows over Internet"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by ryrobbo on 2009-11-01
Hello,

I have install VNC onto Ubuntu 9.04 and Windows and can remote them fine when the PCs are both on the same network.

However, how do i setup my ubuntu machine to accept connections over the internet? I want to be able to enter the external IP of the network and log onto my ubuntu machine.

Would i need to open ports on my router???

Thanks.

---

### Post by Groodles on 2009-11-01
If you're using the standard "built-in" VNC server (Vino) then it listens on port 5900.  So most probably need to forward 5900 (TCP).

If you're using a different VNC server (tightvnc, etc) then you'll need to forward the port it uses instead (could be 5900 or 5901 or something else.)

```

sudo netstat -tulp

```That command will list all listening services on your box.  Find the line that has VNC as it's owner (on the far right) and that's the port you'll need to forward.

---

### Post by ryrobbo on 2009-11-01
I opened up the ports on my router and it worked a treat.

Thanks mate.

---

