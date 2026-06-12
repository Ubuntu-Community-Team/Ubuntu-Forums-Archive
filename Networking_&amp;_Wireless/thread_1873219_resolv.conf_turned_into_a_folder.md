---
title: "resolv.conf turned into a folder"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Mark_S on 2011-11-01
Hey everyone, I've never had the need to post here but I ran into something strange today and do not see it documented anywhere so I figured I better let the masses know.

I have a netbook that I run Ubuntu 10.10 on and it's always worked great for me. I hadn't used it in a while but today I turned it on and came to find that I could not get to any websites. I was properly connected and everything, so after some basic network troubleshooting I narrowed it down a DNS issue because nothing was resolving but I could still get to everything by IP address. I went to check out my resolv.conf file and magically it had turned into a folder....The folder had no permissions set as well. 

So I chmod'd the folder, renamed it to .old (just incase I did need it later), and then copied the resolv.conf.tmp file to be the resolv.conf file. Everything is now working fine.

Basically I am wondering if anyone has ever seen this before? Does anyone have any explanation as to how this might happen? It just seems really weird to me that it would happen out of nowhere.

---

### Post by jonobr on 2011-11-01
Hello


I scan the networking forums and most the DNS issues appear to be incorrect information or it not being populated correctly or the search order is wrong.

Usually for DNS problems, I ask peps to post their resolv.conf.
I dont believe I have seen it like you describe.

Mind you, Im sure there are people who run into a problem like this, reinstall and their problem disappear.

---

### Post by bab1 on 2011-11-01
> **jonobr said:**
> Hello


I scan the networking forums and most the DNS issues appear to be incorrect information or it not being populated correctly or the search order is wrong.

Usually for DNS problems, I ask peps to post their resolv.conf.
I dont believe I have seen it like you describe.

Mind you, Im sure there are people who run into a problem like this, reinstall and their problem disappear.

Come on guys.  Of course there is both a /etc/resolv.conf file and a /etc/resolvconf directory.  Note the dot (.) in the first example. You can list the contents of /etc/ and grep to filter only resolv.  This is what you should get```
ls -l /etc/ |grep resolv
drwxr-xr-x  3 root    root      4096 2011-03-29 13:24 resolvconf
-rw-r--r--  1 root    root        80 2011-07-15 07:46 resolv.conf

```

You can see their different descriptions with the man pages```
man /etc/resolv.conf
man resolvconf
```

Note that resolvconf is an application.  If it is not installed you will have no man page.  The directory should still exist.

