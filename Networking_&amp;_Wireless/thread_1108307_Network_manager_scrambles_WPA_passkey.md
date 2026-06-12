---
title: "Network manager scrambles WPA passkey"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by wiseloki on 2009-03-27
Hi,

I've recently (today) upgraded from 8.04 to 8.10 to try to improve the wireless networking of my laptop. But now the network manager seems to scramble and forget the passkey every time I enter it. If I check the "show password" box then the password in network manager bears no resemblance to the password I entered. I am using a fairly strong password with lots of non-alpha-numeric characters.

As said in the sig line, I'm a complete Ubuntu novice (never mind the cups, I haven't even ground the beans yet) and have 8.10 on an IBM T42 with built-in wireless. I'm using a Netgear DG834GT router with WPA security and currently network name being broadcast. 

If I turn off the router security then the laptop finds the network and logs in fine, so I know that the network card, etc. is OK.

The problem I had with 8.04 (same router, same laptop) was that network manager did not seem to find the network, even with the name, and mostly I had to manually enter the CSID and passkey each time I booted. I had the network details all set up as a network connection, which were reliably there, but I could never figure out how to select and force the laptop to use those connection details to log on, even if I disabled roaming. I read that network manager was better in 8.10, hence the upgrade.

When I first installed Ubuntu (using 7.10) and set up the wireless, network manager remembered the passkey and the laptop would connect automatically, even with WPA on and no name broadcast. Things just seem to have gone downhill since.

Wireless works flawlessly with a Dell C840 running XP and a Netgear USB dongle.

Any advise welcome, as I currently can only use my T42 on Ethernet. I hope this rambling explanation makes some sense to the experts here.****

---

### Post by wiseloki on 2009-03-28
Aha! (and bump). It appears that others have had the same problem. I have now found this thread:-

[http://ubuntuforums.org/showthread.php?t=975684]("http://ubuntuforums.org/showthread.php?t=975684")

And that leads to this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390")

The only thing different to my issue is that these threads did not specify that the passkey was not being maintained unchanged, but other than that, their symptoms are my symptoms exactly.

So my help request changes slightly. Being an Ubuntu novice, I've seen the manual fix in the bug report:

> Resolution (manual):
conn@inspiron:~$ sudo rmmod ipw2100 ieee80211_crypt ieee80211_crypt_tkip ieee80211_crypt_ccmp
conn@inspiron:~$ sudo modprobe lbm_cw_ieee80211_crypt_tkip lbm_cw_ieee80211_crypt_ccmp ipw2100

and this looks pretty scary to someone unused to tinkering under the hood. So my request is now for some help with understanding and installing the fix. 

I know that the command "sudo" in a terminal window is telling Ubuntu to do something fundamental (explanation of exactly what would be welcome, but probably outside the scope of this thread - I can Google later), but I don't understand the  "conn@inspiron:~$" part in front of it. 
[LIST]
[*]Is this something specific to a Dell Inspiron? (I have an IBM T42)
[*]Do I need it, or should I just try the two commands from "sudo" onwards? Or is it Linux-speak that I need to include?
[/LIST]

I'm looking forward to a little hand-holding from you guys as I'll be tweaking Ubuntu for only the second time, so thanks in advance.

As an aside, I'm a little surprised that a bug reported in November still appears to be there on a new install. So I'm hoping it is the real problem.

---

### Post by epha on 2009-04-08
hi,
well I don't know much , but I can help you a little bit.

this is the username and computer name of the person who posted-
   conn@inspiron:
ignore it - you should have your own username and computername when you open a terminal window -Applications->Accesories-Terminal

you should type the commands starting with:   sudo

'sudo' means 'superuser do'   superuser is a user with access to the inner workings of the operating system, so to change passwords, add modules, install software and many other things you need to use 'sudo'- you will then be asked for your password.

'rmmod'  removes modules
'modprobe' adds modules

hope that helps,

epha

---

### Post by wiseloki on 2009-04-10
Thanks for the explanation.

I just tried the fix outlined in the bug report, and I got this

> pvs@ibm-t42:~$ sudo rmmod ipw2100 ieee80211_crypt ieee80211_crypt_tkip ieee80211_crypt_ccmp
[sudo] password for pvs: 
ERROR: Module ipw2100 does not exist in /proc/modules
ERROR: Module ieee80211_crypt does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
pvs@ibm-t42:~$ sudo modprobe lbm_cw_ieee80211_crypt_tkip lbm_cw_ieee80211_crypt_ccmp ipw2100
FATAL: Module lbm_cw_ieee80211_crypt_tkip not found.
pvs@ibm-t42:~$ 
pvs@ibm-t42:~$ 

So the bug I found doesn't appear to be my problem, unless I did something wrong when I tried the fix.

Anyone else got any ideas?

---

### Post by wiseloki on 2009-04-11
Apologies for the multiple posts, but I thought I'd update this thread with the latest status.

Yesterday, I changed my WPA passkey to use only lower-case letters and numbers, as that seems to be the format of the scrambled result after I try to log on and review the stored password. Having done this, I was able to connect to my wireless network with no problems. I could plug in and unplug the Ethernet to the same router and the laptop would switch seamlessly between wired and wireless connection.

I shut down and rebooted the laptop and it connected to the wireless. I checked on what passkey the network manager had stored, but it was scrambled and was 64 characters (lower-case alpha-numerics), not the passkey I had entered. But the laptop was still logging in OK. I stopped the router broadcasting the network name and still it found it and logged in.

Today, after the laptop had been shut down overnight, it can't log in again. I've deleted the network and recreated the login several times, but always with the same result - one green light on the "swirly" network symbol then, after a long delay, I get a screen asking for the network passkey. This screen has a passkey already entered which, when I check the "show password" box, is always the **same** 64-character string of lower-case alpha-numerics. I even thought about using this string as my network passkey to see if that would work, but my router has a maximum passkey length of 63 characters.

So I know that the laptop can connect to the wireless network, even using WPA security (it connects no problem with security off but that's just not an option, for obvious reasons). 

The problem seems to relate to the corruption of whatever WPA passkey I enter and it being overwritten with the same 64-character string that the laptop network manager seems to conjure up for itself.

If I knew how to do it, I'd be inclined to delete the network manager and whatever encryption modules it has, then download and reinstall new ones, as that would eleiminate a corrupted module.

Anyone any ideas?

**Update**

I tried WEP (both 64-bit and 128-bit) as an alternative to PSK-PSK but I can't log in that way either, although network manager seemed to remember the key for the 64-bit.

Some help with this would be really, really appreciated. From my noobie messing about, it all seems to revolve around the retention of the passkey by Ubuntu.

---

### Post by Tankerdog2002 on 2009-09-16
I realize this post is months old; however, I had the same problem and the fix was so simple.

[LIST]
[*]Right click the nm applet on your panel.

[*]Choose eidt connections

[*]Click the "Wireless Tab"

[*]High-light your network connection

[*]Click the Edit button on the right side.

[*]In the new window that opens, look at the little box at the bottom left that says "Available to all users".

[*]Check it

[*]Close

[*]Your done
[/LIST]

---

### Post by wiseloki on 2009-12-06
Just for info, I upgraded to 9.10 and this seemed to fix the issue......for a while.

It now looks like I had an unknown and intermittent hardware problem. Issue solved by ditching the T42 and installing Ubuntu on an X60s

Thanks for the advice from all who chipped in

---

