---
title: "Help to finally correctly configure my Intel pro/wireless 3945ABG??"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-26
I am a uni student who is learning about networkin. I also work for my fan=mily bussiness that runs a couple of networks.

I am very interested in learning about WEP encryption.

I am in the process of configuring my intel pro/wireless 3945 wireless card to allow packet injection and to use aircrac-ng to learn and test one of my own wep networks.

I used these commands to patch my driver to allow the above.

But something is not quite right.

ie. when i re-start ubuntu my wireless card connects to the internet even though my card should be set to monitoring mode which should not allow me to connect untill i run the 
with this command: 
    sudo iwconfig wlan0 mode manage

and  sudo iwconfig wlan0 mode monitor to allow monitoring mode with no active internet connection
 
I am not sure if I am correctly blacklisting the default  ipwraw driver.

sudo apt-get install build-essential (get core files)

sudo apt-get install libssl-dev (get supporting library)

wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2) (downloads driver)

tar -xjf ipwraw-ng* (extract the archive file)

cd ipwraw-ng (go to the extracted folder)

make (compile the source files into a binary)

sudo make install (install the driver)

sudo make install_ucode

echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

sudo depmod -ae (create a dependency file for the modules)

sudo modprobe -r iwl3945 (unload driver that you do not need)

sudo modprobe ipwraw (load the driver that you installed)

sudo ifconfig wlan0 up (enable the network adapter)

When you're done, open a terminal and type lsmod, you should see the ipwraw driver loaded.


Can somebody help me rectify this and correctly configure my card for  package injection and also possibly give me the correct commands??

cheers in advance

---

### Post by scrypt on 2009-03-26
I had one sucessful session running aircrack-ng with the correct patched driver to allow packet injection.

But as soon as I rebooted I no longer can run it again correctly.

Can someone with knowlege of above help me to sort this out

thank's

---

### Post by dexter1983 on 2010-07-31
I had the same wifi card, the same problem....

---

