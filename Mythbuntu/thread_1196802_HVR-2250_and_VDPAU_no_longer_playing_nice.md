---
title: "HVR-2250 and VDPAU no longer playing nice"
date: 2009-06-25
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-06-25
I did an update using JY Avenard’s repositories via synaptic update earlier this week and the backend no longer recognizes my HVR-2550 tuners.  I tried reinstalling the drivers but still the backend “could not detect the tuner hardware” ant the information center in the frontend says the tuners are unavailable.  I deleted the tuners but I was unable to add them again.  Does anyone have any suggestions?  Is there a way to add the mercurial repositories to synaptic?

---

### Post by LowSky on 2009-06-25
sorry but could you link to JY Avenard&#8217;s repos, and what it exactly updated?

---

### Post by epi 1:10,000 on 2009-06-26
[http://www.avenard.org/files/ubuntu-repos/release/](http://www.avenard.org/files/ubuntu-repos/release/)
 
anything dated after Jun 14 09  which includes:
 
 
[Packages.gz]("http://www.avenard.org/files/ubuntu-repos/release/Packages.gz")
[Sources.gz]("http://www.avenard.org/files/ubuntu-repos/release/Sources.gz") 
[libmyth-0.21-0_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb]("http://www.avenard.org/files/ubuntu-repos/release/libmyth-0.21-0_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb") 
[libmyth-dev_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb]("http://www.avenard.org/files/ubuntu-repos/release/libmyth-dev_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb") 
[libmyth-perl_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb]("http://www.avenard.org/files/ubuntu-repos/release/libmyth-perl_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb") 
[libmyth-python_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb]("http://www.avenard.org/files/ubuntu-repos/release/libmyth-python_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb")
[mythtv-backend-master_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb]("http://www.avenard.org/files/ubuntu-repos/release/mythtv-backend-master_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb")  
[mythtv-backend_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb]("http://www.avenard.org/files/ubuntu-repos/release/mythtv-backend_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb") 
[mythtv-database_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb]("http://www.avenard.org/files/ubuntu-repos/release/mythtv-database_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb")
[mythtv-doc_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb]("http://www.avenard.org/files/ubuntu-repos/release/mythtv-doc_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb")
[mythtv-frontend_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb]("http://www.avenard.org/files/ubuntu-repos/release/mythtv-frontend_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb")
[mythtv-transcode-utils_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb]("http://www.avenard.org/files/ubuntu-repos/release/mythtv-transcode-utils_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.deb") 
[mythtv_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb]("http://www.avenard.org/files/ubuntu-repos/release/mythtv_0.21.0+fixes-20722-openglvdpau-0ubuntu5_all.deb")
[mythtv_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.changes]("http://www.avenard.org/files/ubuntu-repos/release/mythtv_0.21.0+fixes-20722-openglvdpau-0ubuntu5_amd64.changes") 
 
Prety much all dated June 19 09

---

### Post by epi 1:10,000 on 2009-06-30
I'm such a brainless linux noob
 
Problem solved:
 
On the last symantic update it mush have updated the kernel and messed up the HVR-2250 drivers. 
 
Fix:
 
Delete all the previous HVR-2250 install folders then download and reinstall the driver. (lowstar's install tutorial worked)
 
Sorry for the 2 thread post.

---

### Post by ian dobson on 2009-07-01
Hi,

If it's solved,please mark this thread as solved.

Regards
Ian Dobson

---

### Post by epi 1:10,000 on 2009-07-01
[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

