---
title: "wifi disconnects on ubuntu11.04"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by imubun2 on 2011-10-26
i have this shuttle computer: [http://us.shuttle.com/barebone/Models/XS35.html](http://us.shuttle.com/barebone/Models/XS35.html)

the wifi connects fine, however, from time to time, it disconnects and i have to shutdown and restart before it will reconnect again.

these days, i am finding that doesn't work as well either.

i don't know what model of the wifi card i have in here, so if there's a way to find out, please teach me.

i'm a total noob when it comes to linux.

please see attached photos of what i'm seeing.  even if i re-entered my password, it still shows up as this.  and if i disconnect manually and try to reconnect, it doesn't work either.

[Authentication Required]("http://imageshack.us/photo/my-images/269/screenshotwirelessnetwo.png/")

[Disconnected]("http://imageshack.us/photo/my-images/855/screenshottnk.png/")

---

### Post by imubun2 on 2011-10-26
^^ bump.. anyone?

---

### Post by lintoon on 2011-10-27
Maybe you have a channel overlap with one of your neighbours.  This sometimes happens to me so I turn my router off and on.

You can use a nice little utility called inSSIDer which will show the neighbouring routers and power and channels.  You can then set yours manually.  Some routers have an Auto feature on the channel option.

You could try upgrading the firmware in your router.
Try setting the wireless security to just what you need (eg wpa-psk) and not mixed mode.  
Move your router.  It may be getting interference from somewhere or the signal may be bouncing everywhere.  
Switch off any cordless phones just for test (these use the same frequency reange - 2.4Ghz)

---

### Post by imubun2 on 2011-10-27
> **lintoon said:**
> Maybe you have a channel overlap with one of your neighbours.  This sometimes happens to me so I turn my router off and on.

You can use a nice little utility called inSSIDer which will show the neighbouring routers and power and channels.  You can then set yours manually.  Some routers have an Auto feature on the channel option.

You could try upgrading the firmware in your router.
Try setting the wireless security to just what you need (eg wpa-psk) and not mixed mode.  
Move your router.  It may be getting interference from somewhere or the signal may be bouncing everywhere.  
Switch off any cordless phones just for test (these use the same frequency reange - 2.4Ghz)

hi, thank you for your suggestions.  i have another computer next to it that is also running wifi.  but when this computer was running windows XP and the other is on Win7, I never had this problem before until i formated the WinXP to Linux.  

i love the linux os and hopefully there's a fix to my wifi disconnecting issue.  :(

---

### Post by lintoon on 2011-10-28
From what I've read a lot of users seem to be having wifi issues.

You could try finding your wifi adapter here

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

and see if there is a known issue or installation method.

---

