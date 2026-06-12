---
title: "Connecting Telkom 3G on Ubuntu 8.10"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by josamoto on 2009-01-11
I have a Huawei E220 modem, and using Telkom 3G (South Africa) to connect to the internet. I can't figure out exactly how to get this connection working on Ubuntu 8.10?

The configuration dialog box allows me to select 3G service providers like Virgin, Vodacom, MTN, Cell-C, but not Telkom, which is understandable, as Telkom only released their 3G service a couple of weeks ago.

Ubuntu appears to be picking up the device, but when setting up, I just can't connect.

Can anyone possibly point me in the right direction?

---

### Post by dmizer on 2009-01-11
Have a look here: [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220)

---

### Post by josamoto on 2009-01-21
Hi dmizer! Thank you so much for your links and advice. After a couple of days, retried setting up my modem, and this time I had much luck.

It turns out that the South African provider, Telkom's 3G works on Kubuntu!!! I'm amazed! Telkom don't often get a lot of things right.

My major problem was probably the pin on the sim card, I popped it in my cellphone, turned the pin checking off, and hey presto!

It turned out that I did not even need to do anything in the command line at all. I started fiddling with the kNetworkManager taskbar settings (in Kubuntu) and did my settings as follows:

Right click the kNetworkManager icon in your Kubuntu taskbar,
Click "New Connection" >> select your modem (in my case it was ttyUSB0)
On the first page, leave everything blank except:
[LIST]
[*]Number : *99#
[*]APN : internet
[*]Network Type : Any
[/LIST]
With Telkom, Username and Password is blank!!!
Click Next - leave this page unchanged
Click Next again - I left it unchanged with default values
(I want to know if it's safe however to change Baud rate to 460800?)
Click Next again (...this guys becoming boring now) - we won't be using manual IP configuration for Telkom.
Click Next and type a name for your connection - I named mine Telkom 3G, but you can call yours Anny Fanny if you want.
If so desired, check the Autoconnect - guess what this does?
Click Save, or Connect & Save, (unfortunately the Connect, Make Me Coffee & Save is unavailable.)

Now depending on whether you enabled Autoconnect or not, you might have to right click your kNetworkManager icon, and just click on "Telkom 3G" or whatever you named your connection.

Hope this helps, and if anyone has any suggestions on making this connection better, please, I'm actually a Linux noob.

Next question: Can anyone recommend a network monitoring application that will tell me how much data this Telkom 3G connection of mine uploads / downloads.

This is South Africa, we get charged per MegaByte...sucks...I know.

Bye!

---

