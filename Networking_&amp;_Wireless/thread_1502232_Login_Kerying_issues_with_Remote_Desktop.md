---
title: "Login Kerying issues with Remote Desktop"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by ubun2warrior on 2010-06-05
Hi 


 I have three pc's and i have enabled remote desktop in two of them and also configured them such that the person sitting on those particular pc's don't have to authenticate my remotely accessing them. Also those two pc's automatically login(i.e. without authentication)

Now coming to the problem part 
Now when i try to access the desktops remotely this the message that comes on the two pc's which i want to access remotely.
"[I]Login keyring did not get unlocked when you logged into your computer"
[/I]So the whole purpose of my accessing the pc's remotely without them interfering in the process remains unfullfilled.

Please help me out with this. I feel there is some problem with the pc's automatically being logged in and the login keyring not being unlocked....
So if there is a way to get the login keyring unlocked as soon as i log in(note: the pc's being remotely accessed do not have to authenticate...)

---

### Post by ubun2warrior on 2010-09-19
actually the problem is solved when i enable the login prompt, that unlocks the keyring at startup and then i am able to use vnc viewer without the user knowing they are being monitored..

---

### Post by tombert on 2010-10-19
I would like to bump this thread - having similar issue ... but my computer runs as server in the shelf ... so I need to automatically login ... using VNC with password then makes no sense cause I do not have the chance of entering the keyring password ...
looks like a design error to me ...

thx

---

### Post by okorkie on 2010-10-19
ubun2warrior, I am receiving the same error when attempting to remote desktop to my Ubuntu 10.10 PC for the first time after the PC is booted up.  I receive the "The login keyring did not get unlocked when you logged into your computer" error as well.

I have the login prompt disabled at bootup (logs right into the desktop without having to enter a password upon bootup).

Have you found another solution without having enable the login prompt?

Thanks

---

### Post by tombert on 2010-10-20
I found a workaround running

gnome-screensaver-command --lock

in the .profile

Then disable the VNC password - so you always have to login into the screensaver - similar to having a VNC password.

---

### Post by Freaky#Funga on 2010-12-12
I think someone found a way better workaround:

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423/comments/11]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423/comments/11")

This contains:
> 
Open up Applications->Accessories->Passwords and Encryption Keys

Right click Passwords:login and unlock it.

You should be able to expand the tree and find a listing for vino. Right click and delete it.

Close Passwords and Encryption Keys.

Open gconf-editor as and navigate to /desktop/gnome/remote_access

Enter in your BASE64 encoded password into the vnc_password key.

Save the config and close the editor.

Reboot and you can now use your VNC client to connect to your machine without being first prompted with the keyring.

Base64 encoder could be found here
[http://www.motobit.com/util/base64-decoder-encoder.asp]("http://www.motobit.com/util/base64-decoder-encoder.asp")

---

### Post by papu40000 on 2011-08-01
OK, this works Freaky#Funga

But... you know that the key is encoded in BASE64 and if you want, you can decode it. Where is the security?

---

### Post by Cue2 on 2011-08-22
> **papu40000 said:**
> OK, this works Freaky#Funga

But... you know that the key is encoded in BASE64 and if you want, you can decode it. Where is the security?

This workaround doesn't even work in 11.04. Just keeps complaining about an unkown authentication failure. This stupid bug has been around since 2007, I don't understand why it hasn't been addressed yet.

---

