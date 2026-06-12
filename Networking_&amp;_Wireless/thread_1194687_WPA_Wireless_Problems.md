---
title: "WPA Wireless Problems"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by NapalmScorpion on 2009-06-22
Quick Question. I am running Ubuntu 9.04, and I'm trying to connect to a WPA wireless network. Any unsecured networks I can connect to, so I know the hardware is installed. 
This is where things get weird. I can click on, or highlight any netword that isn't WPA. But my own network that is WPA securred is greyed in, and I cannot even click on it to get to a screen to enter a password. I've looked on the forums and have yet to see a post that has this same problem.

Again, all networks but WPA protected can be clicked on, and accessed. I can see the WPA networks, but they are greyed in, and I cannot interact with them.... :(

Thanks for the help!

---

### Post by xtjacob on 2009-06-22
What kind of card do you have and can you post the output of lsusb and lspci?

---

### Post by prshah on 2009-06-23
> **NapalmScorpion said:**
> But my own network that is WPA securred is greyed in, and I cannot even click on it to get to a screen to enter a password. 

Try connecting from the commandline to check for problems; the output can give us a clue.

Open a terminal (Applications-Accessories-Terminal) and give the commands```
sudo wpa_passphrase **YOUR_SSID YOUR_WPA_KEY** > /root/wpakey.conf
sudo wpa_supplicant -Dwext -i**wlan0** -c/root/wpakey.conf
sleep 10
sudo dhclient **wlan0**
```

Replace the parts in bold with that specific to your setup. (Eg, your wireless lan maybe called ath0, or wifi0, or eth4, or so on; check with the command iwconfig)

Post back the results (fudge security information) for more troubleshooting.

---

