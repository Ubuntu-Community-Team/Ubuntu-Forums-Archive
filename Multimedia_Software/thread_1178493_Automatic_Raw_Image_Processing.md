---
title: "Automatic Raw Image Processing"
date: 2009-06-04
forum: Multimedia Software
---

### Post by theSeeker88 on 2009-06-04
As an amateur photographer, I'm intrigued by the idea of shooting in Raw. However, I often shoot between one and two hundred pictures every day, and I don't like the idea of doing all that manipulation by hand. 

What I'd like is a tool which could perform the exact same conversion (raw -> JPEG) which is normally performed on my camera, but on my computer. I'd like it to do this in batch, with essentially no input from me. I understand this defeats the purpose of shooting in raw, but the idea is I'd keep the raw files so that I could edit certain ones later - i.e. have my cake and eat it too. 

I've tried RawStudio and Raw Therapee - both seem oriented towards manipulation by hand, and even the batch tools require you to specify certain settings. Does anyone know of a tool which would simply use the camera's settings and perform the conversion in the same exact manner?

Thanks!

---

### Post by xzero1 on 2009-06-05
You might check into imagemagick. See this link: [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

### Post by megamania on 2009-06-10
> **theSeeker88 said:**
> I often shoot between one and two hundred pictures every day, and I don't like the idea of doing all that manipulation by hand. 
[...]
What I'd like is a tool which could perform the exact same conversion (raw -> JPEG) which is normally performed on my camera, but on my computer.

Probably a silly question, but doesn't your camera support shooting raw+jpg? That way you'd have both files instantly.

Since you shoot 200 pictures a day, I'd consider switching to a camera that supports that option in case yours doesn't.

---

### Post by reeseslover531 on 2009-06-10
check [this ]("http://ubuntuforums.org/showthread.php?t=1016950")out

---

### Post by FrankVdb on 2009-07-16
What do you need RAW for? Why not use the highest JPG quality available on your camera? The only advantage of RAW is that it allows you to edit in 16-bit mode before going back to an 8-bit JPG picture. Apparently you just want to batch convert without adjusting your picture. That means that you should be shooting JPG instead of RAW.

---

### Post by mcduck on 2009-07-16
> **theSeeker88 said:**
> As an amateur photographer, I'm intrigued by the idea of shooting in Raw. However, I often shoot between one and two hundred pictures every day, and I don't like the idea of doing all that manipulation by hand. 

What I'd like is a tool which could perform the exact same conversion (raw -> JPEG) which is normally performed on my camera, but on my computer. I'd like it to do this in batch, with essentially no input from me. I understand this defeats the purpose of shooting in raw, but the idea is I'd keep the raw files so that I could edit certain ones later - i.e. have my cake and eat it too. 

I've tried RawStudio and Raw Therapee - both seem oriented towards manipulation by hand, and even the batch tools require you to specify certain settings. Does anyone know of a tool which would simply use the camera's settings and perform the conversion in the same exact manner?

Thanks!
Ufraw can be used from command-line, which makes it easily scriptable. If your camera is supported or if you have the correct color profiles and other information (as in you know the settings your camera uses) for it then it's definitely possible to use it to convert your pictures automatically.

Imagemagick is a grat CLI image processing tool as well, but not the best tool for handling RAW files. But in case you want to do any additional image processing after the RAW conversion you should definitely check it out as well.  

Actually this is pretty much what I do, shoot in RAW and then use a script with Ufraw and Imagemagick to generate JPG files for web use.

---

### Post by mcduck on 2009-07-16
> **FrankVdb said:**
> What do you need RAW for? Why not use the highest JPG quality available on your camera? The only advantage of RAW is that it allows you to edit in 16-bit mode before going back to an 8-bit JPG picture. Apparently you just want to batch convert without adjusting your picture. That means that you should be shooting JPG instead of RAW.
If he'd shoot in JPG he wouldn't even have the option to use the RAW files if he feels that some of the pictures would benefit from it.

Shooting in RAW and converting automatically still leaves you with the RAW files, not to mention that this also allows more options for the JPG generation than using the RAW+JPG option in the camera would do.

---

### Post by megamania on 2009-07-24
> **mcduck said:**
> Actually this is pretty much what I do, shoot in RAW and then use a script with Ufraw and Imagemagick to generate JPG files for web use.
I'm very interested in understanding how you process your raw pictures.
In my experience, the only way to have a RAW picture look like the jpeg in terms of colors/light is to open it with the Nikon software (I have a D90) under windows (which I don't use). I (quickly) tried most raw-processing programs for linux and had the same problem.

Apparently there's something I'm missing... can you share your experience? I'd be happy to be able to properly handle raw files with linux.

---

### Post by Whiffle on 2009-07-24
Look into ufraw ( [http://ufraw.sourceforge.net/](http://ufraw.sourceforge.net/) ), its a plugin for the Gimp used for processing RAW.

sudo apt-get install ufraw

---

### Post by mcduck on 2009-07-24
> **megamania said:**
> I'm very interested in understanding how you process your raw pictures.
In my experience, the only way to have a RAW picture look like the jpeg in terms of colors/light is to open it with the Nikon software (I have a D90) under windows (which I don't use). I (quickly) tried most raw-processing programs for linux and had the same problem.

Apparently there's something I'm missing... can you share your experience? I'd be happy to be able to properly handle raw files with linux.

Ufraw with the camera's color profile file works great. (for D90 you can get the profile from UFRaw web site, alternatively you'll also find it in the Windows software disk that came with the camera.)

As long as you have the color profile any RAW program should be able to give you as good results as the Nikon's software does.

---

### Post by megamania on 2009-07-24
> **mcduck said:**
> Ufraw with the camera's color profile file works great. (for D90 you can get the profile from UFRaw web site, alternatively you'll also find it in the Windows software disk that came with the camera.)

Ahhhhhhhh. I'll check it out as soon as I get back home.

Thanks a lot! :-)

---

### Post by megamania on 2009-07-26
> **mcduck said:**
> (for D90 you can get the profile from UFRaw web site, alternatively you'll also find it in the Windows software disk that came with the camera.)

I feel quite stupid, but... I downloaded the color profile but can't understand where to put it or how to select it.

I tried from "options", but with no success. I've been searching the net but found no solution, which makes me think it *has* to be simple...

---

### Post by stani on 2009-08-26
From now on your problem will be solved as Phatch 0.2: can do automatic batch processing of RAW files (but also SVG,...). Moreover you don't have to script anymore. For more info see:
[http://ubuntuforums.org/showthread.php?t=1178224&highlight=phatch](http://ubuntuforums.org/showthread.php?t=1178224&highlight=phatch)

where you also find installation instructions.

---

