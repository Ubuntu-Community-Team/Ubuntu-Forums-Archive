---
title: "Ubuntu 10.10 bluetooth connection with android"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by scarleo on 2011-01-30
Hi,

I've been trying to connect my android phone (Samsung Galaxy S) with bluetooth to transfer files. They find each other perfectly fine and both phone and computer say they are paired. But I cannot transfer any files what so ever. When I do the connection there is a small icon (a cable?) in the device list which I guess shows that there is a connection and the device name is in bold. This is the case for just a second after setup and then it goes back to look like the other items in my device list.

What am I doing wrong? Am I supposed to mount the phone? If so, why isn't it done automatically?

Thanks in advance.

---

### Post by ephioz on 2011-01-30
If I remember correctly, this is what I did to transfer files to my Galaxy S.

1. Under bluetooth settings on my phone I made the device visible.
2. In Ubuntu under system-preferences-bluetooth I marked "make computer visible" and "show bluetooth icon". I then clicked "set up new device" and followed the instructions. 
3. On my phone I clicked on the name of my computer under bluetooth devices and accepted the pin. It should say "connected".
4. In Ubuntu I clicked the bluetooth icon, chose "Galaxy S" and then "browse files".
5. That did it for me. One thing I noticed though when I browsed my phone in nautilus was that I was able to transfer files to my phone but they didn't show up immediately. But when I checked with the file manager on my phone they were there.

Hope this helps.

---

### Post by Andras B. on 2011-02-11
Turns out you need a package to transfer files from the phone, that is not installed. It's called gnome-user-share. After installing this package, file transfer works fine.

I have another problem though. If I click Bluetooth icon - Galaxy S - Browse files..., I can see all the folders, and can navigate to any of them, but all folders appear completely empty, I don't see any files in any of the folders. This is very frustrating. Any similar issues / ideas?

(of course they aren't actually empty)

---

### Post by Yarod on 2011-02-17
I've got the same problem. Only folders are displayed

---

### Post by igorlunamoura on 2011-02-18
Same thing over here with an Samsung Galaxy 3 + Ubuntu 10.04

---

### Post by mihaimm on 2011-02-20
Same here... Galaxy Teos and Ubuntu 10.10. Is this something specific to Samsung devices?

---

### Post by protomank on 2011-02-25
Sae for my Galaxy 3. This is really bad, as Samsung devices are not very nice when connected to USB either :-P

---

### Post by metalf8801 on 2011-02-26
first you need to install Bluetooth File Transfer (OBEX FTP and OPP) for Android [https://market.android.com/details?id=it.medieval.blueftp&feature=search_result](https://market.android.com/details?id=it.medieval.blueftp&feature=search_result)

Then click on the Bluetooth icon thenselect "Set up new device" go threw the steps it wakes you threw 
after that's done and if you have Bluetooth File Transfer for Android running on your phone you can now send files to your phone 

In order to send files to your computer from your phone you need to click on the Blue tooth icon on your Ubuntu panel then select Preferences then Receive files then check Receive files in Download folder over Bluetooth 

I hope this helps 
Dan

---

### Post by jtdaling on 2012-08-10
Hello,

regarding this threat I have problems sending files as well.
I am using an experimental rom on my galaxy s2 and unfortunatly the usb mount option is not supported.
However I would like to recommend a very nice app that avoids all the problems whe encounter: airdroid.

Via airdroid you can simply connect to your device via a webpage ([http://web.airdroid.com](http://web.airdroid.com)) and after the login (via bar-code) the computer and android device will be connected wifi.

Hopefully the android community will stop using the microsoft protocol again!

---

