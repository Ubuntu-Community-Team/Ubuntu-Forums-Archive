---
title: "BSNL broadband modem connection problem"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by scorpion2189 on 2009-05-18
I have UT 300 R2U modem connected via usb in windows. How do i configure it in Ubuntu? Please give a step by step guide as i am a newbie.. I use Ubuntu 9.04. Please suggest any GUI program other than Ubudsl for the job. Ubudsl hangs at "Please connect your modem"

---

### Post by superprash2003 on 2009-05-18
well it should work without any drivers in ubuntu as well.. why cant you use LAN isntead..

---

### Post by scorpion2189 on 2009-05-19
It doesnt work.. Ubuntu doenst detect my usb modem. I dont have ethernet card. How should i connect it? any other programs other than ubudsl?

---

### Post by superprash2003 on 2009-05-19
strange . i've tried it with the same modem in ubuntu and it worked, connect it via USB and go to the terminal and type **ifconfig** and post output here

---

### Post by kpkeerthi on 2009-05-19
No drivers needed. Connect it via [ethernet port]("http://en.wikipedia.org/wiki/Ethernet_port"). The cable should be cheap.

---

### Post by superprash2003 on 2009-05-19
i think scorpion2189 said that he doesnt have a LAN port

---

### Post by neo_1in on 2009-05-19
I have a Tata Indicom usb modem at home which works just fine with wvdial.
```
sudo wvdial
```
You should go over the documentation that came with the modem.

---

### Post by scorpion2189 on 2009-05-20
thanks for the replies..
Here is the report of ifconfig:
  Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

the code sudo wvdial doesnot work, it says invalid command. what next?
I dont have LAN port.
Ubuntu recognizes my portable usb hard disk but not my modem. It also recognizes my external dvd writer.i have some drivers for linux in my modem drivers cd, but i dont know how to install them. Please see the attached readme file from the cd, please explain how to go about.

---

### Post by superprash2003 on 2009-05-20
ok , try this

1)copy ASL-25020 ( from cd ) to your home folder , eg /home/prash
2)then type the following in the terminal

cd ./ASL-25020
sudo make clean
sudo make all

got this from the txt you posted, i feel you should just purchase a LAN card , a PCI one , it should not cost more than 200 Rupees

---

### Post by scorpion2189 on 2009-05-20
did that it returned errors as attached. next what? isnt the drivers for 2.4? ubuntu 9.04 is 2.06..
are all ethernet cards same or there are types? you suggested PCI , so guessed.

---

### Post by superprash2003 on 2009-05-20
i mean there is USB and stuff.. if its a desktop PCI is the best..

---

### Post by scorpion2189 on 2009-05-20
thats fine.. but isnt there any way out with usb?

---

### Post by neo_1in on 2009-05-21
> **scorpion2189 said:**
> the code sudo wvdial doesnot work, it says invalid command. what next?

Install wvdial package. It is there in ubuntu repositories. Then try again.

---

### Post by scorpion2189 on 2009-05-21
how can i install that if i dont get a connection in the first place? is there any other good dsl connection program like ubudsl? i used ubudsl but it hangs..

---

### Post by GeorgeVita on 2009-05-21
> **neo_1in said:**
> Install wvdial package. It is there in ubuntu repositories. Then try again.
> **scorpion2189 said:**
> how can i install that if i dont get a connection in the first place? is there any other good dsl connection program like ubudsl? i used ubudsl but it hangs..

Hi **scorpion2189**, please take a look to my post: "*How I restored the missing wvdial (Ubuntu 9.04)*": **[http://ubuntuforums.org/showpost.php?p=7245790&postcount=8](http://ubuntuforums.org/showpost.php?p=7245790&postcount=8)**

Hope this "offline" solution will help you!

Regards,
George

---

### Post by superprash2003 on 2009-05-21
this may sound stupid , but try to get hold of ubuntu 7.10 (gutsy) , i remember trying the exact same modem on gutsy using USB and it worked right away.. technically it should work on 9.04 as well , but just incase..

---

### Post by scorpion2189 on 2009-05-22
hey GeorgeVita the wvdial is not the main problem as  the modem itself is not recognised. I  did  not get the solution you suggested to the problem "How to restore the usbserial driver (9.04)".. could you please explain it in detail. How can i use update manager if i cant connect to the net? can i download the update in windows and use it in ubuntu? where can i download it? Is there something like "Add Hardware" in ubuntu?

---

### Post by GeorgeVita on 2009-05-22
Hi **superprash2003**,

> **superprash2003 said:**
> this may sound stupid , but try to get hold of ubuntu 7.10 (gutsy) , i remember trying the exact same modem on gutsy using USB and it worked right away.. technically it should work on 9.04 as well , but just incase..

Unfortunately 9.04 is not backwards compatible in some points. It has no **wvdial** (and associated programs), the **usbserial** driver is encapsulated into kernel (cannot run as driver to add parameters for a non detected modem) and finally if you are in the extreme condition that you have no other internet connection, you cannot use Synaptic to get them.
---------------------
Hi **scorpion2189**,
as you faced many problems with 9.04 and till a newer version has all the tools you need to detect your modem you could use 8.10 (?)
Finally we need some extra data from you, just in case we think another way:
Boot without your modem, wait for the system to stabilize, attach the modem to a USB port, wait 20 seconds, open a terminal window and try:
**dmesg**
**lsusb**
**ls /dev/ttyU* /dev/ttyA* /dev/ttyH***

Post here the _last 10-15 lines_ concerning modem or serial port/driver and the output of the other 2 commands.

Regards,
George

---

### Post by superprash2003 on 2009-05-22
i dont think wvdial is required for ADSL .. i've used it successfully with pppoeconf

---

### Post by scorpion2189 on 2009-05-22
Hi, this is the output:
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 003: ID 152e:2507 LG (HLDS) 
Bus 001 Device 002: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0451:6060 Texas Instruments, Inc. RNDIS/BeWAN ADSL2+
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
ls: cannot access /dev/ttyU*: No such file or directory
ls: cannot access /dev/ttyA*: No such file or directory
ls: cannot access /dev/ttyH*: No such file or directory
ubuntu@ubuntu:~$ 

am ready to ue not only 8.10 but also 8.04 if my modem is detected!!

---

### Post by scorpion2189 on 2009-05-26
Hey GeorgeVita, I have posted the required info. Pleaase help..
Thanks in advance.

---

### Post by GeorgeVita on 2009-05-26
Hi **scorpion2189**,
no post from me means that I have no new ideas for this case!

I saw your posted data almost "online". I searched all over internet, downloaded from BSNL specs, drivers and howto's but the only note I kept was from [https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html](https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html)

"***If you have a modem that can connect both via USB and ethernet, or an ethernet router, you should use the ethernet connection.***"

I have no ADSL modem to test it locally. My "help" here was about wvdial but unfortunately as you realize this is not the main problem.

Regards,
George

---

### Post by scorpion2189 on 2009-05-28
Thanks alot for your help.. I would be looking forward to buying an ethernet card as this USB stuff is not working. Thans once again for your effrots.

---

