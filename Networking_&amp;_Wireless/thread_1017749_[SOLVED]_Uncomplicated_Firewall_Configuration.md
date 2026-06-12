---
title: "[SOLVED] Uncomplicated Firewall Configuration"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by urban48 on 2008-12-21
I am trying to access a Windows box on my home network with my Ubuntu laptop. When I disable ufw, I can access the network. When I enable ufw, I cannot. I know that this is because I need to open certain port(s) in order to allow information to be transmitted between the two machines, but I have no clue which ports to open. Any help or information is greatly appreciated!

---

### Post by pytheas22 on 2008-12-21
The port for samba, which is almost definitely what you'd be using to share files between Windows and Ubuntu, is 139.  Try opening that.

---

### Post by urban48 on 2008-12-21
I opened port 139 using ufw but I still cannot see the Windows machine.

I am using the "Network" file browser under Nautilus (Places -> Network -> Windows Network), but I think this is the same as using Samba.

---

### Post by Kevbert on 2008-12-21
What do you get if you enter
```
sudo ufw status
```
It should give you a list of all the rules that have been set up.
Here's more [[COLOR="Red"]info[/COLOR]]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") on ufw.

---

### Post by urban48 on 2008-12-21
```
urban@urban-48:~$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
137/udp                    ALLOW   Anywhere
138/udp                    ALLOW   Anywhere
139/tcp                    ALLOW   Anywhere
445/tcp                    ALLOW   Anywhere
```

After thinking about it, I realized that this only allows other machines to connect to me through these ports. I believe I have to add something to allow my machine to access other machines, so I added this:

```
urban@urban-48:~$ sudo ufw allow from any to any

urban@urban-48:~$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
137/udp                    ALLOW   Anywhere
138/udp                    ALLOW   Anywhere
139/tcp                    ALLOW   Anywhere
445/tcp                    ALLOW   Anywhere
Anywhere                   ALLOW   Anywhere
```

Now I am able to see my windows machine. Does this create a security issue? That is, is allowing access to anywhere from anywhere mean that anyone can access my computer, or does that just mean I can access any computer from any port?

---

### Post by gTinker on 2008-12-21
> **urban48 said:**
> I opened port 139 using ufw but I still cannot see the Windows machine.

I am using the "Network" file browser under Nautilus (Places -> Network -> Windows Network), but I think this is the same as using Samba.

Well you might have to open 137-139 for your LAN subnet, and if it is CIFS instead of SMB you'll probably have to open port 445.

You could try opening them all then closing one at a time to see the minimum you need. I suggest closing ones you don't need.

[edit] Oh, I see you figured it out while I was typing. Only allow from your LAN subnet, those are the only boxes you want to have that access.

---

### Post by urban48 on 2008-12-21
OK, so I believe that this is how ufw should be configured:

```
urban@urban-48:~$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
137/udp                    ALLOW   192.168.1.0/24
138/udp                    ALLOW   192.168.1.0/24
139/tcp                    ALLOW   192.168.1.0/24
445/tcp                    ALLOW   192.168.1.0/24
```

However, I must still be missing a port, because I cannot access the Windows machine on my network. If I change it so that the "To" field contains "Anywhere" (i.e., any port on my machine), I can access the Windows machine. So, there has to be another port that needs to be opened...

---

### Post by gTinker on 2008-12-21
Well, what I see there is in one direction, and you've already determined that you need both directions with that anywhere - anywhere rule you mentioned previously. How about something that allows your box to establish connections to the other boxes on the subnet?

I can't really be specific about UFW, I use firestarter with outbound permissive.

---

### Post by urban48 on 2008-12-21
Perhaps I should give firestarter a try.

---

### Post by gTinker on 2008-12-21
No reason why what you want to do couldn't work with UFW, it's just that I can't give you definitive instructions for it. Someone else here will be along to do so, probably soon.

For me it's just a matter of choice of what I'm familiar with.

You will find people here who are against using Firestarter and we don't want a flame war.

How about something like to anywhere in your subnet from your box?

---

### Post by jfernyhough on 2008-12-21
You could try installing GUFW to make configuration easier. It even has built-in options for various services (though not samba, annoyingly).

Anyhow, I have my box open to my local network.

ALLOW To Anywhere From 192.168.0.0/24

---

### Post by urban48 on 2008-12-21
Thanks for all the replies. I ended up just allowing access to any port on my computer only from machines on my local network (just like jfernyhough said) and everything is working fine. That should allow sufficient firewall protection while enabling local networking.

---

