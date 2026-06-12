---
title: "Cant see shares on network"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by merdok1981 on 2009-07-29
Ok here is the story:

Yesterday I bought myself a static IP address from my ISP and then went around setting everything up, one of the things I had the biggest difficulty with was getting webcam-server working. At one point I'd messed up the code and stopped Jaunty from booting at all, it just froze on 'starting samba deamon', I realised I'd messed up and I removed the line of script I'd added to init.d and it allowed me to boot again without a problem.

However it now appears that samba has stopped working properly. On windows machines I can do \\fileserver to access the shares on my server but it does not appear in the network explorer window and my other computers (whcih are all on Jaunty) cannot see the network at all!

I'm not sure what I've done and I have been trying for hours to fix it and i'm at a loss... can anyone help me?

---

### Post by superprash2003 on 2009-07-29
try this to start samba **sudo /etc/init.d/samba start**

---

### Post by merdok1981 on 2009-07-29
Thanks for the reply mate.

Samba IS running, this is where my confusion is coming, I've reinstalled it, stopped it started it... I've done loads but although I can access my shares via windows I can't see them in windows explorer and I can't access them at all from my other linux machines.

---

### Post by superprash2003 on 2009-07-30
> lthough I can access my shares via windows I can't see them in windows explorer
then how are you able to access them? post output of** smbtree** from ubuntu terminal

---

