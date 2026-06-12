---
title: "3G Network connection fails using a Blackberry as a modem"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by wishmaster-mx on 2010-04-30
Folks,

I just installed Ubuntu 10.04 on my VAIO VPCEB19FL, i3, 4GB RAM, 500GB HD. So I having issues while I try to connect it to a 3G network.

Well, at first instance the wizard does not works, I suspect because I use a BB Storm as a modem (with pass), even though, I cannot see the files in its internal MEM, as well as in its uSD (via usb), this could be a later discussin.

I found a tut about how to configure the 3G Network on Ubuntu when the moden is a BB device, this is done via Bluetooth. I released the pass and even though does not works.

Here is a summary what I followed: (Sorry if I miswrite some command, I have mi Ubuntu in Spanish)

1. I went to System->Bluetooth and I followed the wizard looking for my BB (Previosly putting my BB visible), well this step was done without any issue. The coupling was succesful.
2. In the BB side be aware of selec Options->Discoverable->yes, this over your lap's name coupled. By default is "no", if you not consider this, this is the root cause of the following issue that I will describe.
3. Once the devices were coupled, I typed in a terminal **sdptool search DUN**, and the inquiring began, if you did not select "yes" in the above mentioned step, you cannot see the results of the "search".
4. Then the DUN number was displayed, and more stuff.
5. I configured the file **gedit /etc/bluetooth/rfcomm.conf** , something like this:
rfcomm0 {
bind yes;
device 00:21:06:96:7F:77;
channel 3;
comment "Black Berry";
}
6. I restared the bluetooth by typing: **sudo /etc/init.d/bluetooth restart**
7. So, the tut says that now I can comunicate with the cel at **/dev/rfcomm0**
 and here is when I get lost (the tut is taking Kubuntu as reference)
these are the following step proposed, is where I request your help.
8. To configure KPPP (I dont know if there is a correspondence in Ubuntu):
9. Open KPPP and enter to configure.
10. Create new moden, in device select /dev/rfcomm0
11. Boud rate: 115200
12. Create new account
13. Tel num: #777
14. Save
15. Enter any user name and pass
16. Connect
17. Enjoy

I'm a beginner in Ubuntu, and I want to take all its advantages connecting it to the web.

Thanks in advance!
p.s. My apologies for my bad english

---

