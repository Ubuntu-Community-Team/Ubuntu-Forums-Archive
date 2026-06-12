---
title: "Unlock login keyring"
date: 2010-09-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by clive littlewood on 2010-09-17
Hi All

I've got a good one this morning and would love your thoughts.

Each time I start a session (I'm on auto login) and reach the desktop, then open any app, I am asked for my password to unlock the login keyring.

If I ignore the request or just cancel I can then just carry on as normal.

Any Ideas

Clive

---

### Post by Mr. Picklesworth on 2010-09-17
Are you connecting to a wireless network?

The keyring is encrypted using your login password. The only way to get the stored passwords back out is by entering your password. So, it can either do this automatically via PAM (so it uses your password if you type it at the first login screen), or it needs to ask you.

If you don't care about encrypting that stuff, you can remove the keyring password, which will make everything unencrypted and get rid of that password screen. Open up the Passwords and Encryption Keys tool (seahorse), and under the Passwords section you get a list with your keyrings. You probably just have the one, called &#8220;login.&#8221;
Right click it, choose Change Password, and enter nothing for the new password.

This definitely isn't new behaviour, although it is a little strange that it's asking to be unlocked only after you open an application. If you can find some more detail on that (is it definitely *any* application?), it would probably be helpful :)

---

