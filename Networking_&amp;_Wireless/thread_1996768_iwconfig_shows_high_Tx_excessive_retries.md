---
title: "iwconfig shows high Tx excessive retries"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by raptir on 2012-06-04
When I first installed Ubuntu I was having some major wireless connectivity issues (hanging for 20-30 seconds trying to load a page) which were resolved by disabling the power save mode on my wireless card (other people with the Intel Centrino Wireless N 1030 reported issues with power management on). In my research for that issue I was lead to believe that the stat *Tx excessive retries* in the output of iwconfig was something of an indicator for that.

Now that I have set it to *Power Management Off* I have no issues with loading webpages, but my *Tx excessive retries* number is still very high. Through a half hour of web browsing it will get up to around 300,000. I can still hit my internet connection's full speed while performing a download. Is that something to be concerned about (increasing the possibility of corrupted downloads, possibly?) or is that a fairly normal number considering I am living in an apartment with a number of other wireless connections in the immediate area?

Thanks in advance and let me know if I can provide more details.

EDIT: To clarify, I'm really wondering if this is normal considering the conditions (many other wifi networks in the area) or could it be a problem with my laptop/router.

---

### Post by chili555 on 2012-06-04
Please try this temporarily:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Any improvement?

---

### Post by raptir on 2012-06-04
Well, that solved it. *And* it works with power management enabled now. What can I do to make that change permanent?

Also, is that a Linux-specific bug, or is it an issue with the Intel wireless regardless?

Edit: I do still get some "Invalid Misc", but it's intermittent and ~50 on a 50 MB download. I take it that's normal?

---

### Post by chili555 on 2012-06-04
> Well, that solved it. And it works with power management enabled now. What can I do to make that change permanent?
Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit.> Also, is that a Linux-specific bug, or is it an issue with the Intel wireless regardless?I don't know much about those other operating systems, but I believe it's Linux-specific. You might add to a bug report here: [http://bugzilla.intellinuxwireless.org/](http://bugzilla.intellinuxwireless.org/)> Edit: I do still get some "Invalid Misc", but it's intermittent and ~50 on a 50 MB download. I take it that's normal? Pretty much; I get a few on my iwlwifi card that otherwise works fine, too. 

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by raptir on 2012-06-04
Thanks again. Marked as solved.

I did notice that my wireless interface is now wlan1 instead of wlan0. Is there any way to restore that? I'm guessing it won't break anything if not.

---

### Post by chili555 on 2012-06-05
> I did notice that my wireless interface is now wlan1 instead of wlan0. Is there any way to restore that?Sure. You can carefully edit */etc/udev/rules.d/70-persistent-net.rules* and immediately reboot. If in the slightest doubt, post it here and we'll help.

---

