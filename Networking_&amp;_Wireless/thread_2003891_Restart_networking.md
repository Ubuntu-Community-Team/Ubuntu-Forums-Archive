---
title: "Restart networking"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by holtfox on 2012-06-14
Ubuntu 12.04
After I remote desktop into my Ubuntu system, the networking of my Ubuntu system stops working. 

My plan was to restart the adapter using ifconfig. I am trying to do a ifconfig wlan0 down which hangs. (I even try to kill that process and can't.)

Are there other ways to restart the networking component.  I have also tried to kill NetworkManager and cannot.

I can restart the system and everything is fine but that sucks.

---

### Post by papibe on 2012-06-14
Hi holtfox.

Try this:
```
sudo service network-manager restart
```
Tell us how it goes.
Regards.

---

### Post by holtfox on 2012-06-14
```
sudo service network-manager restart
```

The command just hangs.  Can't kill that process either.

---

### Post by holtfox on 2012-06-14
Another point

I am using a network adapter connected to a usb port.  After I physically disconnected the adapter and plugged it into another port, the network services restarted perfectly.  

I don't know if that helps coming up with a set of commands to restart the networking services.

Thanks

---

### Post by apiper on 2012-08-12
> **holtfox said:**
> ```
sudo service network-manager restart
```

The command just hangs.  Can't kill that process either.

The command isn't hanging, its been terminated because the network connection you're using has been closed by the command you executed, so the command cannot complete.

The way around this chicken-and-egg situation is to execute the command from inside a 'screen' session:

1) Install 'screen' (apt-get install screen) you only need to do this once
2) type "screen" <enter> <enter>
3) Execute the "sudo service network-manager restart" command. The terminal session will 'hang' because the network connection has been closed.
4) Open a new connection
5) type "screen -x" to re-connect to the screen-session started in step 2
6) you should now see the result of the "sudo service network-manager restart" command

---

### Post by NTL2009 on 2013-06-26
JUST FYI: I am not the OP, but my ISP was up/down this AM (bad storms, and I am on fixed wireless).


The ISP came up later, and I finally got up on a wired connection, but my wireless would just spin and time-out. This command:
[I]
( sudo service network-manager restart )[/I] 

worked for me. I was up in a few seconds - THANKS!!!


BTW, I got the following messages as it did its thing:

*network-manager stop/waiting*
*network-manager start/running, process 32693*



-NTL2009

---

### Post by VenturaVan on 2013-06-27
If you just want a clean restart of the interface you are working on WITHOUT restarting the network manager or anything else just use the following commands after you modify any of your network files:

sudo ifdown eth0

sudo ifup eth0

substitute your connection name for "eth0" :-)

---

