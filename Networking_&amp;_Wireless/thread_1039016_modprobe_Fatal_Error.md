---
title: "modprobe Fatal Error"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by kitts on 2009-01-14
I h've been trying to install my Reliance ZTK CDMA USB modem on lenovo ideapad. I work on 8.10 Ubuntu.

After reading some guides i get stuck up at the following command on the terminal..

```
~$ sudo modprobe usbserial vendor=0×19d2 product=0xfffd

FATAL: Error inserting usbserial (/lib/modules/2.6.27-7-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

```

the above modprobe is the last step in modem detection process after which i'll have to edit wvdialconf. Please help me to fix this invalid argument error. what is wrong with the command?

---

### Post by kitts on 2009-01-15
No replies?? Any solution please

---

### Post by wmdiem on 2009-01-15
I don't know if it is it, but the x in the vendor number doesn't look right
```
vendor=0×19d2 product=0xfffd

```
I don't know what else it is, but it looks like a multiplication sign.

---

### Post by kitts on 2009-01-16
> **wmdiem said:**
> I don't know if it is it, but the x in the vendor number doesn't look right
```
vendor=0×19d2 product=0xfffd

```
I don't know what else it is, but it looks like a multiplication sign.
in which case what is the symbol i need to try instead of x. Any suggestions? The above symbol i got it from one tutorial.

---

### Post by wmdiem on 2009-01-16
I assume it should be an x as in the letter (like is in the product number)

---

### Post by Loosewheel on 2009-01-16
> **kitts said:**
> I h've been trying to install my Reliance ZTK CDMA USB modem on lenovo ideapad. I work on 8.10 Ubuntu.

After reading some guides i get stuck up at the following command on the terminal..

```
~$ sudo modprobe usbserial vendor=0×19d2 product=0xfffd

FATAL: Error inserting usbserial (/lib/modules/2.6.27-7-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

```

the above modprobe is the last step in modem detection process after which i'll have to edit wvdialconf. Please help me to fix this invalid argument error. what is wrong with the command?

"Invalid argument"....Maybe try 'sudo modprobe usbserial' without 'vendor=...' product=....'

---

### Post by kitts on 2009-01-31
the error is small 'x' (right one) instead of Big 'X'.

I have got other errors after detection of the modem. 

> kitts@kitts-laptop:~$ sudo wvdial zte
> > > --> WvDial: Internet dialer version 1.60
> > > --> Cannot get information for serial port.
> > > --> Initializing modem.
> > > --> Sending: ATZ
> > > ATZ
> > > OK
> > > --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
> > > ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
> > > OK
> > > --> Modem initialized.
> > > --> Sending: ATDT#777
> > > --> Waiting for carrier.
> > > ATDT#777
> > > CONNECT
> > > --> Carrier detected.  Waiting for prompt.
> > > --> Connected, but carrier signal lost!  Retrying...
> > > --> Sending: ATDT#777
> > > --> Waiting for carrier."

Any suggestions?

---

### Post by kitts on 2009-01-31
My wvdial looks like this on editing

> [Dialer zte]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = #777
Username = 932xxx
Password = 932xxxx
ISDN = 0
SetVolume = 1
FlowControl = Hardware (CRTSCTS)
Modem = /dev/ttyUSB0
Dial Command = ATDT
Baud = 460800
stupid mode = 1

Any errors...?

---

### Post by noworry on 2009-03-06
I also got the error
--> Carrier detected.  Waiting for prompt.                                                                   
--> Connected, but carrier signal lost!  Retrying... 

But now it is gone and connecting fine after adding "Stupid Mode = yes" in /etc/wvdial.conf

This is what my file looks like:

[Dialer zte]
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Password = 937xxxx         
Mode = 1                       
Phone = #777                   
+FCLASS = 0                    
Modem Type = Analog Modem      
SetVolume = 0                  
Baud = 460800                  
Dial Command = ATDT            
Modem = /dev/ttyUSB0           
ISDN = 0
Username = 937xxxx
FlowControl = Hardware (CRTSCTS)
Stupid Mode = yes

Now I am very happy :)

---

