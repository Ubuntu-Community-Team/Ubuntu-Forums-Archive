---
title: "Sound problems Kernel 2.6.37"
date: 2010-12-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by arashiko28 on 2010-12-18
Actually I had the same problem with Maverick and had to go back to 2.6.34 in order to get sound back to work. Actually don't know how to report a bug since there's no crash, just that the sound configuration won't work, because there's a conflict with ACL-888, ACL-883 configuration. Hope there's a fix soon.

---

### Post by lidex on 2010-12-18
Try running this command in a terminal:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Reiger on 2010-12-19
That one. You can probably “fix” this by editing /etc/modprobe.d/alsa-base.conf to load your sound module using a specific model rather than using BIOS parameters (default).

---

### Post by arashiko28 on 2010-12-19
> **Reiger said:**
> That one. You can probably “fix” this by editing /etc/modprobe.d/alsa-base.conf to load your sound module using a specific model rather than using BIOS parameters (default).

There is actually where the problem happens, when it's unchanged, it's too low, actually only there's sound of 2 of 5 speakers, when I use the previous configurations, there's no sound at all.

I went back to kernel 2.6.34, so I can't run the bug- audio command.

---

### Post by Reiger on 2010-12-19
Silly question: are you sure there's no sound, or are they just muted? (alsamixer -V playback)

If there really is no sound, trying for instance SPDIF instead of analog or vice versa might work around the problem too.

Also: [http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut) and/or [https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture) might prove useful resources.

---

### Post by lidex on 2010-12-19
If you are experiencing a regression, it would be very helpful for you to report a bug against that kernel so a fix can be released.

---

### Post by arashiko28 on 2011-02-06
Still no sound at all, this is taking longer than expected to be fixed and I'm worried about next release coming up and yet no fix to this.

---

### Post by dino99 on 2011-02-06
maybe you have some usefull errors logged about that

the latest kernel is 2.6.38.2 so better to try it

---

### Post by arashiko28 on 2011-02-06
Fresh upgrade, no sound at all. On headphones I do get some white noise nothing understandable. I'll try all over again with the list of possible configurations.

---

### Post by alexmurray on 2011-02-06
> **arashiko28 said:**
> Still no sound at all, this is taking longer than expected to be fixed and I'm worried about next release coming up and yet no fix to this.

If you don't file a bug how do you expect this to magically get fixed? File a bug which will let the developers know the bug exists, only then will there be any chance of it getting fixed. You can't complain about a bug not being fixed if you don't bother to bring it to the attention of those that can fix it.

---

### Post by arashiko28 on 2011-02-06
Hey, calm down. There are about 150 similar reports, I'm not the only one with this problem, and it's something carrying since 2.6.35 kernel, ever since then, I had to downgrade to 2.6.34 to have a working sound. I had reported this bug a long time ago and then again today.

---

### Post by arashiko28 on 2011-04-03
Hello, even though the header reads 2.6.37 it's actually 2.6.38 kernel.

The problem persist, still no sound at all, I'm upgrading to beta 1 right now.

I have already tried everything at hand and can't solve it on my own, I have filed bug reports but seems as if no one cares, is Ubuntu not supporting Lenovo laptops anymore o any of it's components? 

This problem has been carrying since Maverick release with no fixes or workarounds than downgrading kernel to 2.6.34.

Please help! Or at least answers!

---

### Post by cariboo on 2011-04-03
Can you give us a link to the bug report you created?

---

### Post by lidex on 2011-04-03
Or at least your alsa-info when booted into 2.6.37 (not the working one) ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by arashiko28 on 2011-04-03
Here are the bugs I've reported:

