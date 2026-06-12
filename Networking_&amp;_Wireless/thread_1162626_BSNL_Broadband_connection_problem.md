---
title: "BSNL Broadband connection problem"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by vivekrocks on 2009-05-17
Hello,

I have installed ubuntu 8.04 Hardy Heron on my HP 6720s Compaq with 1.4 GHz Intel Core 2 Duo CPU and 1 GB RAM.
I configured my BSNL Broadband internet connection using a DSL modem. Following is the code i used for configuration of Point-to-point over ethernet connection:

```
sudo pppoeconf
```

I start the connection using: 

```
sudo pon dsl-provider
```

I get connected comfortably but during the time when the connection is active it suddenly gets disconnected and when I use the following code:

```
plog
```

It shows that 4 echo requests were timed out and then modem hangs up. 
:(
Can anyone tell me what might be the problem? Thanx in advance!!:D

---

### Post by superprash2003 on 2009-05-18
are you connected via LAN or USB?

---

### Post by vivekrocks on 2009-05-18
I'm connected to DSL Modem via LAN. Sorry not to have mentioned this! Do u hav a solution to this?

---

### Post by harish_kd on 2009-05-18
I too had problems with BSNL Dataone pppoe in 8.04. It isn't the best handling networks.
Better go for 8.10 or 9.04. They have a good network manager.You can set up the connection graphically too.

---

### Post by vivekrocks on 2009-05-18
Thanx for advice! Can u please tell me if I can update from 8.04 to 8.10 without changing the system settings, like installed software?

---

### Post by vijaybilgoji on 2009-07-26
Bsnl broadband settings for ubuntu 8.04-

1.Type 192.168.1.1 in your browser u will get the router page open.
Type username-admin and password-admin to open this page.

2.In WAN Settings Select- PPP
3.Type u r username and password given to u by Bsnl.
4.Select- Always on.
5.Select-Apply
Router will save u r settings and reboot.

Now select the option DHCP just below WAN Settings

6.IN DHCP-- Enable the DHCP Server and click Apply
Router will save u r settings and reboot at this stage.

Close the router page.

7.Now go to the Top pannel of your desktop in that
  i)click Network connection (At the right corner of ur pannel)
 ii)Mannual configuration
iii)Select your wired connetion 
 iv)Click on properties
  v)Select Automatic Configuration(DHCP)& Click on OK

Run your browser and enjoy the virus free browsing through ubuntu.

---

### Post by thedreamer09 on 2009-09-05
hello friends i have got the CD yesterday and installed it 
but now i cannot connect to internet and i have entered the above 192.168.1.1 in the browser , but i cannot connect it.
it says cannot find the server and one more thing, whenever i login to ubuntu and then windows ,i cannot connect internet in windows too

---

### Post by karthick87 on 2009-09-06
Post the output of ifconfig.

---

### Post by lskumar on 2009-11-29
hi
i just installed ubuntu-v9.10 on my gateway laptop.
i have bsnl wired-broadband, which works fine for my desktop with xp.
please help me how do i connect to internet from my laptop.
thanks
kumar

---

### Post by vaibhav.dkm on 2010-10-01
Will this work in UBUNTU 10.04 also .....

---

### Post by dineshs on 2010-10-01
If your modem is configured in Bridge mode,try [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
If your modem is in PPPoE mode the connection should work automatically(provided the modem has DHCP enabled by default).If you find difficulty please post the results of ```
ifconfig -a
```when modem is connected and is switched ON.Also let us know the model name of your modem
Note:Configuring different modems in PPPoE mode is explained [here]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html") under modem/CPE config

---

