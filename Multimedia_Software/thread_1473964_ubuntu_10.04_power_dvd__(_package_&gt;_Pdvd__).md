---
title: "ubuntu 10.04 power dvd  ( package &gt; Pdvd  )"
date: 2010-05-05
forum: Multimedia Software
---

### Post by lostman121 on 2010-05-05
HI I bought the power dvd half a year ago and now it wont work.

worked great on 9.10 but after upgrade it will not start at all.

error messages below.

./version.kc
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/koan/Src/koan/platform/__init__.py", line 108, in <module>
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 72, in import_hook
ImportError: No module named PIL
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/koan/Src/koan/__init__.py", line 123, in <module>
ImportError: cannot import name GetTime
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/mm/MediaCtrl/__init__.py", line 45, in <module>
AttributeError: 'module' object has no attribute 'EventManager'
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/Common/EntryBrowser.py", line 7, in <module>
ImportError: cannot import name mcobj
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/Common/__init__.py", line 5, in <module>
ImportError: cannot import name mcobj
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 352, in <module>
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/startup_dist.py", line 64, in main
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/root.py", line 384, in main
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/root.py", line 328, in InitPath
AttributeError: 'module' object has no attribute 'SetPath'

---

### Post by Crashedata on 2010-08-04
> **lostman121 said:**
> HI I bought the power dvd half a year ago and now it wont work.

worked great on 9.10 but after upgrade it will not start at all.

error messages below.

./version.kc
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/koan/Src/koan/platform/__init__.py", line 108, in <module>
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 72, in import_hook
ImportError: No module named PIL
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/koan/Src/koan/__init__.py", line 123, in <module>
ImportError: cannot import name GetTime
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/mm/MediaCtrl/__init__.py", line 45, in <module>
AttributeError: 'module' object has no attribute 'EventManager'
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/Common/EntryBrowser.py", line 7, in <module>
ImportError: cannot import name mcobj
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 178, in kImport_module
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 332, in LoadKoanModule
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/Common/__init__.py", line 5, in <module>
ImportError: cannot import name mcobj
KImport fail
Traceback (most recent call last):
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/version.py", line 352, in <module>
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/startup_dist.py", line 64, in main
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/root.py", line 384, in main
  File "/home/david/SVN/pdvdlinux_ubuntu/trunk/PCM4/root.py", line 328, in InitPath
AttributeError: 'module' object has no attribute 'SetPath'

I just upgraded to 10.04 today, and I am receiving the same damn error... pretty f(badword)ked up that a piece of software that cost me $50.00 just stops working because of an upgrade. Canonical needs to get their (stuff that comes out of a sphincter) together if they plan to offer commercial software.

What I want to know is why in the heck is it looking for /home/david/* when my name is not david, and no one under that name has ever used my laptop? Of course there is no home directory for David! Did Ciberlink/Can. pull that name out of their asses?

---

### Post by mc4man on 2010-08-04
> I just upgraded to 10.04 today, and I am receiving the same damn error... ect., ect.

I believe you're misinterpreting the error messages, no matter.

I'd go to whatever account you created when purchasing the software, download and try a re-install. If powerdvd works, great, if not then try contacting the cyberlink cs. or remember the saying "buyer beware"
(were you given any indication that pdvd would remain 'workable' in future ubuntu releases via an 'upgrade'?

---

### Post by aeiah on 2010-08-04
maybe you should look at the sourcecode



oh wait.

---

### Post by _march_ on 2010-10-18
I don't own a copy of PowerDVD 4 Linux but the problem may perhaps be solved by using lokicompat or creating a symlink (libpython2.5/libpython2.6).

[LIST]
[*][http://www.swanson.ukfsn.org/loki/](http://www.swanson.ukfsn.org/loki/)
[*][http://translate.google.de/translate?js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FSpiele%2FLoki_Compat](http://translate.google.de/translate?js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FSpiele%2FLoki_Compat)
[/LIST]

---

### Post by solitaire on 2010-10-18
Pdvd requires Python2.5 
10.04 and 10.10 have Python2.6 installed so the old pDVD won't install or work.
Since it's not been updated for a while (well since 9.10 was released) Looks like they are not bothering with new versions at the moment!

If I recall the Support was OK when I first got pdvd (in '08 ) they are a bit slow to reply but they get the job done.

If you lodge a support ticket they might compile a new version for the 10.## users!!

---

