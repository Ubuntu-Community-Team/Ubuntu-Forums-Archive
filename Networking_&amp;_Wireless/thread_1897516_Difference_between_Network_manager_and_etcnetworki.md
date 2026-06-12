---
title: "Difference between Network manager and /etc/network/interfaces"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by arulnambi on 2011-12-19
HI All
  I am confused with the network settings for ubuntu.  There are two places in Ubuntu where you can change network settings.
  1)    1)  Through gui Network Manager
  2)     2)Through /etc/network/interfaces
  If I make a change in one, it’s not reflected in other, so I assume they are not interlinked. Which leads to the following question?
  1)      1) What is the difference between using the GUI to configure your network settings and specifying them manually in /etc/network/interfaces to configure your network? 
  2)      2) What is the recommended approach for Ubuntu desktop? 
  3)      3) What happens if you use both?
  4)      4) Which one does the system gives importance to?(Which one is given priority)
  

Sorry if the questions seems to be repetitive.

Thanks a lot in advance for taking your time to got through the tutorial.
  With regards
  Arul

---

### Post by praseodym on 2011-12-19
Hi,

you should only use one of that, manual configuration in the "interfaces" or with the NM-applet. But you can configure in the "interfaces", too ("classic Linux config") _and_ use the applet. In this case you need to change "false" to "true" in the file **/etc/NetworkManager/NetworkManager.conf**. Until 11.04 it was in the file **/etc/NetworkManager/nm-system-settings.conf**. Dont remove the two lines with "lo" in the **/etc/network/interfaces**!

---

### Post by 2F4U on 2011-12-19
These two networking options are distinct and thats why changing one is not reflected in the other. Networkmanager can handle much more situations and can also be configured through profiles. For example, you could have two wireless profiles, one for work and the other for home. Networkmanager lets you select one or the other without additional configuration. To achieve the same with /etc/network/interfaces, you would have to manually edit the config files each time you want to switch.

---

### Post by arulnambi on 2011-12-20
> **praseodym said:**
> Hi,

you should only use one of that, manual configuration in the "interfaces" or with the NM-applet. But you can configure in the "interfaces", too ("classic Linux config") _and_ use the applet. In this case you need to change "false" to "true" in the file **/etc/NetworkManager/NetworkManager.conf**. Until 11.04 it was in the file **/etc/NetworkManager/nm-system-settings.conf**. Dont remove the two lines with "lo" in the **/etc/network/interfaces**!
 
Hi praseodym,
Thanks for your response. 
If i set the 
[ifupdown]
managed=true.
Then i can add the settings in both the file, am i right? If i am. Then which one will be given priority. 
If this is still set to false and if i have the entries in both the file then which one will be given priority?
Thanks once gain for taking your time to reply for my response.

With regards
Arul

---

### Post by arulnambi on 2011-12-20
> **2F4U said:**
> These two networking options are distinct and thats why changing one is not reflected in the other. Networkmanager can handle much more situations and can also be configured through profiles. For example, you could have two wireless profiles, one for work and the other for home. Networkmanager lets you select one or the other without additional configuration. To achieve the same with /etc/network/interfaces, you would have to manually edit the config files each time you want to switch.

Hi,
Thanks for your input, can you tell me which one will be given priority if i have entries in both of them?
with regards
Arul

---

### Post by praseodym on 2011-12-20
On boot-up its the "interfaces", on login the NM. This can disturb each other. If you want to use wake-on-LAN the interfaces-way is recommended

---

### Post by arulnambi on 2011-12-20
> **praseodym said:**
> On boot-up its the "interfaces", on login the NM. This can disturb each other. If you want to use wake-on-LAN the interfaces-way is recommended
Hi
Thanks for your quick response. 

Is there a way in which i can disable NM or the other all to gather, so that it will not disturb one another?

Or is there any way or procedure by which i can make sure that one does not disturb the other?

One last confirmation
if 
[ifupdown]
managed=false

This will make sure that only the setting is read from only one file, the "interfaces" and will ignore NM. Am i right?

With regards
Arul

---

### Post by praseodym on 2011-12-20
"false":

