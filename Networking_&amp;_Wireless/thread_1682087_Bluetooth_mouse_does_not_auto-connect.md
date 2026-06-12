---
title: "Bluetooth mouse does not auto-connect"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by 1fireman1 on 2011-02-05
Im using a Samsung R420/R470 laptop with Broadcom bluetooth and a Prolink PMO624B mouse ([http://www.prolink2u.com/new/products/index.php?cid=262](http://www.prolink2u.com/new/products/index.php?cid=262))

My mouse works when I add it as a new device, but if I off the mouse and on it again, the mouse does not auto connect. I have to press and hold the connection button under the mouse and reconnect to the mouse.

The mouse says that it is linux compatible, so I guess its a problem with my bluetooth drivers.

---

### Post by ebasa on 2011-02-05
I have the same problem posted several months ago, no one here seems to know the answer or maybe we are the only two using a bluetooth mouse on Ubuntu.

---

### Post by 1fireman1 on 2011-02-05
It works now, but I have to leave the mouse on for ~5 mins before the cursor moves or the buttons work. Is there any way to speed up the connection without re-adding the device?

---

### Post by paulr9 on 2011-02-14
Hello,

I'm having the same problem, no advice I find online seems to fix the problem. I have to manually reconnect to the mouse, with a few clicks of... another mouse. I discovered that typing 'hcitool scan' into a command prompt, has a similar effect. Maybe this will work for you too.

Is there a startup script I could add this command to to make it work on every powerup / wake?

Paul

---

