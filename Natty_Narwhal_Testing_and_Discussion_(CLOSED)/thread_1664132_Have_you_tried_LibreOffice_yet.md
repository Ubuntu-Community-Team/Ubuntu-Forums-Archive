---
title: "Have you tried LibreOffice yet?"
date: 2011-01-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-10
Ubuntu will switch from OpenOffice.org to the new LibreOffice.
The reasoning behind this is that the new LibreOffice may be better developed to match the needs of Ubuntu.
It can be installed from the LibreOffice PPA.
Here: [https://launchpad.net/~libreoffice/+archive/ppa/](https://launchpad.net/~libreoffice/+archive/ppa/)

I have installed it into both Maverick and Natty.
The version 3.3.0 rc2 is available ATM.

Note that, installing LibreOffice means that you have to uninstall OpenOffice.org first.

---

### Post by abdulapopoola on 2011-01-10
But is LibreOffice really better than OpenOffice.org? And why the need for the change?

Open source rocks!!!
[http://abdulapopoola.wordpress.com](http://abdulapopoola.wordpress.com)

---

### Post by cariboo on 2011-01-10
I've been using LibreOffice since the ppa became available, on all my systems, Libreoffice loads faster than OracleOffice.org. :) otherwise I haven't noticed any difference. The reason for the change is more due to politics than anything else.

---

### Post by zerubbabel on 2011-01-10
I've been using it since the first Beta was announced. No complaints.

---

### Post by jfernyhough on 2011-01-10
Ah, been waiting for a PPA for a while. Excellent.

Have been using the version from the LibreOffice website for the past few weeks, all seems fine. Had a couple of crashes with the first (alpha?) release but the RCs have been fine.

---

### Post by ScislaC on 2011-01-10
I tried the PPA version of LibreOffice but had an Office 2007 document to edit for someone and their embedded graphics (charts of sorts) were horribly mangled, whereas stock OO.o Natty does not have the same issue. (appears to be a regression)

---

### Post by t1497f35 on 2011-01-11
I only hope that the Java dependencies will be taken out of LibreOffice (completely), I'm myself a Java dev but as some folks acknowledged - it was a "political" move on Sun's side (basically to get more ppl hooked into Java) rather than a technical one to make OpenOffice functionality depend on Java.

---

### Post by West201 on 2011-01-11
No. Where can I get it ?

---

### Post by rburkartjo on 2011-01-11
yes i like and i also put it on my drive that has windows7 on. it seems to be a little slower than openoffice was at first load but after that just as good.

---

### Post by jerrylamos on 2011-01-11
Install complication with Natty.
Removed all of openoffice I could find with Synaptic.

Followed the instructions to get a LibreOffice ppa key.  Went O.K.
The update of sources.list didn't work, so I copied the lines.
Upgrade & update didn't install LibreOffice.
Synaptic had LibreOffice so installed it from there.
Seemed to run O.K.  

First test was to select a portion of an internet screen, BBC News with text surrounding graphics.  That seemed to copy O.K.  I'll have to work with it a bit to see if it is O.K. and doesn't get confused by page breaks.

Jerry

---

### Post by KegHead on 2011-01-11
Yes,

w/no problems.

KegHead

---

### Post by ronacc on 2011-01-11
I am filing a bug on libreoffice  , it alters the dependencies of openoffice to read libreoffice . this is reminicent of the windows browser wars of the mid 90's where netscape and IE were busily disabling eachother with each update . This is totaly unacceptable for open source and must not be tolerated . especialy for a PPA app to disable ( and infact make unavailable for install ) a default package . NOTE it does not say conflicts which would be acceptable but instead alters the default synaptic listing , this IMHO is reason enough to boycott libreoffice until they behave.In the past I have had both installed side by side for comparison and did not note that they conflicted in any way so this sudden evil act is suprising .

---

### Post by ronacc on 2011-01-11
bug # 701520  , had to file it against synaptic since LP wouldn't let me file against libreoffice .

NOTE nowhere do the synaptic>properties>dependencies of libreoffice say anything about conflictingwith or breaking OO .

---

### Post by Harry33 on 2011-01-11
> **ronacc said:**
> bug # 701520  , had to file it against synaptic since LP wouldn't let me file against libreoffice .
NOTE nowhere do the synaptic>properties>dependencies of libreoffice say anything about conflictingwith or breaking OO .

The truth is that you cannot have both installed.
LibreOffice is currently not supported by Canonical (Ubuntu).
Anyone using the PPA does that at own risk.

Anyway, the PPA contains transitional OpenOffice packages (3.3.0~rc2-3natty2).
They depend on corresponding LibreOffice packages and should be removed after the installation. Earlier there was something wrong in that setup and the installation did not finish. That is why I consider it better to first remove completely all OpenOffice packages and only then install LibreOffice packages.

Reversing this is only possible by completely manually removing LibreOffice packages first.

More info can be found on this great site here:
[http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html](http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html)

---

### Post by ronacc on 2011-01-11
ppa-purge gets rid of it also . In the past both could be installed at the same time . I understand the implications of using a ppa but he should have given some warning .

---

### Post by Harry33 on 2011-01-11
Here is some more info on this subject (an ubuntu-devel message, lists.ubuntu.com)
**LibreOffice for natty, replacing the current OpenOffice packaging**
[https://lists.ubuntu.com/archives/ubuntu-devel/2011-January/032298.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-January/032298.html)

Note this one:
"The packages definitely need some testing, but else they look ok-ish for 
inclusion in natty for alpha-2.  See the list of issues, and maybe target some 
of these for alpha-2 or alpha-3."

---

### Post by ronacc on 2011-01-11
What I was complaining about was that LO overwrites OO in synaptic and as I said I consider this an unacceptable practice LO should stand on its own merits not masquerade as something it is not, namely OO which it a seperate project and as I stated above smells of the kind of crap that goes on in windows . It is fine if they announce that they are incompatible ( conflicts with) something else but to flatly overwrite the apt entry of another app is bad bad bad . Note I do not have anything against LO as an app and have had previous versions installed for testing I only object to the behavior of the PPA package .

---

### Post by gradinaruvasile on 2011-01-11
It can be installed from here:

[http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86/LibO_3.3.0rc2_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86/LibO_3.3.0rc2_Linux_x86_install-deb_en-US.tar.gz)

or 

[http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86_64/LibO_3.3.0rc2_Linux_x86-64_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86_64/LibO_3.3.0rc2_Linux_x86-64_install-deb_en-US.tar.gz)

Just unpack and install all packages from DEBS folder then the desktop-integration folder. It is standalone installation, does not conflict with anything.

---

### Post by ronacc on 2011-01-11
> **gradinaruvasile said:**
> It can be installed from here:

[http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86/LibO_3.3.0rc2_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86/LibO_3.3.0rc2_Linux_x86_install-deb_en-US.tar.gz)

or 

[http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86_64/LibO_3.3.0rc2_Linux_x86-64_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/3.3.0-rc2/deb/x86_64/LibO_3.3.0rc2_Linux_x86-64_install-deb_en-US.tar.gz)

Just unpack and install all packages from DEBS folder then the desktop-integration folder. It is standalone installation, does not conflict with anything.

thats the way I've always done it in the past and it indeed does still install side by side with OO with no apparent conflicts which makes the PPA's action even worse .

---

### Post by jerrylamos on 2011-01-12
> **ronacc said:**
> thats the way I've always done it in the past and it indeed does still install side by side with OO with no apparent conflicts which makes the PPA's action even worse .

I'm missing something.  Both Open Office and Libre Office chew up a lot of premium disk space on my two laptops.  Why would I want to have both installed at the same time?  I don't want to lose all that space, so I'd use one or the other.  Not both.

With Lubuntu I've tried Abiword, however seems to be pretty short on function such as copying internet selections including text and imbedded graphics.  Abiword will do it by separately copying in the images but I haven't found it to flow the text around the graphics.

Jerry

---

### Post by jacky.alcine on 2011-01-12
Amen, when LibreOffice moves to the C family; that'll be the shift of a century.

---

### Post by ronacc on 2011-01-12
> **jerrylamos said:**
> I'm missing something.  Both Open Office and Libre Office chew up a lot of premium disk space on my two laptops.  Why would I want to have both installed at the same time?  I don't want to lose all that space, so I'd use one or the other.  Not both.

With Lubuntu I've tried Abiword, however seems to be pretty short on function such as copying internet selections including text and imbedded graphics.  Abiword will do it by separately copying in the images but I haven't found it to flow the text around the graphics.

Jerry

To answer your question , I have them both installed to compare (and test) them side by side , I also have ,abiword which is what I use if I have a need for a word processor ( maybe once a year ) for writing notes and letters I use gedit . I am not space poor I have 6 drives and 1.8 TB in my test box and never give an install less than 100 GB ( I like to install lots of things ).

---

