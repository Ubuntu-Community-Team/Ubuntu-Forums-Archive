---
title: "AMD Catalyst Control Panel"
date: 2012-12-02
forum: Multimedia Software
---

### Post by Yunito on 2012-12-02
Well... When I want to install AMD ccpl, I received this message:

 

[QUOTE=Error]Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-19-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.[/QUOTE]

How i resolve it? And How I install AMD Catalyst Control Panel?

---

### Post by Yellow Pasque on 2012-12-02
How did you install the fglrx driver and which version did you install? You need the linux-headers-generic package as well as some others. [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

^Really, instead of doing that, you should just install the fglrx package from the UBuntu repo and it will take care of all that stuff automatically.

---

### Post by Yunito on 2012-12-03
I want to install version 12.10, using .run package.

What I have to install before?

---

