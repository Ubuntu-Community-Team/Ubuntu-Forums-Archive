---
title: "NVidia Settings will not stick and other problems."
date: 2008-07-26
forum: Multimedia Software
---

### Post by galvheim on 2008-07-26
Hi again, helpers who are more clever than me!

Here's my struggle. 
I have followed this guide to the letters: 
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6")

But still I get this message when trying to go into *NVIDIA X Server Settings*, and then into *X Server Display Configuration*:
[COLOR="Navy"][SIZE="1"]Unable to load X Server Display Configuration page:

Failed to parse the following modeline of display device
0x00000001 'Samsung SyncMaster' connected to GPU-0 'GeForce 8800 GTS':

source=xserver, source=vesa, source=edid :: "nvidia-auto-select"  108.000  1280 1328 1440 1688  1024 1025 1028 1066  +HSync +VSync[/SIZE][/COLOR]

I have tried these solutions and they somehow worked - but only when using this code:
```
sudo LANG=C nvidia-settings --and--
sudo LANG=C nvidia-xconfig
```

When I do a normal start of NVIDIA X Server Settings it's still back to "normal" again. 

But this is not my biggest issue. 
My biggest issue is that the settings for VSync, Mouse Shadow, Quality, Antialiasing, Overriding settings, Anisotropic Filtering and much more will never stick for longer than next time I reboot my box. 
This has been a problem since I first started using Ubuntu 1 year ago, and this issue has not yet been resolved. I have tried edit the xorrg.conf file by hand and also tried to edit the .nvidia-settings-rc file, and after that write protect it. Nothing seems to work. Even sudo'ing the nvidia-settings controls seems to do nothing. 

This is annoying since I thought this would be a much less pain than it is. I just never will stick and I don't know why this has to be. 
I have tried maybe 10 suggested solutions to this problem, but as I have said; this will be wiped clean off everytime Ubuntu starts up again. It's very annoying and I'm very sure there must be an easy way around this, but for me this seems like a never ending story. 

I can live with this problem, but I hate to have a NVidia 8800 GTS in my computer who does nothing. I want compiz to shine with high antialiasing settings and other stuff, but no...

How can I fix these two problems? I have tried both installing my drivers with EnvyNG and with the instructions followed manually in the link above. For many this might work, but for me it's still the same whatever I seem to do. 

Best Regards,
Gunnar

---

