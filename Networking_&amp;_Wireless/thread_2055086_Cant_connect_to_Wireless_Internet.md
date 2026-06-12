---
title: "Cant connect to Wireless Internet"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by AnUbunter on 2012-09-08
I have been searching for HOURS with no resolution
I can connect to the internet via ethernet but not through wifi, it shows the signal but the internet doesnt work.
I tried with another wifi connection and it works so the problem is my computer cant connect to my home wifi router. I think its because of the wireless card or something after reading a lot of topics, but i only just got ubuntu today and am running 12.04 so dont use much big words :P i know about terminal and thats about it.

I am running 12.04 with a HP Elitebook 2760p.
I forgot how to see the wireless network card thing via the terminal but i remember that it is a Centrino one and had HD in it

Any help will be appreciated!

Thanks,
 A soon to be Ubuntu Converter

---

### Post by Janomark on 2012-09-08
Pretty much in the same boat as you at the moment. I don't have the technical knowledge to really help but I do know the command to get your network controller. 

Try: lspci -nnk | grep -iA2 net

---

### Post by PerplexedPangolin on 2012-09-08
Do you have a Broadcom STA driver?  I had the same problem after upgrading to 12.04, now I'm sitting at Panera Bread using wireless... check out this thread and see if it helps:

[http://ubuntuforums.org/showthread.php?t=2053243](http://ubuntuforums.org/showthread.php?t=2053243)

---

### Post by AnUbunter on 2012-09-09
Bump

Not much point having a laptop if i cant move it around!
Someone please help

Found out my card is a Intel Corporation Centrino Advanced-N 6205

---

### Post by chili555 on 2012-09-09
Please try this temporarily. If it helps, we'll write one file to make it persistent:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Thanks.

---

### Post by AnUbunter on 2012-09-10
Wow! You are a life saver!
Thanks so much, ive spent HOURS looking for a solution with no success

It worked btw so how should i make it persistent?

---

### Post by chili555 on 2012-09-10
Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Use kate, leafpad or any text editor if you don't have gedit. Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. You should be all set.

Please use thread tools at the top to mark Solved. Have fun!

---

