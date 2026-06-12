---
title: "Enna - can't install"
date: 2010-12-15
forum: Multimedia Software
---

### Post by clint8679 on 2010-12-15
I'm trying to install Enna media centre but having trouble.

When I try to install through the Software Centre, I get a message saying package dependencies can not be resolved.  

Can anyone help me with this?

---

### Post by michaeldemetrus on 2010-12-17
I'm having the same problem.  I tried DLing everything individually and the one component that doesn't seem to work is "debugging symbols for enna"

---

### Post by abumaia on 2010-12-22
It seems you need to add the geexbox repository to your sources for it to install.  However, you may get a warning about most of the files to be installed not being authenticated.  I have yet to find any information about how to get this authentication.

---

### Post by Siddhartha Valmont on 2010-12-24
> **clint8679 said:**
> I'm trying to install Enna media centre but having trouble.

When I try to install through the Software Centre, I get a message saying package dependencies can not be resolved.  

Can anyone help me with this?

Hi clint8679,

I run into the same issue as you on a fresh install of Ubuntu 10.10 amd64. It seems that as of today (24dec2010), the enna metapackage is referencing old packages that are no longer available on Maverick repositories.

I have successfully installed Enna by using the following approach with Synaptic :

=> search for enna package, try to install it and copy paste the unresolved dependencies on a text editor

=> add in Configuration>Repositories menu in other software tab the lucid main and universe repos
(for example : deb [http://[URL](http://[URL)="http://ubuntu.media.mit.edu/ubuntu//pool/main/e/evas/libevas-svn-06-engines-core_0.9.9.49898-1_amd64.deb"]ubuntu.media.mit.edu/ubuntu/[/URL] lucid main universe)

=> once the repos are added and the cache refreshed, you can search for the svn-05 missing deps and try to install all the packages from the list you got pasted in the text editor

WARNING ! You will experience a conflict for 2 or 3 packages that are existing also in a newer version in maverick repos. Don't panic !

Just search for the package that is mentionned "will not be installed" and use the Packets>Force a version to force the lucid one and then select for (re)install the packet.

Once you are all set with the missing dependencies, you will be able to install the enna metapackage.


WARNING !! Beware that the packages you have force on an older version will be candidate when you update your system. You can choose to use Packets>Block version to ensure that an update won't break your install.

Nevertheless, you will have to un-block the packages once the metapackage will be corrected by the ubuntu packaging team to benefit from the newer Maverick packets.

---

