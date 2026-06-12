---
title: "XBMC force close/crash after selecting &quot;play&quot; Ubuntu 14.04 (crash log inc.)"
date: 2014-05-26
forum: Multimedia Software
---

### Post by Mike1977 on 2014-05-26
I have a brand new machine with fresh install of Ubuntu 14.04 and I'm  trying to run Gotham 13.0 on it. I've already added the restricted  multimedia codecs (just in case) to Ubuntu. 
                                                        ```
 sudo apt-get install ubuntu-restricted-extras   
```                   
     
 
As well as Unrestricted LibavCodec
                                                         ```
sudo apt-get install libavcodec-extra 
```                     
     
 
My graphics is AMD/ATI Tahiti (Radeon HD 7970) with a core i7. 
Here's the crashlog: [http://xbmclogs.com/show.php?id=209365](http://xbmclogs.com/show.php?id=209365) 

Here's what's happening: I just download the appropriate PPA's etc. through the XBMC wiki.
                                                         ```
sudo add-apt-repository ppa:team-xbmc

sudo apt-get update

sudo apt-get install xbmc                      
     
```
 
The first time I installed it on this machine, I went through  installed Fusion and ran the Hub wizard Template/Setup. Everythings  seems good, 
but when I select Al Jazeera, for example, I click "watch live", and  then I get the "working" scroll in the bottom right for few seconds, and  then the entire program force closes. The same happens with " The Daily  Show" "Youtube" "UsTv Now" etc.
I completly uninstalled XBMC 
                                                         ```
sudo apt-get purge xbmc xbmc-standalone     
```                 
     
 
and started over. This time only installing one add on and trying  it out. Still I get the same results. The music add-ons work though. I have this posted a few days on XBMC forums, and no replies yet. I'm not sure if this is an Ubuntu or XBMC issue ,at this point.

---

### Post by Mike1977 on 2014-06-10
I never did get this issue resolved. Except to say that I reinstalled Ubuntu 14.04, but this time as 64bit, and everything seems to work fine with XBMC now. The only other difference I can think of is instead of deleting the linux-swap partition, I shrank it to 2.5GB. I have 16GB ram, so I wouldn't think this, or even the 64bit install should make a difference. But for whatever reason, all is well now.

---

