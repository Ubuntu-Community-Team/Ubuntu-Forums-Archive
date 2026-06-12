---
title: "Wireless Adapter help needed."
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by phemice123 on 2010-10-12
I've been trying a lot of the fixes but none of them seem to work so far.
I did find that my wireless card seems to be "hard blocked" when I run the rfkill list command.
I assume this is a hardware block, and it varies greatly with different models, but any help would be greatly appreciated.

I have an HP G60-458dx running ubuntu 10.10 64bit.

---

### Post by dineshs on 2010-10-12
You mean your wireless switch in the laptop is ON still it says hardblocked?
please see [this]("http://ubuntuforums.org/showpost.php?p=9952957&postcount=6")

---

### Post by phemice123 on 2010-10-12
The only switch I see is a wireless on/off button near the power button. I've been mashing on that all day and it doesn't seem to do anything.

---

### Post by dineshs on 2010-10-12
> **Peter09 said:**
>  I have also heard of a bug where, if the wireless is switched off in windows (through the function key) then it does not resume in Ubuntu. The fix was to go back to windows and switch the wireless on, not sure if this is the case here.
Did you try what Peter09 suggested in the thread I referred ?

---

### Post by stimpysoft on 2010-10-13
I also had some trouble getting my HP G60's wireless button to work.
My solution : 
use rfkill to unblock wlan, while holding down the wireless on/off button:
   $ rfkill unblock wlan

my router was detected and I was able to enter my password and connect 
(I continued holding the wireless button while connecting)
Once I made the connection and released the button, I was able to disconnect and reconnect normally.
My only problem now is that I have to use rfkill to unblock wlan after every reboot.

Hope this helps.

---

### Post by phemice123 on 2010-10-14
@dineshs Yes, but unfortunately it did not seem to work.

---

### Post by phemice123 on 2010-10-14
> **stimpysoft said:**
> I also had some trouble getting my HP G60's wireless button to work.
My solution : 
use rfkill to unblock wlan, while holding down the wireless on/off button:
   $ rfkill unblock wlan

my router was detected and I was able to enter my password and connect 
(I continued holding the wireless button while connecting)
Once I made the connection and released the button, I was able to disconnect and reconnect normally.
My only problem now is that I have to use rfkill to unblock wlan after every reboot.

Hope this helps.
This seems to have worked. I wish there was a more permanent solution though.

---

### Post by phemice123 on 2010-10-14
I think it might possibly be a hardware issue. I've since tested it on windows 7, where it works fine, but it actually disables itself every time I put the computer to sleep.

---

