---
title: "Libre"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rosswmcgee on 2011-03-12
I did an upgrade to 11.04 natty. Then noticed that Open Office is Libre open office. Why and what is the difference?

---

### Post by owenll on 2011-03-12
> **rosswmcgee said:**
> I did an upgrade to 11.04 natty. Then noticed that Open Office is Libre open office. Why and what is the difference?

Wikipedia says this about **why**.> On 28 September 2010, some members of the OpenOffice.org Project formed a new group called The Document Foundation and made available a rebranded fork of OpenOffice.org, which they dubbed LibreOffice. The fork was created over fears that Oracle Corporation, after buying out the project's former sponsor Sun Microsystems, would discontinue OpenOffice.org as it had done with OpenSolaris.

---

### Post by kaldor on 2011-03-12
First, be aware that 11.04 is still an alpha; expect a load of problems. It does not get released until late April. If you're aware of this, report bugs as much as you can to make the release smoother.

LibreOffice is a fork from OpenOffice. Check out their website and follow the reasons behind it. LibreOffice should end up getting much better than OpenOffice in a while.

---

### Post by rosswmcgee on 2011-03-12
Thanks!

---

### Post by rg4w on 2011-03-12
> **owenll said:**
> Wikipedia says this about **why**.
Should we be concerned about VirtualBox as well?

---

### Post by Vaphell on 2011-03-12
i don't think so, virtualbox improves all the time and virtualization techniques have great value in corporate world so i doubt oracle would pull the plug on the project.

---

### Post by rg4w on 2011-03-12
> **Vaphell said:**
> i don't think so, virtualbox improves all the time and virtualization techniques have great value in corporate world so i doubt oracle would pull the plug on the project.
That's reassuring.

What caused the lack of confidence in OOo?  I would think Oracle would be happy to invest in anything that helps keep Microsoft in check.

---

### Post by Old_Man_Unix on 2011-03-13
> **rg4w said:**
> 
What caused the lack of confidence in OOo?  I would think Oracle would be happy to invest in anything that helps keep Microsoft in check.

Basically, it was Oracle's previous  handling of  FOSS applications - most recently the killing of OpenSolaris - that made the company  suspect insofar as OOo is concerned.  But there was also the perception that OOo is not moving forward under Oracle.  LibreOffice has already jumped out with a couple of improvements.

As to what Oracle's motives are, I wouldn't hazard a guess.

---

### Post by rosswmcgee on 2011-03-16
I read that the Open Office folks were also working on Libre and Oracle felt it was 

a conflict of interest, so many just left Open office.


Yesterday I did my natty updates, and then a partial upgrade. All is well, but I was wondering if I keep doing the latter two things will I at the end have a total upgrade of the completed 11.04???

---

### Post by uRock on 2011-03-16
Not sure why you would ask this in Absolute Beginner's section.

Moved to NNT&D

---

### Post by rosswmcgee on 2011-03-16
OK! sorry, do you have the answer?

---

### Post by MadCow108 on 2011-03-16
> **rosswmcgee said:**
> I read that the Open Office folks were also working on Libre and Oracle felt it was 

a conflict of interest, so many just left Open office.


Yesterday I did my natty updates, and then a partial upgrade. All is well, but I was wondering if I keep doing the latter two things will I at the end have a total upgrade of the completed 11.04???

when you keep upgrading your alpha it will in the end be 11.04 (+ maybe some obsolete stuff from 10.04).

But beware, using an alpha version is dangerous and should only be done when you have enough experience with the system and do not require a working system at all times. E.g. partial upgrades can break your system, see the sticky in the natty forum.

---

### Post by r-senior on 2011-03-16
If you understand what I mean by this, and it's a good thing, I've hardly even noticed LibreOffice is on my Natty test machine. I saw the logo change but then I've been using it between filing bug reports without any further thought: Opened email attachments with it, worked with a couple of spreadsheets, reviewed a presentation, printed some labels.

Better font rendering than I have with OpenOffice on Maverick too. It's something to look forward to using.

---

### Post by rosswmcgee on 2011-03-16
Yes I have seen no difference in performance, but I mostly do spread sheets.

---

### Post by bruce89 on 2011-03-17
LibreOffice is basically go-oo, which was being used by distros anyway.

---

### Post by zika on 2011-03-25
Should libtextcat-data-utf8 be removed or should I wait for upgrade?
I've read changelogs but, no clear answer. I'm inclined to remove, but...

---

### Post by Harry33 on 2011-03-25
> **zika said:**
> Should libtextcat-data-utf8 be removed or should I wait for upgrade?
I've read changelogs but, no clear answer. I'm inclined to remove, but...

Libreoffice-core_3.3.2-1ubuntu2 depends on libtextcat0.
Libtextcat0_2.2-9ubuntu2 depends on libtextcat-data.
Libtextcat-data conflicts and replaces libtextcat-data-utf8.

So definitely libtextcat-data-utf8 is to be removed.

---

### Post by zika on 2011-03-25
> **Harry33 said:**
> Libreoffice-core_3.3.2-1ubuntu2 depends on libtextcat0.
Libtextcat0_2.2-9ubuntu2 depends on libtextcat-data.
Libtextcat-data conflicts and replaces libtextcat-data-utf8.

So definitely libtextcat-data-utf8 is to be removed.Removed...
Thank You...

---

### Post by encefalocardia on 2011-03-25
> **kaldor said:**
> First, be aware that 11.04 is still an alpha; expect a load of problems.

However, at least for me. It's a very stable alpha. Yeah, sometimes some apps crash, specially Compiz. But never the entire system.

---

