---
title: "Save Desktop Settings?"
date: 2009-03-22
forum: Mythbuntu
---

### Post by Nobodyspeshul on 2009-03-22
Stupid question here, but how can I save the desktop settings on mythbuntu so that every time I restart I don't have to exit the frontend and resize the window to then again restart the frontend.

Also, I've got a wireless card installed and operating normally, but every time I restart I have to enter the password to tell it to connect.

Thanks for your help, I'm getting better!

---

### Post by Nobodyspeshul on 2009-03-22
Ok, I found out what I needed to do.

Had to run gksudo nvidia-settings from a terminal and it opened up the nvidia window with root access.

Any ideas on the wireless password now?

---

### Post by Nobodyspeshul on 2009-03-23
Bumping, still looking how to have the wireless auto connect on startup.

---

### Post by newlinux on 2009-03-23
My wireless autoconnects at startup... Are you getting asked for your wireless password or a keyring password?

---

### Post by newlinux on 2009-03-23
I guess I could just assume. If it is in fact your keyring password that gets asked for, this is because it is different from your logon password or you are using automatic login. If you don't use automatic login then you can simply change your keyring password to be the same as your login password. If you use automatic login, you will want to make you keyring password blank to avoid this.

1. Open Applications/Accessories/Passwords and Encryption keys.
2. Go to Edit/Preferences.
3. On the password Keyrings-tab select the "login"-keyring and click "Change Unlock Password"

---

### Post by Nobodyspeshul on 2009-03-24
Well, I tried doing that Newlinux and couldn't figure it out, but I did do some searches about changing the keyring password and came across this little gem right here.

```
rm ~/.gnome2/keyrings/default.keyring
```

This did it for me, it deleted the WPA protection and the keyring password so when I logged in next all I had to do was put in my wireless password and I was in.

Thanks for the help though, never would have thought about the keyring password without your help.

I appreciate it!

---

