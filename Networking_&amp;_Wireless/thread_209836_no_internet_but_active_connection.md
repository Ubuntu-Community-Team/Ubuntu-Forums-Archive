---
title: "no internet but active connection"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by kunatz on 2006-07-05
hello community,

i have a big big problem with my internet connection. although i can ping any internet page, firefox, gaim, synaptics, ... cannot establish connection to the net. i even cannot open the config page of my router, but ping works

as i already said i am sitting behind a router, my connection is adsl.

so what am i doing wrong?


thx

---

### Post by DJ Scribblinni on 2006-07-05
post the command ```
ifconfig
```

---

### Post by kunatz on 2006-07-06
oh sure, should have known that. here it is
> eth0      Protokoll:Ethernet  Hardware Adresse 00:11:09:E8:46:42
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Basisadresse:0x2000

eth1      Protokoll:Ethernet  Hardware Adresse 00:11:09:E8:46:41
          inet Adresse:192.168.1.3  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::211:9ff:fee8:4641/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:1598 (1.5 KiB)  TX bytes:1854 (1.8 KiB)
          Interrupt:209 Basisadresse:0xe000

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)


i hope it's gonna help you and the german commands aren't confusing u too much!! eht1 is the used connection.


thx a lot

---

### Post by DJ Scribblinni on 2006-07-07
Well, I myself won't be able to tell you much, but perhaps something you could try to do, would be to disable the network card that you aren't currently using, which would be eth0.  eth1 has all the information needed to access any network.  It works for me sometimes.  The next thing to try after that would be to see if there are any DNS address listed in the network config.  Other than that, I wouldn't be too much of help....Hope something works for ya.

---

### Post by Ptero-4 on 2006-07-07
Check your router. Also ask your ADSL ISP if they have changed their IP/DNS information (some ISP's have software that reads your user-agent and if you're using linux it changes your IP/DNS randomly to twarth your conection).

---

### Post by kunatz on 2006-07-07
I should have mentioned, that i am running win xp on the same machine and internet works properly. so i think the router cannot be the problem.
i also used suse 10 and had no problem with the connection. another user in a german forum, who actually has the same problem like me in ubuntu, said that kubuntu 6.06 worked fine - it seems to be a gnome issue.

can anyone tell me how to change this value:
> UP BROADCAST RUNNING MULTICAST MTU:1500
my isp uses an mtu of 1454, i had to change that value in suse too


thx

edit
as DNS adress ubuntu automatically put in my router's IP

---

### Post by kunatz on 2006-07-10
Hmmm does anyone know how to change the MTU value? I am quite sure that's the problem

---

### Post by mips on 2006-07-10
Before adjusting the MTU try disabling IPv6

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

You can change the MTU as follows in the **/etc/network/interfaces** file:

```
# The primary network interface
iface eth0 inet static
     address 192.168.0.10
     netmask 255.255.255.0
     gateway 192.168.1.1
[COLOR=Red]**      mtu 1492**[/COLOR]
```

---

### Post by apoth on 2006-07-10
It could be a router filtering outgoing http maybe? Have you tried setting up a webserver and used destination/source port 80 the wrong way round?

---

### Post by kunatz on 2006-07-10
No I didn't try that but I can say that the internet on win xp on the same pc works fine, so I do not think, that it is a router problem.

---

### Post by kunatz on 2006-07-11
thx a lot mips now firefox and gaim are working properly!!

i am only worried about synaptic, which still cannot connect to the repositories - what am i doing wrong? is synaptic using a special port?

---

### Post by mips on 2006-07-11
I assume you are using the de. repositories. try removing the de. from your sources file and see if it helps.

---

### Post by kunatz on 2006-07-11
hmm don't know what i did, but now synaptic is working.

nevertheless i wanna say that you're great. thank you very much for your help!!

---

