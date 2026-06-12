---
title: "(UK) Virginmedia mobile internet - Troubles with Yahoo and Google sign in"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by candtalan on 2009-11-26
Is anyone in UK using Virginmedia mobile internet dongle and yahoo or google accounts?
I would be most interested to know if you see the following problems too. tia.

Workaround - please see below.

Problem:
is that although all internet sites are available and work ok, when the user tries to login to either yahoo or login to google, the login process stalls.

It is emphasised that generally, internet use is perfectly ok. The problem is most specifically only at the early stage of trying to sign in, in yahoo and also, since a week ago, google.

The yahoo process shows an incomplete login invitation screen, which is continually trying to complete, where the user name and password fields are shown, and can be filled, but the 'Sign in' button never becomes visible.

The google process accepts the entry of username and password.

However, subsequently the sign in browser progress bar hangs at around halfway, never completing.

Virginmedia phone support do not know anything useful about Ubuntu use.

The user used the dongle on a windows machine with Internet Explorer as a test and it completed the google sign in ok, suggesting the dongle is not faulty.

A second Ubuntu laptop, nominally identical, was also tried, with identical problem results.

When the laptops were connected to the internet via an ethernet cable, then the sign in processes are ok with no problems.

It is interesting to note that the yahoo sign in page problem has remained unchanged for some months, and that the google sign in problem has only begun a week or so ago, previously google sign in was normal and ok.

The browser being currently used is Firefox, currently version  3.0.15

Different browsers:
epiphany-gecko was installed and tried, and also showed exactly the same problems.

At this stage, Opera browser was downloaded and installed, however, for better download speed, the laptop was connected using an ethernet cable, which remained connected while initial yahoo and then google sign-in were tested - being wired connection - all was ok and working.

However a bright idea was considered at this time:

Both yahoo and google sign in facilities invited the user to *remain* signed in. If the (virgin media??) machines somewhere were getting an issue with some security timing or procedure, then what would happen if the initial sign in was completed using the wired connection, and the setting chosen for the user to *remain* signed in?

This was done for yahoo and google with both firefox and also opera, with the user setting to remain signed in.

When the internet connection was then later transferred to Virginmedia mobile internet dongle, both yahoo and google were available fully signed in no problems! The process had apparently by passed the issue.

Workaround:
was to initially *not* use a Virginmedia mobile connection
but to use a wired connection to login and set to *remain* logged in.
Then subsequently use the Virginmedia mobile internet connection.

Thoughts:
It seems as if when internet connection is used from Virginmendia mobile internet, that something in the early process with the ISP or other secure machines, that an essential item is not being completed satisfactorily. This is for both yahoo sign in and also for google
sign in. Use of the 'Remain signed in' option seems to avoid this issue.

Note: one experiment which was not done at this time was to attempt a complete sign in from scratch using Opera browser and virginmendia mobile internet. It is hoped that this may be done at a later time or please may be done by others reading this to help test this issue.

=========================================================
Hardware:

Dongle:
Virginmedia mobile internet broadband dongle, monthly account use.
Dongle type: believed to be: Huawei E160G 3g USB modem

Signal strength is good at 3 out of 4 bars

Laptop:
Lenovo  type: ThinkPad N500-1 (from Linux Emporium)

and also the same problem on another, nominally identical laptop.

Software: Ubuntu 9.04, fully updated
browsers used:
firefox currently version 3.0.15
epiphany-gecko
Opera currently version 10.10
=========================================================

Suggestions welcomed
tia

---

### Post by candtalan on 2010-01-12
More information:
as days and weeks went by, the workaround of using the pre-signed in method ceased to be successful. 

An answer on the [ubuntu-uk] users list from Jonathon Fernyhough had suggested that the mtu setting might be relevant:

[http://www.mail-archive.com/ubuntu-uk@lists.ubuntu.com/msg21736.html](http://www.mail-archive.com/ubuntu-uk@lists.ubuntu.com/msg21736.html)

extract:
>>> Have you tried lowering the MTU? This fixes problems on certain sites
>>> for me quite often.
>>> e.g..:
>>> $ sudo ifconfig ppp0 mtu 1400

The adjustment of mtu value was tried by the method of editing the file 
/etc/ppp/options
by adding the line
mtu 1400

It was noted that the original options file did not contain an explicit mtu value, so I guess a default was being used somewhere.

It worked! Google mail sign in worked ok :-)
Yahoomail was not tested, but I would be hopeful that it also would be ok.

---

