---
title: "Resolution Stuck at 640x480"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by Dark Severance on 2008-03-01
I have looked through the various threads of those that have the similar issue, unfortunately none of them have been any help. I am using an Acer 17" monitor (AL1706) which supports up to 1280x1024.

I have manually edited /etc/X11/xorg.conf and rebooted but there are no changes in resolution.

With a previous monitor I had a similar issue, removing the lines for HorizSync and VertRefresh fixed it. But that didn't work for this time around either.

When I go into System -> Preferences -> Screen Resolution all it shows is 640x480. I don't see any of the other resolutions, even though I removed that from the xorg.conf as well.

I also tried sudo dpkg -reconfigure xserver-xorg creating a new xorg.conf and selected only 1280, 1024 and 800 which is shows in the xorg.conf but even after restarting XServer (Control + Alt + Backspace).

Any other ideas I can try?

```

Section "Monitor"                                                            
        Identifier      "Generic Monitor"                                    
        Option          "DPMS"                                               
#       HorizSync       28-64                                                
#       VertRefresh     43-60                                                
EndSection                                                                   
                                                                             
Section "Screen"                                                             
        Identifier      "Default Screen"                                     
        Device          "NVIDIA Corporation NVIDIA Default Card"             
        Monitor         "Generic Monitor"                                    
        DefaultDepth    24                                                   
        SubSection "Display"                                                 
                Depth           1                                            
                Modes           "1280x1024" "1280x800" "1024x768" "800x600"  
        EndSubSection                                                        
        SubSection "Display"                                                 
                Depth           4                                            
                Modes           "1280x1024" "1280x800" "1024x768" "800x600"  
        EndSubSection                                                        
        SubSection "Display"                                                 
                Depth           8                                            
                Modes           "1280x1024" "1280x800" "1024x768" "800x600"  
        EndSubSection
        SubSection "Display"                                                  
                Depth           15                                            
                Modes           "1280x1024" "1280x800" "1024x768" "800x600"   
        EndSubSection                                                         
        SubSection "Display"                                                  
                Depth           16                                            
                Modes           "1280x1024" "1280x800" "1024x768" "800x600"   
        EndSubSection                                                         
        SubSection "Display"                                                  
                Depth           24                                            
                Modes           "1280x1024" "1280x800" "1024x768" "800x600"   
        EndSubSection                                                         
EndSection
```

---

### Post by PurposeOfReason on 2008-03-01
What is your graphics card?

EDIT - Should've check the xorg for that. Have you installed the restricted drivers?

---

### Post by xzero1 on 2008-03-03
I'm guessing the monitor section has no real information about the monitor's requirements. First, back up xorg.conf then install the restricted drivers as mentioned above. Create a modeline based on your known screensize and refresh rates appropriate for your monitor. See "calculate using gtf" in: [http://gentoo-wiki.com/TIP_Getting_modelines#Calculate_Using_gtf]("http://gentoo-wiki.com/TIP_Getting_modelines#Calculate_Using_gtf")

---

### Post by alexandru_sorin on 2008-03-03
Have a problem with my monitor in ubuntu 7.10:
System: ACER Aspire 5520. Nvidia GeForce7000M, AMD64 Turion 2GHz, 2Gb Ram, 250HDD
The system don't remember what resolution i set after a logout, restart ....etc.
The monitor must be set at 1280x800 but he goes down to 800x600 every time. Try to use different monitor, like ACER 55, generic PnP, LCD1280x800, nothing change. I have install the nvidia restricted driver and everything is ok. Try to change settings with sude nvidia-settings, same thing. If anyone know a solution pls hepl me. I'm new with ubuntu.
Another problem is wireless. Is connecting when she wants, not when i want. Driver is ok, first time connecting was ok, after shut down stop working, After a while start working again.  Again stop's. Try to reset network, didn't help.I really need wireless and VPN (at school). 
Thank's 
Alex

---

### Post by snteran on 2008-03-03
Awesome....I only had one option for screen resolution, 800 x 600 and then I saw the post about using "restricted drivers".  I had to look around for what they were talking about, but finally found the section.  System > Administration > Restricted Drivers Manager.  Listed there was an option to install  nvidia drivers.  Selected and then restarted and I now have a few more options for screen resolution.  Thanks,
:)

---

