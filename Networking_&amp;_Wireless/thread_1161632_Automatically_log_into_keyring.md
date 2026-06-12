---
title: "Automatically log into keyring"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by Mouser58907 on 2009-05-16
Hey guys, I've tried googling to solve this one but I'm still a pretty big noob, though I'm learning to love ubuntu more and more. I have auto-login enabled and want it to automatically log into the wireless instead of having to type in my keyring password.

Thanks in advance.

---

### Post by Mouser58907 on 2009-05-17
Bump, come on, I know its a noob question but should be a quick answer I would think.

---

### Post by Brandon Williams on 2009-05-17
You will have to clear the keyring password if you want this to work. If that's an acceptable solution for you, then you're good. Otherwise, you'll have to continue entering the password.

I have a faint recollection of a bug about this in launchpad that suggests a workaround for users who don't want to use an empty password. Try searching for bugs related to gnome-keyring and autologin in launchpad.

The "bug" is unlikely to be fixed, because the gnome developers do not consider it to be a bug. They don't like the security implications of automatically ignoring the keyring password when it is set, since this would allow a local user to circumvent keyring security with a simple reboot. I agree with them, but there are a lot of people who don't.

---

### Post by Mouser58907 on 2009-05-17
Oh! So I can leave the password fields blank and hit Enter, I tried hitting cancel and it made me re-enter. Man that seems so obvious, I'll give it a quick try thanks!

-edit-
Worked like a charm, thanks.

---

