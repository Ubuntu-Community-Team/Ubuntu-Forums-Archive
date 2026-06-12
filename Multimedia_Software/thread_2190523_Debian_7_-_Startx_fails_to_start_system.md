---
title: "Debian 7 - Startx fails to start system"
date: 2013-11-27
forum: Multimedia Software
---

### Post by darkloader on 2013-11-27
When I boot into the second primary boot loader, I get to the text based console to boot when I type 'startx'. The screen loads, and goes black for 10 seconds. Then when it loads a white screen appears with a computer monitor an sad face on it. Under it, it says

    "Oh no! Something has gone wrong"
    A problem has occurred and the system can't recover. Please log out and try again

When I click the logout button in the console it reports the errors as follows:

    X.Org X Server 1.12.4
    Release Date: 2012-08-27
    X Protocol Version 11, revision 0
    build operating system: Linux 3.2.0-4-amd64 x86_64 Debian
    ....
    The XKEYBOARD Keypmap compiler (xkbcomp) reports:
    > warning:  compat map for group 2 redefined
    > using new definition
    > warning:  compat map for group 3 redefined
    > using new definition
    > warning:  compat map for group 4 redefined
    > using new definition
    Errors from xkbcomp are not fatal to the X server
    xinit: connection to X server lost

    Waiting for X server to shut down server terminated successfully (0). closing the file

Does anyone know how I can successfully boot into my operating system with startx and avoid getting these errors? Any help is appreciated!

Cheers

---

### Post by rackit on 2013-11-28
Here is a thread with the same issue on arch linux - maybe this will get you moving tin the right direction: [http://is.gd/TgXuAr](http://is.gd/TgXuAr)

---

