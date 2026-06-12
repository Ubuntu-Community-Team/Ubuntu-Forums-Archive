---
title: "Wireless keep asking password??"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by safarin on 2011-04-02
Hi all,

Is this a bug?? Everytime I login into Ubuntu (Natty-beta), it keep asking me my wireless password then follow by keyring pop-up. I already tick "Connect automatically" in "Edit Connections.." menu. 

Need some help.
Thank you.

---

### Post by iponeverything on 2011-04-02
To stop the keyring from asking you can go to:

Applications ->  Passwords and Encryption Keys

Then to the "My Personal Keys" tab Then click on "Properties" and change the passphrase to be blank.

---

### Post by safarin on 2011-04-02
> **iponeverything said:**
> To stop the keyring from asking you can go to:

Applications ->  Passwords and Encryption Keys

Then to the "My Personal Keys" tab Then click on "Properties" and change the passphrase to be blank.

Nothing inside "My Personal Keys" :(

[ATTACH]187849[/ATTACH]

---

### Post by cariboo on 2011-04-02
Can you create a new Stored Password?

---

### Post by safarin on 2011-04-02
> **cariboo907 said:**
> Can you create a new Stored Password?

How to create that??

---

### Post by empty_spaces on 2011-04-02
> **safarin said:**
> Hi all,

Is this a bug?? Everytime I login into Ubuntu (Natty-beta), it keep asking me my wireless password then follow by keyring pop-up. I already tick "Connect automatically" in "Edit Connections.." menu. 

Need some help.
Thank you.

Have you also checked the "Available to all users" box?

---

### Post by terry_gardener on 2011-04-02
> **safarin said:**
> Nothing inside "My Personal Keys" :(

[ATTACH]187849[/ATTACH]

under the password tab.

right click passwords:logon and  select change password. 
enter current password and under new password leave blank 
click ok 
accept the security warning saying use weak password. 
thats it.

---

### Post by sddfdds on 2011-04-03
same problem here...everything was fine in maverick...all of a sudden doesnt work in natty.  when trying to connect to my network, dmesg just has this over and over

wlan0 direct probe to (mac address of my ap) timed out (try 1/3)

and then 2/3 and 3/3 and then timed out

---

### Post by safarin on 2011-04-03
> **empty_spaces said:**
> Have you also checked the "Available to all users" box?

Thanks empty_spaces, my problem solved after checked the "Available to all users" box.

sddfdds, if your problem solved after checked that box please update here. I will closed this thread as [SOLVED].

To terry_gardener, cariboo907 and iponeverything, thank you also for helping me.

:popcorn:

---

### Post by sddfdds on 2011-04-03
Unfortunately, no, that didn't solve it for me.  I'm pretty sure that was already checked in the pre-existing connection from before the update, and I confirmed it is checked now.  When the connection was setting up though, it did ask me for my password to make administrative changes or whatever so I think the user was approved either way.

Nm-tool just says 'connecting (configuring)' when its doing the direct probe thing, and then once it re-asks for the password again, it says 'connecting (authenticating)'

Thats what it did before i checked the available to all users box...but once its checked, it seems to be stuck in configuring and doing the direct probe thing over and over.  After a while it just gives up now instead of re-asking for the password.

Also, I'll just note that the wireless is still working for 3 other devices, including a maverick laptop, so the wireless itself likely isnt at issue.

---

### Post by safarin on 2011-04-03
Hmm.. weird, how about you check your password that have been save. Maybe you enter the wrong password.

Maybe hardware issue, could be Natty have hardware problem issue with your hardware driver.

---

### Post by sddfdds on 2011-04-03
I've checked and rechecked the password...not only am I sure it's correct, but i now remember the semi-random 20 letter and digit sequence because ive typed and retyped it so many times.  The hardware is a netgear wg121 usb adapter, the driver is p54usb.  It at least partially works though since the adapter is recognized fine in the system, and it does recognize the wireless ap, it just cant complete the connection

---

### Post by sddfdds on 2011-04-03
I also tried with the wireless unpassworded and it still doesnt connect, so its not specific to the wpa2 stuff

---

### Post by sddfdds on 2011-04-05
No luck with todays updates to network manager and/or the kernel

---

### Post by safarin on 2011-04-05
Have you try using other wireless device such as USB wireless dongle?? I think this is to check either the problem come with your wireless compatibility with natty, hardware issue or maybe you have no luck to solve that. :(

---

### Post by cariboo on 2011-04-05
What wireless chipset does your system have, I had a similar problem when the Broadcom wl driver was broken, and tried to use the b43 driver.

---

### Post by d3v1150m471c on 2011-04-05
This only happens if you reboot. I almost always suspend my sessions to ram if i even turn my machine off. Which means I rarely have to enter the password for the keyring. You might try doing this, and besides, you won't have to wait to boot up all the time to use your system. :)


edit:
I use the b43 driver for my broadcom card and it works perfect. ^^^, if you need it you can do:
```

sudo apt-get install b43-fwcutter

```

Also, it won't load on boot without me manually entering `sudo modprobe b43'. You can get around this by the following:
```

sudo echo "modprobe b43" >> /etc/rc.local

```

Now your new b43 wireless driver will load on boot.

---

### Post by sddfdds on 2011-04-06
safarin: it is a usb adapter...

cariboo907: its a netgear wg121 using the p54usb driver

d3v1150m471c: due to a slight misreading on my part, or a lack of clarification in the original post, my issue is slightly different.  There's no problem with the keyring, just the wpa2 password gets repeatedly asked for

---

