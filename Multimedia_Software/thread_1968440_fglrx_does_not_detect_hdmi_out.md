---
title: "fglrx does not detect hdmi out"
date: 2012-04-29
forum: Multimedia Software
---

### Post by DavidSommen on 2012-04-29
I have a ATI RS780D [Radeon HD 3300] onboard video card on my motherboard (MSI 790Gx-G65). I have a VGA display monitor and a TV connected via HDMI. When I use the opensource driver, the TV is detected perfectly. The problem with this driver is that it doesn't handle video well (videos tear or play choppily). So I want to try it with FGLRX, which should be a better specific driver for my card. However, it doesn't detect my TV at all. Instead, in 'Displays' it shows a second screen called 'Laptop', which doesn't work if I enable it.

My output from xrandr with the **opensource** driver is:
```

sommen@sommen:~$ xrandr
Screen 0: minimum 320 x 200, current 2646 x 1024, maximum 8192 x 8192
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     72.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
   640x350        70.1  
HDMI-0 connected 1366x768+1280+179 (normal left inverted right x axis y axis) 640mm x 360mm
   1920x1080      50.0 +   24.0  
   1920x1080i     25.0  
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0

```
And the same with **fglrx**:
```


sommen@sommen:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1920 x 1920
DFP1 connected (normal left inverted right x axis y axis)
   1920x1080      50.0 +   60.0     30.0     25.0     24.0  
   1776x1000      60.0 +   50.0 +   25.0     24.0  
   1680x1050      50.0 +   60.0     24.0  
   1400x1050      50.0 +   60.0     24.0  
   1280x1024      50.0 +   60.0     24.0  
   1440x900       50.0 +   59.9     24.0  
   1280x960       50.0 +   60.0     24.0  
   1280x800       50.0 +   60.0     24.0  
   1152x864       50.0 +   60.0     24.0  
   1280x768       50.0 +   59.9     24.0  
   1024x768       50.0 +   60.0     24.0  
   1152x648       60.0 +   50.0  
   1280x720       60.0     50.0     24.0  
   800x600        60.3     50.0     24.0  
   720x576        50.0     25.0  
   720x480        60.0     50.0     30.0     24.0  
   640x480        60.0     50.0     24.0  
CRT1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x800       60.0 +   75.0  
   1280x720       60.0 +
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3  
   720x480        60.0  
   640x480        75.0     72.8     60.0  

```
As you see, with the fglrx driver, it detects a with dfp and crt, which isn't correct, and it doesn't detect the VGA or HDMI (My VGA monitor works fine however).

In Windows, this does work with the catalyst driver.

Any ideas? Thanks.

---

### Post by DavidSommen on 2012-04-29
In amdcccle, I managed to enable the TV.

However, video tearing (edit: only on my TV) is even worse than with the opensource driver. Compiz is also laggy and slow. I don't understand how this is possible?...

---

