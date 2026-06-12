---
title: "sirius XM from command line"
date: 2010-07-29
forum: Multimedia Software
---

### Post by nixIT on 2010-07-29
If you were like me, you longed to listen to your favorite sirius XM satellite radio without the annoying popup every 90ish minutes.  And if you were like me, you missed sipie, an application that allowed you to stream sirius via a command line.

Since sipie has been flakey, some people have decided to start a new project on GITHUB, called pyxis, and I have to say, after installing (which is a breeze), it is working perfectly.  I am excited to have my sirius back up and running strong from the command line.

Here is the link to the main page:  
[http://ionshard.com/pyxis]("http://ionshard.com/pyxis")

From the developer:
> 
Installation on Ubuntu is simple:
sudo add-apt-repository ppa:pyxis/pyxis && sudo apt-get update && sudo
apt-get install pyxis

then just run pyxis or pyxis --help


Please note, I have no affiliation with the development team, I just thought that this very handy application deserved to be recognized and appreciated.

to all the sirius listeners out there....ENJOY!

--nixIT

---

### Post by Kasuko on 2010-07-29
EDIT: No Longer True as of version 0.2.1

I would like to point out that currently siriuscanada.ca does not work. It has been brought to my attention though and I am working on it.

---

### Post by Hogmeister on 2010-08-06
i ..... LOVE YOU!!!! 

ugh i had it working fine inside of firefox and chrome in my previous install of kubuntu 10.04 and then i decided i wanted to try 10.10 ubuntu (gnome rather than kde this time) and for whatever reason i could not get it to work at all in either browsers.....

this post rules and i love whoever made pyxis :)

---

### Post by spesheled1 on 2010-08-08
This is a SWEET little program! Sirius XM from the command line is pretty awesome! Thanks.

---

### Post by nixIT on 2010-08-09
> **Hogmeister said:**
> i ..... LOVE YOU!!!! 

ugh i had it working fine inside of firefox and chrome in my previous install of kubuntu 10.04 and then i decided i wanted to try 10.10 ubuntu (gnome rather than kde this time) and for whatever reason i could not get it to work at all in either browsers.....

this post rules and i love whoever made pyxis :)

You'll need to thank Eli for the original Sipie and Kasuko for pyxis.

--nixIT

ps.  havne't had a hic-up on it since I installed it, working GREAT.

---

### Post by Kasuko on 2010-08-09
Wow, this is really great to see. Thank you so much for the words of encouragement. Really makes it all worthwhile in the end.

---

### Post by jpb0104 on 2010-08-26
This is awesome I agree. I'd love to get the ball rolling on how to record mp3s from the stream.  I think mplayer can do that.  Anyone have anything setup to do this?

---

### Post by Kasuko on 2010-08-31
> **nixIT said:**
> You'll need to thank Eli for the original Sipie and Kasuko for pyxis.
Please don't forget JohnR and JVC. They did more work than I did :P

> **jpb0104 said:**
> This is awesome I agree. I'd love to get the ball rolling on how to record mp3s from the stream.  I think mplayer can do that.  Anyone have anything setup to do this?

JohnR added record support to the current HEAD of the git repo if you want to play with that,

Like I said I am currently engaged in Canada support. I will be getting to the MP3 recording when that is done.

---

### Post by cheqmate1 on 2010-09-04
Just wanted to thank you guys for your work. This is excellent. I have been a fan of sipie for a while now, and have been bummed that the developer had to discontinue support. 

THANK YOU!!

---

### Post by akshunj on 2010-09-27
AWESOME and insanely easy to use!!!

The Web player only works with Firefox and is crazy slow, AND it doesn't show song artist and titles. This is fast and shows song info!  Thanks to the dev!

--Akshun J

---

