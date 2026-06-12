---
title: "No connection to the internet???"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by Castrum on 2006-01-31
Hi,
After installation of  Kubuntu ,i dont have internet connection.

I have LAN connection ,cable direktly connected to Modem without Router.
I put manually my IP and everything but didn't help.

Then i tried this:
etc/network/interfaces:

#This file describe the network interfaces available on your system
#and how to active them.For more information, see interfaces(5).

#The loopback network interfaces
auto lo
iface lo inet loopback
adress 127.0.0.1
netmask 255.0.0.0


#This is a list of hotpluggable network interfaces.
#They will be activeded automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

auto eth0
iface eth0 inet static
adress 62.178.69.187
netmask 255.255.255.0
broadcast 62.178.69.255
gateway 62.178.69.1


Then i put  "ifconfig":

root@ubuntubadjo:~#ifconfig

eth0 Link encap:Ethernet HWaddr 00:11:d8:B1:A7:3F
inet addr:62.178.69.187 Bcast:62.178.69.255 Mask:255.255.255.0
inet6 addr:fe80::211:d8ff:feb1:a73f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets :1067 errrors:0 dropped:0 overruns:0 frame:0
TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:654839 (639.4 KiB) TX bytes:2297 (2.2KiB)
Interrupt:21 Base address:0xa000

lo Link ancap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:81 errors:0 dropped:0 overruns:0 frame:0
TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:6119 (5.9 KiB) TX bytes:6119 (5.9KiB)

I have sent the ping to my IP under Root Directory and every Package i sent was transmitted and recieved. 

But in Home Directory they get all lost.

Do you have any ideas?

bye

Castrum

---

### Post by Who on 2006-01-31
You're doing all the right things!

Seeing as the device seems to be configured fine the issue may well be with permissions
You can view and modify which groups a user is part of using the System--Administration-->Users and Groups

There will be a group called networking or something (I'm not on Ubuntu now) - and you'll need to be a member to use the network.

HTH

Who

---

### Post by mips on 2006-01-31
Do I understand correct, you have no router ? If you dont then your config wont work as you require pppoe and that is where the tcp/ip settings are configured.

The fact that you are connecting via ethernet tells me you might possibly acttually have a router :)

What is the Brand & Model number of your "*modem*" ???
Who is your ISP, web link please ???

---

### Post by Castrum on 2006-01-31
for WHO:
no groups called networking....

for Mips:

I have NO Router.
Modem: ARRIS ,Model:CM450B
P/N:TC00EA1450
Serial NO.499BM5254523944

ISP>chello,

