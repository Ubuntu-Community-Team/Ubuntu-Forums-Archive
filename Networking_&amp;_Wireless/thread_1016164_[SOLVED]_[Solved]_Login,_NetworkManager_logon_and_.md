---
title: "[SOLVED] [Solved] Login, NetworkManager logon and unlocking encrypted /home -  all in"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by korpenkraxar on 2008-12-19
Hi!

I run Ubuntu 8.10 on a Thinkpad. As many other laptop users I've been struggling with getting the unholy boot-up triad of unlocking my encrypted /home partition, auto-logging in and having NetworkManager to automatically connect to my protected home wifi network to do the right thing, namely only requiring me to give my passphrase once during the whole process. I just cant stand typing a password more than once each time I boot the laptop.

Getting NetworkManager to automatically open the default keyring where it stores wifi passwords while using auto-login in GDM is tricky if not impossible (?) judging from the various bug reports and fairly cryptic config-file editing found here in the forums and on Launchpad and Google.

My solution up until today was this:

[LIST=1]
[*]Have Ubuntu ask for the /home disk encryption key early while booting by having the details about this partition specified in /etc/crypttab and /etc/fstab
[*]Use auto-login in GDM
[*]Uninstall NetworkManager and use wicd instead (which is a fine network-manager but I lately ran into problems with automatically reconnecting after resuming from suspend) as it does not need to access any external keyrings and can auto-connect using the internally stored password.
[/LIST]

However, since I will soon need to use the Mobile Broadband features in NetworkManager I went googling for a while and came across this wonderful guide to /home encryption and a solution to the unlock-login-NetworkManager problem:
[http://pupeno.com/blog/encrypted-home-in-ubuntu-8-10?set_language=es](http://pupeno.com/blog/encrypted-home-in-ubuntu-8-10?set_language=es)

I you are a laptop-user and the my scenario applies to you too, the simple solution above might be for you too.

It assumes that you are using the same passphrase/key to unlock the drive (not necessarily the same you used when you encrypt it since you can have multiple keys) as you do when you login and unlock the keyring for NetworkManger. You can add new disk unlocking keys using **cryptsetup** (see link above) and change the keyring password using **seahorse** to synchronize them if they are not already the same.

Now I can instead use this scenario:

* Follow guide to configure automagic mounting
* Comment out info about encrypted /home in /etc/crypttab and /etc/fstab (if you had any)

[LIST=1]
[*]Turn off auto-login and use your password to log in at the GDM screen. PAM automatically unlocks and mounts your disk and unlocks the keyring for NetworkManager
[/LIST]

At least for me, this is exactly like it should be. Enjoy. :-)

---

