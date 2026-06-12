---
title: "Linux mint security issue. Weird firewall results from shields up."
date: 2019-06-03
forum: MINT
---

### Post by mark284 on 2019-06-03
Hey there fellow Linux friends. I was a Ubuntu user but I now am running Linux Mint 18 Mate 64 on my dell laptop. Anyways I went on the shields up website and I did their firewall test with scanning the first main 1000 ports. It 
says on the site that port 22 and port 23 are opened, everytime I scanned it says open. I tried netstat and nothing seems fishy with that. Here is my netstat results as I am posting this, 

netstat -lntup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1623/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3280/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      3280/cupsd      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           973/avahi-daemon: r
udp        0      0 0.0.0.0:40037           0.0.0.0:*                           1623/dnsmasq    
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1623/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           4852/dhclient   
udp        0      0 192.168.0.12:123        0.0.0.0:*                           1229/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1229/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1229/ntpd       
udp        0      0 0.0.0.0:57897           0.0.0.0:*                           973/avahi-daemon: r
udp        0      0 0.0.0.0:631             0.0.0.0:*                           3281/cups-browsed
udp6       0      0 :::5353                 :::*                                973/avahi-daemon: r
udp6       0      0 :::54884                :::*                                973/avahi-daemon: r
udp6       0      0 fe80::c15b:4da3:ff3:123 :::*                                1229/ntpd       
udp6       0      0 ::1:123                 :::*                                1229/ntpd       
udp6       0      0 :::123                  :::*                                1229/ntpd       


So I am not a expert with all of this, but I don't see port 22 and port 23 opened, but maybe I'm not using netstat right or this is a false positive. Is there other ways to check and make sure my computer is OK ? Also doesn't Linux have a built in firewall to prevent this result from Shields up ? Thanks.

---

### Post by coffeecat on 2019-06-03
*Thread moved to Mint sub-forum*.

---

### Post by kpatz on 2019-06-03
If you're behind a router, shields up would be scanning that and not your Mint box.

If it's your own router, I would check your router for firmware updates, and disable any remote access management features on it.  Having ports 22 and 23 open on a router is asking to be pwned.

If it's an ISP provided router, then it's a moot point.  Hopefully they keep it updated.

---

### Post by mark284 on 2019-06-03
Hey Kpatz, thanks for the answer. I am behind a modem/router that was provided by my ISP like 4 months ago. It says scanning my IP address so I guess youre right it is scanning my modem. If my Linux firewall is keeping those ports closed, then should it not be a problem ? Also I have setup a username and password on the modem.

---

### Post by mark284 on 2019-06-03
OK so I tried everything I can so far. I rebooted the modem/router, I unchecked the Telnet and SSH options in the modems menu under both WAN and LAN. I am going to give my ISP a call in 3 days when im off from work to take care of this. It says on shields up that having this port open is exactly what hackers look for. Should I not be to worried since the Linux software firewall is running, I think it's iptables ? also I see nothing when I check netstat. Or are other people who are using windows on my network in more trouble ? also Android tablets on the network, smart TV's etc..

---

### Post by TheFu on 2019-06-03
22/tcp is usually ssh.
23/tcp is usually telnet.
If you don't have those enabled on your systems then I wouldn't worry.  You can check the process table for either:
```
ps -eaf|grep ssh
```
is an example. Something similar for telnet.

Having iptables really doesn't mean much.  If you didn't specifically configure it, then it is useless.  On Linux, you must configure the firewall for it to do anything.  The idea that there are "reasonable defaults" applies to grandma OSes.  If you want something to work on Linux, expect to
a) install is
b) configure it
c) tell the startup manager (there are 10 of these) that you want it started at reboot or login or at some other point, perhaps dependent on some other item. For example, starting a configured set of firewall rules before networking is up doesn't work.  Networking needs to be up, then firewall rules can be applied.

As others have said, if the router is controlled by the ISP, then there isn't much you can do to alter those settings.  ISPs don't configure 1 router at a time. They configure 10,000-50,000 at a time, probably nightly.  

When it comes to security, having multiple layers is the game, so when 1 layer fails, your system isn't compromised.

All my systems have ssh running, but only a few have ports forwarded from the internet inside to reach those computers.  None of my systems have telnet or FTP.  I consider both of those as dead protocols since 1995. Unless there is a very specific purpose, having either of those unencrypted protocols on your network would be a terrible idea.  

