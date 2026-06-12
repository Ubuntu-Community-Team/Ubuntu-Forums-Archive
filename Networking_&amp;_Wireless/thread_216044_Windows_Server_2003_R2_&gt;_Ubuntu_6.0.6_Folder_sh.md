---
title: "Windows Server 2003 R2 &gt; Ubuntu 6.0.6 Folder sharing (within a workgroup, not domain)"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by Thenotsowyzewun on 2006-07-14
Hi,

My setup:

Workgroup called WORKGROUP
Comprimises of the Server and Workstation.
Server called MSSERVER
Runs Windows Server 2003 R2 Standard Edition, with no roles assigned and Windows Firewall enabled.
Workstation called UBUNTUWORKSTATION
Running Ubuntu 6.0.6.

I've setup a shared folder on the workstation, and with the help of a post I found using a quick search on here have finished Samba setup (by adding a password).

So my server can now access the shared folder on the workstation.

But now I'm trying to configure shares on the Server (so maybe this is more a Windows Q than a *nix Q, hope you don't mind!).

When I right-click on a folder in windows and select "Sharing and Security..." it shows that a share has already been created called D$, however I can't change the permissions for this share (or remove it) because "This has been shared for administrative purposes".
So then I noticed the button that says "New Share" and I've clicked that and created a new share called D.
The workstation can now see the server within Network Servers (under Places), but when I click on SERVER it says "The folder contents could not be displayed".
I could move the files I want to share onto the workstation, but I don't have the room, and I'd rather not have to do that every time I wanted access to files from either machine.

Thanks very much for reading :D

---

### Post by Thenotsowyzewun on 2006-07-15
Wahey got it working :D.

Undoubtably someone else is gonna come along and want to know how to do this at some point.

In Windows, go into REGEDIT and browse to HKEY_LOCAL_MACHINESYSTEMCurrentControlSetServiceslanmanserverparameters\ and change the vale of the key called requiresecuritysignature to 0.
Then click Start, Control Panel, Administrative Tools, Local Security Policy and browse to Security Settings\Local Policies\Security Options\ and disable the following options:
Domain member: digitally encrypt or sign secure channel data (always),
Microsoft network client: Digitally sign communications (always), and Microsoft network server: Digitally sign communications (always)

As you've probably guessed, this does make your Windows Server less secure, but it's necessary because SMB does not yet support digital signing (AFAIK - I couldn't get the machines to connect with these options enabled (as they are by default).

Now all you need to do is allow File Sharing to the local subnet (or wherever the Linux machine is).
In my case this was easy because I'm running Windows Firewall, so I opened that up (through Control Panel) and on the 2nd tab (called Exclusions I think) ticked File Sharing.
Again, this minimizes security somewhat, but I'm beyond a perimeter firewall so I think the risk is ok.
Lastly, go back to your ubuntu machine and click Places, Network Serves, browse to the machine and it'll probably ask you to login. You need to login as one of the users you authorized under Share Permissions in Windows.
In my case, this is set to the Everyone group with full-control, again a big security hole.

Now this is a very insecure way of going about connecting your Windows 2003 Server and Ubuntu machine, make no mistake, so you might want to experiment with the settings/read some more stuff elsewhere to do this in a more secure manner (I'm going to) but in the meantime at least it's nice that they're talking to each other!

Hope that helps someone :)

BTW I got my answers from some people speaking french on this forum last year, and a mac forum.

---

