---
title: "Trying to save a watermark brush in Gimp"
date: 2012-08-08
forum: Multimedia Software
---

### Post by mohawk69 on 2012-08-08
I have been trying to save a watermark brush in Gimp. I have created the image, but all the tutorials are instructing me to save it in my Brushes folder, but not telling me how to find said folder, or the user is on a PC which does not help me...I really need a step by step on how to find this. Please.

---

### Post by ajgreeny on 2012-08-08
All the brushes seem to be either in the hidden folder .gimp in your home, or in a variety of /usr/share/gimp/2.0/brushes and other folders in /usr/share.

Run the command ```
locate -i brushes | grep gimp
```and you will see where they all are. However, I have no idea how you actually save an image as a brush, so will leave you to search that for yourself.

---

### Post by mohawk69 on 2012-08-08
Thanks for the help...I will investigate more tonight. I have a good idea of how to save them, it's just finding the folder seems to be a problem.

---

### Post by mohawk69 on 2012-08-10
Ok that helped me find the file to save the new brush in. But now it is not allowing me to do so:

Saving '/usr/share/gimp/2.0/brushes/bds.gbr' failed:

Could not open '/usr/share/gimp/2.0/brushes/bds.gbr' for writing: Permission denied


It's my computer, I or my partner installed Gimp, when I go to change the folder's Permissions it says I am not the owner or whatever and that I am not allowed to (!) 

Any ideas?

---

### Post by ajgreeny on 2012-08-11
If you are sure that is where the file should go you will need to save it somewhere in your /home and then copy it with ```
sudo cp */path/to*/bds.gbr /usr/share/gimp/2.0/brushes/
```You can not save anything to system folders in the root filesystem as an ordinary user unless you use **sudo** to raise your permissions temporarily.

---

