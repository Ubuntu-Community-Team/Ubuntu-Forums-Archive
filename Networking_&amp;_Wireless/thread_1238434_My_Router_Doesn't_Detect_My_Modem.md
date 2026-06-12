---
title: "My Router Doesn't Detect My Modem"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by mohtasham1983 on 2009-08-12
Hi,

Recently my old netgear router started dropping connections several times a day, that's why, I decided to buy a better router. After doing a research, I bought Asus WL-500gP V2. 

I turned off my old router and connected all the cables to the new one and turned the new one on. Opened my browser and saw that it was trying to detect the internet connection which eventually failed. So I tried to set everything manually, but it was complaining that the subnet mask IP I was providing wasn't an IP, and didn't let me go further. 

When I tried to visit some websites it told me that You have set the wrong dynamic or static IP address for your WL-500gP V2.

Since, I heard very bad reviews about the company firmware, I decided to install dd-wrt firmware. I downloaded the mini-generic firmware (dd-wrt.v24_mini_generic.bin) and checked the md5 checksum and it was the correct one. 

I followed the instruction from [http://www.dd-wrt.com/wiki/index.php/Installation](http://www.dd-wrt.com/wiki/index.php/Installation) and took a look at [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=51486](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=51486) to make sure I don't brick my router. 

After hard resetting my router, I went to the web interface and tried to upload my dd-wrt firmware, but it was telling me that "Firmware upgrade file. It may result from incorrect image or error transmission. Please check the version of firmware and try again."

I tried mega generic firmware, as well, but got the same results. I even switched to Vista and installed the utilities that come with the CD and tried to change the firmware using them with no success. 

Then I downloaded the latest version of Asus firmware which was the same as the default one. When I tried to upload that one, it actually processed it and asked me to wait for 3 minutes. However, I wasn't still able to connect to the Internet.

Just to make sure if my router was working properly, I hooked up my old router again and connected my new router to it. Then I went to the web interface of my new router which showed that the connection between my new router and old router was established successfully. 

Since, I got the connection between my new and old router established, I realized that my new router is having problem establishing connection with my modem. I guess it's the problem with the default firmware.

The modem is inside my roommate's room who is out of town for next couples of days, so I cannot reset the modem for now to see if it solves the problem. 

However, I'm looking for a way to get the dd-wrt firmware working, as I heard the default firmware drops the connections very often.

I really appreciate if anyone can help me with this.

Thanks in advance.

---

### Post by hibliss on 2009-08-12
> **mohtasham1983 said:**
> Hi,
The modem is inside my roommate's room who is out of town for next couples of days, so I cannot reset the modem for now to see if it solves the problem. 

However, I'm looking for a way to get the dd-wrt firmware working, as I heard the default firmware drops the connections very often.


My guess is a hard powercycle of the modem, then the router will do the trick at getting the new router to pull the proper IP/DNS/Subnet from the line. Is this a cable modem?

As far as the upgrade to DD-WRT goes, there are three ways to load it. One is the web interface. Note that on the first flash to DD-WRT, you have to use a special firmware made for that router from DD-WRT. It is available here -- [http://dd-wrt.com/routerdb/de/download.php?file=1423]("http://dd-wrt.com/routerdb/de/download.php?file=1423"). The standard micro firmware image will not work. You seem to have tried the mini generic image, which will not work for the first flash.

If that is not working, you can give the other two a shot, one requires a Windows PC unfortunately -- [http://dd-wrt.com/wiki/index.php/Installation#Asus_WL500G_Premium]("http://dd-wrt.com/wiki/index.php/Installation#Asus_WL500G_Premium")

I personally have had success with the web interface, but have had to use tftp in the past to put firmware on some Linksys router, it is pretty straightforward.

Let me know how it goes, and being able to access the modem to powercycle it would be a plus.

Edit: Here are some specific instructions for Debian/Ubuntu from their Wiki:

> 
Requirements:

    * TFTP If you are on a Debian box, simply typing apt-get install tftp will do the trick.
    * wl500g-clear-nvram.trx
    * wl500g-recover.trx
    * The most recent stable release of DD-WRT from the downloads page. Make sure you use the firmware specifically compiled for the Asus router. Check the readme included with the files, but it should be called something like dd-wrt.v**_asus.trx 


    * Step 1: Connect your computer via ethernet cable to a LAN port on the router (I used LAN port 1)
    * Step 2: Unplug the power cord from the router
    * Step 3: Wait 20 seconds
    * Step 4: Press and hold the reset button on the back of the router. Note that the reset button is recessed and you need a pen or paper clip to press it in. The button protruding from the back is the EZ Setup, which is not what you want to press.
    * Step 5: While holding the reset button, plug the power cord into the router. Continue to hold the reset button until the power light starts flashing. Let go of the reset button
    * Step 6: Use tftp to transfer wl500g-clear-nvram.trx to the router. The commands are as follows: 


user@box:$ tftp 192.168.1.1

> mode binary

> put wl500g-clear-nvram.trx


    * Step 7: Tftp should report a successful file transfer in 7-15 seconds. Wait 2-3 minutes after that before unplugging the router
    * Step 8: Unplug the router, wait 20 seconds. Hold the reset button and plug the power cord into the router, continuing to hold the reset button until the power light flashes. Release the reset button.
    * Step 9: Use tftp to transfer wl500g-recover.trx to the router. Same method as above, just change the file name. Wait 2-3 minutes after tftp reports a successful file transfer before unplugging the router.
    * Step 10: Unplug the router, wait 20 seconds. Hold the reset button and plug the power cord into the router, continuing to hold the reset button until the power light flashes. Release the reset button.
    * Step 11: Use tftp to transfer the DD-WRT firmware to the router. MAKE SURE YOU USE THE CORRECT FILE. It should be be called something like dd-wrt.v**_asus.trx Do not upload a .bin file.
    * Step 12: Wait 2-3 minutes after tftp reports a successful file transfer before unplugging the router. Unplug the power cord from the router, wait 20 seconds, and plug the power cord back into the router. 


The router should now boot to DD-WRT firmware. Go to 192.168.1.1 to confirm. You may need to power cycle your cable modem (if applicable) to get an internet connection.


Notes: You may need to manually specify your computers IP address (in order to use tftp to upload the files) if for some reason DHCP is not working. I did not need to do this, but if you cannot establish a connection to the router try the following settings:

IP address: 192.168.1.10

net mask: 255.255.255.0

router: 192.168.1.1

DNS: 192.168.1.1



As always, be patient and NEVER interupt the transfer of a new firmware image.

---

