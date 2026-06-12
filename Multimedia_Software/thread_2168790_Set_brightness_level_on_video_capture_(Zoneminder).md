---
title: "Set brightness level on video capture (Zoneminder)"
date: 2013-08-19
forum: Multimedia Software
---

### Post by Richard_Gosling on 2013-08-19
Hi,

I have a couple of black & white cameras connected to a four channel video capture card which has the Techwell (TW68) chipset.

I'm using this in a Zoneminder CCTV setup.

The problem is that the images captured are so bright that they are almost all white with a very pale image visible.

I've checked in the Zoneminder options but I can't find anything for adjusting the brightness/contrast of the cameras.

I've seen some posts saying that video properties such as brightness can be set by using "zmu", but there are no examples on how to set these values, only how to query the existing settings. - [http://www.zoneminder.com/wiki/index.php/Zmu](http://www.zoneminder.com/wiki/index.php/Zmu)

Does anyone know how to adjust the brightness and contrast for each camera?

Thanks.

---

### Post by Richard_Gosling on 2013-08-20
I've managed to work out the syntax for ZMU and that seems to have an effect on the cameras, so it looks like that's the way to go rather than trying to adjust the tw68 settings.

I worked out that I need to specify the Monitor ID (-m 2) rather than the Device when checking or setting specific parameters.

So this tells me the current brightness setting (-B);

```
sudo zmu -m 2 -B -v
```
Which gave me a result of 220.

I changed the value using this;

```
sudo zmu -m 2 -B=120 -v
```

But it told me that the new brightness level was now 0 instead of 120 as expected.

I experimented with various number values and formats including hex values, but whatever I try to set it to comes out as "0".

Has anyone ever successfully set any values with ZMU, do you know the number format required?

Thanks.

---

