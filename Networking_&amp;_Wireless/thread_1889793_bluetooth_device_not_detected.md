---
title: "bluetooth device not detected"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by _siva_ on 2011-12-02
Hi,

I've the following problem: I'm running Ubuntu 11.10 (64bit) on a HP 8560w laptop. Bluetooth seems to work, ie it is shown as ON and when I make my cellphone discoverable it is detected by the laptop as a device in the neighborhood.
I have another bluetooth device however (an SMA inverter for photovoltaic cells) which is not detected. 
If i scan for bluetooth devices on my cellphone, the SMA inverter IS detected. So something is wrong on my laptop.

Any ideas where the problem could be,

thanks in advance

---

### Post by matt_symes on 2011-12-02
Hi

With the devices discoverable, open a terminal and type

```
hcitool dev
```

and then 

```
hcitool scan
```

Post back the results back here.

Kind regards

---

### Post by _siva_ on 2011-12-02
here goes:

marc@hp8650w:~$ hcitool dev
Devices:
	hci0	CC:52:AF:7B:27:C7

marc@hp8650w:~$ hcitool scan
Scanning ...
	B0:89:91:62:8C:27	Optimus 2X

This is new to me but re-executing scan I get

hcitool scan
Scanning ...
Inquiry failed: Invalid argument

and I confirm that on my Optimus 2x, I have a bluetooth device listed called 'SMA001d', which I assume to be my SMA inverter in the basement.

thanks for your help

---

### Post by matt_symes on 2011-12-02
Hi

What exactly is an *Optimus 2X* ? Is it an LG phone ?

The scan is only finding one device and i am not sure what that device is.

Is your laptop close to the device you are having problems connecting to ?

Kind regards

---

### Post by _siva_ on 2011-12-02
Hi,
yes it is my LG Optimus phone. THe fact that it is detected means that bluetooth is working on my laptop. Agreed?

However, as explained, I have also an SMA inverter with bluetooth enabled. The proof that it is enabled, comes from the fact that my LG Optimus phone detects the device.

But if the phone can see it, why can't my laptop see it?

Marc

---

### Post by matt_symes on 2011-12-02
Hi

Is it a range issue ? Have you taken your laptop down to the basement and tried to connect in local proximity ?

After all, where were you when you paired your phone with the SMA ? Were you very close to it ?

Kind regards

---

### Post by _siva_ on 2011-12-02
Yes, that was it. The cell phone seems to have much better reception, because I was holding the cellphone next to the laptop. 
Putting the laptop in the basement allows discovery.

thanks!

---

