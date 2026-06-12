---
title: "3G Modem - COMPLETELY and FINALLY SOLVED!!"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by daka on 2010-02-18
I have been struggling for many years with mobile modem connections up to the recent 3G modems and Karmic Distro problems.  FINALLY all is well.  The solution for me has been buying a Huawei E5830 Mifi (wifi) 3G gadget.  It converts the 3G signal to wifi and all is well from there ..... EASY for the first time!!!!  ..... no wvdial, no configuration hardly at all ... just usual wifi settings.  (I left it "always on" with no WEP so my life is finally extremely simple).

Also with the latest version of this E5830 one can install it in Linux, and configure easily, without first installing in a Windows op sys!  Make sure you request a Huawei E5830 that can be "configured wirelessly" so that you can completely avoid windows.

80 euros WELL-SPENT on the HuaweiE5830.  I am sure other Mifi gadgets work well too, but I can only speak personally about this one.

Good Luck
(What a Relief!)

daka

---

### Post by alexfish on 2010-02-18
hi

good to here about this device

But I am curious as to the type of device listing as seen by Linux , IE :the output from the lsusb command from the terminal

Thanks in advance

alexfish

---

### Post by daka on 2010-02-18
Hi Alexfish

Here's the lsusb output ..... (not seen as usb).. but picked up as a wifi source

daka@daka-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
daka@daka-laptop:~$ 

When the unit is turned on it sends a wifi signal to laptop... one then enters an ip address (192.168.1.1) and enters a configuration process, changing the password, selecting "always on" or other modes and choosing WEP or no WEP.   This is SO easy!!   Now I turn on the laptop and it is connected to 3G/WIFI automatically.

Cheers

daka

---

### Post by antoni2 on 2010-02-20
Very interesting indeed.
I was going mad with all this fuss. First, installing usbserial and wvdial (8.04). Then, it cannot be installed because it is already in the kernel (8.10, or 9.04). Then it seems to be again a separate module (9.10 ?). Later, I realize I cannot install wvdial because I have no internet connexion on the target computer (I cannot just download the file with my other laptop and copy it here... Dependencies are too many). Has someone realized that programs essential for internet connexion could (should) be treated in a special way, to cope for the fact that the user in need of them often lacks a direct internet connexion to the computer ?
Well, I think I once solved that by downloading the sources, copying to target box and installing...
So I think this is brilliant idea. Lets forget 'bout USB modems in Ubuntu.  And in Linux, for that matter. Thanks.
BTW, where did you buy the Huawei device ?

---

### Post by pdc on 2010-02-20
here you will find it on ebay australia 

[http://cgi.ebay.com.au/Unlocked-HUAWEI-E5830-MiFi-WiFi-Wireless-Modem-E6939_W0QQitemZ140384660491QQcmdZViewItemQQptZAU_Modems?hash=item20af93ec0b](http://cgi.ebay.com.au/Unlocked-HUAWEI-E5830-MiFi-WiFi-Wireless-Modem-E6939_W0QQitemZ140384660491QQcmdZViewItemQQptZAU_Modems?hash=item20af93ec0b)

but note it is offered from a UK dealer

---

### Post by daka on 2010-02-21
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItemVersion&item=290399228497&view=all&tid=408647682019](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItemVersion&item=290399228497&view=all&tid=408647682019)

This is where I bought it from eBay UK

good luck

---

### Post by Sven6210 on 2010-02-22
I also bought the device and indeed, it works very well. However I am still facing some problems.

1. When changing the SIM (changing the country) I still need a windows machine to change the profile of the device (APN, user name etc. of the new SIM card). I did not fin any way to do it with Ubuntu yet

2. I can't send or receive SMS with this device, even when connecting it through USB with my Ubuntu laptop

Do you have any solutions for the mentioned problems?


** UPDATE 23rd April 2010**
Yesterday I installed the new firmware for my E5830 and now I can change the APN profile trough the web interface.

