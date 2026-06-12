---
title: "Annoying password prompt on wifi reconnect"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by hellfeuer on 2009-01-16
Whenever my wifi connection drops out and Ubuntu tries to reconnect, Network Manager asks for the WPA password. I have it saved (and NM does in fact remember it) so this prompt is unnecessary and extremely annoying. Can I get rid of it? There seems to be a Brainstorm post on the same issue but there were no solutions. Will switching to Wicd or something help?

I'm running Intrepid

---

### Post by Whoopie on 2011-01-17
Hi,

I'm also interested in a solution. Is it possible with NM to reconnect to a WLAN without the prompt to re-enter the passphrase?
It sometimes happens that my router crashes and I'd like my laptop to try to reconnect automatically.

Best regards,
Whoopie

---

### Post by kimberlite on 2011-01-17
Right click on icon, than edit connections. On WIFI tab, select your wifi network than at wireless security, where you can add your key, you can tick "automatic connection".

---

### Post by Whoopie on 2011-02-03
I opened a feature request: [https://bugzilla.gnome.org/show_bug.cgi?id=639937](https://bugzilla.gnome.org/show_bug.cgi?id=639937)

---

### Post by MichaelBurns on 2011-05-19
> **kimberlite said:**
> Right click on icon, than edit connections. On WIFI tab, select your wifi network than at wireless security, where you can add your key, you can tick "automatic connection".This did not work for me.  I already had these settings from the beginning.  Every time I connect to my wireless router, I am asked for a password (not the key, but a password that I had to choose the first time I connected).

---

### Post by napzilla on 2012-02-08
This has been driving me insane since I upgraded to oneiric and moved into my current apartment. The wireless connection here is a bit dodgy, and it frequently drops for a minute or so. To make matters even more irritating, the damned NM prompts for the (already saved and entered password) every time it tries to reconnect. The upshot of this is that I wake up or come home to several dozen password prompts. On the up-side, un-ticking the "Make available to all users" may have solved it, so thanks for the advice.

---

