---
title: "Kubuntu and Tata indicom Dialup USB modem woes"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by hideipuser on 2009-06-28
Hi  I am new to this forum.  I have just installed Ubuntu 9.04 and Kubuntu 9.04 side by side.  I am using Tata Indicom dialup USB modem to connect internet.  The problem is with Kubuntu. During startup the modem gets detected by Knetwork manager as ttyACM0. But network manager could not auto configure the modem.  I created a new connection with Knetwork Manager, when I connect - the network manager gets hung. It shows as &quot;Preparing to connect&quot;.  I installed KPPP, configured and tried with it, it showed me a message the modem does not respond.  I treid with pppconfig also , plog shows that the script failed to connect or something.  As the last resort, I installed WVDIAL , I was able to get Kubuntu connected to the internet. Felt happy. I did a system update, fine. Before the reboot, I installed Guarddog.  I did a reboot. From then, the wvdial shows in the terminal that I am connected if I dialup(shows local IP, remote IP etc.,)  But none of the applications could connect the network. Tried konqueror and Bitdefender etc., , no luck.  I thoght it was Guarddog which blocks the outgoing traffic, so I removed and tried connecting many times. Nothing happened.  The same modem  works perfectly with Ubuntu 9.04 without any need of configuration.  What exactly is blocking my internet connection?  It is very unfortunate that nowhere I could find a solution to this in our forum.  Pls help me, Thanks.

---

### Post by sundar_ima on 2009-07-06
i am also using Tata indicom Plug2Surf service on Kubuntu and Ubuntu. Like you i also encounter problem using network manager. Later i came to know that it is a bug in the Kde network manager which caused problem. Again i tried to connect via KPPP there too i encountered bug, it simply crashes every time (till now). Lastly i could configure usb modem using pppconfig which i found simple and easy...

Now i have installed gnomeppp and tried to connect but because of permission issue it is not allowing to connect. Does any body have a solution for this?

---

### Post by tp42 on 2009-07-26
Regarding the permission woes. Perhaps you have to add your user to the dip and the dialout group?

 $ sudo adduser USERNAME dip
and then
 $ sudo adduser USERNAME dialout

where USERNAME = name of your user

The make a restart and try it again.

Hope this helps.

Best regards, tp42

---

### Post by suhani76 on 2009-08-08
The idea of a dongle although is amazing but there are so many speed and network issues that just beat the whole purpose. I have so far got good reviews about Tata  photon Plus..seems it is the best so far and a speed of 3.1 Mbps actually sound good. I guess I will go for this one. Take a look [http://www.tataindicom.com/HSIA-service-personal.aspx?um=12](http://www.tataindicom.com/HSIA-service-personal.aspx?um=12)

---

### Post by d.dinakaran on 2009-08-24
Hi all,
I am newbie to linux.
I dont know much information about linux.
 
I have installed Ubuntu and KDE desktop over ubuntu
 
I have the tata indicom photon+ cdma usb modem for internet connection
 
When i connect it with ubuntu gnome environment it working perfectly but i am unable to connect it through KDE desktop
 
I dont know how to configure.
 
It would be thankful if any one tell step by step procedure for how exactly configure and make work that usb modem in KDE
 
Details are follows
Service provider: Tataindicom
machine: Huawei EC1260
Technology: CDMA and HSPA

---

### Post by sundar_ima on 2009-08-24
I am also using Kubuntu for a while. It is very easy to configure tataindicom on linux OS (but not reliance) with out trouble. Here we go...

Insert your modem wait for few second then type following in the terminal (Kickoff menu-->applications-->system --> Terminal)

```
sudo pppconfig
```

This will bring up new window. Read the instructions carefully. 
select the following options on each screen 

> Create

> tata 

> Dynamic

> PAP

> internet

> internet 

> 115200 

> Tone

> #777 

> yes

> ok

> /dev/ttyACM0 

> Finished Write files and return to main menu 

> ok

> Quit   Exit this utility 


Now you have configured your modem. For connecting to internet then type following command in the terminal...

```
sudo pon tata
```


Once you are connected to internet you can close the terminal.
For disconnecting type

```
sudo poff tata
```

If you do not want to type sudo every time then you can follow up what **tp42** said in the 4th post (this thread).

Finally you may want to login to internet directly every time start / restart your computer. To do this create a text file in your home folder (or any directory in your home folder) and type **pon tata** and save as tata.sh (you must add ".sh" after tata). Now right click on the newly created tata.sh file --> properties --> permission tab --> check "is executable" then close all window. Go to system settings (kick off menu--> applications --> settings -- > system settings) --> Advanced (tab) --> Auto start --> Click add script --> navigate to tata.sh and select ok. Restart your computer and happy browsing :)

Hope this will help you. 
Gud Luck.

---

### Post by sundar_ima on 2009-08-24
> **tp42 said:**
> Regarding the permission woes. Perhaps you have to add your user to the dip and the dialout group?

 $ sudo adduser USERNAME dip
and then
 $ sudo adduser USERNAME dialout

where USERNAME = name of your user

The make a restart and try it again.

Hope this helps.

Best regards, tp42


It worked flawlessly. Forgot to tell you one thing man...

**Thank you** :)

---

### Post by p1977p on 2009-09-22
> **hideipuser said:**
> Hi  I am new to this forum.  I have just installed Ubuntu 9.04 and Kubuntu 9.04 side by side.  I am using Tata Indicom dialup USB modem to connect internet.  The problem is with Kubuntu. During startup the modem gets detected by Knetwork manager as ttyACM0. But network manager could not auto configure the modem.  I created a new connection with Knetwork Manager, when I connect - the network manager gets hung. It shows as &quot;Preparing to connect&quot;.  I installed KPPP, configured and tried with it, it showed me a message the modem does not respond.  I treid with pppconfig also , plog shows that the script failed to connect or something.  As the last resort, I installed WVDIAL , I was able to get Kubuntu connected to the internet. Felt happy. I did a system update, fine. Before the reboot, I installed Guarddog.  I did a reboot. From then, the wvdial shows in the terminal that I am connected if I dialup(shows local IP, remote IP etc.,)  But none of the applications could connect the network. Tried konqueror and Bitdefender etc., , no luck.  I thoght it was Guarddog which blocks the outgoing traffic, so I removed and tried connecting many times. Nothing happened.  The same modem  works perfectly with Ubuntu 9.04 without any need of configuration.  What exactly is blocking my internet connection?  It is very unfortunate that nowhere I could find a solution to this in our forum.  Pls help me, Thanks.
Hi I had the same problem. In gnome-ppp, check "enable stupid mode" option. Also edit the init strings so that init3=at+crm=1
Now click connect. that should be it!

---

### Post by jkohler2 on 2009-11-09
Earlier versions of Ubuntu, 9.04, 8.10, and 8.04 have worked with both my usb dial up modems, the US Robotics, and Zoom:

first, I installed the graphic tool

sudo apt-get install gnome-ppp

Second, I went to [www.linuxant.org](www.linuxant.org) to find a driver for my distro, among the fedora, SUSE,  and the others.  At the end of the list was an Ubuntu
driver, in a deb.zip file.

I unzipped the file, and installed with the program:

dpkg dgc1.09..........deb

Then, calling the gnome-ppp as the super user.....

sudo gnome-ppp

I populated the windows with id/password/isp modem phone, tone or pulse,
and other options. 

It worked the first time every time.

Until Karmic Koala, 9.10.    Current message is "modem not found."

---

