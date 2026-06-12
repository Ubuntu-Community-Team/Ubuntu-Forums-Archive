---
title: "Help getting connected with Internet!"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by Saurabhdua on 2009-10-11
Hi There!

My Router is configured to work in "Bridge Mode". In WINDOWS OS, as soon as I double click the Broadband Icon it pops up a "Login Screen" with my Username & Password stored within it & Iam able to connect to the Internet quite easily!

Now...how to emulate the same settings within Ubuntu(Version-9)? Where would I get the same Login Screen? How should I connect to the Internet?

Please help....!

---

### Post by GuyCorngood on 2009-10-11
From your description, I'm guessing you have a DSL connection. Go to the System menu -> Preferences -> Network Connections, choose the DSL tab, click add, and set up your connection. You shouldn't need to enter anything but your username and password.

---

### Post by Saurabhdua on 2009-10-12
Thanks Dear!

But here goes the main concern....!

I connect to my DSL Connection using USB.Is there an easy way to make UBUNTU recognize my USB Connection to my ADSL Router?

Aren't the USB Drivers available through repositories?

---

### Post by GuyCorngood on 2009-10-13
Yeah, that's a lot harder. I don't have any experience with USB DSL modems, but I know enough to say you should use Ethernet if you possibly can. You should be able to get a better DSL modem for under $50.

If you don't want to spend money on this, read [the documentation on USB modems]("https://help.ubuntu.com/community/UsbAdslModem"). The exact procedure depends on what brand of modem you have. Good luck!

---

### Post by Saurabhdua on 2009-10-13
Thanks again!

But contrary to whatever claims that have been made in that suggested reading, I have always found USB Connection to Internet a lot more smoother,with less latency &  a rather  stable performance...!

Anyways, I do have a provision to suit the "Dual Connectivity" method.Just opted for USB one by choice!

Thumbs up..!

---

### Post by Bucky Ball on 2009-10-13
With your router plugged in open a terminal (Applications->Accessories) and paste this in:

```
lsusb
```

Does the router show as being plugged in?

---

### Post by Saurabhdua on 2009-10-14
Hello Bucky Ball!

I think..YES, it does show my Trendchip ADSL Router being connected as evident in the following output of the command-lsusb>>>

saurabhdua@saurabhdua-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 12a7:3160 Trendchip Technologies Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
saurabhdua@saurabhdua-desktop:~$ 


So..Dear..What Next?

---

### Post by Rich_B_uk on 2009-10-14
When I used Virgin Media here in the UK I would always opt for the wired LAN as opposed to the USB. Why not just try your router with that if you have a Cat5 cable lying around somewhere?

---

### Post by Bucky Ball on 2009-10-14
You need to match the details in:

System->Administration->Network

... with the information from the router. The router is connecting to the internet no problem? The card is signifying it is on with a blue light or something?

If so, you will need the ESSID (the name of the router or access point) and WEP or WPA security key. Set 'Configuration' to 'Auto DHCP (Configuration)'.

Also, could you open a terminal again and post the result of this command:

```
iwconfig
```You need to get the details of your router and get them matching on your computer.

---

### Post by Saurabhdua on 2009-10-21
You are one of the Lucky ones..! I have read that Virgin has initiated trials with 200Mbps Connection Speed using a Unique Compression technology(can't recall the name..)

Iam a keen follower of the BB development going on within UK  through BBC!...Kudos!

---

### Post by Bucky Ball on 2009-10-21
How you going with it S? Having any luck?

---

### Post by irohaphoto on 2009-10-21
Hello
I just installed ubuntu v9.04 on a new Acer notebook KAV60
dual boot with  xp for now.
It works great but I can't get my internet connection to work.
according to the beginners guide it should work just by plugging the lan cable in as it does on windows xp and vista. the beginners guide says that this is due to non DHCP but the wired lan works fine on xp and vista so I can't see what is the problem. 
any help would be appreciated.

---

### Post by Bucky Ball on 2009-10-22
> **irohaphoto said:**
> Hello
I just installed ubuntu v9.04 on a new Acer notebook KAV60
dual boot with  xp for now.
It works great but I can't get my internet connection to work.
according to the beginners guide it should work just by plugging the lan cable in as it does on windows xp and vista. the beginners guide says that this is due to non DHCP but the wired lan works fine on xp and vista so I can't see what is the problem. 
any help would be appreciated.

Hi. You should start a new thread about your issue rather than posting twelve deep in someone else's thread. You are much more likely to get help specific to your problem. Be as descriptive as possible in the thread title.

---

### Post by nanosaw on 2009-12-02
I Had same problem with my TP-Link ADSL modem TP8817. I cannot get connected to router/modem via USB-port. 
I had use 8.04 till 9.04 , there are not problem with it. Just I upgrade to 9.10 my USB-port cannot connected to any network device.

~$ lsusb
Bus 003 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 002: ID 12a7:3160 Trendchip Technologies Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13d1:abe6 A-Max Technology Macao Commercial Offshore Co. Ltd. 
Bus 001 Device 005: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

