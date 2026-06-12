---
title: "Setting up desktop (9.04) behind router for remote access by latptop (9.10)"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by fisheater on 2010-01-08
Setting up desktop (9.04) behind router for remote access by latptop (9.10)

Hi,

I am setting up desktop (9.04) behind router for remote access by latptop (9.10).

Rationale: All of my files are on my desktop HD, but I am often out of my home needing to work on my files. It is becoming labour intensive to keep track of the files I make/change and try to copy them on my non-connected desktop/laptop.

Dream: Able to remote access and modify my desktop files from my laptop (while the files remain on the desktop).

Request: A simple, GUI, basic, non-technical guide how to set it up!

What I know:
1.I was going to use the 'Remote Desktop' VNC connection under System->Preferences. However, if I understand this correctly, this only secures my computer (i.e. Locks the front door of my desktop) and the data streamed between them is not encrypted.
1.[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
2.Then I need to set up my router to accept the connection from my laptop.
3.Then I will need to use SSH to secure the info sent between them. This is the bit I don't really have a good grip on. The info I have read is more confusing that helpful. [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Remote_Access)

In order, I think this is the setup
1.Set up VNC on desktop (target computer)
2.Set up router (DDWRT) to allow connection from laptop to desktop.
3.If that works, then set up SSH

I will keep trying with this and update any (mis)adventure!

Thanks for your help with *simple, *basic, *non-technical advice!

Kind regards,

FE

---

### Post by pricetech on 2010-01-08
Set up SSH first.  Forward port 22 (default) to your desktop IP.  Install NX from Nomachine dot com.  (Client, Server, Node on your Linux box and Client on your winders laptop.

That's the best solution I've found.  I use it all the time.

---

### Post by fisheater on 2010-01-08
Wow, it worked.

I downloaded the NX, installed and with a bit of effort it was up and running. I first tried via my LAN, then switched to my router's IP. I have my DDWRT router port forward 22 to my desktop.

I looked to see if this was secure, but I really have no idea. Some of the tutorials note that there is a tick box 'all communication via SSH', but I could not find it. I am using version 3.4.0-5.

Thanks this looks great. I cant believe I havent done this yet! WOW.

The next thing to look at is security. Is NX encrypted by default? If not, what is the next step? Do I need to have any additional security now that I have opened port 22?

TY

FE

Q2: Do i need to further secure my NX server on my desktop (target) machine? i.e. unless they have login/pw they cant get in.

Q3:  Should i change to port from 22 to something less standard? i.e. any advantage to that?

Q4: how do i get a file from my laptop into the instance of NX on my desktop? Or getting files on my desktop onto my laptop when I am away? Dragging and dropping didnt work... TY

---

### Post by pricetech on 2010-01-11
> **fisheater said:**
> Wow, it worked.

The next thing to look at is security. Is NX encrypted by default? If not, what is the next step? Do I need to have any additional security now that I have opened port 22?

Short answer;  NX is secure because it functions over SSH.

> **fisheater said:**
> Q2: Do i need to further secure my NX server on my desktop (target) machine? i.e. unless they have login/pw they cant get in.

Install fail2ban from the repos.  It will help secure against attacks.

> **fisheater said:**
> Q3:  Should i change to port from 22 to something less standard? i.e. any advantage to that?

That's Optional.  Some people find the idea distasteful as "security through obscurity" but I see no reason not to.  Here's how I do it (from my "notes to self")
NX runs over SSH.  Both must be configured to use a port other than 22.:
SSH:  /etc/ssh/sshd_config

One entry for Port, close to the beginning of the file.


NX:  /usr/NX/etc/node.cfg

One entry just shy of two thirds of the way through the file.  (SSHDPort)


NX:  /usr/NX/etc/server.cfg

Two entries, one within the first page (SSHDPort) and the second about a third of the way down (SSHDAuthPort)


The easiest way to find the entries is to search for "22" since that is the default port.  You may want to put a comment at the top of each file showing the new port number to make it easier to find.

You'll have to sudo gedit to make changes to the files.  SSH and NX Server (or the computer) will have to be restarted to make the changes take.  Remember to back up the original files before editing as a precaution.  Once the changes are made you'll need to change the forwarded port in your router.

> **fisheater said:**
> Q4: how do i get a file from my laptop into the instance of NX on my desktop? Or getting files on my desktop onto my laptop when I am away? Dragging and dropping didnt work... TY

I've never attempted it since it's not something I need to do in my case, but it seems there is a way to do it with NX.  If not, then Secure Copy or Secure FTP would be your answer, though someone else can better explain how to set that up than I.

---

### Post by fisheater on 2010-01-11
Great info, thanks. I have cut/paste this beauty into my working notes for linux.

So far it has been superb, this is a good product that works well.

TY for your time.

FE

---

### Post by pricetech on 2010-01-11
No problem.  Glad to be of assistance.

---

