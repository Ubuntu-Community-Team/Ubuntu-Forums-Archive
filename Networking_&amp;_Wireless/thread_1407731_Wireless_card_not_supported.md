---
title: "Wireless card not supported?"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by cybernetic toaster pastry on 2010-02-15
I just recently installed Ubuntu on my wife's computer, and per her request I removed windows. She is now stuck without internet. She has a Dell studio with a BCM4312 and it appears Ubuntu doesn't even recognize it. I'm afraid wireless is the only way to connect to the internet on that laptop so I can't even get the new updates that I just got on my laptop.
Is there any way to resolve this? Please help me keep from getting scolded.

---

### Post by chili555 on 2010-02-15
It is well supported. Can you temporarily connect the wired ethernet? Please see: [http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation](http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation)> Ubuntu/Debian

In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you:

```
sudo apt-get install b43-fwcutter

```
You will be asked to automatically fetch and install the firmware into the right location.



---

### Post by cybernetic toaster pastry on 2010-02-15
I cannot connect to a wired ethernet. I have tried the 43cutter and it says:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package b43-fwcutter

I understand I need the internet for this but I tried anyway- what the heck, right?
I do have an Ethernet hook up but when I connect it nothing happens and I'm not sure how to set it up. Mine automatically connects when I use my computer.

---

### Post by cybernetic toaster pastry on 2010-02-15
Alright I now have it connected to the Internet via Ethernet but when I do the sudo apt-get install b34-fwcutter it still says it can't find it

---

### Post by bkratz on 2010-02-15
> **cybernetic toaster pastry said:**
> Alright I now have it connected to the Internet via Ethernet but when I do the sudo apt-get install **b34-fwcutter** it still says it can't find it

That is b43

---

### Post by cybernetic toaster pastry on 2010-02-15
I'm not following I still can't connect via wireless. It wont even pick up other routers in the area. Nothing but wired connections

---

### Post by chili555 on 2010-02-15
> **cybernetic toaster pastry said:**
> Alright I now have it connected to the Internet via Ethernet but when I do the sudo apt-get install b34-fwcutter it still says it can't find itPlease open System -> Admin -> Synaptic and select Settings -> Repositories and make sure the repositories are enabled as per attached. Press Reload and then search for 'b43.' Install and follow the prompts.

Select the correct download server if you are not in the USA.

---

### Post by cybernetic toaster pastry on 2010-02-15
I really appreciate the help and now it has b43. I went into the hardware drivers and saw the b43 driver and another that said it was for linux systems with b4311-b4312-b4313. I assume this is suppose to be the active driver and if it is I have a whole new problem because when I try to activate it a box pops up stating "downloading and installing drivers". I have walked off and came back 30-45 minutes later and nothing has changed. Just sitting there with an empty bar. It also will not let me cancel it. Crap this sucks.

---

### Post by cybernetic toaster pastry on 2010-02-15
Would anyone suggest reinstalling and starting over. I'd hate to but if I must, I must.

---

### Post by bkratz on 2010-02-15
Is the other driver mentioned STA?  Here is a pretty good thread on the BCM4312 especially post 12.

[http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf](http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf)

look at the whole thing first and decide whether it looks familiar

---

### Post by cybernetic toaster pastry on 2010-02-15
I knew as soon as you said STA I was on to something. I never thought it was a problem of clashing files and only two were present, the b43 and b43legacy directories. Once I logged in as root and removed those two everything else went completely smooth. She now has wireless and I got to keep my hide. Me and my sanity thank you!

---

