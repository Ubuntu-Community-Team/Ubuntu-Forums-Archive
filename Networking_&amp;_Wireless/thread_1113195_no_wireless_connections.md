---
title: "no wireless connections"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by sunnyroy on 2009-04-01
please help

just installed ubuntu on the main home computer.

when i click on the icon to view available wireless networks, there are none there. there is not even a heading Wireless Networks.

I run sudo iwlist scan from the terminal which return the following error

lo    Interface doesent support scanning
eth0  Interface doesent support scanning
pan0  Interface doesent support scanning

again please help

---

### Post by superprash2003 on 2009-04-01
in your terminal type **sudo lshw -C network** and post output

---

### Post by sunnyroy on 2009-04-01
*network:0 UNCLAIMED
    description: Ethernet controller
    product: AR5413 802. 11abg NIC
    vendor Atheros communications
    physical id: 3
    bus infopci@0000:02:03.0
    version: 01
    width: 32 bits
    clock: 33MHz
    capabilities: pm cap-list
    configuration:latency=168 maxlatency=28 mingnt=10
*network: 1
    description: Ethernet interface
    product: 82801G (ICH7 Family) LAN Controller
    vendor: Intel Corperation
    physical id: 8
    bus info: pci@0000:02;08.0
    logical name: eth0
    version: 01
    serial: 00:17:31:c0:17:db
    size: 10MB/s
    width: 32 bits
    clock: 33MHz
    Capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-K4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
*network DISABLED
    description:Ethernet interface
    physical id: 1
    logical name: pan0
    serial: 2e:af:d3:b5:f4:56
    capabilities:ethernet physical
    configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

please respond as i hed to write all that longhand

---

### Post by superprash2003 on 2009-04-02
[http://ubuntuforums.org/showthread.php?t=778726](http://ubuntuforums.org/showthread.php?t=778726)

---

### Post by sunnyroy on 2009-04-06
thanks for all the help, this is now sorted, for anyone who's interested see the following.
get the windows driver from [http://www.downloadatoz.com/driver/download_4858.html](http://www.downloadatoz.com/driver/download_4858.html)

locate the .inf file (its in the ABG folder)

put this folder on your desktop (you may have to adjust your privileges in properties to gain access to this file)

goto the synaptic package manager and get "ndisgtk"

when you have done that go to system>administration>windows wireless drivers

select install new driver, when it asks for the location, select your previously downloaded .inf file.

thanks again

---

### Post by superprash2003 on 2009-04-06
great!!glad you got it to work.. really appreciate you mentioning the steps you followed to get it to work :)

---

