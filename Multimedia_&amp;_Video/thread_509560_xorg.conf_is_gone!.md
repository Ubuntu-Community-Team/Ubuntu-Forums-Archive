---
title: "xorg.conf is gone!"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by Hullon on 2007-07-25
Is there a way to recreate it without reinstalling ubuntu?

---

### Post by dabl on 2007-07-25
Assuming you're looking at the Command Line Interface (CLI, aka "text prompt") you can enter ```
sudo dpkg-reconfigure xserver-xorg
``` and it will build a new xorg.conf file for you.  When you finish the script, it will dump you back to the CLI.  At that point, you can enter ```
startx
``` and you should get a GUI login prompt. :)

And then you can make a backup of xorg.conf!

---

### Post by Hullon on 2007-07-25
> Users of PowerPC machines, and users of any computer with multiple video  
devices, should specify the BusID of the video card in an accepted        
bus-specific format.                                                      
                                                                          
Examples:                                                                
                                                                          
 ISA:1                                                                    
 PCI:0:16:0                                                               
 SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000

For users of multi-head setups, this option will configure only one of    
the heads.  Further configuration will have to be done manually in the X  
server configuration file, /etc/X11/xorg.conf.                            
                                                                        
You may wish to use the "lspci" command to determine the bus location of  
your PCI, AGP, or PCI-Express video card.                                 
                                                                        
When possible, this question has been pre-answered for you and you        
should accept the default unless you know it doesn't work. 

But it won't let me go any further, what should i do?

---

### Post by Hullon on 2007-07-26
After rereading your post i realized maybe I should mention this, I have a GUI right now.

---

### Post by dabl on 2007-07-26
Good!  Sorry I didn't see the problem with your PCI ID -- guess it's a good thing because I've never used it.  :popcorn:

---

### Post by Hullon on 2007-08-01
I was away for awhile and couldn't continue posting here. I have a GUI but the xorg.conf is still gone. But the wierd thing is that as I have understood it xorg.conf is needed for the GUI to show at all.

---

### Post by Hullon on 2007-08-01
Is there a way to get xorg.conf from a livecd?

---

