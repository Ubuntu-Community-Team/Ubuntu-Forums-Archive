---
title: "Unable to connect using Sony Ericsson PC300 Mobile Broadband"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by HarvMan on 2010-03-01
Hi, am using Ubuntu 9.10 (Karmic) with a PC300 card on Rogers (Canadian) network.
I have little experience with Ubuntu.  How should I proceed to resolve?  Thanks!

lsusb shows:        
              Bus 006 Device 002: ID 0fce:d0b2 Sony Ericsson Mobile Communications AB

The log file shows the following activity:
Mar  1 11:42:37 ubuntu NetworkManager: <info>  Activation (ttyACM0) starting connection 'Rogers PC300'
Mar  1 11:42:37 ubuntu NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 (reason 0)
Mar  1 11:42:37 ubuntu NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  1 11:42:37 ubuntu NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Mar  1 11:42:37 ubuntu NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Mar  1 11:42:37 ubuntu modem-manager: (ttyACM0) opening serial device...
Mar  1 11:42:38 ubuntu modem-manager: Registration state changed: 4
Mar  1 11:42:46 ubuntu modem-manager: get_reg_status_done: unknown response: *EMWI: 1,0#015#012#015#012+CREG: 0,4
Mar  1 11:42:46 ubuntu NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Could not parse the response
Mar  1 11:42:46 ubuntu NetworkManager: <info>  (ttyACM0): device state change: 4 -> 9 (reason 1)
Mar  1 11:42:46 ubuntu NetworkManager: <info>  Marking connection 'Rogers PC300' invalid.
Mar  1 11:42:46 ubuntu NetworkManager: <info>  Activation (ttyACM0) failed.
Mar  1 11:42:46 ubuntu modem-manager: (ttyACM0) closing serial device...
Mar  1 11:42:46 ubuntu NetworkManager: <info>  (ttyACM0): device state change: 9 -> 3 (reason 0)
Mar  1 11:42:46 ubuntu NetworkManager: <info>  (ttyACM0): deactivating device (reason: 0).
Mar  1 11:42:46 ubuntu NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Mar  1 11:42:46 ubuntu NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed

---

### Post by ubunterooster on 2010-03-01
try "ifconfig" in the terminal to see what we are looking at.

---

### Post by HarvMan on 2010-03-01
Here's the results from ifconfig:

user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:b1:13:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

usb0      Link encap:Ethernet  HWaddr 02:80:37:06:03:00  
          inet6 addr: fe80::80:37ff:fe06:300/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:90 (90.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:77:c5:03  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe77:c503/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1718536 (1.7 MB)  TX bytes:454195 (454.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-77-C5-03-37-37-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@ubuntu:~$

---

### Post by ubunterooster on 2010-03-01
open synaptic and search for "ndiswrapper-utils" and "ndisgtk"
(these are tools for setting up ndis based cards [yours is ndis5]) Install those packages.

 Oh, and you do very well at knowing which info is not needed. [username, etc]

---

### Post by HarvMan on 2010-03-01
OK, have installed above packages.  Next step ...

---

### Post by ubunterooster on 2010-03-01
get your driver [yes the windows one] and extract the zip file. there should be a .inf or .INF file there.

---

### Post by HarvMan on 2010-03-01
OK, there are 9 inf files.  Any particular one(s) to focus on?

---

### Post by ubunterooster on 2010-03-01
[After getting Windows drivers]

Go to system>administration>windows wireless drivers. 

select install new driver

[not sure which one]

---

### Post by HarvMan on 2010-03-01
I attached an image to my previous post.

---

### Post by ubunterooster on 2010-03-01
Here it is difficult selecting which one. could you try to paste them?

---

### Post by ubunterooster on 2010-03-01
....the names that is.
We'll try one and, if we are wrong, remove it and try another.
 No big deal

---

### Post by HarvMan on 2010-03-01
I will check which ones are presently installed in Windows XP.

Here are the inf files:

---

### Post by ubunterooster on 2010-03-01
you can go to the first, install it, see if it works. If no, uninstall [System>Administration>Windows Wireless Drivers click on remove driver, and remove the just installed driver] then repeat.




my browser froze when trying to view the screenshot, sorry I'm blind to graphics. [using 'computer' w/ 16MB RAM]

---

### Post by HarvMan on 2010-03-01
I need to step away from the computer for about 1 hour.  Will check the Windows XP install and then try installing those into Ubuntu.  Will let you know the results.

Thanks so much for your help!

---

### Post by HarvMan on 2010-03-01
Reviewed Windows and all of the .inf files are required.
 
Tried to install in Ubuntu, but immediately shows as "Invalid Driver!".

---

### Post by ubunterooster on 2010-03-01
so you went to system>administration>windows wireless drivers, you clicked "Install new driver" navigated to one .inf file and clicked install, and it said "invalid driver" for each one you did this to?

---

### Post by HarvMan on 2010-03-01
That is correct ... however, just to verify, I picked the same .inf again and it then said the driver is already installed???
 
How can I list or report what drivers are installed?

---

### Post by HarvMan on 2010-03-01
Found a command to list ndis drivers:

user@ubuntu:~$ ndiswrapper -l
semb2mdm2 : invalid driver!
sembbus : invalid driver!
sembmdm2 : invalid driver!
sembndis : invalid driver!
sembsdm2 : invalid driver!
sembsmc2 : invalid driver!
sembunic : invalid driver!
sembwwn2 : invalid driver!
sesc : invalid driver!

---

### Post by HarvMan on 2010-03-01
I have found a reference for installing Windows drivers:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading Windows Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading Windows Drivers)
 
Does section 3.3. Downloading Windows Drivers provide any hints on how to proceed?

---

### Post by ubunterooster on 2010-03-01
> **HarvMan said:**
> I have found a reference for installing Windows drivers:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading Windows Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading Windows Drivers)
 
Does section 3.3. Downloading Windows Drivers provide any hints on how to proceed?
not that I see.
 3.1, however looks possible
I finished going through most of my large collection of linux books to find quite little on ndis wrappers.
Nothing was helpful in my library. I'll finish reading some more bookmarked sites on this....

---

### Post by HarvMan on 2010-03-03
I have made some progress installing drivers. :)

All .inf and related .sys files are placed together in a directory.  Started a root terminal and issued the following command for each .inf file: ndiswrapper i <inf file name>.

I then used ndiswrapper to list the drivers.  Of the 9 installed, there are 2 that appear as Invalid! - sembndis, sesc.

I also used Windows Wireless Drivers to view the drivers.  It confirms "Hardware present: Yes" for those that installed properly and shows the 2 that are Invalid!

How should I proceed?  Thanks!

---

### Post by ubunterooster on 2010-03-03
I understand you need to:
1, remove the opensource drivers (ones preinstalled) for the device [not sure where (or which) they are]
2, add ndsiwrapper to programs started at boot


I've found more info that says to buy another device than giving info on using ndiswrapper. I'm frustrated and it's not even my computer.

---

### Post by HarvMan on 2010-03-03
Frustrating for sure ... with reference to the following document:
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide?](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide?)
 
I will review the Blacklisting Existing Drivers procedure and see what can be found.

---

### Post by HarvMan on 2010-03-03
Well, device manager showed cdc_acm.  I blacklisted, restarted but still no improvement.
 
Oh well, we tried ... perhaps there may be improvements in an upcoming release.  For now I'll just have to run the card in Windows XP.
 
Thanks for your help ...
 
Harv

---

### Post by ubunterooster on 2010-03-03
For a last resort: [http://www.linuxant.com](http://www.linuxant.com)
Try the trial of the Driver Loader

---

