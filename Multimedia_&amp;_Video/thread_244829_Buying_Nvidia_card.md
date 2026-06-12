---
title: "Buying Nvidia card"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by bluntu on 2006-08-27
I recently bought ATI Radeon X1300 and upon installing Ubuntu it run fine but I don't think 3d acceleration is on because I did '$ glxgears' and got something like:

628 frames in 5.0 seconds = 125.467 FPS

and after doing: fglrxinfo I got:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

I have read tutorials/howtos but the instructions are very confusing and that is where the frustration comes so I decided to drop ATI And go with NVIDIA. My question is: Do I need to follow a lot of instructions just to get NVIDIA working? Do I have to download this and that and do this and that? Does NVIDIA comes with tool to control my LCD's brightness/contrast/gamma?

Having never used Nvidia before what do you recommened for someone who doesn't play 3d game, just a lot of web surfing/watching videos and using Blender (I need blender to run as fast and smooth as it can and it's 3d related). 

Thanks for your time.

---

### Post by Schalken on 2006-08-27
125.467 FPS??? Sounds like you have 3D acceleration to me.

---

### Post by Perfect Storm on 2006-08-27
> I have read tutorials/howtos but the instructions are very confusing and that is where the frustration comes so I decided to drop ATI And go with NVIDIA. My question is: Do I need to follow a lot of instructions just to get NVIDIA working?
It's easy
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```
then restart X and you are rolling :cool: 

> I have to download this and that and do this and that? Does NVIDIA comes with tool to control my LCD's brightness/contrast/gamma?
sure.
[IMG]http://www.imageviper.com/displayimage/52516/0/Screenshot-NVIDIA_X_Server_Settings.jpg[/IMG]

> Having never used Nvidia before what do you recommened for someone who doesn't play 3d game, just a lot of web surfing/watching videos and using Blender (I need blender to run as fast and smooth as it can and it's 3d related).
What does your motherboard support? agpx2, agpx4, agpx8, pci-express?
I use (and can recommend) geforce 6600 GT 256 mb. You can get them quiet cheap and they are powerful.



> 125.467 FPS??? Sounds like you have 3D acceleration to me.
Well....very very very low score. I know it isn't a benchmark, but it is still too low.
I get over 6000 on mine.

---

### Post by Schalken on 2006-08-27
Don't we just love nVidia's Linux support?

> I use (and can recommend) geforce 6600 GT 256 mb. You can get them quiet cheap and they are powerful.

I have a 6200 256mb and it runs Blender quite well. I don't think you need any more than that unless you want to play something like F.E.A.R.

> Well....very very very low score. I know it isn't a benchmark, but it is still too low.
I get over 6000 on mine.

Hey, you're right! I get around 1290. My bad. It's just that before I got my card I was getting a decimal FPS!

---

### Post by bluntu on 2006-08-27
It was a mistake for me to bought ATI X1300 since the 6600 GT's price is almost the same as ATI. BY the way, do you have a direct link to that 6600GT cause I did a search on google and it came up a lot and I don't know which one it is.

My motherboard is Nvidia and it supports AGP (I *think* x2) thinking about it now it's kind of strange for me to run ATI card on Nvidia board. I think I'll go with 6600GT since I don't play 3d game but I do want to work with as much polycount as I can with Blender.

---

### Post by Perfect Storm on 2006-08-27
[Performance](http://www.nvidia.com/page/geforce_6600.html) note that you'll properly won't get the exact performance as your motherboard only support x2
Well my motherboard can only handle x4 though the graphic card x8.
There's a pci-express and x8. You have to choose x8.
Go for the 256 mb. I'm not sure you can get them 128mb but I think it's possible.

---

### Post by bluntu on 2006-08-27
It turns out that my nvidia is agp x8.

Which one is better: PCI or AGP?

Having looked at the chart on the site you posted I notice that the AGP list is weaker than the PCI list. Does that means PCI is faster/better than AGP?

---

### Post by Perfect Storm on 2006-08-27
You can only use Pci-express if your motherboard support it (newer motherboards). Otherwise you'll end up with a card you can't use.

---

