---
title: "Problem- wireless lenovo N500"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by glummyro on 2013-07-04
Hello,

I have a problem with wireless. I use ubuntu 13.04.
```
sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

[B]Wi-Fi Networks
Wi-Fi is disabled by hardware switch

[/B]I try FN+F5, but nothing.

---

### Post by kc1di on 2013-07-04
There must be a botton on the laptop that turns off wireless on my Dell it uppcase F2 key.
Just down loaded the Manual for your Lenovo and it says the FN+F5 key turns wireless on and off try that first. 
You can down load a pdf copy of the manual [here.]("https://www.google.com/url?q=http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/45n3577_01.pdf&sa=U&ei=KzfVUaagN5W34AP6yYGIAQ&ved=0CAwQFjAC&client=internal-uds-cse&usg=AFQjCNFqe6KKvhWwxUkaejgK4B8tAKOkvQ")
this is what it says:
> Enable or disable the built-in wireless networking features and the Bluetooth features. If you press Fn+F5, a list of wireless features is displayed. You can quickly change the power state of each feature in the list.

---

### Post by glummyro on 2013-07-04
> **kc1di said:**
> There must be a botton on the laptop that turns off wireless on my Dell it uppcase F2 key.
Just down loaded the Manual for your Lenovo and it says the FN+F5 key turns wireless on and off try that first. 
You can down load a pdf copy of the manual [here.]("https://www.google.com/url?q=http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/45n3577_01.pdf&sa=U&ei=KzfVUaagN5W34AP6yYGIAQ&ved=0CAwQFjAC&client=internal-uds-cse&usg=AFQjCNFqe6KKvhWwxUkaejgK4B8tAKOkvQ")
this is what it says:

I try FN + F5, but not function.

---

### Post by rkmugen on 2013-07-04
Well, if FN+F5 doesn't work, you could try this workaround... "soft-unblocking".  Here's the manual page for rfkill:

> **[NAME ]("http://man.cx/rfkill%288%29#heading1")**

   rfkill &#8722; tool for enabling and disabling wireless devices

  **[SYNOPSIS ]("http://man.cx/rfkill%288%29#heading2")**

   **rfkill** [*options*] *command*

  **[OPTIONS ]("http://man.cx/rfkill%288%29#heading3")**

    ***&#8722;&#8722;version***

  Show the version of rfkill.

  **[COMMANDS ]("http://man.cx/rfkill%288%29#heading4")**

   [TABLE="width: 100%"]
[TR]
[TD="width: 11%"][/TD]
[TD="width: 7%"]   **help**[/TD]
[TD="width: 4%"][/TD]
[TD="width: 78%"]   Show rfkill’s built-in help text.[/TD]
[/TR]
[TR]
[TD="width: 11%"][/TD]
[TD="width: 7%"]   **event**[/TD]
[TD="width: 4%"][/TD]
[TD="width: 78%"]   Listen for rfkill events and display them on stdout.[/TD]
[/TR]
[/TABLE]
  **list** *[type]*
  List the current state of all available rfkill-using devices, or just all of the given type.

  **block** *index|type*

  Disable the device corresponding to the given index. *type* is one of "all", "wifi", "wlan", "bluetooth", "uwb", "ultrawideband", "wimax", "wwan", "gps" or "fm".

  **unblock** *index|type*
  Enable the device corresponding to the given index. If the device is hard-blocked, e.g. via a hardware switch, it will remain unavailable though it is now soft-unblocked.



So, you could use:```
sudo rfkill unblock all
```

Or, if you just want to activate an individual device type, like wifi, you can just do it that way:
```
sudo rfkill unblock wifi
```

---

### Post by glummyro on 2013-07-04
```
# sudo rfkill unblock all
# sudo rfkill unblock wifi
# sudo rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

after restart machine

```
# sudo rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

---

### Post by rkmugen on 2013-07-04
You might want to refer to the last post of this thread from the user Chuckles59h on the Lonovo Forums...

[LIST]
[*=1][http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/wireless-capability-is-not-turning-on-lenovo-n500/td-p/152565](http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/wireless-capability-is-not-turning-on-lenovo-n500/td-p/152565)
[/LIST]
[INDENT]
[/INDENT]
Basically he makes reference to a hardware switch that you can slide on the front of the computer...
[IMG]http://ww2.justanswer.com/uploads/ITuser07/2009-10-27_191446_untitled.JPG[/IMG]

---

### Post by Bucky Ball on 2013-07-04
*Thread moved to **Networking & Wireless**.*

Unsure why this was in ***Apple Users*** ...

---

### Post by glummyro on 2013-07-05
Yes, this button is to right. and FN + F5 not work.

---

### Post by rkmugen on 2013-07-05
Hmmm... well, can you determine if this problem is present in other operating systems (eg. Windows) or perhaps a different, non-Ubuntu-based distro (Debian, Arch, Gentoo, Fedora, etc.)?  If the problem persists in those other OSes, then I'm afraid, something is physically broken or shorted-out inside your N500.

---

