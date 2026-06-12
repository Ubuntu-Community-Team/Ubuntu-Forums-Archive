---
title: "WiFi stopped working entirely (Intel 5300 AGN)"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by Graxer on 2010-10-11
Since I originally started using Ubuntu (10.04) I have had problems with my wireless card. Now I have updated to 10.10 and it has stopped working entirely. 

I am using a "Dell Vostro 1520" with an "Intel(R) WiFi Link 5300 AGN" wireless card.

Here are the details:

**10.04**

In this distribution version, if I had the wireless switch on my laptop activated at startup my wireless card would refuse to activate. There is a light to show when it is activated and this was off, but I checked anyway and wireless capabilities don't work when it is in this state. It didn't even resolve the problem when I switched it off and on again (although this caused the wireless indicator to blink on for less than a second when switched on). 

This was manageable because I found two workarounds:

1. Wait until my laptop had logged into Ubuntu, then activate the wireless card which would start and work as it should.

2. If I had already logged into Ubuntu I could put my computer on standby, switch off the card, come out of standby and reactivate the card while Ubuntu was running.

As I said, this was completely manageable, and I got used to it.

[B]
10.10[/B]

Now that I have upgraded to 10.10 all workarounds fail, I can't use a wireless connection in Ubuntu, as my card won't activate, I cant even get the light to blink as I could before. The only way I can use WiFi is by switching to Windows. :(

Please could someone help, as I tend to use Ubuntu for my university programming work.

---

### Post by chili555 on 2010-10-11
Please boot into Ubuntu with the wireless switch on. Open a terminal and do:```
sudo rmmod -f dell-laptop
```The module *dell-laptop* has been problematical for some time. I am not sure it's the issue in 10.10; I do have one laptop converted (successfully!) to 10.10, but it's not a Dell.

If it works correctly, you can blacklist the module permanently:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Proofread carefully before you press 'Enter.'

Please post back so the searchers will learn the outcome.

---

### Post by Graxer on 2010-10-11
Thank you so much! I am not currently within range of a WiFi network, but that has allowed me to switch the WiFi light on and off with the switch like I should be able to. If I have any further problems I will say, but it appears that the problem has been solved.

Thanks again! :P

---

### Post by Jim_in_Omaha on 2010-10-13
> **chili555 said:**
> Please boot into Ubuntu with the wireless switch on. Open a terminal and do:```
sudo rmmod -f dell-laptop
```The module *dell-laptop* has been problematical for some time. I am not sure it's the issue in 10.10; I do have one laptop converted (successfully!) to 10.10, but it's not a Dell.

If it works correctly, you can blacklist the module permanently:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Proofread carefully before you press 'Enter.'

Please post back so the searchers will learn the outcome.

This fixed my problem getting the BCM4312 on my Dell 11z. It would fail when trying to install/enable the restricted drivers for the BM43. Simply adding 'blacklist dell-laptop' to the end of the blacklist.conf file worked in my case.

---

### Post by coldbluesteel on 2010-10-14
Is there a fix for the Lenovo T61 running the Intel 4965AG wifi?

I'm still having this issue.

---

### Post by chili555 on 2010-10-14
> **coldbluesteel said:**
> Is there a fix for the Lenovo T61 running the Intel 4965AG wifi?

I'm still having this issue.Since this thread refers to *dell-laptop*, please start a new thread. Include the results of these terminal commands:```
rfkill list all
dmesg | grep iwl
```PM me if I don't catch it quickly.

---

### Post by thiagocolebrusco on 2011-02-23
> **chili555 said:**
> Please boot into Ubuntu with the wireless switch on. Open a terminal and do:```
sudo rmmod -f dell-laptop
```The module *dell-laptop* has been problematical for some time. I am not sure it's the issue in 10.10; I do have one laptop converted (successfully!) to 10.10, but it's not a Dell.

If it works correctly, you can blacklist the module permanently:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Proofread carefully before you press 'Enter.'

Please post back so the searchers will learn the outcome.

Thank you very much for this message.

This helped me to solve my problem too.

---

### Post by candinux on 2011-07-01
I am using Dell vostro 1320. I followed the instructions given in this thread for my Ubuntu 11.04 but it din't worked for me.. Let me know if I have done something wrong and/or if you need any particular information about the system/driver etc.

---

### Post by chili555 on 2011-07-01
> **candinux said:**
> I am using Dell vostro 1320. I followed the instructions given in this thread for my Ubuntu 11.04 but it din't worked for me.. Let me know if I have done something wrong and/or if you need any particular information about the system/driver etc.Please post:```
dmesg | grep iwl
cat /etc/modprobe.d/blacklist.conf | grep dell
lsmod | grep dell
rfkill list all
```Thanks.

---

