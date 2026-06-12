---
title: "GTS 250 256bit card/12.10/42&quot; LED/4:3 problem/NOOB w/ TERMINAL OPEN"
date: 2013-05-30
forum: Multimedia Software
---

### Post by need4lightspeed on 2013-05-30
GTS 250 256bit card/12.10/42" LED/4:3 problem/NOOB w/ TERMINAL OPEN

I have no idea how to begin but I have 12.10 ,[U] make sure u realize 12.10 is different than 12.04/

NO Xconf in 12.10[/U]

I have terminal experience so go ahead and instruct me on how to adjust resolution settings in 12.10 for the Nvidia 302 or 310(?driver) in additional drivers.

My installation doesn't let me edit below my admin account user unless it in terminal with sudo
...what config file has the resolution settings
...I will make a backup and go from there if you can provide that much...

[U]It was allowed 1600 x ? on my DVI 20" set up...but I now switched to my 42" LED tv with VGA cause I lost my HDMI cord...(if u think I should just go buy the HDMI cord say so) SO the 42"LED is not recongnzed well by 12.10 and say 1200 x 768? max...that s the problem for now
[/U]
[COLOR=#3E3E3E]GTS 250 256bit card/12.10/42" LED/4:3 problem/NOOB w/ TERMINAL OPEN[/COLOR]

Also I have SiS 671  board and no audio at all...please give me some place to start on that if u can...thanks a ton.

(I looked for posts with the answer but 12.10 is not same as 12.04 and prior so it was difficult to locate anything helpful)

---

### Post by papibe on 2013-05-30
Hi need4lightspeed. Welcome to the forum ):P

Could you post the output of these commands?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -E '(nvidia|nou)'

xrandr

xvidtune -show
```
Regards.

---

### Post by need4lightspeed on 2013-05-30
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [GeForce GTS 250] [10de:0615] (rev a2)
	Subsystem: eVga.com. Corp. Device [3842:1145]
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

nouveau               896008  3 
ttm                    83596  1 nouveau
drm_kms_helper         49113  1 nouveau
drm                   288721  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13414  1 nouveau
mxm_wmi                13022  1 nouveau
video                  19391  1 nouveau
wmi                    19071  2 nouveau,mxm_wmi



Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI-1 disconnected (normal left inverted right x axis y axis)

"1024x768"     65.00   1024 1048 1184 1344    768  771  777  806 -hsync -vsync

---

### Post by papibe on 2013-05-30
Thanks.

You are using the Nvidia open source driver (nouveau). There may be better chances of using more resolutions if you install the Nvidia proprietary driver. Do you know how to do it?

As far as nouveau's probing, the TV's VGA input supports up to 1024x768, which is a little low but not unusual. Not all resolution, specially HD ones, are available on all TV inputs.

Let us know if you need help with the driver.
Regards.

---

### Post by need4lightspeed on 2013-05-30
I went to additional drivers and tried tested one 302 and the experimental one 310...but i guess it didn't save or something and just says 310 when its not maybe?...not sure but makes sense that the res options never changed even tho its said it was 310..still says 310 btw...so what it mean?

---

### Post by papibe on 2013-05-30
Since you are on 12.10 you may need to install this first:
```
sudo apt-get install linux-headers-generic
```
Then try to install the driver again.

Let us know how it goes.
Regards.

---

### Post by need4lightspeed on 2013-05-30
Well, you are getting a BIG thanks from me here...it gave me 1360 x 768 for now and its all I needed. This will probably be the one of best options for any one with a GTS card and going to LED TV's like this. Thanks again.

---

### Post by need4lightspeed on 2013-05-30
Do u know what I would need to do to get a bit better res on this driver or should I try all the addd drivers avail and report back what I get.???

---

### Post by need4lightspeed on 2013-05-30
So, i tried the 304(no 302) 310 and neavou(?) but max is 1360 x 768...fyi

---

### Post by papibe on 2013-05-30
Now you can run 'Nvidia X Server Settings' to configure your resolution and other monitor settings.

Nevertheless, I don't think trying the other versions would allow more resolutions.

My first guess would be to use another TV input, like a DVI, or HDMI input.

Regards.

---

### Post by need4lightspeed on 2013-05-30
sudo nvidia settings ...is that the only way to access the nvidia gui thingy?

---

### Post by papibe on 2013-05-30
You should be able to run it from the dashboard by searching 'nvidia'.

In the case you want to save your settings on the system X configuration file (/etc/X11/xorg.conf), I would recommend using gksudo instead of sudo:
```
gksudo nvidia-settings
```
Regards.

---

### Post by need4lightspeed on 2013-06-24
hi readers...I am back with same set up but I need a couple answers...I think I want to(#1) know how to detect and remove all non install audio settings...trying to get back to default..or (#2) I need to configure nvidia HDMI audio...reminder ;its SiS intel chipset...but it did have VLC able to play audio but now I am trying to use my TV for speakers and Im stuck..with HDMI audio not out putting any sound.

---

