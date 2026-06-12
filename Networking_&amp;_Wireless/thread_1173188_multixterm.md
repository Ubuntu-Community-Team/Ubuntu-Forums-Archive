---
title: "multixterm"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by peridot on 2009-05-29
Hello,

I want to use multixterm (or something similar would be ok) on jaunty. Most places I've looked say that it's included in expect. However, installing expect, expectk and dependencies doesn't give me multixterm. The script that I've found ( [http://expect.nist.gov/example/multixterm](http://expect.nist.gov/example/multixterm) ) fails to run, even after changing the paths:

```
Application initialization failed: no display name and no $DISPLAY environment variable
Error in startup script: can't read "tk_version": no such variable
    while executing
"if {$tk_version < 8.3} {
    tkBad
} elseif {$tk_version == 8.3} {
    if {[lindex [split $tk_patchLevel .] 2] < 3} tkBad
}"
    (file "/usr/local/share/multixterm" line 323)

```Can anyone help me get a working copy of this program, or suggest another? I'm looking for the ability to log into multiple sites through ssh which I can control from a central window, but still be able to type in individual windows (for differing passwords).

Thanks in advance!

---

### Post by 4xel on 2009-06-24
Hi,
 You could try using clusterssh

---

### Post by syberghost on 2009-07-02
> **4xel said:**
> Hi,
 You could try using clusterssh

A lot of people, myself included, are having problems with clusterssh that are getting shoulder-shrugs instead of solutions.


$ cssh
91e1f00 is not a hash at /usr/lib/perl5/Tk/MainWindow.pm line 55.
Aborted (core dumped)

---

### Post by Nick Lutsiuk on 2009-12-01
Hey, [font=courier]multixterm[/font] is installed along with **expect-dev package, not expect**. It's located at [font=courier]/usr/bin/expect_multixterm[/font], and goes with a man page.

---

