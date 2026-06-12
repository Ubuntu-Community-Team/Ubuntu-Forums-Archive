---
title: "merging two seperate video clips into single clip video"
date: 2011-07-14
forum: Multimedia Software
---

### Post by YigalB on 2011-07-14
I have two seperated video clips, that captured same event from two cameras.
i would like to create one clip, that will show one on the left side, the second on the right side, and play together.

Any idea of a tool that can do that?

---

### Post by Enigmapond on 2011-07-14
This can be done in Cinelerra, which is a great tool. You need to add the PPA:

```
sudo add-apt-repository ppa:*cinelerra*-*ppa*/ppa
sudo apt-get update && sudo apt-get install cenelerra
```

Hope this helps...there is a bit of a learning curve.

Cheers!

---

### Post by YigalB on 2011-07-14
> **Enigmapond said:**
> This can be done in Cinelerra, which is a great tool. You need to add the PPA:

```
sudo add-apt-repository ppa:*cinelerra*-*ppa*/ppa
sudo apt-get update && sudo apt-get install cenelerra
```

Hope this helps...there is a bit of a learning curve.

Cheers!

i tried and this is what I got:
```
:~$ sudo add-apt-repository ppa:cinelerra-ppa/ppa
[sudo] password for dnld: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 60DB64FA8E893E577651CF3DCBDFA02B432BB368
gpg: requesting key 432BB368 from hkp server keyserver.ubuntu.com
gpg: key 432BB368: public key "Launchpad PPA for Cinelerra" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
:~$ sudo apt-get update && sudo apt-get install cenelerra
Ign http://il.archive.ubuntu.com natty InRelease
Ign http://il.archive.ubuntu.com natty-updates InRelease                       
Hit http://il.archive.ubuntu.com natty Release.gpg                             
Hit http://il.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://il.archive.ubuntu.com natty Release                                 
Hit http://il.archive.ubuntu.com natty-updates Release                         
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://il.archive.ubuntu.com natty/main Sources                            
Ign http://security.ubuntu.com natty-security InRelease                        
Hit http://il.archive.ubuntu.com natty/restricted Sources            
Hit http://il.archive.ubuntu.com natty/universe Sources                        
Hit http://il.archive.ubuntu.com natty/multiverse Sources                      
Hit http://il.archive.ubuntu.com natty/main i386 Packages                      
Hit http://il.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://extras.ubuntu.com natty Release.gpg                                 
Get:1 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Hit http://il.archive.ubuntu.com natty/universe i386 Packages        
Hit http://il.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://il.archive.ubuntu.com natty/main TranslationIndex
Ign http://il.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://il.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://il.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://il.archive.ubuntu.com natty-updates/main Sources                    
Hit http://il.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://il.archive.ubuntu.com natty-updates/universe Sources                
Hit http://il.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://il.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://il.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://il.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://il.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://il.archive.ubuntu.com natty-updates/main TranslationIndex           
Hit http://security.ubuntu.com natty-security Release.gpg                      
Ign http://il.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://il.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://il.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://extras.ubuntu.com natty Release                                     
Get:2 http://ppa.launchpad.net natty Release [9,731 B]                         
Hit http://security.ubuntu.com natty-security Release                          
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://security.ubuntu.com natty-security/main Sources           
Get:3 http://ppa.launchpad.net natty/main Sources [979 B]            
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources     
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Get:4 http://ppa.launchpad.net natty/main i386 Packages [2,106 B]    
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://il.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://il.archive.ubuntu.com natty/main Translation-en                     
Ign http://il.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://il.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://il.archive.ubuntu.com natty/restricted Translation-en_US  
Ign http://il.archive.ubuntu.com natty/restricted Translation-en               
Ign http://il.archive.ubuntu.com natty/universe Translation-en_US              
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://il.archive.ubuntu.com natty/universe Translation-en                 
Ign http://il.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://il.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://il.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://il.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://il.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://il.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://il.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://il.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Fetched 13.1 kB in 2s (6,416 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cenelerra

```

---

### Post by FakeOutdoorsman on 2011-07-14
FFmpeg can make a side-by-side video from two inputs, but you'll need to compile it first because as of Natty ffmpeg from the repository does not support filters. Compiling isn't too hard with this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Now for an example (assuming both inputs are same resolution):
```
ffmpeg -i right.mp4 -vcodec libx264 -preset medium -crf 24 -threads 0 -acodec libfaac \
-aq 100 -vf "[in]setpts=PTS-STARTPTS,pad=iw*2:ih:iw:0,[T1]overlay=0:0[out];movie=left.mp4 \
,setpts=PTS-STARTPTS[T1]" output.mp4
```
You didn't list any output specifics, so I chose H.264 video and AAC audio in MP4 container.

Another option is [bino](http://www.nongnu.org/bino/) to play both videos at once without re-encoding. I've never used it.

---

### Post by coldraven on 2011-07-14
> sudo add-apt-repository ppa:*cinelerra*-*ppa*/ppa sudo apt-get update && sudo apt-get install cenelerra

The install did not work because cinelerra is spelled wrongly in the second line.

---

### Post by Enigmapond on 2011-07-15
LOL oops....yes just run the install with the correct spelling...so very sorry..:)

Cheers!

---

### Post by YigalB on 2011-07-16
> **Enigmapond said:**
> LOL oops....yes just run the install with the correct spelling...so very sorry..:)

Cheers!
Don't be sorry. You have been very helpful. Now I passed the installation phase. Thank you!

Is there an easy guide how to do the side by side?

---

### Post by shantiq on 2011-07-16
-----

---

### Post by Enigmapond on 2011-07-19
> **YigalB said:**
> Don't be sorry. You have been very helpful. Now I passed the installation phase. Thank you!

Is there an easy guide how to do the side by side?

Fairly easy in Cinelerra. You zoom in on the projector on video 1 track 1  and shift to the right. you zoom in on the projector of video2 track to  and keep it to the left...... then render. viola ! split-screen. :P

---

