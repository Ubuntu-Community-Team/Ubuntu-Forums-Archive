---
title: "Wireless connect fails at WEP key"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by hertfordkc on 2010-10-19
Dell mini 10 with ubuntu 10.04/windows xp, connecting to linksys wrt54g.  Connected when I was using 9.10, has worked for several months since 10.04 was installed.  Still works if I boot XP, but, when booting Ubuntu, router won't accept the passkey which I obtained from my wired computer.  I've glanced through a bunch of posts and see several which are close, but no solution.  
Only cause that I can think of might be a shut down while connected.  I say that because it was working and I had no need to change settings.
Thanks for your suggestions and patience with noobs.
Hertfordkc

---

### Post by bigfootnmd on 2010-10-19
Keys used for WEP or for that matter WPA also, must be an exact match between the router and the PC.

I've been using Ubuntu and WIFI for two years.  Sometimes for whatever reason my Ubuntu Netbook would "forget" the WEP key. Or I would forget it. My WEP key was in HEX this can really be a problem.  If you WEP key is in hex and you mess up just one character it will not work.  Also, WEP Keys in HEX are very long.

So,  I am assuming that you can connect your laptop using an Ethernet cable.  Can you also connect to your router's control page and go to wireless eettings where your WEP key is visible?

1.  Open up the GEDIT text editor.

2. Go to your router's control page, wireless settings and highlight the key and copy the key.

3.  Paste the KEY into the GEDIT and then save the file to your desktop.  

4.  Click on the Network manager or WICD and choose EDIT connections.  Choose your home WIFI connection and go to wireless.  Now, PASTE the key in.  Verify that it matches what your router has.  From now on you never have to type the key again.

5.  Try your WIFI connection again.

---

### Post by hertfordkc on 2010-10-19
> **bigfootnmd said:**
> Keys used for WEP or for that matter WPA also, must be an exact match between the router and the PC.

I've been using Ubuntu and WIFI for two years.  Sometimes for whatever reason my Ubuntu Netbook would "forget" the WEP key. Or I would forget it. My WEP key was in HEX this can really be a problem.  If you WEP key is in hex and you mess up just one character it will not work.  Also, WEP Keys in HEX are very long.

So,  I am assuming that you can connect your laptop using an Ethernet cable.  Can you also connect to your router's control page and go to wireless eettings where your WEP key is visible?

1.  Open up the GEDIT text editor.

2. Go to your router's control page, wireless settings and highlight the key and copy the key.

3.  Paste the KEY into the GEDIT and then save the file to your desktop.  

4.  Click on the Network manager or WICD and choose EDIT connections.  Choose your home WIFI connection and go to wireless.  Now, PASTE the key in.  Verify that it matches what your router has.  From now on you never have to type the key again.

5.  Try your WIFI connection again.

Thanks for your suggestion.
I have copied the WEP passkey to a txt file on a USB drive on my wired desktop, then put the USB drive on the NetBook and copied the passkey into the authentication field.  It doesn't matter whether I manually enter the passkey or copy it, a message comes back saying the passkey isn't recognized. 
Is there some reason why a direct connection might work when the copy and paste wouldn't? 
I've tried some diagnostics suggested in other posts and haven't stumbled onto anything that suggests where the problem might be... or I'm totally clueless in reading the results.  I've worked with computers for about 40 years and I don't give up easily.  However, I'm relatively new to Ubuntu and wireless, so I'm not making much progress.

---

### Post by SeijiSensei on 2010-10-19
First, if it's your own network where you control all the systems, consider migrating to WPA2 Personal.  It's considerably more secure than WEP.  Some older network devices don't do well with WPA2, but, if yours all support it, it's worth trying.

Second, have you tried all the "flavors" of WEP available?  Under standard WEP, Kubuntu 10.10 offers me both a 128-bit-only version and a 64/128-bit alternative.  I've had to try both of those to find the right one.  There's also something called "Dynamic WEP" in the Connection Manager; I have no idea what that is.

---

### Post by hertfordkc on 2010-10-20
> **SeijiSensei said:**
> First, if it's your own network where you control all the systems, consider migrating to WPA2 Personal.  It's considerably more secure than WEP.  Some older network devices don't do well with WPA2, but, if yours all support it, it's worth trying.

Second, have you tried all the "flavors" of WEP available?  Under standard WEP, Kubuntu 10.10 offers me both a 128-bit-only version and a 64/128-bit alternative.  I've had to try both of those to find the right one.  There's also something called "Dynamic WEP" in the Connection Manager; I have no idea what that is.
:)   Rock on.
Changed to WPA2 Personal apparently fixed everything.  I'll hold my breath to see if wireless mysteriously fails again.
Why would Ubuntu 9.10 work flawlessly with WEP for a year or more, and 10.04 work for a while, then croak?  Did the drivers supplied with 10.04 deprecate WEP?
Thank you for your suggestion.  I was about to try some of the driver changes suggested in other threads.  That prospect was giving me a migraine.

---

### Post by putt1ck on 2010-11-18
For anyone experiencing an issue where you don't have control of the access point (me, I'm in a Best Hotel...), the answer for me was to change the type of the key. 

By default Kubuntu assumes a 128bit passphrase, but older APs will only be 64bit - change to the 64/128-bit alternative and re-enter the WEP key given. The clue for me was that Kubuntu occasionally came back and asked for the secret again, and each time it had changed to the 64/128-bit alternative, presenting the key in hex form. I tried switching it back to 128bit a few times before this thread helped the penny drop...

:D

---

