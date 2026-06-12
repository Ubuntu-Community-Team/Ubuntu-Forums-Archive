---
title: "Linux blocked on university network"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by badook on 2011-02-13
Hi, I am facing an annoying problem with the wireless network of my university.
The network is open, doesnt have wpa/wep, and once connected when requesting any page in the browser it gets redirected to a login page.
Basically any pc running windows works fine, however if the os is linux-based than the pc connects just fine, it gets an ip, but the login page never loads. 
I have tried several browsers, several machines, even my android smartphone is locked out as well as all my friends running ubuntu, arch linux and others linux distros.
The technical support never answered my email, and it's now 3 weeks that we are all without internet.
Does anybody know what could be the problem? The university has not officially locked out linux pcs...
Thanks!

---

### Post by AlphaLexman on 2011-02-13
Do you attend school in Redmond, Washington?:D

---

### Post by badook on 2011-02-13
No Italy ;) ...have you got a similar problem there?

---

### Post by SaintDanBert on 2011-02-13
There is a similar problem some of us have with public hotspots in hotel rooms and similar.  I "moved the flat to a different wheel to make it go away..." (grin)

1.  Boot win-dose and connect -- all goes well; you get a session and their network sees your MAC address
2.  Quickly reboot into linux and Try connection -- [highlight]quickly[/highlight] so that their network does not completely discard your session
(Because your MAC address is now known to their network, things seem to move along better)
3.  Open a brower to somewhere "tame" -- (I like to use university home pages) This provokes the login and authentication at most hotels. Some school sites do the same thing.

Pleaes let us know what you discover. We are hearing about more frequent hostilities toward linux workstations.

~~~ 0;-Dan
3.

---

### Post by SaintDanBert on 2011-02-13
> **badook said:**
> No Italy ;) ...have you got a similar problem there?

Er, um, Redmond, Washington (State) is the home of Microsoft, Inc.

Cheers,
~~~ 0;-Dan

---

### Post by badook on 2011-02-13
I tried a similar approach...basically I logged in with windows, turned the wifi off, changed the mac of my phone to match the one of my netbook and connected, but the result was still the same, no pages where loading...I can't understand why it happens...it seems to me so absurd...

---

### Post by badook on 2011-02-13
> **SaintDanBert said:**
> Er, um, Redmond, Washington (State) is the home of Microsoft, Inc.

Cheers,
~~~ 0;-Dan
Ops...I thought he was serious and didn't think about it twice...I should delete my answer then...eheh

---

### Post by Simian Man on 2011-02-13
Have you tried changing your user agent string?

---

### Post by badook on 2011-02-13
Yes...no luck

---

### Post by AlphaLexman on 2011-02-13
> **badook said:**
> Ops...I thought he was serious and didn't think about it twice...I should delete my answer then...eheh
Sorry, I was being silly and was probably out of line, I thought the smiley and the joke was obvious.

---

### Post by SeijiSensei on 2011-02-14
> **badook said:**
> The technical support never answered my email, and it's now 3 weeks that we are all without internet.

Have you actually brought your computer to them and showed them the problem?  Sometimes the best approach is person-to-person.

There may not be a solution.  My daughter's campus uses some kind of proprietary, certificate-based wifi solution that refuses to connect to Linux.  As far as I know, her only solution is to not use Linux.

---

### Post by pricetech on 2011-02-14
Sad but true.  We have an open wireless network that will let pretty much anything connect, but some of the services we offer involve windows only software.

---

### Post by SaintDanBert on 2011-02-14
> **badook said:**
> Ops...I thought he was serious and didn't think about it twice...I should delete my answer then...eheh

No worries, Mate!

As the net and linux community reach more and more of the world, I've become aware that American English colloquial and idomatic speech often does not "communicate."

American geeks know "Redmond" for what it is and know "Washington State" separate from "Washington, DC"  I try to avoid taking anything like that for granted any longer.

The same is true for all sorts of geek-speak, jargon, and techno-babble.
Remember that "communication" involves not only a "sender" and "receiver" but a "message" -- AND -- moving the messages is only half the battle. The "messages" must be one that is understandable and understood at the other end.

(grin)
Je sais que vous pensez que vous avez compris ce que vous pensez que j'ai dit.  Mais ce que vous ne savez pas, c'est que ce que j'ai dit n'est pas ce que je voulais dire.[1]
(grinning)

Cheers,
~~~ 0;-Dan

____________________
[1] I know you think that you understood what you think I said, but
What you do not know is that what I said is not what I really meant.

---