For more information please see:
[http://ubuntuforums.org/showthread.php?t=1411777](http://ubuntuforums.org/showthread.php?t=1411777)

---

### Post by daka on 2010-02-22
Hi Sven

I had it solved in Ireland.  When I came back to Spain it has been a nightmare.  I am not surprised because Spain is a bit third world when it comes to this advanced or new technology.  I am still struggling to get the Huawei 5830 working in Spain but in Ireland it was fine.  I will need to phone tech support people and deal with their limited understanding of these issues.

I would apprecite knowing what you do to do reconfigure the modem precisely for new countries... maybe this will help me get it working in Spain.  I have a windows machine too but can't get it working on that either.

Thanks

daka

---

### Post by Sven6210 on 2010-02-23
[COLOR=black][FONT=Verdana]Hi Daka,[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I only know how to change the settings for the new SIM with a Windows computer. You need to connect the E5830 device by USB with the Windows computer and then you run the &#8216;3 WiFi Manager&#8217;, the tool which is on the USB drive of the E5830 and where you can do all the settings.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Then you click on &#8216;Tools&#8217; and &#8216;Options&#8217; and you choose &#8216;Profile Management&#8217;.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]For adding a new profile click on &#8216;New&#8217; and you get a screen where you are required to enter:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]Profile Name[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]ANP (Dynamic/Static and APN)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]Dial-up number[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]User Name[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]Password[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Profile Name: you choose any profile name, e.g. SIM Spain or Vodafone UK or Telefonica Spain etc.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]ANP: for all my SIM cards I had to choose &#8216;Static&#8217; and the APN you need to enter is defined by your SIM card. I found out about the setting when connecting the SIM in the original modem with a windows machine and looking up in the profile settings. Attention, having the wrong APN could result in higher costs (at least in Germany). The APN could be a text such as &#8216;internet&#8217; or &#8216;web.vodafone.de&#8217; etc.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Dial-up number: Usually *99#[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]User Name and Password: whether you need one depends on the operator, in order to find out look in the internet or connect the SIM with the original device to a Windows machine and look it up in the profile settings. Alternatively you can also call the operator in order to ask for the details.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I hope this helps you.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I would like to make all these settings from my Ubuntu &#8211; unfortunately I did not yet find a way to do so.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Best regards[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Sven


** UPDATE 23rd April**
Attention, with the new firmware it is possible to change the APN profile trough the web interface. I do not need a Windows machine any more.
[/FONT][/COLOR]

---

### Post by bmuluu on 2010-02-23
After struggling for ages with Huawei's E220, I picked up the E160E which is a simple plug and play. No hardware configuration required.

---

### Post by GeorgeVita on 2010-02-23
Hi to all above! I would like to add a 'note':
This 'MiFi' is not a 3G modem but a WiFi router with a Mobile Broadband 'Gateway'. As the 3G modem is controlled by its firmware you do not have any problem.

Some problems still exist when you are trying to use the USB interface. If you can find a WiFi alternative (as the 'web interface' on normal WiFi routers) your problem could be solved. Read careful product's manual or post a question at forum.huawei.com about this 'alternative way to set-up E5830'.

Regards,
George

P.S. also this device will not need [capacitors]("http://forum.huawei.com/jive4/thread.jspa?threadID=323666") as it uses a real battery!

---

### Post by Sven6210 on 2010-03-29
Hi GeorgeVita,

indeed, it is a router with WiFi and 3G connection. I can access the firmware through a web-interface and change many settings through the web interface itself. However the web interface does not allow the following changes:

1. Change of the 3G profile (e.g. APN name, user name, password, dial-in number etc.)
2. Can not send or receive SMS

I do travel a lot and I often change the SIM of my 3G modem (MiFi router), e.g. Chinese SIM, German SIM, Austrian SIM. Currently I always need a Windows machine when I change the SIM because only under Windows I can use the provided software in order to change the profile.

Furthermore my German SIM is a prepaid SIM and I need to activate my daily flatrate or my monthly 5GB package with an SMS. Only after I have received the network operators SMS and i confirmed it once more I can use the 3G. Therefore sending and receiving SMS is also essential to me. The web-interface does not allow to send and read SMS and therefore I either need to put the SIM in a mobile phone or I need a Windows machine to send and receive SMS.

So far the E5830 has two major disadvantages - even though it is a great piece of hardware. I would so much like to use it with my Ubuntu. This is actually the last burden why my main Laptop is still running with Windows and why I only use Ubuntu on my EeePC.

**UPDATE 23rd April 2010**
With the latest firmware it is possible to change the APN profile through the web interface. No need for a Windows machine any more

---

### Post by hipocrita20 on 2010-07-13
> **Sven6210 said:**
> [COLOR=black][FONT=Verdana]Hi Daka,[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I only know how to change the settings for the new SIM with a Windows computer. You need to connect the E5830 device by USB with the Windows computer and then you run the ‘3 WiFi Manager’, the tool which is on the USB drive of the E5830 and where you can do all the settings.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Then you click on ‘Tools’ and ‘Options’ and you choose ‘Profile Management’.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]For adding a new profile click on ‘New’ and you get a screen where you are required to enter:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]Profile Name[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]ANP (Dynamic/Static and APN)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]Dial-up number[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]User Name[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-       [/FONT][/COLOR][COLOR=black][FONT=Verdana]Password[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Profile Name: you choose any profile name, e.g. SIM Spain or Vodafone UK or Telefonica Spain etc.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]ANP: for all my SIM cards I had to choose ‘Static’ and the APN you need to enter is defined by your SIM card. I found out about the setting when connecting the SIM in the original modem with a windows machine and looking up in the profile settings. Attention, having the wrong APN could result in higher costs (at least in Germany). The APN could be a text such as ‘internet’ or ‘web.vodafone.de’ etc.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Dial-up number: Usually *99#[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]User Name and Password: whether you need one depends on the operator, in order to find out look in the internet or connect the SIM with the original device to a Windows machine and look it up in the profile settings. Alternatively you can also call the operator in order to ask for the details.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I hope this helps you.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I would like to make all these settings from my Ubuntu – unfortunately I did not yet find a way to do so.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Best regards[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Sven


** UPDATE 23rd April**
Attention, with the new firmware it is possible to change the APN profile trough the web interface. I do not need a Windows machine any more.
[/FONT][/COLOR]


 many..many thanks sven! your solution works great for me !

---

### Post by hazrpg on 2012-11-06
I'm not sure if its worth bringing this thread back from the grave, but for me I can access SMS from my interface, and thought I'd share how (since it is not where you'd expect).

> **Sven6210 said:**
> 
2. Can not send or receive SMS


You can indeed access the SMS features from within your router Huawei E5830. It's actually quite simple:

**Please Note: Warning! Your mileage may vary! Things in bold represent items you *may* need to change yourself. These however were the default values for mine (and should be the default for yours unless you changed them). Just because it worked for me, doesn't mean it will for you - factors such as carrier branded equipment might have these features removed. However I have noticed this feature is hidden even on non-branded devices.**


[LIST=1]
[*]Open your web interface: http://**192.168.1.1**/
[*]Login with your details; Username: **Admin**; Password: **password**. May be case sensitive.
[*]Once logged in, access this page: http://**192.168.1.1**/**en**/sms.asp
[/LIST]
The reason I have "en" in bold, is because it may differ if your device is in a different language. All I did was change "content.asp" to "sms.asp" from the URL. So please look at the URL carefully.

Hope this helps some of you out! I know it helped me greatly when I found it!

I shall attach an image to show you what the result is once you've done it (again branding may vary what you see!).

---

### Post by wildmanne39 on 2012-11-06
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

