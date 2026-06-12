---
title: "connecting to a windows based network"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by brandontmilan on 2011-03-18
I am a fairly new Ubuntu user.  I've used various distributions of linux at different times in the past, but I've usually moved back to windows because of the difficulty of connecting into a windows network.

Here is my situation.  I have a laptop with a dual boot windows and ubuntu.  I work in a small office with a server (with vista, I believe) that I regularly need to access.  I have limited access to the server (if I need to change some permissions, I could do that, but installing anything is out of the question).

Is there a way that I can connect to the server via linux.  I would love it if there were a GUI that I could use, but if not, what is the easiest way (with limited commands and/or edits to config files)?

When I find the computer under "places-network" it asks for a domain.  I'm not sure what to put in there.  When I put in my password, it will not accept it.

---

### Post by frio on 2011-03-18
Can you provide a bit more information about your network and the server.

Are you in a domain environment? If so, I'll be of little help since I have not used linux with a domain.

If not then...
Do you have a local account on the server. I assume you do if you can access files on it via windows.

Also, I am not using a version of Ubuntu with a GUI so I cannot get into specifics on the GIU's for network setup but I do know they exist.

Basically you will need the Samba suite to access windows 'stuff' from Ubuntu. You may already have some or all of this installed.

Here is what I have installed on my linux server:
    libpam-smbpass -           pluggable authentication module for Samba
    libwbclient0 -            Samba winbind client library
    samba -                    SMB/CIFS file, print, and login server for Unix (you may not need this if you are not serving up files to windows)
    samba-common -            common files used by both the Samba server and client
    samba-common-bin -        common files used by both the Samba server and client
    samba-doc -                Samba documentation
    smbfs -                    Samba file system utilities
    swat -                    Samba Web Administration Tool (optional but maybe a good enough GUI for you)
    winbind -                    Samba nameservice integration server

Using Samba will give you access to the same shares you have with windows. Configuration of most of this is done in /etc/samba/smb.conf

---

