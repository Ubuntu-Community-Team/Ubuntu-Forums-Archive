---
title: "network problem"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by florus on 2010-07-18
I have a home ethernet network with both Windows and Ubuntu computers and an Ubuntu laptop which uses a wireless connection. This network has remained fundamentally unchanged for a couple of years and has always worked perfectly. Now, however, both my Ubuntu machines give an error when trying to access the network:
"Unable to mount location
Failed to retrieve share list from server"
All the computers can access the internet through the router, and the Windows machine can access the Ubuntu machine so there is nothing wrong with the network.
The problem may be linked to Lucid as everything was fine with previous versions of Ubuntu.
Can anyone explain the error message - how do I find out why the problem is occurring?

---

### Post by florus on 2010-07-19
It is a peer to peer network, so I do not understand the reference to a server in the error message.

---

### Post by NoVista on 2010-07-19
Sadly, I have the exact same setup as you, and just realized I have the same problem.
My goodness, is Ubuntu STILL going to have this somewhat same network issue 3 releases in a row? This is an LTS, for goodness sakes!

---

### Post by Iowan on 2010-07-19
> **novista said:**
> this is an ltr, for goodness sakes!LTS?
> **florus said:**
> It is a peer to peer network, so I do not understand the reference to a server in the error message.Peer-to-peer means each machine has both client and server software - so all are clients, and all are servers. 

I'll probably need to do some searching to see what the current status is for the "Unable to mount location Failed to retrieve share list from server" problem

---

### Post by florus on 2010-07-20
Thanks, Iowan, it is probably something simple, but I am not used to having problems with networking Ubuntu and would be glad of some help.

---

### Post by florus on 2010-07-24
bump

---

### Post by Iowan on 2010-07-24
:oops: Thanks for the reminder...
[This]("http://ubuntuforums.org/showthread.php?t=1169149") is a helpful share-debugging How-To, but I didn't see a "Failed to retrieve..." section - unless it was under the name resolution. 
Have you tried accessing via IP address? Not intended as a solution, but it *might* zero in on problem.

---

### Post by florus on 2010-07-24
I tried accessing by IP address, but timed out. I have also noticed that if I go click Places>Network the system is incredibly slow to respond. All the computers are on WORKGROUP, and yet the two Ubuntu computers cannot see each other.

---

### Post by MAFoElffen on 2010-07-24
> **florus said:**
> I have a home ethernet network with both Windows and Ubuntu computers and an Ubuntu laptop which uses a wireless connection. This network has remained fundamentally unchanged for a couple of years and has always worked perfectly. Now, however, both my Ubuntu machines give an error when trying to access the network:
"Unable to mount location
Failed to retrieve share list from server"
All the computers can access the internet through the router, and the Windows machine can access the Ubuntu machine so there is nothing wrong with the network.
The problem may be linked to Lucid as everything was fine with previous versions of Ubuntu.
Can anyone explain the error message - how do I find out why the problem is occurring?
I just noticed I have the same problem when I do that... I have the oppsite in network setup though... My 2 windows machines are wireless only and the Ubuntu machine is wired and wireless.  I have an adhoc network set up in Windows and both Machines are are WORKGROUP...

More strange is my Machine is multi-boot: Ubuntu, Win7, Vista and Opensolaris.  When I boot in either of the Windows OS'es from this machine, it works fine.  But not from Ubuntu 10.04.1.  I think I remember it working in 9.10 on this same machine...

Anyway... I had to do a fresh install of Ubuntu last night (long story).  I noticed in Ubuntu, when I went to set up Personal File Sharing, the top of that dailog box said that I was missing packages to be able to do that...  I installed those packages through the Synaptic Package Manager last night and now that option is there. That still doesn't help me.

And if I tried to go to "Places>Connect To Server>Windows Share"... Where I got a similar meassage:
```
Cannot display location "smb://{server_name}/" Failed to retrieve share list from server
```
I have connections between the two through Network and they say their connected, but I can't get into the Windows Share WORKGROUP...

---

### Post by florus on 2010-07-24
Both my machines were upgrades, not fresh installs. Could this be part of the problem?

---

### Post by MAFoElffen on 2010-07-25
> **florus said:**
> Both my machines were upgrades, not fresh installs. Could this be part of the problem?
Mine was a fresh install.  I had "update" problems when mine tried to do a Distribution Upgrade and got confused about the migration somewhere between 10.04beta2 through 10.04.1... So I just started over via a clean new install.

