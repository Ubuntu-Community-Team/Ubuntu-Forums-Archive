---
title: "Incorrect email and or password when attempting to install vlc"
date: 2016-12-13
forum: Multimedia Software
---

### Post by thedoctor818772 on 2016-12-13
Good Morning,

I am trying to install VLC on my machine which is an Aspire M laptop running Ubuntu 16.10. Upon being asked my email I enter my email: <snipped email address, and upon being asked my password I enter my password which is: <snipped password>. However, I get the message that the password and/or email is incorrect. But when I attempt to reset the password and reset it to the above password and retry I still get the same message. 

First of all this may not be the correct sub-forum. If not, can someone please direct me to the correct one to solve my issue? Secondly, How can I solve this?

Thanks!

---

### Post by SeijiSensei on 2016-12-13
Are you installing the copy of VLC that is in the Ubuntu repositories?  You shouldn't need any email or password for that.

```

sudo apt-get update
sudo apt-get install vlc

```

Personally, I prefer SMPlayer with mpv as the player engine.  It's also in the repos.

---

### Post by howefield on 2016-12-13
Sounds like you are trying to install the VLC snap package which would need logging in to the store with your SSO login details rather than the .deb package which would install straight from the repository. There is currently a bug preventing installing snaps from the Software Centre.

I'd suspect that you are looking for the normal .deb package in which case the answer above will get you there but if it is the snap package you want post back.

---

### Post by thedoctor818772 on 2016-12-13
OK Thanks for that reply. When I use the terminal all is well! Thanks again. Yes I was trying to use the snap package.

---

### Post by howefield on 2016-12-13
> **thedoctor818772 said:**
> OK Thanks for that reply. When I use the terminal all is well! Thanks again. Yes I was trying to use the snap package.

Best to use the terminal to install snap packages until the bug is fixed that prevents using the Software Centre for it, eg

```
sudo snap login xxxxxxxx@xxxxx.com
[sudo] password for hugh: 
Password: 
Login successful
snap install vlc
vlc (stable) daily from 'videolan' installed
```

After using the sudo snap login command you may be asked for your sudo password and then your SSO login password, easy to get confused ;)

---

