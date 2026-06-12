---
title: "wireless on dell studio 1558"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by goslar on 2010-06-01
Hi:
it worked ("dell 1501 wireless" - broadcom-based, lucid amd64, 2.6.32-22) and now it doesn't. Very funny.
It initially required installation of the "STA" driver (system|administration|hardware drivers) and it still shows "activated and currently in use"). It allows me to select my wpa network. But since yesterday, instead of establishing the connection, I will be prompted to re-enter the WPA key, which has not changed.
Any ideas, anyone?
ANYONE?
Thanks in advance.
From /var/log/syslog:
May 31 20:31:43 s1558 wpa_supplicant[1436]: WPA: Could not verify EAPOL-Key MIC 
- dropping packet
May 31 20:31:53 s1558 wpa_supplicant[1436]: last message repeated 5 times
May 31 20:31:53 s1558 wpa_supplicant[1436]: Authentication with 00:14:51:6f:07:6b timed out.
May 31 20:31:53 s1558 NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
May 31 20:31:53 s1558 NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May 31 20:31:53 s1558 wpa_supplicant[1436]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
May 31 20:31:53 s1558 NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
May 31 20:31:59 s1558 NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May 31 20:32:02 s1558 NetworkManager: <info>  eth1: link timed out.
May 31 20:32:04 s1558 wpa_supplicant[1436]: Trying to associate with 00:14:51:6f:07:6b (SSID='XXX' freq=2442 MHz)
May 31 20:32:04 s1558 wpa_supplicant[1436]: Association request to the driver failed
May 31 20:32:04 s1558 NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
May 31 20:32:05 s1558 NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
May 31 20:32:05 s1558 wpa_supplicant[1436]: Associated with 00:14:51:6f:07:6b
May 31 20:32:05 s1558 NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
May 31 20:32:05 s1558 wpa_supplicant[1436]: WPA: Could not verify EAPOL-Key MIC - dropping packet

---

### Post by Jest3r on 2010-06-08
I have the same hardware, and experiencing the same problems.

If i can work out a solution, I'll let you know.

---

### Post by fanny4545ff on 2010-06-08
hello,
        Can you tell me what is the wireless on dell studio and what is the benefits of this studio.         
                   thanks

---

### Post by goslar on 2010-06-08
Killing and re-starting nm-applet (several times) may help in establishing a connection. At other times, connection is established with no problems/intervention at all.
Possibly related to [https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777)

---

### Post by IBUA on 2010-06-08
I think I have a fairly similar problem with the Studio 1555.

However B43-fwcutter works for about 60seconds then dies.
The STA driver doesn't even search for anything :(

---

### Post by goslar on 2010-06-08
Similar, but likely not the same. In my case I can at least display and select from a list of networks, using the STA driver. Reliable connection is another matter. Once/if a connection has been established, I did not yet experience one dying on me.

---

### Post by alnixx on 2010-07-09
same here. I am using Dell studio 1558. The wireless worked fine but I got disconnected and I was asked for username and password again and again with no successful connection establishment. 
When I use the live CD, the wireless network worked fine. I will try restarting the nm-aplet.

---