On mine, this error seems to be a generic non-descript boilerplate message.  It's a  "catchall" to say there was "some" kind of problem connecting to the server.  I say this because, at first I thought it was that it wasn't finding "just" the list of shared files... But if I enter a server that I know "doesn't" exist in my adhoc network, it gets the same message for the server_name.

---

### Post by florus on 2010-07-25
So a fresh install is unlikely to help. I used Lynx very successfully from beta onwards (with fully functional network!) so I may try upgrading to Meercat on my laptop to see if that solves the problem. Easier than trying to find which Lynx update killed my networking.

---

### Post by capscrew on 2010-07-25
> **florus said:**
> So a fresh install is unlikely to help. I used Lynx very successfully from beta onwards (with fully functional network!) so I may try upgrading to Meercat on my laptop to see if that solves the problem. Easier than trying to find which Lynx update killed my networking.

I'm not sure that installing Meercat will help you.  The problem may be the lack of name services from Samba.  

The "Unable to mount location -- Failed to retrieve share list from server" means that the client was unable to retrieve the list of shares maintained by the local master browser.  This can be for any number of reasons.

You should be able to see the failure in the logs.  Look at the logs at /var/log/samba for the specific failure.

Before you decide to "upgrade" the system could you post the output from the following:```
ps -ef | grep mbd
```

The results should be like this:```
root      [COLOR="red"]4791     [/COLOR]1  0 17:10 ?        00:00:00 /usr/sbin/nmbd -D  [COLOR="Red"]**<- name services first**[/COLOR]
root      4793     1  0 17:10 ?        00:00:00 /usr/sbin/smbd -D
root      4832  4793  0 17:10 ?        00:00:00 /usr/sbin/smbd -D


```

---

### Post by MAFoElffen on 2010-07-25
> **capscrew said:**
> You should be able to see the failure in the logs.  Look at the logs at /var/log/samba for the specific failure.

  ...post the output from the ...results
```
1000     12878 12746  0 19:35 pts/0    00:00:00 grep --color=auto [COLOR=Magenta]mbd[/COLOR]
On mine, at least tonight

```The Logfile of "log.winbindd" is:
```
[2010/07/24 08:24:32,  0] winbindd/winbindd.c:1252(main)
  winbindd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/24 08:24:32,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/07/24 13:11:05,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/07/24 13:11:51,  0] winbindd/winbindd.c:1252(main)
  winbindd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/24 13:11:52,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/07/24 13:45:35,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/07/24 14:12:16,  0] winbindd/winbindd.c:1252(main)
  winbindd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/24 14:12:16,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/07/24 14:46:25,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/07/24 14:50:46,  0] winbindd/winbindd.c:1252(main)
  winbindd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/24 14:50:46,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/07/25 08:09:18,  0] winbindd/winbindd.c:1252(main)
  winbindd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/25 08:09:18,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
```The logfile of "log.wb{computer_name}" is:
```
[2010/07/24 13:11:05,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
[2010/07/24 13:45:35,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
[2010/07/24 14:46:25,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
```

---

### Post by capscrew on 2010-07-25
> **MAFoElffen said:**
> ```
1000     12878 12746  0 19:35 pts/0    00:00:00 grep --color=auto [COLOR=Magenta]mbd[/COLOR]
```
On mine, at least tonight
As far as your above post: this would suggest Samba is NOT running at all.

Please don't take this the wrong way.  I don't diagnose multiple posters problems in one thread.  It is not fair to the OP to hijack the thread.  As you are not the OP to the  thread I would suggest you start your own.

> 
The Logfile of "log.winbindd" is:
```
[2010/07/24 08:24:32,  0] winbindd/winbindd.c:1252(main)
  winbindd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/24 08:24:32,  0]
```

There is no need to have winbind running in an adhoc workgroup setup.  Winbind is for domain type networks not workgroups.

---

### Post by florus on 2010-07-26
Thanks for helping, capscrew. My output is:

root       870     1  0 07:43 ?        00:00:00 smbd -F
root      1013   870  0 07:43 ?        00:00:00 smbd -F
root      1518     1  0 07:43 ?        00:00:00 nmbd -D
mark      1961  1943  0 08:39 pts/0    00:00:00 grep --color=auto mbd

which, I have to confess, is meaningless to me.

---

### Post by PratterFak on 2010-07-26
I was never able to get 10.04 to share either. PC to PC, or be able to have my Xbox 360 see the Ubuntu 10.04. I couldn't get any answers to my 360 not seeing the 10.04 issue, so I just went back to 9.10 as everything works perfectly there.

