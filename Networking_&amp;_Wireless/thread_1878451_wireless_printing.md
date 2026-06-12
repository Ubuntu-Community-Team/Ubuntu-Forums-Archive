---
title: "wireless printing"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by Astronaut356 on 2011-11-09
I have the HP Envy D410 printer. I print wireless with OS X - the printer is not connected to my computer or router. In Ubuntu 11.10, the drivers download but I can't figure out how to get the computer to "see" the printer. Anyone got this printer working?

---

### Post by RedSingularity on 2011-11-10
The printer needs to be connected to something, be it another machine or a wireless access point.  Unless it is using bluetooth to connect to your Apple machine.

---

### Post by docbop on 2011-11-10
Does your Ubuntu box connect to same wireless net your Mac and printer does?  If so you should be able to connect to the printer.  Get the network settings of the printer, then use that IP to setup the printer in the Ubuntu printer tool.

---

### Post by Astronaut356 on 2011-11-10
Yes, the printer and all the computers are connected to the same AirPort. I tried connecting by setting up the device URL as socket://10.0.1.1:9100. The make and model of the printer shows up correctly. The driver is installed. Just says "Processing connecting to printer..." and the test page never prints.

Could it be because I am running Ubuntu in Virtual Box right now until my ThinkPad arrives? I am trying to test everything before actually installing on bare metal.

---

### Post by RedSingularity on 2011-11-10
That could be the problem then.  I am not familiar with networking inside a virtual machine, but if it detects it and even installs the drivers for it, I dont think you will have a problem installing the printer to the actual machine when its set up.

When you go to administration >> printing and add a printer, does the printer come up under the "Network Printer" tab?

---

### Post by docbop on 2011-11-10
Yes check your Virtbox config and make sure all the ports are being passed thru.

---

### Post by Astronaut356 on 2011-11-10
Not really sure how to do that. There is a preference pane Virtual Box for "Enable Network Adapter" but I don't really know what to do with it. Maybe I'll just wait until I get Ubuntu installed on my ThinkPad and see if it works there.

---

