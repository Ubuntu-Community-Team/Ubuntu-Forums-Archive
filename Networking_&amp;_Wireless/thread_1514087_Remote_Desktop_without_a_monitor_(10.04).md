---
title: "Remote Desktop without a monitor (10.04)"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by bmwqg on 2010-06-20
I have been trying and trying to get remote desktop to work without using a monitor connected to the server. I have the server set up to where it can be rebooted and everything perfectly fine remotely (as long as it has a monitor). Unfortunately, I need this to be not connected to a monitor-PERIOD. I would think this would be something to be working out of the box, but I guess not. 

Can somebody please help me figure this out?!?

SIDENOTE: Happy Father's Day, Guys!

---

### Post by cariboo on 2010-06-20
You need to be logged in on the server, in order to use remote desktop. You really don't need a desktop on the server, as you can do all the server administration from the command line. I would suggest removing gdm from the server, and only starting the desktop when you need it by typing:

```
startx
```

from the command prompt. To access the server securely I would suggest using ssh, you can set it up to use x-forwarding by typing the following command:

```
ssh -X user@server
```

Then once you have logged on and are at the prompt, just type the name of the program you want to run. For more on installing openssh-server and setting it up securely have a look [here]("https://help.ubuntu.com/7.04/server/C/openssh-server.html") and to set up private keys have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

---

### Post by fdm on 2010-06-20
Which app are you trying to use? The default in Ubuntu is vino. I tried it on my headless box, but no dice. From what I read, vino requires X to be started and for you to be logged in for it to work. I haven't bothered trying it yet, but [freenx]("https://help.ubuntu.com/community/FreeNX") is supposed to be very good and run as a daemon. Other then that, make sure your /etc/network/interfaces file is set up correctly.

---

### Post by bmwqg on 2010-06-20
Well, I want to have a graphical display available, and I am accessing the server using Windows 7 across the network. Which is why I need something like vino.. in that case. Is FreeNX client also available for Windows?

UPDATE: Also, can I use RealVNC client instead to view the desktop with FreeNX?

---

### Post by sanderj on 2010-06-20
> **bmwqg said:**
> I have been trying and trying to get remote desktop to work without using a monitor connected to the server. I have the server set up to where it can be rebooted and everything perfectly fine remotely (as long as it has a monitor). Unfortunately, I need this to be not connected to a monitor-PERIOD. I would think this would be something to be working out of the box, but I guess not. 

Can somebody please help me figure this out?!?

SIDENOTE: Happy Father's Day, Guys!

Do you mean it does not boot at all when there's no monitor connected? How do you know that? Does it stop in the BIOS, or in the OS?

---

### Post by bmwqg on 2010-06-20
No, it boots up... it just doesn't load up the default remote desktop application, so I'm sure there is an error somewhere. 

EDIT: (I think there is an error saying something about finding the resolution or something to output, since one could not be found...)

---

