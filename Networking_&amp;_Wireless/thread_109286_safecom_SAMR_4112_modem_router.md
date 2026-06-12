---
title: "safecom SAMR 4112 modem router"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by avantgardaclue on 2005-12-28
Hello all, having spent the last few months trying to get ubuntu working with the tiscali provided sagem fast 800 usb modem i have bitten the bullet and installed an ethernet card in my computer and attached said safecom SAMR 4112 modem router to that. 

My PC has 2 hard drives, one for windows and the 2nd for ubuntu. Using the windows drive i have got the modem working beautifully even if it seams a bit odd it being connected all the time. However i am at a loss as to how to get my ubuntu drive to work with / recognise the modem.

I am sure there is a simple solution to this, it's just that i can't see it.

advice gratefully received

Simon (UK)

---

### Post by mips on 2005-12-28
Simon,

You have to let your router handle the PPPoE & Authentication stuff. You can even set your router up as a DHCP server.

System-Administration-Networking is where you can do the setup.

All you have to do in Ubuntu is configure it for DHCP or static IP address parameters: IP Address, Netmask, Default Gateway. You might also need to set the two DNS/Name servers of your ISP.

If you get stuck come back to us with the following:
Start windows, open a command prompt, enter "**ipconfig /all**" and paste the output here.

---

### Post by avantgardaclue on 2005-12-28
Mips, thanks for the prompt reply. I went to System-Administration-Networking, but the only options where to do with the  ethernet card and a 56k modem... nothing to do with the router:???:  

Here's the stuff from your ipconfig /all comand....


        Host Name . . . . . . . . . . . . : deletedout
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-B9-00-01-FB-64
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 10.0.0.3
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        Default Gateway . . . . . . . . . : 10.0.0.2
        DNS Servers . . . . . . . . . . . : 10.0.0.2

I looked up on the tiscali web site for some more stuff which is sort've leaving me confused....

Virtual Circuit Identifier -  VCI 	38
Virtual Path Identifier -  VPI 	0
Encapsulation Mode 	VCMux
Authentication Type 	CHAP
Protocol 	RFC 2364:
PPP over ATM (PPPoA)
Modulation Type 	G.DMT or Auto
Tiscali Primary DNS Server 	 212.74.112.66
Tiscali Secondary DNS Server 	212.74.112.67

I'm sure i am only a few clicks and minutes away from finally being able to use ubuntu properly:smile:

---

### Post by mips on 2005-12-28
Simon,

Do you have to enter your username & password to gain access to the internet/ISP when you want to go online or are you permanently connected and the router logs in for you ?

From Windows ipconfig /all:
> Dhcp Enabled. . . . . . . . . . . : No
IP Address. . . . . . . . . . . . : 10.0.0.3
Subnet Mask . . . . . . . . . . . : 255.0.0.0
Default Gateway . . . . . . . . . : 10.0.0.2
DNS Servers . . . . . . . . . . . : 10.0.0.2
Tiscali Primary DNS Server 212.74.112.66
Tiscali Secondary DNS Server 212.74.112.67


1. Go to System-Administration-Networking
**Connections tab**
2. Enter password when prompted
3. Select your ethernet card so it is highlighted
4. Click on 'Properties'
5. Make sure the 'Enable this connection' box is ticked
6. 'Configuration:' Static IP address
7. IP address: 10.0.0.3
8. Subnet mask: 255.0.0.0
9. Gateway address: 10.0.0.2
10. Click 'OK'
**DNS tab**
11. DNS Servers click 'Add'
12. Enter address: 212.74.112.66
13. Repeat and enter address: 212.74.112.67
14. Click 'OK'

You should now be up and running if your router does the logging in part of things.

---

### Post by avantgardaclue on 2005-12-28
Mips, 
>>You should now be up and running if your router does the logging in part of things<<

You are soooo right! many thanks... written from an internet connected ubuntu pc for the first time!!:razz:

---

### Post by mips on 2005-12-28
Cool.

Please test all your applications that require net access and make sure they work. If you have any hassles let us know.

Seeing you are now on the net you probably want to install new applications and update/upgerade your installation.
Do a sudo **apt-get update** followed by a **sudo apt-get upgrade** to bring your installation up to date.

Look at Automatix [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563) to install all the most common stuff you need not in the repositories.

---

