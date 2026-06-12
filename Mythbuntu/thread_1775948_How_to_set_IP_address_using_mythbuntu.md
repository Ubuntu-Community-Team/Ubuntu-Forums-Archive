---
title: "How to set IP address using mythbuntu?"
date: 2011-06-05
forum: Mythbuntu
---

### Post by nhtrader on 2011-06-05
MythTV v0.24.1-9
ubuntu 10.10 (32bit)
xfce 4.8.0

I had a new problem arise this week that had me stumped for a few hours. But I was able to solve it and thought I'd post it.

PROBLEM: MythTV wouldn't start b/c it could not connect to the user defined local home network IP address (ie:10.10.10.12).

Conditions: 
1. MythTV fails. Myth displays the configuration page to reset parameters.
2. I could use any web browser and access the internet. This confirms a lot of things such as verifying hardware works (network card, router/configuration, cables, connections...) and ISP service/connection.
3. I pinged 10.10.10.12 using terminal mode command ping 10.10.10.12<E>

Two outcomes are possible: success or failure. But be mindful of the fact that MythTV failed.

Ping Failure - The error message was "Destination Host Unreachable". 
I checked MythBox's current IP address using the following command:
ifconfig<E>
response: eth0 = 10.10.10.20

This is the wrong IP address. I must find a way to change it to 10.10.10.12.


(NOTE: for most users the network interface for a desktop should be eth0. 
However, this may differ if you have a non-standard desktop configuration
that contains multiple network cards or if your Mythbox uses a wireless network connection.
Substitute eth0 is these instructions with whatever your system uses as the primary network device: eth1, wlan0, ...)


Second outcome: Ping is Successful, but remember MythTV fails.
This problem may occur when another PC on your home network is using your Mythbox's user defined IP address b/c it was reassigned while your Mythbox was turned off. In this scenario, the ping will be successful b/c another PC was assigned your Mythbox's IP address - the address exists, but Myth fails b/c the Frontend can't find the Backend on the other PC and the result is that you are shown the configuration page.

You need to find a way to take that IP address away from the other PC and get that IP address reassigned to your MythBox.



SOLUTION: Change Mythbox from dynamically assigned IP address to statically assigned IP address.
(if you determined that another PC on your home network has been assigned Myth's IP address; turn that PC off before proceeding)

1. Enter Terminal mode
2. enter command: sudo su <E>
3. Now edit a file:
3a. enter command: pico /etc/network/interfaces <E>
3b. Append the existing file by entering the following lines: 

auto eth0               (remember to specify your primary network device: eth0, eth0, wlan0...)
iface eth0 inet static  (remember to specify your primary network device: eth0, eth0, wlan0...)
address 10.10.10.12     (use your user defined IP address as specified on Myth's Frontend Database Configuration page 1 for hostname)
gateway 10.10.10.1      (use your home router's IP address)
netmask 255.255.255.0   (this applies to 99% of all users)

exit/save changes to file (press CTRL+x then "y" to confirm save)

reboot Mythbox

After reboot, verify Mythbox's new IP address.
enter terminal mode
enter sudo su <E>
enter ifconfig <E>
Check IP address. If this didn't work, post a new thread on this forum for help.



Lastly, as an alternative you could of course opt to simply change MythTV's hostname to the new IP address in both the Frontend and in the Backend, which means that you must continually make these changes whenever your MythBox's IP address changes. These instructions help you to avoid these future changes.

---

