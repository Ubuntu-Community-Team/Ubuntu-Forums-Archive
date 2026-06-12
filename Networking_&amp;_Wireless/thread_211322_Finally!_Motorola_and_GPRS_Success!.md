---
title: "Finally! Motorola and GPRS Success!"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by Uncle Che on 2006-07-08
Ok, I got GPRS to work on my Motorola L6, I assume the procedure is the same for my v220. I know support sites only work when people post their own solutions and since a simple search of Motorola Gprs yields nothing of value, here goes:

1. Plug in the motorola phone. It should be recognized as ttyACM0.

2. Open a terminal window and type:
**sudo wvdialconfig /etc/wvdial.conf**

You get a long list of checks that it runs. Basically it checks for a modem and the location.

3. next type:
**sudo vi /etc/wvdial.conf**

In the file, you need to edit a few entries, like edit out the semicolons at the start of the line for phone number, password and username. For user name and password, you can enter anything for those values. For phone number, I used *99#.

Next, add a line:
**Stupid Mode = 1**

You might want to change the baud rate, I used 230400 even though it detected that it could do 460800. GPRS is slow so I can't personally think of a good reason to send data to and from the modem 10 times faster than it can deal with it. 

4. Save the file.

5. Next open another terminal window and type
**sudo wvdial**

You are now connected to the internet and you can surf. I don't know if you can close the window and keep the connection or not. I am just happy to be connected. I can deal with any quirks. 

I hope this can serve as a little bit of help to any searching the forums for how to use a gprs modem with Ubuntu/Kubuntu. It seems really simple, but I have been searching on and off for 6 months for a way to connect through Ubuntu like this.

---

### Post by mips on 2006-07-08
Please post this in the howto section of the forum as well.

---

### Post by anujv73 on 2007-08-17
pls tell me how to save this file?

---

### Post by anujv73 on 2007-08-18
what the fuckall forum it is i posted planty of msg asking about gprs connection but no one reply me did any one is alive here

---

### Post by Rui Pais on 2007-08-18
> **anujv73 said:**
> what the fuckall forum it is i posted planty of msg asking about gprs connection but no one reply me did any one is alive here

not being polite wouldn't help, i think...

> **anujv73 said:**
> pls tell me how to save this file?
What file? The /etc/wvdial.conf? Then your problem should be vi commands...
Try nano instead (much simpler);
```
sudo nano /etc/wvdial.conf
```
to save just hit Ctrl+O (the "O" key) and CTRL+X to exit. 
(Or hit Ctrl+X and then type 'Y' to accept save the changes)

---

### Post by vmosorio on 2007-09-27
> **Uncle Che said:**
> Ok, I got G

You are now connected to the internet and you can surf. I don't know if you can close the window and keep the connection or not. I am just happy to be connected. I can deal with any quirks. 

I hope this can serve as a little bit of help to any searching the forums for how to use a gprs modem with Ubuntu/Kubuntu. It seems really simple, but I have been searching on and off for 6 months for a way to connect through Ubuntu like this.

Thanks so much for this tutorial; I haven't been able to connect my Moto L6 though. After the modem is initialized it disconnects immediately as the terminal windows  reads, the wvdial.conf file  is edited correctly; I wonder if there is any other option. I use this device on a  Windows machine and there is an option called APN, is it something that should be added in Linux?

It also mentions that the daemon has died, it uses the pppo, I have tried configuring the modem in the network manager without suicess, any ideas?

Best
Victor

---

### Post by vmosorio on 2007-10-02
I guess I will continue to post more info in case somebody could help. It looks like the modem is initialized and it connects but it gets disconnected inmediately. This is what the terminal reads...

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*99***3#
--> Waiting for carrier.
ATDT*99***3#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Sep 28 06:28:25 2007
--> Pid of pppd: 5778
--> Using interface ppp0
--> Disconnecting at Fri Sep 28 06:28:26 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.

The wvdial settings are the same as those in the tutorial, I have set the pppconfig as well, I have tried with pon with no result.

Please help...

---

### Post by shriah on 2007-10-17
For saving a wvdial.conf file you must be root. This is how I edit wvdial.conf file.
```
gksudo gedit /etc/wvdial.conf
``` 
This should work perfectly to edit the file. I was trying to connect my phone Motorola L6 with ubuntu and after a long struggle I was able to do it . The key is never loose hope :)
This is my wvdial configuration . I am in India and  Airtel is my mobile operator
```
Init1 = ATZ
Init7 = AT
Init4 = AT+CPIN?
Init5 = AT E0
Init6 = AT+CGQREQ=3,0,0,0,0,0
Init8 = AT+CGQMIN=3,0,0,0,0,0
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=1
Init3 = AT+CGDCONT=3,"IP","airtelgprs.com",,0,0 
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99***3#
Modem = /dev/ttyACM0
Username = a
Password = b
Baud = 230400
```
The "airtelgprs.com" part is my APN so you must edit it with ur own APN from ur service provider , To get your APN try connecting ur phone in Windows using Motorola Mobile Tools and see then AT commands exchange between the software and the mobile (View->Modem Exchange) thats how i fixed my wvdial file . Good Luck

