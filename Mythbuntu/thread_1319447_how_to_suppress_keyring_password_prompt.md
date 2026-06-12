---
title: "how to suppress keyring password prompt"
date: 2009-11-08
forum: Mythbuntu
---

### Post by x17y19 on 2009-11-08
Hi,

How do I suppress the keyring password prompt which appears every time
I boot up ?

I'm running Mythbuntu 9.10 with autologin enabled on a box that has only
wireless (no network cable).

Some posts (e.g. [http://ubuntuforums.org/archive/index.php/t-1101618.html](http://ubuntuforums.org/archive/index.php/t-1101618.html))
suggest changing settings at System -> Preferences -> Network Configuration
but I don't see that menu/option on my box.

Thanks for any help.

---

### Post by KillerKiwi on 2009-11-08
Press Alt-F2

Type in "seahorse-preferences" and run

now select the "login" keyring and change the unlock password to match your login password.

If you dont care about encrypting the passwords on your box...
Reset the password on your key ring to be empty

---

### Post by x17y19 on 2009-11-20
Thanks but I do not have seahorse installed. Is there some other way to configure
NetworkManager and/or keyring ?

Thanks.

---

