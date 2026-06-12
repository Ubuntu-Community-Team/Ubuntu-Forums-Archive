---
title: "I can't uninstall a program called 'workrave', please help"
date: 2015-04-16
forum: Multimedia Software
---

### Post by ange3 on 2015-04-16
Hi! 
I have ubuntu 14.04 64bit
I have installed this program [http://www.workrave.org/](http://www.workrave.org/) from the software centre but now I want to remove it and I'm finding it impossible to do so.
This is what I did
-opened software centre again and clicked on 'remove' workrave
--and I thought it would be done but no, the program was still running, even though it had been apparently removed
-I run sudo apt-get remove workrave
--it does not work
-I go to the website again and find that the program can't be removed if I didn't quit it beforehand [http://www.workrave.org/documentation/faq/#uninstallation-fails-because-the-program-is-still-running-how-do-i-proceed](http://www.workrave.org/documentation/faq/#uninstallation-fails-because-the-program-is-still-running-how-do-i-proceed)
-I installed it again from the software centre and now its icon is back in my sidebar but when I click on it it says the program is already running and that it can't be opened again

I don't know what to do now and I really need this program to be removed, it behaves almost like a virus and is extremely annoying: every two minutes a pop up windows with flashing borders comes out with a beep and stays on the screen for 30 seconds before going out with a car horn sound I can't stand it anymore please help me out.

---

### Post by ian-weisser on 2015-04-16
Did you download workrave from the website?
Or did you install the version that's already in the Ubuntu Software Center?

Please show us the *complete* output from 'sudo apt-get remove workrave'

---

### Post by ange3 on 2015-04-16
> **ian-weisser said:**
> Did you download workrave from the website?
Or did you install the version that's already in the Ubuntu Software Center?

Please show us the *complete* output from 'sudo apt-get remove workrave'

Thanks for your reply!
I installed it from the software center

this is what I get when I run sudo apt-get remove workrave (I had to translate it in English)

```

  The following packages have been installed automatically and are no longer requested:
  libpanel-applet-4-0 workrave-data
Use "apt-get autoremove" to remove them.
The following packages will be REMOVED:
  workrave
0 updated, 0 installed, 1 to remove e 462 not updated.
After this operation 1.622 kB of disk space will be freed.
Continue? [Y/n] 

```

I'm going to wait for your answer before I tell it 'yes' and thanks again!


---edit

when I tried running that before (after removing workrave via the software cernter), it said 0 updated, 0 installed, 0 to remove but the program was still running, so I installed it again to try to quit it before removing it but now it's still running

---

### Post by ian-weisser on 2015-04-16
Tell it 'yes'. Please show us that output, too.

> **ange3 said:**
> 0 updated, 0 installed, 1 to remove e **462 not updated**.
Uh-oh. We'll take a look at that, too.

---

### Post by ange3 on 2015-04-16
This is what I got

```
(Reading database... 218854 files and directories installed.)
Removing workrave (1.10.1-4)...
Elaborating triggers per man-db (2.6.7.1-1)...
Elaborating triggers for gnome-menus (3.10.1-0ubuntu2)...
Elaborating triggers for desktop-file-utils (0.22-1ubuntu1)...
Elaborating triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1)...
Rebuilding /usr/share/applications/bamf-2.index...
Elaborating triggers for mime-support (3.54ubuntu1)...
Elaborating triggers for libc-bin (2.19-0ubuntu6.3)...
```

---

### Post by ian-weisser on 2015-04-16
Now workrave is removed, and you're back to a shell prompt?
Or workrave is still there, but the package manager gave every indication of successful removal?

Please show us the output of:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ange3 on 2015-04-16
Yes, it seems as if it was removed and I was back to the shell prompt  but Workrave is still working (a flashing window popped up just as I was  typing this) 

This is what I get after running the commands (I bolded the english translations of the two reoccurring words)

sudo apt-get update :

```
Ign http://archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Ign http://archive.ubuntu.com trusty-updates InRelease                         
**(Found)Trovato **http://deb.playonlinux.com trusty InRelease                            
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Trovato http://archive.canonical.com trusty Release.gpg                        
**(Downloading)** **Scaricamento** di:1 http://extras.ubuntu.com trusty Release.gpg [72 B]           
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.ubuntu.com trusty-security InRelease                        
Ign http://ppa.launchpad.net trusty InRelease                                 
Trovato http://archive.ubuntu.com trusty Release.gpg                           
Scaricamento di:2 http://archive.ubuntu.com trusty-updates Release.gpg [933 B] 
Trovato http://archive.canonical.com trusty Release                            
Trovato http://extras.ubuntu.com trusty Release                                
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Scaricamento di:3 http://archive.ubuntu.com trusty-backports Release.gpg [933 B]
Trovato http://deb.playonlinux.com trusty/main amd64 Packages                  
Scaricamento di:4 http://archive.ubuntu.com trusty-security Release.gpg [933 B]
Trovato http://archive.canonical.com trusty/partner Sources                    
Scaricamento di:5 http://ppa.launchpad.net trusty Release.gpg [316 B]          
Trovato http://archive.ubuntu.com trusty Release                               
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://extras.ubuntu.com trusty/main Sources                           
Scaricamento di:6 http://archive.ubuntu.com trusty-updates Release [63,5 kB]   
Trovato http://archive.canonical.com trusty/partner amd64 Packages             
Trovato http://deb.playonlinux.com trusty/main i386 Packages                   
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://extras.ubuntu.com trusty/main amd64 Packages                    
Trovato http://archive.canonical.com trusty/partner i386 Packages              
Scaricamento di:7 http://ppa.launchpad.net trusty Release [15,1 kB]            
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Scaricamento di:8 http://archive.canonical.com trusty/partner Translation-en [4.588 B]
Scaricamento di:9 http://archive.ubuntu.com trusty-backports Release [63,5 kB] 
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty/main amd64 Packages                    
Scaricamento di:10 http://archive.ubuntu.com trusty-security Release [63,5 kB] 
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty/main Sources                          
Trovato http://archive.ubuntu.com trusty/restricted Sources                    
Trovato http://archive.ubuntu.com trusty/universe Sources                      
Trovato http://archive.ubuntu.com trusty/multiverse Sources                    
Trovato http://archive.ubuntu.com trusty/main amd64 Packages                   
Scaricamento di:11 http://ppa.launchpad.net trusty/main amd64 Packages [3.517 B]
Trovato http://archive.ubuntu.com trusty/restricted amd64 Packages             
Trovato http://archive.ubuntu.com trusty/universe amd64 Packages               
Scaricamento di:12 http://ppa.launchpad.net trusty/main i386 Packages [3.515 B]
Scaricamento di:13 http://ppa.launchpad.net trusty/main Translation-en [1.429 B]
Trovato http://archive.ubuntu.com trusty/multiverse amd64 Packages             
Trovato http://archive.ubuntu.com trusty/main i386 Packages                    
Trovato http://ppa.launchpad.net trusty/main amd64 Packages             
Trovato http://archive.ubuntu.com trusty/restricted i386 Packages       
Ign http://deb.playonlinux.com trusty/main Translation-it_IT                   
Trovato http://archive.ubuntu.com trusty/universe i386 Packages                
Trovato http://archive.ubuntu.com trusty/multiverse i386 Packages              
Ign http://deb.playonlinux.com trusty/main Translation-it                      
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty/main Translation-it                   
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Ign http://deb.playonlinux.com trusty/main Translation-en                      
Trovato http://archive.ubuntu.com trusty/main Translation-en                   
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Trovato http://archive.ubuntu.com trusty/multiverse Translation-it             
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Trovato http://archive.ubuntu.com trusty/multiverse Translation-en             
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Trovato http://archive.ubuntu.com trusty/restricted Translation-it             
Trovato http://archive.ubuntu.com trusty/restricted Translation-en        
Trovato http://archive.ubuntu.com trusty/universe Translation-it         
Trovato http://archive.ubuntu.com trusty/universe Translation-en         
Scaricamento di:14 http://archive.ubuntu.com trusty-updates/main Sources [194 kB]
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Scaricamento di:15 http://archive.ubuntu.com trusty-updates/restricted Sources [2.564 B]
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Scaricamento di:16 http://archive.ubuntu.com trusty-updates/universe Sources [112 kB]
Scaricamento di:17 http://archive.ubuntu.com trusty-updates/multiverse Sources [4.775 B]
Scaricamento di:18 http://archive.ubuntu.com trusty-updates/main amd64 Packages [502 kB]
Scaricamento di:19 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9.238 B]
Scaricamento di:20 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [269 kB]
Scaricamento di:21 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11,7 kB]
Scaricamento di:22 http://archive.ubuntu.com trusty-updates/main i386 Packages [491 kB]
Scaricamento di:23 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [9.256 B]
Scaricamento di:24 http://archive.ubuntu.com trusty-updates/universe i386 Packages [270 kB]
Scaricamento di:25 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [11,9 kB]
Scaricamento di:26 http://archive.ubuntu.com trusty-updates/main Translation-en [237 kB]
Trovato http://archive.ubuntu.com trusty-updates/multiverse Translation-en     
Trovato http://archive.ubuntu.com trusty-updates/restricted Translation-en     
Scaricamento di:27 http://archive.ubuntu.com trusty-updates/universe Translation-en [138 kB]
Scaricamento di:28 http://archive.ubuntu.com trusty-backports/main Sources [5.851 B]
Scaricamento di:29 http://archive.ubuntu.com trusty-backports/restricted Sources [28 B]
Scaricamento di:30 http://archive.ubuntu.com trusty-backports/universe Sources [24,4 kB]
Scaricamento di:31 http://archive.ubuntu.com trusty-backports/multiverse Sources [1.898 B]
Scaricamento di:32 http://archive.ubuntu.com trusty-backports/main amd64 Packages [6.256 B]
Scaricamento di:33 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Scaricamento di:34 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [28,3 kB]
Scaricamento di:35 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1.245 B]
Scaricamento di:36 http://archive.ubuntu.com trusty-backports/main i386 Packages [6.285 B]
Scaricamento di:37 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Scaricamento di:38 http://archive.ubuntu.com trusty-backports/universe i386 Packages [28,3 kB]
Scaricamento di:39 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [1.249 B]
Scaricamento di:40 http://archive.ubuntu.com trusty-backports/main Translation-en [3.645 B]
Trovato http://archive.ubuntu.com trusty-backports/multiverse Translation-en   
Trovato http://archive.ubuntu.com trusty-backports/restricted Translation-en   
Scaricamento di:41 http://archive.ubuntu.com trusty-backports/universe Translation-en [25,1 kB]
Scaricamento di:42 http://archive.ubuntu.com trusty-security/main Sources [78,4 kB]
Scaricamento di:43 http://archive.ubuntu.com trusty-security/restricted Sources [2.061 B]
Scaricamento di:44 http://archive.ubuntu.com trusty-security/universe Sources [20,3 kB]
Scaricamento di:45 http://archive.ubuntu.com trusty-security/multiverse Sources [1.922 B]
Scaricamento di:46 http://archive.ubuntu.com trusty-security/main amd64 Packages [258 kB]
Scaricamento di:47 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [8.875 B]
Scaricamento di:48 http://archive.ubuntu.com trusty-security/universe amd64 Packages [95,9 kB]
Scaricamento di:49 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [3.451 B]
Scaricamento di:50 http://archive.ubuntu.com trusty-security/main i386 Packages [247 kB]
Scaricamento di:51 http://archive.ubuntu.com trusty-security/restricted i386 Packages [8.846 B]
Scaricamento di:52 http://archive.ubuntu.com trusty-security/universe i386 Packages [95,9 kB]
Scaricamento di:53 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [3.643 B]
Trovato http://archive.ubuntu.com trusty-security/main Translation-en          
Trovato http://archive.ubuntu.com trusty-security/multiverse Translation-en    
Trovato http://archive.ubuntu.com trusty-security/restricted Translation-en    
Scaricamento di:54 http://archive.ubuntu.com trusty-security/universe Translation-en [52,1 kB]
Ign http://archive.ubuntu.com trusty/main Translation-it_IT                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-it_IT              
Ign http://archive.ubuntu.com trusty/restricted Translation-it_IT              
Ign http://archive.ubuntu.com trusty/universe Translation-it_IT                
Recovered 3.494 kB in 12s (280 kB/s)                                          
Reading package list... Done


```


I ran sudo apt-get upgrade too but I did not have unlimited scrolling back in the terminal so I can not paste the whole thing unfortunately..
but I remember reading something about workrave and autoremove at the very beginning but I didn't really register it since I thought I'd be able to scroll back up...

---

### Post by ian-weisser on 2015-04-16
You can increase the scrollback in your Terminal settings.
The apt-get upgrade output will be very helpful if you still have 462 unapplied upgrades.

---

### Post by ange3 on 2015-04-17
Yes, I changes it and now the scrollback is unlimited but it wasn't when I ran apt-get upgrade, so I cannot post the output of that command.
I have now rebooted the computer and the program is no longer running, I don't know if it was removed completely though..
Many thanks for your replies and help!

---

### Post by ian-weisser on 2015-04-17
You can tell if the workrave package is installed using dpkg
[code]dpkg -l workrave[code]

Do you still have hundreds of uninstalled upgrades waiting?
That's a bigger problem than one rogue application.
It usually means you're not getting security upgrades.

---

### Post by ange3 on 2015-04-17
Yes I have updated and upgraded everything now. Workrave is still there though
this is the ouput of dpkg -l workrave

```
 
Wanted=U (not known)/I (installed)/R (removed)/P (removed completely)/H (on hold)
| State=Non/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/R (reinstallation required) (State,Err: maiuscolo=grave)
||/ Name           Version     Architeture Description
+++-==============-============-============-=================================
rc  workrave       1.10.1-4     amd64        Repetitive Strain Injury preventi


```

---

### Post by ian-weisser on 2015-04-17
Happy to hear your upgrades are up-to-date.
The workrave package is certainly uninstalled.

> **ange3 said:**
> Workrave is still there though
How can you tell?

If you can tell because it's running and bothering you, use the command 'ps -aux', and look for the workrave daemon or application running.
Post the output line(s) here.

---

### Post by ange3 on 2015-04-17
My mistake, workrave was actually removed
Thank you again!

---

### Post by Impavidus on 2015-04-17
> **ange3 said:**
> Yes I have updated and upgraded everything now. Workrave is still there though
this is the ouput of dpkg -l workrave

```
 
Wanted=U (not known)/I (installed)/R (removed)/P (removed completely)/H (on hold)
| State=Non/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/R (reinstallation required) (State,Err: maiuscolo=grave)
||/ Name           Version     Architeture Description
+++-==============-============-============-=================================
rc  workrave       1.10.1-4     amd64        Repetitive Strain Injury preventi


```

The rc at the beginning of the line means that the package has been removed, but some configuration files remain. To completely remove the configuration files you can purge the package:```
sudo apt-get purge workrave
```

---

### Post by ange3 on 2015-04-17
Thanks, I completely removed it now!

---

