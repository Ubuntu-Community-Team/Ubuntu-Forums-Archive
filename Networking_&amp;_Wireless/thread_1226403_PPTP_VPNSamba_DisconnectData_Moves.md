---
title: "PPTP VPN/Samba Disconnect/Data Moves"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by bsntech on 2009-07-29
Hi folks,

I've recently moved back into Ubuntu for some testing to try to go more mainstream with a desktop OS.  I'm using Ubuntu on my web servers currently and it is working out well.

Well, let's cut to the chase.  I got the PPTP VPN through NetworkManager working just fine.  I can connect up to the PPTP VPN server I have on a DD-WRT router.

Here's the problem - anytime I begin to try to transfer/delete or do any kind of file operation over a Samba share from the desktop to another PC on the VPN network, the VPN dies and says that the VPN failed.

In addition, I've noticed that if I open a web page through the VPN connection on a server and input any kind of data - an e-mail address, fill out a text form, etc - the VPN also disconnects as well.

I tried to manually configure a vpn connection and use the pon and poff commands, but the same exact thing happens as well.  I'll create the connection, open the Samba share in Nautilus - which works fine and shows the contents of the share, but the moment that file operations start (delete, copy, etc), the VPN connection dies.

I don't recall this ever being a problem in Gusty or previous versions - back when I used Kvpnc to connect.

I also tried Kvpnc and the problems are even worse with it.  Even after setting up the route, there is at least 75% packet loss with Kvpnc when doing a ping.

When using NetworkManager or creating the connection manually using pon/poff, there is 0% packet loss when doing a ping.

Now as a point of success, I am able to SSH into servers and do command-line items through the VPN.  I can even use Midnight Commander (MC) to pull up the full syslog on a server.

But, still Samba and entering forms across web pages in the VPN will disconnect.  Lastly, sometimes even when using the Terminal Services Client to connect to PCs on the VPN, it also terminates the connection.

---

### Post by bsntech on 2009-07-29
Also - I would like to note the following in the syslog when the connection is dropped:

```
Jul 29 14:26:34 Desktop pptp[17092]: nm-pptp-service-17086 warn[decaps_gre:pptp_gre.c:331]: short read (-1): Message too long
Jul 29 14:26:34 Desktop pptp[17101]: nm-pptp-service-17086 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jul 29 14:26:34 Desktop pptp[17101]: nm-pptp-service-17086 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jul 29 14:26:34 Desktop pptp[17101]: nm-pptp-service-17086 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jul 29 14:26:34 Desktop pppd[17089]: Modem hangup
```

---

### Post by bsntech on 2009-07-29
OK - I think I may have resolved my own issue.

Unforuntately, I do believe there is a bug in the NetworkManager.  There should be a setting where we can change the MTU and MRU.

By doing it through the pon/poff way, I was able to change the MRU and MTU to 1250 each.  After doing so, I was able to move files/delete files through Samba and the web pages worked just fine.

I created a file in the /etc/ppp/peers folder and put the following items in it:

```
pty "pptp REMOTE_HOST  --nolaunchpppd"
name admin
remotename PPTP
file /etc/ppp/options.pptp
ipparam FILENAME
mru 1250
mtu 1250
```

REMOTE_HOST is the IP/DNS name of the server I connected to and FILENAME is the name that this file is saved as.  I played around with the MRU/MTU but 1250 seems to be the highest I could attain.  MTU/MRU of 1200 also worked, but the moment I tried 1275, the VPN disconnects.

I just made some scripts in my panel to automatically run/stop the VPN and also setup the route:


To make the connection (must be run as sudo):
```
pon FILENAME
sleep 10
route add -net 192.168.254.0/24 dev ppp0
sleep 3

```

To break the connection (must be run as sudo):
```
poff FILENAME
```

where FILENAME is the name of the file that you created in the /etc/ppp/peers folder with the configuration above.

Also note that you need to put your username/password for this connection in the /etc/ppp/chap-secrets file:

```
USERNAME     PPTP     PASSWORD     *
```

where USERNAME and PASSWORD are replaced with the username/password for the connection.

You may also need to modify your options file (/etc/ppp/options.pptp).  The default file worked for me without mppe encryption and using chap-2 for authentication.

---

