---
title: "Setup Huawei EC325 Modem [Bsnl,Realince, etc..]"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by fizmhd on 2010-03-20
[SIZE=4]**Setup Huawei EC325 Modem [Bsnl,Realince, etc..]**[/SIZE]This same method can be used to connect the WLL from BSNL.



Step X : Open Terminal and type "**[COLOR=DarkRed]sudo bash[/COLOR]**" terminal asks for password enter your 
             login password.(In case if the "sudo bash" dont works just type the "**[COLOR=DarkRed]sudo su[/COLOR]**"     
             command.

Step X : type "**[COLOR=DarkRed]vi /etc/wvdial.conf[/COLOR]**" and press Enter. In the opened window copy and        
             paste the given details.
    
    "You have to change the Username and Password" 

    [COLOR=DarkRed][Dialer Defaults]
    Init1 = ATX0 
    Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    Stupid mode = on
    Auto Reconnect = on
    Carrier Check  = no 
    Init3 = ATM0 
    Modem Type = Analog Modem
    Phone = #777
    ISDN = 0
    Password = password
    Username = username
    Modem = /dev/ttyUSB0
    Baud = 460800[/COLOR]

    After Pasting the following information press "Esc" key and type "**[COLOR=DarkRed]:wq[/COLOR]**" to save 
    the Details.

Step X : Now in terminal type "**[COLOR=DarkRed]wvdial[/COLOR]**" to connect to internet.

---

