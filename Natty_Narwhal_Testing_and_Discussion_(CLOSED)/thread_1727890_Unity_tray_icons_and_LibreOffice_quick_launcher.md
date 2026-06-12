---
title: "Unity tray icons and LibreOffice quick launcher"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-13
This is kind of an odd problem. I use OpenOffice with the quick launcher. In 10.10 there is a bug (not in 10.04) , which is that when the quick launcher is activated, sometimes you can't shut down or restart the computer. It is only mildly annoying because in 10.10.  I can always quit the quick launcher by clicking the tray icon before I shut down or reboot. But guess what, there are NO tray icons in Unity! (part of the new "non desktop metaphor" ??) So I couldn't shut down the computer because I couldn't quit the quick launcher, I had to open Libreoffice and uncheck the box for the quick launcher just so that I could shut down.

---

### Post by ankspo71 on 2011-04-13
Hi,
See if you can add LibreOffice to the whitelist as seen on this link:
[http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/)
Remember that when you add something to the whitelist, you also have to re-add the existing applications in the whitelist.

As far as what to add to the whitelist, I wouldn't know, so run the command 'top' in the terminal to see what name is shown running for LibreOffice while it is supposed to be running in the tray.

Hope this helps.

---

### Post by beew on 2011-04-13
> **ankspo71 said:**
> Hi,
See if you can add LibreOffice to the whitelist as seen on this link:
[http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/)
Remember that when you add something to the whitelist, you also have to re-add the existing applications in the whitelist.

As far as what to add to the whitelist, I wouldn't know, so run the command 'top' in the terminal to see what name is shown running for LibreOffice while it is supposed to be running in the tray.

Hope this helps.

Thanks. Just read the link. I can't believe that you have to go through such obscure means to have something shows up as a tray icon. Why don't they have a blacklist instead? Most thing should show. Is this another brilliant design to make Unity attractive to the non existent "average user" (TM) who may get confused by too many things on the panel??

---