[http://www.chello.at]("http://www.chello.at")

and for English

[http://www.chello.com]("http://www.chello.com")

thanks for your Help!

bye

Castrum

---

### Post by mips on 2006-01-31
Have you set your machine up to use the proxy server, **proxy.chello.at:8080** ?

---

### Post by mips on 2006-01-31
From a dos prompt in Windows please supply the output of ipconfig /all

---

### Post by mips on 2006-01-31
[http://www.chello.at/Support/Frage_und_Antwort/Technisches/](http://www.chello.at/Support/Frage_und_Antwort/Technisches/)

> Ländereinstellungen - Region Wiener Neustadt
Für die Region Wiener Neustadt gelten folgende chello-Konfigurationen:

E-Mail
POP3 (eingehend)	pop.chello.at
SMTP (ausgehend)	mgate.chello.at
Web
Proxy-Server	proxy.chello.at (port 8080)
News
News-Server	news.chello.at
DNS
DNS	195.34.133.10, 195.34.133.11
Kunden-Homepage-Server
Web-Server	members.chello.at
IRC-Server
irc.chello.at (Port 6667)
Auto proxy configuration
[http://www.chello.at/autoproxy/](http://www.chello.at/autoproxy/) (for all chello customers)



Ländereinstellungen - Region Wien
Für die Region Wien gelten folgende chello-Konfigurationen:

E-Mail
POP3 (eingehend)	pop.chello.at
SMTP (ausgehend)	mgate.chello.at
Web
Proxy-Server	proxy.chello.at : 8080
News
News-Server	news.chello.at
DNS
DNS	195.34.133.10, 195.34.133.11
Kunden-Homepage-Server
Web-Server	members.chello.at
IRC-Server
irc.chello.at (Port 6667)
Auto proxy configuration
[http://www.chello.at/autoproxy/](http://www.chello.at/autoproxy/) (für alle chello Kunden)

Wichtig: chello student connect Kunden müssen den jeweiligen Uni Proxyserver verwenden! (Die Einstellungen wechseln regelmäßig - ca. jedes halbe Jahr - und können bei der jeweiligen Universität erfragt werden)

Dies sind die letzten Konfigurationseinstellungen die wir haben:
Uni Wien: tk-proxy.univie.ac.at (Port 3128)
TU Wien: proxy.tuwien.ac.at (Port 1080)
WU Wien: proxy.wu-wien.ac.at (Port 8080)

Also set your DNS servers as per the above in your resolv.conf file.
Use the correct proxy server. You might have to configure the proxy GLOBALLY under your network settings and not just in your web browser.

---

### Post by Castrum on 2006-01-31
thanks,

I am getting used to Linux ,everything is a new for me ,how can i find resolv.conf file.and ,do i need a command to put DNS?

cheers

Castrum

---

### Post by Castrum on 2006-01-31
I didn't set my machine  to use the proxy server, proxy.chello.at:8080.i dont surf through proxy.

---

### Post by mips on 2006-01-31
**sudo gedit /etc/resolv.conf**

---

### Post by Castrum on 2006-01-31
when i put this command in terminal konsole "sudo gedit /etc/resolv.conf " then   i recieve the message "sudo gedit unkown command"???

---

### Post by mips on 2006-01-31
Hehe, change your profile, it says you are using Ubuntu, not Kubuntu.

**kdesu kate /etc/resolv.conf**

add:
nameserver 195.34.133.10
nameserver 195.34.133.11

---

### Post by Castrum on 2006-01-31
i try "sudo gedit /etc/resolv.conf" then i recieve:sudo get "unkown command"

---

### Post by mips on 2006-01-31
Hehe, change your profile, it says you are using Ubuntu, not Kubuntu. Are you using Ubuntu or Kubuntu ??? For Kubuntu use the command below to edit your file.

**[COLOR="Red"]kdesu kate /etc/resolv.conf[/COLOR]**

add:
nameserver 195.34.133.10
nameserver 195.34.133.11


Alternatively use any other text editor to edit thoe files with, remeber to use sudo.

---

### Post by Castrum on 2006-02-01
sorry for writing  the same message two times: i try "sudo gedit /etc/resolv.conf" then i recieve:sudo get "unkown command"bbla bla bla .

i using KUBUNTU.
and it works when i put tne command "sudo kate /etc/resolv.conf".
I have wrote in resolv.conf this and save all :

add:
nameserver 195.34.133.21
nameserver 195.34.133.22

But doesent take any change ,i stiil dont have internet.I ask you stupid questions ,sorry,do i have to write instead of "nameserver" ; "chello" or "chello.at"

my IP configuration under Windoes XP:

Windows-IP-Konfiguration

Hostname. . . . . . . . . . . . . : none-als8gkwtle
Primäres DNS-Suffix . . . . . . . :
Knotentyp . . . . . . . . . . . . : Unbekannt
IP-Routing aktiviert. . . . . . . : Nein
WINS-Proxy aktiviert. . . . . . . : Nein
DNS-Suffixsuchliste . . . . . . . : chello.at

Ethernetadapter LAN-Verbindung:

Verbindungsspezifisches DNS-Suffix: chello.at
Beschreibung. . . . . . . . . . . : NVIDIA nForce Networking Controller
Physikalische Adresse . . . . . . : 00-11-D8-B1-A7-3F
DHCP aktiviert. . . . . . . . . . : Ja
Autokonfiguration aktiviert . . . : Ja
IP-Adresse. . . . . . . . . . . . : 62.178.69.187
Subnetzmaske. . . . . . . . . . . : 255.255.255.0
Standardgateway . . . . . . . . . : 62.178.69.1
DHCP-Server . . . . . . . . . . . : 195.34.134.196
DNS-Server. . . . . . . . . . . . : 195.34.133.21
                                          195.34.133.22
Lease erhalten. . . . . . . . . . : Mittwoch, 01. Februar 2006 10:15:30
Lease läuft ab. . . . . . . . . . : Dienstag, 19. Jänner 2038 04:14:07

bye

castrum

---

### Post by mips on 2006-02-01
What response do you get from:
ping 62.178.69.187
ping 62.178.69.1
ping 195.34.134.196
ping 195.34.133.21
ping 195.34.133.63
ping 213.46.242.72
ping 198.133.219.25

---

### Post by Castrum on 2006-02-01
ping 62.178.69.187 --- all packets transmitted and received
ping 62.178.69.1 ----   all packets transmitted and received
ping 195.34.134.196--network is unreachable
ping 195.34.133.21--network is unreachable
ping 195.34.133.63--network is unreachable
ping 213.46.242.72--network is unreachable
ping 198.133.219.25--network is unreachable

---

### Post by Who on 2006-02-01
[QUOTE=Castrum]when i put this command in terminal konsole "sudo gedit /etc/resolv.conf " then   i recieve the message "sudo gedit unkown command"???[/QUOTE]

Try then sudo kwrite /etc/resolv.conf

sudo means 'gain super user/administrator privelidges for the next command, gedit is Gnome text editor, Kwrite the equivalent for KDE, and /etc/resolv.conf is a configuration file on your disk :)

---

### Post by mips on 2006-02-01
Something funny here, your configuration seems ok. The pings indicate you can connect to your local gateway but not beyond that point. I can even ping you local gateway from my pc.

Please post output of **route -n**


> I ask you stupid questions ,sorry,do i have to write instead of "nameserver" ; "chello" or "chello.at"

No, just add the two lines as indicated.

Also add this line to your /etc/resolv.conf file:
```
search chello.at
```

---

### Post by Castrum on 2006-02-01
Kernel IP routing table

Destination:62.178.69.0

Gateway:0.0.0.0

Genmask:255.255.255.0

Flags:U

Metric:0

Ref:0

Use:0

iface:eth0

---

### Post by mips on 2006-02-01
Ok, you have no default route.

In a terminal type:
sudo route add default gw 62.178.69.1 dev eth0

---

### Post by mips on 2006-02-01
When you have done the above and then do a route -n it should look something like this:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
62.178.69.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         62.178.69.1     0.0.0.0         UG    0      0        0 eth0

Test you internet connectivity now and it should work.

---

### Post by mips on 2006-02-01
Hehe, I can see you are working now ! Or is that the windows pc ?

---

### Post by Castrum on 2006-02-01
Hey,i don't know what i say , i can belief, it's working ,it's working !!!!!
Big Thanks Mips,i try from sunday until today  this problem to disassociate.
Thanks for your patience!

i invite you of some  Beers .

Castrum 

cheers

---

### Post by mips on 2006-02-01
[QUOTE=Castrum]Hey,i don't know what i say , i can belief, it's working ,it's working !!!!!
Big Thanks Mips,i try from sunday until today  this problem to disassociate.
Thanks for your patience!

i invite you of some  Beers .

Castrum 

cheers[/QUOTE]

Glad to hear it is working. Should have asked you for the route -n earlier ;)

I'll take you up on the beer offer if I'm ever in Wien.

PLEASE install a firewall right now as your PC is directly connected to the net with a public IP Address. Maybe look at Gaurddog.

Now that you are online you might want to upgrade your installation to the latest by doing:
sudo apt-get update
sudo apt-get dist-upgrade (to upgrade your entire distribution, alternatively sudo apt-get upgrade)

---

### Post by Castrum on 2006-02-01
[QUOTE=mips]Glad to hear it is working. Should have asked you for the route -n earlier ;)

I'll take you up on the beer offer if I'm ever in Wien.

PLEASE install a firewall right now as your PC is directly connected to the net with a public IP Address. Maybe look at Gaurddog.

Now that you are online you might want to upgrade your installation to the latest by doing:
sudo apt-get update
sudo apt-get dist-upgrade (to upgrade your entire distribution, alternatively sudo apt-get upgrade)[/QUOTE]

every time i restart my PC,i have to go to root and put this command :"sudo route add default gw  62.178.69.1 dev eth0" .Is there any way i can save  it,so it works automatically?
One more question,do you know maybe  why after 1 hour or so many different colors appear on my screen,and they cover everthing.Maybe i must download  new driver for my graphic card?(128 MB Win Fast 6600 Nvidia)

cheers 

Castrum

---

### Post by mips on 2006-02-01
Try this

**kdesu kate /etc/network/interfaces**
```
auto eth0
iface eth0 inet static
adress 62.178.69.187
netmask 255.255.255.0
broadcast 62.178.69.255
gateway 62.178.69.1
**[COLOR="Red"]up route add default gw 62.178.69.1 dev eth0[/COLOR]**

```

Save and exit.

Let me know if it works.

---

### Post by Castrum on 2006-02-01
hey mips,

 yes it's working .Thanks!

cheers

Castrum

---

