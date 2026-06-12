---
title: "Remote Desktop Issues"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by throese on 2010-09-23
Okay, I've tried just about everything. I've downloaded practically all of the different Remote Desktop programs and tried them all to no avail. I always get a stupid "unable to connect" error and it asks if I want to try again. 

I want to be able to do it like this video does:

[http://www.youtube.com/watch?v=n33yl1jAqgQ](http://www.youtube.com/watch?v=n33yl1jAqgQ)

The ONLY thing that actually works so far is the TeamViewer program. I installed it on the Windows XP machine in the den and I have it on my Ubuntu partition on my laptop. TeamViewer is the only way that I can connect my laptop to the desktop, but I wanna be able to connect my laptop to any machine in the house or if a friend of mine needed help, to their computer over the Internet. Please help

---

### Post by an0dos on 2010-09-23
> **throese said:**
> Okay, I've tried just about everything. I've downloaded practically all of the different Remote Desktop programs and tried them all to no avail. I always get a stupid "unable to connect" error and it asks if I want to try again. 

I want to be able to do it like this video does:

[http://www.youtube.com/watch?v=n33yl1jAqgQ](http://www.youtube.com/watch?v=n33yl1jAqgQ)

The ONLY thing that actually works so far is the TeamViewer program. I installed it on the Windows XP machine in the den and I have it on my Ubuntu partition on my laptop. TeamViewer is the only way that I can connect my laptop to the desktop, but I wanna be able to connect my laptop to any machine in the house or if a friend of mine needed help, to their computer over the Internet. Please help

Have you turned off the desktop effects? BTW you should read the stickies at the top of the security forum. VNC is not secure.

---

### Post by throese on 2010-09-23
Oh, I didn't know that. My Networking course hasn't gotten that far yet and I don't have any special effects whatsoever on my Ubuntu partition.

---

### Post by an0dos on 2010-09-25
> **throese said:**
> Oh, I didn't know that. My Networking course hasn't gotten that far yet and I don't have any special effects whatsoever on my Ubuntu partition.

You should verify that by clicking on "System" -> "Preferences" -> "Appearance" thence click on the "Visual Effects" tab.

You may also want to disable the firewall if you have enabled it. You can check the status of your firewall by typing ```
sudo ufw status
``` in the terminal. If this solves the problem, you should adjust your firewall rules.

If you are taking courses on networking you should learn how to set up SSH with pre shared keys. There is a help page here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") and here: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

If you want a graphical environment you can look into X11 forwarding or tunneling VNC over SSH.

---

### Post by throese on 2010-09-25
An0dos: What do you mean by "If you want a graphic environment you can look into X11 forwarding or tunneling VNC over SSH"?

And thanks for the help so far from everyone. I'll keep you all updated/posted as to if/when it starts working.

UPDATE:

Nothing works and idk what the heck to do or how to set up SSH. I don't know what the Windows XP Home Edition has on it. By that I mean idk what programs it has for remote desktop. Would installing UltraVNC make any difference?

---

