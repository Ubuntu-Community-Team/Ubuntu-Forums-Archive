---
title: "Linux-to-Linux Samba NetBios name resolution"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by Clive McCarthy on 2011-05-13
I have a bunch of Linux Ubuntu 10.10 machines all running Samba. I have a router handling DHCP for all machines. I'm using Samba because there are XP machines on the network too.

If I try to get the assigned ip address of a Linux machine using **[COLOR="Blue"]nslookup[/COLOR]** (from another Linux machine) it fails, however, if I try [COLOR="blue"]**nmblookup**[/COLOR] things work fine. 

This is a Linux-to-Linux NetBios name resolution issue I think?

I'm beginning to think that there is poor integration between the name-resolution mechanisms of Linux and Samba NetBios.

Why isn't this enabled by default when Samba is installed? :confused:

What's a clean way of configuring Ubuntu systems so that they use DHCP, Samba? Am I on the right track?

Since ultimately, I'm writing code that calls [COLOR="Magenta"]**gethostbyname(name)**[/COLOR], which fail, is there a system call that does the same thing but in the land of Samba NetBios?

---

### Post by doas777 on 2011-05-13
nslookup queries DNS, not the winbind/WINS database. so unless you have set up a DNS server on your network that is set up to integrate with your routers DHCP service, then nslookup and GetHostByName(iHostName) will not work. the same is true of windows machines running in workgroup mode, unless you have a DNS server that recieves registration information from the host after recieving a DHCP assignment.

you **may** be able to AVAHI (though I am loathe to suggest it), by adding ".local" to the end of the name being queried.

---

### Post by Clive McCarthy on 2011-05-13
Ahah! Thank you. So what should I do? 

Somehow I need to get the DNS database search to include a DHCP database search? Do I have to reconfigure all my Linux machines to do this? That is a bit ugly. Why isn't this enabled by default when Samba is installed?

Is there a Samba system call equivalent to gethostbyname() ? -- then only my application will need to change.

---

### Post by doas777 on 2011-05-13
well, the first thing i would try, is 

"getHostByName("ExHostname.local")"

and see if AVAHI is supported. 

otherwise, you may have to query winbindd through shell tools. don't know if there is an API for it.

---

### Post by Clive McCarthy on 2011-05-13
No, sadly **[COLOR="Blue"]nlslookup machinename.local[/COLOR]** fails too.

Ignoring Samba/NetBios issues how does a pure Linux network of machines handle DHCP? It strikes me that since DHCP is such a common standard, and is so prevalent, that there _ought_ to be a standard mechanism?

Likewise, why are there no system calls into Samba? I could write some code to run shell code and capture the results but that's not really the nice way to go. 

I can't be the only person that bumps into this so there must be a 'clean' solution, surely...

---

### Post by Clive McCarthy on 2011-05-13
I found this: 

[http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/]("http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/")


