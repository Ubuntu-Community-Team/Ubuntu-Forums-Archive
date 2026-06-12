---
title: "Geoip service returning incorrect country"
date: 2022-05-29
forum: MINT
---

### Post by gwi on 2022-05-29
The command
[FONT=Courier New]wget -qO - [http://geoip.ubuntu.com/lookup](http://geoip.ubuntu.com/lookup) | sed -r 's/></>\n</g'[/FONT]
returns USA as country, while I am living in the Netherlands. I am not using a VPN, and three different "what's my ip" websites correctly return the Netherlands as my country. The IP-address shown by geoip is the same as shown by the "what's my ip" websites.
This causes the package sources to only show American mirrors instead of European ones.
Why is the Ubuntu geoip service returning an incorrect country?

---

### Post by ActionParsnip on 2022-05-30
Does
```

curl -s ipinfo.io | grep country

```
show the correct country?
Do you use a VPN for web access? This will obviously change your location

---

### Post by gwi on 2022-05-30
As I wrote I am not using a VPN.
The command you gave results in country NL, which is correct.

---

### Post by #&amp;thj^% on 2022-05-30
Geoip service has been know to have quirks.
EDIT: also this might work:
```
curl --silent ipinfo.io | jq -r '.country,.region,.city'
US
Colorado
Denver

```
For that you need to install "jg and curl"

---

### Post by gwi on 2022-05-31
Apparently the package sources app is using the geoip service to determine the list of mirrors to show. If geoip has quirks, it would be nice to see the list of mirrors based on ipinfo.io (or have someone fix the geoip service).

---

### Post by TheFu on 2022-05-31
You can force [http://nl.archive.ubuntu.com/](http://nl.archive.ubuntu.com/) to be used.
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Lots of people who live in border cities do this.

GeoIP is country/state correct for me, but the GPS returned by almost every service is 50 miles off, which is fine.  10 yrs ago, there was 1 service only 1 mile off, which shocked me a bit.

---

### Post by gwi on 2022-05-31
I am using Linux Mint, which is based on Ubuntu. Today I discovered the package sources app is actually a Python script. I edited it and hard coded my country. Maybe one day I make it use ipinfo.io, who knows.

---

### Post by coffeecat on 2022-05-31
*Thread moved to **Mint** sub-forum.*

---

### Post by gwi on 2022-06-01
Thanks. Didn't know that sub-forum existed. :oops:

---

