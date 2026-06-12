---
title: "Most pain free programs for Ipod video conversion"
date: 2008-12-01
forum: Multimedia Software
---

### Post by fewjr on 2008-12-01
Hello All,
I have and still am pouring over the forum and web trying to get a program going to rip dvds and convert them to Ipod format. I couldn't get the Ipod to mount, but got that taken care of thanks to some info on this forum. I have it working okay for music so far as I know. I tried installing handbrake, which seemed to install fine, but when I tried to run the program it didn't start. Nothing happened and I don't know why. I also tried to install winff which didn't show up in synaptic until I added another repository I read about. Even after that I could not get it to download and install in synaptic. It said it needed two libs and I'm at work so I cannot remember what ones they were right now, but I checked for them in synaptic and they were already installed. So I don't understand that. I tried uninstalling ffmpeg and reinstalling it again also. So I am at a standstill. If anyone can help with this I would appreciate it. I am trying to use this with Hardy right now. Ibex is installed, but I have issues with both versions, so I thought I'd use Hardy for now. If there are any commands you need me to run to give better info I can do it when I get home. Thank you in advance.

fewjr

---

### Post by fenian on 2008-12-01
Handbrake was first developed for the Mac and has presets for ipods/iphones.I use Handbrake for all my ripping/encoding it works quite well IMHO are you sure you downloaded and instaled the version with the GTK GUI (they also have a command line only version)?You can get the GTK GUI version [here]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb").You can read more about Handbrake [here]("http://trac.handbrake.fr/wiki/HandBrakeGuide").

---

### Post by fewjr on 2008-12-01
fenian,
     Thanks for the fast response. I believe I installed the right one. If I got up to Applications>under the proper menu I find the icon to start the program, but nothing happens when I try to run it from this launcher. I will uninstall and try again. I just checked your link and that is where I downloaded it from. I used: GTK GUI (Ubuntu 8.10 x86 Binaries). 
 
fewjr

---

### Post by fewjr on 2008-12-02
An update on this. This is what it says when I try to install winff from Synaptic:
> Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.Make sure that all required repositories are added and enabled in the preferences.

winff:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1 is to be installed

I'm not sure what repository it means. Under third party sources I have [http://winff.org/ubuntu](http://winff.org/ubuntu) hardy universe and [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy free non-free enabled. Under Ubuntu software tab, main, universe, restricted and multiverse are all checked. Also I just noticed this. When I try to reload Synaptic I get an error:
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
What is the public key? That is probably why I can't get the proper libs. I'm guessing.

---

### Post by fewjr on 2008-12-05
bump please...and also, I installed Handbrake gui version but it does not launch. I did have a little success with Mvpod, but the encode fails in xvid and H264.

---

### Post by paul.gevers on 2008-12-05
> **fewjr said:**
> An update on this. This is what it says when I try to install winff from Synaptic:



I will look at this tonight. Looks like there is something wrong with the package.

> **fewjr said:**
> What is the public key? That is probably why I can't get the proper libs. I'm guessing.

