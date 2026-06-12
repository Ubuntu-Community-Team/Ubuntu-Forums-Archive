---
title: "Lenovo T500 F3507g with GPS"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by erik___ on 2008-12-04
The F3507g is recognized in network manager although it dosent seem to work.So this is what I did to make it work:

1. remove the pin from your SIM card. I put the SIM in my cellphone and removed it. 
2. Edit /etc/wvdial.conf to this:

[Dialer gps]
Modem = /dev/ttyACM0
Init1 = AT*E2GPSCTL=1,5,1
Init2 = AT*E2GPSNPD

[Dialer on]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=1

[Dialer off]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=4

[Dialer connect]
Modem = /dev/ttyACM1
Init1 = AT 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","net.tre.se"
Stupid Mode = 1
Modem Type = USB Modem
Baud = 460800
ISDN = 0
Phone = *99#
Password = dummy
Username = dummy


3. edit the /etc/wvdial.conf with your APN settings.(net.tre.se is an example). 
4. in the network  manager applet: deactivate your network. Otherwise your /etc/resolv.conf will get messed up. (this is where the DNS names are written down). 
5. turn on modem in termina.              #sudo wvdial on
6. connect                                #sudo wvdial  connect
7. Firefox  will not work since it uses network manager to get connection status. So dissable this with: [http://www.brunier.nl/?p=61](http://www.brunier.nl/?p=61)
8. you are now connected. 

9. when done, put F3507g back to sleep    #sudo wvdial off
----

GPS
1. turn on modem                          #sudo wvdial on
2. turn on gps                            #sudo wvdial gps
3. start gpsd on /dev/ttyACM0             #sudo gpsd /dev/ttyACM0
4. you now have GPS so confirm it with    #xgps
5. when done put modem back to sleep      #sudo wvdial off   
                                          #sudo pkill gpsd

Good luck.

---

### Post by torgnyj on 2009-07-08
Hi!

Just wanted to point out that it is possible to get the f3507g modules working with NetworkManager and there even is a GPS Control sw available at [http://sourceforge.net/apps/mediawiki/mbm/](http://sourceforge.net/apps/mediawiki/mbm/)

The above page contains installation/usage instructions for both NetworkManager and the GPS.

---

