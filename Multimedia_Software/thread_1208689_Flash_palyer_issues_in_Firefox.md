---
title: "Flash palyer issues in Firefox"
date: 2009-07-09
forum: Multimedia Software
---

### Post by jasonpmontgomery on 2009-07-09
I have made the switch from Windows to Ubuntu and could not be happier. However, I have a small issue regarding Flash in Firefox. I am able to see some flash videos like YouTube and Xtube, but I am unable to see others; such as the home page of AT&T and Cam4. 

Can any one help?

---

### Post by lovinglinux on 2009-07-09
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by nacho32 on 2009-07-09
I have tried the sites you have listed and the same problem. Tried in fire fox 3.5 and Opera latest version have the adobe flash 10 installed. No other flash plugin installed, 9.04 64 bit

---

### Post by lovinglinux on 2009-07-09
> **nacho32 said:**
> I have tried the sites you have listed and the same problem. Tried in fire fox 3.5 and Opera latest version have the adobe flash 10 installed. No other flash plugin installed, 9.04 64 bit

I don't have a 64bit system, so I can't vouch for it, but you could try this:

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

By the way, AT&T works for me on 9.04 32bit. I still believe the problem of the OP is the one describe in my previous post. Probably just a plugin conflict.

---

### Post by HappyFeet on 2009-07-10
Uninstall the flash player you have. Then download the [64bit]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") flash file. Then extract it, and put **libflashplayer.so** file into ~/.mozilla/plugins

If the plugins directory does not exist, create it.

For opera put **libflashplayer.so** into /usr/lib/opera/plugins

Restart the browsers if needed.

The above works for me.

---

