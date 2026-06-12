---
title: "Big bug in gnome-search"
date: 2010-06-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by timosha on 2010-06-11
On my Thinkpad R51 - 2887:

When I search on text in files with gnome-search (Search for Files) I experience a complete system crash. An update today of gnome-system-tools didn't solve the problem.

(Yes, I reported the bug but it is marked "invalid" as I didn't provide enough information, according to the guru's on Launchpad).

---

### Post by MacUntu on 2010-06-11
> **timosha said:**
> I reported the bug but it is marked "invalid" as I didn't provide enough information

It's not marked invalid because you didn't provide enough information:

[QUOTE=Pedro Villavicencio][...]I'm closing this bug report **since the process outlined above will automatically open a new bug report** which can then dealt with more efficiently.[...][/QUOTE]

---

### Post by timosha on 2010-06-11
Well, I followed the instructions and let the thing crash a few times

 [B]process outlined above will NOT automatically open a new bug  report
[/B]
I will wait until somebody of much higher intelligence experiences the bug and reports it according to the procedures.

---

### Post by MacUntu on 2010-06-11
If you don't get a crash file it maybe didn't crash but just hung? I tried to reproduce it but the search tool works fine for me.

---

### Post by SevenMachines on 2010-06-11
for an automatic bug report you need apport to be running, i think its disabled by default during the dev cycle (see /etc/defaullt/apport) to avoid mountains of automatic bug reports.
First force start apport
$sudo service apport start force_start=1

then let the crash happen, hopefully you should see the 'report bug' dialog automatically where apport can generate all the useful information

---

### Post by timosha on 2010-06-11
Apport is enabled at startup.

```
sudo service apport start force_start=1
start: Job is already running: apport
```

But no apport dialog after the crash.

---

### Post by SevenMachines on 2010-06-11
hmmm, do you have the _crash file in /var/crash?

---

### Post by SevenMachines on 2010-06-11
you can send manually if the crash report is actually generated
$ ubuntu-bug /var/crash/_some_crash_report.crash

---

### Post by timosha on 2010-06-11
> **SevenMachines said:**
> you can send manually if the crash report is actually generated
$ ubuntu-bug /var/crash/_some_crash_report.crash

There are no crash files.

---

### Post by chrisccoulson on 2010-06-11
I'm not even sure Apport is enabled yet - it's not normally enabled until later in to the cycle. Have a look in /etc/default/apport

---

### Post by dino99 on 2010-06-11
hm, i feel i've a special bug free maverick :p , no /var/crash/ around there ;-)

---

### Post by chrisccoulson on 2010-06-11
> **dino99 said:**
> hm, i feel i've a special bug free maverick :p , no /var/crash/ around there ;-)

Did you check if Apport is enabled in /etc/default/apport?

---

### Post by timosha on 2010-06-11
> **chrisccoulson said:**
> Did you check if Apport is enabled in /etc/default/apport?

Yes, it is enabled.

---

### Post by dino99 on 2010-06-11
> **chrisccoulson said:**
> Did you check if Apport is enabled in /etc/default/apport?

this maverick is a lucid dist-upgrade, lucid was having /var/crash/, but the upgrade have removed it, and yes apport is installed, but enabled=0 into /etc/default/apport (if i'm not wrong, i've seen somewhere that maverick devs have make this choice for the early development cycle to minimize the number of useless bug reports)

---

### Post by chrisccoulson on 2010-06-11
Did you try running it from a terminal?

---

### Post by taavikko on 2010-06-11
Apport was disabled in 1.13.3-0ubuntu2 lucid
and the newer package in maverick didn't enable it.

---

### Post by timosha on 2010-06-11
> **chrisccoulson said:**
> Did you try running it from a terminal?

Yes !

     ```
sudo service apport start force_start=1
start: Job is already running: apport
```

---

### Post by chrisccoulson on 2010-06-11
> **timosha said:**
> Yes !

     ```
sudo service apport start force_start=1
start: Job is already running: apport
```

No, I meant gnome-search-tool.

---

### Post by timosha on 2010-06-11
> **chrisccoulson said:**
> No, I meant gnome-search-tool.

Sorry ! I will try that.

EDIT:
Same issue. Immediately a black screen with frozen mouse cursor after klicking "find". No apport after restart and no crash files.

Tested it on two installations on the same Thinkpad R51 - 2887. One with the new xorg drivers from today and one with the xorg-edgers drivers. No difference.

---

