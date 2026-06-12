---
title: "can't connect to WiFi  after changing router"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by engine on 2013-03-31
New TP-LINK router successfully installed, with new-fangled WEP 128-bit security; assorted devices &#8210; Mac, Android and Lubuntu &#8210; added to ACL to be on the safe side. Everything except the Lubuntu notebook connects first time … the notebook hangs around for a long time before asking for the general password, then asks for the router access password; thinks about it, and doesn't connect. To rub salt in the wound, when I connect with an Ethernet cable the notebook keeps interrupting what I'm doing by demanding the two passwords … and still failing to connect.

How do I set about analysing what's wrong? Thanks in advance for patient tips and explanations.


Kernel: 3.2.0-39 generic
Distribution: Ubunto 12.04.2 LTS

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by wildmanne39 on 2013-03-31
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by kleenex on 2013-03-31
Hi **ahallubuntu** is right writing about WEP key weakness. Make sure you're using **STRONG** encryption: not WEP but WPA/WPA2. Use a good key consisting of all 63 characters like e.g. $#Tt5 etc., you only have to type it once anyway.

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by kleenex on 2013-03-31
OK, but my post, was only a suggestion. Decision belongs to **engine**.

---

### Post by wildmanne39 on 2013-03-31
Please stay on topic, the real issue is to help the OP get his wireless to connect and work properly not debate security.

But it is a well known fact to people that help with wireless issues that wpa2 only works best for security and linux drivers being able to connect too.
Thanks

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by wildmanne39 on 2013-03-31
> The original poster implied he/she was already connecting to an old router, so it would seem the wireless card is already working. is this directed at me? 

He also states> Everything except the Lubuntu notebook connects first time … the notebook hangs around for a long time before asking for the general password, then asks for the router access password; thinks about it, and doesn't connect.
which suggests while it works there maybe a driver parameter that will help it work better to go along with changing encryption to wpa2.

I agree with your directions but we need to stay on topic so if any other comments need to be made that are not directed at the OP after he replies please do them in a pm.
Thanks

---

### Post by engine on 2013-04-01
<sigh> my mistake, which seems to have stirred up a lively peripheral discussion &#8230; I should have typed WPA-PSK as the new-fangled (to me) security option. The old connection was on WEP, started up when I started the notebook and ran smoothly. Let's start again with the correct information, and my apologies for the error. 

New TP-LINK router successfully installed, with new-fangled **WPA-PSK** security; assorted devices &#8210; Mac, Android and Lubuntu &#8210; added to ACL to be on the safe side. Everything except the Lubuntu notebook connects first time &#8230; the notebook hangs around for a long time before asking for the general password, then asks for the router access password; thinks about it, and doesn't connect. To rub salt in the wound, when I connect with an Ethernet cable the notebook keeps interrupting what I'm doing by demanding the two passwords &#8230; and still failing to connect.

How do I set about analysing what's wrong? Thanks in advance for patient tips and explanations.


Kernel: 3.2.0-39 generic
Distribution: Ubunto 12.04.2 LTS

---

### Post by wildmanne39 on 2013-04-01
Please see post 3. I will be in and out today because my young child is having surgery out of town but if you post the information asked for then someone will be abe to see what is going on and most like be able to help you.
Thanks

---

