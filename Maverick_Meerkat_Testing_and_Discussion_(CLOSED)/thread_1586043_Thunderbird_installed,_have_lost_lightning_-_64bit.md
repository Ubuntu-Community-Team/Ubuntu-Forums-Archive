---
title: "Thunderbird installed, have lost lightning - 64bit"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Foggy on 2010-10-01
Have just done a fresh install of 10.10 64bit, seems to be a tad better on my desktop but Thunderbird and lightning worked perfectly in 10.04 64bit on this desktop. In 10.10 just can not get lightning to work at all, advice would be appreciated as all my appointments birthdays etc are on lightning..!!!!!

My thanks in advance

---

### Post by adsbaer12 on 2010-10-01
_update:_ as pointed out by the following posts from other users you don't have to downgrade to thunderbird 3.1.3 and can keep thunderbird 3.1.4 installed. just download lightning 1.0.b2 here:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/lightning.xpi](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/lightning.xpi)
(install this .xpi via thunderbird tools --> add-ons --> extension-tab "install...")
after restarting thunderbird you should have the working lightning extension.


[SIZE=1][SIZE=2]my original post (please don't use this!):[/SIZE]
> **adsbaer12 said:**
> I just had the very same problem!
On Ubuntu 10.10 64bit (as of this writing it is the "Release Candidate"!) you can use Thunderbird and Lightning - but not their very latest versions. Installing Thunderbird via Ubuntu 10.10's repositories will give you Thunderbird 64bit v3.1.4 and the latest lighting.xpi 1.0b2 will not work with this version of Thunderbird! But Lightening 1.0b2 worked on my machine after I downgraded from Thunderbird 3.1.4 to 3.1.3 (which *imho* is still recent enough)

try this:
- if thunderbird 3.1.4 is present on your system uninstall it via ubuntu's software center
- download and install (double-click) the 3.1.3-.deb-version of thunderbird 64bit here:
[http://launchpadlibrarian.net/55224152/thunderbird-dbg_3.1.3%2Bbuild1%2Bnobinonly-0ubuntu1%7E10.04%7Ericotz1_amd64.deb](http://launchpadlibrarian.net/55224152/thunderbird-dbg_3.1.3%2Bbuild1%2Bnobinonly-0ubuntu1%7E10.04%7Ericotz1_amd64.deb)
- run the installed thunderbird 3.1.3 and verify that it is indeed version 3.1.3 (thunderbird help --> about thunderbird)
- now download lightning 1.0.b2 here:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/lightning.xpi](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/lightning.xpi)
- install this .xpi via thunderbird tools --> add-ons --> extension-tab "install..."
the compatibility check should pass without warnings!

after restarting thunderbird you should have a working lightning extension.

hope this helps...

please provide feedback if this tutorial solved your problem, so that other users with similar problems find a proper solution!

thanks & greetings from germany...
adsbaer12[/SIZE]

---

### Post by cariboo on 2010-10-01
I've got Thunderbird 3.1.4, I just installed the lightning extension that you linked to, and it works without having to install anything else.

---

### Post by Foggy on 2010-10-01
Many thanks, I removed and downloaded as suggested by 'adsbaer12' and from Synaptic package manager installed Lightning, all now seems to be working, with great full thanks, however I still seem to have 3.1.4 installed so goodness knows what I had been doing previously. 

Thanks again, I am as usual in debt.

Greetings and best wishes to Germany.

BJ

---

### Post by cariboo on 2010-10-01
Do you have the 32-bit version, as lightning isn't available in the repositories for the 64-bit version

---

### Post by Foggy on 2010-10-01
cariboo907, I am running 10.10rc 64bit as title suggests. I had no trouble running Thunderbird and lightning inside 10.04 64bit all loaded  from package manager, and again after following suggestion above I again seem to have a sensible working arrangement. I know no more than that...!

I have been using Ubuntu for about 5 years, as primary OS for 4 years, through good and bad, have always found that things work out in the end, so am hoping that it is the same this time..?

BJ

---

### Post by chrisccoulson on 2010-10-01
> **cariboo907 said:**
> Do you have the 32-bit version, as lightning isn't available in the repositories for the 64-bit version

It is! Who told you it wasn't available for 64-bit users? ;)

---

### Post by chrisccoulson on 2010-10-01
> **adsbaer12 said:**
> I just had the very same problem! :)
On Ubuntu 10.10 64bit (as of this writing it is the "Release Candidate"!) you can use Thunderbird and Lightning - but not their very latest versions. Installing Thunderbird via Ubuntu 10.10's repositories will give you Thunderbird 64bit v3.1.4 and the latest lighting.xpi 1.0b2 will not work with this version of Thunderbird! But Lightening 1.0b2 worked on my machine after I downgraded from Thunderbird 3.1.4 to 3.1.3 (which *imho* is still recent enough)

try this:
- if thunderbird 3.1.4 is present on your system uninstall it via ubuntu's software center
- download and install (double-click) the 3.1.3-.deb-version of thunderbird 64bit here:
[http://launchpadlibrarian.net/55224152/thunderbird-dbg_3.1.3%2Bbuild1%2Bnobinonly-0ubuntu1%7E10.04%7Ericotz1_amd64.deb]("http://launchpadlibrarian.net/55224152/thunderbird-dbg_3.1.3%2Bbuild1%2Bnobinonly-0ubuntu1%7E10.04%7Ericotz1_amd64.deb")
- run the installed thunderbird 3.1.3 and verify that it is indeed version 3.1.3 (thunderbird help --> about thunderbird)
- now download lightning 1.0.b2 here:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/lightning.xpi](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/lightning.xpi)
- install this .xpi via thunderbird tools --> add-ons --> extension-tab "install..."
the compatibility check should pass without warnings!

after restarting thunderbird you should have a working lightning extension.

hope this helps...

please provide feedback if this tutorial solved your problem, so that other users with similar problems find a proper solution!

thanks & greetings from germany... ;)
adsbaer12

Please don't offer advice like this! You are advising a user to downgrade to a version that is:

a) Totally unsupported by us
b) Exposed to publicly disclosed security vulnerabilities

---

### Post by cariboo on 2010-10-01
I searched with both synaptic and the Software Center, there was no lightning to be found. The repositories were updated just before searching.

I did find xul-ext-lightning, which is not what I expected it would be called.

---

### Post by chrisccoulson on 2010-10-01
That package naming is as per the Debian policy for Mozilla extensions

---

### Post by cariboo on 2010-10-01
Thank you, I just wasn't aware of it, as I been using the version from Mozilla addons.

---

