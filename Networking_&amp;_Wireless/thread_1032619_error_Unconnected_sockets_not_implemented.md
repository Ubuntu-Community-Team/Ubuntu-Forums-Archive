---
title: "error: Unconnected sockets not implemented"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by anilp on 2009-01-06
I am on ubuntu 8.10/eclipse 3.4.1 and get this error message:

No repository found at [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/).
No repository found at [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)
  Error reading update site [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/).
  Unconnected sockets not implemented

(I am posting here because the error seems to be on ubuntu - the plugin downloads ok from Windows)

was trying to follow these steps for eclipse 3.4: ([http://code.google.com/android/intro/installing.html#installingplugin](http://code.google.com/android/intro/installing.html#installingplugin))
   1.  Start Eclipse, then select Help > Software Updates....
   2. In the dialog that appears, click the Available Software tab.
   3. Click Add Site...
   4. Enter this as the Location:

      [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)

      Click OK.
   5. Back in the Available Software view, you should see the plugin. Select the checkbox next to Developer Tools and click Install...
   6. On the subsequent Install window, "Android Developer Tools", and "Android Editors" should both be checked. The Android Editors feature is optional, but recommended. If you choose to install it, you need the WST plugin mentioned earlier in this page.
      Click Finish.
   7. Restart Eclipse.


thanks,
Anil

---

### Post by anilp on 2009-01-07
removing the https and using http made it work.

---