But it will be a BIG pain to do that on all my Linux machines. :(

---

### Post by SeijiSensei on 2011-05-13
> **Clive McCarthy said:**
> Since ultimately, I'm writing code that calls [COLOR="Magenta"]**gethostbyname(name)**[/COLOR], which fail, is there a system call that does the same thing but in the land of Samba NetBios?

I don't know if this would help, but you could use "nmblookup -A" to query the other machines in the subnet as ask them what their netbios names are.  I've done this in mixed Windows/Linux environments when I wanted to create a DNS nameserver using the machines' netbios names.

To speed up things, I run a "ping scan" first with nmap ("nmap -sP 10.1.1.0/24") to compile a list of active machines,  Then I query each of them with nmblookup.  You could consult this list rather than use gethostbyname().

Another approach you can take is to move your DHCP server onto one of the Ubuntu servers and install a BIND name server there as well.  These programs have hooks that will [enable the DHCP server to update the BIND server]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/DNSDHCP.html") each time it adds or deletes a machine.

---

### Post by Clive McCarthy on 2011-05-13
I have found the **autodns-dhcp** package.

I have just run: [COLOR="Blue"]**sudo apt-get install autodns-dhcp**[/COLOR]

I haven't read /usr/share/doc/autodns-dhcp/ so it looks as if I'm not out of the woods quite yet.

Any advice will be welcome...

---

### Post by capscrew on 2011-05-13
> **Clive McCarthy said:**
> I have a bunch of Linux Ubuntu 10.10 machines all running Samba. I have a router handling DHCP for all machines. I'm using Samba because there are XP machines on the network too.

If I try to get the assigned ip address of a Linux machine using **[COLOR="Blue"]nslookup[/COLOR]** (from another Linux machine) it fails, however, if I try [COLOR="blue"]**nmblookup**[/COLOR] things work fine. 

This is a Linux-to-Linux NetBios name resolution issue I think?

I'm beginning to think that there is poor integration between the name-resolution mechanisms of Linux and Samba NetBios.

Why isn't this enabled by default when Samba is installed? :confused:

What's a clean way of configuring Ubuntu systems so that they use DHCP, Samba? Am I on the right track?

Since ultimately, I'm writing code that calls [COLOR="Magenta"]**gethostbyname(name)**[/COLOR], which fail, is there a system call that does the same thing but in the land of Samba NetBios?

Samba is a suite of applications.  The ***smbd ***daemon manages the SMB protocal calls.  The ***[COLOR="Red"]nmbd [/COLOR]***daemon manages the NetBIOS resolution.  The nmbd daemon should be running (by default) whenever the smbd daemon is running.  You can check to see if both are running like this```
sp -ef | grep mbd
```

It should return something like this```
root       954     1  0 08:26 ?        00:00:00 smbd -F
root      1086   954  0 08:26 ?        00:00:00 smbd -F
root      1115     1  0 08:26 ?        00:00:00 [COLOR="Red"]nmbd -D[/COLOR]
cappy     2287  2270  0 09:59 pts/0    00:00:00 grep --color=auto mbd

```

The nmbd daemon resolves DNS names or hostnames to NetBIOS names for Samba.  There is really no need to have anything more than a functioning LAN side DNS for this to work.  This is how my system works.

I believe the function *gethostbyname (name) *only retrieves hostnmames or DNS names.  This is by design.  NetBIOS names are not retrieved.  But then again they are not needed if DNS is properly set up.  Maybe you need to look to BIND9 for dynamic assignment of hostnames to IP addresses handed out by DHCP.

@doas777

I don't think winbindd has anything to do with this situation.  Quoting from the Samba manual> "winbind is a component of the Samba suite of programs that solves the unified logon problem. Winbind uses a UNIX implementation of Microsoft RPC calls, Pluggable Authentication Modules (PAMs), and the name service switch (NSS) to allow Windows NT domain users to appear and operate as UNIX users on a UNIX machine."

A Windows to Linux user mapping.

---

### Post by Clive McCarthy on 2011-05-13
Thanks for your suggestions. 

I don't have experience of pure Linux networking so I'm puzzled how machines in such a configuration find one another. I assumed that DHCP was an integral part of even a pure Linux environment nowadays?

I really wish to avoid funky stuff like calling shell code from within my C code just to get an ip address of a local machine.

I'm working on a project that uses networked IPC using TCP/IP sockets between _local_ Linux machines. 

The first step in the process is for the program to locate the ip address of a server given the servers name. Most example code uses gethostbyname() which, though seemingly obsolete because it's not re-entrant, ought to play.

---

### Post by Clive McCarthy on 2011-05-13
I don't seem to have **sp**

---

### Post by doas777 on 2011-05-13
> **capscrew said:**
> 
@doas777

I don't think winbindd has anything to do with this situation.  Quoting from the Samba manual

A Windows to Linux user mapping.

interesting. i have always been of the impression that nmbd => winbindd. What is the full name of nmbd i wonder.

@Op, usually in a pure linux network, only servers (boxes that provide services) need predictable names/IPs so they are usually either statically addressed to match a static dns zone configuration, or are assigned via auto-dns registration. workstations usually do not have resources to share, and thus are just fine recieving dhcp addresses, since no one will ever call them.

---

### Post by capscrew on 2011-05-13
> **doas777 said:**
> interesting. i have always been of the impression that nmbd => winbindd. What is the full name of nmbd i wonder.

Actually it's more confusing than just that.  WINS has nothing to do with Winbind either.  WINS is a server that manages NetBIOS name registration.  But it is **not needed on single subnet LAN's**.  

On a single subnet LAN the NetBIOS name registration can be handled by broadcast.  The actual name database is held by the Master Browser: and that can be any host that wins (poor term, eh?) the browser election.  At times my laptop (Vista) is the Master Browser and other times it is my desktop (Ubuntu) and still others it is my NAS, which runs Ubuntu 10.04 server.

---

### Post by Clive McCarthy on 2011-05-13
> 
@Op, usually in a pure linux network, only servers (boxes that provide services) need predictable names/IPs so they are usually either statically addressed to match a static dns zone configuration, or are assigned via auto-dns registration. workstations usually do not have resources to share, and thus are just fine recieving dhcp addresses, since no one will ever call them.

Hmm, that makes networked ipc between DHCP'd machines a bit tricky. 
I'm reluctant to capitulate to hard-coding machine ip addresses. Most of my machines function just as servers (in a sense) but it's an added administrative task to not only name them, but give them unique local ip addresses too. I have no idea how that would play across WiFi either!

---

### Post by capscrew on 2011-05-13
> **Clive McCarthy said:**
> Hmm, that makes networked ipc between DHCP'd machines a bit tricky. 
I'm reluctant to capitulate to hard-coding machine ip addresses. Most of my machines function just as servers (in a sense) but it's an added administrative task to not only name them, but give them unique local ip addresses too. I have no idea how that would play across WiFi either!
There is a 3rd option.  Reserved addressing.  You can reserve a consistent IP address for a particular host at the router.  The client still requests IP addressing via DHCP. All the settings are still set by the router The DHCP server now provides the reserved (constantly the same) IP address.  The reservation is by MAC (hardware) address.

---

### Post by Clive McCarthy on 2011-05-13
> **capscrew said:**
> There is a 3rd option.  Reserved addressing.  You can reserve a consistent IP address for a particular host at the router.  The client still requests IP addressing via DHCP. All the settings are still set by the router The DHCP server now provides the reserved (constantly the same) IP address.  The reservation is by MAC (hardware) address.

My project may require some explanation: I'm building an assemblage of three machines which will drive three displays *-- it's an art work --* these three machines will ultimately detach from my network (and the internet) and stand alone with their own router, when they leave my studio. I'm trying to develop a pretty rudimentary socket ipc application on my normal development machines before I move the component parts to the target hardware.

So I'm working with quite simple examples of client/server ipc using TCP/IP sockets to begin with. There are plenty examples of such fragments to be found on the web. One such is:

[http://www.beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo]("http://www.beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo")

All very nice. But I wasn't planning on reconfiguring my whole network...

---

### Post by doas777 on 2011-05-13
> **Clive McCarthy said:**
> My project may require some explanation: I'm building an assemblage of three machines which will drive three displays *-- it's an art work --* these three machines will ultimately detach from my network (and the internet) and stand alone with their own router, when they leave my studio. I'm trying to develop a pretty rudimentary socket ipc application on my normal development machines before I move the component parts to the target hardware.

So I'm working with quite simple examples of client/server ipc using TCP/IP sockets to begin with. There are plenty examples of such fragments to be found on the web. One such is:

[http://www.beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo](http://www.beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo)

All very nice. But I wasn't planning on reconfiguring my whole network...


ok. that complilcates matters. samba is not a protocol that can be really used over the internet, so once you deploy your PCs, all smb links will fail. is that a showstopper for your current plans?

---

### Post by capscrew on 2011-05-13
> these three machines will ultimately detach from my network (and the internet) 

Samba will still work in his environment (see above).

---

### Post by doas777 on 2011-05-13
> **capscrew said:**
> Samba will still work in his environment (see above).
yeah, saw that, but  also saw the rest of the sentence: 
"and stand alone with their own router, when they leave my studio."
what network is this router connected to and for what purpose.

---

### Post by Clive McCarthy on 2011-05-13
I have samba installed on ALL machines just as a matter of convenience. I have NO plans to attempt to run samba across the internet. The mention of samba may just be a red herring (sorry).

I think my issue is with integrating DHCP and DNS. It seems that the standard interface mechanism for ipc is to reference the DNS data and that DNS data isn't _automatically_ updated with DHCP information. Is this right?

---

### Post by Clive McCarthy on 2011-05-13
> **doas777 said:**
> yeah, saw that, but  also saw the rest of the sentence: 
"and stand alone with their own router, when they leave my studio."
what network is this router connected to and for what purpose.

The router, that is part of the physical art work, is just to permit the three machines to talk to one another via ipc... 
Think of it as an embedded network!

---

### Post by capscrew on 2011-05-13
> **Clive McCarthy said:**
> My project may require some explanation: I'm building an assemblage of three machines which will drive three displays *-- it's an art work --* these three machines will ultimately detach from my network (and the internet) and stand alone with their own router, when they leave my studio. I'm trying to develop a pretty rudimentary socket ipc application on my normal development machines before I move the component parts to the target hardware.

So I'm working with quite simple examples of client/server ipc using TCP/IP sockets to begin with. There are plenty examples of such fragments to be found on the web. One such is:

[http://www.beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo]("http://www.beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo")

All very nice. But I wasn't planning on reconfiguring my whole network...

There have been many times when lack of future vision has precipitated changes in my network scheme.  :-(

It's plain to see that you have to do something.  I guess the most painless would be appropriate.  If the end product (your art work) is not connected to the internet, why do you need a router at all?  A simple switch will work to connect the 3 hosts.  If these 3 hosts are all Linux why are you using Samba.  If they are a mixture of Windows and Linux, I guess the question would be: Why is that so?

What don't I understand here about this project.

---

### Post by capscrew on 2011-05-13
> **Clive McCarthy said:**
> ...

I think my issue is with integrating DHCP and DNS. It seems that the standard interface mechanism for ipc is to reference the DNS data and that DNS data isn't _automatically_ updated with DHCP information. Is this right?

Not unless you set BIND9 up to do so.

Edit: ...or DNSMasq

---

### Post by Clive McCarthy on 2011-05-13
I'd like to do unit testing of code fragments on my development machines (this is my first engagement with ipc and I have a truck load of application code to write once I have it working). As I said, I install samba on all my machines, it will serve no role in the final art work system.

---

### Post by Clive McCarthy on 2011-05-13
> **capscrew said:**
> Not unless you set BIND9 up to do so.

Edit: ...or DNSMasq

Maybe I'm asking for help with BIND9?
Does:
**[COLOR="Blue"]sudo apt-get install autodns-dhcp[/COLOR]**
Get me where I should be going?

Excuse the whine, but since DHCP is so _utterly_ ordinary and Ubuntu invariably will find itself in heterogeneous networks, why aren't Samba, sharing & autodns-dhcp installed by default?

---

### Post by SeijiSensei on 2011-05-13
If you have only three machines, just give them each an /etc/hosts file with the names and addresses of the others.  Then reserve their IP addresses in the router as capscrew suggests.  Or just eliminate DHCP entirely and use static addressing on the servers.  That would be my choice.  

TCP/IP services expect to use DNS to resolve names.  The network model Windows uses of letting clients "announce" their names is pretty foreign to *nix security models which trust the clients as little as possible.

---

### Post by capscrew on 2011-05-13
> **Clive McCarthy said:**
> Maybe I'm asking for help with BIND9?
Does:
**[COLOR="Blue"]sudo apt-get install autodns-dhcp[/COLOR]**
Get me where I should be going?

Yes.  See [**_here_**]("http://www.option-c.com/xwiki/DNS_DHCP_server")

Excuse the whine, but since DHCP is so _utterly_ ordinary and Ubuntu invariably will find itself in heterogeneous networks, why aren't Samba, sharing & autodns-dhcp installed by default?

They have no business on a normal desktop.  If you start adding services (say on a dedicated server) then you (as the systems or network admin) can choose to install them.  No all systems need (or want it all (i.e bloat)).  Try and think of the wider world.

Pardon my whine.  ;-)

Edit:  What happens to your display when DHCP or DNS crashes?  I would think that since you should (and will) know the IP addresses of the 3 hosts, that you would want to program to those IP addresses and eliminate all the potential dangers.  Do these crash?  Sure, that's why there are systems/network admins.  :D

Edit2:  As you can see both @SeijiSensei and I are nudging you towards simplicity.  The /etc/hosts files would sure eliminate a lot of bloat.

---

### Post by Clive McCarthy on 2011-05-13
I'll have about 33 hosts on my network. The trio of machines are suitable only for _deployment_ not development. All my development will take place on my primary workstation (as a client) and I'll use a secondary machine (sitting on my other desk) to act as the test server for the ipc.

Ultimately the target trio will probably be configured so that one of the machines acts as a 'master' client and that it will emit 'commands' via ipc sockets to display-server code running both on itself and to the two other display-servers.

A quick look at BIND9 documentation is not encouraging:

[https://help.ubuntu.com/community/BIND9ServerHowto]("https://help.ubuntu.com/community/BIND9ServerHowto")

This looks a bit more helpful:

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/DNSDHCP.html]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/DNSDHCP.html")

---

### Post by doas777 on 2011-05-13
when you deploy, will your systems be on the same internetwork, or will they need to contact eachother over the Internet? if they need to pass info over the internet, then the naming will have to be done in the public DNS via a registrar. if they are on the same internetwork, then a local dns server or the hosts file will work fine.

---

### Post by Clive McCarthy on 2011-05-13
> **doas777 said:**
> when you deploy, will your systems be on the same internetwork, or will they need to contact eachother over the Internet? if they need to pass info over the internet, then the naming will have to be done in the public DNS via a registrar. if they are on the same internetwork, then a local dns server or the hosts file will work fine.

When I initially deploy, all my machines will be on the same network. When the work leaves the studio it will become entirely isolated, with no internet connection and not in any way part of the WWW.

As I read further, it seems I need to become competent with BIND9 which, if I'm reading things correctly, dynamically updates the DNS tables/files on a machine based on DHCP information.

I'd prefer to keep my WRT54GS gateway-router handling the DHCP for now. 

This means, I think, that I'll need to install BIND9 on all my Linux machines that need DNS services and configure it (on each machine) to be able to find my DHCP server? Then it will keep the DNS up to date and calls to getaddrinfo() will begin to work?

Yes?
BTW, thanks for your patience on this... :popcorn:

---

### Post by Clive McCarthy on 2011-05-13
I just found this:
[INDENT][I]Quick: Ping netbios names from linux

Keywords: linux to windows by "full computer name", netbios lookup, nslookup

Every pc can ping each other using the netbios name which corresponds to ip address.
In windows ping netbios names is working ping mycomputer2 will ping the ip behind the name mycomputer2
You are able to ping a pc that is on dhcp.
This will enable same feature in linux

To enable linux pcs to ping netbios names you need to:

apt-get update
apt-get install winbind
Now edit this file:

vi /etc/nsswitch.conf
Change the line that starts with hosts by adding wins at the end of it.

hosts: files dns
to
hosts: files dns wins
In my Debian it looked like this:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
to
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
Now ping any computer you want:

ping mycomputer2
Done.[/I][/INDENT]

---

### Post by Clive McCarthy on 2011-05-13
And this seems to have done the trick:

[1] install [COLOR="Blue"]winbind[/COLOR]
[2] configure [COLOR="Blue"]/etc/nsswitch.conf[/COLOR] by adding [COLOR="Blue"]wins[/COLOR]

Now my call to [COLOR="Blue"]getaddrinfo[/COLOR](machinename[COLOR="DarkGreen"].local[/COLOR]) succeeds.

N.B. [COLOR="DarkGreen"].local[/COLOR] appended to the machine name

So I'm on my way to ipc. Wheee!

---

### Post by capscrew on 2011-05-13
> **Clive McCarthy said:**
> And this seems to have done the trick:

[1] install [COLOR="Blue"]winbind[/COLOR]
[2] configure [COLOR="Blue"]/etc/nsswitch.conf[/COLOR] by adding [COLOR="Blue"]wins[/COLOR]

Now my call to [COLOR="Blue"]getaddrinfo[/COLOR](machinename[COLOR="DarkGreen"].local[/COLOR]) succeeds.

N.B. [COLOR="DarkGreen"].local[/COLOR] appended to the machine name

So I'm on my way to ipc. Wheee!

Or...
Just put the "wins" at the backend of the NNS and DO NOT add Winbind.  See [[COLOR="Red"]**here**[/COLOR]]("http://blog.tuxopia.net/2010/09/adding-netbios-lookup-support-to-ping.html").

If the example you use there is NO DNS resolution at all.  Thy pinging Google or Yahoo.  For the general user this is not good.  It may well work for your installation to have the "wins" lookup first.

---

### Post by capscrew on 2011-05-13
> **capscrew said:**
> Or...
Just put the "wins" at the backend of the NNS and DO NOT add Winbind.  See [[COLOR="Red"]**here**[/COLOR]]("http://blog.tuxopia.net/2010/09/adding-netbios-lookup-support-to-ping.html").

If the example you use there is NO DNS resolution at all.  Thy pinging Google or Yahoo.  For the general user this is not good.  It may well work for your installation to have the "wins" lookup first.

[COLOR="Green"]**Edit:**[/COLOR] My mistake.  I'm so used to seeing folks put wins in the *front of the NSS line* that I didn't look carefully.  With wins at the back then DNS resolves work fine.  Note that the instructions are for a Domain Controller (PDC) rather than for a workgroup type of situation.  No winbind is needed for a workgroup.

---

### Post by Clive McCarthy on 2011-05-13
Thanks again.

The key step was simply to add **[COLOR="Green"]wins[/COLOR]** to a line in /etc/nsswitch.conf
with [COLOR="Blue"]sudo gedit /etc/nsswitch.conf[/COLOR]

Change the line that starts with hosts by adding **[COLOR="DarkGreen"]wins[/COLOR]** at the end of it.

In my Ubuntu the line now looks like this:
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 **[COLOR="Green"]wins[/COLOR]**

---

