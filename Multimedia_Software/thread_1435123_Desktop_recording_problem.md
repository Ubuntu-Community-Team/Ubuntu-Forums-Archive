---
title: "Desktop recording problem"
date: 2010-03-21
forum: Multimedia Software
---

### Post by alex4c on 2010-03-21
I wanna record painting in Gimp. For that purpose I downloaded XVidCap Screen Capture. I started recording but it was useless, everything was so slow. I look for other software and found recordmydesktop, but my brush falls behind again. 
I tried to build _**[COLOR=Indigo]*[vncrec]("http://www.sodan.org/%7Epenny/vncrec/")*[/COLOR]**_ but an error occur when i execute this line:[FONT=monospace] 
[/FONT]```
% cd ../vncrec; make 
```I'm new to Ubuntu (and Linux, expecially command lines) so sometimes I misinterpret simple things. 
I tried again XVidCap and played a bit with its preferences and now it does some silly things; like when I start recording it disappears and there isn't any tray icon (non that I see). When I star it again I can "unpress" stop button and there is video file in video folder like he did recording but when I click to play it this comes up: Could not demultiplex stream.

My system:
MB: MSI K9N6PGM2-V
CPU: AMD X2 Athlon II 215, 2MB  64Bit  2.7GHz 
Memory: 4GB 800MHz  Dual Channel
Graphic Card: VGA ATI Radeon 4650 1GB

---

### Post by linuxford on 2012-02-25
Try using the GUI Ubuntu Software Center and install the tool called recordMyDesktop. 

This should create a .ogv which can then be converted. I haven't done it, but you should also be able to find a tool in the USC (ubuntu software center) to do the conversion.

[http://my.opera.com/ubuntunerd1/blog/2009/06/17/how-to-convert-ogv-files-to-other-formats-with-winff]("http://my.opera.com/ubuntunerd1/blog/2009/06/17/how-to-convert-ogv-files-to-other-formats-with-winff")

---

### Post by josephmills on 2012-02-25
there is also kazam which I like a-lot 
[https://launchpad.net/kazam](https://launchpad.net/kazam)

---

### Post by linuxford on 2012-02-25
By the way, I had trouble using WinFF to translate ogv. I did a testrun on using my suggestion above, but then had to use 'mencoder' for the translation of .ogv to .avi and it was translated better. You will need to mess around with different options probably to get better pictures. So to use the mencoder, see this following thread:

[http://ubuntuforums.org/showthread.php?t=1925886&highlight=convert+ogv+avi]("http://ubuntuforums.org/showthread.php?t=1925886&highlight=convert+ogv+avi")

Kazam looks cool as previous poster suggested, but I'm still on Lucid. I may upgrade to Unity but still for now like the older menu system.

---

