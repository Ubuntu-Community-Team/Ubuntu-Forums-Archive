---
title: "Wireless WPA2 network won't connect."
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by mpthrapp on 2011-03-29
I am VERY new to Linux in general so please dumb this down as much as possible :P
I just installed Ubuntu on my desktop a few days ago and have spent most of that time attempting to find a fix for my problem, but have not yet found anything.
 
As the title says, I can connect to the neighbor's wireless but cannot connect to my home network. The only difference between them, as far as I know, is that mine is secured with WPA2 encryption.
 
I'll give as much information as I can, but if more is needed, just tell me what/how :)

The chipset is Ralink RT2500USB, It's an external wireless card made by Linksys.
I get "no scan results" from an $iwlist scan.
I'm using 2.6.35-22-generic kernel on a 64 bit system. It's a custom build.
 
Any help that you can offer would be much appriciated :)

---

### Post by Razorback on 2011-03-29
What does iwconfig yield?  Are you using network connections to setup your connection?  I think you made need wpasupplicant in the repositories.  Was your friend's network WEP encryption?

---

### Post by mpthrapp on 2011-03-29
wlan0 
IEEE 805.11bg ESSID:"OhCrapp"
Mode:Managed Frequency:2.412GHz Access Point: 94:44:52:87:6B:C1
Bit Rate=1 MB/s Tx-Power=16dBm
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: on
Link Quality=70/70 Signal level=-36dBm
 
Then the rest of the values are all 0, I can type them out if needed.
 
I am using network manager to set up connections.
 
The other network is unsecured.

---

### Post by Razorback on 2011-03-29
Did you install wpasupplicant?  I think it aids for WPA/WPA2 connections.  You get the package in synaptic.

---

### Post by mpthrapp on 2011-03-29
I ran $sudo apt-get install wpasupplicant and it says it's the latest version.

---

### Post by Razorback on 2011-03-30
So, does the connection show up under System > Preferences > Network Connections.  If so, double check your security settings.  Make sure your SSID, encryption and network key are correct.  Obviously, the adapter works or you would not have been able to connect to your neighbors network.

---

### Post by mpthrapp on 2011-03-30
Yup, it shows up fine, and I have the password correct.
It tries to connect for about a minute or two then disconnects...

---

### Post by mpthrapp on 2011-03-30
I also tried switching encryption methods from TKIP to AES because I had read that some people were having trouble connecting with TKIP, but no luck.

---

### Post by mpthrapp on 2011-03-30
I also tried installing ndiswrapper, but, once again, it still failed to help.

---

### Post by Razorback on 2011-03-30
<delete>

---

### Post by mpthrapp on 2011-03-30
Unfortunately, my router only has 64/128 bit WEP or WPA2 security and my dad would prefer I didn't change it off of WPA-based security :(

---

### Post by Razorback on 2011-03-30
Sorry, I can't be more help.  I find it is easier to be in front of the machine.  I hope someone with the right knowledge chimes in.

---

### Post by mpthrapp on 2011-03-30
Thanks anyway :)

---

### Post by Razorback on 2011-03-30
What is the model of the usb module?

---

### Post by mpthrapp on 2011-03-30
Linksys WUSB854G ver. 4.
I know it's not the adapter, because I could connect fine when I had Windows 7 installed.

---

### Post by sdlyr8 on 2011-05-01
Has anyone else encountered this problem? I'm having it too. My internal wireless card connected fine to my WPA2 wireless, but now using my external wireless card (internal one was old and slow) it will only connect to WEP.

---

