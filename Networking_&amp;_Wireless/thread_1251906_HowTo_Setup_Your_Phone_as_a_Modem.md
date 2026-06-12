---
title: "HowTo: Setup Your Phone as a Modem"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by LonelyTraveler on 2009-08-28
It has been a while since I’ve used my phone as a modem so it never struck me to do a howto about it, but last weekend my friend decided to give Ubuntu another try and as he uses his cellphone to get online, he wanted to know how to do this. I did some research to be able to help him so I decided to share it with the rest of the world.

After plugging my phone in in Ubuntu 9.04 a installation box popped up asking me for some information about creating an internet connection. So it turns out that using your phone as a modem in Ubuntu 9.04 is extremely easy and takes about 10 seconds to set up. But for those who has older versions, or who’s distribution does not support this yet, keep reading. I’m going to run through doing it the old way first and then just quickly show you how easy it is on Ubuntu 9.04 and up.

I’ve found a lot of information on this subject online, but it seems like they are written for the more experienced Linux user and not the total noobie who still has to learn what a repository is and how it works. So this howto is going to be like those “For Dummies” books, but if you still don’t understand or if it doesn’t work for you, tell me so we can troubleshoot your problem.

I’m currently using Ubuntu 9.04 and 9.10 Alpha. If you’re using an older version or even a different distribution, this howto should still work, but you might have to download different files than those I link to in this post. As I can’t test it on each and every version, tell me if you’re having problems so we can troubleshoot it further.

I’m using a Samsung Z400 to test this that does not ask any questions when connecting it to my computer, but some phones might ask if you want to use the mass storage function, the PC suite or just connect it as a phone. If it asks something like this, select phone.

If you have another internet connection running in Linux it makes things a whole lot easier to get the applications and packages you need, but in my friend’s case, he doesn’t have another connection. I will be covering both sides.
[U][B]
Installing wvdial on an Internet Connected Computer
[/B][/U]
   1. Go to Applications – > Accessories – > Terminal
   2. In the Terminal box that pops up type the following without the quotes: “sudo su”
      This is to make you root or better known as the administrator in order to do admin tasks like installing a package. Because of this it will now ask you for your password. Enter that and hit enter. Note that, depending on your Linux distribution, you might not see anything happening on the screen while typing your password.
   3. Type: “apt-get install wvdial”. It might ask you to install some other applications and/or confirm the download of the package(s). Hit “y” and then enter. Wait for the download to finish and install. This should just take a few of seconds.
   4. Now you’re ready to configure wvdial, so skip the next section to get to the wvdial configuration section.

**_Installing wvdial on an Offline Computer_**

You will need to download the needed files on a computer that does have an internet connection or even in Windows. On a huge Linux distribution like Debian, the files might be on the CD. You’ll have to check. In that case you can use the above method.

   1. Click on the following files to download each of them:
          * [xplc]("http://za.archive.ubuntu.com/ubuntu/pool/main/x/xplc/libxplc0.3.13_0.3.13-2_i386.deb")
          * [wvstreams-base]("http://za.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-base_4.4.1-1.1_i386.deb")
          * [wvstreams-extras]("http://za.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-extras_4.4.1-1.1_i386.deb")
          * [libuniconf]("http://za.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.4_4.4.1-1.1_i386.deb")
          * [wvdial]("http://za.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1+nmu2_i386.deb")
   2. Now save each of these files on a flash drive or CD and head over to your offline Ubuntu installation.
   3. Double click on each of these files to install them one by one. Be sure to start with xplc and finish with wvdial. Depending on the distribution and version you’re using, you computer might tell you that it is better to use the package in the channel (repository) but as you’re not online, this is not posible. Just continue past the warning. You will see when it is done installing.
   4. Now you’re ready to configure wvdial.
[B][U]
Configuring wvdial[/U][/B]

   1. At this point you don’t need an internet connection anymore, so unplug any internet cables and modems. This will prevent wvdial from trying to configure the wrong device as a modem.
   2. Attach your phone via cable and wait a few seconds.
   3. In the terminal window type: “wvdial.conf”. You will see something like the following scroll by:(Remember to type "sudo su" first.)

      ```
root@ubuntu:/home/ubuntu# wvdialconf
      Editing `/etc/wvdial.conf'.Scanning your serial ports for a modem.ttyS0<*1>: ATQ0 V1 E1 — failed with 2400 baud, next try: 9600 baud
      ttyS0<*1>: ATQ0 V1 E1 — failed with 9600 baud, next try: 115200 baud
      ttyS0<*1>: ATQ0 V1 E1 — and failed too at 115200, giving up.
      Modem Port Scan<*1>: S1   S2   S3
      WvModem<*1>: Cannot get information for serial port.
      ttyACM0<*1>: ATQ0 V1 E1 — OK
      ttyACM0<*1>: ATQ0 V1 E1 Z — OK
      ttyACM0<*1>: ATQ0 V1 E1 S0=0 — OK
      ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 — OK
      ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
      ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
      ttyACM0<*1>: Modem Identifier: ATI — Manufacturer: SAMSUNG ELECTRONICS CORPORATION
      ttyACM0<*1>: Speed 4800: AT — OK
      ttyACM0<*1>: Speed 9600: AT — OK
      ttyACM0<*1>: Speed 19200: AT — OK
      ttyACM0<*1>: Speed 38400: AT — OK
      ttyACM0<*1>: Speed 57600: AT — OK
      ttyACM0<*1>: Speed 115200: AT — OK
      ttyACM0<*1>: Speed 230400: AT — OK
      ttyACM0<*1>: Speed 460800: AT — OK
      ttyACM0<*1>: Max speed is 460800; that should be safe.
      ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
      WvModem<*1>: Cannot get information for serial port.
      ttyUSB0<*1>: ATQ0 V1 E1 — OK
      ttyUSB0<*1>: ATQ0 V1 E1 Z — OK
      ttyUSB0<*1>: ATQ0 V1 E1 S0=0 — OK
      ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 — OK
      ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
      ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
      ttyUSB0<*1>: Modem Identifier: ATI — Manufacturer: Novatel Wireless Incorporated
      ttyUSB0<*1>: Speed 9600: AT — OK
      ttyUSB0<*1>: Max speed is 9600; that should be safe.
      ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
      WvModem<*1>: Cannot get information for serial port.
      ttyUSB1<*1>: ATQ0 V1 E1 — failed with 2400 baud, next try: 9600 baud
      ttyUSB1<*1>: ATQ0 V1 E1 — failed with 9600 baud, next try: 9600 baud
      ttyUSB1<*1>: ATQ0 V1 E1 — and failed too at 115200, giving up.
      Found an USB modem on /dev/ttyACM0.
      Modem configuration written to /etc/wvdial.conf.
      ttyACM0<Info>: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;
      ttyUSB0<Info>: Speed 9600; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;
