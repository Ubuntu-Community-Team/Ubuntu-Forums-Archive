---
title: "Mediaubuntu"
date: 2008-09-12
forum: Multimedia Software
---

### Post by ikirmikir on 2008-09-12
Dear All,

         I want to install Mediaubuntu in my system, specially to have the codecs libdvd and w32 etc. But following the guideline from Mediaubuntu webpage, whenever I type this command in my terminal 

"sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list "

it gives me 

"--17:40:43--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... failed: Connection timed out.
Retrying.
" 
 In fact , I found that 

"http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list" website probably doesn't exist. So, how to install mediaubuntu for ubuntu 8.04 ? can anyone help me? Also, in the mediaubuntu page , its written "Add Medibuntu to your sources.list, as well as its GPG key to your keyring". This two steps are not clear to me.
:(

ikirmikir.

---

### Post by overdrank on 2008-09-12
> **ikirmikir said:**
> Dear All,

         I want to install Mediaubuntu in my system, specially to have the codecs libdvd and w32 etc. But following the guideline from Mediaubuntu webpage, whenever I type this command in my terminal 

"sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list "

it gives me 

"--17:40:43--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... failed: Connection timed out.
Retrying.
" 
 In fact , I found that 

"http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list" website probably doesn't exist. So, how to install mediaubuntu for ubuntu 8.04 ? can anyone help me? Also, in the mediaubuntu page , its written "Add Medibuntu to your sources.list, as well as its GPG key to your keyring". This two steps are not clear to me.
:(

ikirmikir.

Hi and welcome I just used this command and it worked from the web page
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

