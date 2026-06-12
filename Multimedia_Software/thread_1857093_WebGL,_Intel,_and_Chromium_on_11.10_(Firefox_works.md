---
title: "WebGL, Intel, and Chromium on 11.10 (Firefox works)"
date: 2011-10-09
forum: Multimedia Software
---

### Post by kjano on 2011-10-09
Dear all,

I am running Ubuntu 11.10 and can run WebGL and the Google Demos on Firefox 7. However, I cannot get it working with the Chromium that comes with 11.10 (it is version 14.0.835.202). I am using an Intel graphics card in a new X220 Thinkpad. I am not using Chromium regularly but had to install it to get the zoom functionality in on of Google's demos working.

I checked the previous postings on related topic and they are referring to problems with the Intel drivers in 10.10 and 11.04 that should be fixed soon. Before diving deep into modifying my installation, was anybody successful with Chromium on Intel and 11.10? Why is WebGL working on Firefox without problems?

Thanks for your help.

---

### Post by gururise on 2011-10-12
Same problem here. WebGL is not working in Chromium on 11.10.  Perhaps you should file a bug in bugzilla.

---

### Post by anders_c_ on 2011-10-13
try launching chromium with "--enable-webgl" option.

---

### Post by Garrett77 on 2011-10-25
Sorry, newb here.  Is this additional piece ran from script?

---

### Post by pete04 on 2011-10-26
Hi. I'm havingvthe same issue. I'm getting an error in chrome that webGL is not enabled. I'm using 11.10.

---

### Post by gbringer on 2011-11-06
[http://www.nathan-forbes.com/?p=351](http://www.nathan-forbes.com/?p=351)

This worked for me!

---

### Post by pcorazao on 2012-04-25
Any Leads?  I have this issue on 12.04

---

### Post by techsupport on 2012-04-25
> **pcorazao said:**
> Any Leads?  I have this issue on 12.04

Have you installed them from the PPA instead yet:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

They are down the list.

:guitar:

---

### Post by scarleo on 2012-05-06
My solution was simply typing about:flags and then enable Override software rendering list. Works great, guess there's no official support for this GPU but it still works fine.

---

