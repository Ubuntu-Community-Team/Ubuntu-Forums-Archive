---
title: "Wireless - enter password for keyring default?"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by germanix on 2010-04-30
After now having installed 10.4 everything runs smooth (thank you all).
The only problem I am experiencing is that when I boot  Ubuntu quickly finds my wireless network but does not automatically connect to it. A window then comes up asking me to "enter password for Keyring default". After having then entered this password the connection does take place and remain stable. So really no big deal but why do I need to do this every time I boot up. This is new to me. Never had anything like this on previous versions.
Can anyone throw some light on this matter and maybe advise how I could fix this?

---

### Post by doas777 on 2010-04-30
well, this is common behavior on any machine with autologin enabled, that uses a stored password for wifi, networkshare, etc.

there are a couple ways to work around it, but they all compromise system security in one way or another, so you might want to ask yourself if entering a password is all that much of a pain (or even better just disable autologin, and just login normally. this will automatically unlock your keyring with your login password. )
most of my systems only get rebooted for the occasional kernel update anyway, so even if i have to put a password in once, it's hardly annoying since it's only once every 3 or 4 weeks.

alternately you can set the keyring password to blank, and it will stop encrypting your passwords. 
[http://ubuntuforums.org/showpost.php?p=6365451&postcount=5](http://ubuntuforums.org/showpost.php?p=6365451&postcount=5)

---

### Post by germanix on 2010-04-30
Thank you very much for this advice. Even though in my case system security is not really an issue i will surely give it some more thought before I just change things. Was strange though that I only get this issue now with 10.4. I have always had auto login enabled but never had to enter a password for the keyring. But it is no big deal as you say, I can live with it.
Thanks again and have a good day.

---

### Post by germanix on 2010-05-05
> **doas777 said:**
> well, this is common behavior on any machine with autologin enabled, that uses a stored password for wifi, networkshare, etc.

there are a couple ways to work around it, but they all compromise system security in one way or another, so you might want to ask yourself if entering a password is all that much of a pain (or even better just disable autologin, and just login normally. this will automatically unlock your keyring with your login password. )
most of my systems only get rebooted for the occasional kernel update anyway, so even if i have to put a password in once, it's hardly annoying since it's only once every 3 or 4 weeks.

alternately you can set the keyring password to blank, and it will stop encrypting your passwords. 
[http://ubuntuforums.org/showpost.php?p=6365451&postcount=5](http://ubuntuforums.org/showpost.php?p=6365451&postcount=5)

I have now disabled the auto login expecting that this will automatically unlock the keyring as you explained above. This however does not happen. Even after logging in  I still have to give my password again before I can connect to the internet. Also I am using a laptop and do not leave it on all the time as i travel with it. So it does become a pain to have to enter the password every time I start the computer (more times per day)
S I would still like to know how to solve this problem please.

---

### Post by caffemisto on 2010-07-02
Hi,
 
I know this thread is almost a month old, but it came up when I was searching for solution to the same issue.
 
The instructions given had an unnecessary extra step and it didn't mention one more setting that needs to be set to blank as well.
 
To set autologin for default keyring:
 
Click 'Applications', go to 'Accessories', and click 'Passwords and Encryption Keys'
 
No need to go to 'Edit' then 'Preferences' <-- that's the extra step
 
Right-click 'Passwords: login', click 'Unlock', enter your current password
Right-click 'Passwords: login' again, then click 'Change Password'
 
Enter the current password in the first field, leave new and confirm blank, click OK
 
Confirm use of unsecure options.
 
You're done with 'Passwords: login'.  However, there is one more option in there, at least in my laptop there is:  'Passwords: default'
 
So you have to repeat the above steps for every entry in your 'Passwords and Encryption Keys'.
 
I gave it some thought while unlocking my digital life on the laptop and decided to disable Auto Login as suggested above.
 
Why?  'Passwords: default' contains passwords used in browser, wireless access points, Ubuntu One, and Gwibber to name a few.
 
Now I understand why Dell insists that Linux is more secured than Windows.
 
:guitar:

---

### Post by robelin on 2010-12-19
I am not 100% sure it works all the time, but here is how I got around this problem:
- Go to System > Preferences > Network Connections > Wireless
- Select the wireless network you would like to connect to without having to unlock the keyring password and click "Edit"
[ you need to authenticate ]
- Check the "Available to all users" box and click "Apply..."
You will need to repeat this for each wireless network you would like to connect to automatically.
This works for me in 10.11 and I think I remember it worked in 10.04 as well.

---

