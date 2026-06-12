---
title: "How-to: HSDPA 3G - ZTE MF100 - Ubuntu 9.10 - Vivo"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by Paulo Wageck on 2009-12-19
After taking a lot of time looking at many disperse threads... I looked at a thread for ZTE MF626 that was essential...([http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)). 

This was used to connect a ZTE MF100 in Brasil with the VIVO 3G network.

_Part one (use windows to turn off the usbdrive option_).

1. Connect your ZTE MF100 to the USB port of your computer with hyperterminal on it. The modem will automatically install the appropriate drivers and launch the User Interface (UI).

2. Determine the COM port of the modem by inspecting the modem properties under Modems in the Device Manager (do not get confused with ZTE Dianostics Interface or others).

3. Close the UI and open hyperterminal (or equivalent) and connect to the appropriate COM port using these parameters:

Speed: 115200
Data bits: 8
Parity: None
Stop bits: 1
Flow Control: None

4. Input the following command (you may wish to turn on local echo so you can see what you are typing):

AT+ZCDRUN=8

You should receive the following back in confirmation:

Close autorun state result(0:FAIL 1:SUCCESS):1

5. Close the hyperterminal connection and unplug the modem. Your modem is now reconfigured to be plug and play in Ubuntu.

_Part 2 (Ubuntu)_

6. Connect you modem to your Ubuntu computer. In the NetworkManager Applet you should find the option to create a new mobile broadband connection. Do so with the location and APN appropriate to you ISP.



You should now be able to connect successfully to the internet and your modem should function as a plug and play device in Ubuntu. This works by disabling the self installation and autorun features which would otherwise cause Ubuntu to detect the modem as a CD-ROM. If you wish to revert the modem to it's orginal settings to allow atomatic UI installation on windows PCs the command to do so is: AT+ZCDRUN=9 (administered by hyperterminal as above)


The original thread finishes here... 

[B]What I add now:
[/B]
A[U]fter finishing all the steps I could ping my servers IP address with Terminal but no WWW surfing (the DNS was not working... ). 
[/U]
SO:

Open TERMINAL and type:

***sudo sh /etc/ppp/ip-up***


The ip-up script will correct the DNS for you....


Now open firefox and everything will be fine!!!!!!!!!!!



Cheers

---

### Post by Luciano Pinto on 2009-12-28
Thanks mate! This how-to you've made really worked for me! I was already about to give it up!! And now I'm  using it as I type this!

Cheers!

---

### Post by abalaban on 2009-12-29
I have exactly the same problems - I can connect and ping IP addresses, but I cannot browse.
I tried to run ip-up script, but it did not help.

I have ZTE MF636 under Rogers network here in Canada.

Anything I should try?

Thanks

Alex

---

### Post by Paulo Wageck on 2010-01-14
I am glad it worked for you Luciano. 

I am not sure if it will work with other models...

---

### Post by Amfiprion on 2010-03-15
Many thanks Paulo, it worked for me too, great how-to :D
(used to connect ZTE MF100 in Poland with Netia Mobile network)

---

### Post by produnis on 2010-03-17
> **Paulo Wageck said:**
> 
A_fter finishing all the steps I could ping my servers IP address with Terminal but no WWW surfing (the DNS was not working... ). _
SO:
Open TERMINAL and type:

***sudo sh /etc/ppp/ip-up***


I had the same problem here, using the german "O2-Surfstick" MF100 (see german [manual here]("http://www.produnis.de/blog/?p=1109")).

What worked for me was to look at the  /etc/resolv.conf  , which was empty (!!!).
So I added a nameserver there.
For German O2, it is:
```
sudo vim /etc/resolv.conf
```
> 
nameserver 193.189.244.225
nameserver 193.189.244.206


After saving the file, connection immediatly works

---

### Post by M@N on 2010-11-07
It works with ZTE MF637 as well.

---

### Post by valenajarro on 2011-01-27
On the Windows part, the HyperTerminal procedure did'nt worked for me. But I found a way to send the command **AT+ZCDRUN=8** to the modem by specifying it on the section of special initialization commands on the properties of the modem on the device manager. Then I attempted to connect (Because the command, the connection wasn't established). After the connection attempt I removed it, and then the modem worked fine on Windows. Then I connected it to my Ubuntu 10.04 box, and everything worked just fine!.

---

