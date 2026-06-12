---
title: "IP address plus /user/index.jsp?url= instead of just url"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by stansult on 2010-05-13
Just installed new (10.04) Ubuntu on my laptop (Compaq Presario), along with pre-installed Vista.
Now when I connect (successfully) to wireless network in the office, any time i open any page in Firefox, instead of the url, it goes to ```
[COLOR="SlateGray"]*(IP address of my home wireless modem)*[/COLOR]/user/index.jsp?url=*[COLOR="SlateGray"](and here goes url i wanted)[/COLOR]*
```How can i get rid of it? I tryed "No proxy" in networg configurations, and then "Automatically get proxy", and so on - nothing helps. What should I do?
Thanx in advance

---

### Post by sir_nasty on 2010-05-13
Does it do the same thing in chrome?

---

### Post by stansult on 2010-05-13
> **sir_nasty said:**
> Does it do the same thing in chrome?can't check - i need internet to get chrome..
firefox is pre-installed in ubuntu

---

### Post by sir_nasty on 2010-05-13
can you ping anything from the command prompt? if not try connecting a wire from the router to the laptop and see if that works... does the wireless work normally in vista?

Also, you can get chrome by
```

sudo apt-get install chromium-browser

```

if you can ping that is....

---

### Post by sir_nasty on 2010-05-13
another thought... were you checking the proxy settings in Firefox or in system settings? or both?

---

### Post by stansult on 2010-05-13
Geez, now it works... weird
I tryed another wireless connection and it works

Sorry guys, and thanks anyway! :)

---

