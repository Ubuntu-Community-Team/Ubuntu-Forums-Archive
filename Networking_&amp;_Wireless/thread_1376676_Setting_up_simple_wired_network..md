---
title: "Setting up simple wired network."
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Autodave on 2010-01-09
I have 4 machines all hooked up through a wired router.  All machines Run Ubuntu 9.10 and none of them have Winblows on them.  What program can I use to set up file sharing amongst these machines?  I am a relative newbie to Ubuntu, so a GUI program would be great! :-)  However, I can also run from a command line if forced to. :-)

---

### Post by %hMa@?b&lt;C on 2010-01-09
samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Autodave on 2010-01-09
> **jeffc313 said:**
> samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)


I have seen that before, but I thought that was just for sharing with Windows.  I have no Window machines and only wish to swap files between Ubuntu 9.10 machines.  Isn't there a simpler way of doing it than with SAMBA?

---

### Post by Morbius1 on 2010-01-09
Open **Nautilus** > Right click on a folder in your home folder > select **Sharing options** > check off all the boxes > select **create share**.

Just like windows

---

### Post by Autodave on 2010-01-09
> **Morbius1 said:**
> Open **Nautilus** > Right click on a folder in your home folder > select **Sharing options** > check off all the boxes > select **create share**.

Just like windows


OK: I did that on two of the machines.  I made seperate folder on each machine and gave it sharing properties.  But, now, when I go to NETWORK and click on that, I get this message:  UNABLE TO MOUNT LOCATION: Failed to receive share list from server.

I don't use a server: they are all just individual machines.  How do I share files from one to the other?

---

### Post by Morbius1 on 2010-01-09
Oh lord, you knew that would happen, right? Are you using Karmic by any chance?

Let's hope this is something simple. Please post the output of the following commands from one of the machines please:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the machine you're using.*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.

---

### Post by Autodave on 2010-01-09
> **Morbius1 said:**
> Oh lord, you knew that would happen, right? Are you using Karmic by any chance?

Let's hope this is something simple. Please post the output of the following commands from one of the machines please:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the machine you're using.*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.

Before doing that: maybe I am just being dumb or missing something simple.  Do I have to specify one of the machines as the server?  If so, how do I do that?

I did the same thing on both machines: now, when I click on NETWORK on the other machine, that machine shows up, but not the first machine (the one I am typing on righht now).  When I click on NETORK on this machine, I get the message that I posted before.  Does that help any???  And I am using Karmic on both machines.

---

### Post by Autodave on 2010-01-09
> **Autodave said:**
> Before doing that: maybe I am just being dumb or missing something simple.  Do I have to specify one of the machines as the server?  If so, how do I do that?

I did the same thing on both machines: now, when I click on NETWORK on the other machine, that machine shows up, but not the first machine (the one I am typing on righht now).  When I click on NETORK on this machine, I get the message that I posted before.  Does that help any???  And I am using Karmic on both machines.


I started to run the commands you asked me for: when I get to run smbtree, it asks for a password.  I never set up a passowrd for that and my root password doesn't work.  What now?

---

### Post by Morbius1 on 2010-01-09
(1) Both machines are servers and both machines are clients of the other.

(2) The password it's looking for is your login password

---

### Post by Autodave on 2010-01-09
> **Morbius1 said:**
> (1) Both machines are servers and both machines are clients of the other.

(2) The password it's looking for is your login password

Here's what I got when I did waht you asked for:

david@ddesk-ub:~$ net usershare info
[share]
path=/home/david/share
comment=
usershare_acl=Everyone:F,
guest_ok=n

david@ddesk-ub:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
david@ddesk-ub:~$ smbtree
Enter david's password: 
david@ddesk-ub:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
david@ddesk-ub:~$ nmap -sT 127.0.0.1

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-09 17:35 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 997 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.17 seconds
david@ddesk-ub:~$

---

### Post by Morbius1 on 2010-01-09
(1) > nmap -sT 127.0.0.1That's not the right syntax or ip address.

In a terminal type **ifconfig**:. Look for a line that looks like this in the output:

> [COLOR=Blue]inet addr:192.168.0.100[/COLOR]That's your ip address. so the nmap becomes:

**nmap -sT 192.168.0.100/22**

(2) The **smbtree** command had no output? [COLOR=Blue]EDIT: Never mind I saw that smbtree had no output[/COLOR]

---

### Post by Autodave on 2010-01-09
> **Morbius1 said:**
> (1) That's not the right syntax or ip address.

In a terminal type **ifconfig**:. Look for a line that looks like this in the output:

That's your ip address. so the nmap becomes:

**nmap -sT 192.168.0.100/22**

OK: here's what I got:

