---
title: "firewall"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by ANew on 2009-02-02
Please advise what firewall will be better to install.

Which one is free and with graphical interface? I am not that
experienced in linux to configure iptables.

Thank you

---

### Post by timcredible on 2009-02-02
well, what are you trying to accomplish?  by default, there are no ports open on ubuntu, so there's nothing to firewall unless you run it as a server.  if you have server ports open (http, telnet, ssh, etc.), then guarddog is a gui frontend for iptables.

---

### Post by samiam24 on 2009-02-02
[http://www.pfsense.org/](http://www.pfsense.org/)
[http://www.ipcop.org/](http://www.ipcop.org/)
[http://www.smoothwall.org/](http://www.smoothwall.org/)

there are more out there but the above are the more well known ones.  I have been using ipcop for the last 3 years with no issues, I have Zerina (openvpn) and cop+ (dansgaurdian) installed. 

I have been thinking about moving over to Pfsense.

They are all free and use a web gui.
IPcop was the 1st time I ever used Linux

---

### Post by ANew on 2009-02-02
> **timcredible said:**
>   by default, there are no ports open on ubuntu, so there's nothing to firewall 

i did not know that. the only thing which bothers me a little bit:
when i switch on the wireless i see some odd networks: blacktshirt,
apple network, etc. I do not see those networks in Windows, but in ubuntu
they show at full strenth. what is it? why they appear only in ubuntu?

---

### Post by OrangeCrate on 2009-02-02
If you're new to Ubuntu, this is a great site to read and bookmark. In this particular case, the page on Ubuntu Security...

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by tpfkanep on 2009-02-04
> **timcredible said:**
> well, what are you trying to accomplish?  by default, there are no ports open on ubuntu, so there's nothing to firewall unless you run it as a server.  if you have server ports open (http, telnet, ssh, etc.), then guarddog is a gui frontend for iptables.
1. Is there a way to scan my system to see which ports are open? I have xubuntu installed. 
2. How do I 'close' the ports?

I am also using Network Manager 0.7 with a cell phone connected via USB to access the internet.

---

### Post by OrangeCrate on 2009-02-04
> **tpfkanep said:**
> 1. **Is there a way to scan my system to see which ports are open?** I have xubuntu installed. 
2. How do I 'close' the ports?

I am also using Network Manager 0.7 with a cell phone connected via USB to access the internet.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by tpfkanep on 2009-02-04
**[File sharing]**Passed!

**[Common ports]**Passed!

Please explain this to me:
**[All service ports]**

A grid of squares is shown (I think they represent the ports?). All of the squares are green (stealth), except one, which is blue (closed). I get one failed entry:> Solicited TCP Packets: RECEIVED (FAILED) &#8212; As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.

This is the text summary:
> GRC Port Authority Report created on UTC: 2009-02-04 at 15:20:18

Results from scan of ports: 0-1055

    0 Ports Open
    1 Ports Closed
 1055 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

The port found to be CLOSED was: 1

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

I do not know how to fix this... please help.

---

