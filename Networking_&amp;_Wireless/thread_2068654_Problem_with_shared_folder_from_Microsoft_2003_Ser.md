---
title: "Problem with shared folder from Microsoft 2003 Server to Ubuntu 12.04 Client"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by Tech0 on 2012-10-09
I'm trying to connect to a shared folder on a Microsoft 2003 Server, using Ubuntu 12.04 client.

Server IP: #.#.#.19 ; Client IP: #.#.#.22 ; same network
Directory: D: \Office\Share

I can ping the server without any problems.
I can use firefox to connect to server's welcome screen.
I checked the shared folder settings: full access to users; all ports open.

When I use the terminal command: ssh #.#.#.19
I get: connect to host #.#.#.19 port 22: Connection refused

When I use Connect to Server[INDENT]Server: #.#.#.19
Port 22
Type: SSH
Folder: /Office/Share
User name: <user name on server>
Password: <password on server>
[/INDENT]I get: Connection refused by server

Any thoughts on this problem would be helpful, Thanks.

---

### Post by critin on 2012-10-09
I've not ever tried to do a network through a server (I use Samba with simple lan), so I can't really help there, but did you make a workgroup in windows and add ubuntu to it with the workgroup password?

Will the server accept the password/user name?

---

