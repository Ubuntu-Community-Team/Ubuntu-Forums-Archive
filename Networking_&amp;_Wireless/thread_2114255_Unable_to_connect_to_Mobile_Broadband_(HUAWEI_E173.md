---
title: "Unable to connect to Mobile Broadband (HUAWEI E173) under Ubuntu 12.10"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by firethunderstorm on 2013-02-09
Hi everybody,

since I have updated from Ubuntu 12.04 LTS to 12.10 I am unable to connect to UMTS with my USB Surfstick "HUAWEI Mobile Broadband E173". It uses Vodafone (ProSieben) WebSession.

After plugging the surfstick into the USB slot I am asked to fill in the PIN. That works fine and it is being displayed "Connected to GSM". After clicking on "Vodafone (Websession)" in the menu of network (network icon in the bar at the top) it tries to connect and finally displays "Modem connection: Connection disconnected - You are now offline".

Kind regards,
firethunderstorm

---

### Post by firethunderstorm on 2013-02-12
There is a problem with the new version of ModemManager for Ubuntu 12.10. Thus, the solution for this problem for me was the following:

* uninstall new version of ModemManager
* install old version of ModemManager for Ubuntu 12.04 from [here]("http://packages.ubuntu.com/precise/modemmanager")
* apt-pin ModemManager (have a look [here]("https://help.ubuntu.com/community/PinningHowto")), otherwise it will be overwritten with the new version of ModemManager at the next update
* restart your system

---

### Post by dmsousa on 2013-05-29
> **firethunderstorm said:**
> There is a problem with the new version of ModemManager for Ubuntu 12.10. Thus, the solution for this problem for me was the following:

* uninstall new version of ModemManager
* install old version of ModemManager for Ubuntu 12.04 from [here]("http://packages.ubuntu.com/precise/modemmanager")
* apt-pin ModemManager (have a look [here]("https://help.ubuntu.com/community/PinningHowto")), otherwise it will be overwritten with the new version of ModemManager at the next update
* restart your system

Hi,

I'm very new to Linux and of course Ubuntu.
How can I do the steps you recomend?

Thanks in advance

dmsousa

---

