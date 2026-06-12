---
title: "no internet"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by rebecca hallam on 2009-02-16
Please help, i have a acer aspire one linux netbook, have just bought external dvd rw drive and installed ubuntu now i cant access internet, wireless or wired:confused::

---

### Post by Simian Man on 2009-02-16
Ubuntu doesn't include wireless drivers, you have to download them separately.  So let's focus on getting wired working :).

Do you have a static IP address, or use dhcp?  What happens when you enter the command:
```

sudo /etc/init.d restart

```

---

### Post by rebecca hallam on 2009-02-16
we'v just managed to get wired connected by doing a re-boot, now trying to download network manager to see if we can get wireless, also installed on netbook is linpus which we can get wired and wireless on

---

### Post by Aarookie on 2009-02-16
try this
Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here. At this point however I was unable to connect to wpa type network, switched router back to wep and hooked right up
I'm on 32 bit computer, not sure if this will work in 64 bit environment, my bro's computer wouldn't accept 32 bit driver with this method, and his card doesn't have 64 bit windows' drivers

---

### Post by rebecca hallam on 2009-02-16
Thank u Simian man and Aarookie, am having a go at your suggestions!!!!!::)

---

### Post by rebecca hallam on 2009-02-17
Hiya, I have managed to get wifi internet on my netbook by using a netgear usb adapter-dont know if iv done the right thing but it seems to be working ok!! thank you to everyone on the forum cus by reading everything im a little clearer how things work (just alittle mind u):D

---

