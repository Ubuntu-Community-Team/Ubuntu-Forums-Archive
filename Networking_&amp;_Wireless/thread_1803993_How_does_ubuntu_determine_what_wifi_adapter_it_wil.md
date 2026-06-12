---
title: "How does ubuntu determine what wifi adapter it will use when there are more than one?"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by fpgdu on 2011-07-14
My laptop has an internal wireless g "adapter" (for lack of a better word) and I plugged in a very cheap and very small ASUS wireless N adapter later on. 
 
The ASUS adapter has better bandwidth (again for lack of a better word) but isn't as high quality of a link as the internal adapter is.

The laptop appears to be using the internal adapter, but i want it to use the ASUS adapter.


Any suggestions are welcome. Also, what can be done?

---

### Post by haqking on 2011-07-14
[SIZE=2]> **fpgdu said:**
> My laptop has an internal wireless g "adapter" (for lack of a better word) and I plugged in a very cheap and very small ASUS wireless N adapter later on. 

The ASUS adapter has better bandwidth (again for lack of a better word) but isn't as high quality of a link as the internal adapter is.  [/SIZE]> **fpgdu said:**
> [SIZE=2]

The laptop appears to be using the internal adapter, but i want it to use the ASUS adapter. [/SIZE][SIZE=2]


Any suggestions are welcome. Also, what can be done?[/SIZE][SIZE=2]
[/SIZE]
in network manager you can ask it it to disconnect whatever WIFI adapter you want.
  
you could also go to terminal and:
  
sudo ifdown wlan0
    
wlan0 is probably your internal, you will need to figure that out.
    
sudo ifup wlan0 
    
to bring it back up

[FONT=monospace]
[/FONT]

---

### Post by Elaztic on 2011-07-14
To get information on your network adapters you can use these commands in the terminal:

iwconfig
ifconfig

---

### Post by iiiears on 2011-07-14
Hello,

If you have a spare WiFi card and a length of usb cable
build a "Wok-tenna"  - okay-okay your neighbors will gawk
but it's geeky and a hell of a lot of fun!

Best Wishes.

---

### Post by haqking on 2011-07-14
> **Elaztic said:**
> To get information on your network adapters you can use these commands in the terminal:

iwconfig
ifconfig

These commands only display connection information, he needs to stop one from being used which i answered above.

---

### Post by grahammechanical on 2011-07-14
You might also be able to disable the internal WiFi adapter from the motherboard BIOS. I can. May be you can too.

Regards.

---

