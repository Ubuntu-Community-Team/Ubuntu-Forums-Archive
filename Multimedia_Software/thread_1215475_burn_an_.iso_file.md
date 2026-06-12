---
title: "burn an .iso file"
date: 2009-07-17
forum: Multimedia Software
---

### Post by wstay on 2009-07-17
I burnt an .iso file to a dvd rewritable using Brasero and also using K3b and choose either Burn Image or Data Project. Either way I burnt and after burning successfully, I find that my dvd contains one whole .iso file. How can I burn an .iso file so that my dvd would contain all the individual files from the .iso file? Can someone please help.

---

### Post by ~sHyLoCk~ on 2009-07-17
> **wstay said:**
> I burnt an .iso file to a dvd rewritable using Brasero and also using K3b and choose either Burn Image or Data Project. Either way I burnt and after burning successfully, I find that my dvd contains one whole .iso file. How can I burn an .iso file so that my dvd would contain all the individual files from the .iso file? Can someone please help.

You definitely didn't select the option "Burn image"

---

### Post by wstay on 2009-07-17
I try again and select Burn image from Brasero and also try Burn DVD ISO Image from K3b to burn an .iso file. Both burnt successfully BUT I still got the one whole .iso file instead of all the indidvidual files from the .iso file.
So what is wrong and where could the error be?

---

### Post by lisati on 2009-07-17
Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by wstay on 2009-07-18
> **lisati said:**
> Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I follow the instruction and right click the iso file and select Write to Disc... After Disc write is successful, I still got a .iso file on my dvd.
Could it be a problem with my Recorder or the rewritable dvd or the recording software or the computer or the system as a whole?

---

### Post by martinbaselier on 2009-07-18
Have you tried mounting the iso? 

Open a terminal
use cd to go to the direcotry where the iso is located
mkdir iso
sudo mount NAMEOFIMAGE.iso iso -t iso9660 -o loop

The folder where the iso is located, will now contain a map named "iso".

What do you see when you look to the contents of that map?

---

### Post by wstay on 2009-07-18
> **martinbaselier said:**
> Have you tried mounting the iso? 

Open a terminal
use cd to go to the direcotry where the iso is located
mkdir iso
sudo mount NAMEOFIMAGE.iso iso -t iso9660 -o loop

The folder where the iso is located, will now contain a map named "iso".

What do you see when you look to the contents of that map?

I can see all the individual files in the iso folder.
So do I burn the dvd from there and which burner would you reckon I use?

---

### Post by martinbaselier on 2009-07-19
Personally is use brasero and I never encountered the problem you have. I thought the iso might be faulty, but apparently it isn't. Really strange.

---

### Post by wstay on 2009-07-21
> **martinbaselier said:**
> Personally is use brasero and I never encountered the problem you have. I thought the iso might be faulty, but apparently it isn't. Really strange.

I try another computer with Mandriva installed and burn the same iso using Brasero - Burn image. The dvd burnt successfully with all the indvidual files on the dvd.
Its hard to say where the problem is on my Ubuntu computer where the iso won´t burnt as individual files onto the dvd.
Is it the same as, if I burn from the folder where I mounted the iso using Create a data dvd with Brasero?
Is there a software to extract the iso file into a folder, instead of using the terminal to mount it?

---

