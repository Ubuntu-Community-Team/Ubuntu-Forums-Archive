---
title: "Wireless not staying connected"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by tkoelling on 2010-04-17
[FONT=Times New Roman][SIZE=3]Having problems staying connected on my wireless in Ubuntu: [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I’ve  got a  Dell 1720 Inspiron with a Broadcom Card: BCM4312 802.11b/g. Driver is a wl0 running driver version 5.10.91.9 My router is a NetGear with an access point about 20 feet away from router. This computer is a dual boot with Windows XP and Linux/Ubuntu 9.0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Here is the problem: If I boot in windows, I can run all day long on the wireless…no problem. If I boot into Ubuntu and I’m right next to the router then I’m OK on the wireless. If I move next to the access point (where I want to work) I can boot into Ubuntu and stay connected for a short time (4 minutes or so) then I loose the connection and have to reboot to try to get connected again.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman]HELP! I gotta get to work[/FONT]

---

### Post by cblah001 on 2010-05-04
I am having the same exact problem but it is with my connection at school. My connection at home works just fine... Anyone got any advice?

---

### Post by Visentem on 2010-05-04
Almonst the same with me. My connection in Ubuntu runs slower than in Windows. It doesn't gets to disconnect, but it's really frustraiting. Just like a 64K connection.

---

### Post by udippel on 2010-05-04
> **cblah001 said:**
> I am having the same exact problem but it is with my connection at school. My connection at home works just fine... Anyone got any advice?

Had you searched before posting, you would have seen that many have this problem.
Let me take a guess: at school, you're one of many. At home, you're basically one user with a high throughput. Correct?

Uwe

---

### Post by meithan on 2010-05-04
We definitely need to unify all these threads into a sticky thread. 

By the way, if you don't want to reboot to connect back after it drops, you can unload / reload the kernel driver. It takes a couple commands in the terminal, and it's been doing the trick for me. It's not a solution, but it saves me the reboots.

---

### Post by mr_biglz0rth1985 on 2010-05-04
I've been having the same issue,...I have a Dell inspiron 1501 with a b4311 wireless card from broadcom....and if I do get a connection its INCREDIBLY slow.

---

### Post by cblah001 on 2010-05-04
> **udippel said:**
> Had you searched before posting, you would have seen that many have this problem.
Let me take a guess: at school, you're one of many. At home, you're basically one user with a high throughput. Correct?

Uwe

I didn't create the thread, just tacking myself onto this one in case anyone has a solution for us. I have searched my issue? Yes. Have I found anything that is working? No. Try doling out some advice instead of criticism.

Do you have a solution or one of these threads that can help? It would be much appreciated.

---

### Post by PDA1 on 2010-05-04
Here's how I fixed it- 
 Start TERMINAL 
 
[LIST=1]
[*]     sudo Nautilus
[/LIST]
 
[LIST=1]
[*]     Go to the folder /var/lib/NetworkManager/ 
[*]     Edit the file NetworkManager.state to read “setting NetworkingEnabled=true” 
[*]     Save the edited NetworkManager.state file 
[*]     Close Nautilus 
[*]     Using TERMINAL type “sudo restart network-manager”
[/LIST]

---

### Post by cblah001 on 2010-05-04
I don't know if it worked for tkoelling but it was already enabled for me.

---

### Post by meithan on 2010-05-05
Same here.

---

### Post by kachkeis on 2010-05-09
Hi there,

Try this thread, it's for the WPN111 but i heard that it COULD be  helping for other Netgear adapters. Or  You just use it for inspiration to find a solution.

[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Cheers,
kachkeis :smile:

---

