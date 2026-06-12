---
title: "Pairing Bluetooth device WITHOUT pairing code?"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by $p00ky on 2010-01-07
Dear community,

I have a simple Bluetooth device I would like to pair with my computer.
I detect it in the BlueTooth New Device Setup (from the GNOME pannel), detected as "Unknown", I enter its pairing code (1234) and click on "forward".

But then it asks me to enter a code on the BlueTooth device... I don't have anything to enter any code on this device.
I would like to simply connect to it!

From other OS, I manage to connect to the device as it's not asking to write any pair code in the bluetooth device.
The PIN code 1234 is enough to make the connection.

Any suggestion?

---

### Post by mark bower on 2010-01-08
which Ubuntu ver?  specifically, what is the bluetooth device you are trying to see?

you might look at some of the other posts in this Networking & Wireless section.    you should be able to see its MAC code by entering on the cmd line:
           sudo hcitool scan at the com
if you see the MAC addr, that is a good thing.  it should also show using Sys/Prefs/Bluetooth, and if it shows there, you can select it.  then i am not sure what might come next for you.

by going thru the bluetooth icon/settings on the tool bar, i found i could make things happy between a dongle and BT device by selecting the option for pairing with 0000.  however, this was not the final solution for my printer set-up

mark

---

### Post by $p00ky on 2010-01-09
Hi mark,

Thanks for your answer.
I'm using Ubuntu 9.10 and the device I'm trying to see is the [RooTooth]("http://www.sparkfun.com/commerce/product_info.php?products_id=684").

And yes I see the device and its MAC address by doing "hcitool scan".
I also successfully connect to it by doing "rfcomm connect # ADDR" where # is the port number to use and ADDR the Mac address of my device.

But I would like to be able to pair it with the system as a more "global" way (through the Bluetooth manager i.e.).

---