I'm not posting this to hijack anything, but more of a tag for myself to see if this has any resolution and just an addition of user with issues.

Not sure what they did between 9.10 and 10.04 regarding file sharing, but something was not good.

---

### Post by florus on 2010-07-26
Interesting. I am pleased that other people have described similar problems on this thread - it does confirm that there is a real problem with 10.04 and that it is not specific to my setup.

---

### Post by MAFoElffen on 2010-07-26
Sorry **capscrew**, 

I dodin't know I was hi-jacking a thread.  I apologize. I thought I was joining a thread where I had the "same" problem. that others were having.  I will wait for "f**lorus**" to get resolution and see if I  can learn from it...

---

### Post by capscrew on 2010-07-26
> **florus said:**
> Thanks for helping, capscrew. My output is:

```
root       870     1  0 07:43 ?        00:00:00 smbd -F
root      1013   870  0 07:43 ?        00:00:00 smbd -F
root      1518     1  0 07:43 ?        00:00:00 nmbd -D
mark      1961  1943  0 08:39 pts/0    00:00:00 grep --color=auto mbd
```

which, I have to confess, is meaningless to me.

The **smbd ** is the Samba server daemon (e.g the process).  There should be 2 of them.  The **nmbd **is the netBIOS name service daemon.

I notice that the smbd daemon is not running as a server.  The **-F **shows that.  Not sure what it means so I will have to research  that.  Also the order that the processes spawn different from earlier versions.  That can possibly make a difference.

I would still like to see some of the syslogs to see what errors are generated.  The logs are at: **/var/log/samba**

To make thngs orderly please post these outputs between the "code "symbols".  This is the **#** mark at the top or manually as [code] [/ code]

---

### Post by MAFoElffen on 2010-07-26
Yahoo!  Thank you so very much **capscrew**!!! It was one of those asking the same person (my computer) the same question in different words- and it wouldn't give me an answer unitil I asked correctly...  Meaning until I searched Ubuntu's "Help" for the word Samba, I then found these instructions:  (Read down- There's additional steps for Windows filesharing)
[HTML]8.2.2.&#8195;Sharing folders via Nautilus

To share folders using Nautilus:

1.  Press Places &#9656; Computer to open a File Browser window.

2.  Right click the folder you wish to share and select Sharing Options on the 
popup menu.

3.  Check Share this folder in the Folder Sharing window. You may change the 
Share name field if you want to use a different share name.

4.  You may receive a message which says Sharing services are not installed. If 
this happens, ensure that the two checkboxes in the message box are checked and 
press Install services. Sharing service support will then be downloaded and 
installed; this may take a while.

5.  Select Allow other people to write in this folder if you wish to allow 
others to add, change, and remove files in this folder. If you leave this box 
unchecked, other people will only be able to view files in this folder. You may 
also fill in the Comment field.

6.  Select Guest access (for people without a user account) if you wish to 
allow guest users to access your files.

7.  Press Create share to make the shared folder available.

8.  You may receive a message stating that Nautilus needs to add some 
permissions to the folder in order to share it. If this happens, press Add the 
permissions automatically.

9.  Other people on the same network (LAN) as you should now be able to access 
the folder.

You may receive a message which says You do not have permission to create a 
usershare. If this happens, contact your system administrator or configure the 
Folder sharing service (samba).

See the Shared Folders Administration Tool manual for more information on 
managing network shares.

8.2.3.&#8195;Accessing shared folders via Windows

If you would like to access a shared folder hosted on an Ubuntu computer by 
using computers running Windows, you may have to perform some additional steps:

1.  Press Applications &#9656; Accessories &#9656; Terminal to open a Terminal.

                      
2.  Type sudo smbpasswd -a username, replacing “username” with your own 
username. Press Enter to run the command.

You can find out what your username is by typing whoami into the Terminal and 
then pressing Enter.

3.  Enter your password when prompted with “[sudo] password for username:” and 
press Enter again.

4.  When prompted with “New SMB password:”, enter the password that you would 
like to use to access the shared folder and then press Enter. You can leave the 
password blank, which will allow anyone to access the shared folder.

5.   When prompted with “Retype new SMB password:”, enter the password that you 
just entered and then press Enter.

6.   You should now be able to connect to the shared folders on the Ubuntu 
computer.

8.2.4.&#8195;Problems connecting to shared folders in Windows

If you are unable to connect to a shared folder using Windows, try using the IP 
address of the Ubuntu computer rather than its host name to access the share:

1.  Press System &#9656; Administration &#9656; Network Tools and select the Devices tab.

2.  Select the name of your network connection from the Network device option 
list (for example, “eth0”). If you have several network connections, you may 
have to try this several times.

3.  Make a note of the number in the IP address column. It should consist of 
four numbers separated by dots (for example, “192.168.2.10”)

4.  On the Windows computer, select Start &#9656; Run and type \\ipaddress in the 
text box, replacing “ipaddress” with the IP address of the Ubuntu computer

5.  Press OK to connect to the shared folder.

The folder sharing service in Ubuntu that supports sharing with Windows 
computers is called Samba.  The background process, or daemon, is called smbd.

If you are still unable to access the shared folder, check that the folder 
sharing service is running on the Ubuntu computer. 

In a terminal, run:  
  service smbd status

You should see an output like:  smbd start/running, process 123

If the service is stopped, you will see:
  smbd stop/waiting

If you find that the service is stopped, try starting the service:
  sudo service smbd start

More information can be found on the Ubuntu community help pages.[/HTML]I hope they help...  They did for me.

---

### Post by capscrew on 2010-07-26
> **PratterFak said:**
> I was never able to get 10.04 to share either. PC to PC, or be able to have my Xbox 360 see the Ubuntu 10.04. I couldn't get any answers to my 360 not seeing the 10.04 issue, so I just went back to 9.10 as everything works perfectly there.

I'm not posting this to hijack anything, but more of a tag for myself to see if this has any resolution and just an addition of user with issues.

Not sure what they did between 9.10 and 10.04 regarding file sharing, but something was not good.

Your experience is valuable and you are not asking for help with your setup.  You are not a hijacker. :-)

