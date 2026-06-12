---
title: "Net manager and keyring problem."
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by Pancho Pistolas on 2010-01-11
Hello everyone. I know this is a common thread, and sometimes it is solved. But I will give the best and easiest solution to the problem "My network manager asks for keyring password when I logon" just in one piece, so you do not have to look for it anymore on forums.

Ok, here we go. Once you have logged in on your session and typed in the keyring password when network manager asks for it, go for your network icon (the one with the signal bars) and right click on it. Select "Edit networks..." (or something like that, actually I use Ubuntu in spanish 'cause I'm from Mexico). Once there, go to the "Wireless" tab and select the network you usually connect to. Click on "Edit..." and at the bottom of the window activate the option that makes it available for all users. Click apply, type the password if it asks for it and you're done. It will never ask for keyring password at login anymore.

I hope it helps a lot of users to avoid long searches and stop downloading some apps that "make it easier".

---

### Post by ngolian on 2010-01-11
If the "all users" option didn't get mentioned before it's probably because it didn't appear until well after this thread was started. And didn't work until even more recently :-P.

---

### Post by NTL2009 on 2010-01-19
Well, this sure seems like it should work, thanks for posting it, but I keep going in circles with it. When I do this, after a reboot it does skip the the keyring request, but it also does not connect. When I right-click "edit connections", I get a new connection name ( "Auto " & <*my SSID*> ) in addition to my original connection name -  and it won't connect. 

I make some progress if I de-select "Make Available to all" from <my_connection_name>, and make sure that the passphrase and "connect Automatically are set in that one. But on re-boot, it seems to go through one unsuccessful attempt to access the wireless network (DISCONNECTED" message), and then succeeds on a second attempt.

I see that when I set the <my_connection_name> to  " Available to all users", it loses the passphrase, but I am able to connect eventually. If I de-select " Available to all users", I'm back to entering the keyring. I'm guessing it tries on the first, and then connects on the second (Auto)?


SUMMARY - in "NETWORK CONNECTION", the  (apparently) "auto generated "Auto <SSID>" set to:

    Connect Automatically
    Available to all users
    WEP 128 passphrase is set. 


   And the <my_connection_name> is set to:

    Connect Automatically
    Available to all users
    WEP 128 passphrase is NO LONGER SET???? It seems to get wiped out after a reboot?

But it 'works' after a fashion. just seems to go through two cycles. It now shows the "Auto<SSID>" as the "default" in "Connection Information".

Seems like any other combo either does not connect at all, or asks for keyring. And yes, it asks me for my admin PW to make these changes to the connections.

I'm pretty new to all this, just getting my feet wet, but have been very impressed with much of what I see in Ubuntu. This is just a nag though, that seems like it should work. I had this similar issue in 9.4 NBR, this is a clean install of 9.10 desktop on my eeePC901 (4GB/16GB SSD).

Maybe there is a config file or something somewhere I should look at or trash and let be rebuilt?

TIA

---

### Post by Slates on 2010-02-10
Fantastic. Thanks for the posting. Works a treat (Ubuntu 9.10).

---

