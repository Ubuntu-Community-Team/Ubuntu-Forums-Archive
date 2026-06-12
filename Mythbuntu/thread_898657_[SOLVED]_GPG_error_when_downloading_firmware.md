---
title: "[SOLVED] GPG error when downloading firmware"
date: 2008-08-23
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-23
I received the following error when trying to update my b43-firmware from the this link [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/) using 'sudo aptitude update' after putting the two lines of code in /etc/apt/sources.list as this link instructs.[INDENT]GPG error: [http://ubuntu.cafuego.net/dists/hardy-cafuego](http://ubuntu.cafuego.net/dists/hardy-cafuego) Release: The following signatures couldn't be verified because public key is not available: NO_PUBKEY 81600957AF425CB5
You may want to run apt-get update to correct these problems.

[/INDENT]I also tried 'sudo apt-get update' as the error message suggested and received the same error.

Does anyone know why links like this are posted with problems like this and how I can resolve this problem. I have been trying for weeks to get this Buffalo wireless card to work.

Regards,

dmdbdd

---

### Post by Francisuk on 2008-08-24
Hi
Dunno if you solved this, but I had the same problem, you need to add the key provided on [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/)  (click on the 'key' -> AF425CB5 ) and save the page as 'cafuego.gpg'.
Then from the prompt:
```
sudo apt-key add cafuego.gpg
``` 
Then you should be able to update:
```
sudo apt-get update
``` 
This should work!

---