But you can be of great assistance.  Please post your output of ```
ps -ef | grep mbd
```

This could show the differences between 9.10 and 10.04.  The main change in Samba is in how it is launched.  Ubuntu 9.10 and earlier uses the SysV init system, while 10.04 uses Upstart.

---

### Post by florus on 2010-07-26
I did look at the log files - there seemed to be quite a lot, many of them empty. They are mostly repetitive, so I will post what I think to be relevant extracts.
```
[2010/06/13 08:04:28,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/06/13 08:04:28,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/06/13 08:04:28,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/06/13 08:04:28,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/06/13 08:04:28,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/06/13 08:04:28,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
```

The above presumably relates to my attempt to send output to a printer on the Windows computer.

```
  Samba name server MARK-DESKTOP is now a local master browser for workgroup WORKGROUP on subnet 192.168.2.100
  
  *****
[2010/06/13 00:16:41,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...
[2010/06/13 08:04:45,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/06/13 08:05:11,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server MARK-DESKTOP is now a local master browser for workgroup WORKGROUP on subnet 192.168.2.100
  
  *****
[2010/06/13 08:30:28,  0] nmbd/nmbd.c:130(nmbd_sig_hup_handler)
  Got SIGHUP dumping debug info.
[2010/06/13 08:30:28,  0] nmbd/nmbd_workgroupdb.c:281(dump_workgroups)
  dump_workgroups()
   dump workgroup on subnet   192.168.2.100: netmask=  255.255.255.0:
  	WORKGROUP(1) current master browser = MARK-DESKTOP
  		MARK-DESKTOP 40849a03 (mark-desktop server (Samba, Ubuntu))
  		MAGGIE-PC 40011203 ()
[2010/06/13 08:30:28,  0] nmbd/nmbd.c:130(nmbd_sig_hup_handler)
  Got SIGHUP dumping debug info.
[2010/06/13 08:30:28,  0] nmbd/nmbd_workgroupdb.c:281(dump_workgroups)
  dump_workgroups()
   dump workgroup on subnet   192.168.2.100: netmask=  255.255.255.0:
  	WORKGROUP(1) current master browser = MARK-DESKTOP
  		MARK-DESKTOP 40849a03 (mark-desktop server (Samba, Ubuntu))
  		MAGGIE-PC 40011203 ()
```

MAGGIE-PC is the windows computer, MARK-DESKTOP is my Ubuntu computer.

Please let me know if you need longer extracts or other log files.

---

### Post by capscrew on 2010-07-26
> **florus said:**
> 
Please let me know if you need longer extracts or other log files.

Let's try something.  Form the terminal issue these commands:```
sudo service smbd stop

sudo service smbd start
```

After you have done that post the output of:```
ps -ef | grep mbd
```

See if you can see browse the network.

---

### Post by florus on 2010-07-26
```

