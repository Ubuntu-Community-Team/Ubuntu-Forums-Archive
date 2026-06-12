---
title: "LibreOffice is in Natty repos"
date: 2011-01-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-19
Finally, LibreOffice finds its way to the Natty official repos.
The version is 3.3 rc3.
Here:
[https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0~rc3-2ubuntu1](https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0~rc3-2ubuntu1)

Easiest way to make this shift away from OpenOffice is to purge it.
Use synaptic to completely remove Openoffice packages (do not forget these:
python-uno, ttf-opensymbol, uno-libs3 and ure). This will leave the personal settings in your home directory.
Then install LibreOffice packages (with synaptic of course), same packages (see synaptics file -> history.
And the last move is to remove the .openoffice folder from your home directory.

---

### Post by buzzmandt on 2011-01-19
how does it differ from openoffice? Obviously you think its better, sell me on it.

---

### Post by buzzmandt on 2011-01-19
how does it differ from openoffice? Obviously you think its better, sell me on it.

---

### Post by geojorg on 2011-01-19
When will it be replaced openoffice in favor o libreoffice ?

---

### Post by geojorg on 2011-01-19
When will it be replaced openoffice in favor o libreoffice ?

---

### Post by anders_c_ on 2011-01-19
Has it been decided if Ubuntu will switch to Libre yet?

---

### Post by MacUntu on 2011-01-19
Practically, yes: [https://lists.ubuntu.com/archives/ubuntu-devel/2011-January/032298.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-January/032298.html)

---

### Post by BwackNinja on 2011-01-20
Updates makes OpenOffice a transitional package bringing in LibreOffice now.

---

### Post by Anduu on 2011-01-20
Just ran an update/upgrade now,,,,Libreoffice is being installed on my system as I type this.

Seems for now it is default?

EDIT:Forcing me to uninstall openoffice.org-base

---

### Post by zika on 2011-01-20
Should we uninstall openoffice* or will that be handled later? Now I have working LibreOffice and (only one)leftover in Office menu: openoffice-Formula with many OpenOffice packages still in place, I presume transitional...

---

### Post by rburkartjo on 2011-01-20
zika, my daughter has used openoffice for years. when i got a second hard drive for windows7 i installed libre on it. she has not noticed any difference nor have i. you can uninstall open if you want to. up to you

---

### Post by zika on 2011-01-20
I was talking about stubs left behind as transitional packages...

---

### Post by Harry33 on 2011-01-20
> **zika said:**
> I was talking about stubs left behind as transitional packages...

Yes the transitional packages are there only because this way one could switch to LibreOffice by only updating OpenOffice.
So remove the transitional packages, and do not forget the folder .openoffice.org in your home directory.

---

### Post by MacUntu on 2011-01-20
Transitional packages usually aren't automatically deleted, if that was your question.

---

### Post by ccw on 2011-01-20
Honestly, you should probably just keep them until the ubuntu-desktop dependencies are converted. 

currently...
ubuntu-desktop -> depends on OOO which -> depends on libreoffice

---

### Post by ratcheer on 2011-01-20
So, is it time to remove the Libreoffice PPA from our Software Sources?

Tim

---

### Post by zika on 2011-01-20
> **MacUntu said:**
> Transitional packages usually aren't automatically deleted, if that was your question.Yes, that might be the true meaning of my question.
As i get (even more) old I get a bit less trigger(read „purge“)-happy... :)

[http://www.ubuntu-rs.org/forum/Thread-Ubuntu-11-04-Natty-Narwhal-Alpha-1?pid=153858#pid153858](http://www.ubuntu-rs.org/forum/Thread-Ubuntu-11-04-Natty-Narwhal-Alpha-1?pid=153858#pid153858)

---

### Post by Harry33 on 2011-01-20
> **ratcheer said:**
> So, is it time to remove the Libreoffice PPA from our Software Sources?
Tim

Exactly this.

---

### Post by Harry33 on 2011-01-20
> **ccw said:**
> Honestly, you should probably just keep them until the ubuntu-desktop dependencies are converted. 
currently...
ubuntu-desktop -> depends on OOO which -> depends on libreoffice

Then again, who needs these meta-packages.
I want freedom of choise, and delete those out of my way.

---

### Post by Funnnny on 2011-01-20
You want a freedom of choice, but every others want a working desktop with no touch in synaptic or aptitude. All they know is Ubuntu Software Center and Update-Manager :)

---

### Post by Harry33 on 2011-01-21
> **Funnnny said:**
> You want a freedom of choice, but every others want a working desktop with no touch in synaptic or aptitude. All they know is Ubuntu Software Center and Update-Manager :)

Well well, given that, without reasonable know-how on synaptic and meta-packages, people perhaps should stick to published ubuntu distros, not dev versions.
Managing dev time bugs often really demands the use of synaptic.

---

### Post by Harry33 on 2011-01-21
The LibreOffice3.3 rc4 is out and arrived into Natty repos.
Here:
[https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0~rc4-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0~rc4-1ubuntu1)

---

### Post by mc4man on 2011-01-21
> **ccw said:**
> Honestly, you should probably just keep them until the ubuntu-desktop dependencies are converted. 

currently...
ubuntu-desktop -> depends on OOO which -> depends on libreoffice

Don't see that at all, only as a recommend. Any way i think the best way atm was in post 1, when done you can always search the libreoffice package in synaptic (meta  again), and it will show you what else is available, either thru it's 'mark recommended' or suggested' dropdowns or in the description area itself

---

### Post by garvinrick4 on 2011-01-21
#MY libreoffice came in normal updates using aptitude safe-upgrade and then
removed transitional packages of openoffice in synaptices and all seems to be working fine.
#Did have a .openoffice in home to remove.

---

### Post by Glenn nl on 2011-01-21
When will LO get global menu support?

---

### Post by Zlatan on 2011-01-21
> **Glenn nl said:**
> When will LO get global menu support?

should happen somewhere until April obviously:)

---

### Post by Harry33 on 2011-01-24
For those, who keep ubuntu-meta packages installed.
The new version (1.213) dropped OpenOffice and added LibreOffice as desktop-recommends.

---

### Post by mpjbrennan on 2011-01-26
If you are using OpenOffice as a front end for a MySQL or PostgreSQL database, don't drop it for Libreoffice until you have checked out the database connections. It isn't a simple cut and paste job.

Patrick

---

### Post by Harry33 on 2011-01-26
LibreOffice 3.3 has been released.
Here is the announcement:

[http://listarchives.documentfoundation.org/www/announce/msg00026.html](http://listarchives.documentfoundation.org/www/announce/msg00026.html)

---

### Post by Harry33 on 2011-01-26
Now this is fast.

LibreOffice 3.3 final is already building in Natty repos.
See this:
[https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0-1ubuntu1)

---

### Post by Zlatan on 2011-02-03
> **Harry33 said:**
> Now this is fast.

LibreOffice 3.3 final is already building in Natty repos.
See this:
[https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/libreoffice/1:3.3.0-1ubuntu1)

yay! I'm excited:) love ubuntu crew for picking up new stuff quickly

---

