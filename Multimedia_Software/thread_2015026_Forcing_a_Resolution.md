---
title: "Forcing a Resolution"
date: 2012-07-02
forum: Multimedia Software
---

### Post by am0nrahx on 2012-07-02
Running Ubuntu 12.04 on an Acer Aspire x1200. Video chipset is an onboard  NVIDIA GeForce 9200. I've looked everywhere on the web to figure out how to force it to run at 1366x768, which is the native for the Emerson LCD it's hooked up to. It doesn't detect it on it's own.

It's dual booted with Windows 7 and it detects the correct resolution in Windows, so the GPU is capable of the resolution.

I know it can be done, because I did it before, but for the life of me, I can't remember or figure out how.

Any help is appreciated!

---

### Post by sudodus on 2012-07-02
Try with ```
xrandr
``` and post the output of that command

---

### Post by am0nrahx on 2012-07-02
This is what I got.
> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720       50.0     51.0* 
   960x600        52.0  
   960x540        53.0  
   840x525        54.0     55.0     56.0  
   832x624        57.0  
   800x600        58.0     59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x480        66.0     67.0  
   720x450        68.0  
   720x400        69.0  
   700x525        70.0     71.0     72.0     73.0  
   680x384        74.0     75.0  
   640x512        76.0     77.0     78.0  
   640x480        79.0     80.0     81.0     82.0     83.0     84.0     85.0  
   640x400        86.0  
   640x350        87.0  
   576x432        88.0     89.0     90.0     91.0     92.0     93.0     94.0  
   512x384        95.0     96.0     97.0     98.0     99.0  
   416x312       100.0  
   400x300       101.0    102.0    103.0    104.0    105.0  
   360x200       106.0  
   320x240       107.0    108.0    109.0    110.0  
   320x200       111.0  
   320x175       112.0  



---

### Post by sudodus on 2012-07-02
> Screen 0: minimum 320 x 175, current 1280 x 720, maximum 1280 x 720
is close to 1366x768, but not quite there. What graphics driver are you using?
- nouveau (the default built in driver), or
- a built-in proprietary driver (via ***jockey-gtk***) or
- a proprietary driver downloaded from nvidia's web page?

You might need to test more than one of those from nvidia's web page.

---

### Post by am0nrahx on 2012-07-03
Well, here's the deal. I updated to the linux drivers from the nvidia site and now it won't boot.

Not really that familiar with Ubuntu in console mode, how do I revert back so I can get it to boot? Otherwise, I'm just going to reinstall and start over lol.

---

### Post by am0nrahx on 2012-07-04
Ok, so I just went ahead and reinstalled Ubuntu 12.04. I had it dual  booted with Windows, and I didn't really see the point as it's just a  media rig and it doesn't need BluRay/HDCP support. So we can safely say  it's running the default built-in driver at this point.

---

