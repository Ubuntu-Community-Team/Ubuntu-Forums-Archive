---
title: "Clear &quot;Work Offline&quot; checkbox in Firefox"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by Jeff Root on 2012-01-27
I just installed Maverick Meerkat, which comes with
Firefox 3.6.10.  I have a dial-up connection, which
does not depend on Ubuntu's Network Manager.
 
Whenever I start Firefox, the "Work Offline" box is
checked, whether I'm already connected to the Internet
or not.  If I uncheck the box and start a new instance
of Firefox, the box will be cleared in the new window.
But if I close Firefox before opening it again, the box
will always be checked.
 
I went into Firefox's about:config page and changed
"browser.offline" and "browser.offline-apps.notify" from
"true" to "false", with no change in behavior.
 
I also turned off startup of "Network Manager" at logon
with no change in behavior.
 
How do I get that checkbox to start out clear?
 
   -- Jeff, in Minneapolis

---

### Post by lovinglinux on 2012-01-28
Try this: [https://addons.mozilla.org/en-US/firefox/addon/stayinonlinemode/?src=search](https://addons.mozilla.org/en-US/firefox/addon/stayinonlinemode/?src=search)

BTW, you need to update your system. Firefox will be upgraded to version 9.0.1

---

### Post by Jeff Root on 2012-01-29
I also asked at the Firefox website.  One of their
suggestions was to go into about:config and change
toolkit.networkmanager.disable to true.  So far, it
has worked.
 
Thank you.
 
   -- Jeff, in Minneapolis

---

