---
title: "Dual boot laptop with wifi problem"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by Sandy.1 on 2012-07-12
but only on Ubuntu.

I have a Compaq Presario set up as dual boot with Windows XP and Ubuntu 12.04 LTS.

VDSL modem is upstairs and by itself doesn't have much signal when I try to use the laptop downstairs so have added a Belkin N300 wireless router to provide a good signal in the sitting room.

Booting into XP the wifi works perfectly and the little blue wireless switch/light is nicely alight.

If I boot straight into Ubuntu the wifi switch appears to be inoperative.

However it is possible to switch from XP into Ubuntu and at the same time keep the wifi light shining.

BUT  there is no wifi connection.

Gave the problem a ccouple of hours last night and on occasion seemed to get a clear indication that Broadcom STA drivers were installed and active.


This is where I throw my hands up and ask for your advice. Where do I go from here.

Cheers   Sandy

---

### Post by chili555 on 2012-07-12
Please open a terminal and let us see some diagnostics. Please run and post:```
lspci -nn | grep 0280
rfkill list all
lsmod | grep -e wl -e b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Sandy.1 on 2012-07-12
Thanks for your prompt reply. Now I have to confess that I am a complete beginner so working through your recommendations may take a while.

I have brought the problematical laptop back up to my study where when in Windows it is receiving a good signal from the modem which is just across the room. I now seem inacapable of booting into Ubuntue while keeping the wifi light on.

There is/was a message on the screen saying wifi disconnected

Going into a terminal is new ground for me

Alt + F2and I have an invitation to run a command and I have copied in your first line
. This appears to be copied down to a section called Results

I have continued typing in the rest of your instructions and all have been copied down to results.

Finished with an Enter but no results were forthcoming.

Looks like I need to go away and read up on using a terminal.

More anon

Sandy

---

### Post by chili555 on 2012-07-12
If you are running Unity and have the white, possibly, Ununtu symbol in the upper left corner, click it and type in 'terminal.' When the black box opens, type in the commands one at a time and press Enter. Copy and paste the whole result here, like this from my machine. Please see attached. ```
chili@LAPTOP60:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
chili@LAPTOP60:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
chili@LAPTOP60:~$ lsmod | grep -e b43 -e wl
iwlwifi               289862  0 
mac80211              440734  1 iwlwifi
cfg80211              178818  2 iwlwifi,mac80211
```Please note my details are very different from yours; your exact readings will help us figure out what's wrong and how to fix it.

---

### Post by steeldriver on 2012-07-12
... you may find it easier to hit Ctrl-Alt-t to get the terminal up (rather than using the search box)

---

### Post by Sandy.1 on 2012-07-12
Getting there !!! can't cut and paste from laptop onto this desktop but first line up to grep 0280 results in      06:00.0 Network controller (0280): Broadcom Corporation BCM4311 802.11b/g WLAN ( 14e4:4311)  ( rev 01)
Next line results exactly like yours through to Hard Blocked: no

And the last line results in wl ( in red)     2646601 0
                                                   lib80211        14040    1  wl ( in red again)


Hope this means something !!!

Sandy

---

### Post by chili555 on 2012-07-12
Yes, indeed; it means the wrong driver is installed. Can you please temporarily hook up the ethernet, get a connection and open the terminal again and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us have your good news.

---

### Post by Sandy.1 on 2012-07-12
have followed the instructions and the good news is that I now have the little blue wifi light glowing on the laptop.

Unfortunately I still can't get a connection !!!

Windows is working fine and Wifi radar shows a good signal.

Going to reboot and try again and await further instructions.

Really do appreciate your help

Sandy

---

### Post by Sandy.1 on 2012-07-12
And the really good news is that this message is coming from the laptop on wifi and Ubuntu. many, many thanks. Next job has to be to learn what all those instructions meant !!!

Cheers  Sandy

---

### Post by chili555 on 2012-07-12
Awesome! Glad it's working. Please use thread tools at the top and mark Solved.

---

### Post by billhedges on 2012-08-25
it worked great!
thank you so much.
i dont know the 1st thing about computers .
but that  was easy!

dell d620

---