root      1518     1  0 07:43 ?        00:00:00 nmbd -D
root      3094     1  0 18:36 ?        00:00:00 smbd -F
root      3096  3094  0 18:36 ?        00:00:00 smbd -F
mark      3121  3066  0 18:38 pts/0    00:00:00 grep --color=auto mbd

```

still unable to access network.

---

### Post by capscrew on 2010-07-26
Are you able to ping these hosts by name?

---

### Post by florus on 2010-07-26
I can ping MAGGIE-PC with a mean round trip of 55 ms, but the IP address in the 'source' column is not one I recognise.

---

### Post by capscrew on 2010-07-26
> **florus said:**
> I can ping MAGGIE-PC with a mean round trip of 55 ms, but the IP address in the 'source' column is not one I recognise.

What is it?  For Samba to work correctly the name and IP must be resolved correctly.

---

### Post by florus on 2010-07-26
Sorry, I think I am being thick. The IP address given as the source is an OpenDNS address.

---

### Post by capscrew on 2010-07-26
> **florus said:**
> Sorry, I think I am being thick. The IP address given as the source is an OpenDNS address.

That makes no sense.  Post the output of the ping.

---

### Post by florus on 2010-07-26
I am using System>Admin>Network Tools>Ping which is not giving me anything I can post. The source address is 67.215.65.132 and other than that it merely tells me that it is using 64 byte packets, 5 requests.

---

### Post by capscrew on 2010-07-26
> **florus said:**
> I am using System>Admin>Network Tools>Ping which is not giving me anything I can post. The source address is 67.215.65.132 and other than that it merely tells me that it is using 64 byte packets, 5 requests.

Use the command line.  The proper incantation is:```
ping -c5 MAGGIE-PC
```

The output should resemble this:```
PING kona (192.168.1.15) 56(84) bytes of data.
64 bytes from kona (192.168.1.15): icmp_seq=1 ttl=128 time=0.491 ms
64 bytes from kona (192.168.1.15): icmp_seq=2 ttl=128 time=0.538 ms
64 bytes from kona (192.168.1.15): icmp_seq=3 ttl=128 time=0.573 ms
64 bytes from kona (192.168.1.15): icmp_seq=4 ttl=128 time=0.462 ms
64 bytes from kona (192.168.1.15): icmp_seq=5 ttl=128 time=0.495 ms

--- kona ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.462/0.511/0.573/0.048 ms

