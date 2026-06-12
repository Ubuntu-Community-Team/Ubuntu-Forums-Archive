---
title: "Rhythmbox no longer working post upgrade to 13.10"
date: 2013-11-13
forum: Multimedia Software
---

### Post by p1tbool on 2013-11-13
Hello,

I upraded 13.04 to 13.10 on my dell latitude d820, and since then Rhythmbox is no longer working properly. The ui works, but it doesn't play audio at all.

I'm getting the following asserts :

* when firing up the application
(rhythmbox:7830): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed

* when pressing play, it loops through the list of files switch the icon to an error one... and keeps looping through all the file.
If I hit pause I'll get the following assert:

(rhythmbox:7830): GStreamer-CRITICAL **: gst_uri_is_valid: assertion 'uri != NULL' failed

(rhythmbox:7830): GStreamer-CRITICAL **: gst_uri_handler_set_uri: assertion 'gst_uri_is_valid (uri)' failed

Would you have any idea to why it no longer works ?

I'm guessing that there is an issue between GStreamer and Rhythmbox ...

Thanks in advance for your help!

---

