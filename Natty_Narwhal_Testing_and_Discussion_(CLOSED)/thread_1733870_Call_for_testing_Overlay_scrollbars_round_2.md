---
title: "Call for testing: Overlay scrollbars round 2"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jibel on 2011-04-19
3 weeks ago we tested a preview version of new feature unique to Ubuntu Natty: the overlay scrollbars.
The feedback you've provided were really great and the overlay scrollbars are now part of your favourite desktop.

We'll ask you to do it again and test the overlay scrollbars in the latest build.

The goal of the testing is to discover:
 * any kind of crashers, like when the application starts and tries to display the window(s) containing scrollbars
 * slowdowns in using scrollable areas; measurements can help judge how much the scrollbar really impacts the application, or whether the application is just slow due to other circumstances
 * any other kind of anomaly obviously due to the scrollbars that impacts the user experience


 * How can you help ?

We need people running Natty either installed or from a live session, then follow the the instructions below:

1. Update your system yo the latest version of the packages available or use the latest ISO from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

The Overlay Scrollbar are installed by default starting from Natty Beta 2 and available in Unity and Classic Desktop.

 2. You have to have an account in our tracking system. Go to
      [http://desktop.qa.ubuntu.com](http://desktop.qa.ubuntu.com)
 and click on "Log In" and "Create New Account"

 3. Run the 5 tests described on the tracker (when you click on "Overlay Scrollbars) with as many applications as you can and post the results of the tests to the Tracker [1]. Add the applications you've tested in the comment area of the result.

To test the scrollbar with as many applications as possible you'll need to disable the whitelist. To disable the whitelist prefix each application invocation with:

LIBOVERLAY_SCROLLBAR=1 <command>

for example

LIBOVERLAY_SCROLLBAR=1 yelp

To enable it permanently, create a file /etc/X11/Xsession.d/80overlayscrollbars with the content:

export LIBOVERLAY_SCROLLBAR=1

The tracker only allows 1 result per reporter and testcase. Paste the list of applications with the results in the comment area of the test case you covered.

Before starting to test the scrollbars, read the detailed instructions on:
  [http://testcases.qa.ubuntu.com/Applications/System/Scrollbars](http://testcases.qa.ubuntu.com/Applications/System/Scrollbars)

 * How to file bugs ?

In case you find bugs, please report them at:
[https://bugs.launchpad.net/ayatana-scrollbar/+filebug](https://bugs.launchpad.net/ayatana-scrollbar/+filebug)

Don't forget to mention the version of the overlay library tested, and of the application that exposes the problem. If the application crashed,
apport should have captured a crash file which can help narrow down the issue more quickly.


You can join us in #ubuntu-testing on Freenode where we are coordinating this effort and we'll be happy to help you in testing this feature.


[1] [http://desktop.qa.ubuntu.com](http://desktop.qa.ubuntu.com)

---

### Post by mc4man on 2011-04-19
Can say here that evolution works fine (to extent I use it, mainly just mail) and that pending some real 'fixing' synaptic should not be returned, causes all sorts of issues beyond the initial bug report on.

---

### Post by shafin on 2011-04-20
Is there any chance of the scrollbars to land in Firefox? It can come as a part of ubuntu firefox modifications extension. 
There are already some userstyles that sort of achieve this:
[http://userstyles.org/styles/46044/firefox-simple-scrollbars](http://userstyles.org/styles/46044/firefox-simple-scrollbars)

---

### Post by chrisccoulson on 2011-04-20
> **shafin said:**
> Is there any chance of the scrollbars to land in Firefox? It can come as a part of ubuntu firefox modifications extension. 
There are already some userstyles that sort of achieve this:
[http://userstyles.org/styles/46044/firefox-simple-scrollbars](http://userstyles.org/styles/46044/firefox-simple-scrollbars)

No, this definitely won't happen in Natty, and it also won't be part of Ubufox or any other extension. Integration with these scrollbars is not possible from an extension

---

