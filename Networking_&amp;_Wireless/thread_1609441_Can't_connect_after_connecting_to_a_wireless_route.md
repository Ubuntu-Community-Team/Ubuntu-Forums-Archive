---
title: "Can't connect after connecting to a wireless router"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by gibsonsimswilson on 2010-10-30
I have very little understanding (ok no technical ability so be gentle)

Ubuntu 10.10 connects to a DSL modem without any problems - I mean I just plugged it in and it worked - GREAT

I bought a wireless router so I could connect my netbook and now my Ubuntu machine which is simply using a cable from the wireless router now DOES NOT connect.

I tried a windows machine on the wired connection from the wireless router and it connects without a problem.

OF course if I remove the wireless router from the chain, i.e. simply connect directly to the modem it works straight away.

I guess I have covered what happens - anyone know how I can fix this?

Thanks

Gibby

---

### Post by johnnytm on 2010-10-30
Without knowing the manufacturer and model of your wireless card it's kind of hard to do much. If you can find that out, it would be the first step. post the results of ```
sudo lshw -C network
``` ```
 iwconfig
``` and ```
ifconfig
```

---

### Post by gibsonsimswilson on 2010-10-30
Hi

Thanks for the reply but there is NO card..

I am simply connecting the ubuntu machine to the wireless router using a cable NOT wireless

cable--modem---cable---wireless router---cable---ubuntu machine

Take the router out of the chain and it connects immediately as before...

Thanks

---

### Post by elico on 2010-10-30
what do you mean by wont connect to the router?
first make sure that there is a wired connection.
then use the ifconfig to see your network connection status and ip address
the try the command

ping 8.8.8.8
(to google dns servers)

if you are getting reply from 8.8.8.8 that means you should try to edit the /etc/resolv.conf
and add the lines 
nameserver 208.67.220.220
nameserver 8.8.8.8

or instead the IP address of your local ISP dns servers.

---

### Post by johnnytm on 2010-10-30
If that's the case, I would suggest calling your ISP to see what settings are required for the router in order to connect to the internet such as is dchp automatic, is it ppoe, etc...... Depending on your ISP many of those settings can be different, but I would make sure they are all correct before looking further.

---

### Post by gibsonsimswilson on 2010-10-30
First my internet works fine I have been connected fine 
The problem starts when I connect the wireless router
USING A CABLE FROM THE WIRELESS ROUTER I now can not connect

If I switch the ubuntu machine for a windows machine - works no problem

Take away the router and the ubuntu machine connects straight away again


So all seems to work (using a windows machine no changes needed)

But when I connect the ubuntu (remember all cables I am not using the wireless) does not now connect

Thanks

---

### Post by gibsonsimswilson on 2010-10-31
Sorry I think my explanation was not too good

I have normal internet with a modem and my ubuntu machine works no problem

I bought a wireless router so I could use the wireless for another machine

THE UBUNTU MACHINE WOULD BE WIRED TO THE WIRELESS ROUTER VIA A CABLE - NOT WIRELESS CONNECTION

When I connected it up it does not connect to the internet, if I remove the wireless router it works fine

Now if I use a machine with windows connected to the wireless router with a cable, it works !!

So I think there is a problem with connecting the ubuntu machine with a cable to the wireless router

Thanks

Gibby

---

