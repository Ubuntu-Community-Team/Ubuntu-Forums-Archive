---
title: "Restart Mobile Broadband"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by electric-wildflower on 2011-05-02
I have a problem with my mobile broadband stick that needs answering.

Sometimes when im using mobile broadband it disconnects me and to re start i just click on mobile broadband and it will re connect. Other times when ive been disconnected i will try re connect and everytime i just get a disconnected pop up.

I disable networking and wait a few seconds re enable networking and it works. But alot of the time i have to re start the computer just to get it to connect again seems taking out dongle waiting a few seconds and re inserting doesn't do anything.

Having to restart the computer is annoying so i came here to ask the question is there a way for me to restart the dongle using a command i tried restarting network in terminal but seems nothing changes ??

Im using ubuntu 10.10 and a t-mobile mobile broadband stick.

Any help would be greatful

---

### Post by alexfish on 2011-05-02
some time modem manager gets a bit sticky when a disconnection not of it's own making

next time it happens try
```
sudo killall modem-manager 
```then give time for modem manager to register the device

see what happens, should save having to reboot

if you find it a pain, could try another connection manager such as Sakis3g

Added: when removing the device give time for the system to settle before plugging back in

alexfish

---

### Post by electric-wildflower on 2011-05-03
Thanks for the tip once it starts acting again ill try and see what happens.

sometimes when it cuts out ill take dongle out wait around 30 seconds then try again but it either works or needs a reboot this should hopefully help.

---

### Post by arunharidas on 2011-09-03
> **alexfish said:**
> some time modem manager gets a bit sticky when a disconnection not of it's own making

next time it happens try
```
sudo killall modem-manager 
```then give time for modem manager to register the device

see what happens, should save having to reboot

if you find it a pain, could try another connection manager such as Sakis3g

Added: when removing the device give time for the system to settle before plugging back in

alexfish

thanks a lot!!! ... i was facing the same problem for about an year ... i used to connect internet through my mobile phone , if the mobile phone is charging i cannot switch on any light or fan or it will disconnects my internet and the computer needs restarting... once again thanks for the help :D

---

