---
title: "How to setup my ADSL Connection?"
date: 2006-04-13
forum: Networking &amp; Wireless
---

### Post by djgenesis on 2006-04-13
Hi all, 
I have ordered my ADSL and the ADSL modem just arrived. 
I noticed that it was an Alcatel Based speedtouch 330 usb and after digging around i found out that the drivers were included in the distro. 
I downloaded them, installed them and i connected the ADSL modem.
I also installed pppoe off synaptic without any problems. 
But when i am trying to run pppoeconfig, ubuntu does not recognise the ADSL modem as anything :-k 
The system log when i connected the modem showed 
```

Apr 12 19:54:09 localhost kernel: usb 1-2: USB disconnect, address 3
Apr 12 19:54:34 localhost kernel: usb 1-2: new full speed USB device using uhci_hcd and address 4
Apr 12 19:54:35 localhost usb.agent[9722]:      speedtch: already loaded
Apr 12 19:54:35 localhost usb.agent[9722]:      speedtouch: loaded successfully
Apr 12 19:54:35 localhost kernel: usb 1-2: khubd timed out on ep0in
Apr 12 19:54:35 localhost usb.agent[9790]:      speedtch: already loaded
Apr 12 19:54:35 localhost usb.agent[9790]:      speedtouch: loaded successfully
Apr 12 19:54:36 localhost usb.agent[9785]:      speedtch: already loaded
Apr 12 19:54:36 localhost usb.agent[9785]:      speedtouch: loaded successfully

```

Also
```
lspci
```
shows me that the hardware is there and connected.

Now, as i am new to Ubuntu, i don't have a clue how to make use of my hardware. In windows i would go to network connections and set up a new dialer but in Ubuntu the system can't find a modem (Probably cause it is fro 56k connections only)


*How do i check if my ADSL modem is properly installed?
*How do i create an ADSL connection to my ISP?
{ Phonenumbers
  Authentication type
  User/Pass
  etc }
*Is there a script or is pppoe compulsary? Isn't there a graphical application to help me ?
*How can i make sure it is working properly? Can i just dial my mobile phone through the ADSL modem or does this sound stupid?

---

### Post by angkor on 2006-04-13
See if this thread has some useful info for you:

[http://www.ubuntuforums.org/showthread.php?t=44763&](http://www.ubuntuforums.org/showthread.php?t=44763&)

---

### Post by djgenesis on 2006-04-13
This is **panacea**!!!  cheers

---

