---
title: "Wireless stopped working on Lenovo S10 netbook"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by tdn on 2010-01-10
Hi. 

I have a Lenovo S10 with Ubuntu (Netbook Remix) installed. Suddenly, the wireless network stopped working. Maybe after an update. I don't know.
What do I need to do to make it work agian?
I am online from another computer right now. I can attach a network cable to the netbook to get it online.



There is no available networks to connect to.
My network is called 'opennet'. I can tried clicking "Connect to hidden network", and manually type 'opennet', but it does not connect.

I have two other Ubuntu computers. They connect immediately.

When installing Ubuntu on the netbook, I had to select non-free drivers to get the wireless to work.
I have tried uninstalling the non-free drivers and then rebooting -- no difference. Then I installed them again, rebooted. Same same.
Note, it is not the wireless network that is the problem. Because I can see *no* availalble networks. But before, there were several network. Not just my own.

I hope you can help.

---

### Post by juicyoner on 2010-01-17
Same problem here.

Has happened 3 times. First 2 times it magical;ly fixed itself after several days of not working.

is there a wireless/network reset?

please? this is very frustrating

---

### Post by barneystroud on 2010-01-17
Same happened with me a number of times, Just now on my brothers computer he got an update from ubuntu and now, no wireless connection. 
The update he got had image and grub updates I think this may be to blame.

---

### Post by nathanieldouglas on 2010-01-17
Yup.  Me too.  I went back to 9.10 standard on my s10, which used to work fine and now its not getting any network connect either.

I'd love to see a fix for this but I've looked up and down these forums for days...

---

### Post by mgol on 2010-01-17
Do You have a "Device not managed" message when right-clicking Network Manager applet? If so, I can suffer from the similar issue, see the bug report:
[https://bugs.launchpad.net/bugs/473215](https://bugs.launchpad.net/bugs/473215)
and the forum thread:
[http://ubuntuforums.org/showthread.php?p=8675480](http://ubuntuforums.org/showthread.php?p=8675480)

---

### Post by megamania on 2010-01-18
did you try running 
```

sudo dhclient

```
from the terminal? it worked for me.

---

### Post by tdn on 2010-01-18
Doh!

I have found the problem at my end. It was a user error. I (or someone) had pressed the Wireless Kill Switch.

I have attached a picture showing this button.

Press it, reboot, and your wireless network should work again.

---

### Post by juicyoner on 2010-01-18
I can't believe it was because i hit the switch. "physical" actually means physical. Like real. Tangible. Touchable.

I didn't even know this switch existed :-/

Not sure if I should blame it on me being stupid or "bad" design on the part of lenovo/ibm. maybe both?

But either way I figured it out.

Thanks for your help!

---

### Post by yunone on 2010-01-25
just installed 9.10 on my Lenovo S10 and i dont have the option to select my wireless network

all my full size laptops see the network fine, its not hidden, but this S10 does not see available networks

i have configured the wireless network connection under Network Connections>Wireless
but when i left click on the icon from the top it doesnt show a wireless network

when i ran UNR it saw the network connection fine and i didnt have issues.  just not a fan of UNR, rather run Karmic



any ideas?

---

### Post by intlbeans on 2010-05-29
> **tdn said:**
> Doh!

I have found the problem at my end. It was a user error. I (or someone) had pressed the Wireless Kill Switch.

I have attached a picture showing this button.

Press it, reboot, and your wireless network should work again.

tdn - THANK YOU. This was all I needed. And by the way, it was kind of a long press for me, I just had to press it until I saw the wireless light light up on the left side of the speaker panel (next to the power and battery lights). I feel like such an idiot, but I don't remember ever pressing this button. Maybe my kids...

---

### Post by Betobuntu on 2010-06-10
I have a Lenovo U350 and my wireless card is disabled now, i removed the battery and when i booted up my machine, the wireless card never turned on.

---

