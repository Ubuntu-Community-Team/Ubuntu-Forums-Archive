---
title: "Easy fix for the hex in password box for WPA2 bug"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by epicoder on 2009-07-18
Launch seahorse, go to the passwords tab and deny NetworkManager (nm-connection-editor) write and delete access. Each time NM tries to change the password, Ubuntu will stop it and ask if you want to grant it permission. ALWAYS click deny, and use seahorse to change your password.

---