david@ddesk-ub:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:90:4c:30:5b  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe4c:305b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4733424 (4.7 MB)  TX bytes:286187 (286.1 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:237036 (237.0 KB)  TX bytes:237036 (237.0 KB)

david@ddesk-ub:~$ nmap -sT 192.168.2.101

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-09 18:37 EST
Interesting ports on 192.168.2.101:
Not shown: 998 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.24 seconds


(2) The **smbtree** command had no output? [COLOR=Blue]EDIT: Never mind I saw that smbtree had no output[/COLOR]


I also turned off the firewall and now I can see this machine, but I do not see the other machine.  Am I doing something else wrong? :-)

---

### Post by Morbius1 on 2010-01-09
(1) Please copy and paste the command below into your terminal, hit enter, and post the output: ```
nmap -sT 192.168.2.101/22
```(2) Now that your firewalls have been disabled post the output of these commands again please:

**smbtree**
**findsmb**

---

### Post by Autodave on 2010-01-09
> **Morbius1 said:**
> (1) Please copy and paste the command below into your terminal, hit enter, and post the output: ```
nmap -sT 192.168.2.101/22
```(2) Now that your firewalls have been disabled post the output of these commands again please:

**smbtree**
**findsmb**


Before I do that, let me thank you for all of your help today!!!!!

Right now, file sharing is working fine both ways on both machines.  Does this mean that I cannot run a firewall AND use file sharing at the same time????

---

### Post by Morbius1 on 2010-01-09
Wait, you mean to tell me that file sharing both ways now works?

---

### Post by R.Bucky on 2010-01-09
You could always use Dropbox and enable LAN sync... It is bloody brilliant.[IMG]http://buckycomputing.net/uploads/dropbox_lan_sync-326x400.png[/IMG]

---

### Post by Autodave on 2010-01-09
> **Morbius1 said:**
> Wait, you mean to tell me that file sharing both ways now works?


Yuppers!  As soon as I shut off the firewall and went back to my network icon, both machines showed up right away....and it happened on both machines (the other machine's firewall was off already.

Now, I just need to figure out if there is a way to run the firewall and share files or if I have to shut the firewalls everytime I want to share.......

---

### Post by Autodave on 2010-01-09
> **R.Bucky said:**
> You could always use Dropbox and enable LAN sync... It is bloody brilliant.[IMG]http://buckycomputing.net/uploads/dropbox_lan_sync.png[/IMG]

Where do I get this program to try it, does it work with firewalls turned on, and do I have to uninstall anything before installing it?

---

### Post by Morbius1 on 2010-01-09
Thanks for the thank you but you figured this out by yourself. In the future I'm going to start every answer I give to a sharing question with a request to disable all firewalls first.

I have very little experience in setting up firewalls on linux machines I'm afraid. I'm behind a router so I have no need for another firewall. You need to have ports 139,445, and 631 open for file and print sharing to work is all I know.

Sorry.

---

### Post by Morbius1 on 2010-01-09
Before you re-enable your firewall or go to the web based dropbox solution you might want to check out "Shields Up"'s explanation on how you're already behind a firewall because of your router.

> The following explains how a router acts as a firewall: [http://www.grc.com/nat/nat.htm](http://www.grc.com/nat/nat.htm)

    A NAT Router's Inherent Security
    Although NAT routers are not generally purchased for their security benefits, all NAT routers inherently function as very effective hardware firewalls (with a few caveats examined below). As a hardware firewall they prevent "unsolicited", unexpected, unwanted, and potentially annoying or dangerous traffic from the public Internet from passing through the router and entering the user's private LAN network.

    The reason they do this is very simple: With multiple "internal" computers on the LAN behind the router, the router must know which internal computer should receive each incoming packet of data. Since ALL incoming packets of data have the same IP address (the single IP address of the router), the only way the router knows which computer should receive the incoming packet is if one of the internal computers on the private LAN FIRST sent data packets out to the source of the returning packets.If you don't believe that this is true go to the ShieldUp Website to check your security level
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
Look at the ip address that it's probing - it's the public ip address of the router not your machine behind the router.

Just a thought

---

### Post by Autodave on 2010-01-09
> **Morbius1 said:**
> Thanks for the thank you but you figured this out by yourself. In the future I'm going to start every answer I give to a sharing question with a request to disable all firewalls first.

I have very little experience in setting up firewalls on linux machines I'm afraid. I'm behind a router so I have no need for another firewall. You need to have ports 139,445, and 631 open for file and print sharing to work is all I know.

Sorry.


No need to apologize.  If you hadn't answered me many hourts ago, I probably wouldn't have played with it anymore today for fear of screwing something else up!

I may still look at that Dropbox thingy if he/she sends me their web address: I still have 5 more machines to hook up! :-)

---

### Post by R.Bucky on 2010-01-09
Dropbox uses standard web protocols and is free. Sign up for your free account and get 2GB's of free storage. It is similar to Ubuntu One, but Dropbox is cross platform - even better!

---

