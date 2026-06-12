---
title: "Help with NVIDIA drivers and required files"
date: 2009-12-29
forum: Mythbuntu
---

### Post by rodercot on 2009-12-29
Hey All,

 I am in need of some clarification. I could at this point have about 10 ppa's in my sources.list if I just took the advice from Google searches.

 I always install my nvidia drivers from the command line and usually tend to install the latest beta drivers. I am confused at to the libs that should be installed or should not be installed with a particular beta driver or any driver for that matter. 

 right now I have 195.22 installed but if I grep nvidia I have libs like this

```
xbmc@xbmc:~$ dpkg -l|grep nvidia     
ii  libvdpau1                                  0.3-2ubuntu1~nvidiavdpauppa4                                                                                     
				Video Decode and Presentation API for Unix (
ii  libxine1-bin                               1.1.16.3-vdpau-0ubuntu2~karmic~nvidiavdpauppa1 
				the xine video/media player library, binary
ii  nvidia-173-modaliases                      173.14.12-1-0ubuntu5.1
                                                Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-modaliases                      177.82-0ubuntu0.1                                                                                                
				Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-180-libvdpau                        180.37-0ubuntu1~intrepid2 
                                                Video Decode and Presentation API for Unix
ii  nvidia-180-modaliases                      180.37-0ubuntu1~intrepid2
                                                Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-185-modaliases                      185.18.36-0ubuntu10~karmic~nvidiavdpauppa2 
				Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-190-modaliases                      190.53-0ubuntu1~karmic~nvidiavdpauppa7 
			            Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-195-modaliases                      195.30-0ubuntu1~karmic~nvidiavdpauppa1 
			            Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                       71.86.04-0ubuntu10 
                                                Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                       96.43.09-0ubuntu1.1                                                                                       
			            Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                              0.2.4.2                                                                                                          

Find obsolete NVIDIA drivers
```

 I am in the 190 series drivers, testing between 190.42-pkg1.run and 195.22-pkg1.run. 
 
 What files should I have and which file should not be there. 

 thanks and sorry for the long post, I spent most of yeaterday searching for some sort of answer. Hopefully JYA can chime in on this.

 both of my Front end systems are A P5N7A-VM - C2D 7400 - 2Gb 800 - Nvidia 9400 - HDMI 

 Regards,

 Dave

---

