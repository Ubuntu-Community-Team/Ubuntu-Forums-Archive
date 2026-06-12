---
title: "How do I remotely control another Ubuntu Pc via a LAN"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-02-12
Hi.
I can connect my PC to my laptop in two ways. The first way is to use a crossover cable and the other method is to use a router. I am not connected to the internet while the desktop PC and laptop are connected together.
I want a way to control my laptop from my desktop PC. I know of QuickSynergy and it is great. However I want to be able to control the laptop as if I was sitting in front of it. To have its screen on my desktop monitor. 
I know this is only useful if you have many computers on a network but I want to do this for testing reasons and just to know how its done.

Please help. Thank you.

---

### Post by howlingmadhowie on 2009-02-12
> **Rytron said:**
> Hi.
I can connect my PC to my laptop in two ways. The first way is to use a crossover cable and the other method is to use a router. I am not connected to the internet while the desktop PC and laptop are connected together.
I want a way to control my laptop from my desktop PC. I know of QuickSynergy and it is great. However I want to be able to control the laptop as if I was sitting in front of it. To have its screen on my desktop monitor. 
I know this is only useful if you have many computers on a network but I want to do this for testing reasons and just to know how its done.

Please help. Thank you.

system->preferences->remote desktop

and

applications->internet->remote desktop viewer

---

### Post by Rytron on 2009-02-12
I did that. I am connected via crossover cable so there should be no problem with ports.

Do I need to do anything with my firewall?

In remote desktop I get this error (image attached).

Also I tried Terminal Server Client but I can not select VNC as the protocol as it is not selectable.

:confused:

---

### Post by Rytron on 2009-02-12
Got it! To enable VNC in Terminal Server Client I found that I needed to install vncviewer

```
sudo apt-get install vncviewer
```

For the remote computer it should only have the two sharing boxes ticked.

Done.

:popcorn:

---

### Post by Rytron on 2009-02-12
Next I am going to connect via a router (without internet access).
What port number do I need to open on the router?

---

### Post by pdtpatrick on 2009-02-12
what do you mean by you are going to connect via a router without internet? is the router connected to your ISP modem? You might want to think about using RealVNC .. install the server on the machine you want to connect to and install the client on the computer you are connecting from and then make sure you are using SSH protocol and that your router port forwards to the vnc server .. port forward 22 or whatever number you assign in your sshd.conf file ..

---

### Post by Rytron on 2009-02-12
> **pdtpatrick said:**
> what do you mean by you are going to connect via a router without internet? is the router connected to your ISP modem? You might want to think about using RealVNC .. install the server on the machine you want to connect to and install the client on the computer you are connecting from and then make sure you are using SSH protocol and that your router port forwards to the vnc server .. port forward 22 or whatever number you assign in your sshd.conf file ..

I mean I use a wireless modem/router to connect to the internet. Also, I have a spare old router that I just use for testing and learning new stuff. That router is not wireless and I just use it in my room to connect up different computers. My wireless modem/router is downstairs, too far away for cables. Does your method above allow for remote access over the internet?

---

### Post by ugm6hr on 2009-02-12
> **Rytron said:**
> Next I am going to connect via a router (without internet access).
What port number do I need to open on the router?

None is necessary.

Default VNC port is 5900, which should be opened on the remote desktop server machine:
```
sudo ufw enable
sudo ufw allow 5900
```

If you forward the port on the router, you could connect from the outside world / internet.

---

### Post by Rytron on 2009-02-12
> **ugm6hr said:**
> None is necessary.

Default VNC port is 5900, which should be opened on the remote desktop server machine:
```
sudo ufw enable
sudo ufw allow 5900
```

If you forward the port on the router, you could connect from the outside world / internet.

Do I have to run

```
sudo ufw enable
sudo ufw allow 5900
```

on both my desktop PC and the PC I want to connect to? Is that code vital?

How do I undo do the above code later?

---

### Post by ugm6hr on 2009-02-13
> **Rytron said:**
> Do I have to run

```
sudo ufw enable
sudo ufw allow 5900
```

on both my desktop PC and the PC I want to connect to? Is that code vital?

How do I undo do the above code later?

Just on the PC you want to connect to.

It opens port 5900 on that PC, to allow the desktop PC to connect to it.  If you have a router with a firewall, there is no security risk, since the router firewall will prevent the outside world from connecting.

To undo:
```
sudo ufw deny 5900
sudo ufw disable
```

---

### Post by Rytron on 2009-02-13
> **ugm6hr said:**
> Just on the PC you want to connect to.

It opens port 5900 on that PC, to allow the desktop PC to connect to it.  If you have a router with a firewall, there is no security risk, since the router firewall will prevent the outside world from connecting.

To undo:
```
sudo ufw deny 5900
sudo ufw disable
```

Thank you ugm6hr, your a star. Do I still have to open port 5900 on the router of the PC I want to connect to?

---

### Post by ugm6hr on 2009-02-13
> **Rytron said:**
> Thank you ugm6hr, your a star. Do I still have to open port 5900 on the router of the PC I want to connect to?

Not if both the desktop and computer you want to connect to are on the same network (i.e. connected to the same router).

---

