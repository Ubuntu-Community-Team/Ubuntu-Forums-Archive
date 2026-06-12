---
title: "Wireless stopped working under Ubuntu 9.04"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by Gniewko on 2009-08-18
Hello out there!

I upgraded my Dell Inspiron 1300 laptop to run with Ubuntu 9.04 about 4-5 months ago. From the beginning it was running well and I never experienced any troubles with wireless connectivity. In fact, where ever I went and there was a available WiFi I could connect.
Then about a week ago I wanted to use my wired connection at home for admin use. Afterwards I did not use the laptop until yesterday where I tried to connect to my WiFi - which usually happens automatically. This time however NetworkManager claimed that "Wireless unavailable". 
Subsequently I connected through ethernet/wire again (which still works fine). I tried to 'sudo ifdown eth0' thinking that there might be a driver/setup conflict between eth0 and wlan0 (as I experienced with earlier distributions). This did not help. 
I browsed various forums to see if there was something similar described out there. However could not find exactly the above mentioned problem.

Has anyone experienced this? And if so, how did you solve it? 
For the sake of good order: the laptop is equipped with a 
Broadcom 1370 adapter 4318.

Many thanks in advance!

---

### Post by superprash2003 on 2009-08-18
post output of **sudo iwlist scanning** , i have a feeling the wireless switch on your laptop must have switched off

---

### Post by Gniewko on 2009-08-18
I get the following:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


It should be mentioned that the wireless adapter is turned on (physically). NetworkManager claims that 'Wireless is not enabled' and the whole wireless section is greyed out.

---

### Post by Gniewko on 2009-08-18
Well... seems you were right about the wireless being turned off. It confused me though as the indicator lamp was on (it is usually off when the adapter is turned off). Now I made a fool of myself but at least it works. Sorry for the confusion.

---

