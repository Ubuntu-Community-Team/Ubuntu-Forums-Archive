---
title: "how to install cowpatty on ubuntu 9.04"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by ramazani on 2009-07-22
Hi can anyone tell me how to install cowpatty on ubuntu 9.04 i tried many fourm and searched on google no chance 


anishixan@kanishixan-laptop:~$ sudo apt-get install build-essential checkinstall                                                                   
Reading package lists... Done                                             
Building dependency tree                                                  
Reading state information... Done                                         
build-essential is already the newest version.                            
checkinstall is already the newest version.                               
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.            
kanishixan@kanishixan-laptop:~$ sudo apt-get install cvs svn git-core mercurial                                                                     
Reading package lists... Done                                             
Building dependency tree                                                  
Reading state information... Done                                         
Package svn is not available, but is referred to by another package.      
This may mean that the package is missing, has been obsoleted, or         
is only available from another source                                     
E: Package svn has no installation candidate                              
kanishixan@kanishixan-laptop:~$ cd ~/Desktop                              
kanishixan@kanishixan-laptop:~/Desktop$ tar xvzf cowpatty-4.3.tgz         
cowpatty-4.3/                                                             
cowpatty-4.3/FAQ                                                          
cowpatty-4.3/TODO                                                         
cowpatty-4.3/dict                                                         
cowpatty-4.3/wpa2psk-linksys.dump                                         
cowpatty-4.3/eap-test.dump                                                
cowpatty-4.3/Makefile                                                     
cowpatty-4.3/md5.c                                                        
cowpatty-4.3/md5.h                                                        
cowpatty-4.3/README                                                       
cowpatty-4.3/wpapsk-linksys.dump                                          
cowpatty-4.3/cowpatty.c                                                   
cowpatty-4.3/cowpatty.h                                                   
cowpatty-4.3/file_magic                                                   
cowpatty-4.3/genpmk.c                                                     
cowpatty-4.3/CHANGELOG                                                    
cowpatty-4.3/common.h                                                     
cowpatty-4.3/sha1.c                                                       
cowpatty-4.3/sha1.h                                                       
cowpatty-4.3/AUTHORS                                                      
cowpatty-4.3/utils.c                                                      
cowpatty-4.3/utils.h                                                      
cowpatty-4.3/INSTALL                                                      
cowpatty-4.3/radiotap.h                                                   
cowpatty-4.3/COPYING                                                      
kanishixan@kanishixan-laptop:~/Desktop$ cd cowpatty-4.3                   
kanishixan@kanishixan-laptop:~/Desktop/cowpatty-4.3$ ./configure          
bash: ./configure: No such file or directory                              
kanishixan@kanishixan-laptop:~/Desktop/cowpatty-4.3$ make & make install  
[1] 5626                                                                  
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c               
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c               
md5.c:20:25: error: openssl/md5.h: No such file or directory              
md5.c:20:25: error: openssl/md5.h: No such file or directory              
md5.c: In function ‘md5_mac’:                                             
md5.c:28: error: ‘MD5_CTX’ undeclared (first use in this function)        
md5.c:28: error: (Each undeclared identifier is reported only once        
md5.c:28: error: for each function it appears in.)                        
md5.c:28: error: expected ‘;’ before ‘context’                            
md5.c:29: warning: implicit declaration of function ‘MD5_Init’            
md5.c:29: error: ‘context’ undeclared (first use in this function)        
md5.c:30: warning: implicit declaration of function ‘MD5_Update’          
md5.c:33: warning: implicit declaration of function ‘MD5_Final’           
md5.c: In function ‘hmac_md5_vector’:                                     
md5.c:40: error: ‘MD5_CTX’ undeclared (first use in this function)        
md5.c:40: error: expected ‘;’ before ‘context’                            
md5.c:48: error: ‘context’ undeclared (first use in this function)        
md5.c: In function ‘md5_mac’:                                             
md5.c:28: error: ‘MD5_CTX’ undeclared (first use in this function)        
md5.c:28: error: (Each undeclared identifier is reported only once        
md5.c:28: error: for each function it appears in.)                        
md5.c:28: error: expected ‘;’ before ‘context’                            
md5.c:29: warning: implicit declaration of function ‘MD5_Init’            
md5.c:29: error: ‘context’ undeclared (first use in this function)        
md5.c:30: warning: implicit declaration of function ‘MD5_Update’          
md5.c:33: warning: implicit declaration of function ‘MD5_Final’           
md5.c: In function ‘hmac_md5_vector’:                                     
md5.c:40: error: ‘MD5_CTX’ undeclared (first use in this function)        
md5.c:40: error: expected ‘;’ before ‘context’                            
md5.c:48: error: ‘context’ undeclared (first use in this function)        
make: *** [md5.o] Error 1                                                 
make: *** [md5.o] Error 1                                                 
[1]+  Exit 2                  make                                        
kanishixan@kanishixan-laptop:~/Desktop/cowpatty-4.3$ sudo checkinstall    

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.             


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y        

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> cowpatty                                    
>>                                             

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@kanishixan-laptop ]
1 -  Summary: [ cowpatty ]                 
2 -  Name:    [ cowpatty ]                 
3 -  Version: [ 4.3 ]                      
4 -  Release: [ 1 ]                        
5 -  License: [ GPL ]                      
6 -  Group:   [ checkinstall ]             
7 -  Architecture: [ i386 ]                
8 -  Source location: [ cowpatty-4.3 ]     
9 -  Alternate source location: [  ]       
10 - Requires: [  ]                        
11 - Provides: [ cowpatty ]                

