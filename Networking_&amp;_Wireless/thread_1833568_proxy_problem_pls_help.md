---
title: "proxy problem pls help"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by gayden on 2011-08-26
hi everybody,

1stly i downloaded the latest version of ubuntu using wubi
then i installed backtrack5 on my system bcuz it supports my wireless card
and i setup a proxy to open blocked websites
but here's the problem :-
```
root@bt:/# sudo apt-get install ncurses* gettext
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting lib64ncurses5 for regex 'ncurses*'
Note, selecting libncurses5 for regex 'ncurses*'
Note, selecting libncurses-ruby1.8 for regex 'ncurses*'
Note, selecting libkaya-ncursesw-dev for regex 'ncurses*'
Note, selecting libcunit1-ncurses for regex 'ncurses*'
Note, selecting libncurses-dev for regex 'ncurses*'
Note, selecting libncurses5-dev instead of libncurses-dev
Note, selecting irmp3-ncurses for regex 'ncurses*'
Note, selecting ncurses-base for regex 'ncurses*'
Note, selecting libncurses-gst for regex 'ncurses*'
Note, selecting libncursesw5-dbg for regex 'ncurses*'
Note, selecting libncursesw5-dev for regex 'ncurses*'
Note, selecting ncurses-term for regex 'ncurses*'
Note, selecting ncurses-hexedit for regex 'ncurses*'
Note, selecting libcunit1-ncurses-dev for regex 'ncurses*'
Note, selecting lib64ncurses5-dev for regex 'ncurses*'
Note, selecting libkaya-ncurses-dev for regex 'ncurses*'
Note, selecting libncurses-ruby1.9.1 for regex 'ncurses*'
Note, selecting libncurses-ruby for regex 'ncurses*'
Note, selecting ncurses-runtime for regex 'ncurses*'
Note, selecting ncurses-base instead of ncurses-runtime
Note, selecting libncurses5-dbg for regex 'ncurses*'
Note, selecting libncurses5-dev for regex 'ncurses*'
Note, selecting libncursesw5 for regex 'ncurses*'
Note, selecting ncurses-bin for regex 'ncurses*'
Note, selecting ncurses-developer for regex 'ncurses*'
Note, selecting ncurses for regex 'ncurses*'
Note, selecting ncurses-dev for regex 'ncurses*'
Note, selecting libncurses5-dev instead of ncurses-dev
gettext is already the newest version.
gettext set to manually installed.
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc16 python-pyicu libdebian-installer4 cryptsetup
  libecryptfs0 reiserfsprogs rdate bogl-bterm ecryptfs-utils libdebconfclient0
  dmraid keyutils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.4-multilib gcc-multilib gnu-smalltalk gnu-smalltalk-common
  irmp3-ncurses kaya lib64gcc1 lib64gomp1 lib64ncurses5 lib64ncurses5-dev
  libc6-amd64 libc6-dev-amd64 libcunit1-ncurses libcunit1-ncurses-dev
  libgc-dev libgcrypt11-dev libgnutls-dev libgpg-error-dev libgst7
  libkaya-ncurses-dev libkaya-ncursesw-dev libncurses-gst libncurses-ruby
  libncurses-ruby1.8 libncurses-ruby1.9.1 libncurses5-dbg libncursesw5-dbg
  libncursesw5-dev libpcre3-dev libpcrecpp0 libruby1.9.1 libsigsegv0
  libtasn1-3-dev ncurses-hexedit ncurses-term ruby1.9.1
Suggested packages:
  lib64mudflap0 gnu-smalltalk-doc irmp3 libcunit1-doc libgcrypt11-doc
  gnutls-doc gnutls-bin guile-gnutls ruby1.9.1-examples rdoc1.9.1 ri1.9.1
  rubygems1.9.1
The following NEW packages will be installed:
  gcc-4.4-multilib gcc-multilib gnu-smalltalk gnu-smalltalk-common
  irmp3-ncurses kaya lib64gcc1 lib64gomp1 lib64ncurses5 lib64ncurses5-dev
  libc6-amd64 libc6-dev-amd64 libcunit1-ncurses libcunit1-ncurses-dev
  libgc-dev libgcrypt11-dev libgnutls-dev libgpg-error-dev libgst7
  libkaya-ncurses-dev libkaya-ncursesw-dev libncurses-gst libncurses-ruby
  libncurses-ruby1.8 libncurses-ruby1.9.1 libncurses5-dbg libncursesw5-dbg
  libncursesw5-dev libpcre3-dev libpcrecpp0 libruby1.9.1 libsigsegv0
  libtasn1-3-dev ncurses-hexedit ncurses-term ruby1.9.1
0 upgraded, 36 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.3MB of archives.
After this operation, 84.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6-amd64 ncurses-term libc6-dev-amd64 lib64gcc1 lib64gomp1
  gcc-4.4-multilib gcc-multilib irmp3-ncurses lib64ncurses5 lib64ncurses5-dev
  libcunit1-ncurses libcunit1-ncurses-dev libgc-dev libgpg-error-dev
  libgcrypt11-dev libtasn1-3-dev libgnutls-dev libncurses-ruby1.8
  libncurses-ruby libruby1.9.1 ruby1.9.1 libncurses-ruby1.9.1 libncursesw5-dev
  libpcrecpp0 libpcre3-dev libsigsegv0 ncurses-hexedit libgst7 gnu-smalltalk
  gnu-smalltalk-common kaya libkaya-ncurses-dev libkaya-ncursesw-dev
  libncurses-gst libncurses5-dbg libncursesw5-dbg
Install these packages without verification [y/N]? y
Err http://32.repository.backtrack-linux.org/ revolution/main libc6-amd64 2.11.1-0ubuntu7.8       
  Could not connect to 80.172.172.153:8080 (80.172.172.153), connection timed out
Err http://32.repository.backtrack-linux.org/ revolution/main libc6-dev-amd64 2.11.1-0ubuntu7.8   
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main lib64gcc1 1:4.4.3-4ubuntu5          
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main lib64gomp1 4.4.3-4ubuntu5           
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main gcc-4.4-multilib 4.4.3-4ubuntu5     
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main gcc-multilib 4:4.4.3-1ubuntu1       
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main irmp3-ncurses 0.5.3.1-2             
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main lib64ncurses5 5.7+20090803-2ubuntu3 
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main lib64ncurses5-dev 5.7+20090803-2ubuntu3
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libcunit1-ncurses 2.1-0.dfsg-9      
  Unable to connect to 80.172.172.153:8080:
Err http://all.repository.backtrack-linux.org/ revolution/main ncurses-term 5.7+20090803-2ubuntu3 
  Could not connect to 80.172.172.153:8080 (80.172.172.153), connection timed out
Err http://all.repository.backtrack-linux.org/ revolution/main libncurses-ruby 1.2.4-2            
  Unable to connect to 80.172.172.153:8080:
Err http://all.repository.backtrack-linux.org/ revolution/main gnu-smalltalk-common 3.0.3-2ubuntu0.10.04.1
  Unable to connect to 80.172.172.153:8080:
Err http://all.repository.backtrack-linux.org/ revolution/main libncurses-gst 3.0.3-2ubuntu0.10.04.1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libcunit1-ncurses-dev 2.1-0.dfsg-9  
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libgc-dev 1:6.8-1.2ubuntu1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libgpg-error-dev 1.6-1ubuntu2
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libgcrypt11-dev 1.4.4-5ubuntu2
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libtasn1-3-dev 2.4-1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libgnutls-dev 2.8.5-2
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libncurses-ruby1.8 1.2.4-2
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libruby1.9.1 1.9.1.378-1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main ruby1.9.1 1.9.1.378-1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libncurses-ruby1.9.1 1.2.4-2
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libncursesw5-dev 5.7+20090803-2ubuntu3
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libpcrecpp0 7.8-3build1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libpcre3-dev 7.8-3build1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libsigsegv0 2.5-3
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main ncurses-hexedit 0.9.7-14ubuntu1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libgst7 3.0.3-2ubuntu0.10.04.1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main gnu-smalltalk 3.0.3-2ubuntu0.10.04.1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main kaya 0.4.4-2ubuntu1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libkaya-ncurses-dev 0.4.4-2ubuntu1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libkaya-ncursesw-dev 0.4.4-2ubuntu1
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libncurses5-dbg 5.7+20090803-2ubuntu3
  Unable to connect to 80.172.172.153:8080:
Err http://32.repository.backtrack-linux.org/ revolution/main libncursesw5-dbg 5.7+20090803-2ubuntu3
  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/e/eglibc/libc6-amd64_2.11.1-0ubuntu7.8_i386.deb  Could not connect to 80.172.172.153:8080 (80.172.172.153), connection timed out
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/n/ncurses/ncurses-term_5.7+20090803-2ubuntu3_all.deb  Could not connect to 80.172.172.153:8080 (80.172.172.153), connection timed out
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/e/eglibc/libc6-dev-amd64_2.11.1-0ubuntu7.8_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/g/gcc-4.4/lib64gcc1_4.4.3-4ubuntu5_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/g/gcc-4.4/lib64gomp1_4.4.3-4ubuntu5_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/g/gcc-4.4/gcc-4.4-multilib_4.4.3-4ubuntu5_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/g/gcc-defaults/gcc-multilib_4.4.3-1ubuntu1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/i/irmp3-ncurses/irmp3-ncurses_0.5.3.1-2_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses/lib64ncurses5_5.7+20090803-2ubuntu3_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses/lib64ncurses5-dev_5.7+20090803-2ubuntu3_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/c/cunit/libcunit1-ncurses_2.1-0.dfsg-9_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/c/cunit/libcunit1-ncurses-dev_2.1-0.dfsg-9_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/libg/libgc/libgc-dev_6.8-1.2ubuntu1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/libg/libgpg-error/libgpg-error-dev_1.6-1ubuntu2_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/libg/libgcrypt11/libgcrypt11-dev_1.4.4-5ubuntu2_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/libt/libtasn1-3/libtasn1-3-dev_2.4-1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/g/gnutls26/libgnutls-dev_2.8.5-2_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses-ruby/libncurses-ruby1.8_1.2.4-2_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/n/ncurses-ruby/libncurses-ruby_1.2.4-2_all.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/r/ruby1.9.1/libruby1.9.1_1.9.1.378-1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/r/ruby1.9.1/ruby1.9.1_1.9.1.378-1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses-ruby/libncurses-ruby1.9.1_1.2.4-2_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses/libncursesw5-dev_5.7+20090803-2ubuntu3_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/p/pcre3/libpcrecpp0_7.8-3build1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/p/pcre3/libpcre3-dev_7.8-3build1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/libs/libsigsegv/libsigsegv0_2.5-3_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses-hexedit/ncurses-hexedit_0.9.7-14ubuntu1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/g/gnu-smalltalk/libgst7_3.0.3-2ubuntu0.10.04.1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/g/gnu-smalltalk/gnu-smalltalk_3.0.3-2ubuntu0.10.04.1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/g/gnu-smalltalk/gnu-smalltalk-common_3.0.3-2ubuntu0.10.04.1_all.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/k/kaya/kaya_0.4.4-2ubuntu1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/k/kaya/libkaya-ncurses-dev_0.4.4-2ubuntu1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/k/kaya/libkaya-ncursesw-dev_0.4.4-2ubuntu1_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://all.repository.backtrack-linux.org/pool/main/g/gnu-smalltalk/libncurses-gst_3.0.3-2ubuntu0.10.04.1_all.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses/libncurses5-dbg_5.7+20090803-2ubuntu3_i386.deb  Unable to connect to 80.172.172.153:8080:
Failed to fetch http://32.repository.backtrack-linux.org/pool/main/n/ncurses/libncursesw5-dbg_5.7+20090803-2ubuntu3_i386.deb  Unable to connect to 80.172.172.153:8080:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```what i understood from this is that the problem maybe 1 of 2
1- it could be " the proxy " ( i tried to erase the proxy server details but the problem still there "
2- it could be the resource of downloading so how 2 chg it 2 ubuntu official server

thanks in advance

---

### Post by gayden on 2011-08-26
sry 4 that i found the solution somewhere

thanks any way

---

### Post by gayden on 2011-08-26
but now there is another problem
each time i try 2 download anything with any programit uses the proxy server so i want to uninstall it from all the system how?

thanks in advance

+ i need to delete it from wget too

---

### Post by gayden on 2011-08-26
hi again ,
tried this env | grep proxy
each time i chg the proxy it returns 2 it again
wat should i do?

---

