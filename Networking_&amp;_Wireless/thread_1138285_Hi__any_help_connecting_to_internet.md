---
title: "Hi  any help connecting to internet"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by daie3 on 2009-04-26
***hi any help to connect to broadband internet i installed ubuntu 8.10 from 5 days and till no i cant access the internet from ubuntu i try every threads i found here but no thing happened ***
Apr 25 05:04:56 ubuntu pppd[5799]: local  IP address 172.16.22.227
Apr 25 05:04:56 ubuntu pppd[5799]: remote IP address 172.16.22.1
Apr 25 05:04:56 ubuntu pppd[5799]: primary   DNS address 2.2.2.10
Apr 25 05:04:56 ubuntu pppd[5799]: secondary DNS address 4.5.6.7
Apr 25 05:04:58 ubuntu pppd[4102]: CHAP authentication failed
Apr 25 05:04:58 ubuntu pppd[4102]: CHAP authentication failed
Apr 25 05:04:58 ubuntu pppd[4102]: Connection terminated.

---

### Post by krazymir on 2009-04-26
> **daie3 said:**
> ***hi any help to connect to broadband internet i installed ubuntu 8.10 from 5 days and till no i cant access the internet from ubuntu i try every threads i found here but no thing happened ***
Apr 25 05:04:56 ubuntu pppd[5799]: local  IP address 172.16.22.227
Apr 25 05:04:56 ubuntu pppd[5799]: remote IP address 172.16.22.1
Apr 25 05:04:56 ubuntu pppd[5799]: primary   DNS address 2.2.2.10
Apr 25 05:04:56 ubuntu pppd[5799]: secondary DNS address 4.5.6.7
Apr 25 05:04:58 ubuntu pppd[4102]: CHAP authentication failed
Apr 25 05:04:58 ubuntu pppd[4102]: CHAP authentication failed
Apr 25 05:04:58 ubuntu pppd[4102]: Connection terminated.

try:
sudo lspci -nn
see if you see your network card listed with the proper name and model it's a good bet that you have the right driver.
Adjust your wired connection with the network manager.
then try:
sudo pppoeconf
answer all the questions.
I hope this helps :)

---

