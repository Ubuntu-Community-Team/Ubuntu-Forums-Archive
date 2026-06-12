---
title: "VLC Media Player - Ubuntu 12.04 LTS Not Working"
date: 2014-06-11
forum: Multimedia Software
---

### Post by pancho5 on 2014-06-11
Hello!

I have read the many threads about VLC Media Player not working, and I an unable to resolve it with the various methods recommended from users.  When I try to read a video file, I get the following msg:  **   **
Codec not supported:

 VLC could not decode the format "h264" (H264 - MPEG-4 AVC (part 10))

I admit I am less than a novice when it comes to Linux, but I have tried to do all the listed resolutions on the threads with no success.  Can anyone advise another way to resolve this?

TIA, 


 		](*,)

---

### Post by A Bunny on 2014-06-12
[SIZE=2][FONT=arial]You may want to try installing Ubuntu restricted add on's. 

[/FONT][/SIZE][SIZE=2][FONT=arial]sudo apt-get install ubuntu-restricted-extras

Hope this helps
A_Bunny[/FONT][/SIZE]

---

### Post by pancho5 on 2014-06-12
> **A Bunny said:**
> [SIZE=2][FONT=arial]You may want to try installing Ubuntu restricted add on's. 

[/FONT][/SIZE][SIZE=2][FONT=arial]sudo apt-get install ubuntu-restricted-extras

Hope this helps
A_Bunny[/FONT][/SIZE]

Tried that already...no success!

---

