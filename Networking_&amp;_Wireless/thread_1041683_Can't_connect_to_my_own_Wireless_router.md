---
title: "Can't connect to my own Wireless router"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by Emanuele_Z on 2009-01-16
Hello

I can't connect to my own BT wireless router.
My wireless card is working on other (unprotected) connections and worked until 25 days ago on my own WEP connection.

My laptop is an **Asus G2S**
lspci
[i]
...03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
...
[/i]
The version of Ubuntu is 8.10.

Attaching both screenshots of my own configuration menu of the router.
I managed to make it work with this config only **once**. After that, turning off/on my laptop the connection never worked again.

I upgraded from 8.04 to 8.10, I didn't touch my network configuration (this was 3 months ago).
I successfully used Ubuntu 8.10 + WEP until 25 days ago.
One thing that I see is when I tick "Show password" then I see another string of chars (the hex value?) instead of what should be.
If I rewrite the password with the right one, it gets replaced with the hex value.

Is there any way to wireless connect via terminal/console?

For work reason I'm a 10+ year Linux/Win32 C/C++ dev (even network software), I use shell/perl scripts every day, so if you have some very technical information please feel free to share.

I'd like to fix this issue asap, because it bothers me a lot that in WinXP it works a treat (is the same computer btw).

Thanks in advance,
Ema! :-)

---

### Post by Emanuele_Z on 2009-01-16
Now I'm connected with the Ubuntu 7.10 bootable CD.
Setting the network to WEP 64bit key it works a treat.

1) Why can't I choose WEP 64bit key in 8.10?
2) In which file are those settings saved?

Thanks again,
Ema! :-)

---

### Post by Emanuele_Z on 2009-01-17
Hi guys, any news?

At least, where can I find a logfile, what are the shell commands to use to connect to a wireless network?

Can someone please say something? Really I'm **desperate**.

Again, why do
- WinXP
- Ubuntu 7.10
work a treat, while Ubuntu 8.10 doesn't?

Thanks again,
Ema! :-)

---

### Post by lemmy999 on 2009-01-17
@Ema

I think this is what you are asking for```
#Connect using commandline

#No Crypto

ifconfig <interface> up
iwconfig <interface> essid "ESSID"
iwconfig <interface> mode Managed
dhcpcd -nd <interface> 

#WEP

ifconfig <interface> up
iwconfig <interface> essid "ESSID"
iwconfig <interface> key HEXKEY
iwconfig <interface> mode Managed
dhcpcd -nd <interface>

```

---

### Post by Emanuele_Z on 2009-01-17
Thanks mate.

At the moment I've turned on WPA+WAP2 (because of security I'm using a kinda longish password).

Do you have a similar command for WPA?
Actually the settings are like the ones in the screenshots.

Btw,

- My girlfriend's Asus EEE (with linux) works
- My PS3 works
- My Wii works
- My PC with ubuntu 7.10 works.

Thanks again,

---

### Post by Emanuele_Z on 2009-01-17
Update:

While trying to connect to my wireless network I typed iwconfig and noted another wireless connection name (ssid).
Then, typing:
```

sudo iwconfig wlan0 essid "my network name"

```
It connected. And finally it works.

Might it be that the issue that on default Ubuntu network manager tries to connect to that other network with settings for the proper network?

Any thoughts?

---

### Post by Ubuginer on 2009-01-17
To get the WIFI work on my pc, I followed someone's post on this forum, but I can't find the link right now.

This is how I get it to work my two pcs:

1-Create two wireless connection names with wireless passwords(or keys) in NM
2-Go to Applications>Accessories>Passwords and Encryption Keys
3-Click the Passwords tab
4-Double-click each wireless name
5-Click on password and put keys(wireless passwords) in the box.  Do the samething on each wireless name.
6-Reboot.

---

### Post by Favux on 2009-01-17
Hi Emanuele_Z,

It looks like you may have run into a bug with NM that some of us have also encountered.  Maybe not if you have it working now.  If not try:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

### Post by Emanuele_Z on 2009-01-17
It's official,

all my other devices run perfectly, for my Ubuntu 8.10 I have to type:
```

sudo iwconfig wlan0 essid "my_wireless_name"

```
And then works.

Now I've tried deleting the old keys, and will set again the good password.
I'll keep you posted with updates.
Cheers and thanks,

---

### Post by Emanuele_Z on 2009-01-18
Ubuginer, thanks for your hint, this has allowed me to properly set the password.

The strange thing is that I have to retry a couple of time to connect, or use the 
```

sudo iwconfig wlan0 essid "my_wireless_name"

```
command.
Anyone has any ides?

Cheers,

---

