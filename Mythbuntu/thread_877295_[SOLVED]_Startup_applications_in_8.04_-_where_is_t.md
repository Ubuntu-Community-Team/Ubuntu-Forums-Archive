---
title: "[SOLVED] Startup applications in 8.04 - where is the tab?"
date: 2008-08-01
forum: Mythbuntu
---

### Post by menny on 2008-08-01
Hi,
In 7.10 there was a "Startup applications" tab in the Sessions settings dialog. It is not there anymore (check the screenshot).
Where can I find it?
My system starts MythTV and Azureus (since I configured it in 7.10), but I want to add additional applications and remove Azureus, and can't.

Please help.

Also, when I press "Quit"->"Reboot", the system does not reboot, instead it goes to the login screen and after 30 seconds re-login.
What with this? This is a new behavior.

Thanks.

---

### Post by funkydan2 on 2008-08-02
I'm not sure how to do this graphically, but there is a directory ~/.config/autostart which contains links to applications you want autostarted on login.

---

### Post by menny on 2008-08-02
Thanks funkydan2.
It does include the applications which starts up.

Also, I've found an autostart @ '/usr/bin/xfce4-autostart-editor'.
It shows additional applications which do are in the '.config/autostart' folder.

Thanks.

---

