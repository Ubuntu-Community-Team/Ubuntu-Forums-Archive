---
title: "Embedded pdf viewer (adobe) in firefox has problem viewing pdfs"
date: 2010-01-19
forum: Multimedia Software
---

### Post by CUJimmy on 2010-01-19
Hi All,

Since I updated to 9.10, I have had problems viewing pdfs in firefox with the embedded adobe reader. Strangely enough, on starting firefox, I am able able to view one pdf, save it etc. However, within the same firefox session, if I then go on to try and find and view a second pdf, it does not render on the screen. Instead I am left with a blank window. Upon closing firefox and starting again, I am again able to view a single pdf before the problem happens again. Does anyone know why this might be?!

Thanks, Jim

---

### Post by mike-g2 on 2010-07-02
Alas, I have the same problem but no solution other than restarting FF.

I hope someone more knowledgeable can chime in.

Mike

---

### Post by popov74 on 2011-02-15
I have the same problem and I have found no solution so far. The only workaround is to install mozplugger, which opens the whole acroread within firefox as if it was a plugin. It looks somehow worse but it works. The only problem is that sometimes it opens acroread externally instead of embedding the application within firefox. Maybe this is related with the problem that makes the native plugin crash.

---

### Post by spottraining on 2011-03-11
I have the same problem. Firefox is able to show only first PDF file. After that - all are blanks pages. It work three days ago norally- what now happens - I don't know.

---

### Post by nnahler on 2011-04-08
Exactly the same problem: Opens the first PDF fine and afterwards shows a blank tab.

I am running Ubuntu 10.04 LTS 64bit, Firefox 3.6.16, Adobe Reader 9.3

Any help would certainly be appreciated as this is a rather annoying problem. 

Thanks

---

### Post by fabio.hipolito on 2011-05-05
Hi there,

The same problem with 11.04 AMD64.
The first always open normally and I have no problem while I keep at least one pdf open in a tab. If I close all tabs then I have problems, every time I try to open a pdf in firefox I get either a black or white tab.

If I look for acroread, I get a zombie process that I cannot kill.

Thanks.

---

### Post by beew on 2011-05-06
Why don't you just use the document viewer (evince) to read embedded pdf? Fast and problem free.

---

### Post by filiatra on 2011-05-19
Same problem here (on ubuntu natty), I have to do a "killall acroread" before being able to reopen embedded pdf normally..

---

### Post by cerberanke on 2011-06-10
Exactly the same problem on AMD64 with 11.04 (also on earlier versions) :(

---

### Post by chaeron on 2011-07-21
Same issue here...still on 64 bit Lucid, with all recent updates, Firefox 4.0.1. Latest Acroread 9.4.2

Had this problem for some time...I suspect it's a 64 bit issue.

Real PITA...has anyone found a solution yet?

---

### Post by prosist on 2011-10-13
Same problem here.
Using Lucid 64

---

### Post by wmccarty on 2011-10-18
Same problem using Lucid 64 as well.

Can we Bump this problem? Where do we send this to Adobe - Firefox - Conical?

---

### Post by beew on 2011-10-18
Install gpdf addon for Firefox, or install mozplugger and use evince as the embedded pdf viewer. Forget about acroread, all it does it slow down your system.

---

### Post by skitheo on 2011-11-07
I'm seeing the same behavior with FF 7.0 (from Mozilla PPA), Acroread 9.4 (from Canonical Partners) on 

@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

Starting FF from the terminal and loading a PDF from a web site, when clicking the FF "back" button, AcroRead emits hundreds of the following:

(acroread:27288): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:27288): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:27288): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

Then Acroread becomes a zombie process and no further PDF's can be read from within FF.

Looks like it is well documented in[ bug 571247]("https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/571247")


[COLOR=Red]**UPDATE: Workaround**[/COLOR]: Keep one PDF open in a tab at all times, then acroread will continue to communicate with FF and remain active.

---

### Post by peredur on 2011-11-28
Yeah.  Same problem here.  Thanks for the workaround.  Not ideal, but OK for now.

BTW, I found that when the pdf document fails to display in FF, you can still do File --> Save and save the pdf to view in your viewer of choice.  I mention this just as a curiosity rather than as a suggestion.

Cheers


PAE

---

### Post by xadder on 2012-02-07
I'm having the same problem with Ubuntu 11.10, on a 32bit Thinkpad clean install. Has anyone solved this yet?  And please, don't tell me to use evince -- I like and use evince too, but prefer acroread as my default. I think that loading pdf's and reading with acrordead should not cause pain for normal users...

Thanks!

---

### Post by xadder on 2012-02-20
bump

---

### Post by dschaller on 2012-02-24
I've had this same issue for a long time (a least a year) and thought it must just be some configuration problem on my end that I couldn't figure out. But I see now that I'm not alone. This is really an annoying problem. Sometimes I can't open anything, other times I can open one, maybe two PDF files and after that just blank screens. Sometimes hitting the page reload button works and sometimes it doesn't. Sometimes it will work correctly, but more often than not it doesn't. I can't figure out why it works or why it doesn't. I'm on 10.04 with Acrobat Reader 9.4.2.

---

### Post by DaBzzz on 2012-02-25
Kill npviewer.bin and reload the pdf. And, if you are experiencing the problem very often, set a global hotkey for killing npviewer ;)
Notice that this might also kill all standalone windows of acroread.

---

### Post by shevek. on 2012-02-26
Same problem, Ubuntu 11.10 x64, Firefox 10.0.2, Adobe Reader 9.4.

Workaround of #19 worked for me, by killing that process, everything works fine... annoying but works. Thanks a lot!

---

### Post by jgehrcke on 2012-02-29
I would like to add myself to this list. Same problem here.

---

### Post by xadder on 2012-08-04
I'm still being plagued by this problem. Did anyone find a good solution to this yet? 

I'm running a clean install of 12.04, 32bit. 

Why is such a basic combination (firefox+acroread) not working?

Thanks!

---

