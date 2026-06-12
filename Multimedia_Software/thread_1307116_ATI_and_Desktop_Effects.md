---
title: "ATI and Desktop Effects"
date: 2009-10-30
forum: Multimedia Software
---

### Post by PlatosGimp on 2009-10-30
I am running 9.10 upgraded from 9.01 on a Dell Inspiron 9100 with a Mobility Radeon 9600 M10 graphics card. Under 9.10 I had opengl apparently running fine, with compiz desktop effects etc. However, I cant seem to get this working now that I have upgraded to 9.10. Below are some of the details. I also tried re-installing the fglrx (apt-get install xorg-driver-fglrx), but this did not seem to make any difference.


fglrxinfo

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 



Any suggestions?

---

