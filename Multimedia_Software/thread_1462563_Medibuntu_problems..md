---
title: "Medibuntu problems."
date: 2010-04-25
forum: Multimedia Software
---

### Post by keljaden on 2010-04-25
?

---

### Post by WinterRain on 2010-04-25
I believe their servers have been having problems lately. Be patient and try again.

---

### Post by 2hot6ft2 on 2010-04-25
> **keljaden said:**
> when I am attempting to get medibuntu to install, well I am having some problems, I have successfully installed medibuntu before. This is pretty much is what going on in the terminal.

I enter in:
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

And this is what happens;

Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110                                                         
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.                                      
HTTP request sent, awaiting response... 200 OK                                                       
Length: 272 [text/plain]                                                                             
Saving to: `/etc/apt/sources.list.d/medibuntu.list'                                                  

100%[===========================================================>] 272         --.-K/s   in 0s      

2010-04-25 20:52:40 (55.3 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]
It finished no errors there. You don't have to do that each time. Just once.
> **keljaden said:**
>     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     

That worked no problem with medibuntu.            
> **keljaden said:**
>     
Err [http://javadesktop.org](http://javadesktop.org) stable/contrib Packages                         
  404  Not Found
Beats me, that's something you added I think that had an error.                                                           
> **keljaden said:**
> W: Failed to fetch [http://javadesktop.org/lg3d/debian/dists/stable/contrib/binary-amd64/Packages.gz](http://javadesktop.org/lg3d/debian/dists/stable/contrib/binary-amd64/Packages.gz)  404  Not Found
Again, that's something you added I think that had an error.

> **keljaden said:**
> E: Some index files failed to download, they have been ignored, or old ones used instead.
[B]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

and I can't get the DVD and other codecs to install, any help?
And no other synaptic to my knowledge is open.
So medibuntu had no errrors but you have something open that has a lock on dpkg. It doesn't have to be Synaptic, it could be a terminal, Update Manager, Synaptic, A package installer. Something's open. Close it or reboot and try again before opening other things.

---