Your ISP should be embarrassed.  Back when I had to use shared web hosting, when I found that a company allowed telnet or plain FTP, that was reason enough to cancel. I didn't want anything to do with a company that foolish as to  allow clients to login over protocols that don't use **any** encryption. It isn't just foolish, stupid, dumb - it is **negligent** and has been for about 20 yrs.

---

### Post by mark284 on 2019-06-03
I am not that computer savy. I am more like a beginner to mid level skill with computers. I have helped people with average problems. Is my computer safe with the info I have provided ? 
I was sure that Linux has a built in firewall that uses protection as a backup. I tried to open iptables to check status and I get this. 


Dell ~ # service iptables status
&#9679; iptables.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
Dell ~ # sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     



Is the firewall doing what it should ? I also did a rkhunter scan and everything is green and perfect. No malicious software, no backdoors, no open ports etc... here it is everything here was in green. 


Checking the network...

  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]
    Checking for hidden ports                                [ Skipped ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for an SSH configuration file                   [ Not found ]
    Checking for a running system logging daemon             [ Found ]
    Checking for a system logging configuration file         [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]


I'm trying to see if my PC was hacked due to these 2 open ports on my network. Here is the result of the command you told me to post 

ps -eaf|grep ssh
mint      1507  1351  0 11:32 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch mate-session
mint     22802 22782  0 18:06 pts/0    00:00:00 grep --color=auto ssh


I do see SSH-agent in my processes tab in system monitor.

---

### Post by TheFu on 2019-06-03
We were all beginners at some point. The way to get passed that stage is to lookup every command you see, read about it, review the manpage about it and try to understand what it really says in the output.

> Having iptables really doesn't mean much. If you didn't specifically configure it, then it is useless. On Linux, you must configure the firewall for it to do anything. The idea that there are "reasonable defaults" applies to grandma OSes. If you want something to work on Linux, expect to
a) install is
b) configure it
c) tell the startup manager (there are 10 of these) that you want it started at reboot or login or at some other point, perhaps dependent on some other item. For example, starting a configured set of firewall rules before networking is up doesn't work. Networking needs to be up, then firewall rules can be applied.

No. iptables isn't configured.
No. iptables hasn't been setup to automatically start, at least from what I can see.
No. iptables isn't doing anything to protect your system.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Windows computer skills DO NOT translate to Linux/Unix. Sorry. Learning Unix is like learning to speak another language.

rkhunter isn't very useful either, BTW. When the signatures get out of date and you begin seeing 5, 10, 15, 20, 50, 100 false positives, you'll understand.

There is a sticky thread at the top of the Ubuntu Forums "Security" forum. Probably best to review those, follow the links they provide, review those links as much as needed.

A good beginning text on Linux: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Learn a chapter every week and in just a few months the connections between the different commands will really start to snowball.

---

### Post by mark284 on 2019-06-04
So what do I do, since my computer is exposed at port 22 and port 23 ?  What GUI firewall would you recommend or do I even need a firewall ? I have SSH-agent running, but netstat has not shown port 22 and 23 used. 
Also does it help that my home folder is password protected and locked ? I seriously do not understand lots of this stuff and I was told many times that Linux has a built in firewall protecting things called iptables. I want to get a GUI firewall that can maybe monitor all connections ( better than netstat ) and do some investigating. 

If someone is using Linux on a PC that connects to a older modem with no hardware firewall built in, that means they are screwed, since all ports are open ? I am really confused here.

---

### Post by mark284 on 2019-06-04
Here is my current netstat settings. I think something on port 8009 is suspicious. I'm all paranoid due to all the passwords I have on my computer. It seems like I have been running Linux without a firewall for years. 

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.12:54542      192.168.0.14:8009       ESTABLISHED
tcp        0      0 192.168.0.12:52294      23.77.240.17:443        ESTABLISHED
tcp        0      0 192.168.0.12:48586      149.28.200.96:443       ESTABLISHED
tcp        0      0 192.168.0.12:60308      198.252.206.25:443      ESTABLISHED
tcp        0      0 192.168.0.12:32904      149.28.193.225:443      ESTABLISHED
tcp        0      0 192.168.0.12:46152      192.168.0.23:8009       ESTABLISHED
tcp        0      0 192.168.0.12:37650      192.168.0.14:8008       ESTABLISHED
tcp        0      0 192.168.0.12:42884      34.210.113.231:443      ESTABLISHED
tcp6       0      0 ::1:631                 :::*                    LISTEN     


