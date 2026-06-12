---
title: "Can't install Cinelerra - E: Broken Packages"
date: 2008-11-08
forum: Multimedia Software
---

### Post by tom66 on 2008-11-08
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
             Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.1.0-2svn20071030) but it is not going to be installed
E: Broken packages

```

Any help appreciated. Ubuntu Linux 8.10 Intrepid Ibex.

---

### Post by Yellow Pasque on 2008-11-08
Those dependencies look to be for Debian.

Try this: [http://www.cinelerra.org/getting_cinelerra.php#intrepid](http://www.cinelerra.org/getting_cinelerra.php#intrepid)

---

### Post by tom66 on 2008-11-09
```

thomas@minerva:~$ echo deb http://akirad.cinelerra.org akirad-intrepid main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update 
[sudo] password for thomas: 
deb http://akirad.cinelerra.org akirad-intrepid main
OK
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB
Get: 1 http://gb.archive.ubuntu.com intrepid Release.gpg [189B]                
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB               
Hit http://akirad.cinelerra.org akirad-intrepid Release.gpg                    
Ign http://akirad.cinelerra.org akirad-intrepid/main Translation-en_GB         
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
Hit http://security.ubuntu.com intrepid-security Release                       
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB           
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB       
Ign http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB   
Ign http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB 
Hit http://akirad.cinelerra.org akirad-intrepid Release                        
Get: 2 http://gb.archive.ubuntu.com intrepid Release [65.9kB]                  
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://gb.archive.ubuntu.com intrepid-updates Release                      
Hit http://akirad.cinelerra.org akirad-intrepid/main Packages                  
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Get: 3 http://gb.archive.ubuntu.com intrepid/main Packages [1256kB]            
Ign http://www.kiberpipa.org ./ Release.gpg                               
Ign http://www.kiberpipa.org ./ Translation-en_GB                         
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Ign http://www.kiberpipa.org ./ Release                 
Ign http://www.kiberpipa.org ./ Packages                
Hit http://www.kiberpipa.org ./ Packages
Get: 4 http://gb.archive.ubuntu.com intrepid/restricted Packages [8408B]
Get: 5 http://gb.archive.ubuntu.com intrepid/main Sources [505kB]
Get: 6 http://gb.archive.ubuntu.com intrepid/restricted Sources [3113B]
Get: 7 http://gb.archive.ubuntu.com intrepid/universe Packages [4542kB]
Get: 8 http://gb.archive.ubuntu.com intrepid/universe Sources [1981kB]         
Get: 9 http://gb.archive.ubuntu.com intrepid/multiverse Packages [199kB]       
Get: 10 http://gb.archive.ubuntu.com intrepid/multiverse Sources [95.8kB]      
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages                
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources                 
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources           
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources           
Fetched 8657kB in 31s (279kB/s)                                                
Reading package lists... Done
thomas@minerva:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
             Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.1.0-2svn20071030) but it is not going to be installed
E: Broken packages
thomas@minerva:~$ 

