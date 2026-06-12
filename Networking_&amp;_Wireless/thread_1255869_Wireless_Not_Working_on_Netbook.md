---
title: "Wireless Not Working on Netbook"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by CandlJack on 2009-09-02
Hi, 

I got a Dell Mini 9 Netbook with Windows XP on it and had a ton of problems. I won't get into a long wall of text about all the problems since they're probably irrelevant now that I've installed Ubuntu on it, but I'm still unable to use the wireless adapter to connect to my router. I'm somewhat new to linux, though not COMPLETELY new. 

The first thing I'd like to point out is that my wireless router is right next to the netbook, and I also have other devices connecting to it just fine. This is what leads me to believe this is a software problem on the netbook.  

I started to follow the troubleshooting steps [here]("https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html"). 

The very first step says: "Many wireless network devices can be turned on or off. Check to see if there is a hardware switch, some devices can be switched off from Windows and may need to be turned back on from Windows." 

There is no physical on/off switch, but the Fn-2 key I believe is supposed to turn it off and on ([keyboard image]("http://img8.imageshack.us/img8/6751/keyboard1w.jpg")) I get no response from hitting this key. 


Under the "Check for device recognition" section I followed the steps it said, and I do see both the wired connection and wireless connection, as well as a bluetooth device which is disabled. The bluetooth device does say DISABLED, as the page says it should, but neither the wired nor wireless say any of the states they list (CLAIMED, UNCLAIMED, ENABLED or DISABLED). 

The section with the heading "Check for a connection to the router", I entered the command and the result for the wireless device was this: 
eth1 IEEE802.11 Nickname:"" Access Point: Not-Associated Link Quality: 5 Signal Level: 0 Noise Level: 0 Rx invalid nwid: 0 invalid crypt:0 invalid misc:0 
I'm not sure what most of this means but the whole Not-Associated thing looks pretty wrong. 

The "Check IP assignment" section: 
I see an IP address listed for the wired as "inet addr:192.168.1.101". I see none for the wireless. 

I skipped the "Check DNS" section since there was no IP address. Under the "IPv6 Not Supported", I tried to edit the file using the given command "gksudo gedit /etc/modprobe.d/aliases", but no such file exists.

---

### Post by Vakman on 2009-09-02
The section that reads "Using Windows Wireless Drivers". Have you attempted this. This is usually a great option and is unlikely to fail you. If it does not post back here.

---

### Post by CandlJack on 2009-09-02
Oh yeah. I got to the "Choose the location of your Windows .inf file and click Install." part, but I don't know what this file is or where I would find it.

---

### Post by mjhendricks on 2009-09-02
...Similar issues following the Wireless Troubleshooter as CandlJack...

Ran the process thru "Using Windows Wireless Drivers"

```
sudo lshw -C network
```[FONT=Verdana] went from "DISABLED" before trying NDISWrapper, to what is shown below...Note that CLAIMED, UNCLAIMED, ENABLED or DISABLED is not present, and the "Logical Name" section is completely missing...[/FONT]


```
  *-network
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
```---Assuming that NDISWrapper is going to alter the results of ```
sudo lshw -C network
```...I proceed to the next step---  Kind of an irritant to noobs like me if it is SUPPOSED TO change this, and no one tells us...

```
iwconfig
``` provides

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```I was able to locate a Windows driver package with two .inf files...  netathw.inf and netathwx.inf
  The first installs rather quickly, and NDISWrapper responds with "Unable to see if hardware is present."  NOW AT THE POINT OF CHASING MY TAIL

  The second just sits and stares at me...45 minutes and counting...Forced quit and restart, NDISWrapper pops with "Unable to see if hardware is present" and then tells me that "Hardware Present: Yes" --Except that I'm still chasing my tail.

...If someone suggests "look for drivers," I'm going to scream...Good friggin' luck..at least 8 hours scouring the web through endless loops.  If someone has a recently verifiable link (as in actually accessible and proven to work), I'd be eternally grateful...


HP G60-230US Laptop

---

### Post by CandlJack on 2009-09-08
Hey,  Just wanted to bump this thread as it has been six days idle. My main question now is how do I find or create the Windows.inf file. I found [this link]("http://www.microsoft.com/whdc/archive/w2inf.mspx") but it seems somewhat over my head O_o. Am I supposed to create an inf file from scratch or is there one that is already made that goes with the drivers I want? If the latter, how do I know where to get it?

---

