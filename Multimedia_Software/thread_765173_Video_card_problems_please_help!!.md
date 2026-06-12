---
title: "Video card problems please help!!"
date: 2008-04-24
forum: Multimedia Software
---

### Post by diirka on 2008-04-24
Ok I have searched for the last hour and cant find anything that helps with my problem.  I have a dell inspiron 5100 and I cant get the desktop effects to work.  Im guessing its because i dont have the right video drivers installed but I'm not even sure what video card I have (I bought the laptop from a friend that didnt know the specs.)  Any help would be great. Thanks.

---

### Post by andrebrait on 2008-04-24
Laptop specs please

---

### Post by diirka on 2008-04-24
What specs are you looking for?  Im not sure what video card it has, thats why I dont know if I have the right drivers or not.  Is there a way to find the specs?

---

### Post by andrebrait on 2008-04-24
Well... this should be written somewhere in the laptop, but...

Ok, so... do ubuntu present you with a message saying your drivers aren't installed?

Anyway, it seems it uses an ATi Radeon 7500 with 32MB. It's a pretty old laptop, isn't it? ^^

Anyway, it seems to be good too...

So... if Ubuntu don't recognize it and show you the message, from the Restrict drivers manager, you can download Envy and see if it solve the problem for you. For Hardy, envyng is present in the package manager, synaptic.

But, it shouldn't solve your problem. It's a pretty old GPU, so it shouldn't even support the effects required for the 3D Desktop.

---

### Post by diirka on 2008-04-24
yea your right it is old and it is a radeon 7500. So there is noway to get the desktop effects to work with this card?  Also is there a video card you would recomend?

---

### Post by prshah on 2008-04-24
> **diirka said:**
> yea your right it is old and it is a radeon 7500. So there is noway to get the desktop effects to work with this card?  Also is there a video card you would recomend?

```
lspci | grep -i vga
``` will tell you about the card.

For desktop effects, you need to support compositing mode. This is activated automatically when you start the desktop effects manager (usually compiz).

Open a terminal (Applications-Accessories-Terminal) then type the following command and post the output of the command here.

```
compiz --replace
```

That will tell us where the problem lies with desktop effects.

---

### Post by diirka on 2008-04-24
diirka@diirka-laptop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
diirka@diirka-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity

---

### Post by Sunflower1970 on 2008-04-24
Isn't this one of the ATI cards that's blacklisted in Hardy...?

Look here: [http://ubuntuforums.org/showthread.php?t=722943&highlight=ati+mobility+7500](http://ubuntuforums.org/showthread.php?t=722943&highlight=ati+mobility+7500) 

There does seem to be a way to get it to work, somewhere in that thread. 

I know compiz works on that card since I have a Thinkpad R40 running Gutsy now with full 3-D.

---

### Post by andrebrait on 2008-04-24
```
andrebrait@andrebrait-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

That's what this copmmand says to my 8600GT
What's that advice in the last line?

---

### Post by prshah on 2008-04-24
> **andrebrait said:**
> ```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```
What's that advice in the last line?

To delete the value, press Alt+F2  and give the command ```
gconf-editor
```, then navigate to the value mentioned above and delete it.

---

### Post by andrebrait on 2008-04-26
[http://ubuntuforums.org/showthread.php?t=766802](http://ubuntuforums.org/showthread.php?t=766802)

---

