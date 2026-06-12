---
title: "Adding &quot;winbind&quot; (wins) to resolve windows hostnames slows down firefox"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by fermulator on 2010-05-29
This is really bothersome, and I want to make a howto for this, but I don't have a 100% complete/acceptable solution.

**_Requirements:_**
 A) Ubuntu machine should be able to ping windows machines on the network by name without hard coding hosts file, nor through the configuration of an official internal DNS server (which would be overkill for <10 hosts).
 B) Samba (through nautilus) should also be aware of these windows' names.

**_Constraints:_**
 C) This addition should not impact performance of pinging through the terminal (i.e. ping [www.google.ca](www.google.ca)).
 D) This addition should not impact performance of browsing the Internet using Firefox or any other browser.

Here's what I've got so far.

Install windbind:
```
sudo apt-get install winbind
```
Add the entry "wins" before the "dns" entry in **/etc/nsswitch.conf**:
> hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4

This Solves A and B.  However, breaks C.  As it currently stands, when you fire up a terminal and try to ping a web address, there is a significant delay (on the order of seconds) before it returns, however it doesn't affect the latency directly.

To fix C, (as per [http://ubuntuforums.org/showpost.php?p=8321202&postcount=6](http://ubuntuforums.org/showpost.php?p=8321202&postcount=6)), we can remove mdns4 from the hosts line in **/etc/nsswitch.conf**:
> hosts:          files mdns4_minimal [NOTFOUND=return] dns wins

Now C is fixed, and pings return immediately, and as they should.  However, we're still left with the problem of D.  Any "new request" for Firefox to resolve a web address, it takes seconds before it finds it, stalling on "looking up BLAH".  Once it does look it up, the page loads blazingly fast like it should.

How to proceed next?

---

### Post by capscrew on 2010-05-29
> **fermulator said:**
> This is really bothersome, and I want to make a howto for this, but I don't have a 100% complete/acceptable solution.

**_Requirements:_**
 A) Ubuntu machine should be able to ping windows machines no the network by name without hard coding hosts file.  (all machines are DHCP)
 B) Samba (through nautilus) should also be aware of these windows' names.

**_Constraints:_**
 C) This addition should not impact performance of pinging through the terminal (i.e. ping [www.google.ca](www.google.ca)).
 D) This addition should not impact performance of browsing the Internet using Firefox or any other browser.

Here's what I've got so far.

Install windbind:
```
sudo apt-get install winbind
```
Add the entry "wins" before the "dns" entry in **/etc/nsswitch.conf**:


This Solves A and B.  However, breaks C.  As it currently stands, when you fire up a terminal and try to ping a web address, there is a significant delay (on the order of seconds) before it returns, however it doesn't affect the latency directly.

