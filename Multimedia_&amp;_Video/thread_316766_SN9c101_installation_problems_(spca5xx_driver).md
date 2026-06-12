---
title: "SN9c101 installation problems (spca5xx driver)"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by luizfernando on 2006-12-11
Hello,

I've installed my microdia webcam (0x0c45,0x6007, SOnix based - sn9c101) using the spca5xx drivers ([http://mxhaard.free.fr/)](http://mxhaard.free.fr/)). Everything goes ok, the cam is now installed, but strange things occurs when I start an application (like camorama, camstream, spcaview, amsn): the cam image is so strange, with saturated colours, like this screenshot: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=20890&stc=1&d=1165851312[/IMG]

Althought there is no error message, I can't fix this! Not only the colors are wrong, but the image quality too. ](*,) 


Thanks

Luiz Fernando

---

### Post by loicfreville on 2007-02-18
Hi,

Did you find a solution to this problem ? I have exactly the same problem and I can't find an answer to this.

Thanks

---

### Post by ostry on 2007-02-21
Hello,

has somebody solved problem with picture colors and quality? I successfully installed webcams 0c45:6025 Microdia (Mercury CC-320) and 0c45:6007 Microdia (Genius VideoCAM Eye v2.0 made in China) with drivers downloaded from [http://mxhaard.free.fr/](http://mxhaard.free.fr/) according to [http://www.ubuntuforums.org/showthread.php?t=75284](http://www.ubuntuforums.org/showthread.php?t=75284), but with the second I have the same poor picture quality results as the other trialists.

I also found these lines in dmesg output after plugging webcam:
[17205135.624000] usb 1-6: new full speed USB device using ohci_hcd and address 17
[17205135.836000] usb 1-6: configuration #1 chosen from 1 choice
[17205135.840000] /home/ostry/Desktop/webcam_driver_install/gspcav1-20070110/gspca_core.c: USB SPCA5XX camera found. SONIX sn9c10[1 2]
[17205135.840000] /home/ostry/Desktop/webcam_driver_install/gspcav1-20070110/gspca_core.c: [spca5xx_probe:3983] Camera type SN9C 
[17205135.840000] /home/ostry/Desktop/webcam_driver_install/gspcav1-20070110/gspca_core.c: [spca5xx_getcapability:1189] maxw 352 maxh 288 minw 160 minh 120

and after starting camorama:
[17206506.160000] /home/ostry/Desktop/webcam_driver_install/gspcav1-20070110/gspca_core.c: [spca5xx_set_light_freq:1858] Sensor currently not support light frequency banding filters.
[17206506.160000] /home/ostry/Desktop/webcam_driver_install/gspcav1-20070110/gspca_core.c: [gspca_set_isoc_ep:881] ISO EndPoint found 0x81 AlternateSet 8
and these 2 lines appeared repeatedly when testing with Ekiga Softphone.

Look attached screenshots from Camorama and Ekiga.

Hope is still alive: [http://www.linux-projects.org/modules/newbb/viewtopic.php?viewmode=thread&topic_id=231&forum=3&post_id=944#944](http://www.linux-projects.org/modules/newbb/viewtopic.php?viewmode=thread&topic_id=231&forum=3&post_id=944#944)

Thanks in advance.

ostry

---

### Post by mongolito404 on 2007-04-20
Same here with a freshly installed Feisty.

---

### Post by gpo on 2007-05-03
I have the same problem here, running a Genius VideoCAM Eye V2 on feisty. No additional drivers installed...

Strangely, caminfo (comes with the camstream package) gives me
```
gp@gp-thinkpad:~$ caminfo 
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   :[COLOR="Red"] "Sweex SIF webcam"[/COLOR]
Minimum size     : 160x120
Current size     : 0x0
Maximum size     : 352x288
Video inputs     : 1
 Input 0
  Name             :[COLOR="Red"] "SN9C102"[/COLOR]
  Type             : Camera
  Audio            : no
  Tuners           : 0
Audio inputs     : 0
```
Shouldn't that be "SN9C101"? Any help would be greatly appreciated...

Although I already start liking the fx on my cam :biggrin:

---

### Post by maroini on 2007-05-13
anyone figured this one out yet?

---

### Post by uptimebox on 2007-05-21
Same problem here. No additional drivers used, just Feisty install.

---

### Post by luizfernando on 2007-08-23
more than 8 months and my cam continues to show me as yellow as an emoticon =(

---

### Post by hoomanb on 2007-09-24
I'm still yellow too! I bought another camera but it can't replace this tiny Genius cam so I'm still desperate for a fix.

---

### Post by daniel.ibrahim.germer on 2007-10-07
Hi folx,
there is always the possibility to get the latest gspca and compile it:

search for your camera Model (usb- Webcam):
type into a terminal:
 ```
lsusb
```
check which is your usb Camera

In My case it was: 
```
Bus 002 Device 004: ID 0c45:613c Microdia
```


visit [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
find your camera Model

get the driver:
in a terminal type:
 ```
wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz

```
type:
 ```
tar -xvcf gspcav1-20070508.tar.gz
```

type:
 ```
cd gspcav1-20070508/
 make
 sudo make install
```

Now it should be compiled (oh, in case of error, did you install linux-headers?)
next step you would have to go and insert the module gspca into your kernel at boot time
first try it out:
```
modprobe -r gspca
modprobe gspca
```

Now you hopefully get a slightly improved image. it isn't perfect yet in my case...
have a look...

---

### Post by luizfernando on 2007-10-07
thank you man, but you can see that for my cam (0x0c45,0x6007, Sonix based - sn9c101) there isn't a driver. We still without solutions =(

I've already tried many ways of installation (your suggestion is the "standard way"), but I think Mr. Haard actually doesn't have this driver.

Ubuntu install this "bad" driver by default, too =)

---

### Post by Meos on 2007-11-13
Isn't driver?
So, what is this?
Sweex 	153 	**0x0c45 	0x6005** 	350 Mp 	  	**sn9c101 **	Tas5110 	**Yes** 	gbgr 	spca5xx
But  0x6005... may b&#1091; this is another product....

---

### Post by luizfernando on 2007-11-17
Yes, no driver available yet. This is **0x6005**, which is different from **0x6007** :)

---

### Post by Meos on 2007-12-06
After adding sn9c102 to /etc/modprobe.d/blacklist
this driver successfully loaded and "working"... But... i'm yellow again... Same as with built-in driver...
I'm became to want to grab this camera and get it to the scrap...
*sorry for my horrible english

---