/etc/network/interfaces starts the interfaces configured there during booting. If nothing is configured there, no internet connection. If you login the NM takes over, but manual config can disturb, and is ignored

"true":

/etc/network/interfaces starts the interfaces configured there during booting. If nothing is configured there, no internet connection. If you login the NM takes over, but manual config is used, too, and is not ignored.

The alternate network-manager "Wicd" handles both without additional config-files reading "true", "false", whatever

---

### Post by arulnambi on 2011-12-20
> **praseodym said:**
> "false":

/etc/network/interfaces starts the interfaces configured there during booting. If nothing is configured there, no internet connection. If you login the NM takes over, but manual config can disturb, and is ignored

"true":

/etc/network/interfaces starts the interfaces configured there during booting. If nothing is configured there, no internet connection. If you login the NM takes over, but manual config is used, too, and is not ignored.

The alternate network-manager "Wicd" handles both without additional config-files reading "true", "false", whatever
Thank you for your response with regards
Arul

---

### Post by arulnambi on 2011-12-28
> **praseodym said:**
> "false":

/etc/network/interfaces starts the interfaces configured there during booting. If nothing is configured there, no internet connection. If you login the NM takes over, but manual config can disturb, and is ignored

"true":

/etc/network/interfaces starts the interfaces configured there during booting. If nothing is configured there, no internet connection. If you login the NM takes over, but manual config is used, too, and is not ignored.

The alternate network-manager "Wicd" handles both without additional config-files reading "true", "false", whatever
Hi praseodym,
  I have a question, I set different ip address in interface file and in the NM. I have open ssh and tomcat installed in the system. I tried logging in the ssh by starting the system and not logging in. But I was unable to log in, using the ip address i have in the INterface file. I was only able to login with the ip address i have mentioned in the GUI.
I thought until i login the entries in the interface file will be given priority.
Can you please explain?
with regards
Arul

---

### Post by praseodym on 2011-12-28
Is it an address from the same pool (netmask, gateway, broadcast)?

---

### Post by arulnambi on 2011-12-28
> **praseodym said:**
> Is it an address from the same pool (netmask, gateway, broadcast)?
Hi
yes they are of same pool
The entries in both the files are as follows.
/etc/network/interface
auto eth7
iface eth0 inet static
address 192.168.128.3
netmask 255.255.255.0
gateway 192.168.128.2
NM
Address : 192.168.128.4
netmask:255.255.255.o
gateway: 192.168.128.2
With regards
Arul

---

### Post by praseodym on 2011-12-28
> netmask:255.255.255.[COLOR="Red"]o[/COLOR]
Is it a typo? Looks like a small Oh instead of zero..

---

### Post by arulnambi on 2011-12-28
> **praseodym said:**
> Is it a typo? Looks like a small Oh instead of zero..
Hi 
Yes its a typo  :)[in the system i have entered the right value, it is a typo when i entered it here.]
With regards
Arul

---

### Post by praseodym on 2011-12-28
> **arulnambi said:**
> Hi 
Yes its a typo  :)[in the system i have entered the right value, it is a typo when i entered it here.]
With regards
Arul

Another typo here or there?

```
auto eth[COLOR="Red"]7[/COLOR]
```
shouldnt it be eth0???

---

### Post by arulnambi on 2011-12-28
> **praseodym said:**
> Another typo here or there?

```
auto eth[COLOR=Red]7[/COLOR]
```shouldnt it be eth0???
  I get the eth7 when i run ifconfig. 
so this is not a typo. We are suppose to get the value from the ifconfig right?

---

### Post by praseodym on 2011-12-28
Ok, so this is the typo then:

> iface eth[COLOR="Red"]0[/COLOR] inet static
It should be eth7, too.

---

### Post by arulnambi on 2011-12-28
> **praseodym said:**
> Ok, so this is the typo then:


It should be eth7, too.
HI
Thanks a lot, now it does not matter if i have logged in or not. My system always uses the information from the interface file and ignores the NM GUI.
FYI- i have entered the setting in the IPV4 tab in the Manual Method.
Thanks once again for your quick responses.
with regards
Arul

---

