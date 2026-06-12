---
title: "MythWeb, Apache and Hardy"
date: 2009-05-09
forum: Multimedia Software
---

### Post by Deborah Norling on 2009-05-09
I am trying to get mythweb running on 64-bit hardy. I installed apache and a pleuthora of libraries and modules for enabling php that various forum threads recommended.
 
However, I get errors about shared libraries when I try to start apache with
    /etc/init.d/apache2 restart
 
output is similar to this:
* Restarting web server apache2                                                
/usr/sbin/apache2: error while loading shared libraries: libpq.so.5: cannot open
 shared object file: No such file or directory                                  
   ...fail!                                                                     
 
For some of the missing libraries, I've been able to creat symbolic links, but I can't find this libpq library anywhere on my system. Yet apt-get install assures me that libpq5 and libpq5-dev are installed and are the latest version. It also states that they are set to 'manually' install, which I assume means that they load when apache loads.
 
I am not serving any other web pages except mythweb, which is not externally accessed. How can I set up apache properly for mythweb and avoid loading shared libraries not needed by mythweb? How can I ensure it does load the libraries that are required?
 
Debee

---