### Post by A Bunny on 2014-06-13
[COLOR=#333333][FONT=sans-serif]Try disabling hardware video acceleration in VLC.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]You can find it in Tools --> Preferences. Then in the lower left tell it to show all settings.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Now navigate to "Input / Codecs" --> "Video Codecs" --> "FFmpeg", in there you'll want to uncheck the box that relates to "Hardware decoding".[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Then close vlc and open it up again, load up your video as see if that works.

[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]Note there is also an option to accelerate video output (overlay).[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]That shouldn't be an issue, but it might be, try turning it off:[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Tools --> Preferences. Then in the lower left tell it to show simple settings.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Go to the Video button, and try unchecking "Accelerated video output (overlay)", then restart vlc and try to load up a video.

Hope this helps.
A_Bunny[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-06-13
Well how did you install vlc? There are two threads on videolan complaining the same problem 
[https://forum.videolan.org/viewtopic.php?f=2&t=119538](https://forum.videolan.org/viewtopic.php?f=2&t=119538)
No real solution but it was suggested that that they might have installed some incompatible packages somewhere..

---

### Post by A Bunny on 2014-06-14
It may be a problem with the Ubuntu package so can try to install the Vlc source package and see if that gives you any problems. To install Vlc use this guide provided by them 
[https://wiki.videolan.org/UnixCompile/](https://wiki.videolan.org/UnixCompile/)

---

### Post by monkeybrain20122 on 2014-06-14
Or before you compile you may want to try a ppa first 
```
sudo add-apt-repository ppa:djcj/vlc-stable

sudo apt-get update

sudo apt-get install vlc
```

---

### Post by pancho5 on 2014-06-16
> **monkeybrain20122 said:**
> Well how did you install vlc? There are two threads on videolan complaining the same problem 
[https://forum.videolan.org/viewtopic.php?f=2&t=119538](https://forum.videolan.org/viewtopic.php?f=2&t=119538)
No real solution but it was suggested that that they might have installed some incompatible packages somewhere..

I used the following url's to install VLC Media Player:

[http://www.videolan.org/](http://www.videolan.org/)
[http://www.videolan.org/vlc/#download](http://www.videolan.org/vlc/#download)
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) (I selected Ubuntu 12.04 LTS "Precise Pangolin") and installed it the graphical way using Synaptic Package Manager.  I still had the problem, then I removed it completely and tried the command line way.

% sudo apt-get update
% sudo apt-get install vlc browser-plugin-vlc

The above command lines didn't resolve the problem either.

---

### Post by pancho5 on 2014-06-16
> **monkeybrain20122 said:**
> Well how did you install vlc? There are two threads on videolan complaining the same problem 
[https://forum.videolan.org/viewtopic.php?f=2&t=119538](https://forum.videolan.org/viewtopic.php?f=2&t=119538)
No real solution but it was suggested that that they might have installed some incompatible packages somewhere..

I used the following url's to install VLC Media Player:

[http://www.videolan.org/](http://www.videolan.org/)
[http://www.videolan.org/vlc/#download](http://www.videolan.org/vlc/#download)
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) (I selected Ubuntu 12.04 LTS "Precise Pangolin") and installed it the graphical way using Synaptic Package Manager.  I still had the problem, then I removed it completely and tried the command line way.

% sudo apt-get update
% sudo apt-get install vlc browser-plugin-vlc

The above command lines didn't resolve the problem either.

---

### Post by VMC on 2014-06-16
Does vlc work on other codecs and just fail on h264?

From a terminal, what the output of this:

```
$ [B]dpkg -S vlc|grep h264

[/B]vlc-nox: /usr/lib/vlc/plugins/demux/libh264_plugin.so
vlc-nox: /usr/lib/vlc/plugins/packetizer/libpacketizer_h264_plugin.so
```

---

### Post by pancho5 on 2014-06-16
> **VMC said:**
> Does vlc work on other codecs and just fail on h264?

From a terminal, what the output of this:

```
$ [B]dpkg -S vlc|grep h264

[/B]vlc-nox: /usr/lib/vlc/plugins/demux/libh264_plugin.so
vlc-nox: /usr/lib/vlc/plugins/packetizer/libpacketizer_h264_plugin.so
```

Good question! Yes it did fail on one other movie that I DL'd two days ago, but I don't remember what the error was.  I got frustrated and I deleted the movie so I cannot provide you the information.  I have DSL so it takes about an hour or so to DL a movie...sorry!

---

### Post by pancho5 on 2014-06-16
> **pancho5 said:**
> Good question! Yes it did fail on one other movie that I DL'd two days ago, but I don't remember what the error was.  I got frustrated and I deleted the movie so I cannot provide you the information.  I have DSL so it takes about an hour or so to DL a movie...sorry!

This is what came up on my xterm:

francisco@francisco-Satellite-M30X:~$ dpkg -S vlc|grep h264
vlc-nox: /usr/lib/vlc/plugins/demux/libh264_plugin.so
vlc-nox: /usr/lib/vlc/plugins/packetizer/libpacketizer_h264_plugin.so
francisco@francisco-Satellite-M30X:~$

---

### Post by pancho5 on 2014-06-16
> **monkeybrain20122 said:**
> Or before you compile you may want to try a ppa first 
```
sudo add-apt-repository ppa:djcj/vlc-stable

sudo apt-get update

sudo apt-get install vlc
```

After the add-apt, the next two commands resulted as follows:

```
francisco@francisco-Satellite-M30X:~$ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release.gpg                                                    
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg                                                          
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                                                              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                              
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                                               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release                                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                                                    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg                                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted i386 Packages                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main i386 Packages                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse i386 Packages                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe i386 Packages                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main TranslationIndex                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse TranslationIndex                                    
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted TranslationIndex                                    
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe TranslationIndex                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en                                      
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release                                                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main Translation-en                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse Translation-en                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted Translation-en                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe Translation-en                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_US                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                                                      
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps i386 Packages                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps TranslationIndex
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games TranslationIndex
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en_US         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en_US
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Reading package lists... Done
francisco@francisco-Satellite-M30X:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
vlc set to manually installed.
The following packages were automatically installed and are no longer required:
  remuco-base libdiscid0 libsvga1 libgmtk0 libx86-1 python-bluez libgmtk0-data libgmlib0 libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
francisco@francisco-Satellite-M30X:~$
```

---

### Post by pancho5 on 2014-06-16
> **A Bunny said:**
> [COLOR=#333333][FONT=sans-serif]Try disabling hardware video acceleration in VLC.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]You can find it in Tools --> Preferences. Then in the lower left tell it to show all settings.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Now navigate to "Input / Codecs" --> "Video Codecs" --> "FFmpeg", in there you'll want to uncheck the box that relates to "Hardware decoding".[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Then close vlc and open it up again, load up your video as see if that works.

[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]Note there is also an option to accelerate video output (overlay).[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]That shouldn't be an issue, but it might be, try turning it off:[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Tools --> Preferences. Then in the lower left tell it to show simple settings.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Go to the Video button, and try unchecking "Accelerated video output (overlay)", then restart vlc and try to load up a video.

Hope this helps.
A_Bunny[/FONT][/COLOR]

Tried your above instructions in VLC, still did not work but thanks, it was worth a try.

---

### Post by monkeybrain20122 on 2014-06-16
> **pancho5 said:**
> I used the following url's to install VLC Media Player:

[http://www.videolan.org/](http://www.videolan.org/)
[http://www.videolan.org/vlc/#download](http://www.videolan.org/vlc/#download)
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) (I selected Ubuntu 12.04 LTS "Precise Pangolin") and installed it the graphical way using Synaptic Package Manager.  I still had the problem, then I removed it completely and tried the command line way.

% sudo apt-get update
% sudo apt-get install vlc browser-plugin-vlc

The above command lines didn't resolve the problem either.

Well if you install with that link you would get vlc 2.0.8 or something like that for Ubuntu 12.04 and the ppa should give you 2.1.4 or 2.1.5. Not sure why it says it is already the latest version.

---

