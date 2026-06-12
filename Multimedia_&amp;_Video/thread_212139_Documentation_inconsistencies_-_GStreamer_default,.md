---
title: "Documentation inconsistencies - GStreamer default, Xine recommended"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by tibbe on 2006-07-09
While reading about restricted formats at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) I came upon this paragraph:

> Playing Streaming Video from the Internet

    * Ubuntu

      There are a variety of plugins that allow you to play streaming video in your browser. *The recommended plugin is totem-xine-firefox-plugin*. First, install the Windows Codecs, then install the totem-plugin.

      On Ubuntu, *Totem can use either the gstreamer (default) or xine multimedia frameworks*. The plugin installation process depends on the framework you use. If you use totem-gstreamer (the version of Totem that uses the gstreamer back-end), install the totem-gstreamer-firefox-plugin package. If you use totem-xine, install the totem-xine-firefox-plugin package.

      See this page for instructions for Ubuntu 5.10 and 5.04.


Notice the two parts in italics. The default (and recommended?) back-end is  gstreamer but the recommended plugin uses xine. So if xine is recommended why is gstreamer the default and vice versa?

---

