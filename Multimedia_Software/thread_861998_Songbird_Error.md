---
title: "Songbird Error"
date: 2008-07-17
forum: Multimedia Software
---

### Post by Brijamelsh on 2008-07-17
I get these errors when i try to play a music file in Songbird. Any help would be appreciated. I am using Ubuntu Studio (hardy Heron 8.04)

Might be worth noting that Audacious wasn't playing music either until i switched it to use ALSA, however i cant figure out how to possibly check Songbird for ALSA.
> 
Error: [Exception... "'Component does not have requested interface' when calling method: [nsIFactory::createInstance]"  nsresult: "0x80004002 (NS_NOINTERFACE)"  location: "<unknown>"  data: no]

Error: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIProperties.get]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: file:///home/user/Songbird/components/nsBrowserGlue.js :: bg__initPlaces :: line 325"  data: no]
Source File: file:///home/user/Songbird/components/nsBrowserGlue.js
Line: 325

** So i fixed it, all i had to do was go to my sound control menu and set everything to ALSA from Autodetect.

---

### Post by xc3RnbFO8P on 2008-07-17
Can you see if **BrowserGlue** is a Addon?

---

### Post by Brijamelsh on 2008-07-17
> **Ringi said:**
> Can you see if **BrowserGlue** is a Addon?

its not an add on for SB.

---

### Post by xc3RnbFO8P on 2008-07-17
Firefox?
Try to remove it.

---

### Post by Brijamelsh on 2008-07-17
> **Ringi said:**
> Firefox?
Try to remove it.

what does Firefox and this plug in have to do with Songbird and playing music?

The only Firefox add on i have is the Ubuntu Firefox Modification plug in.

---

### Post by xc3RnbFO8P on 2008-07-17
Its a bug in Firefox both in Windows and Linux.
[http://support.mozilla.com/tiki-view_forum_thread.php?locale=de&forumId=1&comments_parentId=95027]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=de&forumId=1&comments_parentId=95027")

---

### Post by Brijamelsh on 2008-07-17
So i fixed it, all i had to do was go to my sound control menu and set everything to ALSA from Autodetect.

---

