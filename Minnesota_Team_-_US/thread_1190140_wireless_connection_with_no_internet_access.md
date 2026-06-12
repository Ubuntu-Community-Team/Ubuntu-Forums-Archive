---
title: "wireless connection with no internet access"
date: 2009-06-17
forum: Minnesota Team - US
---

### Post by rscsok on 2009-06-17
I installed ubuntu 9.04 on my Dell Inspiron 1525 some time ago & had wireless connection & internet for a short while. Then the internet was lost! I still have a great wireless connection (100%) but no internet! I've uninstalled & reinstalled ubuntu probably 3 times now with the same results & am ready to give it up altogether. My router is a netgear WGR614v7 & have Dell Wireless 1395 WLAN Mini-Card.
   Please some simple instructions, not pages of data! I would certainly appreciate any help. Thanks, Rand

---

### Post by ppjdd on 2009-06-25
Well I had the same problem. I found a forum somewhere that helped me. I copied the info and it is long. But it worked for my card. It might be of some help to you.

[COLOR="Navy"]I've finally managed to get my Airlink AWLC3028 wireless card working on the most recent version of Xubuntu (Hardy) so I decided to write a tutorial for anyone else who is in the same boat I was!

-The installation process I describe here does require a working internet connection. I used the Windows Drivers via the ndiswrapper program.

1. Open the Synaptic Package Manager and install ndisgtk. This will require you to install ndiswrapper-utils-1.9 and ndiswrapper-common. Do it.

2. After installation of ndiswrapper you're going to need to get ahold of the Win98 Drivers for AWLC3028. They can be found on the installation CD you received with your wireless card or they can be found at [www.airlink101.com](www.airlink101.com)

(The driver file you want is the net8185.inf found in the Win98 directory.)

3. Copy the .inf file from your CD or .zip file to your User Directory.

4. Click Applications > System > Windows Wireless Drivers and click Install New Driver. Then point to the .inf file you just placed in your directory.

5. At this point it should say net8185 hardware present: yes and the act led light on your wireless card should start blinking.

6. From the point go ahead and open up the terminal. Go ahead and type ndiswrapper -l to verify you have the driver installed properly. You should get..

net8185 : driver installed
device (10EC:8185) present

7. In the terminal type sudo gedit /etc/modprobe.d/blacklist and make sure you have

blacklist rtl8187
blacklist rtl818x

8. Go to Applications > System > Network. Unlock this and select the Wireless Connection and click Properties. Under properties select the connection you plan to use, pick your encryption type, enter your key, and select automatic configuration.


You're done! Your wireless connection should be working from here, if not you may need to reboot but you should be set. Let me know if this works for you or if you have any problems.u[/COLOR]

I hope this helps you. If not then I will try harder.

---

