---
title: "Can't Install Network Card Driver"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by emagine on 2010-02-13
Hello Linux Community,

I recently installed Ubuntu 9.10 on an old family laptop. It is a Compaq Presario V2000. Everything works perfectly except no wireless networks are recognized, even though I know there are available networks. My network controller is detected but is not doing it's job, which is finding available wireless networks! Using "system testing" I found this out about my network controller:

"Detecting your network controller(s):

Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)"

I know there are similar posts as mine, but I searched and none use the same netork controller.
Please Linux Community, help me out.
Than you.

P.S.  I have already tried the below steps, with no success.  Any other way?
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Xog on 2010-02-13
If you have the drivers, put them in a folder anywhere within your ubuntu partition. Install NDISwrapper. Load the driver using NDISwrapper and you should be able to use Network Manager to connect.

NDISwrapper (you will need all 3 packages for whatever system you have): 

   1. For 9.10 Karmic Koala
         1.

            [http://packages.ubuntu.com/karmic/misc/ndiswrapper-common](http://packages.ubuntu.com/karmic/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/karmic/net/ndisgtk](http://packages.ubuntu.com/karmic/net/ndisgtk) 
   2. For 9.04 Jaunty Jackalope
         1.

            [http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk) 
   3. For 8.10 Intrepid Ibex
         1.

            [http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/intrepid/net/ndisgtk](http://packages.ubuntu.com/intrepid/net/ndisgtk) 
   4. For 8.04 Hardy Heron
         1.

            [http://packages.ubuntu.com/hardy/misc/ndiswrapper-common](http://packages.ubuntu.com/hardy/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk) 
   5. For 6.06 Dapper Drake
         1.

            [http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
         2.

            [http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)

To access NDISwrapper once it's installed go to System > Administrator > Windows Wireless Drivers

---

### Post by emagine on 2010-02-13
> **Xog said:**
> If you have the drivers, put them in a folder anywhere within your ubuntu partition. Install NDISwrapper. Load the driver using NDISwrapper and you should be able to use Network Manager to connect.

NDISwrapper (you will need all 3 packages for whatever system you have): 

   1. For 9.10 Karmic Koala
         1.

            [http://packages.ubuntu.com/karmic/misc/ndiswrapper-common](http://packages.ubuntu.com/karmic/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/karmic/net/ndisgtk](http://packages.ubuntu.com/karmic/net/ndisgtk) 
   2. For 9.04 Jaunty Jackalope
         1.

            [http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk) 
   3. For 8.10 Intrepid Ibex
         1.

            [http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/intrepid/net/ndisgtk](http://packages.ubuntu.com/intrepid/net/ndisgtk) 
   4. For 8.04 Hardy Heron
         1.

            [http://packages.ubuntu.com/hardy/misc/ndiswrapper-common](http://packages.ubuntu.com/hardy/misc/ndiswrapper-common)
         2.

            [http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)
         3.

            [http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk) 
   5. For 6.06 Dapper Drake
         1.

            [http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
         2.

            [http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)

To access NDISwrapper once it's installed go to System > Administrator > Windows Wireless Drivers

This didn't work.  Under Administrator there is no "Windows Wireless Drivers" option.  And I don't understand what downloading these things does.  I already had them installed.  But how is it supposed to work, you just install these and the boom, my wireless card works?

---

### Post by emagine on 2010-02-13
This information should help most people with this problem:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Thanks for your help!

---

