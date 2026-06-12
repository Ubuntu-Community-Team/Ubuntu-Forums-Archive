---
title: "Tricky Wireless Problem, Please Help Guys!"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by JugglinPhil on 2009-06-05
Hi everybody, I just signed up here because I really need some help. I had wubi running for a while now, so i decided to get rid of windows and only use Ubuntu (9.04 by the way). Until then everything was fine, but now that windows is gone the wireles internet has stopped working. I assume this was because the windows driver were used by wubi, so I used ndiswrapper to set it up again. Everything worked fine, however my wifi card is not detected, ndiswrapper says hardware not present and lspci gives no evidence that a wireless card even exists. Now here comes the clue: I believe this is because my wifi is not activated, however I don't have a hardware switch, only a button which does not respond for some reason. My computer is a Compaq Presario cq60  120eg laptop with a 802.11b/g WLAN card if that helps, so is there any way to get this thing working again? 
Thanks for your help in advance, I really do not want to go back to windows but if this does not work I'll probably have to...
Please ask if you need any more details etc.

---

### Post by chili555 on 2009-06-05
Please open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open and press the wireless switch a few times and let's see if the kernel recognizes the key press.

---

### Post by JugglinPhil on 2009-06-06
Hi thanks for the reply, I gave the command but nothing about wireless is listed. Pressing the wireless button didn't have any effect either, so I take it it is not recognised by the system? Dunno, I'm just another newbie who doesn't know what he's doing. ^^

---

### Post by chili555 on 2009-06-07
Let's see if either *dmesg* or *messages* knows the kill switch is the problem. Please do:```
dmesg | grep -i kill
sudo cat /var/log/messages | grep -i kill
```Also, I wonder is a proper driver has bound to your wireless device. Please do:```
sudo lshw -C network
```Post all details here and we can continue.> I'm just another newbieOnce upon a time, so were we all!

---

### Post by JugglinPhil on 2009-06-07
Hi buddy, thanks a lot for your kind support, I really appreciated it. :) However, I managed to solve my problem, I reinstalled Windows on a small partition to get the drivers working again and the rest of my hard drive is Ubuntu and it works just fine. That's the easiest way I saw and I might actually need windows at some point for ubuntu incompatible software. But thanks anyway, the community really is great!

---

### Post by mikey.duhhh on 2009-06-07
I've had the same problem, and had to actually boot Vista for the first time since I installed 9.04 to get the wireless to work. 

Here's a caveat:  Don't disable the wireless in the panel. 

You'll have to shut down, wait for a little while, and reboot into Vista to get the wireless to work again.  I think there might be a bug in the 9.04 wireless app that wasn't present in earlier versions.

---

### Post by allroys on 2009-06-07
I'm having a somewhat similar problem as the original post. 

I've got an Avenger AG2 by hypersonic, running 9.04. It's got a Fn+F11 button to activate the wireless card. It is always off when I log in, but it still somehow sees the wireless networks around the house. It won't log in to any of them, and if I toggle the switch to activate the wireless, the entire system hard locks when it tries to use the card. (Either immediately if it's already trying to connect to a network, or right when I click on the wireless network if it's inactive.) By hard lock, I mean it no mouse or keyboard, no Ctrl+Alt+Del, nothing except hold in the manual shut down button.  

The wireless card is a 
"Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)"
According to lspci...

Please help, I love the computer, except this stupid CAT-5 cable!

---

