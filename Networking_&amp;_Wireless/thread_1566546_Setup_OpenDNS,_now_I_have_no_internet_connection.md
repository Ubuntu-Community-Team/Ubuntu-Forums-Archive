---
title: "Setup OpenDNS, now I have no internet connection"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by mutuma on 2010-09-02
I have an Asus EeePC 1001p running Ubuntu 10.04.

I recently setup OpenDNS, following the instructions found here: [http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/](http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/)

I reset my computer and now I only get "Server not found" in Firefox. 

How can I get my connection back and how can I get OpenDNS working?

---

### Post by mutuma on 2010-09-02
Tried "sudo dhclient" 
Attempted several times to get an IP
"No DHCPOFFERS received. No working leases in persistent database - sleeping."

BTW the network at my school requires me to login to Websense to access the internet.

---

### Post by zipizap on 2010-09-04
> **mutuma said:**
> Tried "sudo dhclient" 
BTW the network at my school requires me to login to Websense to access the internet.

I guess that maybe the network at your school may need some specific intranet DNS configuration... 


> 
How can I get my connection back and how can I get OpenDNS working?     


Anyway, to undo the changes you made following the instructions of the site you mentioned (which are the same as indicated by the official OpenDns webpage), you can execute this in a console:

```

#Make a backup of dhclient.conf (just in case)
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.withOpenDns

#Remove the line of the OpenDns servers from dhclient.conf
sudo sed --in-place '/^prepend domain-name-servers 208.67.222.222,208.67.220.220;/s' /etc/dhcp3/dhclient.conf

#Put the connection interface (assumed it is eth0) down and up again
  #NOTE - about the interface 
  #  If you are connecting with a cable, most probably the interface is eth0
  #  If you are connecting with wireless, then your interface will probably *not* be eth0, 
  #  but you can see the name of the wireless interface in the left side after running
             iwconfig 2>&1 | sed '/no wireless/d'
  #  Some wireless interfaces can  be wlan0, ath0, mad0, or even eth1... see what's yours if you are connecting with wifi
   # After knowing the connection interface, if it is not eth0 then change in the following line, the eth0 by your interface

sudo ifdown eth0 && sudo ifup eth0
  

```

Now your original configuration (previous to the OpenDns change) has been restored and you should again try to connect. (and there is no need to reboot, that is a Windowz bad-habit that got us all fooled - in linux things actually work right without violence :) )

Tell us how it went :) that's my satisfaction for helping :)

---

