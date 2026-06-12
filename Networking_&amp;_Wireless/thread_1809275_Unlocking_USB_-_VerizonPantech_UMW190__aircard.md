---
title: "Unlocking USB - Verizon/Pantech UMW190  aircard"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2011-07-21
Having problem getting connected to Internet on Ubuntu/Lucid computer via Verizon/Pantech UMW190 aircard.  I think this is because the computer user repeatedly attempted to use an incorrect password due to the functioning of Ubuntu's keyring feature and "I think" that has caused the aircard to become LOCKED/BLOCKED.

My question is, if the above is the case, and if I can get Verizon tech. support of the phone to walk me thru this, can they give me the proper steps to UNLOCK the aircard while it is connected to a Ubuntu based computer or is this going to have to be done on a WINDOWS based computer, which I don't have ???

Thanks.

---

### Post by alexfish on 2011-07-21
hi

doubt if keyring manager will have caused the device to become locked or blocked

most device security is with pin or puck codes , the password may be used for the server connection ( not the the keyring manager password)

the possible cause may be the modem manager probing the device with AT commands that may produce an error , can look at system logs or messages , see what it shows.

modem manager usually requires plugins for specific devices, not sure if this device is listed in the plugin's.

if the modem manager is failing to connect or causing errors then suggest installing WVDIAL . also consider disabling modem manager, or remove if not required,

see what happens


alexfish

---

