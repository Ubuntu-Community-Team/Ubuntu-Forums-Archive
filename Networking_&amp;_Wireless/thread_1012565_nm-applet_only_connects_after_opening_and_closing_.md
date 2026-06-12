---
title: "nm-applet only connects after opening and closing dialog"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by splitpane on 2008-12-16
Hello,

I have searched and not found a solution to this problem, which is happening on my wife's laptop.  She's running 8.10 and wifi worked fine.  Then at some point recently it stopped connecting at login.  If I right-click on the nm-applet icon in the taskbar and select "edit connections" and then go to the wireless tab, select my connection (I've named it "home") and click edit, then click OK, without doing anything, the connection will start fine.

But if I don't go in and open the dialog, it won't connect.  Left clicking on the nm-applet and selecting the ssid of my network just pops up a message that my connection has been lost (though it wasn't there in the first place).

AT onepoint I removed nm-applet from the taskbar by accident and then added it back.  It shows under System->Preferences->Sessions as starting and the command is "nm-applet -sm-disable" which all seems fine.  

Any suggestions for how to troubleshoot?

One thing I did notice when I started nm-applet from the command line was that it gave errors when starting about no connections found, and then later about not having a valid encryption key.  But these seem to be inaccurate, because it can in fact connect if I just open and close the dialog.

Thanks in advance for any suggestions.

---

