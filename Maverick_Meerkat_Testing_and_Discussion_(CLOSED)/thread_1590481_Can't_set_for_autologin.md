---
title: "Can't set for autologin"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by red_hax0r on 2010-10-07
I checked to see if this problem was already mentioned, but on the amd64 Maverick Ubuntu, autologin is set in the dialog, but it doesn't work.  Don't know if this is universal.

---

### Post by ronacc on 2010-10-07
did you set it during install or using system>administration>login window ? I have 3 amd64 maverick installs and auto login works on all of them . I always set my login for password required during install and then change it on first boot to auto ( with a short delay) using the system menu .

---

### Post by cariboo on 2010-10-08
Check to see if you have a custom.conf file in /etc/gdm it should look something like this:

```
cat custom.conf

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=cariboo
AutomaticLogin=cariboo
TimedLoginDelay=30
DefaultSession=gnome
```

---

### Post by red_hax0r on 2010-10-08
the 'AutomaticLogin' variable was unset, but the 'AutomaticLoginEnable' variable was true.  Don't know why this was.

---

### Post by red_hax0r on 2010-10-08
I tried setting the values in the configuration file manually, but it gave me errors about not being able to find my Desktop and .nautilus directories, but they're there.  I have to go to a root shell and reset the variable to blank again.  

I'm using the iso off the website, so I don't know if anyone is using a more recent version.

---

