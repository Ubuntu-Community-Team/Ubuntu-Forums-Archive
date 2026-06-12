---
title: "Gray hair from nxserver :((((("
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by djevlen on 2012-03-25
Hi guys.
Using ubuntu 10.04 LTS

server boards has two network cards

server is configured so that one of them is only for inet and other one is for local only.

Here is the interfaces config :
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet static
address 192.168.0.104
netmask 255.255.255.0


Then I install open ssh server.
If i leave it default and install the free version of nx server from nomachine then it works out of the box.

But i want to limit ssh acces only to my local network so i edit the sshd.conf and uncomment ListenAddress and enter ip : ListenAddress 192.168.0.104

ssh is now restricted only to the network card that has no internet and it works fine but as soon i change sshd config nxserver stop working. i tried everything and still no luck :((((
 !!! I want to bind NX server to specific eth0 or eth1 or IP


Please HELP ME !!

this is the install log from nx (i tried edit server.conf and node.conf with no luck

heres the warning from installlog :

 700 WARNING: Error when trying to connect to NX server. Error is:
NX> 700 WARNING: ssh: connect to host 127.0.0.1 port 22: Connection refused
NX> 700 WARNING: NX has been configured to use the SSH server on default port
NX> 700 WARNING: 22 but no SSH daemon is listening on this port. When the
NX> 700 WARNING: installation completes, please ensure that SSHD is installed
NX> 700 WARNING: and is up and running. If you want to contact SSHD daemon on
NX> 700 WARNING: a port different from 22, you need to configure NX Server and
NX> 700 WARNING: Node accordingly. More information is available on the NoMachine
NX> 700 WARNING: Knowledge Base at: [http://www.nomachine.com/kb/index.php](http://www.nomachine.com/kb/index.php)
NX> 700 Installation of NX server was completed with warnings.



After editing in the server.cfg the login got litle ruther  it even says downloading session information but in the end it change its mind and connectio refused . Here are som details : 

Info: received data in err channel from NX Node: 'ssh: connect to host localhost port 22: Connection refused
' (NXNodeExec)
Info: NX Node out channel was closed (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: A011075D. To get detailed information about
NX> 595 ERROR: the error search for the string A011075D in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

Hope some one can help mere here...

greets

---