### Post by one2bet on 2010-10-25
I tried installing Pyxis on 64-bit Ubuntu 10.10 and got the following errors:
$ [SIZE=5]*sudo add-apt-repository ppa: pyxis/pyxis*[/SIZE]
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 00421A8454B06F816217BC1AC7A98659083FACDB
gpg: requesting key 083FACDB from hkp server keyserver.ubuntu.com
gpg: key 083FACDB: "Launchpad Pyxis" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
you@Howard100:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                                                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                        
Ign [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/) maverick/main Translation-en                                     
Ign [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/) maverick/main Translation-en_US   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                          
Ign [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/) maverick/main Translation-en              
Ign [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/) maverick/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US                                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
W: Failed to fetch [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
$

It looks like my machine is not "hitting" some update packages. Anyone knows how to correct it?

---

### Post by one2bet on 2010-10-25
I tried installing Pyxis on 64-bit Ubuntu 10.10 and got the following errors:
$ [SIZE=5]*sudo add-apt-repository ppa: pyxis/pyxis*[/SIZE]
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 00421A8454B06F816217BC1AC7A98659083FACDB
gpg: requesting key 083FACDB from hkp server keyserver.ubuntu.com
gpg: key 083FACDB: "Launchpad Pyxis" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
you@Howard100:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                                                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                        
Ign [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/) maverick/main Translation-en                                     
Ign [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/) maverick/main Translation-en_US   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                          
Ign [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/) maverick/main Translation-en              
Ign [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/) maverick/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US                                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
W: Failed to fetch [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pyxis/pyxis/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
$

It looks like my machine is not "hitting" some update packages. Anyone knows how to correct it?

---

### Post by Kasuko on 2010-10-26
Sorry about that, I didn't have Pyxis built for Maverick. I just copied the binaries to Maverick, it should work since it's python but if it doesn't let me know.

Try again via sudo apt-get update
sudo apt-get install pyxis

---

### Post by one2bet on 2010-10-31
Thank you! Thank you! Thank you!

---

### Post by telengard on 2010-11-27
Just installed the latest and I get this:

Traceback (most recent call last):
  File "/usr/local/bin/pyxis", line 47, in <module>
    Interface(opts, station)
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Interface.py", line 77, in __init__
    self.repl()
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Interface.py", line 138, in repl
    completer = Completer([x['longName'] for x in self.sirius.getStreams()])
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Sirius.py", line 301, in getStreams
    self.auth()
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Sirius.py", line 198, in auth
    raise LoginError
pyxis.Sirius.LoginError

I've run the setup multiple times to ensure I have entered the right login info.  My other script stopped working recently too.  I wonder if something has changed on the XM side?  For the record, logging in via the normal web method works fine.

~telengard

---

### Post by Kasuko on 2010-11-27
Can you please edit the file ~/.config/pyxis/pyxisrc and change the line Debug=False to Debug=True (Also you can modify the Directory=~/pyxisdebug to change the default location of the debug data) then run the program again. After you get the exception can you zip/tar the debug data (again default at ~/pyxisdebug) and email that to me at [email]coreyling@ionshard.com[/email]

We'll figure this out!

---

### Post by cheqmate1 on 2010-11-29
Hi, 

Since upgrading to 10.10 I do not get sound from the pyxis app. 

It runs, the pop-up occurs for new songs, I see the songs on the
command line, but I have no sound. 

I have sound in all other apps, just nothing from pyxis. 

Any ideas?

Thanks,
Cheqmate1

---

### Post by xm1014 on 2010-12-10
I'm having the same issue as cheqmate1!

Any ideas folks? 

I'll be glad to post debug info if I could get some info on how to gather it :)

---

### Post by cheqmate1 on 2010-12-18
For what it is worth and in the hopes of helping someone else, I appear to be having an mplayer issue. I noticed in the pyxis debug file that pyxis runs a mplayer command so I attempted to run mplayer from the command line and received the following error,

/usr/bin/mplayer: error while loading shared libraries: libvdpau.so.1: cannot open shared object file: No such file or directory

It seems to be some type of issue related to the nvidia card and driver that I am using. 

Hope that helps point someone else in the right direction. I miss my Octane!

---

### Post by cheqmate1 on 2010-12-18
Further update - I removed mplayer and libvdpau1 (i.e. sudo apt-get remove mplayer and sudo apt-get remove libvdpau1), then installed them again (i.e. sudo apt-get install mplayer libvdpau1) and I no longer get the mplayer error. 

I cannot fully test this until Monday, I am accessing that box remotely so I cannot tell if this has corrected the sound issue with pyxis, but it seems promising!

---

### Post by xm1014 on 2010-12-18
> **cheqmate1 said:**
> Further update - I removed mplayer and libvdpau1 (i.e. sudo apt-get remove mplayer and sudo apt-get remove libvdpau1), then installed them again (i.e. sudo apt-get install mplayer libvdpau1) and I no longer get the mplayer error. 

I cannot fully test this until Monday, I am accessing that box remotely so I cannot tell if this has corrected the sound issue with pyxis, but it seems promising!

This worked for me! Can't wait to start listening to Alt Nation via the command line :)

---

### Post by cheqmate1 on 2010-12-20
Update - that worked, it was an mplayer issue.

---

### Post by Kasuko on 2010-12-29
Thanks for figuring it out cheqmate1, I haven't had much time to work on it as of recently (just finishing up a semester of school)

Is there anything regarding the packaging of pyxis you found to be wrong or was it just an upgrade issue?

---

### Post by Dr. Feltersnatch on 2011-01-01
Nice work Kasuko! Thanks!!

I got this working on my N900 too without a hitch.

---

### Post by shaunjohn007 on 2011-01-06
i read somewhere that there was ability to record is that possible, do i need to reinstall for that update

---

### Post by Kasuko on 2011-01-21
Version 0.2.1 Released!

Now supports Sirius Canada and recording (No timed recording though)

To record just run pyxis --record <name of file>.mp3

---

### Post by Joseph R on 2011-01-21
> **telengard said:**
> Just installed the latest and I get this:

Traceback (most recent call last):
  File "/usr/local/bin/pyxis", line 47, in <module>
    Interface(opts, station)
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Interface.py", line 77, in __init__
    self.repl()
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Interface.py", line 138, in repl
    completer = Completer([x['longName'] for x in self.sirius.getStreams()])
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Sirius.py", line 301, in getStreams
    self.auth()
  File "/usr/local/lib/python2.6/dist-packages/pyxis/Sirius.py", line 198, in auth
    raise LoginError
pyxis.Sirius.LoginError

I've run the setup multiple times to ensure I have entered the right login info.  My other script stopped working recently too.  I wonder if something has changed on the XM side?  For the record, logging in via the normal web method works fine.

~telengard

I've just had this same problem come up. Yesterday everything was fine, even after the latest package releases on 10.10 x64. This morning I attempted to reconnect to Sirius (system was still on from previous day) and I'm getting the same Auth error messages. I haven't dug into yet...

Edit: removed and reinstalled pyxis package and all is working again.

---

### Post by Kasuko on 2011-01-21
> **Joseph R said:**
> I've just had this same problem come up. Yesterday everything was fine, even after the latest package releases on 10.10 x64. This morning I attempted to reconnect to Sirius (system was still on from previous day) and I'm getting the same Auth error messages. I haven't dug into yet...

So it was working on Pyxis before though?
Can you follow the steps here [https://github.com/Kasuko/pyxis/wiki/Sending-Debug-Information]("https://github.com/Kasuko/pyxis/wiki/Sending-Debug-Information")

Thank you
Kasuko

---

