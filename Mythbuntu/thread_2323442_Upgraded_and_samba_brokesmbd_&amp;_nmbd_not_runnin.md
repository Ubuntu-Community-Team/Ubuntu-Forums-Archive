---
title: "Upgraded and samba broke:smbd &amp; nmbd not running..."
date: 2016-05-05
forum: Mythbuntu
---

### Post by dibuntux on 2016-05-05
a week ago...just did a standard upgrade of packages as usual, including samba, and samba stopped working. smbd & nmbd not running...
System has been working for years, 14.04 lts...any ideas?

---

### Post by T.J. on 2016-05-05
> **dibuntux said:**
> a week ago...just did a standard upgrade of packages as usual, including samba, and samba stopped working. smbd & nmbd not running...
System has been working for years, 14.04 lts...any ideas?


Did you: 
[LIST=1]
[*]Check to make sure your previous Samba configuration is still intact?  It's  /etc/samba/smb.conf.
[*]Make sure that Samba is enabled on startup?
[/LIST]




This will ensure it starts up on boot. After checking the /etc/samba/smb.conf, checking bootup and then rebooting -  you should be all set.   I would also make sure to check the passwords on your shares and use *smbpasswd* command to reset them as needed.

If that doesn't work, I suggest you look in the logs (possibly  /var/log/samba or /var/log/smb) to see if your system is configured for logging errors.

---

### Post by dibuntux on 2016-05-06
THanks TJ for the repyl, btw I love cats..., I did not upgraded the systemo to 16.04, still on 14.04, just normal package upgrades, which included samba...everything else is working, I can use mythweb and control the machine via VNC...samba config is the same...it is just that you cannot start samba: if I do a sudo service samba start still does not work...smbd & nmbd not running. Even if I try to start each service separately...IN samba logs I got nothing becouse it does not start...

---

### Post by Morbius1 on 2016-05-06
Just a guess here but run the following command:
```
testparm -s
```
If it comes back with something like this:
> tester1@vub1404:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: Ignoring invalid value 'share' for parameter 'security'
Error loading services.
Edit /etc/samba/smb.conf, find the line "security = share", and remove it. Save the file and see if you can start smbd.

[COLOR=#0000cd][I]Samba deprecated share level security about 45 years ago ( I may be a little off on the time period ). In the past Samba would silently replace "share" with "user" because it assumed the user never got the memo on this but after the recent update it stops it from running - eventually. It will start it but then it eventually dies:
> tester1@vub1404:~$ sudo service smbd status
smbd stop/waiting
tester1@vub1404:~$ sudo service smbd start
smbd start/running, process 3632
tester1@vub1404:~$ sudo service smbd status
smbd stop/waiting
[/I][/COLOR]

---

### Post by dibuntux on 2016-05-06
...well...thanks a lot! That did it...I also had logging = 0, for which I got a warning from testparms, saying also was depracated...
I was not able to browse share...getting this message from client:

Unhandled error message: Failed to retrieve share list from server: Connection refused

So...after a small search I found a suggestion to add  to smb.conf the line:

name resolve order = bcast host

Restart of the server...and was OK like always before...

Thank you so much, thanks everybody and hopes this will be valuable to others in the future...

PS: just one thing - upgrading and getting no samba networking on a machine that was up for years it is not really neat for ubuntu...in general...

---

