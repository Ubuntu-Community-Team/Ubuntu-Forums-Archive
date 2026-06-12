---
title: "how do i open a pdf inside firefox?"
date: 2009-03-16
forum: Multimedia Software
---

### Post by kaston on 2009-03-16
i want to be able to open pdfs using adobe reader inside firefox.  currently, whenever i click on a link to a pdf, adobe reader starts up outside firefox.  in edit/preferences/applications, i noticed that for pdfs the action is "use adobe reader 8", whereas for some other file types it says "(in firefox)".  how do i change the action to "adobe reader 8 (in firefox)"?

---

### Post by 73ckn797 on 2009-03-16
Go to Tools/Add-ons.

There is a tool that will view within Firefox. See attached screenshot.

---

### Post by yaroto98 on 2009-03-16
Maybe a Firefox plugin like PDF Download?

[https://addons.mozilla.org/en-US/firefox/addon/636](https://addons.mozilla.org/en-US/firefox/addon/636)

---

### Post by 73ckn797 on 2009-03-16
> **yaroto98 said:**
> Maybe a Firefox plugin like PDF Download?

[https://addons.mozilla.org/en-US/firefox/addon/636](https://addons.mozilla.org/en-US/firefox/addon/636)

That looks like the same thing but just use the one as I mentioned. It will place an icon at the top right side of the address bar.

---

### Post by yaroto98 on 2009-03-16
Yea, same thing. Both'll work

---

### Post by kaston on 2009-03-16
ok i installed this addon but the same thing happens when i try to open a pdf from a link in a new tab by middle clicking the link.  in the pdf download plugin options/opening pdf, i set it to "open in new tab", but it's still opening it in acrobat outside firefox.  is there another setting i need to set?

---

### Post by 73ckn797 on 2009-03-16
Try logging out or restarting.

---

### Post by Dougie187 on 2009-03-16
You might have to make adobe not the default for pdfs in firefox, check your mimetypes.

---

### Post by gandaran on 2009-03-17
install the adobe acrobat reader plugin for firefox (it also works for opera browser) and forget the addon, adobe acrobat reader and plugin are in synaptic if you have added the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository.

---

### Post by OrangeCrate on 2009-03-17
The specific plugin you're looking for in synaptic, is:

mozilla-acroread

Description:

> Adobe Reader - mozilla/konqueror plugin - Medibuntu package

Adobe Reader is an Adobe Portable Document Format (PDF) files viewer.

This package contains the plugin for a www-browser like
mozilla/firefox/galeon/konqueror.

---

### Post by binbash on 2009-03-17
install mozilla-acroread

---

### Post by kaston on 2009-04-27
new problem:  i am trying to use zotero to open a pdf inside firefox.  in edit/preferences/applications, what i choose to open "pdf document (video/x-flv)" seems to control how firefox opens it from zotero.  when opening pdfs in firefox not in zotero, i have set the action to "use adobe reader 8.0 (in firefox)" which works nicely.  i have been trying to make this the action for when it opens pdfs from within zotero but i can't seem to find the application in /usr/bin which will give me the option to "use adobe reader 8.0 (in firefox)".  any idea where this is?  thanks

---