Enter a number to change any of them or press ENTER to continue: 1
Enter new summary:                                                
>>                                                                

This package will be built according to these values: 

0 -  Maintainer: [ root@kanishixan-laptop ]
1 -  Summary: [ cowpatty ]                 
2 -  Name:    [ cowpatty ]                 
3 -  Version: [ 4.3 ]                      
4 -  Release: [ 1 ]                        
5 -  License: [ GPL ]                      
6 -  Group:   [ checkinstall ]             
7 -  Architecture: [ i386 ]                
8 -  Source location: [ cowpatty-4.3 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ cowpatty ]

Enter a number to change any of them or press ENTER to continue:

Installing with make...Installing with install...

========================= Installation results ===========================
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c
md5.c:20:25: error: openssl/md5.h: No such file or directory
md5.c: In function ‘md5_mac’:
md5.c:28: error: ‘MD5_CTX’ undeclared (first use in this function)
md5.c:28: error: (Each undeclared identifier is reported only once
md5.c:28: error: for each function it appears in.)
md5.c:28: error: expected ‘;’ before ‘context’
md5.c:29: warning: implicit declaration of function ‘MD5_Init’
md5.c:29: error: ‘context’ undeclared (first use in this function)
md5.c:30: warning: implicit declaration of function ‘MD5_Update’
md5.c:33: warning: implicit declaration of function ‘MD5_Final’
md5.c: In function ‘hmac_md5_vector’:
md5.c:40: error: ‘MD5_CTX’ undeclared (first use in this function)
md5.c:40: error: expected ‘;’ before ‘context’
md5.c:48: error: ‘context’ undeclared (first use in this function)
make: *** [md5.o] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

kanishixan@kanishixan-laptop:~/Desktop/cowpatty-4.3$

---

### Post by 4llf0rn0t on 2009-07-28
opht@foo$ sudo aptitude install libssl-dev libpcap0.8-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  libpcap0.8-dev libssl-dev zlib1g-dev{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2352kB of archives. After unpacking 6808kB will be used.
Do you want to continue? [Y/n/?]

Then try > make:
opht@foo~/cowpatty-4.6$ make
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o utils.o utils.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o cowpatty.o cowpatty.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o genpmk.o genpmk.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb cowpatty.c -o cowpatty utils.o md5.o sha1.o -lpcap -lcrypto
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb genpmk.c -o genpmk utils.o sha1.o -lpcap -lcrypto

---

### Post by andytof47 on 2009-11-07
Hi I'm running cowpatty 4.6 but I'm wondering if there is a an svn - because i've searched or b I do have a patch file but i get these errors when trying to patch

```
oot@john-laptop:/home/andy1/aircrack-ng# sudo patch /usr/bin/cowpatty /home/andy1/cowpatty_patch.diff 
patching file /usr/bin/cowpatty
Hunk #1 FAILED at 94.
Hunk #2 FAILED at 150.
Hunk #3 FAILED at 165.
Hunk #4 FAILED at 267.
Hunk #5 FAILED at 290.
Hunk #6 FAILED at 398.
Hunk #7 FAILED at 465.
Hunk #8 FAILED at 477.
Hunk #9 FAILED at 492.
Hunk #10 FAILED at 520.
Hunk #11 FAILED at 538.
Hunk #12 FAILED at 1027.
12 out of 12 hunks FAILED -- saving rejects to file /usr/bin/cowpatty.rej
can't find file to patch at input line 391
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNr cowpatty-4.6/cowpatty.h cowpatty-4.6-fixup16/cowpatty.h
|--- cowpatty-4.6/cowpatty.h	2009-06-04 06:24:16.000000000 -0700
|+++ cowpatty-4.6-fixup16/cowpatty.h	2009-07-17 16:16:58.043152023 -0700
--------------------------
File to patch: /usr/local/bin/cowpatty
patching file /usr/local/bin/cowpatty
Hunk #1 FAILED at 178.
1 out of 1 hunk FAILED -- saving rejects to file /usr/local/bin/cowpatty.rej
```

can anyone help here?

What am i doing wrong, this is the first time i've tried to patcha  file so i won't be suprised if it is something i've done wrong


cheers

---

