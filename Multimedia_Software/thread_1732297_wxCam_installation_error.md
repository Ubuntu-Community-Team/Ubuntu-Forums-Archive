---
title: "wxCam installation error"
date: 2011-04-18
forum: Multimedia Software
---

### Post by Nonito on 2011-04-18
I would like to install **[COLOR=navy]wxCam[/COLOR]** in Ubuntu 10.04 and I have downloaded the file **wxcam_1.0.7_i386.deb**
  
  Then I have installed with Synaptic Package Manager the following packages:
  llbwxbase2.8-0
  libwxbase2.8-dev
  libwxgtk2.8-0
  libwxgtk2.8-dev
  libxvidcore4
  libxvidcore-dev
   
  Next step is double click on **wxcam_1.0.7_i386.deb**
  And I obtained the following error:
  **Error: Dependency is not satisfiable: libwxbase2.8-0 (>=2.8.11.0)**
   
  Synaptic Package Manager shows me that the latest version is **2.8.10.1-oubuntu1.2**. So what means (>=2.8.11.0) ?
   
  When I remove the packages  “libwxbase”, then again I have the same error.
   
  What is the right procedure to install wxCam?

---

### Post by no2498 on 2011-04-18
try a different number of wxcam
on my 2 computers both running 10.04 
1 has 1.0.6 other has 1.0.5
i could not get 1.0.7 to go myself

---

### Post by dniMretsaM on 2011-04-18
After a little bit of googleing I read that someone else who couldn't get this to work fixed it by upgrading to Ubuntu 10.10. Also, I have 10.10 and libwxbase 2.8.11.0 is available in Synaptic. See attached image for proof. Apparently this version is not supported by 10.04 so your options are (a) upgrade to Ubuntu 10.10 or (b) use an earlier version of wxCam compatible with libwxbase 2.8.10.1.

---

### Post by no2498 on 2011-04-18
wxcan works fine for me on both computers

---

### Post by dniMretsaM on 2011-04-18
> **no2498 said:**
> wxcan works fine for me on both computers

Yes, but you are using an earlier version which is compatible with 2.8.10.1 which is the highest available version on Ubuntu 10.04.

---

