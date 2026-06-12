---
title: "Very confused"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by mengfei on 2006-06-11
Hello everyone!

I have a Zonet wireless pci card in my desktop computer. Once I find the box, I'll post what model it is.

Anyhow, I just finished installing Ubuntu, and it seems to be working fine, until I try to set up my network connections.

I go into Networking Manager, and see that my wireless, "eth0" is inactive.

So I go into properties, put in the network name, and the hexadecimal WEP password, and pressed activate.

It goes through this "activating" window for quite a while, and when it finally says my card is active, I don't get anything. No window showing available networks or signal strength.

I then try to go on the Internet, but it's not connected!

I searched around and found that you need to enter the hexadecimal keys with a slash between each 4 digits/letters.

I tried that with no success, it still doesn't connect.

Anyone know what's wrong?

Much Obliged,
mengfei

---

### Post by Aelfric5578 on 2006-06-11
Let me preface this by saying I am very inexperienced, but I managed to get my usb wi-fi adapter to work by putting colons ( : ) between every pair of hex digits.  
Then again, this was not using the Networking Manager but rather this was in a bash script using wlanctl-ng.  I guess it's worth a try, but I make no guarantees.

---

### Post by mengfei on 2006-06-12
Doesn't seem to work :-(

I never do seem to be able to get wireless working in any Linux.

---

### Post by ignavia on 2006-06-12
I can confirm that the default network-admin will connect to a wireless network WITHOUT any delimeters in the WEP key.

Try iwconfig and see if you're actually connected. I had a Zonet CardBus adapter that I had a lot of trouble with. I gave it to my wife to use on Windows and I took her D-Link card which Ubuntu fell in love with.

---

### Post by mengfei on 2006-06-12
What is iwconfig?

I'm sorry, I am completely new to all this stuff.

---

