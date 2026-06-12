---
title: "Wired network and Auto Eth0"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by canadianwriterman on 2009-03-02
I recently moved and had to connect to a new DSL connection on my Intrepid laptop.

After setting up the connection using the DSL tab on Network Manager, it does not connect automatically when rebooting. Instead Network Manager defaults to "Auto Eth0" which is not connected to the new DSL connection. I set the DSL connection to "Start Automatically," but it doesn't help. Each boot, Auto Etch0 comes up and I have to manually connect to the DSL setting in Network Manager. Any way to get the DSL to connect automatically?

Thanks.

---

### Post by terazen on 2009-03-02
What network manager do you use?

If you are using the NetworkManager Applet you can "Connect Automatically" under the connection properties for DSL or maybe just delete the "Auto Eth0" setting.

---

### Post by canadianwriterman on 2009-03-02
Hi terazen. I am using the default Network Manager and have set the DSL to start automatically. I get a message saying that I can't delete Auto Eth0.

---

### Post by anubhavrocks on 2009-03-02
Check your  ```
/etc/network/interfaces
``` and see if eth0 is configured through that.In case it is enabled you should disable that.

---

### Post by terazen on 2009-03-02
It may be a bug if that's the case.  You should be able to delete whatever you want.  You may want to try another network manager, possibly WICD.

Does this sound like your problem?
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/311158](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/311158)

---

### Post by canadianwriterman on 2009-03-02
Yes, the bug report is the same as my issue and it recurs in my test install of Jaunty, too. I cannot delete Auto eth0.

Oddly, this only happened when I changed DSL accounts. Previously, Auto eth0 picked up the DSL account regardless of what version of Ubuntu or other distro I installed on my machine. Not sure why the old DSL account was picked up through Auto eth0 and the new one can't. Same ISP, just a new account.

---

### Post by canadianwriterman on 2009-03-02
> **anubhavrocks said:**
> Check your  ```
/etc/network/interfaces
``` and see if eth0 is configured through that.In case it is enabled you should disable that.

How do I disable it (other than highlighting it and pressing delete in NM)?

---

### Post by canadianwriterman on 2009-03-03
What is "Auto eth0," why can't it be deleted and why does it override my wired DSL connection at every boot? I now am forced to manually select my wired DSL connection in Network Manager every single time I boot. It's annoying and makes me wonder just what the purpose of "Auto eth0" is.

---

### Post by japsai on 2009-03-03
Do you mean "Auto eth0" in NetworkManager? Can you post more (all) content of your "/etc/network/interfaces"?

---

### Post by kevdog on 2009-03-03
auto eth0

This instructs that this interface if brought up automatically at boot -- its equivalent of sudo ifup eth0

---

### Post by canadianwriterman on 2009-03-03
> **japsai said:**
> Do you mean "Auto eth0" in NetworkManager? Can you post more (all) content of your "/etc/network/interfaces"?

This is all that's in that file:

auto lo
iface lo inet loopback

---

### Post by Iowan on 2009-03-03
Might be beneficial to check the  NM config files: */etc/NetworkManager/nm-system-settings.conf*

---

### Post by divyabdasar on 2011-07-08
Auto etho connection gets established but unable to browse. I am able to ping to my domain too. 

Can anybody tell what would be the problem.

---

### Post by St.Marys HSS Morakkala on 2011-07-08
[

After setting up the connection using the DSL tab on Network Manager, it does not connect automatically when rebooting. Instead Network Manager defaults to "Auto Eth0" which is not connected to the new DSL connection. I set the DSL connection to "Start Automatically," but it doesn't help. Each boot, Auto Etch0 comes up and I have to manually connect to the DSL setting in Network Manager. Any way to get the DSL to connect automatically?

Asus Motherboard P5G41T-MLX3  eubuntu internet connection is no working Auto Eth0 is not active how to connect the internet connection this motherboard

---

### Post by dineshs on 2011-07-08
> Asus Motherboard P5G41T-MLX3 eubuntu internet connection is no working Auto Eth0 is not active how to connect the internet connection this motherboard Open a terminal(applications-accessories-terminal)and post the results of```
sudo lshw -C network
``` ```
route -n
``` and```
cat /etc/network/interfaces
```
Is it a DSL broadband connection?
Do you use windows? If yes, do you use a PPPoE dialler in windows ?
The dialler equivalent in linux is [here]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9")

---

