---
title: "WUSB54Gv2 networking problem"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by alex.montandon on 2006-06-10
Hi all,

I installed ubuntu yesterday, it was very smooth (much more that the windows xp one :D). My video card, sound card and everything was detected and all works fine. I have been trying to get the internet working. I have a WUSB54Gv2 (wireless-g) usb network adapter. After looking around these forums and following some of the instructions for it, it seems like it is dectected (it detected two wireless networks near me (throught the essid form)):

[[IMG]http://img131.imageshack.us/img131/6677/screenshot18ql.png[/IMG]](http://imageshack.us)

I just dont know what to enter in the IPaddress, subnet mask and gateway address forms. I tried contacting my ISP (they speak very little english, i live in thailand) who said that my ip address and my gateway address was 192.168.1.1 (the address to get to the linksys preferences). Is this correct? I also have a another computer with windows installed and which connects to the same network. If i do a ip lookup, would that give me the correct ip to put in the form?

When i try puting 192.168.1.1 as my IP and gateway address and enable, the computer doesnt freeze (it did before). i think this is because i blacklisted:

blacklist islsm_usb
blacklist islsm_device
blacklist islsm
blacklist ieee80211softmac
blacklist ieee80211
blacklist ieee80211_crypt

However, when i press OK, the computer freezes :( any thoughts on this?

I dont know if ive posted all the information needed to solve this problem so if you need to know anything else, please tell me. thanks in advance for any help.

thanks, alex

---

### Post by alex.montandon on 2006-06-10
anyone?

I think that I've found all the info i need, but now, when i insert all the settings and click 'OK', the computer freezes.. does anyone know how to solve this and what the problem might be?

thanks, alex

---

