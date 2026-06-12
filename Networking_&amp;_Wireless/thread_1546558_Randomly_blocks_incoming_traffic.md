---
title: "Randomly blocks incoming traffic"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by boast on 2010-08-05
I am running the latest ubuntu. Sometimes it randomly stops accepting ssh connections, afp/smb connections, and even stops responding to pinging. It is connected via WIFI. 

I go over to the desktop and use the browser, and the internet still works fine. Then after a while, it starts accepting incoming traffic again.

This is not great, since I am running it as a server.

---

### Post by ajgreeny on 2010-08-05
It sounds as if the wifi is occasionally dropping out.  If you have a gnome gui you would expect to get notifications on screen saying the connection is lost, but if you have no gui, you would need to use a command to find out if it was live or not, maybe **ifconfig**.

---

### Post by boast on 2010-08-05
Right now I just tried to ping it (after the desktop having no traffic for a while) and it says host is down.

On the desktop, nm-tool shows that the wifi is connected, and I can surf the web fine.

---

### Post by cavalier911 on 2010-08-05
With my previous wifi router my laptop could share it's files over samba. When that wifi router burned out and I installed the new one the laptop no longer shares it's files yet it surfs the web fine and can use files being shared by my other computers on my network. In addition it doesn't reply to pings anymore unless I ping from it to the router at the same time as I ping it from another computer.This is even when I'm 2 feet away from the wifi router and the laptop is showing a 90% signal strength.I have 2 other computers with wifi that work perfectly sharing files with the new router.It's just this laptops builtin wifi adapter doesn't like the new access point. Attaching the laptop with ethernet cable to the router it shares files perfectly. So I wouldn't count out wifi as the problem unless you have the same issues with wired ethernet.

---

