---
title: "Burn VCD from DAT"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by psynaps3 on 2007-03-06
Hi,

I have a couple of DAT files (copied from a VCD) which I need to use to create a VCD. There are 2 DAT files (totalling around 700mb) which I need to put into a single VCD. Which program can I use to do this task? k3b doesn't accept .DAT files as input while burning VCD's.

Thanks

---

### Post by tagra123 on 2007-03-06
I'm guessing here but I believe those will need to be converted back first.

An easier option if you have the vcd would be to create an iso image and burn the image to cd.

you can do this in gnome by right clicking on the cd icon or using the dd command.

---

### Post by psynaps3 on 2007-03-07
I am under the impression that creating a VCD filesystem and copying the DAT files to the respective directory should be enough. I am however not aware of any tools for this purpose. 

I do not have the VCD with me. Ain't DAT files in VCD really mpeg files?

---

### Post by tagra123 on 2007-03-07
Have you tried this command
TRY THIS

TO CONVERT FOR VCD
```
ffmpeg -i mybinfile.bin -target ntsc-vcd mybinfile-VCD.mpg
```

TO CONVERT FOR DVD
```
ffmpeg -i mybinfile.bin -target ntsc-dvd mybinfile-VCD.mpg
```


If the ffmpeg for the VCD converts the file then you can use k3b to easily burn the VCD.

---

### Post by psynaps3 on 2007-03-07
I do not have a BIN image with me. All i have is the DAT file directly copied from the VCD using windows. I need to put this back into a VCD in linux.

---

### Post by tagra123 on 2007-03-07
ffmpeg -i mybinfile.dat -target ntsc-vcd myfile-VCD.mpg

---

### Post by psynaps3 on 2007-03-12
Update:
used vcdgear to convert the DAT to MPEG-1
used k3b to burn the MPEG as VCD

many thanks for all the help.

---

### Post by andoty_jazz on 2007-05-16
> **psynaps3 said:**
> Update:
used vcdgear to convert the DAT to MPEG-1
used k3b to burn the MPEG as VCD

many thanks for all the help.

VERY VERY NICE FIND **[COLOR="Red"]psynaps3[/COLOR]**

THANK YOU VERY VERY VERY MUCH. 

You gave me a lot of help. 

Thanks again **[COLOR="Red"]psynaps3[/COLOR]** and everyone. :guitar:

---

### Post by etcpool on 2007-06-03
Nice howto!


Thanks!

---

### Post by bulletboy on 2007-06-07
Hi all,
I used a very cool package called devede to convert the .DAT to a burnable image and then used 
k3b to burn the VCD.
I found this much easier.
Hope this helps.

---

### Post by rereynanda on 2008-05-28
hi,,,
i'm a newbie..
i want to ask you about ffmpeg.
what command i should run to convert video .DAT to video .mpeg with ffmpeg??
i've read ffmpeg manual pages and documentation, but i can't understand.
need your help ,please...
thanks for the attention..

---

### Post by Nawaf on 2008-07-16
> **bulletboy said:**
> Hi all,
I used a very cool package called devede to convert the .DAT to a burnable image and then used 
k3b to burn the VCD.
I found this much easier.
Hope this helps.
Thanks for the tips bulletboy
It's always easier to use a graphical interface

---

