---
title: "Wireless Printing Through Network"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by izizzle on 2009-03-06
Ok, so here is my situation. I have a Samsung ML-2010 printer connected to a print server on my network. The print server is a D-link DPR-1260. I need to figure out how to print with this! When I go to System > Administration > Printing > I do not see an option for ipp. I only see AppSocket/HP Jetdirect, Windows Printer via SAMBA, LPT#1 Port, and Other. However, I am able to ping the print server and access it's setup page from firefox. 

What should I do to be able to print wirelessly? Any help would be much appreciated.

---

### Post by izizzle on 2009-03-07
Bump...Anyone??

---

### Post by hexanol on 2009-03-07
Well, there should be no difference between printing with a wired or wireless connection, except if there's complex settings you can chnage in your router/access point.

I don't understand why there is no option for IPP on your computer, I personnaly have it, and it detects automatically printers using IPP. I'm also using Ubuntu 8.10.

---

### Post by izizzle on 2009-03-07
Well, for some reason it does not detect ipp on my computer, and I have to figure out what the problem here is...

---

### Post by ugm6hr on 2009-03-07
> **izizzle said:**
> Well, for some reason it does not detect ipp on my computer, and I have to figure out what the problem here is...

The Printer configuration doesn't detect anything.  It just lists all the options.

I am on Hardy, with no printers to be seen, and I still get all the options.

Have you modified a default Ubuntu?  Are you using 8.10 Gnome Ubuntu?

---

### Post by warp99 on 2009-03-07
Set the printer up as a socket printer as follows:

socket://<ip_address_of_printer>:9100

I have a D-Link DPR-1260 and a Samsung ML-2510 working perfectly with this setup.

Edit:

AppSocket/HP Jetdirect is the socket printer extension you need.

---

### Post by izizzle on 2009-03-07
I'll try that warp99. I am on Original Ubuntu 8.10 64-Bit LiveCD. I want to make sure I can get everything working before I do the actual install.

---

### Post by warp99 on 2009-03-07
> **izizzle said:**
> I'll try that warp99. I am on Original Ubuntu 8.10 64-Bit LiveCD. I want to make sure I can get everything working before I do the actual install.

I made a mistake on the print server. My print server **is** a DPR-1260, so if you run into trouble I can help you with the setup.

---

### Post by izizzle on 2009-03-09
Alright, so. I used the method that Warp suggested and we have partial success. The test page didn't print, but the "On-Line" light on the printer started blinking and you can hear the printer humming (usually it's just silent), and the printer is still active (It still has not stopped blinking and humming). What should I do to get it to print?

---

### Post by warp99 on 2009-03-09
Cycle the printer, then cycle the print server. Try the test print again. If it doesn't work you I can walk you through how the setup should be on the print server and the computer.

---

### Post by izizzle on 2009-03-09
Well whada'ya know! It printed on the same job, except it took like 2 hours. I can't thank you enough Warp, but whats keeping the hold-up? 2 Hours is quite a bit.

---

### Post by warp99 on 2009-03-09
Sometimes the print server or the printer for some reason will just get stuck. I use the AppSocket/HP Jetdirect port with Windows clients and the same things happens every once in a while, so it's not OS specific.

Best thing is to use static addresses instead of DHCP because with a small network DHCP becomes a PITA. Check the settings on the DPR-1260 through the web interface under "Advanced". Make sure that  "Raw TCP Port" is enabled, "LPR/LPD" is disabled, and "UPnP" is disabled. On your Linux, Mac, or Windows clients make sure that your printing to TCP port 9100. Windows clients can also use TCP port 9100 but you have to setup an additional printer port, takes two minutes.

Need trick if you use static IPs is that you can add the address to the host file, then give them a name:

```
sudo gedit /etc/hosts
```
then add the names including printers:
```
127.0.0.1 localhost.localdomain localhost
192.168.0.1 alice
192.168.0.4 caterpillar
192.168.0.5 mad_hatter
192.168.0.7 rabbit
192.168.0.8 cheshire_cat
192.168.0.10 samsung

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

That way to access the print server, or any other machine on your network including routers, you only need to give the host name and not the address. :)

Edit:

You need to reload the networking daemon for changes to take effect:

```
sudo /etc/init.d/networking restart
```

or just reboot.

---

### Post by warp99 on 2009-03-09
One more thing with the DPR-1260 is that sometimes when the unit is idle it doesn't wake to print. So if the unit has been sitting for a while you should ping the print server before you start printing:

```
ping -c 15 192.168.0.10
```

I have a MythTV server that runs 24/7 with a crontab that pings the print server every 5 minutes so the port stays alive. This may not be an option for you, but just be aware about the idiosyncrasies with the DPR-1260.

---