---

### Post by pigbig842001 on 2007-10-30
> **shriah said:**
> For saving a wvdial.conf file you must be root. This is how I edit wvdial.conf file.
```
gksudo gedit /etc/wvdial.conf
``` 
This should work perfectly to edit the file. I was trying to connect my phone Motorola L6 with ubuntu and after a long struggle I was able to do it . The key is never loose hope :)
This is my wvdial configuration . I am in India and  Airtel is my mobile operator
```
Init1 = ATZ
Init7 = AT
Init4 = AT+CPIN?
Init5 = AT E0
Init6 = AT+CGQREQ=3,0,0,0,0,0
Init8 = AT+CGQMIN=3,0,0,0,0,0
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=1
Init3 = AT+CGDCONT=3,"IP","airtelgprs.com",,0,0 
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99***3#
Modem = /dev/ttyACM0
Username = a
Password = b
Baud = 230400
```
The "airtelgprs.com" part is my APN so you must edit it with ur own APN from ur service provider , To get your APN try connecting ur phone in Windows using Motorola Mobile Tools and see then AT commands exchange between the software and the mobile (View->Modem Exchange) thats how i fixed my wvdial file . Good Luck
Hi,
 
I have tried everything but I am far from GPRS connection. I did everything as you said. My **wvdial.conf** file is like this:
 
>  
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyACM0
Username = a
Password = b
Baud = 460800

 
I have tried putting in lines from your conf file but it doesn't work. It shows an error wherever I add something from your file except for **Stupid Mode**.
 
My case is a little different. Wvdial dials perfectly and the connection is stable too. Now, if I try to run firefox then page can not open ie., as if there is no internet connection. Mine is **Nokia 5200 **phone.

---

### Post by pigbig842001 on 2007-10-30
> **pigbig842001 said:**
> Hi,
 
I have tried everything but I am far from GPRS connection. I did everything as you said. My **wvdial.conf** file is like this:
 

 
I have tried putting in lines from your conf file but it doesn't work. It shows an error wherever I add something from your file except for **Stupid Mode**.
 
My case is a little different. Wvdial dials perfectly and the connection is stable too. Now, if I try to run firefox then page can not open ie., as if there is no internet connection. Mine is **Nokia 5200 **phone.
Aha, finally I could get my GPRS connection to work. The problem was with the **wvdial.conf** file. Actually my connection is **!dea Cellular, Delhi, India**. Here's what I did to it.
 
```

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Baud = 460800
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = *99***1#
Modem = /dev/ttyACM0
Username = a
Password = b

```
 
The APN is **internet** in my case. I enquired about it. What I read from the terminal is, earlier there was no **DNS.** But now, after I edited the file, I can see **DNS address** coming in the terminal. I don't know what the **Stupid Mode = 1** does, but I wrote it just because I saw it elsewhere.
 
This thread came as an immense help to me as I have no other mode to access internet other than GPRS.
 
Thanks everybody

---

### Post by pigbig842001 on 2007-10-30
This is what I get when dialed.
```

nitro@Nitrous-Fumes:~$ sudo wvdial
[sudo] password for nitro:
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","internet"
WvDial Modem<*1>: AT+CGDCONT=1,"IP","internet"
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Tue Oct 30 22:15:25 2007
WvDial<Notice>: Pid of pppd: 8143
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: 
WvDial<*1>: pppd: 
WvDial<*1>: pppd: 
WvDial<*1>: pppd: 
WvDial<*1>: local  IP address 10.8.248.87
WvDial<*1>: pppd: 
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: pppd: 
WvDial<*1>: primary   DNS address 202.56.250.5
WvDial<*1>: pppd: 
WvDial<*1>: secondary DNS address 202.56.250.6
WvDial<*1>: pppd: 

```


And the connection is stable too. Didn't get a disconnection till now. Too Good.

---

### Post by aslamdoctor on 2007-11-05
[B][SIZE="4"]Hey Thanks for these Settings.
I am now able to use airtel gprs internet on ubuntu.
But I face one problem.
Does it keeps charging the battery of my phone??
Becoz when I disconnected my phone,
the battery of the phone was totally down.[/SIZE][/B]

---

### Post by Innocent Devil on 2008-02-15
hai thanx all i m too running net thru my phone usin same settings

am gettin this
```
ubuntu@spike:/etc/udev/rules.d$ wvdial airtel
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","airtelgprs.com",,0,0
WvDial Modem<*1>: AT+CGDCONT=1,"IP","airtelgprs.com",,0,0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Fri Feb 15 20:01:54 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 8153
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local  IP address 117.97.57.12
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary   DNS address 202.56.250.5
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address 202.56.250.6
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]

```
how can i dial without using console ??

---

