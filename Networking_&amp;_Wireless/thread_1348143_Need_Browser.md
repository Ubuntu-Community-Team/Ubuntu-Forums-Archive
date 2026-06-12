---
title: "Need Browser"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by BalaViknesh on 2009-12-06
All,

I need to get IE in my Ubunutu. though it may sound a bit odd, need a way out..

Or can u suggest a browser which does the same work of IE.. (Same means exact replica).

Tried using Wine but didnt help. :confused:

---

### Post by davidm84 on 2009-12-07
Whats wrong with Firefox?? Practically the same

---

### Post by DGortze380 on 2009-12-07
> **BalaViknesh said:**
> All,

I need to get IE in my Ubunutu. though it may sound a bit odd, need a way out..

Or can u suggest a browser which does the same work of IE.. (Same means exact replica).

Tried using Wine but didnt help. :confused:

ies4linux

---

### Post by BalaViknesh on 2009-12-07
Officially I have to upload a file... which server denies saying am using Mozilla. Need to Use IE 6.0 or higher of it.

---

### Post by gradinaruvasile on 2009-12-07
> **BalaViknesh said:**
> Officially I have to upload a file... which server denies saying am using Mozilla. Need to Use IE 6.0 or higher of it.

Then try the user agent string changer in Firefox first:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

If it doesnt work, try ies4linux as suggested above:

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Note: It is reported as an attack site by google. But being the nature of it i think its more of a microsoftish maneuver...

Anyway, this is what you need from the site if you dont wanna go there:

```
IEs 4 Linux needs two packages: cabextract and Wine. You can install them using your Linux package manager (synaptic, apt-get, yum, emerge etc) or go to their sites. 

After that, download IEs 4 Linux. Extract it. Run 'ies4linux'. Follow the instructions. 

In a terminal, you can do: 

sudo apt-get install cabextract wine

wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```


PS. There are sites that use some Activex controls, crypto stuff that just doesnt run with these workarounds. In that case you must use windows for it.

---

### Post by ankur1990 on 2009-12-07
try out ubuntu version of opera.......
another gud choice :p

---

### Post by gradinaruvasile on 2009-12-07
That wont help if the site asks specifically for IE.

---

### Post by BalaViknesh on 2009-12-07
ll Try that and come back in shortly.. Hope it works 4 me.. 

Thanks in Advance. ;):D

---

