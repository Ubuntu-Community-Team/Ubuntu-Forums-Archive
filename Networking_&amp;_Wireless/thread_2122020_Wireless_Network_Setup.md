---
title: "Wireless Network Setup"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by sschlagel on 2013-03-03
I am an absolute new user.  I purchased a laptop from ebay without an OS.  I installed Ubuntu and do not have wireless capabilities.  This laptop appears to be wireless capable.  Is there a way to verify whether the wireless is working or available?  The wired network configured automatically.

---

### Post by darkcrimson on 2013-03-03
I'm really sorry to hear that the wireless is not working on your Ubuntu machine, hopefully we can get this resolved!

Open a command prompt (Terminal) and type this:

```
iwconfig
```

Then paste the results here, if any.

---

### Post by Mikhail.Inspired on 2013-03-04
Does the proprietary drivers dialog have any drivers listed in it?

---

### Post by zeroseven0183 on 2013-03-05
Connect your computer via wired connection, open Unity Dash and search for Additional Drivers. Make sure you are connected to the internet so it can download any drivers for your detected hardware.

---

### Post by mörgæs on 2013-03-05
Please provide a complete hardware description, for example by running

```
sudo lshw > lshw.txt
```

and posting lshw.txt

---

### Post by sschlagel on 2013-03-05
pgis@ProvidenceUbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pgis@ProvidenceUbuntu:~$ ^C
pgis@ProvidenceUbuntu:~$

---

### Post by sschlagel on 2013-03-05
Where do I find the proprietary drivers list.  When I open the network configuration window I do not see any available networks.

---

### Post by sschlagel on 2013-03-05
pci sysfs is what came up for a brief moment then it went to the command prompt

---

### Post by sschlagel on 2013-03-05
I typed driver in the Dash and saw a NIC icon that said additional drivers.  I executed it and it loaded the wireless driver and started working.  I am replying on my wireless now.  Thank you for your time.  It is greatly appreciated.

sam

---

### Post by sschlagel on 2013-03-05
I typed driver in the dash search and a Nic icon showed up.  I clicked it and it loaded a wireless driver.  I am now posting on my wireless connection.  Thank you for your time.  It is greatly appreciated.

sam

---

### Post by sschlagel on 2013-03-05
I typed driver in the dash search and a Nic icon showed up.  I clicked  it and it loaded a wireless driver.  I am now posting on my wireless  connection.  Thank you for your time.  It is greatly appreciated.

sam

---

