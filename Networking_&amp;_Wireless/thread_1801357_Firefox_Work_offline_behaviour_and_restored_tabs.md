---
title: "Firefox Work offline behaviour and restored tabs"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by emanuel.landeholm on 2011-07-10
Is there any way to start Firefox without having it trying to refresh all my previous tabs when I'm offline? I have tried ticking on the Work offline checkbox before I close the window but when I restart Firefox again it does not remember the Work offline setting.

This is a problem because I often fill upp lots of tabs of blogs and articles while I'm online to read later on offline. But if I have to restart the browser, it will start trying to refresh the tabs and replace the cached pages with network error pages which are of little help to me...

TIA

---

### Post by lovinglinux on 2011-07-11
You need to prevent Firefox from deleting the cache when closing.

Set the history options to "Remember History" or "use custom settings for history". Also make sure to untick the options "Clear History when Firefox closes" or if you need that to be selected, disable the Cache entry in the "Settings" options next to it.

[[IMG]http://www2.picturepush.com/photo/a/6073145/640/6073145.png[/IMG]](http://picturepush.com/public/6073145)

You might also like [Session Manager]("https://addons.mozilla.org/en-US/firefox/addon/session-manager/") extensions, that allows a greater control of your sessions, including saving multiple sessions.

---

### Post by emanuel.landeholm on 2011-07-11
> **lovinglinux said:**
> You need to prevent Firefox from deleting the cache when closing.

Set the history options to "Remember History" or "use custom settings for history".

Hmmm. My settings are "Remember history", and when I select "use custom" I get the same values you posted in your image.

I don't think that's it. The problem is that the browser needs to do an IF-MODIFIED-SINCE HTTP request to see if the cached page has changed remotely. This request fails, or gets some kind of redirect from the wlan router (public network) which causes Firefox to render a network error page.

I'm going to have peek around in about:config to see if there is some way to control the cache.

Thanks for replying

---

### Post by lovinglinux on 2011-07-11
> **emanuel.landeholm said:**
> Hmmm. My settings are "Remember history", and when I select "use custom" I get the same values you posted in your image.

I don't think that's it. The problem is that the browser needs to do an IF-MODIFIED-SINCE HTTP request to see if the cached page has changed remotely. This request fails, or gets some kind of redirect from the wlan router (public network) which causes Firefox to render a network error page.

I'm going to have peek around in about:config to see if there is some way to control the cache.

Thanks for replying

I tried on a clean profile and it worked. The browser still tries to connect, but the page is initially displayed from cache.

---

### Post by emanuel.landeholm on 2011-07-11
> **lovinglinux said:**
> I tried on a clean profile and it worked. The browser still tries to connect, but the page is initially displayed from cache.

I'm on a public, pay-for-access wlan. So I'm always "online", but all HTTP requests are redirected with an error code when I don't have an active session.

---

### Post by lovinglinux on 2011-07-11
> **emanuel.landeholm said:**
> I'm on a public, pay-for-access wlan. So I'm always "online", but all HTTP requests are redirected with an error code when I don't have an active session.

I am also always "online" and I never bothered with offline access from cache, but it seems to me that this is the default behaviour.

See the Unresolved Questions of [https://wiki.mozilla.org/Session_Restore](https://wiki.mozilla.org/Session_Restore)

Perhaps you could achieve what you want with Better Cache extension. I will do some tests and get back to you.

---

### Post by emanuel.landeholm on 2011-07-12
> **lovinglinux said:**
> I am also always "online" and I never bothered with offline access from cache, but it seems to me that this is the default behaviour.

Hey, thanks for replying. I will check out your links.

I have found a partial solution to my problem. I make sure the wireless adapter is off (physically, by pressing the button on the front). Only THEN do I start Firefox. The restored tabs that fail are typically script-heavy sites like facebook, gmail etc. But maybe that cache extension will help.

ciao!

---

### Post by noxilie on 2012-02-24
Same problem.
xubuntu 11.10 
firefox 10.0.2

about:config - set **network.manage-offline-status** to [B]true
[/B]That worked for me
Best regards.

---