```

Still not working. Thanks for your help though.
Tom

---

### Post by Vinno on 2008-11-10
Same thing here.

---

### Post by mike4ubuntu on 2008-12-24
worked for me in Intrepid:

=========================================
$ wget -q [http://akirad.cinelerra.org/pool/addakira](http://akirad.cinelerra.org/pool/addakira)
d.deb && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
[sudo] password for mike:
Selecting previously deselected package akirad-keyring-and-mirrors.
(Reading database ... 163717 files and directories currently installed.)
Unpacking akirad-keyring-and-mirrors (from addakirad.deb) ...
Setting up akirad-keyring-and-mirrors (2008.09.23) ...
OK
update-rc.d: warning: /etc/init.d/akiradrelease missing LSB style header
 Adding system startup for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc1.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc6.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc2.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc3.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc4.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc5.d/S20akiradrelease -> ../init.d/akiradrelease

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Get:1 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid Release.gpg [197B]
Ign [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main Translation-en_US
Get:2 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid Release [3534B]
Get:3 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main Packages [13.4kB]
Fetched 17.1kB in 1s (10.8kB/s)
Reading package lists... Done
mike@lic3:/opt/cinelerra/cinelerra-4-ubuntu-i686$
mike@lic3:/opt/cinelerra/cinelerra-4-ubuntu-i686$
mike@lic3:/opt/cinelerra/cinelerra-4-ubuntu-i686$
mike@lic3:/opt/cinelerra/cinelerra-4-ubuntu-i686$ which cinelerra
mike@lic3:/opt/cinelerra/cinelerra-4-ubuntu-i686$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwebkit-1.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akiradnews cinelerracv libguicastcv libmpeg3cv libquicktimecv optlibx11-noxcb-6
  optlibx11-noxcb-data
The following NEW packages will be installed:
  akiradnews cinelerra cinelerracv libguicastcv libmpeg3cv libquicktimecv optlibx11-noxcb-6
  optlibx11-noxcb-data
0 upgraded, 8 newly installed, 0 to remove and 5 not upgraded.
Need to get 14.2MB of archives.
After this operation, 31.0MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main optlibx11-noxcb-data 2:1.1.3-1akirad1 [162kB
]
Get:2 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main optlibx11-noxcb-6 2:1.1.3-1akirad1 [611kB]
Get:3 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main libguicastcv 2.1.0-git20081029akirad3 [309kB
]
Get:4 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main libmpeg3cv 2.1.0-git20081029akirad3 [111kB]
Get:5 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main libquicktimecv 2.1.0-git20081029akirad3 [152
8kB]
Get:6 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main akiradnews 20081019 [11.3kB]
Get:7 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main cinelerracv 2.1.0-git20081029akirad3 [11.4MB
]
Get:8 [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main cinelerra 1:2.1.0-1svn20081017akirad2 [1180B
]
Fetched 14.2MB in 16s (837kB/s)
Selecting previously deselected package optlibx11-noxcb-data.
(Reading database ... 163723 files and directories currently installed.)
Unpacking optlibx11-noxcb-data (from .../optlibx11-noxcb-data_2%3a1.1.3-1akirad1_all.deb) ...
Selecting previously deselected package optlibx11-noxcb-6.
Unpacking optlibx11-noxcb-6 (from .../optlibx11-noxcb-6_2%3a1.1.3-1akirad1_i386.deb) ...
Selecting previously deselected package libguicastcv.
Unpacking libguicastcv (from .../libguicastcv_2.1.0-git20081029akirad3_i386.deb) ...
Selecting previously deselected package libmpeg3cv.
Unpacking libmpeg3cv (from .../libmpeg3cv_2.1.0-git20081029akirad3_i386.deb) ...
Selecting previously deselected package libquicktimecv.
Unpacking libquicktimecv (from .../libquicktimecv_2.1.0-git20081029akirad3_i386.deb) ...
Selecting previously deselected package akiradnews.
Unpacking akiradnews (from .../akiradnews_20081019_all.deb) ...
Selecting previously deselected package cinelerracv.
Unpacking cinelerracv (from .../cinelerracv_2.1.0-git20081029akirad3_i386.deb) ...
Selecting previously deselected package cinelerra.
Unpacking cinelerra (from .../cinelerra_1%3a2.1.0-1svn20081017akirad2_i386.deb) ...
Processing triggers for man-db ...
Setting up optlibx11-noxcb-data (2:1.1.3-1akirad1) ...
Setting up optlibx11-noxcb-6 (2:1.1.3-1akirad1) ...

Setting up libguicastcv (2.1.0-git20081029akirad3) ...

Setting up libmpeg3cv (2.1.0-git20081029akirad3) ...

Setting up libquicktimecv (2.1.0-git20081029akirad3) ...

Setting up akiradnews (20081019) ...

Setting up cinelerracv (2.1.0-git20081029akirad3) ...
update-rc.d: warning: /etc/init.d/cinestart missing LSB style header
 Adding system startup for /etc/init.d/cinestart ...
   /etc/rc0.d/K20cinestart -> ../init.d/cinestart
   /etc/rc1.d/K20cinestart -> ../init.d/cinestart
   /etc/rc6.d/K20cinestart -> ../init.d/cinestart
   /etc/rc2.d/S20cinestart -> ../init.d/cinestart
   /etc/rc3.d/S20cinestart -> ../init.d/cinestart
   /etc/rc4.d/S20cinestart -> ../init.d/cinestart
   /etc/rc5.d/S20cinestart -> ../init.d/cinestart

Setting up cinelerra (1:2.1.0-1svn20081017akirad2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


$ which cinelerra
/usr/bin/cinelerra

---

### Post by drkitty on 2010-06-24
Go [http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu")- this solved my broken package problems

---

