---
title: "OpenVPN Client List"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by jfreak53 on 2012-04-10
I have looked all over for this and not found it.  I am thinking of switching over to OpenVPN for my personal VPN system, to connect me to my local network and such.  Problem being I have not found a GUI interface (or cli for that matter) that gives me the list of client's connected to my VPN.  I have my own server to run my OpenVPN on, so all client's will be connecting to it.  With ubuntu and window's I found how to connect each to my VPN server using network connection's, that's fine.  But I would like to find some sort of GUI kind of like Hamachi's that let's me list client's and if they are connected to my VPN with their IP's.  Is this possible and does anyone know of a software for this?

---

### Post by SeijiSensei on 2012-04-10
What about just grepping the logs as a first cut?  You'll see entries like these:

```
Apr  4 11:21:53 hostname openvpn[6461]: Peer Connection Initiated with xx.xx.xx.xx:19191

```

---

### Post by jfreak53 on 2012-04-10
Yeah that would work, but that would require me to SSH into the server every time I wanted to know who was connected :S, a lot of work instead of opening a GUI that has a list :)

---

### Post by SeijiSensei on 2012-04-10
On the server you could run:

```
sudo tail -f /var/log/messages | grep 'Peer Connection Initiated'
```

and just leave the session open in a window.

---

