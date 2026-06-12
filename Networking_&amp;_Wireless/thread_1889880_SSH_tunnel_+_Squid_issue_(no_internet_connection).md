---
title: "SSH tunnel + Squid issue (no internet connection)"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by rufinus on 2011-12-02
Hello All,

here is my strange issue, which i try to solve already several days.
Configuration: 

**Home server** - running ubuntu, apache server, internal network IP 192.168.0.100, SSH enabled, router is forwarding ssh port (2022).

**Remote PC** - running windows, putty (SSH --> home server).

**Putty settings** and **squid.conf**: please see attached

**Firefox setting**: host SOCKS 5, 127.0.0.1:8080

**_Problem description_**: i am able to connect to home server using Putty, also WinSCP works well. 
But the tunneling of internet connection does not work at all! Firefox just says "Connecting to (address here)" and after some time just times out. 
Strangely enough, access log of squid is empty, looks like sshd somehow is not forwarding the information to squid.

Putty seem to establish tunnel connection:

2011-12-02 14:03:31	Opened channel for session
**2011-12-02 14:03:31	Local port 8080 forwarding to localhost:8080**
2011-12-02 14:03:31	Allocated pty (ospeed 38400bps, ispeed 38400bps)
2011-12-02 14:03:31	Started a shell/command

For me it looks like sshd somehow does not communicate with squid. And the most strange situation, that the tunneling worked for about 5 days, and then suddenly stopped!

---

### Post by collisionystm on 2011-12-02
> the tunneling worked for about 5 days, and then suddenly stopped!

okay so lets assume there is nothing wrong with your remote-pc.

can your squid server access the internet? can you ping google.com ?

have you checked your iptables?

---

### Post by rufinus on 2011-12-02
Wow, thanks for rapid reply. 
Ping works, Lynx bowsing as well. 
Abot IP tables, i attached the output of sudo iptables -L.
Also UFW is disable for now, untill i find a solution.

---

### Post by rufinus on 2011-12-02
And here is output of iptables -L with ufw enabled. But anyway, the problem persists in both cases.

---

### Post by collisionystm on 2011-12-02
So you are running a setup I am not exactly familiar with. You are using an SSH tunnel from your windows PC back to your server at home?

Did you set your proxy settings in your web browser?

---

### Post by rufinus on 2011-12-02
> **collisionystm said:**
> So you are running a setup I am not exactly familiar with. You are using an SSH tunnel from your windows PC back to your server at home?

Did you set your proxy settings in your web browser?

1) Yes. I also tried it from inside the home network, from my home PC, with exactly the same negative result as from remote PC. So for home server it does not matter feom where i tunnel, from inside the home range or from outside somwhere.

2) Yes, as i mentioned in the first post:
**Firefox setting**: host SOCKS 5, 127.0.0.1:8080

---

### Post by collisionystm on 2011-12-02
could the windows firewall be causing the problem? have you tried to disable it?

sorry, all I can do at the moment is throw you ideas lol.

---

### Post by rufinus on 2011-12-02
Well, firewall settings did not change, and it was working before. 
Disabling firewall on remote machine does not help, same on internal PC.

I attached a little diagram with network setup, maybe it will help somehow.

---

### Post by collisionystm on 2011-12-02
install curl on your server and run an nmap to see if the port is listening

sudo apt-get install curl

sudo apt-get install nmap

nmap -P0 $(curl [www.whatismyip.org](www.whatismyip.org))

---

### Post by collisionystm on 2011-12-02
scratch that

just install nmap

nmap localhost


i forgot you are behind a router... woops! Oh well, maybe you can find a future use out of it

---

### Post by rufinus on 2011-12-02
Installed, scanned.

**nmap localhost:**

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-12-02 16:53 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0016s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
Not shown: 992 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
2022/tcp  open  down
3306/tcp  open  mysql
8080/tcp  open  http-proxy
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.28 seconds

Seems to be ok, 8080 is open.

---

### Post by collisionystm on 2011-12-02
> **rufinus said:**
> Installed, scanned.

**nmap localhost:**

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-12-02 16:53 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0016s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
Not shown: 992 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
2022/tcp  open  down
3306/tcp  open  mysql
8080/tcp  open  http-proxy
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.28 seconds

Seems to be ok, 8080 is open.


I dont see ssh

---

### Post by collisionystm on 2011-12-02
edit your sshd_config file and change its port to whatever you want it to be

/etc/ssh/sshd_config

---

### Post by rufinus on 2011-12-02
2022/tcp open down

that is my  SSH, i run it on this non-standard port, just for safety.

---

### Post by Doug S on 2011-12-02
It does seem odd that it used to work and now it doesn't. As collisionystm said earlier
> sorry, all I can do at the moment is throw you ideas lol. 
Based on all you have listed, this one seems very unlikely, but I'll say it anyhow: Be sure that ssh TCPforwarding is not disabled in your sshd_config file. It defaults to allowed, if the directive is missing. Check for a line with "AllowTcpForwarding no" and either comment it out or delete it or set it to "yes". For me recently (and because I stupidly forgot that I had it disabled) it was completley not obvious that was the problem.
 
Another idea (which also seems unlikely for your case) is that I have found the order of things matters. I mean I have to set up the recieving end of the tunnel first. If I don't then the sending end fills up some small buffer, because the data has nowhere to go yet, and the sending side dies.

---

### Post by rufinus on 2011-12-02
Just checked the sshd_config, there is no line AllowTCPForwarding. Which means, it is enabled.

How could i check, if sshd actually transmits data to squid? And how do i check if squid is able to receive data from internet?

Another info, it stopped working after my little son pulled the plug of the server, so basically after server reboot. Maybe this will help to narrow it down somehow..

---

### Post by Doug S on 2011-12-02
You should be able to use tcpdump or wireshark to determine what is going on at the packet level.

---

### Post by rufinus on 2011-12-03
Installe tshark, running:

sudo tshark -i eth0 -f "tcp port 8080"  **thats where squid listens, shows nothing**

sudo tshark -R "ip.addr == 127.0.0.1" **shows also nothing**

sudo tshark -i eth0 -f "tcp port 2022"  **shows some packets, which is logic, as my SSH is running there**

So it looks like there is nothing arriving at the Squid. SSH is opening a connection from remote PC, but looks like is not actually tunneling packets from remote firefox to squid?

How can i run shark to monitor processes and not ports/addresses? I would then monitor SSHD activity.

---

### Post by rufinus on 2011-12-03
Here is some update: i tried to set the firefox proxy not to SOCKS (over SSH), as usually, but directly to Squid. And it does work perfect, also access log from squid is getting populated. 

Which means that there is an issue with firefox to putty or SSHD to Squid communication.

How does SSHD communicates with Squid? Squid listens on specified port, how does SSHD binds to that port? how can i trace it?

---

### Post by rufinus on 2011-12-03
Issue solved, thanks all, who tried to help.

In case someone encounters similar problem: if you want to create SOCKS proxy, in Putty on the Tunnels page specify the local forwarded port and put radio button on Dynamic.
In firefox specify in the SOCKS line of proxy settings 127.0.0.1:(local forwarded port)

Standard proxy settings are a bit different.

---

