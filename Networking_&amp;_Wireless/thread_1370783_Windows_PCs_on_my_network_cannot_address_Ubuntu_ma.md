---
title: "Windows PCs on my network cannot address Ubuntu machine by hostname"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by Amurko on 2010-01-02
I'm sharing an internet connection and printer among 3 computers on my LAN.  2 of them use Ubuntu and 1 use Windows.  The printer is attached to one of the Ubuntu machines and filesharing on the LAN is managed with Samba.

The hostnames for my Ubuntu machines are:

ComputerA
ComputerB

The hostname of the XP machine is: ComputerC

Since the router assigns IPs dynamically, I address resources (such as the printer) via hostname rather than IP.  When I'm using an Ubuntu machine, I can address the other Ubuntu machine by hostname (rather than IP like 192.168.10.5 or something.)  However, when I'm using the Windows machine and I try to ping either ComputerA or ComputerB by hostname, it says that the hostname isn't recognized.  The windows machine can ping and access resources on the Ubuntu machines fine if I provide the correct IP..  but since this network uses DHCP, it's not practical.

So my question is, how can I get my Windows machines to recognize the hostnames of my ubuntu machines?

---

### Post by skmelville on 2010-01-02
Hi:
I am a newbie Linux and had the same problem. I tried the old trick of shutting down all the machines and started the Linux machines and then the windows machine. Viola! all machines recognized all others. Be sure name the work group for windows and linux machinee the same. That said, I still have not been able to have my new WIndows 7 machine open the files on the linux machines, though they are recognized. It seems Win XP does the job better than Win-7. Go to the Ubuntu Forum and search. It is a wealth of info on a lot of these types of problems.
SK:)

---

### Post by issih on 2010-01-02
[EDIT]I knew this thread was out there somewhere...its rather excellent for sorting these issues out..
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
[/EDIT]

Try using hostname.local, i.e. append ".local" to the end of the hostname.

That way the system tries to use bonjour (also known as avahi and various other things) to achieve the name resolution. I admit I am not sure if XP has it enabled by default, but I'd have expected 7 to.

In general you need to do one of the following things to get dhcp assigned ip addresses to resolve via normal hostnames.

1) run a dns server somewhere on the network (some routers offer this)

2) sort out the netbios name resolution (i.e. windows networking name resolution)

I've had to use this in the past, but I don't know if its still necessary

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

Given that your ubuntu machines are seeing each other I would also check that the workgroup of the ubuntu machines matches that of the windows box.

you can check the ubuntu machines workgroup in the file:

/etc/samba/smb.conf.

If its not the same either change the windows machine to match the others, or edit that file using sudo to gain root privileges (N.B. save a backup copy first!!!)

Hope that helps

---

