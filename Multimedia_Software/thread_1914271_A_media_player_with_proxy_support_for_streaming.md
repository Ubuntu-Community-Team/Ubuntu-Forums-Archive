---
title: "A media player with proxy support for streaming"
date: 2012-01-24
forum: Multimedia Software
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-24
Hi all,

Is there a media player or a plugin to allow support for media streaming through an IP:port proxy?

---

### Post by wolfen69 on 2012-01-24
I believe VLC player can do this.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-24
Thanks wolfen69, that's what I thought too, but wasn't able to find any such option. Can you please give me a clue where can I set up proxy for VLC?

---

### Post by wolfen69 on 2012-01-24
Perhaps [this]("http://crypt-sdk.blogspot.com/2011/11/how-to-set-proxy-settings-in-vlc-http.html") may help. I just searched for *vlc proxy settings* in google.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-25
Thanks for the link. Although the data there is given for Windows, I was able to find Proxy settings under Tools > Preferences. However, it only supports HTTP proxy. I should've mentioned that I need support for SOCKS5 proxy. This didn't help me.

---

### Post by SankaD on 2012-03-16
VLC does support SOCKS proxy settings. You have to find the "Socks proxy" section from the right hand side of the window, when in the left hand side, [**"Input/Codecs" is selected**]("http://crypt-sdk.blogspot.com/2011/11/how-to-set-proxy-settings-in-vlc-http.html"). The settings are same for Windows and Ubuntu (Don't know about VLC 2.0 though):rolleyes:

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-17
Perfect! SankaD you're a lifesaver!

I should only say that before SOCKS option is revealed, All Settings need to be selected at the bottom of the left panel.

Also, proxy needs to be entered like so: ip:port without the protocol (so no http:// or https:// or whatever).

Works like a charm!

---

### Post by proxybuy on 2012-05-03
[COLOR="Black"]> **&#1058 said:**
> Perfect! SankaD you're a lifesaver!

I should only say that before SOCKS option is revealed, All Settings need to be selected at the bottom of the left panel.

Also, proxy needs to be entered like so: ip:port without the protocol (so no http:// or [[COLOR="black"]_http_[/COLOR]]("proxybuy.com")s:// or whatever).

Works like a charm![/COLOR]

Its very interesting.

---

