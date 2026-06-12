---
title: "Webcam and video4linux"
date: 2009-03-10
forum: Multimedia Software
---

### Post by rouge568 on 2009-03-10
Hello. I am running kubuntu, and have just discovered the wonderful kdenlive, which is definitely the best video editor for linux I have found so far. Anyways, it has the ability to import footage directly from a webcam, which is prefect for my need. Except it doesn't work. It sees the camera, but when I try to get a stream, it says that it isn't connected. The interesting thing is that Cheese can use the webcam perfectly, and I get nice video from that. So I know that this camera works. 
Further digging brings up some more information. Kdenlive uses the video4linux drivers, which seems to be the root cause in this problem. A kernel changelog I found online said that my camera was supported by video4linux, so I know that support is not the issue. I also know that neither the camera nor the connection are the issue, because Cheese works fine. Any help in figuring this out is much appreciated.

If it helps, here is the output for v4l-info
```
$ v4l-info                                                 
                                                                                
### v4l2 device info [/dev/video0] ###                                          
general info                                                                    
    VIDIOC_QUERYCAP                                                             
        driver                  : "sunplus"                                     
        card                    : "Sunplus SPCA533        "                     
        bus_info                : "0000:00:1d.1"                                
        version                 : 2.2.0                                         
        capabilities    $ v4l-info                                                 
                                                                                
### v4l2 device info [/dev/video0] ###                                          
general info                                                                    
    VIDIOC_QUERYCAP                                                             
        driver                  : "sunplus"                                     
        card                    : "Sunplus SPCA533        "                     
        bus_info                : "0000:00:1d.1"                                
        version                 : 2.2.0                                         
        capabilities            : 0x5000001 
[VIDEO_CAPTURE,READWRITE,STREAMING] 
                                                                                
standards                                                                       
                                                                                
inputs                                                                          
    VIDIOC_ENUMINPUT(0)                                                         
        index                   : 0                                             
        name                    : "sunplus"                                     
        type                    : CAMERA                                        
        audioset                : 0                                             
        tuner                   : 0                                             
        std                     : 0x0 []                                        
        status                  : 0x0 []                                        
                                                                                
video capture                                                                   
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)                                            
        index                   : 0                                             
        type                    : VIDEO_CAPTURE                                 
        flags                   : 1                                             
        description             : "JPEG"                                        
        pixelformat             : 0x4745504a [JPEG]                             
    VIDIOC_G_FMT(VIDEO_CAPTURE)                                                 
        type                    : VIDEO_CAPTURE                                 
        fmt.pix.width           : 320                                           
        fmt.pix.height          : 240                                           
        fmt.pix.pixelformat     : 0x4745504a [JPEG]                             
        fmt.pix.field           : NONE                                          
        fmt.pix.bytesperline    : 320                                           
        fmt.pix.sizeimage       : 29390                                         
        fmt.pix.colorspace      : JPEG                                          
        fmt.pix.priv            : 2                                             
                                                                                
controls                                                                        
    VIDIOC_QUERYCTRL(BASE+0)                                                    
        id                      : 9963776                                       
        type                    : INTEGER                                       
        name                    : "Brightness"                                  
        minimum                 : 0                                             
        maximum                 : 255                                           
        step                    : 1                                             
        default_value           : 0                                             
        flags                   : 0                                             
    VIDIOC_QUERYCTRL(BASE+1)                                                    
        id                      : 9963777                                       
        type                    : INTEGER                                       
        name                    : "Contrast"                                    
        minimum                 : 0                                             
        maximum                 : 255                                           
        step                    : 1                                             
        default_value           : 32                                            
        flags                   : 0                                             
    VIDIOC_QUERYCTRL(BASE+2)                                                    
        id                      : 9963778                                       
        type                    : INTEGER                                       
        name                    : "Color"                                       
        minimum                 : 0                                             
        maximum                 : 255                                           
        step                    : 1                                             
        default_value           : 26                                            
        flags                   : 0                                             
                                                                                
### video4linux device info [/dev/video0] ###                                   
general info                                                                    
    VIDIOCGCAP                                                                  
        name                    : "Sunplus SPCA533        "                     
        type                    : 0x1 [CAPTURE]                                 
        channels                : 1                                             
        audios                  : 0                                             
        maxwidth                : 464                                           
        maxheight               : 480                                           
        minwidth                : 48                                            
        minheight               : 32                                            
                                                                                
channels                                                                        
    VIDIOCGCHAN(0)                                                              
        channel                 : 0                                             
        name                    : "sunplus"
        tuners                  : 0
        flags                   : 0x0 []
        type                    : CAMERA
        norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
        brightness              : 32896
        hue                     : 0
        colour                  : 4112
        contrast                : 8224
        whiteness               : 0
        depth                   : 8
        palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 320
        height                  : 240
        chromakey               : 0
        flags                   : 0

        : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING] 
                                                                                
standards                                                                       
                                                                                
inputs                                                                          
    VIDIOC_ENUMINPUT(0)                                                         
        index                   : 0                                             
        name                    : "sunplus"                                     
        type                    : CAMERA                                        
        audioset                : 0                                             
        tuner                   : 0                                             
        std                     : 0x0 []                                        
        status                  : 0x0 []                                        
                                                                                
video capture                                                                   
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)                                            
        index                   : 0                                             
        type                    : VIDEO_CAPTURE                                 
        flags                   : 1                                             
        description             : "JPEG"                                        
        pixelformat             : 0x4745504a [JPEG]                             
    VIDIOC_G_FMT(VIDEO_CAPTURE)                                                 
        type                    : VIDEO_CAPTURE                                 
        fmt.pix.width           : 320                                           
        fmt.pix.height          : 240                                           
        fmt.pix.pixelformat     : 0x4745504a [JPEG]                             
        fmt.pix.field           : NONE                                          
        fmt.pix.bytesperline    : 320                                           
        fmt.pix.sizeimage       : 29390                                         
        fmt.pix.colorspace      : JPEG                                          
        fmt.pix.priv            : 2                                             
                                                                                
controls                                                                        
    VIDIOC_QUERYCTRL(BASE+0)                                                    
        id                      : 9963776                                       
        type                    : INTEGER                                       
        name                    : "Brightness"                                  
        minimum                 : 0                                             
        maximum                 : 255                                           
        step                    : 1                                             
        default_value           : 0                                             
        flags                   : 0                                             
    VIDIOC_QUERYCTRL(BASE+1)                                                    
        id                      : 9963777                                       
        type                    : INTEGER                                       
        name                    : "Contrast"                                    
        minimum                 : 0                                             
        maximum                 : 255                                           
        step                    : 1                                             
        default_value           : 32                                            
        flags                   : 0                                             
    VIDIOC_QUERYCTRL(BASE+2)                                                    
        id                      : 9963778                                       
        type                    : INTEGER                                       
        name                    : "Color"                                       
        minimum                 : 0                                             
        maximum                 : 255                                           
        step                    : 1                                             
        default_value           : 26                                            
        flags                   : 0                                             
                                                                                
### video4linux device info [/dev/video0] ###                                   
general info                                                                    
    VIDIOCGCAP                                                                  
        name                    : "Sunplus SPCA533        "                     
        type                    : 0x1 [CAPTURE]                                 
        channels                : 1                                             
        audios                  : 0                                             
        maxwidth                : 464                                           
        maxheight               : 480                                           
        minwidth                : 48                                            
        minheight               : 32                                            
                                                                                
channels                                                                        
    VIDIOCGCHAN(0)                                                              
        channel                 : 0                                             
        name                    : "sunplus"
        tuners                  : 0
        flags                   : 0x0 []
        type                    : CAMERA
        norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
        brightness              : 32896
        hue                     : 0
        colour                  : 4112
        contrast                : 8224
        whiteness               : 0
        depth                   : 8
        palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 320
        height                  : 240
        chromakey               : 0
        flags                   : 0


```
And the output for camorama -D , which uses video4linux
```
$ camorama -D   

VIDIOCGCAP
device name = Sunplus SPCA533        
device type = 1                      
can use mmap()                       
# of channels = 1                    
# of audio devices = 0               
max width = 464                      
max height = 480                     
min width = 48                       
min height = 32                      

VIDIOCGWIN
x = 0     
y = 0     
width = 464
height = 480
chromakey = 0
flags = 0    

VIDIOCGWIN
x = 0     
y = 0     
width = 320
height = 240
chromakey = 0
flags = 0    

VIDIOCGPICT:
bright = 32896
hue = 0       
colour = 4112 
contrast = 8224                                                                 
whiteness = 0                                                                   
colour depth = 8                                                                
                                                                                
VIDIOCGMBUF                                                                     
mb.size = 344064                                                                
mb.frames = 4                                                                   
mb.offset = 86016                                                               
/home/scott/.gtkrc-2.0:1: Unable to find include file: ".gtkrc-2.0-gnome-color-chooser"                                                                         
                                                                                
(camorama:6588): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated                                                     
update_tooltip called                                                           
tip - acap off                                                                  
** Message: SET PIC                                                             
** Message: SET PIC                                                             
** Message: SET PIC                                                             
update_tooltip called                                                           
tip - acap off                                                                  
Unable to capture image (VIDIOCSYNC)                                            

```
I can supply any more information that might be needed.

---

### Post by rouge568 on 2009-03-18
bump.

---

### Post by maiatoday on 2009-03-19
I had a similar problem here is a solution in noted in the OpenCV bug tracking system.
[http://sourceforge.net/tracker/index.php?func=detail&aid=2653321&group_id=22870&atid=376677](http://sourceforge.net/tracker/index.php?func=detail&aid=2653321&group_id=22870&atid=376677)

Also you can see the bug in launchpad and suggestions and which apps have been fixed.
[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

basically you need to have the use start kdenlive like this

LD_PRELOAD="/usr/lib/libv4l/v4l2convert.so" kdenlive

---

### Post by rouge568 on 2009-03-20
Thank you! This fixes the issue for me. I posted a bug on the kdenlive bug tracker and linked it back to the launchpad bug you supplied. Hopefully we can see this fix in 0.7.3/0.7.4.

[http://www.kdenlive.org/mantis/view.php?id=726](http://www.kdenlive.org/mantis/view.php?id=726)
[https://bugs.launchpad.net/ubuntu/+s...4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+s...4l/+bug/260918)

---

