---
title: "ushare - &quot;bind address is already in use&quot; ive tried to KILL daemon"
date: 2008-07-03
forum: Multimedia Software
---

### Post by Majin_Buu on 2008-07-03
> greenfish@skynet:~$ ushare -x
uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
bind: Address already in use
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]
greenfish@skynet:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      [ OK ]

It doesn't matter how many times I try to kill the daemon it's still up and running.

Anyone have any other ideas to shutdown the process?

a simple "ps" doesnt even list ushare

---

### Post by Majin_Buu on 2008-07-04
:popcorn: *bump*

---

### Post by xc3RnbFO8P on 2008-07-04
Is there something you can use here:
>  Re: How to make Ubuntu, uShare and xBox 360 play nice.
This is soo frustrating.

I had this working the other day, I updated mime.c and was happily watching Divx movies. Great.

The next day I get an error from ushare :

"bind: Address already in use"

Lots of tearing of hair, eventually found it was something to do with the telnet connection? Well at least I think it was, disabling with -t and ushare starts up... but now the xbox cannot see the computer! Do we need telnet on? Or is there something else wrong?

EDIT: Success! Some notes :
It works if I disable telnet and web : ushare -t -w -x -f /etc/ushare.conf
Even then it doesn't always connect, the xbox seems to remember previous connections so it's useful to use the same port number and/or select a different ushare name each time. I seem to get the best results if I start ushare after the xbox. Lots of old divx files just won't play, and after a failed attempt of an old file it'll often refuse to play a new valid file with the same error. Restarting and going straight to the new file plays without a problem.

---

### Post by thenetking on 2010-11-07
EDIT: Success! Some notes :
It works if I disable telnet and web : ushare -t -w -x -f /etc/ushare.conf

This worked for me, sounds like another program, possibly even ushare is binding to a port of some kind and this instance of ushare is unable to use it at that point.

---