A public key is used to sign all packages distributed by Ubuntu, or other repositories, so that you (or your program) can verify that the source is ok. Before it can do that it needs to trust (and know) the key. I described it in the second half of [[1]("http://code.google.com/p/winff/wiki/UbuntuInstallation")]. The steps consist of:
First install the repository (looks like you already did that:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Than add the keyring:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Hope this helps.
Paul
[1] [http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

---

### Post by fewjr on 2008-12-05
Okay, let me know please if you find a problem with the package. I redid the wget and apt-get update commands and opened synaptic. I reloaded synaptic and searched for winff, but nothing comes up from the search now. I guess I'll wait and see what you come up with. Thank you for checking and for all your work on the project.

fewjr

---

### Post by paul.gevers on 2008-12-05
> **fewjr said:**
> Okay, let me know please if you find a problem with the package. I redid the wget and apt-get update commands and opened synaptic. I reloaded synaptic and searched for winff, but nothing comes up from the search now. I guess I'll wait and see what you come up with.

Not working on it yet, but could you try to install winff directly:
```
sudo apt-get install winff
```
and post the output here (I assume that it will fail as you don't see it in Synaptic, but it might help me in determining what is going on).

---

### Post by fewjr on 2008-12-05
Here you go Sir. looks like your right.

```
goblin@goblin-lanbox:~$ sudo apt-get install winff
[sudo] password for goblin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package winff
goblin@goblin-lanbox:~$ 

```


Best Regards
fewjr

---

### Post by paul.gevers on 2008-12-05
> Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.Make sure that all required repositories are added and enabled in the preferences.

winff:
Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1 is to be installed

I understand now what was wrong there, that was a my mistake. I use a script to create my local repositories for the different Ubuntu releases, but it behaved differently than I expected. You were downloading the intrepid version instead of the hardy version. This should be fixed two days ago.

> **fewjr said:**
> goblin@goblin-lanbox:~$ sudo apt-get install winff
[sudo] password for goblin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package winff
goblin@goblin-lanbox:~$
This looks exactly like I expected after the rest of your comments. I just tried on my own system using the hardy repository (I have intrepid myself) and for me it worked.

Just to be sure, did you install my public key, as described on the [winff wiki]("http://code.google.com/p/winff/wiki/UbuntuInstallation")? The necessary code is:
```
wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add -
```

If no, can you try that first? If yes, then I wonder, did you put the description of the repository in /etc/apt/sources.list or in /etc/apt/sources.list.d/winff.list? Can you show the content of that file (at least the lines with the winff source)?
```
cat /etc/apt/sources.list | grep winff
# or
cat /etc/apt/sources.list.d/winff.list
```
Can you please also update via command prompt and post the output:
```
sudo apt-get update
```
If you don't want to show the complete output, try to locate the lines like:
```
Get:2 http://winff.org hardy Release.gpg [197B]                                
Ign http://winff.org hardy/universe Translation-en_US                          
Get:4 http://winff.org hardy Release [2896B]                                   
Get:6 http://winff.org hardy/universe Packages [706B]

```
although I expect that you see something different due to the problem your having.

---

### Post by fewjr on 2008-12-05
paul.geavers,
I am very sorry, but I started this thread 4 days ago when I was using Hardy and thought I would change up and concentrate on Intrepid instead. I was doing so many things in Hardy that I was afraid I had messed up to many things. When I bumped the thread and you jumped in, I had started using Intrepid. Anyway the commands I ran from your first two post here were in Intrepid. When I ran the commands from your wiki site I was using hardy. I saw that you needed to change intrepid to hardy. I did add the key also then.> If you use the signed repository you need to accept the key AAFE086A. To get that installed you can run: 

```
wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add -

```
> After that you need to add the repository to apt. You can do that by entering the line (1) in /etc/apt/sources.list.d/winff.list. You will have to create that file, which can be done with the following command: 

```
echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list

```
> (Of course change intrepid to hardy or jaunty if you need that). You can also just add the line to /etc/apt/sources.list . 


I am at work now until 7:00a.m. tomorrow morning. I will make sure I added the key and repository in Intrepid. I will try to get the commands run and posted here for you as soon as I can. I will do it in both Intrepid and Hardy if you like. At any rate, I did have the same problem in Hardy as stated in the first post above.  Thanks you for your help. 

Best Regards
fewjr 

fewjr

---

### Post by fewjr on 2008-12-05
Paul,
I think I see what I did wrong. I missed a step if I'm not mistaken. I will check tomorrow.
> After that you need to add the repository to apt. You can do that by entering the line (1) in /etc/apt/sources.list.d/winff.list. You will have to create that file, which can be done with the following command: 
```
echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list
``` 
I did those fine, but I think I forgot to go down to (1)
> (1) deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe 
and add it to /etc/apt/sources.list.d/winff.list file. If thats what I did, I am sorry. I will post when I'm sure. noob mistake!:rolleyes:

---

### Post by paul.gevers on 2008-12-05
> **fewjr said:**
> Paul,
I think I see what I did wrong. I missed a step if I'm not mistaken. I will check tomorrow.

```
echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list
``` 
I did those fine, but I think I forgot to go down to (1)

and add it to /etc/apt/sources.list.d/winff.list file. If thats what I did, I am sorry. I will post when I'm sure. noob mistake!:rolleyes:

I don't think you did it wrong, if I read you correct here. The code is *a* way to achieve that the deb http.... ends up in the file. But anyway, lets check what is in your /etc/apt/sources.list.d/winff.list file. Then we know more.

---

### Post by paul.gevers on 2008-12-05
Anyway, I also updated the description at the [winff wiki]("http://code.google.com/p/winff/wiki/UbuntuInstallation") to include a description for synaptic. I hope that works.

---

### Post by fewjr on 2008-12-06
Paul,
In Intrepid I ran:
```
goblin@goblin-lanbox:~$ gksudo gedit /etc/apt/sources.list.d/winff.list

``` I get an empty file...it does not exist. I opened the folder manually and all that is in  /etc/apt/sources.list.d/ is medibuntu.list.

---

### Post by fewjr on 2008-12-06
So I followed your install steps more closely. I thought i forgot something. Here is the output:
```

goblin@goblin-lanbox:~$ wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add -
OK
goblin@goblin-lanbox:~$ echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list
deb http://winff.org/ubuntu intrepid universe
goblin@goblin-lanbox:~$ sudo apt-get update && sudo apt-get install winff
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US       
Hit http://archive.canonical.com intrepid Release.gpg                         
Ign http://archive.canonical.com intrepid/partner Translation-en_US           
Hit http://packages.medibuntu.org intrepid Release.gpg                        
Hit http://us.archive.ubuntu.com intrepid Release.gpg                         
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US              
Get:1 http://winff.org intrepid Release.gpg [197B]                            
Ign http://winff.org intrepid/universe Translation-en_US                      
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US 
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US   
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US 
Hit http://archive.canonical.com intrepid Release                             
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US        
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US          
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US        
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                 
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US      
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US  
Get:2 http://winff.org intrepid Release [2902B]                               
Hit http://security.ubuntu.com intrepid-security Release                      
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg      
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Hit http://archive.canonical.com intrepid/partner Packages           
Ign http://packages.medibuntu.org intrepid/free Translation-en_US    
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release                             
Hit http://us.archive.ubuntu.com intrepid-updates Release                     
Hit http://archive.canonical.com intrepid/partner Sources                     
Hit http://security.ubuntu.com intrepid-security/main Packages                
Get:3 http://winff.org intrepid/universe Packages [744B]                      
Hit http://us.archive.ubuntu.com intrepid-backports Release                   
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US         
Hit http://security.ubuntu.com intrepid-security/restricted Packages 
Hit http://security.ubuntu.com intrepid-security/main Sources                 
Hit http://security.ubuntu.com intrepid-security/restricted Sources           
Hit http://us.archive.ubuntu.com intrepid/main Packages                       
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                 
Hit http://us.archive.ubuntu.com intrepid/main Sources                        
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                  
Hit http://us.archive.ubuntu.com intrepid/universe Packages                   
Hit http://security.ubuntu.com intrepid-security/universe Packages            
Hit http://security.ubuntu.com intrepid-security/universe Sources             
Hit http://security.ubuntu.com intrepid-security/multiverse Packages          
Hit http://security.ubuntu.com intrepid-security/multiverse Sources           
Hit http://us.archive.ubuntu.com intrepid/universe Sources                    
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                 
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://packages.medibuntu.org intrepid Release
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-backports/main Sources
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Sources
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 3843B in 1s (3084B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  winff
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1515kB of archives.
After this operation, 5173kB of additional disk space will be used.
Get:1 http://winff.org intrepid/universe winff 0.43-0ubuntu1~ppa2i [1515kB]
Fetched 1515kB in 2s (664kB/s)  
Selecting previously deselected package winff.
(Reading database ... 139496 files and directories currently installed.)
Unpacking winff (from .../winff_0.43-0ubuntu1~ppa2i_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up winff (0.43-0ubuntu1~ppa2i) ...

goblin@goblin-lanbox:~$ 


``` 

Winff is now installed. This was in intrepid, I will post for hardy in a minute.

fewjr

---

### Post by fewjr on 2008-12-06
Okay paul,
In Hardy, there is an winff.list file and deb [http://winff.org/ubuntu](http://winff.org/ubuntu) hardy universe is listed. For some reason in /etc/apt/sources.list.d/ I have my winff.list and medibuntu.list files, but there are also copies of each file named medibuntu.list.save and winff.list.save. I don't know why or if it matters. I ran the install command and winff is installed on hardy now. Here is the output:
```
goblin@goblin-lanbox:~$ sudo apt-get update && sudo apt-get install winff
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Get:2 http://packages.medibuntu.org hardy Release.gpg [189B]                   
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Get:3 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]            
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Get:4 http://security.ubuntu.com hardy-security Release [58.5kB]               
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com hardy Release                                 
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Get:5 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]              
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Get:6 http://winff.org hardy Release.gpg [197B]                                
Ign http://winff.org hardy/universe Translation-en_US                          
Get:7 http://winff.org hardy Release [2896B]                                   
Get:8 http://security.ubuntu.com hardy-security/main Packages [89.4kB]         
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Get:9 http://winff.org hardy/universe Packages [706B]                          
Get:10 http://packages.medibuntu.org hardy Release [9335B]                   
Ign http://packages.medibuntu.org hardy Release                                
Get:11 http://us.archive.ubuntu.com hardy-updates/main Packages [390kB]        
Get:12 http://security.ubuntu.com hardy-security/restricted Packages [7487B]   
Get:13 http://security.ubuntu.com hardy-security/universe Packages [46.9kB]    
Hit http://packages.medibuntu.org hardy/free Packages                          
Get:14 http://security.ubuntu.com hardy-security/multiverse Packages [8986B]   
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Get:15 http://us.archive.ubuntu.com hardy-updates/restricted Packages [7487B]
Get:16 http://us.archive.ubuntu.com hardy-updates/universe Packages [147kB]
Get:17 http://us.archive.ubuntu.com hardy-updates/multiverse Packages [24.2kB]
Fetched 843kB in 2s (390kB/s)                          
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ffmpeg
The following NEW packages will be installed:
  ffmpeg winff
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 1289kB/1483kB of archives.
After this operation, 4284kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ffmpeg
Install these packages without verification [y/N]? y
Get:1 http://winff.org hardy/universe winff 0.43-0ubuntu1~ppa1h [1289kB]
Fetched 1289kB in 1s (668kB/s)  
Selecting previously deselected package ffmpeg.
(Reading database ... 146439 files and directories currently installed.)
Unpacking ffmpeg (from .../ffmpeg_3%3a0.cvs20070307-5ubuntu7.1+medibuntu1_i386.deb) ...
Selecting previously deselected package winff.
Unpacking winff (from .../winff_0.43-0ubuntu1~ppa1h_i386.deb) ...
Setting up ffmpeg (3:0.cvs20070307-5ubuntu7.1+medibuntu1) ...
Setting up winff (0.43-0ubuntu1~ppa1h) ...

goblin@goblin-lanbox:~$ 


```

Thank you for knocking me in the head and making me think it out. I'm not sure where I went wrong before. If you really did find something wrong like you said, then that is probably why it installed in Hardy this time.

Best regards
fewjr

---

### Post by paul.gevers on 2008-12-06
I am glad it works for you now, but the only change that I made was that the files pointed to changed, see your original message that complained about
> Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1 is to be installed 
So the rest of the story has not changed. It is a shame that we don't know exactly what you did different now, but at least it works. Thanks for confirming that.

---

### Post by paul.gevers on 2008-12-06
> **fewjr said:**
> For some reason in /etc/apt/sources.list.d/ I have my winff.list and medibuntu.list files, but there are also copies of each file named medibuntu.list.save and winff.list.save. I don't know why or if it matters.
This does not matter, they are just backup files, probably because you did an upgrade, or used synaptic to change something, or... I don't know, but they are not used by apt/synaptic during normal operation.

---

### Post by fewjr on 2008-12-06
Hello Paul,
Yes, now I have to learn how to use the program. I'll be reading all about presets tonight I suppose. 
> Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1 is to be installed  
This was odd to me because when I went into synaptic to check for them, they were already installed. Why does it say it depends on the ones that are there and at the same time is going to install a different version of these libs? 
Thanks again Paul.

---

### Post by paul.gevers on 2008-12-06
> **fewjr said:**
> This was odd to me because when I went into synaptic to check for them, they were already installed. Why does it say it depends on the ones that are there and at the same time is going to install a different version of these libs?

It means that the version that is necessary is higher than anything you can install. Synaptic warns you that the program will not be able to run and therefor won't install it.

---

### Post by fewjr on 2008-12-06
Ah...that makes sense. Well winff starts up fine. Can you point me to a howto that will help with using the program. I'm a father of 5 girls, and I'm finding it hard to figure out what I need to do with going to work and family. What I mean is my time is limited in teaching myself. I think thats why I made the blunder installing your program. I start to figure something out and I have to put it up and go to work or take care of the kids...LOL. I thought I read that you could copy a dvd to an iso image and convert it later. I have 3 iso movies on my hard drive. I also have one that was ripped with DVDrip.  I am choosing ipod (16:9), but I don't know what to put for the additional options. I need something to read up on while I'm at work tonight. If I try to convert the vob files I get some errors about...well it won't let me copy/paste from ffmpeg terminal, but it says > unknown encoder 'libxvid' It says the same thing for H264 except for libx264. I am using the presets that come with the version of winff that we just got installed here. Also can the iso images be converted as is or do they need to be ripped first? I know this goes beyond what the thread was about, but I thought I'd ask while you were watching.

Thanks much
fewjr

---

### Post by paul.gevers on 2008-12-06
> **fewjr said:**
> Ah...that makes sense. Well winff starts up fine. Can you point me to a howto that will help with using the program.
If you find the time, the manual is included in the package. So you can take a look on your harddrive at /usr/share/doc/winff/WinFF.pdf.gz (you will have to `gunzip` that one first. It can also be found in the download section of the winff.org site.

> I thought I read that you could copy a dvd to an iso image and convert it later. I have 3 iso movies on my hard drive. I also have one that was ripped with DVDrip.

Sorry, I don't have much knowledge about this, I only use it to convert my own movies (photo-camera). But I guess if the next problem is solved you are already on the right track.

> If I try to convert the vob files I get some errors about...well it won't let me copy/paste from ffmpeg terminal, but it says
```
unknown encoder 'libxvid' 
```
It says the same thing for H264 except for libx264.

This means that ffmpeg does not have the right codecs available. You are running intrepid, right? Winff **should** have installed ubuntu-restricted-extras. Can you check if that is installed? If not, you can install it or directly the necessary codec:
```
sudo apt-get install libavcodec-unstripped-51
```

If it is installed, but it still does not work, I read somewhere that it might help to purge ffmpeg like so (although I don't understand why that would work):
```
sudo apt-get purge ffmpeg
sudo apt-get update
sudo apt-get install ffmpeg libavcodec-unstripped-51
```

Hope this helps.

---

### Post by paul.gevers on 2008-12-06
Hmm. We did find a problem with my description here. If I say we use the command line, apt doesnot install (k|x|)ubuntu-restricted-extras. So I have to add that to the description. If you followed my code, you need to manually add **works only for intrepid**```
sudo apt-get install libavcodec-unstripped-51
```

I updated the description on the winff.org website. Thanks for helping spotting that.

---

### Post by fewjr on 2008-12-06
I added the unstripped-51 and it starts to convert. So i think you have me on the right track. I will stick with this until I learn it all as best I can. I have to go to work. Thanks and I'll post tomorrow to update you.

---

