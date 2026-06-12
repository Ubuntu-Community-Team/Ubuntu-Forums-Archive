---
title: "Mythtv won't recognise backends?"
date: 2011-08-25
forum: Multimedia Software
---

### Post by bgrohe on 2011-08-25
I wasn't sure what forum to post into, so I chose this one. My problem is that I can't get the frontend and backend on the same computer to connect. When I ran thos command:
```
mysql> SELECT * FROM settings WHERE value LIKE '%Server%';
```
I get this: 
```
+----------------------------------------------------+--------------------------------------+----------------------+
| value                                              | data                                 | hostname             |
+----------------------------------------------------+--------------------------------------+----------------------+
| BackendServerIP                                    |                                      | brian-ubuntu-desktop |
| BackendServerPort                                  | 6543                                 | brian-ubuntu-desktop |
| MasterServerIP                                     | 127.0.0.1                            | NULL                 |
| MasterServerPort                                   | 6543                                 | NULL                 |
| ServerHaltCommand                                  | sudo /sbin/halt -p                   | NULL                 |
| upnp:UDN:urn:schemas-upnp-org:device:MediaServer:1 | 256a89b4-1266-49ca-9ac7-f0b4b4641e7f | brian-ubuntu-desktop |
| BackendServerIP                                    |                                      | brian-ubuntu-desktop |
| BackendServerPort                                  | 6543                                 | brian-ubuntu-desktop |
| BackendServerIP                                    | 127.0.0.1                            | front                |
| BackendServerPort                                  | 6543                                 | front                |
+----------------------------------------------------+--------------------------------------+----------------------+
10 rows in set (0.02 sec)

```
It doesn't seem to save the ip address for either backend. 
Additonal info:
I am using mysql root account as that was the only one I could figure out how to work.
My tv tuner card is a sabrent tv-pcirc

Thanks in advanced
Brian

---

### Post by fenian on 2011-08-26
Run the backend set up for mythtv,in the terminal enter...

> mythtv-setup

In the "General" section on the first page you can set the local and master IP addresses.I use the actual address ie: 192.168.1.116 because I have multiple frontends if you are running the backend and frontend on the same machine use 127.0.0.1 as your IP address.Make any changes and quit the backend setup.

Next open Mythtv frontend...
 
> mythfrontend --service

Navigate to Utilities/Setup>Setup>General

On the first page 
Set the hostname to localhost
Set the Database name to mythconverg
set the User to Mythtv
Set the password (to find your password go to /etc/mythtv/mysql.txt)


In the future you may want to post Mythtv questions in the Mythbuntu section of the third party projects section.

---

### Post by bgrohe on 2011-08-26
I did what you said and I still get the unable to connect to master, problem :confused:

What else do you think can be causing it.

Also, can I move this thread to mythbuntu or can only moderators do that?

Brian

EDIT: I ran the command I did the first time and got this:
 +----------------------------------------------------+--------------------------------------+----------------------+
| value                                              | data                                 | hostname             |
+----------------------------------------------------+--------------------------------------+----------------------+
| BackendServerIP                                    |                                      | brian-ubuntu-desktop |
| BackendServerPort                                  | 6543                                 | brian-ubuntu-desktop |
| MasterServerIP                                     | 192.168.1.6                          | NULL                 |
| MasterServerPort                                   | 6543                                 | NULL                 |
| ServerHaltCommand                                  | sudo /sbin/halt -p                   | NULL                 |
| upnp:UDN:urn:schemas-upnp-org:device:MediaServer:1 | 256a89b4-1266-49ca-9ac7-f0b4b4641e7f | brian-ubuntu-desktop |
| BackendServerIP                                    |                                      | brian-ubuntu-desktop |
| BackendServerPort                                  | 6543                                 | brian-ubuntu-desktop |
| BackendServerIP                                    | 192.168.1.6                          | front                |
| BackendServerPort                                  | 6543                                 | front                |
| UPnP/UDN/MediaServer                               | 46c75760-df60-4641-bcd2-771d0c044a32 | front                |
| UPnP/UDN/MasterMediaServer                         | eccfdfdd-a798-4c85-9e30-37a77ccde00e | front                |
+----------------------------------------------------+--------------------------------------+----------------------+
12 rows in set (0.00 sec)

---

