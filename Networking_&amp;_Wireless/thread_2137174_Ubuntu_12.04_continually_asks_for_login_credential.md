---
title: "Ubuntu 12.04 continually asks for login credentials."
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by Kyzz on 2013-04-19
Hello,  

I've had Ubuntu installed for a few months,and have stopped using it since It can't connect to the internet.  I have a Intel(R) Centrino(R) Advanced-N 6205 wireless card in my Thinkpad X220.  When I first login I am able to be online for a few moments then it drops and asks me for my login and password every two minutes.  Anyone have suggestions that I can accomplish while offline?  I attend university and I'm on their WPA connection with zero issues while on Windows.

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by Kyzz on 2013-04-19
Yeah just did with no luck...

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by Kyzz on 2013-04-19
Trying that now...one moment

---

### Post by Kyzz on 2013-04-19
> **ahallubuntu said:**
> How about disabling power management?

[http://blog.linuxjunkie.com/blog/2012/04/11/linux-and-the-intel-centrino-wireless-n-1030/](http://blog.linuxjunkie.com/blog/2012/04/11/linux-and-the-intel-centrino-wireless-n-1030/)

(Hint: does it work better with power plugged in vs. just running on battery?)

Well tried it with power pluggin in vs unplugged and no difference...

---

### Post by ahallubuntu on 2013-04-19
Type "iwconfig" and make sure it says "power management: off" when plugged into AC power.

Sorry to hear of your frustration with this problem.  I have several laptops with a different Intel card using the same iwlwifi driver in 12.04 and they all work flawlessly, on many different access points.

---

### Post by Kyzz on 2013-04-19
Power management is turned off. 

It keeps asking me to login to my schools Internet but it won't connect.

---

### Post by Kyzz on 2013-04-20
bump

---

### Post by Kyzz on 2013-04-21
bump

---

### Post by ashwinrao on 2013-04-21
Have you tried to log in via console (Alt+F2)? If able to login, check for .Xauthority file in your home directory and rename it (using mv command). After this, you should be able to login via GUI. Once this happened to me and I was able to login by this method.

---

### Post by Kyzz on 2013-04-21
> **ashwinrao said:**
> Have you tried to log in via console (Alt+F2)? If able to login, check for .Xauthority file in your home directory and rename it (using mv command). After this, you should be able to login via GUI. Once this happened to me and I was able to login by this method.

I'm still new with Ubuntu so could you break it down into steps please?  I'm no sure what you mean.

---

### Post by midnightramen on 2013-04-21
i think there is some confusion. The login via console method and home directory .Xauthority move / rename is referring to the Ubuntu login. My sense, unless incorrect, is that the "login and password" that keeps on popping up and not referring to the Ubuntu login, but rather with the wifi access point "login and password".

If I have understood the issue correctly, what I would say is that the issue may be with the specific settings for connectivity with wifi - possibly the encryption or compression method. What I would say is that login to the wifi via Windows, note down the encryption (TKIP / AES, etc) and other settings, and then check to see if the same settings are used in Ubuntu. A rather general reply, but hopefully it points you to a resolution.

---

### Post by ashwinrao on 2013-04-22
Thanks [**[COLOR=#000000]@midnightramen[/COLOR]**]("http://ubuntuforums.org/member.php?u=1811935") for pointing out my mistake. Yes, my solution was to Ubuntu login. I haven't read the initial post of OP completely and in a hurry made a mistake of posting wrong solution. It seems that real issue is due to the specific settings for connectivity with wifi here.

---

