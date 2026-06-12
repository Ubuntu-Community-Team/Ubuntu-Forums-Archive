---
title: "asterisk sip server install errors"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by anilp on 2011-10-25
Maverick 10.10. 32 bit.
I am trying to install asterisk per [https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages#AsteriskPackages-Addingthereleasebranch](https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages#AsteriskPackages-Addingthereleasebranch)
$ sudo add-apt-repository "deb [http://packages.asterisk.org/deb](http://packages.asterisk.org/deb) `lsb_release -cs` main"
$ sudo add-apt-repository "deb-src [http://packages.asterisk.org/deb](http://packages.asterisk.org/deb) `lsb_release -cs` main"
Error: 'deb-src [http://packages.asterisk.org/deb](http://packages.asterisk.org/deb) maverick main' invalid
$

Any help appreciated.
Anil

---

### Post by jonobr on 2011-10-25
Are you stuck on asterisk?

I mention it as I think Piaf or incredible do a fanstastc job of a complete solution in a box....

The installation was easy and the forums are pretty active for support.

If your stuck on this version, Did you do an update after changing your sources?

---

### Post by anilp on 2011-10-25
> **jonobr said:**
> Are you stuck on asterisk?

I mention it as I think Piaf or incredible do a fanstastc job of a complete solution in a box....

The installation was easy and the forums are pretty active for support.

If your stuck on this version, Did you do an update after changing your sources?

The project requires asterisk - not my decision :)
I just followed the instructions on that web page and got the error.

---

### Post by jonobr on 2011-10-25
> The project requires asterisk - not my decision
Aint that a bitch!!


I notice the syntax has "proposed main"
and yours just has main.

Is there a difference in that?

---