To fix C, (as per [http://ubuntuforums.org/showpost.php?p=8321202&postcount=6](http://ubuntuforums.org/showpost.php?p=8321202&postcount=6)), we can remove mdns4 from the hosts line in **/etc/nsswitch.conf**:


Now C is fixed, and pings return immediately, and as they should.  However, we're still left with the problem of D.  Any "new request" for Firefox to resolve a web address, it takes seconds before it finds it, stalling on "looking up BLAH".  Once it does look it up, the page loads blazingly fast like it should.

How to proceed next?
In my network I have the following types of hosts:
[LIST]
[*]Ubuntu Server - Samba fileserver
[*]Ubuntu Desktop Environment - Samba Server and Client
[*]Windows XP  
[*]Windows Vista 
[/LIST]

The network uses these services:
[LIST]
[*]DHCP
[*]DNS
[*]NetBT -broadcast
[/LIST]

This system meets all of your goals (A,B,C, and D) without using winbind or altering the /etc/nsswitch.conf file.  Here is the appropriate line from my Ubuntu desktop /etc/nsswitch.conf file:```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
I have seen others who feel that winbind is needed for successfully resolving IP to either NetBIOS or DNS name.  i wonder why.  Nothing I have read states that.  In fact I always seem to return to the documentation at samba.org for this definition:
```
winbind is a component of the Samba suite of programs that
**[COLOR="Green"]solves the unified logon problem[/COLOR]**.
 
Winbind uses a UNIX implementation of Microsoft RPC calls,
Pluggable Authentication Modules (PAMs), and the name service
switch (NSS) [B][COLOR="Green"]to allow Windows NT domain users
to appear and operate as UNIX users on a UNIX machine.[/COLOR][/B]
```
In another section of the documentation this is described as:```
The service provided by winbindd is called `winbind' and can be
**[COLOR="Green"]used to resolve user and group information[/COLOR]** from a Windows NT server. 
The service can also provide authentication services via an associated PAM module.
```

It appears to me that this is a ***[COLOR="Blue"]networking name service[/COLOR]*** problem.  This means NetBT (WINS) or DNS, not winbind.  

I am also looking for a solution that is consistent for use in networks that don't have DNS (e.g peer to peer) and do not want to use static hosts files.  So far this means DNS in the form of DNSmasq.  This is what is used in most home or SOHO routers.

Windows platforms are self sufficient.  They broadcast their COMPUTER names.  I believe Linux hosts can also do this with Samba installed.  I have seen NetBIOS calls from my Samba servers, but I have never followed it up though.

As to what you could do next:  I would remove winbind completely and increase the syslog setting in smb.conf to [FONT="Courier New"]**syslog = 3 **[/FONT]and see what happens.  I would use that as a baseline to look for solutions.

---

### Post by superrikku on 2010-05-30
I am having a similar problem. Capscrew's setup doesn't use the windows boxes as servers. In the OP's (and my own) scenario, the windows computers are servers, and we want to be able to see them in 'Network' with nautilus. When 'wins' is added to host resolution in nsswitch.conf, it slows things down considerably for requests that aren't directed at a windows server share, like loading websites in Firefox.

I think I saw a bug report somewhere talking about this, with the solution to take 'wins' out of the host resolution list, but that prevents windows computers from being recognized.

---

### Post by fermulator on 2010-05-30
Indeed.  capscrew thanks for the detailed information and posting, and I believe you've hit the root cause issue on the button.

I've for now, disabled the "wins" entry in /etc/nsswitch.conf as I prefer speedy Internet browsing over ability to resolve "windows names" over samba.

Your point that Windows broadcasts their hostnames is very relevant.  In fact, so does Linux with samba is installed and configured properly.  I suppose, the *ideal* solution would be that when sambafs (cifs) is installed, by default, it should also listen to these broadcasts from other Windows machines?  That might be, most elegant?

---

### Post by capscrew on 2010-05-30
> **superrikku said:**
> I am having a similar problem. Capscrew's setup doesn't use the windows boxes as servers. In the OP's (and my own) scenario, the windows computers are servers, and we want to be able to see them in 'Network' with nautilus. 

What type of server are you refering to?  Are we talking about file servers (SMB) or name servers (DNS or WINS)?   I don't see the relevence of any other kind of server.  All Windows hosts run SMB/CIFS file servers.  This would be the functionall equivelent of Samba.  NetBios does not need a WINS server to function on Windows hosts.  But it appears unfortunatley that Ubuntu does.
> 
When 'wins' is added to host resolution in nsswitch.conf, it slows things down considerably for requests that aren't directed at a windows server share, like loading websites in Firefox.

This is due to the routines configured in nsswitch looking for a WINS server and not finding one.  I believe that installing winbind and modifiying the nsswitch.conf file is not the correct way to go.
> 
I think I saw a bug report somewhere talking about this, with the solution to take 'wins' out of the host resolution list, but that prevents windows computers from being recognized.
The bug reports using that solution are partly correct.  Removing the "wins" out of the line stops Samba from vainly searching over and over for a non-existant WINS server.

So why do so many reccomend winbind as a means of correcting NetBIOS naming problems?  It appears that SUN Solaris and IRIX unix systems have name services that are intertwined with users/groups.  This has lead to the use of /lib/libnss_wins.so and nsswitch for help.  This lib is only available in the wibbind package.  This 'lib' is only incidentlay relevent and and winbind is not needed at all.

I know this doesn't provide answers directly.  Hopefully an answer will come soon.

---

### Post by capscrew on 2010-05-31
> **fermulator said:**
> Indeed.  capscrew thanks for the detailed information and posting, and I believe you've hit the root cause issue on the button.

I've for now, disabled the "wins" entry in /etc/nsswitch.conf as I prefer speedy Internet browsing over ability to resolve "windows names" over samba.

Your point that Windows broadcasts their hostnames is very relevant.  In fact, so does Linux with samba is installed and configured properly.  I suppose, the *ideal* solution would be that when sambafs (cifs) is installed, by default, it should also listen to these broadcasts from other Windows machines?  That might be, most elegant?

By *sambafs *, do you mean the package **smbfs**? This is the client side of Samba.  It is needed for you to use the Ubuntu host as a SMB client.

My thought was to see if my Ubuntu and Windows hosts will communicate via NetBIOS broadcasts only.  This should be possible as long as all hosts are on the same subnet (on the same switch in my case).  Sadly this is not happening at this time. :-( 
Tomorrow is another day though.

---

### Post by mockingbird on 2010-05-31
I can confirm this problem.  Maybe someone should submit a bug report.

---

### Post by capscrew on 2010-05-31
@ fermulator,

I finally found some time to try a few things when it was quiet here.  Earlier, my first mistake was to try and troubleshoot using ping.  Ping is part of TCP/IP.  NetBIOS has no idea what that is, Duh!!!  The better tool would be this! ```
sudo smbtree
``` First off let me say, it is elegant and it does work.  My system will allow the browsing of all shares without the need for DNS, WINS server or windbind.  **[SIZE="3"]The entire system is browseable using nothing more than NetBIOS broadcast.[/SIZE]**

This means that a Ubuntu host can act exactly like a Windows host in a peer to peer network. In my system there is a slight lag with the 2 Ubuntu hosts, but that is because broadcasts are a last resort in default configuration of smb.conf.  I'm sure I can tune the system for faster times.   

@ superrikku,

Let me be clear here: If you have a Windows server that shares files via SMB then it will work just like I described above.  Part of the SMB protocol is to create a virtual network using all the endpoints and resources.  This is encapsulated in TCP, but is not part of it.

@ mockingbird,

I'm sure you have the symptoms but there is no bug in the system.  There has always been misunderstanding of how browsing shares (Network Neighborhood) really works.

------

I think it would help for all to read [**_[COLOR="Blue"]"Understanding the Network Neighborhood"  [/COLOR]_**]("http://www.linux-mag.com/id/785").  This really explains all the aspects of browsing shares.

Another good site is [**_[COLOR="blue"]Implementing CIFS[/COLOR]_**]("http://www.ubiqx.org/cifs/").

FYI -- both of these sites are listed on the main page of Samba.org!  :D

---

### Post by B!aine on 2010-05-31
The OP's description was excellent.  I am having this same problem on my Linux machine.  I am accessing a Western Digital NetCenter which shares both files and a printer with an iMac, Windows box, and my Linux (ubuntu) box.  Using samba, smbfs, winbind, and adding wins to the /etc/nsswitch.conf file allows me to use it seamlessly with all three, but brings what ever internet browser I'm using to a crawl.  If I delete wins from the /etc/nsswithc.conf file or remove winbind the internet is very fast like it should be, but then I can't access the NetCenter.  What is the next step to fix this and have them both work?  I have been using Ubuntu for about a year now and just thought slow internet was part of Linux.  I even bought a new computer to try and fix it (it was needed anyway, just gave me a good reason), but still slow internet.  I would love to have this problem fixed.

---

### Post by capscrew on 2010-05-31
> **B!aine said:**
> The OP's description was excellent.  I am having this same problem on my Linux machine.  I am accessing a Western Digital NetCenter which shares both files and a printer with an iMac, Windows box, and my Linux (ubuntu) box.  Using samba, smbfs, winbind, and adding wins to the /etc/nsswitch.conf file allows me to use it seamlessly with all three, but brings what ever internet browser I'm using to a crawl.  If I delete wins from the /etc/nsswithc.conf file or remove winbind the internet is very fast like it should be, but then I can't access the NetCenter.  What is the next step to fix this and have them both work?  I have been using Ubuntu for about a year now and just thought slow internet was part of Linux.  I even bought a new computer to try and fix it (it was needed anyway, just gave me a good reason), but still slow internet.  I would love to have this problem fixed.

The answer may not be obvious in my post above.  So let me put it in another way.  You should not use nsswitch routines  as a means of locating the NetBIOS names for *Network Neighborhood Browsing*.  Winbind is also not an acceptable method of using the NeBIOS namespace for browsing.  These 2 methods in Linux are only for Sun Solaris and IRIX compatibility.

Read my previous posts carefully and the the information that I provided in the links.  The answer is there.  I have a network that does not need winbind or nsswitch modification and I can browse all shares on all hosts --[LIST]
[*]Ubuntu to Windows
[*]Windows to Ubuntu
[*]Ubuntu to Ubuntu
[*]Windows to Windows
[/LIST]

---

### Post by B!aine on 2010-05-31
@ capscrew,

Thank you for the reply.  I read the "understanding network neighborhood" page and looked over implementing cifs page.  I also reread your previous posts.  The second link I really didn't understand.  I'm sure there is a solution in there, but I don't understand networking enough to have seen it.  

I think I have figured out at least a temporary solution for my setup though.  By going to Places>Connect to Server>Server Type>Windows Share, and typing in the IP address of my NetCenter I am able to connect.  For the printer if I go to System>Administration>Printing>Add>Network Printer and again type in the IP address of my NetCenter I am able to find and add that printer.  All that is installed is Samba and SMBFS, no winbind or changes the the /ets/nsswitch.conf file.  

This is not elegant but it does work for now.  I also don't know if the IP address will change, or what causes it to change, or what it will change to if it does.  I think the solution will continue to work though if there is a change.

---

### Post by carnagex420x on 2010-08-07
```
wins [NOTFOUND=continue] dns
```

[http://www.softpanorama.org/Solaris/Reference/etc/nsswitch.shtml](http://www.softpanorama.org/Solaris/Reference/etc/nsswitch.shtml)
that should push it threw but it doesn't help. 

I made a real rough workaround but you still need a command line.

[http://x420x.fookops.com/forum/bash/samba-mount/#p16](http://x420x.fookops.com/forum/bash/samba-mount/#p16)

---

### Post by chuckyp on 2010-12-01
@capscrew

  I've also read your posts and I don't see any solution that you are talking about. Can you please tell us what you did to get it working without winbind or wins in nsswitch.conf?????

---

### Post by drdanielfc on 2011-10-15
I don't mean to revive a dead thread, but this is still a problem in Ubuntu 11.10. Has anyone made any progress?
This has proved to be a major problem when trying to show off how amazing Ubuntu is and compatible, and then i still can't browse samba shares!

---

### Post by capscrew on 2011-10-15
> **drdanielfc said:**
> I don't mean to revive a dead thread, but this is still a problem in Ubuntu 11.10. Has anyone made any progress?
This has proved to be a major problem when trying to show off how amazing Ubuntu is and compatible, and then i still can't browse samba shares!
The *problem * you are referring to is really a lack of configuration.  The default install requires modification of the /etc/samba/smb.conf.  Add this to the [global] section```
netbios name = <hostname>
name resolve order = bcast host
```

Then either restart the smbd and nmbd services or reboot the system.

Edit: Substitute your machine's hostname for <hostname> above.  The NETBIOS name should be less than 15 characters long.

---

### Post by drdanielfc on 2011-10-16
Wow, I've been searching for hours and never found a post that "just worked" like that. Thank you so much capskrew!

---

### Post by fermulator on 2011-12-01
Confirmed!  Great, thanks Capscrew!

---