```
      As you can see in bold, it detected my phone. The same should happen with your phone. (I made the text bold myself by the way.)
   4. Next, in the terminal, type: “gedit /etc/wvdial.conf”. Configure this file so that it looks like this:
     ```
 [Dialer Defaults]
      Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
      Modem Type = USB Modem
      Phone = *99#
      ISDN = 0
      Username = A
      Init1 = ATZ
      Password = B
      Modem = /dev/ttyACM0
      Baud = 460800
      Stupid Mode = Yes
```
      The phone, username and password field will depend on your network. If your network does not require a username or password, make the username a A and password a B like in my case as wvdial does not like blank fields. You can get this information from your network. The Modem you can leave like it was in your original file as that is the port your cellphone is attached to and might differ from mine. The Baud area you can also leave as is.
   5. Save and close the above file and type the following in the terminal window: “wvdial”. You will see something similar to this pop up:
     ```
 root@ubuntu:/home/ubuntu# wvdial
      –> WvDial: Internet dialer version 1.60
      –> Cannot get information for serial port.
      –> Initializing modem.
      –> Sending: ATZ
      ATZ
      OK
      –> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
      ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
      OK
      –> Modem initialized.
      –> Sending: ATDT*99#
      –> Waiting for carrier.
      ATDT*99#
      CONNECT
      –> Carrier detected.  Starting PPP immediately.
      –> Starting pppd at Wed Aug 26 18:53:15 2009
      –> Pid of pppd: 6855
      –> Using interface ppp0
      –> pppd: &#65533;WA  aA
      –> pppd: &#65533;WA  aA
      –> pppd: &#65533;WA  aA
      –> pppd: &#65533;WA  aA
```

      It might seem to you like the window freezed, but when you get to this point and all went well, you should be online now. Open a website to check that it worked. Leave the terminal window open (just minimize it). When you’re done, come back to this window and press Cnrl + C. This will disconnect your phone from the internet and display something like this in the terminal window:

    ```
  ^CCaught signal 2:  Attempting to exit gracefully…
      –> Terminating on signal 15
      –> pppd: &#65533;WA  aA
      –> Disconnecting at Wed Aug 26 18:53:54 2009 
```

That is all there is to it. Very easy once you know what’s going on. To make it a little bit easier, I’ll show you how to create an icon on your desktop so that you can just double click that to go online, instead of typing wvdial each time as you might forget that command anyway.

**_Creating a Desktop Icon to connect to the Internet_**

   1. Right click on the desktop and select “Create Launcher”.
      [CENTER][IMG]http://technologyheaven.com/wp-content/uploads/2009/08/1.png[/IMG][/CENTER]
   2. Edit the box that pops up so that it looks like this:
      [CENTER][IMG]http://technologyheaven.com/wp-content/uploads/2009/08/6-300x141.png[/IMG][/CENTER]
   3. After clicking ok you will have an icon on the screen called Internet. You can change this name in the above box if you want to and you can also change the icon by clicking on it in the above box and choosing something else.
   4. Double click on the Internet icon. You will see a terminal window pop up asking for your password. enter it and hit enter. You will then see the same thing you did when typing “wvdial” earlier.

On Ubuntu 9.04 and Newer

It really can’t be easier to use your phone as a modem in Ubuntu 9.04 and newer. Just follow the next steps:

   1. Plug in your phone via USB cable and wait a few seconds. A window like the one below will pop up.
   [CENTER]   [IMG]http://technologyheaven.com/wp-content/uploads/2009/08/11-300x268.png[/IMG][/CENTER]
   2. Click forward and then select your country and network.
     [CENTER] [IMG]http://technologyheaven.com/wp-content/uploads/2009/08/2-300x294.png[/IMG][/CENTER]
   3. Click forward again and choose a name for your new internet connection.
[CENTER]      [IMG]http://technologyheaven.com/wp-content/uploads/2009/08/31-300x295.png[/IMG][/CENTER]
   4. Click apply and you’re done!
   5. To connect, simply click on the network icon close to the time and select your connection. (Your network connection icon might be 2 little computer monitors.) Just make sure you select the connection that is listed under your phone’s name:
      4It’s a bit weird that this box is so big, but it might be that it’s just with the alpha version I have.

So there you have it. Now you can easily use your phone as a modem. If this didn’t work for you or if you have any questions/suggesstions, ask me.

---

