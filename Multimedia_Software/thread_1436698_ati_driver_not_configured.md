---
title: "ati driver not configured?"
date: 2010-03-23
forum: Multimedia Software
---

### Post by lv. on 2010-03-23
Hey guys!

Just installed Ubuntu today and loving it :D

I installed envyng using Synaptic Package Manager and when it finished I used CTRL+ALT+F1 and went through the steps on setting up the ATI driver, there was only 1 driver for my card in the list to choose from so I went for that, I then rebooted when prompted me to do so.

Just before It's about to goto the login window my screen flashes a couple of times then it throws me an error:

Ubuntu is running in low-graphics mode

The following error was encounted. You may need to update your configuration to solve this.
(EE) No devices detected.

What would you like to do?
* Run ubuntu in low-graphics mode for just one session
* Reconfigure graphics
* Troubleshoot the error
* Exit to console login

My card is a Radeon 7000 AGP (Yes very old hehe) anyone know the the fix for this?

---

### Post by Yellow Pasque on 2010-03-23
The driver you need is pre-installed. The proprietary ATI Catalyst/fglrx driver you tried to install with envyng hasn't supported your card in years. Purge it off your system: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
Uninstall envyng and never try to install any video driver other than the open-source radeon driver.

---

### Post by lv. on 2010-03-23
Ok thanks. I followed the link and it removed it. Thing is when i try and play CS in steam it goes fullscreen then my monitor goes crazy with lines and whatnot..

What do you suggest is a good compatible AGP card that will run on CS 1.6? It's the only game I play so I don't need something over the top

specs: AMD Athlon 1.3GHZ - 1GB ram - 450w PSU

---

### Post by Yellow Pasque on 2010-03-23
The best AGP card I've seen is either Nvidia 7300GT or RadeonHD 4350/4650. I've actually seen better cards in regular PCI slot form (like 8400GS and 9400GT): [http://www.tigerdirect.com/applications/category/category_slc.asp?Recs=30&Nav=|c:319|&Sort=4](http://www.tigerdirect.com/applications/category/category_slc.asp?Recs=30&Nav=|c:319|&Sort=4)

Once you start spending more than $50-60, it becomes less and less worth it to add a new video card to your existing system.

---