> [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/714323](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/714323)
[https://bugs.launchpad.net/alsa-driver/+bug/662009](https://bugs.launchpad.net/alsa-driver/+bug/662009)

I'm going to try the new patches from the latest comments :P

---

### Post by arashiko28 on 2011-04-03
:confused: sorry for the dumb question, but how do I install these patches? I have never done this before :oops:

---

### Post by lidex on 2011-04-03
It looks like he wants you to update your alsa driver modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by arashiko28 on 2011-04-04
> **lidex said:**
> It looks like he wants you to update your alsa driver modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

I can't install the modules, I get an error about not finding packages :confused:

> :~$ sudo apt-get install linux-alsa-driver-modules-$ 2.6.38-020638rc3
[sudo] password for...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-2.6.38-020638rc3' for regex '2.6.38-020638rc3'
Note, selecting 'linux-image-2.6.38-020638rc3-generic' for regex '2.6.38-020638rc3'
Note, selecting 'linux-headers-2.6.38-020638rc3-generic' for regex '2.6.38-020638rc3'
E: Unable to locate package linux-alsa-driver-modules-$
E: Couldn't find any package by regex 'linux-alsa-driver-modules-$'


---

### Post by cariboo on 2011-04-04
It looks like you either didn't get the ppa setup right, or you didn't do an update after you enabled the repository. Open Sysnaptic Package Manager and go to Settings->Repositories->Other Software, and make sure the ppa is setup.

---

### Post by arashiko28 on 2011-04-05
> **cariboo907 said:**
> It looks like you either didn't get the ppa setup right, or you didn't do an update after you enabled the repository. Open Sysnaptic Package Manager and go to Settings->Repositories->Other Software, and make sure the ppa is setup.

The ppa it is setup and box checked. I did ran update after adding ppa.

---

### Post by lidex on 2011-04-05
> **arashiko28 said:**
> The ppa it is setup and box checked. I did ran update after adding ppa.

It's probably that kernel you're in. Boot into default natty kernel and try it there.

---

### Post by arashiko28 on 2011-04-05
I am running kernel 2.6.38-020638rc3-generic, it's the available upgrade to the beta 1 version of natty. I decided to do it this way rather than VM to actually see it's behavior. This is how it goes step by step, perhaps you can see something I don't.

> ~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
[sudo] password for arashiko: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: "Launchpad Ubuntu Audio Dev team PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
> ~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty InRelease                               
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates InRelease                       
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Get:3 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates Release.gpg                     
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [737 B]                   
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources [14 B]                       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [14 B]            
Get:8 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty Release [39.8 kB]                     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages [14 B]                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [14 B]       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [14 B]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [14 B]     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [14 B] 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates Release                         
Get:17 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/main Sources [866 kB]                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Get:18 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/restricted Sources [4,117 B]         
Get:19 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/universe Sources [4,389 kB]          
Get:20 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/multiverse Sources [154 kB]          
Get:21 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/main i386 Packages [1,557 kB]        
Get:22 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/restricted i386 Packages [9,023 B]   
Get:23 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/universe i386 Packages [6,036 kB]    
Get:24 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/multiverse i386 Packages [182 kB]    
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/universe TranslationIndex               
Get:25 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/main Sources [14 B]          
Get:26 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/restricted Sources [14 B]    
Get:27 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/universe Sources [14 B]      
Get:28 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/multiverse Sources [14 B]    
Get:29 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/main i386 Packages [14 B]    
Get:30 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]
Get:31 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/universe i386 Packages [14 B]
Get:32 [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/multiverse i386 Packages [14 B]
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://do.archive.ubuntu.com](http://do.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 13.2 MB in 1min 19s (166 kB/s)                                         
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


As you can see, there is a problem updating and then:

> ~$ sudo apt-get install linux-alsa-driver-modules-$ 2.6.38-020638rc3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-2.6.38-020638rc3' for regex '2.6.38-020638rc3'
Note, selecting 'linux-image-2.6.38-020638rc3-generic' for regex '2.6.38-020638rc3'
Note, selecting 'linux-headers-2.6.38-020638rc3-generic' for regex '2.6.38-020638rc3'
E: Unable to locate package linux-alsa-driver-modules-$
E: Couldn't find any package by regex 'linux-alsa-driver-modules-$'


How do I fix this? All the repositories are checked.

---

### Post by lidex on 2011-04-05
I guess I need to re-read the postings over at launchpad. There are no natty sources at that ppa, hence the error.

Edit: Yep, here it is:
> @Stephanie, [COLOR="Red"]if you're running Ubuntu 10.10[/COLOR], you can follow the instructions here: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

The fix should be appearing in natty soon.
Or you could use the ppa modules in a maverick install - I'm just sayin'

---

### Post by cariboo on 2011-04-05
You could download the packages manually from the pps, and use dpkg to install them. I have to ask why you aren't using the default Natty kernel, I'm currently updating to 2.6.38-8.41

---

### Post by arashiko28 on 2011-04-05
> **lidex said:**
> I guess I need to re-read the postings over at launchpad. There are no natty sources at that ppa, hence the error.

Edit: Yep, here it is:


The fix should be appearing in natty soon.
Or you could use the ppa modules in a maverick install - I'm just sayin'

I already followed those instructions, however, i'll try it on previous kernel version installed. But what I showed earlier is on natty latest available kernel version.

---

### Post by arashiko28 on 2011-04-05
> **cariboo907 said:**
> You could download the packages manually from the pps, and use dpkg to install them. I have to ask why you aren't using the default Natty kernel, I'm currently updating to 2.6.38-8.41

I haven't seen this version offered for update, I'll manually download it.

Edit: I'm confused, there is already available 2.6.38.1-natty, 2.6.38.2-natty, 2.6.39-rc1-natty. Which one should I install?

---

### Post by arashiko28 on 2011-04-06
I have updated the kernel, but still don't understand why the updated kernels are separated on a previous kernel version hidden to view on grub and the old one stays as default. That's why I thought I had up to date kernel but actually didn't.

---

### Post by arashiko28 on 2011-04-07
I solved it. I updated the kernel to 2.6.38.2 and on etc/modprobe.d/alsa-base.conf file, changed the model to auto. Then opened alsa mixer and just raised the bar on all of the speakers, now 5.1 surround working as a charm!:D
Thanks to all, I hope it stays like this to the release.

---

