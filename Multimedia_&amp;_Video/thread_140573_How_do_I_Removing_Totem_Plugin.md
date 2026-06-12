---
title: "How do I Removing Totem Plugin?"
date: 2006-03-06
forum: Multimedia &amp; Video
---

### Post by Maverick88 on 2006-03-06
Does anoyone know how I can remove the totem firefox plugin?
I tried removing totem but that does not do it.

Rob

---

### Post by ajgreeny on 2006-03-06
Open firefox and type "about:plugins" in the address bar and you will see listed the name of the totem plugin file, something like totemplugin.so I think.  Search for this and move it to trash as root.  That should do it, but if there are any problems you can just restore it.

---

### Post by Maverick88 on 2006-03-06
As I noted in another post relating to the same issue being painfully experienced by another user, there is a solution!

After I did the following, the mplayer plugin took over and I was finally able to see streaming QT and WM content in Firefox:

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt_backup

You might also have to rename the following if they exist (they weren't on my system):

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la_backup

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so_backup

I wish this info was added to the WIKI. Or at minimum this post should be made sticky since I am sure others will have exactly the same problems and experience the same frustration (unless they give up and use automatix).

Rob

---

