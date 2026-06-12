---
title: "Ubuntu &gt; Mac Terminal Server Client (VNC) Annoying Problem!?"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by neonpanther on 2010-09-09
Okay
So I setup VNC on my Mac (that runs Snow Leopard) and my PC (that runs  Ubuntu) and I gave the IP address to Ubuntu, entered the password and it  worked fine.

The problem is that it still works fine...
I only made this connection to test it because I thought it'd be cool,  which it was (for a while). Now I cannot delete this connection  whatsoever!!!

I have tried changing the password on the Mac, limiting the users, and  even switching it off completely by unchecking its checkbox. I have also tried limiting the users...
BUT UBUNTU STILL MANAGES TO GET INTO MY COMPUTER!

This is really annoying because anyone using the PC downstairs can now go into my Mac and mess about with things - I hate this.

Somehow, Ubuntu has locked in on my Mac and, despite the changes, can earn access no matter what!

Does anyone know of a solution to this VERY annoying problem???

---

### Post by davrosuk on 2010-09-09
Awesome! :)

If you ask me, the problem is going to be at the remote end (ie the mac). Clearly something is still running on the host if you think you've disabled it and another computer can still connect.

---

### Post by neonpanther on 2010-09-09
I have tested the VNC between my iPhone and my Mac and my iPhone recognises the password changes and what not so it's definitely Ubuntu...


Sooooo     is there a way how I can reset the 'Terminal Server Client' software on the Ubuntu so that it has forgotton everything it knows?

---

### Post by davrosuk on 2010-09-09
Not to be funny, but Ubuntu isn't at fault here. If you change the password on the host, all clients would be expected to present this new password. If you disable VNC on the host then nothing (and I do mean *nothing*) should ever be able to connect... ever!

The fact that something can connect suggests that the package on the Mac is not working correctly and allowing a previously connected client to connect regardless. To be fair VNC is not exactly the most secure thing in the world at the best of times! I'd only ever use it in an SSH tunnel. 

Still... Put simply, in situations like this - it is *always* the host that is at fault. The fact that another device can or can't connect doesn't prove anything - you might find clients that can. Check to make sure that there isn't multiple VNC/VNC-like services running from the Mac. If you haven't already (though I'm sure you have) reboot it.

---

### Post by neonpanther on 2010-09-09
Thankyou for your reply.

(Yes I have rebooted).

I understand that it might not be Ubuntu that is at fault but can you tell me a way to COMPLETELY ERASE all of the Ubuntu Terminal Server Client's memory (a ULTRA-HARDCORE UNINSTALL)???

There must be because I just want it to forget everything it knows (when I open it it has my IP address in the input box already) :@

---

### Post by davrosuk on 2010-09-09
In the home directory there is a directory called ".tsclient" if you remove its contents then all the information pertaining to previous connections will be lost.

I would look into why the host is allowing this though as you may have a massive hole in your security! :-)

---

