---
title: "Problem in Network Manager - WiFi card disabled"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by hotshot05 on 2010-07-11
I am using [COLOR=green]Linux Mint 9[/COLOR] Gnome : Isadora (*since the same Network Manager applet is used in Ubuntu, I am asking the question here too*)
 
I was trying to configure my wireless card to connect my PPPoE  connection by using the command **pppoeconf wlan0** and also **pppoeconf**  
I was not able to dial my PPPoE connection when connected via Wi-Fi. 
When I restarted my system, **in the Network Manager, under Wireless  Networks it says "Device not managed"**. Now I am not able to use my  Wi-Fi card at all and cant connect to my Wi-Fi modem.
 
Can anyone suggest how to repair my system so that I can use my Wireless  card again
 
 
 **Note 1:** There is no hardware Wi-Fi switch, only the key combination **Fn+F2** to enable or disable the wireless card. I have used the key combination  Fn+F2 (which enables or disables the Wi-Fi card) many a times, but the  same thing is displayed in the network manager.
**If I use LiveCD mode and use any distro even Isadora, the Wi-Fi works fine.**
 
 **Note 2:**  My ethernet connection is working fine. I can connect to the internet if  I connect my modem using Ethernet port.

---

### Post by hotshot05 on 2010-07-11
Solved my problem. Found my solution in another thread here. Just cant find that thread again. 

**Step 1 :** Go to the Terminal ( Applications->Accessories->Terminal ) and type **sudo gedit /etc/NetworkManager/nm-system-settings.conf**
**Step 2 :** A window would now popup displaying the contents of the nm-system-settings.conf file
**Step 3 :** Now Change **"managed=false"** to **"managed=true"**
**Step 4 :** **Save the file** and close the window
**Step 5 :** Now back in the terminal type sudo killall nm-system-settings
**Step 6 :** Thats it, your network interface should now be detected and it should attempt to connect to a network.

**Note:** Step 5 did not work for me as I got an error "process nm-system-settings not found". So I just *restarted my system* and my Wi-Fi is working fine again.

---

