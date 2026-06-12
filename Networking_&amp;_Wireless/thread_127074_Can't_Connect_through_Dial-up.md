---
title: "Can't Connect through Dial-up"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by z|x on 2006-02-08
I did all the steps that were needed that were stated in the other threads.
I made the connection but I can't connect. 
When I go to the terminal and type pon nothing happens. when i type poff, it something like there is no pppd connected...
When I go to System >> Administration >> Networking and activate the modem after filling in all the detials, nothing happens.

Is there anyother way to get through?? Also, is there any software like a connection manager that does this.

I have a U.S. Robotics Modem. I'm not sure if its a WinModem or what. I read somewhere on this forum that I would have to create a file to create a driver or something. Is that possible??

Thanks!!

---

### Post by StefanoCole on 2006-02-09
To know if your modem is a winModem or not go to [http://linmodems.org/]("http://linmodems.org/")

About "sudo pon": if you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum.

Stefano

---

### Post by z|x on 2006-02-09
My modem isnt a linmodem. I cant find a driver anywhere for it. Its a U.S. Robotics 56k v.92 Fax Modem Internal. The model number is 3090.

---

### Post by StefanoCole on 2006-02-10
Go to [http://linmodems.org]("http://linmodems.org") and download the ScanModem utility. Follow the instructions to run it. It generates a file named ModemData.txt. Read it carefully to see if a driver for your modem is available.

Stefano

---

### Post by z|x on 2006-02-10
[QUOTE=StefanoCole]Go to [http://linmodems.org]("http://linmodems.org") and download the ScanModem utility. Follow the instructions to run it. It generates a file named ModemData.txt. Read it carefully to see if a driver for your modem is available.

Stefano[/QUOTE]
not available

---

### Post by the_duce on 2006-02-10
Did you go to the US Robotics web site?

---

### Post by z|x on 2006-02-10
[QUOTE=the_duce]Did you go to the US Robotics web site?[/QUOTE]
yep, only drivers for windows.

---

### Post by the_duce on 2006-02-10
Here's a page from their web site [http://www.usr.com/support/756/756-ug/two.html#Linux]("http://www.usr.com/support/756/756-ug/two.html#Linux")

Oh, is your modem PCMCIA?

---

### Post by the_duce on 2006-02-10
Hey, you can go to Wikipedia, and See If someone posted a guide on there.

---

### Post by z|x on 2006-02-10
[QUOTE=the_duce]Hey, you can go to Wikipedia, and See If someone posted a guide on there.[/QUOTE]
nope

---

