---
title: "3com router, unable to config - please help"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by Criminel on 2010-06-08
Hi,
Under ubutntu 10.04 I'm unable to acces the config page 192.168.1.1
the browser just won't  open th page (and I have Internet as I'm writing this right now).
What should I do?

---

### Post by mikewhatever on 2010-06-08
Disable noscript and addblock+ on that page, that is, if you use them.

---

### Post by Criminel on 2010-06-08
> **mikewhatever said:**
> Disable noscript and addblock+ on that page, that is, if you use them.

Hi,
Just did that. 
Still no results.
Thanks anyway.

---

### Post by mikewhatever on 2010-06-08
Is there anything else you use that might block that particular address? Squid proxy? Host file?

---

### Post by Criminel on 2010-06-08
Not  that I'm aware of.

---

### Post by PRC09 on 2010-06-08
Are you sure of the address,you could try 192.168.1.254 or 192.168.0.1.Different routers have a variety of addresses.Just a guess on my part....

---

### Post by Criminel on 2010-06-09
> **PRC09 said:**
> Are you sure of the address,you could try 192.168.1.254 or 192.168.0.1.Different routers have a variety of addresses.Just a guess on my part....
I've tried several adresses with no results. Still unable to config.
Thanks anyway.

---

### Post by Criminel on 2010-06-09
Any of you have wireless routers working with 10.04?
Because in my system it just doesn't seem to work at all.

---

### Post by PRC09 on 2010-06-10
If you are trying to connect via wireless then try cabled in and see if it will open then.You might also check to see if your ssid is not hidden.Dont know if any of this helps but have seen hidden wireless give me all kinds of weird problems...You could also try to ping the router itself and see what happens.....

---

### Post by Criminel on 2010-06-11
> **PRC09 said:**
> If you are trying to connect via wireless then try cabled in and see if it will open then.You might also check to see if your ssid is not hidden.Dont know if any of this helps but have seen hidden wireless give me all kinds of weird problems...You could also try to ping the router itself and see what happens.....

Hi,
All my attempts are wired -in (I have a dsl connection). What do you mean by "ping the router itslelf"?

---

### Post by Criminel on 2010-06-11
Additional info (please help me if you can):

Ping 192.168.1.1 via terminal gives me "no response" answer.
Telnet opnening of 192.168.1.1 gives me "unable".
ifconfig on terminal gives me this:
eth0      Link encap:Ethernet  direcciónHW 00:19:66:2b:33:ca  
          Dirección inet6: fe80::219:66ff:fe2b:33ca/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:10742 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:10511 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:7909084 (7.9 MB)  TX bytes:1889058 (1.8 MB)
          Interrupción:27 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:13760 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:13760 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:3043688 (3.0 MB)  TX bytes:3043688 (3.0 MB)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:190.172.4.123  P-t-P:200.63.148.3  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1492  Métrica:1
          Paquetes RX:10061 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:10153 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:7627386 (7.6 MB)  TX bytes:1598101 (1.5 MB)

---

### Post by mikewhatever on 2010-06-11
Interesting. I take it ppp0 is the dsl connection, is it not? How about the output of **nm-tool**?

---

### Post by Criminel on 2010-06-12
PPP0 is indeed my DSL connection.
For nm-tool:

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unmanaged
  Default:           no
  HW Address:        00:19:66:2B:33:CA

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

---

### Post by mikewhatever on 2010-06-12
Was the internet connected when you posted it? I was hoping it might reveal the router's gateway address.

---

### Post by Criminel on 2010-06-12
Yes, internet was ON.

DSL goes to my modem, from there to the router (it it also ON) and from the router to my PC's CPU.

Any ideas?

---

### Post by PRC09 on 2010-06-13
I am no expert on this but if you go to System > Admin > Network Tools and select your ethernet connection from the dropdown menu it should list your ip address. Then from the top menu again select Netstat and hit Routing Table Information and then hit the Netstat button.The screen that is displayed should list your gateway info on one of the lines.At least on mine it does.....

---

### Post by Criminel on 2010-06-13
Thanks PRC09. What am I supossed to do with the ifo when I get it?
I have my IP adress and the netstat info. What's next?

---

### Post by PRC09 on 2010-06-13
I just thought that if you had the gateway address then you may be able to access the config page. Just what are you trying to configure?If you have all that info and still cannot access the config page I am at a loss.What does the browser say when you type in the address???

---

### Post by Criminel on 2010-06-14
> **PRC09 said:**
> I just thought that if you had the gateway address then you may be able to access the config page. Just what are you trying to configure?If you have all that info and still cannot access the config page I am at a loss.What does the browser say when you type in the address???

Hi,
I'm trying to configure my router so my netbook can access internet via wireless.  When I type the adress of the config page (or the IP given by netsat) the results is either a "can't connect to the page" message or the browser stays idle.
Trying to acces the router via telnet (192.168.1.1 or its variations) gives a consistent "unable to connect" message.
Additionally, I've tried to configure the router from the netbook in wireless mode (the netbook runs a Win 7 SO) and I do can access the config page, but  the internet in my wired PC get s cut out this way.

Any other ideas will be appreciated.

---

### Post by Criminel on 2010-06-14
Also:
I've noticed that the config page can be accesed without any trouble via an IE browser (but I don't have one, of course, in my PC). 
Can this be a bug from Mozilla and other similar browsers? is there any shortcut if so?

---

### Post by PRC09 on 2010-06-14
If your router is already broadcasting wireless and you can access it from win 7 then maybe you dont have the drivers for your cards installed..Check in System > Admin > Hardware drivers and see if they show up.If so activate and you hould be ready to go...Just a thought....

---

### Post by Criminel on 2010-06-14
> **PRC09 said:**
> If your router is already broadcasting wireless and you can access it from win 7 then maybe you dont have the drivers for your cards installed..Check in System > Admin > Hardware drivers and see if they show up.If so activate and you hould be ready to go...Just a thought....

Done it already. No 3rd party (or other) drivers show up.... I guess I'll die without an answer for this problem.

---

### Post by PRC09 on 2010-06-14
Last try......Is the page a flash or java login page, try to install both if you havent tried already...Other than that I am lost....

---

### Post by Criminel on 2010-06-15
> **PRC09 said:**
> Last try......Is the page a flash or java login page, try to install both if you havent tried already...Other than that I am lost....

Flash and Javascripts are running OK. We're both lost, I guess.

---

### Post by Criminel on 2010-06-15
Another bit of additional info:
I acctivate my DSL connection via terminal "pon dsl-provider" "poff" commands.
The connections lits under the System Administration / Network Tools/  is empty (I mean, no dsl or other connection is listed). Is this normal?

---

### Post by Criminel on 2010-06-30
Still no solution.
Help please?

---