port 8009 is making connections on my network and thats what concerns me. The only firewall I've had is the hardware firewall.

---

### Post by Rubi1200 on 2019-06-05
Hi,

can you show us the output of the following commands please:

```
netstat -ltnp | grep -w ':8009'
```

and

```
lsof -i :8009
```

Thanks.

---

### Post by mark284 on 2019-06-05
Here it is. 

mint@Dell ~ $ sudo bash
Dell ~ # sudo netstat -ltnp | grep -w ':8009'
Dell ~ # lsof -i :8009
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
chromium- 1395 mint   37u  IPv4 401997      0t0  TCP 192.168.0.12:54542->192.168.0.14:8009 (ESTABLISHED)
chromium- 1395 mint   38u  IPv4 402018      0t0  TCP 192.168.0.12:46152->192.168.0.23:8009 (ESTABLISHED)



Looks like this is just Chromium which I am using with a VPN and maybe that has something to do with it or there might be some things I don't understand yet. I read a Ubuntu 
page talking about iptables and security. The reason why the firewall is disabled is to have things running and connecting without hassle like Samba and printers. Also since Linux 
keeps the ports closed to the outside world unless running servers, things should be fine. This all started because my ISP modem/router has port 22 and 23 wide open.

---

### Post by Rubi1200 on 2019-06-05
I can't answer all your questions. For the high-level firewall/security matters you need to wait for someone like TheFu or kpatz because they really know this stuff.

What I can tell you is create a file with useful commands saved for reference, like lsof for example.

Then you can check things that seem unfamiliar or suspicious and can post it here in this thread or a new thread depending on what is going on.

