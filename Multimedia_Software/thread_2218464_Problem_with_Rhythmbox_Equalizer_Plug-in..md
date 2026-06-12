---
title: "Problem with Rhythmbox Equalizer Plug-in."
date: 2014-04-20
forum: Multimedia Software
---

### Post by bananamancan on 2014-04-20
I downloaded the 10-band equalizer plugin for for Rhythmbox, just cuz I want and equalizer, but Rhythmbox has my favourite interface, and it shows up just find, but when I try to use it, 
it just says "The plugin 'Equalizer' could not be  loaded. An error occured: Plugin loader "Python" not found"
Which doesn't make sense, since I totally have the program Python installed...Do i like need some other library?

---

### Post by davidmohammed on 2014-04-25
I guess you are using Rhythmbox 3?

if so - look at the README file of the plugin.  You need to use

./install.sh --rb3

This will ensure the correct plugin file is installed.

---

### Post by bananamancan on 2014-04-25
Thank bro, I should prolly try reading the readme next time.

---

### Post by jason163 on 2015-01-04
Having same problem/error. Can someone please elaborate on the fix?

No idea where "install.sh" is. Installed from apt-get; downloaded tarball and no install.sh there either.

---

### Post by Yellow Pasque on 2015-01-05
Be more specific. What did you install from apt-get? What tarball did you download?

EDIT: Instructions are here: [https://github.com/luqmana/rhythmbox-plugins](https://github.com/luqmana/rhythmbox-plugins)

---

