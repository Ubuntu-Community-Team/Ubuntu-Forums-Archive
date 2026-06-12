---
title: "changing account in DFO"
date: 2009-04-06
forum: Multimedia Software
---

### Post by anfractuosities on 2009-04-06
I downloaded Desktop Flickr Organizer, b/c I am making a website for someone and they want me to download all of their images from flickr.

I did a tet to make sure it would work using my account, and now I can't figure out how to change accounts.  I checked all of the .flickr folder and anything ele that I could find that may have stored my name....even tried uninstalling and reinstalling....

---

### Post by anfractuosities on 2009-04-07
found it....need to delete keys in config editor

---

### Post by epakai on 2011-07-26
There seems to be little info on this and DFO offers no help when it can't connect as a result of removing the authorization on Flickr. So I'm posting to give a little more info since this was a fairly good hit on google.

The relevant key are changed by opening the Configuration Editor 'gconf-editor' navigating to /apps/DesktopFlickrOrganizer. Then you just right click and unset each key. Restart DFO and it'll direct your web browser to Flickr to re-authenticate.

---

