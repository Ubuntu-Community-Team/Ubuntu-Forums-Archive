---
title: "How to make sure my files weren't remotely accessed?"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by d'oh on 2011-09-25
I did a fresh install of Ubuntu 11.04  on my desktop computer last saturday and, as I was having some problems with my internet connection, I had to reset my wireless router and reconfigure it.

Turns out, as my nickname suggests, I'm not very bright, and I forgot to confirm my Wi-Fi security preferences, which were supposed to allow wireless access only to my laptop's MAC address. Just 10 minutes ago I realized that the Wi-Fi led on my router was blinking quite a lot.

Now, my question is: What are the odds that my files (those in my desktop Ubuntu) have been remotely accessed by the ruffian who plundered into my connection? And what can I do to verify whether it happened or not?

 I have changed very little the oringinal install: I installed the restricted extras and SSH, in order to access my desktop files from my Xubuntu laptop. I've checked the SSH log in my Ubuntu desktop and I can only find my laptop's IP there.

I don't know how the VNC setup works on Ubuntu, but I didn't enable it, and I just tried to make a VNC connection from my laptop and access was denied.

I have not enabled Windows-style file sharing, and I just tried to open a folder from laptop and access was denied.

My Ubuntu session starts only with password.

What else should I look for?

Thanks in advance and sorry for the rambling.
(and don't worry, I have confirmed the MAC address restriction in my router now, the Wi-Fi les stopped blinking).

---

### Post by Dangertux on 2011-09-25
If you're not running any services on your Ubuntu install (ie: samba, mysql, nfs, vnc, ssh, apache, etc) not very high. 

You mentioned you have SSH installed : if you check /var/log/auth.log it will indicate who has logged in to your machine. You say you have done this, so it should be nothing to worry about, so long as there are not large gaps of time missing in your log. 

Now on to another point : MAC address filtering is nice and all, but it is not particularly secure, it is EXTREMELY easy to spoof a MAC address, and equally easy to figure out which one needs to be spoofed. That being said your real security lies in whatever type of Wireless encryption you are using. You should be using WPA2 if your wireless access point supports it, or at the very least WPA.

---

### Post by d'oh on 2011-09-25
> **Dangertux said:**
> If you're not running any services on your Ubuntu install (ie: samba, mysql, nfs, vnc, ssh, apache, etc) not very high. 

You mentioned you have SSH installed : if you check /var/log/auth.log it will indicate who has logged in to your machine. You say you have done this, so it should be nothing to worry about, so long as there are not large gaps of time missing in your log. 


Thanks for the quick response!

I have just double checked auth.log.0 and auth.log.1 with the log viewer. I did a Ctrl+F search for the word "Accepted" and all the matches were followed by my laptop's address.
The log goes back to Sept 18th, which is last sunday, one day after I installed it.

Are there any other logs that I should check?

> **Dangertux said:**
> 
Now on to another point : MAC address filtering is nice and all, but it is not particularly secure, it is EXTREMELY easy to spoof a MAC address, and equally easy to figure out which one needs to be spoofed. That being said your real security lies in whatever type of Wireless encryption you are using. You should be using WPA2 if your wireless access point supports it, or at the very least WPA.

I'm not using any passwords for my wireless because a friend of mine told me that if you turn on WPA or WEP, the router stop checking the MAC filtering, and vice-versa. Is that correct? I don't know anything about networking, so I don't know if you can turn on both methods at the same time. 

What I did for now, was to change my WiFi SSID and hide it. Would MAC filtering + hidden SSID be enough security, or should I just enable WPA2 and disable MAC filtering?

Thanks a lot!

---

### Post by Dangertux on 2011-09-25
> **d'oh said:**
> Thanks for the quick response!

I have just double checked auth.log.0 and auth.log.1 with the log viewer. I did a Ctrl+F search for the word "Accepted" and all the matches were followed by my laptop's address.
The log goes back to Sept 18th, which is last sunday, one day after I installed it.

Are there any other logs that I should check?



I'm not using any passwords for my wireless because a friend of mine told me that if you turn on WPA or WEP, the router stop checking the MAC filtering, and vice-versa. Is that correct? I don't know anything about networking, so I don't know if you can turn on both methods at the same time. 

What I did for now, was to change my WiFi SSID and hide it. Would MAC filtering + hidden SSID be enough security, or should I just enable WPA2 and disable MAC filtering?

Thanks a lot!

Those 2 files should contain all the logs pertinent to SSH logins so if nothing is odd there you should be fine on that front.

Now back to Wireless Security. MAC filtering has nothing to do with WPA or WEP whatsoever. 

As far as the hidden SSID that is also relatively meaningless. Malicious individuals who wish to break in to your Wireless network can quite plainly see the access point via its BSSID (which is the MAC address of the access point) the named ssid (also known as ESSID) that you hid does nothing for them or you it is entirely optional for them to even know it.

WPA provides better security than either hiding your SSID or MAC filtering which provide you virtually no security whatsoever against anyone who has the capability to perform a simple google search, download some free software and have a few extra minutes on their hands.

I highly encourage using WPA/WPA2. WEP is considered deprecated and can be cracked in minutes.

Hope this was helpful.

---

### Post by d'oh on 2011-09-25
> **Dangertux said:**
> Those 2 files should contain all the logs pertinent to SSH logins so if nothing is odd there you should be fine on that front.

Now back to Wireless Security. MAC filtering has nothing to do with WPA or WEP whatsoever. 

As far as the hidden SSID that is also relatively meaningless. Malicious individuals who wish to break in to your Wireless network can quite plainly see the access point via its BSSID (which is the MAC address of the access point) the named ssid (also known as ESSID) that you hid does nothing for them or you it is entirely optional for them to even know it.

WPA provides better security than either hiding your SSID or MAC filtering which provide you virtually no security whatsoever against anyone who has the capability to perform a simple google search, download some free software and have a few extra minutes on their hands.

I highly encourage using WPA/WPA2. WEP is considered deprecated and can be cracked in minutes.

Hope this was helpful.

Thanks a lot mate, that was very helpful indeed!

I just enabled WPA2 personal and chose a long passphrase. I also kept the MAC filtering.

---

### Post by Dangertux on 2011-09-25
Great : Glad I could be helpful :-)

---