This page has more on commands to track down which processes are using ports:
[https://www.tecmint.com/find-out-which-process-listening-on-a-particular-port/](https://www.tecmint.com/find-out-which-process-listening-on-a-particular-port/)

In the context of the current question, I think you answered that yourself already. Chromium is using that port. By the way, your output also showed something on port 8008 and you may want to check that as well.

---

### Post by mark284 on 2019-06-05
I just did a test to check port 22 and 23. 
Dell ~ #  netstat lsof -i :22
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
enp3s0     1500 0         0      0      0 0             0      0      0      0 BMU
lo        65536 0      5892      0      0 0          5892      0      0      0 LRU
wlp1s0     1500 0   1992418      0      0 0        726583      0      0      0 BMRU
Dell ~ # netstat lsof -i :23
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
enp3s0     1500 0         0      0      0 0             0      0      0      0 BMU
lo        65536 0      5894      0      0 0          5894      0      0      0 LRU
wlp1s0     1500 0   1993053      0      0 0        726690      0      0      0 BMRU


I checked port 8008 and it is also chromium. I hope the recent result is also fine. I am going to reinstall Linux mint, make a better user password and install a GUI firewall, but I still need to run some tests on this OS. I am going to 
call my ISP to question them on why those 2 network ports are open on their modem.

---

### Post by Rubi1200 on 2019-06-05
Mint (at least Cinnamon version) already has a GUI for the firewall installed by default, though not enabled.

Search for gufw in the menu.

If not, you can install from the repositories.

It is relatively easy to use but if there are any questions ask here.

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by mark284 on 2019-06-05
Yeah I just noticed it and I will enable it on my next install, it was disabled when I opened it.

---

### Post by Morbius1 on 2019-06-05
> I have SSH-agent running, but netstat has not shown port 22 and 23 used. 
SSH-agent is client side. It's invoked when you try to connect to an SSH server not if another computer wants to connect to you. It's there because openssh-client is installed by default so that you as a client can access an SSH server.

I would be willing to bet the farm that you aren't running the SSH server because you have to install it explicitly. 

Run this command:
```
sudo service ssh status
```
Does it come back with "Loaded: not found" and "Active: ( inactive ) dead"

---

### Post by TheFu on 2019-06-05
It never hurts to look things up, but I seriously doubt port 22/tcp and 23/tcp are forwarded to any of your systems inside.  They are probably open just to the modem so the ISP can manage settings there without having to reboot and use tftp to push new settings.  Port 23/tcp is embarrassing to have enabled by an ISP, IMHO.

I don't use GUI interfaces to the Linux firewall. Cannot recommend any.

I won't have google-chrome on my systems. Why would they have anything on non-standard ports like 8008-8009?
```
192.168.0.12:54542->192.168.0.14:8009
```
is between 2 internal systems. Have you setup remote streaming?  What sort of devices are both those IPs?  I'd guess .12 is your Mint system.  What is .14?

When posting command output, please use code tags so the output lines up in columns. Too hard to read otherwise.

```
$ netstat lsof -i :22
```
What is the point of this?  netstat is 1 command.  lsof is a completely different command. They are used separately. lsof usually requires sudo or it doesn't have access.  The command is:
```
$ sudo lsof -i :22
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd    1800 root    3u  IPv4  28725      0t0  TCP *:ssh (LISTEN)
sshd    1800 root    4u  IPv6  28727      0t0  TCP *:ssh (LISTEN)
```
My system is running openssh-server and has a daemon listening on IPv4 and on IPv6 addresses.

---

### Post by kpatz on 2019-06-05
> **mark284 said:**
> Here is my current netstat settings. I think something on port 8009 is suspicious. I'm all paranoid due to all the passwords I have on my computer. It seems like I have been running Linux without a firewall for years. 

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.12:54542      192.168.0.14:8009       ESTABLISHED
tcp        0      0 192.168.0.12:52294      23.77.240.17:443        ESTABLISHED
tcp        0      0 192.168.0.12:48586      149.28.200.96:443       ESTABLISHED
tcp        0      0 192.168.0.12:60308      198.252.206.25:443      ESTABLISHED
tcp        0      0 192.168.0.12:32904      149.28.193.225:443      ESTABLISHED
tcp        0      0 192.168.0.12:46152      192.168.0.23:8009       ESTABLISHED
tcp        0      0 192.168.0.12:37650      192.168.0.14:8008       ESTABLISHED
tcp        0      0 192.168.0.12:42884      34.210.113.231:443      ESTABLISHED
tcp6       0      0 ::1:631                 :::*                    LISTEN     


port 8009 is making connections on my network and thats what concerns me. The only firewall I've had is the hardware firewall.Run **sudo netstat -ntup** so we get PIDs and process names.

I'm curious what chromium is connecting to on port 8008 and 8009.  What are 192.168.0.23 and 192.168.0.14?  What extensions are you running on chromium?

The netstat output you've given so far seems to indicate that ports 22 and 23 aren't open on your Ubuntu box.  The router has them open for its own management features, that's the ISP's job to keep those secure and patched.

---

### Post by Rubi1200 on 2019-06-05
> **mark284 said:**
> 
Looks like this is just Chromium which I am using with a VPN and maybe that has something to do with it or there might be some things I don't understand yet.

OP mentioned he is using a VPN, though which one we do not know. (Sorry, just wanted to point this out in case it makes a difference).

---

### Post by TheFu on 2019-06-05
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.12:54542      192.168.0.14:8009       ESTABLISHED
tcp        0      0 192.168.0.12:52294      23.77.240.17:443        ESTABLISHED
tcp        0      0 192.168.0.12:48586      149.28.200.96:443       ESTABLISHED
tcp        0      0 192.168.0.12:60308      198.252.206.25:443      ESTABLISHED
tcp        0      0 192.168.0.12:32904      149.28.193.225:443      ESTABLISHED
tcp        0      0 192.168.0.12:46152      192.168.0.23:8009       ESTABLISHED
tcp        0      0 192.168.0.12:37650      192.168.0.14:8008       ESTABLISHED
tcp        0      0 192.168.0.12:42884      34.210.113.231:443      ESTABLISHED
tcp6       0      0 ::1:631                 :::*                    LISTEN     
```
Much easier to read, yes?  code tags matter.

Hopefully, it isn't one of those browser-only VPNs.  Would need to see the routing table and network device list to know anything about the VPN.

---

### Post by mark284 on 2019-06-06
Yes guys I am running a VPN on my chromium, I also have one on Opera. It's a browser add on VPN that I pay for. I am not sure which devices these are on my network because this new modem doesn't show the names like the other one did. Why is chromium connecting to these addresses I don't know. I assume its normal.

I just did the command for port 8009 and I got this. 
lsof -i :8009
COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
chromium-  8524 mint   36u  IPv4 116476      0t0  TCP laptop:44368->192.168.0.14:8009 (ESTABLISHED)
chromium-  8524 mint   40u  IPv4 123861      0t0  TCP laptop:44616->192.168.0.14:8009 (ESTABLISHED)
chromium-  8524 mint   45u  IPv4  91714      0t0  TCP laptop:44128->192.168.0.14:8009 (ESTABLISHED)
chromium-  8524 mint   48u  IPv4 186217      0t0  TCP laptop:45378->192.168.0.14:8009 (ESTABLISHED)
chromium-  8524 mint   53u  IPv4 191261      0t0  TCP laptop:33350->192.168.0.23:8009 (ESTABLISHED)
opera     10008 mint  173u  IPv4 191306      0t0  TCP laptop:33352->192.168.0.23:8009 (ESTABLISHED)
opera     10008 mint  177u  IPv4 119109      0t0  TCP laptop:44378->192.168.0.14:8009 (ESTABLISHED)
opera     10008 mint  182u  IPv4 123859      0t0  TCP laptop:44612->192.168.0.14:8009 (ESTABLISHED)
opera     10008 mint  188u  IPv4 188055      0t0  TCP laptop:45374->192.168.0.14:8009 (ESTABLISHED)

I reinstalled Linux mint. I have Opera and Chromium running at the same time using the same VPN company that I use. This looks like normal proxy VPN activity to me. I have the Firefox browser without the VPN on and it shows no activity like this, it's only the VPN browsers.

I did log in to my modem and 192.168.0.23 and 192.168.0.14  is online and I have no idea which device it is or why the VPN is connecting to those devices. I have a downstairs neighbour and I assume it might be one off his devices which are a desktop computer and a laptop. I assume this is normal, especially since I just reinstalled mint, setup a GUFW firewall and locked the computer with more passwords.Maybe the VPN is just bouncing off other connections on the network, but that is just a guess.

---

### Post by mark284 on 2019-06-07
Yes it is the browser VPN, virtualshield.

---

### Post by mark284 on 2019-06-09
OK it seems like those 2 browsers are connected to the Vizio smart TV and a basement speaker connected to my internet network. I go on youtube and youtube says that the cast is available to show what I'm watching on youtube, even though I'm using a VPN. I don't want someone having access to what I'm watching on youtube. It was both Chromium and Opera that popped up saying I can use casting and not firefox. Its pretty much impossible to have privacy even with VPN's, firewalls and Linux. I didn't connect to the cast option for those 2 devices, because I think it will just bypass the VPN's protection. I would just rather not have my computer communicating with these devices. I assume that I manually have to connect to the cast option on that TV thats connected to my network.

---

### Post by TheFu on 2019-06-09
```
sudo ufw deny from {IP of the Vizio}
```
Assuming you are using ufw already.

Trying to hide what you do on youtube is like trying to avoid raindrops, in a downpour, at a nudist beach, with nothing else around for 5 kms.  Can't be done.

I use chromium, but only in a restricted jailed environment and only for non-local purposes.  When Opera was sold to a different company, I stopped using it over privacy considerations.  I use full, trusted, paid, VPNs, not tied to the browser.  Not all VPNs are equal.  I also put my chromecast into a drawer when it became clear what the true purpose was for that device. I couldn't bring myself to sell it to someone else.

BTW, most commercial VPNs will specifically allow local subnet access, since most people would like to have the VPN allow them to print and access local LAN shared resources.  If you don't run the VPN, I don't think you get to control the routes to limit the local LAN.

---

### Post by mark284 on 2019-06-12
Sorry for the late reply. 
 
Still it seems like the browsers are the ones doing this and not the VPN. I will take your advice and delete Opera. I will just use Firefox for my normal day to day personal stuff and I will use Chromium to post and talk trash on youtube and watch videos. The 2 ports are still open, but I open the GUI firewall when I start up. Also sometimes my wifi disconnects and when I go into the network tab, it shows that the Vizio and basement speaker as available in the Wifi menu and then after 1 minute it goes away, connects back and shows the normal access points available. That has been going on the past month. All of this TBH has been going on the past month and i do not trust chromecast either, so I would never cast with it. I will get Nord VPN to install in Linux and add a Chromium browser VPN. The only reason I use VPN browser extensions is due to the company not having a Linux version VPN.

The firewall I have is the GUI version of UFW. If I put that command in, Is it permanent or do I have to punch it in everyday or can I block it with the GUI version ? I see Opera is bought out by some Chinese company, but the good thing is they wont understand what I'm writing. Nah I get why you wouldn't trust them, you can't trust anything. Firefox and Chromium are open source and that is the most trustworthy. Privacy is dead, however you can try to improve it. Thats why I got a VPN.

---