You can view the web version of the man page for resolvconf [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://manpages.ubuntu.com/manpages/natty/man8/resolvconf.8.html")

---

### Post by jonobr on 2011-11-01
Well feed me garlic and call me sticky, I didn't know there was a resolvconf 

I suppose I took OP at face value that he had a resolve.conf not a resolvconf.. interesting stuff

Anyway, One thing..... i'm on 10:04 - 

Looking at my current work machine I have this...
Im missing something...Help me understand...

```
lumpy@jabba:/etc$ ls resolv*
resolv.conf
lumpy@jabba:/etc$ ls -l /etc/ |grep resolv
-rw-r--r--  1 root root      96 2011-11-01 10:03 resolv.conf
lumpy@jabba:/etc$ man man
lumpy@jabba:/etc$ man resolv.conf
RESOLV.CONF(5)                                                       Linux Programmer's Manual                                                       RESOLV.CONF(5)

NAME
       resolv.conf - resolver configuration file

SYNOPSIS
       /etc/resolv.conf

DESCRIPTION
       The  resolver  is a set of routines in the C library that provide access to the Internet Domain Name System (DNS).  The resolver configuration file contains
       information that is read by the resolver routines the first time they are invoked by a process.  The file is designed to be human readable  and  contains  a
       list of keywords with values that provide various types of resolver information.

       If  this  file doesn't exist the only name server to be queried will be on the local machine; the domain name is determined from the hostname and the domain
       search path is constructed from the domain name.

       The different configuration options are:


```

---

### Post by bab1 on 2011-11-01
> **jonobr said:**
> Well feed me garlic and call me sticky, I didn't know there was a resolvconf 

I suppose I took OP at face value that he had a resolve.conf not a resolvconf.. interesting stuff

Anyway, One thing..... i'm on 10:04 - 

Looking at my current work machine I have this...
Im missing something...Help me understand...

```
lumpy@jabba:/etc$ ls resolv*
resolv.conf
lumpy@jabba:/etc$ ls -l /etc/ |grep resolv
-rw-r--r--  1 root root      96 2011-11-01 10:03 resolv.conf

```

I believe you are looking at a sever version of Ubuntu 10.04.  This would be correct for that version of the OS.  There is no *automatic* gathering of DNS data.  In fact the first paragraph in the resolv.conf pages speaks to that.  > 

```
lumpy@jabba:/etc$ man resolv.conf
RESOLV.CONF(5)                                                       Linux Programmer's Manual                                                       RESOLV.CONF(5)

NAME
       resolv.conf - resolver configuration file

SYNOPSIS
       /etc/resolv.conf

DESCRIPTION
      [COLOR="DarkGreen"] The  resolver  is a set of routines in the C  
library that provide access to 
the Internet Domain Name System (DNS).  The resolver configuration file
contains information that is read by the resolver routines the first
time they are invoked by a process.[/COLOR] ...


```

On the other hand, the desktop version of Ubuntu has need of automated DNS data collection for services like AVAHI and Network-Manager.  On my desktop I have removed NM and resolvconf, but left AVAHI.  The /etc/resolvconf/ directory is there because of AVAHI only in my case.  It will not over write my manually configured resolv[SIZE="5"].[/SIZE]conf file.   

The man pages for resolvconf show different useage:```
[COLOR="Blue"]NAME

       resolvconf - manage nameserver information


SYNOPSIS

       cat FILE | resolvconf -a INTERFACE

       resolvconf -d INTERFACE

       resolvconf -u

DESCRIPTION

      [B][I] Overwrite  (-a)  or  delete  (-d) the nameserver information record for
       network  interface  INTERFACE   and   run   the   update   scripts   in
       /etc/resolvconf/update.d/ if the nameserver information has changed.[/I][/B]

       With -u, just run the update scripts.

PUBLICATION

       Normally  resolvconf  is  run  only by hook scripts attached to network
       interface configurers such as pppd(8) (for  ppp  interfaces),  to  DHCP
       clients  such  as dhclient(8), to ifup(8) and ifdown, and to DNS caches
       such as dnsmasq(8) (for the loopback interface).   These  hook  scripts
       furnish  resolvconf  with  information about nameservers.  For example,
       dhclient  receives  one  or  more  nameserver  addresses   during   its
       negotiation  with the DHCP server; its hook script /etc/dhcp3/dhclient-
       enter-hooks.d/resolvconf publishes this information to resolvconf.

[/COLOR]
```

---

### Post by jonobr on 2011-11-01
Sweet

Its a sad day you dont learn something.

I am indeed on the server version

---

### Post by Mark_S on 2011-11-01
Well thanks for the replies guys.

I know there is a resolvconf directory, that is partly how I first noticed that the resolv.conf _file_ turned into a directory. When I ls'd the /etc/ directory they were both the same color which threw me. 

I know I may look like a noob since I've never posted here but I know what I'm doing ;) I've used Linux since I switched from Unix to Slackware when I was 11 years old. I still get called "The Linux Guy" at my work and am forced to handle anything Linux related that may come in. 

I like to solve my own problems and usually keep to myself, not much of a forum poster, but this was just so weird I had to see if anyone had run into it before. When I searched around I found nothing so I thought I'd post it for anyone who may run into it in the future. Like jonobr said, I'm sure someone may have run into this before and just reinstalled to fix it, but hopefully now if someone does run into it again they will see this and be able to resolv.it (UCWUTIDIDTHUR?)

---

### Post by davemidd on 2012-04-17
Thanks for the post Mark_S.  I had exactly the same problem and was wondering the same as you, what was going on. I fixed the problem in the same way as you.

---

