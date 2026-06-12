---
title: "Mythbuntu Key-ring auto entry?"
date: 2008-08-05
forum: Mythbuntu
---

### Post by higgylm on 2008-08-05
Hi there,

When i start up my mythbox box i am prompted for a password keyring in order to connect to my network, this is a pain because i dont have a keyboard attached, is there any way that the password can be entered automatically?

Thanks

---

### Post by fatmonk on 2008-11-08
[bump]

I'm also having this issue and it's really bugging me having to plug in a screen and keyboard to work on my box rather than VNC to it as I did with Hardy.

-FM

---

### Post by fatmonk on 2008-11-10
[bump2]

I can't believe there's no response to this one.

Is everyone who has upgraded to 8.10 running with a system that asks for a default keyring password on boot?

To me, this means that a Myth box can't be run 'as an appliance', and I'll always need a keyboard handy to get the box up and on the network if it needs rebooted for any reason.

I've hunted and hunted for a solution to this, but most seem to involve uninstalling NM, which seems a bit drastic - surely this is just a default keyring issue.

For info, I didn't enter a password for the keyring during the install - I just hit return. I got no message about that being insecure as some have reported, but now I have to enter my logon password to unlock the default keyring.

-FM

---

### Post by johnnybirdman on 2008-11-10
> **fatmonk said:**
> [bump2]

I can't believe there's no response to this one.

Is everyone who has upgraded to 8.10 running with a system that asks for a default keyring password on boot?

-FM

I upgraded to 8.10 from 8.04 and don't have that problem.  I do have that issue on my xubuntu 8.10 laptop.  This issue usually comes up in the context of connecting to a wireless network.  However, I don't think I read anywhere in your post that you were using wireless but I wanted to confirm a working 8.10 box without this issue.
J.

---

### Post by Lester_Burnham on 2008-11-11
This is my /etc/network/interfaces file. It auto-connects at boot.
I'm still using mythbuntu 8.04 and RT73 wireless dongle.

```
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid **your ssid**
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=11
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=**your wpa password**
pre-up iwpriv wlan0 set TxRate=0
mtu 1500
auto lo
iface lo inet loopback
```

---

### Post by fatmonk on 2008-11-11
> **johnnybirdman said:**
> I upgraded to 8.10 from 8.04 and don't have that problem.  I do have that issue on my xubuntu 8.10 laptop.  This issue usually comes up in the context of connecting to a wireless network.  However, I don't think I read anywhere in your post that you were using wireless but I wanted to confirm a working 8.10 box without this issue.
J.

Sorry, that's an oversight. I am connecting via wireless.

Worked perfectly in 8.04, but need to enter the password to unlock the default keyring every time the machine boots under 8.10.

-FM

---

### Post by johnnybirdman on 2008-11-11
> **fatmonk said:**
> Sorry, that's an oversight. I am connecting via wireless.

Worked perfectly in 8.04, but need to enter the password to unlock the default keyring every time the machine boots under 8.10.

-FM

If wireless then take a look at this [[COLOR="SandyBrown"]**post here**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1").  I plan to implement this on my laptop... as soon as I get around to it....

---

### Post by fatmonk on 2008-11-12
> **johnnybirdman said:**
> If wireless then take a look at this [[COLOR="SandyBrown"]**post here**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1").  I plan to implement this on my laptop... as soon as I get around to it....

Tried that last night.. no change, still asks for the password to unlock the keyring.

The auto-login and start of the Myth frontend itself doesn't ask for a password (although there IS a user password) - and I understand this to be correct behaviour.

The default keyring thing opens up behind the Myth frontend GUI and only pops forward when I hit a key.

To me, this whole having to enter a password on the keyboard goes completely against Myth's intention to allow you to build 'an appliance'.

-FM

---

### Post by johnnybirdman on 2008-11-12
> **fatmonk said:**
> Tried that last night.. no change, still asks for the password to unlock the keyring.

The auto-login and start of the Myth frontend itself doesn't ask for a password (although there IS a user password) - and I understand this to be correct behaviour.


-FM

Like everything else in Ubuntu, there is a way to get it done we just need to figure out how.  It is certainly less usable unless it can auto connect.
J.

---

### Post by quantumhobbit on 2008-12-01
Originally Posted by johnnybirdman  View Post
If wireless then take a look at this post here. I plan to implement this on my laptop... as soon as I get around to it....

I tried this as well with no success.  For the record I am using WIFI with a WPA password on Mythbuntu 8.10.  When I log in the Key-ring popup appears behind the MythTV frontend.  I also have to click ok to log into the wireless network, requireing a mouse as well as a keyboard.  As far as I am concerned this renders my Mythbuntu set up useless as an appliance.

---

### Post by Geurrilla on 2008-12-28
No one has solved this? :/

---

### Post by NickMalone85 on 2009-01-27
[http://nickblog85.blogspot.com/2009/01/how-to-of-week-remove-default-keyring.html#links](http://nickblog85.blogspot.com/2009/01/how-to-of-week-remove-default-keyring.html#links)

Maybe this can help.

---

### Post by Bal_Zac on 2009-01-28
You can try [WICD]("http://wicd.sourceforge.net/").

---

### Post by johnnybirdman on 2009-04-25
Finally found an easy solution that works... at least it works on a new Ubuntu 9.04 install, have not tried to mythbuntu yet.
J.

[http://ubuntuforums.org/showthread.php?t=1136366]("http://ubuntuforums.org/showthread.php?t=1136366")

---

