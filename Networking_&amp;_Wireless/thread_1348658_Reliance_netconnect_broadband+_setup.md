---
title: "Reliance netconnect broadband+ setup"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by tilakadhya on 2009-12-07
Hi,

I have bought Reliance netconnect broadband+ recently but not able to connect it to my Ubuntu. I love to use Ubuntu only but for this USB modem I have to open it in windows. I am desperately need your help for setting up USB modem (reliance) in my Ubuntu box. Any help will be highly appreciated.
Here is the device details --- Huawei EC1260

Awaiting for your help.

Cheers,

Tilak

---

### Post by harshguy on 2009-12-08
What I did was:

1. Plug in the modem into the port of my computer
2. If the computer successfully senses the device, open the network selector (icon is on top panel), and click on "Auto Mobile Broadband (CDMA) connection"
3. Obviously, first it won't work, because you need the username and password. But it is needed for another step.
4. Right click on the network icon and click "Edit Connections".
5. On the top of the window that opens, there will be a bunch of tabs. Click on the "Mobile Broadband" tab.
6. If everything is fine, you should see the "Auto Mobile Broadband (CDMA) Connection"
7. Click on the selection in the window and click the "Edit" button.
8. Enter the access no., username and password. Usually, the access no. will be there.
9. Click Apply, and repeat step no. 2.
10. Hopefully, it should connect, and you should see an antenna with waves coming out of it replace whatever icon represents the network manager.

It is easy, and requires no usage of the terminal. Good Luck!
I've also given pics, to make this process easier.[LIST=1]
[/LIST]

---

### Post by tilakadhya on 2009-12-10
Thanks for your so elaborate reply...

But I am struggling in another thing... Not getting my Nework Manger... and since not connected to net im not getting it from internet... so what to do ? any work around ?

Thanks
Tilak

---

### Post by tilakadhya on 2009-12-11
well today i have improved my ubuntu to the 9.10... its showing me the network-manager... i gave the username password but its not connecting...
what to do...? 
please let me know...

cheers
tilak

---

### Post by harshguy on 2009-12-12
You did give in the right access number(the topmost number in the edit part)?
Did you get the Auto Mobile Broadband(CDMA) connection thing, right?
Please reply ASAP as it will help a lot.:KS

---

### Post by tilakadhya on 2009-12-14
sorry for my late reply again...

yes I gave the correct no. its showing Network manager... and from this I choose the wirelss broadband tab and gave the passwd... its accepting... but showing no connection... 
I don't know how to proceed next... 

expecting ur help...

thanks in advance

tilak

---

### Post by harshguy on 2009-12-19
OK...one more question.
What did you do after entering the numbers and clicking apply? 
If you don't, it wont connect, because the computer wont know what to connect to.
Please reply ASAP.:P:)

---

### Post by tilakadhya on 2009-12-21
nothing... just entered the numbers and apply...
seems u have the answer... please let me know the next step ASAP :) :)

cheers

---

### Post by tilakadhya on 2009-12-23
hey harshguy,

where is ur next reply :(
am waiting for u... still fighting with netconnect USB... 

thanks

---

### Post by harshguy on 2009-12-25
ok...maybe after clicking apply, you aren't clciking on the network manager and connecting to the Auto Mobile Broadband thing.

After clicking apply, **_repeat step no. 2_**.

If u still don't get connected, please post again.

ttyl:P

---

### Post by kcode on 2009-12-25
Use wvdial. Follow this link : 
[http://reliancewireless.wordpress.com/2009/05/01/setting-up-your-reliance-broadband-connection-in-linux/]("http://reliancewireless.wordpress.com/2009/05/01/setting-up-your-reliance-broadband-connection-in-linux/")

EDIT : Just found this -> [http://ubuntuforums.org/showthread.php?t=843973]("http://ubuntuforums.org/showthread.php?t=843973")

---

