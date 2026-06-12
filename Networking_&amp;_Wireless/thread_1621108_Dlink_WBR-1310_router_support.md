---
title: "Dlink WBR-1310 router support??"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by jpmackay on 2010-11-13
I am new in this forum and have trying to get online with the latest program of Ubuntu on my PC laptop. I have no luck with this part. Also search on the list with Hardware Support Components Wireless for** Dlink WBR-1310** router and I don't see any with this router. Guess that your program doesn't support this router. If it is then I guess that I will have to uninstall the program of Ubuntu 10.4 unless someone reply to my message. Anyway all day long I have been trying to get the network connections and no luck with this part. All I got the message that Wired Network disconnected and Wireless Networks disconnected. I did go to " Connect to Hidden Wireless Network " but not sure what is the network name: and password ? I do know the name of the router -- **Dlink WBR-1310** and network name and password for Windows but for this part -- they kept telling me " Wireless network disconnected -- you are offline " That is my biggest struggle with this network trying to connect the wireless router.

Thank you,

John

---

### Post by chili555 on 2010-11-14
It is possible that the reason you can't connect to the router is a configuration issue with the wireless card in your computer. Before you abandon Ubuntu, let's troubleshoot.

When you click the Network Manager icon, do you see your network name? What happens when you click the icon and try to connect? Are you challenged for the password?

---

### Post by jpmackay on 2010-11-14
First of all want to say thank you for your reply. Yes I see your attachment thumbnail to compare mine with yours. OK mine said both **Wired Network disconnected** and **Wireless Network disconnected** and nothing show available in both networks. OK now I think that I got you and myself too much confusing about which wireless am I using? It's my fault anyway. I am using Ubuntu 10.10 on my laptop which is on** Compaq Presario M2105CA** and the wireless is **Broadcom 802.11b/g WLAN ver. 5.10.38.26 **and not sure what is the number like **BCM43xx**?  Hope that will help you with more information about my wireless on my laptop? The main router for our home network is **Dlink WBR-1310** router to connect with 4 laptops and 2 desktops in our house. Only one laptop is using Windows and Ubuntu for now. Also I am very new and just download the program on Friday evening. Look forward to hear more about this problem.

Thank you again,

John

---

### Post by chili555 on 2010-11-14
Broadcom wireless cards generally require firmware which is not included by default because it's proprietary. Let's see what your computer can tell us about that. Please open Applications > Accessories > Terminal and type in:```
dmesg | grep -e wlan -e firmware
```Please post the result.

Is your wired ethernet connection available?

---

### Post by jpmackay on 2010-11-14
Here is the information below that you requested.

johnm@ubuntu:~$ dmesg | grep -elan -e firmware
[     16.880630]  platform radeon_cp.0:[COLOR=Red] firmware[/COLOR]: requesting radeon/R300_cp.bin
[     19.676105]  b43 ssb0:0: [COLOR=Red]firmware[/COLOR]: requesting b43/ucode5.fw
[     19.685258]  b43 ssb0:0: [COLOR=Red]firmware[/COLOR]: requesting b43-open/ucode5.fw
[     19.695588]  b43-phy0 ERROR:  You must go to [http://wireless.internet.kernel.org/en/users/Drivers/b43#device](http://wireless.internet.kernel.org/en/users/Drivers/b43#device)[COLOR=Red]firmware[/COLOR] and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[     19.768112]  b43 ssb0:0: [COLOR=Red]firmware[/COLOR]: requesting b43/ucode5.fw
[     19.770453]  b43 ssb0:0: [COLOR=Red]firmware[/COLOR]: requesting b43-open/ucode5.fw
[     19.775644]  b43-phy0 ERROR:  You must go to [http://wireless.internet.kernel.org/en/users/Drivers/b43#device](http://wireless.internet.kernel.org/en/users/Drivers/b43#device)[COLOR=Red]firmware[/COLOR] and download the correct [COLOR=Red]firmware[/COLOR] for this driver version. Please carefully read all instructions on this website. 
johnm@ubuntu

-----------------------------------------------------------------------------------------------------

Also I do have the wired ethernet connection.  Look forward to have the answer solve about this problem.

Thank you,

John

---

### Post by chili555 on 2010-11-14
There is a handy mechanism to get the firmware installed. Please go to System > Administration > Additional Drivers and see if you can activate your Broadcom. In this instance, 'activate' will mean go out on the internet, find the firmware and install it in the right place.

It may take a reboot, but your wireless should be working.

---

### Post by jpmackay on 2010-11-14
Had no problem to go to System > Administration > but nothing show **Additional Drivers** on the list. Is there something wrong with the folder for **Additional Drivers**. I did look up at your request but don't see any of that word. Sorry!

John

---

### Post by chili555 on 2010-11-14
On older versions of Ubuntu, it's called System > Administration > Hardware/Additional Drivers or maybe System > Administration > Hardware Drivers Do you have that?

---

### Post by jpmackay on 2010-11-14
OK here what I have mine on the laptop with Ubuntu


**System > Administration > Hardware Drivers**

Thank you again,

John

---

### Post by chili555 on 2010-11-14
And did you click it and activate your Broadcom wireless card?

---

### Post by jpmackay on 2010-11-14
Yes I did clicked this as your request and here is the message below:

[B]Downloading package indexes failed, please check 
your network status. Most drivers will not be available.

                                                             [ Close ]
[/B]

Then I click " Close " and here is the other message below:

[B]Hardware Drivers

No proprietary drivers are in use on this system.

                                                             [ Close ][/B]

Thank you again,

John

---

### Post by chili555 on 2010-11-14
> Downloading package indexes failed, please check
your network status. Most drivers will not be available.
This suggests you did not have a network connection at the time. Please hook up the ethernet cable and try again.

---

### Post by jpmackay on 2010-11-14
Yes I can download through Hardware Drivers from the wired network (ethernet) now.

Thank you,

John

---

### Post by jpmackay on 2010-11-14
Now I am on wireless connection and be able to surfing on Firefox on my laptop. Finally it's working now.

Thanks for your patience with me and appreciated this. If I have any more questions about Ubuntu and will come back to post my question here.

Thank you very much

John

---

### Post by chili555 on 2010-11-14
I'm very glad it's working. Have fun!

---

### Post by jpmackay on 2010-11-14
I am having fun with this new program, Ubuntu also enjoying surf on the Internet on this program as well. 

John

---

