---
title: "Can't connect to a Samba share on Ubuntu server from Ubuntu desktop"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by Niarbeht on 2010-03-01
Hello.  My laptop's running Ubuntu 9.10, relatively fresh install, ran it through all the updates and everything.  Anyway, nautilus is being rather annoying and refusing to connect to my server's password-protected Samba shares.The server is running Ubuntu server 9.10.  Anyway, I can connect fine from Windows 7, and I can browse non-passworded shares with ease.  I can navigate to the share I want, or type the full path of hidden shares in to the address thinger in nautilus, but it comes up with a username/domain/password prompt.  I enter the username and password correctly, leave the domain ("WORKGROUP") alone, since nautilus doesn't even ALLOW for empty input there (smart, huh?  D'oh), smack okay, and promptly get the same prompt again, with the password field emptied out.

I can do this as many times as I like, it'll never connect me.

And yes, I am using the correct username and password for the server's side of things.

[http://pastebin.ca/1816996](http://pastebin.ca/1816996)

The above URL is a comment-and-other-sensitive-info-stripped version of my smb.conf

Any advice?  Is nautilus just retarded, or is there hope?

By the way, the reason I'm trying to connect so badly?  My home directory from my old Gentoo install is sitting on my server.  It's got a bunch of class notes and stuff in there that would be nice to have.  Time's not an issue, I never look at the things after I write them anyway, but it'd be nice to at least have them around in case I break that trend.

Also, just for kicks, has anyone found a nice, successful guide to publishing SSH and SFTP services to the network via Zeroconf/Avahi for Ubuntu server?  My old Gentoo desktop setups made sharing between my computers darn easy, and I liked it quite a bit...  But that's not as important, I guess.

Anyway, thanks for taking the time to read this far!  I'd appreciate any input or crazy things to try.  I haven't tried mounting from a terminal yet, mainly because I'd rather do things "The Ubuntu Way" before I switch back to my old Gentoo habits...

*starts itching, wondering why he's not at the command line right now....*

---

### Post by Niarbeht on 2010-03-03
I still haven't gotten around to trying to connect/mount manually from my laptop's Ubuntu installation.

---

### Post by Iowan on 2010-03-03
Probably doesn't matter - but are you using the "Connect to Server" or the "Network" option?

---

### Post by Niarbeht on 2010-03-05
The network dialog.  I navigate to my server that way.  I'll give the "Connect to server..." thing a poke in a sec...

EDIT:
Well, alright, even via the "Connect to server..." interface, I get the same sort of treatment.  I plugged in the server's name on the local network (IP address acts the same way, just to head off that question), punched in the share's name and a valid user name on the server.  No dice.  Same issue where it's asking for a password (understandable) and asking for a Domain (what?!).  Inputting the correct password does nothing, I've tried various names for the domain/workgroup (the server's name, localhost, my computer's name, etc...)

I dunno.  I have the same account name/password across my desktop/server, and my desktop runs Windows and Gentoo.  The Windows install connects, no problem, doesn't even ask for a username/pass since Windows just spits out your current login info when connecting to a "Windows" share...  Haven't seen if KDE4 under Gentoo has no issues yet.  I should probably do that today...

---

### Post by Morbius1 on 2010-03-05
Forgive me if this is a stupid question, but you did create a samba password on the server for the remote client, right?

As in sudo smbpasswd -a remote_user_name

---

### Post by Niarbeht on 2010-03-05
If you examine the smb.conf, a url to which was provided in the original post, you'll note that the configuration includes already synchronization with my UNIX users.

And even if I manually use smbpasswd to create an account and then try to log in as that account, same thing happens.

---

### Post by Niarbeht on 2010-03-06
Well, I tried using dolphin from KDE on my desktop, no dice there either.  Same story.

I probably have something set up improperly in the smb.conf, but what I don't know.

So, yeah.  Works from Windows, even when logging in from a friend's computer.  Doesn't work from Linux.

Weird.

---

