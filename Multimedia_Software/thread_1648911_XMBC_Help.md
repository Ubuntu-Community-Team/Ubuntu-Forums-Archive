---
title: "XMBC Help"
date: 2010-12-19
forum: Multimedia Software
---

### Post by TimEnid on 2010-12-19
I installed XMBC and i keep getting this message

"Error 
XBMC needs hardware accelerated OpenGL rendering. Install an appropirate graphic driver"

i have a radeon 5750 hd graphics card. i updated the drive thru the website. but i keep getting this message. any solutions.

---

### Post by Yellow Pasque on 2010-12-19
> i updated the drive thru the website
What website? Are you running opne-source or proprietary driver? Post output of glxinfo:
```
sudo apt-get install mesa-utils
export LIBGL_DEBUG=verbose; glxinfo
```

---

### Post by TimEnid on 2010-12-19
> tim@tim-desktop:~$ sudo apt-get install mesa-utils
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
mesa-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tim@tim-desktop:~$ export LIBGL_DEBUG=verbose; glxinfo
name of display: :0.0
libGL error: XF86DRIQueryDirectRenderingCapable returned false
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18


and i downloaded it from this site
[http://support.amd.com/us/psearch/Pages/psearch.aspx](http://support.amd.com/us/psearch/Pages/psearch.aspx)

---

### Post by TimEnid on 2011-01-01
any help

---

### Post by TimEnid on 2011-03-13
anyone?

---