```

---

### Post by florus on 2010-07-26
> 
PING MAGGIE-PC (67.215.65.132) 56(84) bytes of data.
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=1 ttl=51 time=65.6 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=2 ttl=51 time=49.7 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=3 ttl=51 time=50.1 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=4 ttl=51 time=57.5 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=5 ttl=51 time=58.3 ms

--- MAGGIE-PC ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 49.754/56.307/65.611/5.887 ms
mark@mark-desktop:~$ 

So I can ping the computer ok. Or I can ping something.

---

### Post by capscrew on 2010-07-26
> **florus said:**
> So I can ping the computer ok.

No you can't.  You are pinging: ```
nxdomain.opendns.com (67.215.65.132)
```

This is not maggie-pc

Go to maggie-pc and tell me the IP address of that machine.

---

### Post by florus on 2010-07-26
Sorry, I have to leave now. I think 192.168.2.101 is the correct address. Back in about 30 minutes.

---

### Post by capscrew on 2010-07-26
> **florus said:**
> Sorry, I have to leave now. I think 192.168.2.101 is the correct address. Back in about 30 minutes.I am out for a bit myself.

---

### Post by florus on 2010-07-26
Checked the correct IP address. Output of ping
> 
ping -c5 192.168.2.101
PING 192.168.2.101 (192.168.2.101) 56(84) bytes of data.

--- 192.168.2.101 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms


---

### Post by capscrew on 2010-07-26
> **florus said:**
> Checked the correct IP address. Output of ping

Edited: After rereading the post.

Ah, you can't ping IP address or by name; therefore Samba fails.

This has to be corrected before anything further can be contemplated.

How did you setup your IP networking (including name services)?

---

### Post by florus on 2010-07-26
Right, as far as I can remember: My router was set up originally to connect to the internet through my ISPs (TalkTalk) servers. These got very congested, so I changed first my computer, and then the router to use OpenDNS servers. The Windows PC was still using the TalkTalk servers, so I changed the settings in Windows as well.  
I am sure that my network problems are are recent than those changes, but presumably there is a connection. I still don't understand why I cannot ping the Windows computer by IP address.

---

### Post by capscrew on 2010-07-26
> **florus said:**
> Right, as far as I can remember: My router was set up originally to connect to the internet through my ISPs (TalkTalk) servers. These got very congested, so I changed first my computer, and then the router to use OpenDNS servers. The Windows PC was still using the TalkTalk servers, so I changed the settings in Windows as well.  
I am sure that my network problems are are recent than those changes, but presumably there is a connection. I still don't understand why I cannot ping the Windows computer by IP address.

On the Ubuntu host post the output of:```
ifconfig -a
```
On the Windows host post the output of: ```
ipconfig /all
```

This will provide the basic IP addressing for the 2 hosts.

Now we need to see how you have setup name resolution on the Ubuntu host.  Post the output of ```
cat /etc/resolv.conf
```

---

### Post by florus on 2010-07-27
```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:84:a2:a7  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe84:a2a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:712315 (712.3 KB)  TX bytes:111448 (111.4 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```

```

cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 208.67.222.222
nameserver 8.8.8.8
nameserver 208.97.220.220
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 8.8.4.4
```
I see that I am using GoogleDNS as well as OpenDNS - the TalkTalk servers were a real pain.
I will add the Windows output shortly, when I have access to the computer. In the mean time I will correct the address of the second OpenDNS nameserver.

---

### Post by florus on 2010-07-27
From the Windows host: 
```
ipconfig /all



Windows IP Configuration



   Host Name . . . . . . . . . . . . : maggie-PC

   Primary Dns Suffix  . . . . . . . :

   Node Type . . . . . . . . . . . . : Hybrid

   IP Routing Enabled. . . . . . . . : No

   WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller

   Physical Address. . . . . . . . . : 00-24-E8-23-02-8F

   DHCP Enabled. . . . . . . . . . . : Yes

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::99f5:fdbc:f35:f643%10(Preferred)

   IPv4 Address. . . . . . . . . . . : 192.168.2.101(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Lease Obtained. . . . . . . . . . : 27 July 2010 07:52:12

   Lease Expires . . . . . . . . . . : 29 July 2010 07:52:11

   Default Gateway . . . . . . . . . : 192.168.2.1

   DHCP Server . . . . . . . . . . . : 192.168.2.1

   DHCPv6 IAID . . . . . . . . . . . : 251667688

   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-03-27-F7-00-24-E8-23-02-8F



   DNS Servers . . . . . . . . . . . : 208.67.220.220

                                       8.8.8.8

   NetBIOS over Tcpip. . . . . . . . : Enabled



Tunnel adapter isatap.{C119B1F6-CF65-4FD2-8403-08545660BD24}:



   Media State . . . . . . . . . . . : Media disconnected

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : Microsoft ISATAP Adapter

   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes



Tunnel adapter Teredo Tunneling Pseudo-Interface:



   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface

   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes

   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:73ba:20fd:311d:b16a:b651(Pref

erred)

   Link-local IPv6 Address . . . . . : fe80::20fd:311d:b16a:b651%11(Preferred)

   Default Gateway . . . . . . . . . : ::

   NetBIOS over Tcpip. . . . . . . . : Disabled
```

---

### Post by capscrew on 2010-07-27
I see one problem with MAGGIE-PC.

```
 NetBIOS over Tcpip. . . . . . . . : Disabled
```

This needs to be enabled.  This you can find the settings in **Network Sharing**.  You need at least **Network Discovery** and **File Sharing** to be on.

I think you need to return (if only temporarily) to the ISP provided DNS settings on both computers.  Try it and see if you can now ping by name both ways.  If that works we can discuss how to use Google and OpenDNS properly.

What is the manufacturer and model number of the router you are using?

---

### Post by florus on 2010-07-27
Network Discovery and File & Printer Sharing are both enabled, as is NetBIOS over Tcpip for the Ethernet adapter. 
NetBios over Tcpip is not enabled for the Tunnel adapter, but that section is totally unknown to me and I have no idea where to start. I have never used Windows 7, and it was Vista that converted me to Ubuntu.
I will try to find the IP addresses for the TalkTalk servers.

---

### Post by capscrew on 2010-07-27
> **florus said:**
> Network Discovery and File & Printer Sharing are both enabled, as is NetBIOS over Tcpip for the Ethernet adapter. 
NetBios over Tcpip is not enabled for the Tunnel adapter, but that section is totally unknown to me and I have no idea where to start. I have never used Windows 7, and it was Vista that converted me to Ubuntu.
I will try to find the IP addresses for the TalkTalk servers.

Yes, you are right.  I missed that.  What I was looking at is Tunnel adapter for IPv6.  Not part of your problem.

Hmmm,  I'm not sure about Win7 problems, but are you using "Public Shares".  If so, try turning that off also.

---

### Post by florus on 2010-07-27
Right, I have set both computers to get their DNS servers automatically. I can ping MARK-DESKTOP from MAGGIE-PC but when I ping the MAGGIE-PC I still get the same strange OpenDNS address.

---

### Post by capscrew on 2010-07-27
> **florus said:**
> Right, I have set both computers to get their DNS servers automatically. I can ping MARK-DESKTOP from MAGGIE-PC but when I ping the MAGGIE-PC I still get the same strange OpenDNS address.

On MARK-DESKTOP, Show me the results of ```
cat /etc/resolv.conf

and 

cat /etc/hosts


```

**What is the manufacturer and model number of the router you are using?**

---

### Post by florus on 2010-07-27
The router is an ADSL2 SMC Barricade, model SMC7904WBRA.
> 
cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.2.1

> 
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	mark-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---

### Post by capscrew on 2010-07-27
> **florus said:**
> The router is an ADSL2 SMC Barricade, model SMC7904WBRA.

I have looked at the router and it does not appear that you can configure local LAN DNS.  

The NetBIOS name service is working on the Windows host.  We need to provide name service for the Ubuntu host.

The easiest way is to add that mapping to the /etc/hosts file.  Have you used the test editor "nano"?  If not see if you can do this:
1. Open Nano from the terminal like this:
```
nano test.file
```

2. Add some text

3. Save the file
  See the commands at the bottom 
  Use the "cntl-X" and follow the instructions.

If you can do that we can update the /etc/hosts file.

---

### Post by florus on 2010-07-27
I have not used Nano before, but followed the instructions and anded up with a plain text file test.file in ~/home/mark.
I normally use gedit - what is the advantage of Nano?

---

### Post by DEVIL DOG on 2010-07-27
I have 10.04 on one puter and 9.10 on the other.  They can't see each other.  Maybe this will help you guys.  I tried the samba start command on my 10.04 and it worked.  Tried it on my 9.10 and it said smbd service not recognized.  There is definitely a samba problem.  Not trying to hijack, just watching and trying to contribute as I have the same problem.

---

### Post by capscrew on 2010-07-27
> **DEVIL DOG said:**
> I have 10.04 on one puter and 9.10 on the other.  They can't see each other.  Maybe this will help you guys.  I tried the samba start command on my 10.04 and it worked.  Tried it on my 9.10 and it said smbd service not recognized.  There is definitely a samba problem.  Not trying to hijack, just watching and trying to contribute as I have the same problem.

This is because Samba uses Upstart when stating up in 10.04 and 9.10 does not.

---

### Post by DEVIL DOG on 2010-07-27
> **capscrew said:**
> This is because Samba uses Upstart when stating up in 10.04 and 9.10 does not.

Ok then.  Occams Razor... right?  The problem is incompatible software.

---

### Post by capscrew on 2010-07-27
> **florus said:**
> I have not used Nano before, but followed the instructions and anded up with a plain text file test.file in ~/home/mark.

Great!

We now need to make a copy of /etc/hosts.  As these files are owned by **root **you will need to use the term *sudo * to gain root privileges This is how to make a copy:```
sudo cp /etc/hosts /etc/hosts.original
```

You can check that it worked fromthe terminal with this:```
ls /etc | grep hosts
```

Now we can open the file /etc/host file to modify it like this ```
sudo nano /etc/hosts
```

Add the line like I did in **[COLOR="Red"]red [/COLOR]**:```
127.0.0.1	localhost
127.0.1.1	mark-desktop
[COLOR="red"]**192.168.2.101  maggie-pc**[/COLOR]


# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
[COLOR="Red"]**This should work as long as maggie-pc is given the same IP address!!!!**[/COLOR]

If you want to keep this address for maggie-pc you will need to either || switch it to a static address || or make it a reserved address (via MAC addr) in the router.

Try it and see if you can ping and that Samba is working.

---

### Post by DEVIL DOG on 2010-07-27
So the software is incompatible, but can be worked around through manual configuration?
2 10.04 puters on the same network should be automatic config then, right?

---

### Post by florus on 2010-07-27
All went well except the ping. The hosts file reads:
> 127.0.0.1	localhost
127.0.1.1	mark-desktop
192.168.2.101   maggie-pc

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
but> ping -c5 maggie-pc
PING maggie-pc (192.168.2.101) 56(84) bytes of data.

--- maggie-pc ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4032ms


---

### Post by florus on 2010-07-27
Crazy - I can't ping, but my network is back, fully functional.

---

### Post by florus on 2010-07-27
Many thanks, capscrew, for your help and unending patience. You really have been very kind. Can I mark this thread up as solved?

---

### Post by capscrew on 2010-07-27
> **florus said:**
> Crazy - I can't ping, but my network is back, fully functional.

You have ICMP pings firewalled.

Editing the /etc/host file sure works but there are more elegant ways.

Now you need to make sure the IP address stays the same on the Windows host.  This can be done in the router as reserved by MAC address.

PM me if you want the entire details as to what went wrong and what is the proper fix

---

### Post by capscrew on 2010-07-27
> **DEVIL DOG said:**
> So the software is incompatible, but can be worked around through manual configuration?
2 10.04 puters on the same network should be automatic config then, right?

The OP's problem has nothing to do with Upstart.  If you wish to pursue this start you own thread.  You are of topic and the OP's problems have been solved.

---

### Post by DEVIL DOG on 2010-07-27
> **capscrew said:**
> The OP's problem has nothing to do with Upstart.  If you wish to pursue this start you own thread.  You are of topic and the OP's problems have been solved.

Just trying to understand what is happening.

---

### Post by oldsoundguy on 2010-07-27
reboot everything .. that is what I had to do.  Make sure that the Windows boxes are still granting network permissions

---

### Post by Morbius1 on 2010-07-27
capscrew,

I haven't been on this forum very long but I think this is the first time I've seen anyone attempt to and fix this particular problem without suggesting to the user that he install winbind, edit a few other non relevant config files, and launch their own personal communications satellite in geosynchronous near-earth orbit.  :p

I just have one request:
>  PM me if you want the entire details as to what went wrong and what is the proper fix
Don't you dare hide anything from us. ;)

---

### Post by capscrew on 2010-07-27
> **florus said:**
> Many thanks, capscrew, for your help and unending patience. You really have been very kind. Can I mark this thread up as solved?

@florus,

You are welcome.  I would say that you can  mark the thread solved(and you have done so).

But..., You are not out of the woods just yet.  We have proven that you basic problem involved name services.  You have cured the immediate problem of DNS name resolution for maggie-pc by editing the /etc/hosts file.  What happens when you add another host to the network?  How will we prevent another host from using the IP address currently leased to maggie-pc?.

---

### Post by capscrew on 2010-07-27
> **Morbius1 said:**
> capscrew,

I haven't been on this forum very long but I think this is the first time I've seen anyone attempt to and fix this particular problem without suggesting to the user that he install winbind, edit a few other non relevant config files, and launch their own personal communications satellite in geosynchronous near-earth orbit.  :p

I'm sure you jest.  Although I usually use a reamer in these situations.  :D> 

I just have one request:

Don't you dare hide anything from us. ;)

Actually the story has been told before.  See [**_here_**]("http://ubuntuforums.org/showthread.php?t=1496488&highlight=winbind").  In the past I have been accused (rightfully so, I must say) of providing too much information.

---

### Post by Iowan on 2010-07-27
> **capscrew said:**
>  In the past I have been accused (rightfully so, I must say) of providing too much information. Perhaps you should consider generating a thread in **Tutorials & Tips**. It'd be nice to have the info in one place. :)

---

### Post by Morbius1 on 2010-07-28
> **Iowan said:**
> Perhaps you should consider generating a thread in **Tutorials & Tips**. It'd be nice to have the info in one place. :)
+1

You bring us tantalizingly close to the answer but then you stop. Perhaps you are telling us the answer and perhaps the answer is in the links you mentioned in your other post ( which I have not read ) but remember the rest of us are but mere mortals. In my particular case I have machines that had Windows and OSX preinstalled and linux machines. Except for throwing up a firewall or something overt , I can't make samba fail. It's been that way since I left SuSE 6. Everything works out of the box. If I'm doing something elegant ( and no one has ever accused me of that ) - if I'm doing anything at all - it's happening in my sleep. Others are not so fortunate ( or lucky ).

If you tell us the secret you'll have thousands of adoring fans and dispel one of the great Samba myths.

---

### Post by NoVista on 2010-07-28
Solved, perhaps, but reading the original post is what led me here.
For others that arrive here with the dreaded
"Unable to mount location", read on.
What resolved my problem was turning off the firewall.

See post #14 >>
[http://ubuntuforums.org/showthread.php?t=1484700](http://ubuntuforums.org/showthread.php?t=1484700)

It was due to some updates a while ago. I never changed anything with my network since Lucid. Now I can see the WORKGROUP name again.

---

