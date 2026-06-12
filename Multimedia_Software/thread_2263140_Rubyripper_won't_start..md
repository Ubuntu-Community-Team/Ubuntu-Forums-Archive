---
title: "Rubyripper won't start."
date: 2015-01-29
forum: Multimedia Software
---

### Post by warren3 on 2015-01-29
Hi.

I installed Rubyripper about an hour ago and it loaded up first time.  Anyway the FLAC wasn't set up properly so I closed it down for the time being.  Now it will not start.  I also have two Rubyripper icons in the dash.  One says 'rrip-gui in the description the other says nothing in the description.  

I installed it via GetDeb repos. and I am running 14.10.

What have I done wrong?

---

### Post by mc4man on 2015-01-29
Open a terminal & run this, maybe it'll give you a clue
```
rrip_gui
```

---

### Post by warren3 on 2015-01-30
$ rrip_gui
/usr/lib/ruby/1.8/rr_lib.rb:213:in `loadSettings': undefined method `rstrip!' for nil:NilClass (NoMethodError)
    from /usr/lib/ruby/1.8/rr_lib.rb:130:in `initialize'
    from /usr/bin/rrip_gui:53:in `new'
    from /usr/bin/rrip_gui:53:in `initialize'
    from /usr/bin/rrip_gui:1485:in `new'
    from /usr/bin/rrip_gui:1485:in `<main>'
$

I also installed cdrdao because I wanted to make logs etc, but in the output folder for Rubyripper I have a txt file with 'cdrdao: no process found' inside it.

---

### Post by mc4man on 2015-01-30
try removing ~/.config/rubyripper/settings

---

### Post by warren3 on 2015-02-01
> **mc4man said:**
> try removing ~/.config/rubyripper/settings

That worked!

Your a star.  Thank you very much.

Cheers.

---

