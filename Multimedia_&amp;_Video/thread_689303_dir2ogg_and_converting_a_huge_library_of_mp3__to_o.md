---
title: "dir2ogg and converting a huge library of mp3  to ogg"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by farueulogy on 2008-02-06
**[SIZE="5"]P[/SIZE]reamble - I'm tired, filled with tea and still pretty much a linux noob. Appologies for any mistakes.**

I've been trying to make the jump for ages - I plan on throwing rockbox on my ipod as soon as I have made all my music files nice uniform .ogg 128kbps files. Uniformity is good when it comes to files.

The program soundconverter is not my answer. You'd think it really should be but it loves to die on me. It's suitable for a couple of files but just gets sticky and weird when I have tried to stick all my music in.

My suggested solution is dir2ogg. The drawbacks include working from the command line and duplicating your library, requiring some harddrive space (explained below)

So basically:

1-Copied my library. It normally resides on my external hdd so I just copied it over to my laptops main hdd.

This was because dir2ogg doesn't support defining a destination folder for your converted files. It just sticks your ogg next to your mp3. If you move these you'd have to recreate your folder structure. By copying your library you can keep your folder structure then modify your terminal command to tell it to delete the mp3 its working from. You'll still have your mp3 in your old library.

2-Head over to the synaptic package manager and install dir2ogg package.

3-Slammed the following into the terminal:

> dir2ogg -r -q4 /location/of/copied/library -x

What does that mean you ask?** It's good habit to google all commands before executing them as they could be malicious and destroy your system.**

But just so you know what I think they mean:

dir2ogg = indicate the script/program to act
-r = convert music in all folders and subfolders
-q4 = convert at 128kbps
/location/of/copied/library = the address of the folder with the music you want to convert
-x = delete the folder once conversion is complete

You can also use dir2ogg for m4a and wma but not subfolders. You have to go through them album by album. The command I use goes a little something like this for m4a:

> dir2ogg -d -m -q4 /location/of/copied/album -x

Basically meaning:

-d = only this folder
-m = convert m4a

---

