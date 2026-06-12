---
title: "Flash player won't work?"
date: 2011-01-18
forum: Multimedia Software
---

### Post by freshmeat20 on 2011-01-18
Says it's installed via the Ubuntu software center. But youtube, grooveshark, pretty much everything that uses flash doesnt work. An interface will pop up (ex. youtube player will pop up but can't do anything with it) but nothing happens. Any ideas?

---

### Post by lovinglinux on 2011-01-18
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

---

### Post by freshmeat20 on 2011-01-18
tried to install flash-aid came up with this

Firefox could not install the file at 

[https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=addondetail](https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=addondetail)

because: Download error
-228

But since I found out what this was, Im pretty sure this will fix my problem.

---

### Post by lovinglinux on 2011-01-18
> **freshmeat20 said:**
> tried to install flash-aid came up with this

Firefox could not install the file at 

[https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=addondetail](https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=addondetail)

because: Download error
-228

But since I found out what this was, Im pretty sure this will fix my problem.

Type **about[noparse]:[/noparse]config** in the address bar, then type **network.dns.disableIPv6** in the filter, then double click the property to make it **true**.

That should fix the download issue. If not, then get the file from the [extension web site]("http://www.webgapps.org/addons/flash-aid"), which has an alternative download link.

---

### Post by pizzafarmer on 2011-01-19
Thanks, lovinglinux, it worked like a charm. I finally started getting caught up on releases here and after upgrading to 10.04 Flash didn't work and installing the latest version didn't help.

---

