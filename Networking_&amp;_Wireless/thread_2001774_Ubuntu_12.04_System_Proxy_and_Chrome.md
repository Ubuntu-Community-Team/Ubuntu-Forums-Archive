---
title: "Ubuntu 12.04 System Proxy and Chrome"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by fraterm on 2012-06-11
What used to work: Google Chrome used to use a proxy configuration dialog similar to firefox currently uses.  If I set the proxy settings in firefox to use system proxy settings I have the same problem I will detail with chrome and chromium.

When running Google Chrome inside of a proxied environment (with the network proxy configuration set appropriately) I recieve DNS failures for addresses that are internal, but there is no place to insert what would go into a no_proxy="*.foo.com,*.foo-baz.com,localhost,127.0.0.1" sort of environment variable.

The no_proxy environment variable and ignore proxy configuration options in firefox are not able to be input for system-wide proxy settings in the sort of "dumbed down" configuration panel that ubuntu 12.04 offers.

Is there a proper way to set up google-chrome to run in a proxied environment (and I have tried the ones indicated in the man page for google-chrome (they involve setting up http_proxy/all_proxy/no_proxy environment variables and also setting them using --options_thatendinproxy=urls)) that works reliably?  I'm frustrated at this.  It seems that having a proxy configuration applet in the state this one is in is, well, is not a good sign of development having been well thought out.

Does anyone else work in a proxied environment and use google-chrome/chromium?  Perhaps I'm all wrong here and it points at a problem in my works proxy/DNS infrastructure.

---

