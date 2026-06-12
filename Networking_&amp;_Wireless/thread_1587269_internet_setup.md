---
title: "internet setup"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by c2tarun on 2010-10-03
hi friends
recently i switched from windows to ubuntu and i m loving it.
now i have a BSNL broadband connection and i m unable to setup the internet using this broadband.
i assume that no one here is familier with BSNL broadband.
i exactly don't know what i m asking so let me explain a bit.

previously i was using win xp. in win xp to setup up the broadband i follow the following steps.

START>ACCESSORIES>COMMUNICATION>NEW CONNECTION WIZARD

then i choose the option "connect to internet"
then "setup my connection manually"
then "connect using a broadband connection that requires username and password"
then i provide there my ISP name
then userid and password provided to me by my ISP
then i can see an icon in network connections from control panel.
i simply open that icon click on connect and i can easily access internet.

can anyone tell me how to do this on ubuntu.

i m using ubuntu 10.04 Lucid.

thanx

---

### Post by amite on 2010-10-03
have u tried network manager's wired connection?
just i want to know whether u don't know to setup a network connection or have some specific problem during setup..

---

### Post by c2tarun on 2010-10-03
i tried that, but sorry i dont exactly know the settings there.
i created a new connection but dont know how to make it live.

---

### Post by c2tarun on 2010-10-03
guys there is one more problem.
when i m connecting lan wire and booting from XP, LAN light in my modem is glowing.
but when i am booting from ubuntu i see no light there.
i checked "ifconfig eth1" and my LAN card is there.
need help
plz

---

### Post by amite on 2010-10-03
i am mentioning how i used to connect to internet using sifi broadband........hope bsnl broadband have same procedure.
As you are using the same connection on windows machine so u can get the required information from ur windows machine...

-> right click on networkmanager applet and click on edit connection
-> click on "wired" tab and click on "add"
-> click on IPv4 setting tab and select manual method
-> Now enter IPv4 address in Address, subnet mask value in Netmask,gateway value in gateway and DNS server.Search domain won't be necessary.
-> Now check available to all user and connect automatically option.
-> Now click apply

Now as u insert ur connection wire in RJ45 connector port,it automatically detect and connect.

---

### Post by c2tarun on 2010-10-03
thanks
but i m still not getting the place to enter username and password provided to me by my ISP

---

### Post by dineshs on 2010-10-04
The method you are using is [COLOR="Blue"]Modem in bridge mode[/COLOR].Here you need a PPPoE dialler to connect/disconnect
Please try [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
By the way I suggest you try [COLOR="Blue"]Modem in PPPoE mode[/COLOR] so that you dont need a dialler,ie the connection will be always ON.Configuring different BSNL modems in PPPoE mode is explained [here]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html") under CPE/modem config
If you have any difficulties please post the result of```
sudo lshw -C network
```and```
ping 192.168.1.1 -c3
```

---

