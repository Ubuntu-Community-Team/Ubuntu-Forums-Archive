---
title: "Ubuntu 8.10 and 9.04 - weird Athk5 function"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by Drufi on 2009-05-23
Hello,
I'm quite knew to Ubuntu and linux in general and I've recently invested quite some time in getting my Wireless PC Card to work.
Before I go any further here are the Specs of the system (if you need or are interested in any other information please indicate which ones)

Fujitsu-Siemens Amilo Pro V2000;
1.5 Ghz Pentium M
512 ram
PC card Siemens Gigabit 108 PC Card

Now here is what has been happening and how I am resolving the problem.
When I installed 8.10 as well as 9.04, I only see Wired and Wireless network, most notably for the Wireless since, it seems, normally it indicates which card and driver.
I can't select the wireless although there is a NON-SECURE wlan. 
I hoped upgrading to 9.04 would resolve this problem i.e. it would work "out of the box". Yet this has not been the case.

1)At first I tried different solutions: Ndiswrapper, ndisgtk (GUI for ndiswrapper- if I got it correctly), the madiwifi.sh ([http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)) and finally the compat-wireless ([http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)).
Yet none of these work,
BUT the last one seems to make the Ubuntu propietary driver work:
2) I open the terminal and move to the compat* file.
(having already compiled the strings- i think this is what i did with "make")
3)I use: sudo make unload
This process is then stopped because of a fatal error (there are various ones but the repeated one is:) "ssb in use"
4)I then return to the "hardware drivers" and reactivate the proprietary drivers. 
And VOILA the network panel (on the menu bar) searches and then connects to the wireless network.

I'm really happy it works, but I don't understand why. Addtionally if I can find a work around I'd be quite happy since I wouldn't have to go through the process each time.

Hopes this can help some of you and would be grateful for some help.

cheers,
drufi

---

