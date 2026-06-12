---
title: "Fglrx doesn't detect monitor"
date: 2010-09-14
forum: Multimedia Software
---

### Post by powerslavez on 2010-09-14
Hi, 

I'm running 10.04 on a Radeon HD 4650 card with fglrx. The driver installation went without a hitch, and the log file contained no errors. 

When I try to run 

```
aticonfig --initial
```i get the response 

```
Found fglrx primary device section
 Unable to find any supported Screen sections

```
Running 

```
fglrxinfo
```I get 


```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  20
  Current serial number in output stream:  20

```

When I boot up my computer, all I see is a black screen until the Xorg server starts. I think this is because fglrx won't detect my monitor. 

My best guess is that I have to write an Xorg.conf file, in which I say what type of monitor I have. 

I cannot do that, as I need to shut down the Xserver in order to make it generate my xorg.conf file. When I shut it down I get the black screen. 


Does anyone happen to know a way around this? 


Thanks in advance, 
Vlad

---

### Post by powerslavez on 2010-09-14
By running

```
sudo amdcccle
```I was able to access the Catalyst Control Center, which recognized my Acer H223HQ monitor. 

I was then able to run 

```
sudo aticonfig --initial
```which produced the following xorg.conf file:

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Running 


```
fglrxinfo
```
still produces 


```
 X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  20
  Current serial number in output stream:  20

```
and I still am unable to see anything other than points on the top side of the monitor during booting. The only way of "talking" to my computer is when I have the X server up and running. 


Any ideas on how to solve this? 


Thanks in advance, 
Vlad

---

### Post by azwar on 2010-09-14
how do you install the fglrx. Is it by using jockey-gtk/default repo or bleeding edge here  [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").

try run ```
sudo aticonfig --initial -f
```then restart xserver

---

### Post by powerslavez on 2010-09-14
Hi, 

Thanks for your help. Both the jokey and the bleeding edge versions lead to the same results I mentioned above. The bleeding edge version does seem to work a bit faster, but desktop effects don't run on it. 

I've also tried using the xorg.conf file produced by the better-working bleeding edge version on the jockey driver, but to no avail. 

Forcing the initial configuration sadly doesn't help either. 

So my main problems are:


> Inability to drop the a simple CLI without the X server started
> Choppy video performance on files of all kinds stored on my hard drive - streaming flash video works wonderfully, oddly enough.

---

