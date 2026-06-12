---
title: "Open WEP 128 bit 26 character not accepted!"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by pearsdb on 2009-04-16
How can I get my Open Wep 128 bit key accepted by Ubuntu Gui Network manager?  Both for home and work this is an issue.  local wireless networks are seen and are available but when I put in the key only hex or passphrase allows 26 character and it fails.

this is on a new dell inspiron mini..  is there a conversion of characters required?  I've tried with iwconfig as well not sure what parameter to use as the key seems to be accepted without error using sudo yet.. nothing.
Help!

---

### Post by SuperSonic4 on 2009-04-16
Is there not an option for ASCII input on wireless? I know wicd has an option to do that but it's been much too long since I used ubuntu

---

### Post by chili555 on 2009-04-16
> I've tried with iwconfig as well not sure what parameter to use as the key seems to be accepted without error using sudo yet.. nothing.```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <your_router>
sudo iwconfig wlano key <your_26_character_key>
sudo dhclient wlan0
```What is the result of these commands?

---

### Post by wkulecz on 2009-04-16
As far as I can tell the WEP ASCII key and/or passphrase is broke on Linux, I've always had to use the hex key I get from the AP configuration screen.  The hex keys should all be the same length differing only if you use 64 or 128 bit security.  As I recall the scrolling in the GUI box was broke, but I typed in the full hex key and it did work, although I could not see the last few characters I typed.

Contrary to what you might think for WEP you need to set "open system" instead of "shared key" when you enable WEP.  Shared key is actually less secure (not that WEP is anyway) and some drivers seem to refuse to work if you enable it.  Generally both the AP and all systems must agree, although some AP and drivers offer an "auto" setting which may or may not work with mixed hardware.


I've run into issues with WPA2 where the AP and wireless drivers do not agree on the maximum pass phrase length, and had to reprogram everything to use a shorter one :(

Use WPA2 or at least WPA over WEP if your AP and wireless drivers support it.

--wally.

---

### Post by chili555 on 2009-04-16
> Use WPA2 or at least WPA over WEP if your AP and wireless drivers support it.Quite correct. However the original poster says it's a problem at work, too. He may have no ability to change the encryption at work.

---

### Post by wkulecz on 2009-04-16
> **chili555 said:**
> Quite correct. However the original poster says it's a problem at work, too. He may have no ability to change the encryption at work.

In which case he also likely has no ability to change to a different or shorter key.

--wally.

---

### Post by pearsdb on 2009-04-16
thanks for the reponses didn't realise anyone had replied.
I get no response with iwconfig using wlan0 - no such device
with iwconfig:
sudo iwconfig eth1 essid is accepted
sudo iwconfig eht1 key - accepted
sudo dhclient eht1 - no offers is the final message as it shows subnet mask 255.255.255.255, at least I think this is subnet mask. 

I could modify home but work no.. as far as encryption method

just odd that wireless lans are available and I'm unable to present key appropriately to router/access point.

Thanks again!

---

### Post by chili555 on 2009-04-16
> when I put in the key only hex or passphrase allows 26 character and it fails.First, 26 characters *is* HEX. Are you saying you drop down to 128-bit HEX, then type in the entire 26 characters, even though it over-runs the box (which is normal) and click 'connect' but it won't connect? Or is your complaint that the box is not long enough to take the entire 26 characters?

---

### Post by pearsdb on 2009-04-16
as previously mentioned only passphrase or hex will even take the 26 character and the Network manager box kicks back to passphrase asking for a passphrase or key.

---

### Post by pearsdb on 2009-04-16
sorry and no it never connects

---

### Post by pearsdb on 2009-04-16
using iwlist found ad hoc network in my work building, key:off, able to connect yet my dhcp requests are ignored.. so this may not be a wep issue.  it picks up the mac of their router but will not issue an ip to my linux wireless adapter!

---

### Post by chili555 on 2009-04-16
I don't believe an ad-hoc network is intended to give out an IP address and connect you to the internet. I doubt any of the nodes is acting as a DHCP server. 

[http://en.wikipedia.org/wiki/Ad-hoc_network](http://en.wikipedia.org/wiki/Ad-hoc_network)

You are looking for networks that show up as Master.

---

### Post by pearsdb on 2009-04-18
your right.. I need infrastructure mode not ad-hoc
ok at home I've disabled wep and wireless access is available
I'll experiment with the wpa configurations but I would like to get the open wep 26 character config working as well.

thanks for your suggestions.

---

### Post by pearsdb on 2009-05-28
downloaded ubuntu 9.04 and installed it on a dell e6400
takes 128 bit / 26 character key without an issue.  I using this particular laptop right now!  possibly my dell mini wireless card is an issue or I need to see what version of ubuntu my dell mini is running and upgrade.
so old fashion open wep 128 bit is working with ubuntu.. just not on my home laptop.

---

