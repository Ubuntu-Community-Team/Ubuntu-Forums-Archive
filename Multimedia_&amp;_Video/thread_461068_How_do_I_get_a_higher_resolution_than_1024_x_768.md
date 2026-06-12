---
title: "How do I get a higher resolution than 1024 x 768"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by Nickhalliwell on 2007-06-01
I am using an Nvidia GE Force 7300 Card and cannot get anythuing higher than 1024 x 768.  Anyone any ideas where there might be drivers that can give me a higer resolution?

---

### Post by Bluecube on 2007-06-01
Search on the forums for info on how to change the res as there are plenty of threads giving the solution. You have to manually edit a text file. It's very easy but IMHO it shouldn't be necessary...

---

### Post by miggols99 on 2007-06-01
You can run
```
sudo dpkg-reconfigure xserver-xorg
```
And set up the resolutions.

---

### Post by Electric_Cowboy on 2007-10-15
While browsing through the X11 config files I found the following code in the comment
section of xorg.conf ,maybe it might be helpful. 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

So I typed that into Konsole to see what would happen, and the first thing it asks
is what video driver to use, since I have an Nvidia e-GeForce 7100 GS video card
I selected the "nv" driver, if you don't know what video card your using it might
be safe to select "vesa" or "vga".

Next it offers a list of what resolutions you want enabled, you might want to
un-select 640 x 480 since anything below 800 x 600 is mostly useless.

I enabled 800 x 600 and the next two higher resolutions "1024 x 768"
and the one just above it, leaving all other resolutions disabled.
Then after tapping the tab key to reach the <ok> and pressing return
then I typed ```
exit
``` to get out of Konsole.

After rebooting the system and logging back on, I went to system settings
clicked on Monitor and Display, clicked on the admin button at the bottom 
right hand corner, you might have to use the scroll bars to reach it.
Next adjust the resolution the way you want it, then click on Apply
click on Ok at the prompt then close the panel, all done!

However there are no promises it won't be right back at 640 x 480
the next time you reboot, since this appears to be only a temporary fix
to an even greater problem.

---

### Post by doKtor_hallam on 2007-10-16
ok, i have been scanning the forums for this topic, and this thread seemed to be helpful. i did the konsole commands, and effected all settings that you mentioned. i rebooted. the only problem i have now is i run kubuntu, and my system settings has no monitor properties window that i can find (and no admin button on bottom right either)
could this be because you run ubuntu instead? or gnome as opposed to kde?
i think the console may have helped, i just cant figure how to change the resolution afterwards.

anyone?

(insert all the proper pleases and thank yous )
:D

---

### Post by doKtor_hallam on 2007-10-16
what if i simply go back into konsole, run the commands, and disable all resolutions but the one i want? would this force it into what i am after? (which is 1024x768)

---

### Post by doKtor_hallam on 2007-10-16
errrr, that was supposed to say 1024x768
the smiley ate the 8.
1024x76 would be a pretty awKward resolution......

---

### Post by doKtor_hallam on 2007-10-16
well, this did not work. so i am still in need of some app to effect changes to my resolution. all i am finding in the repos seem to be gnome based.
i tried resapplet, which is gnome based, but it is only installing with options for small resolutions under 1024x768. i cant figure out how to make anything larger. the konsole commands listed above arent seeming to work either, does anyone know of an effect app that will work for this?
and just for reference i run an onboard ati rage 3d pro.

thanks everyone

---

### Post by TNakos on 2007-10-16
i had this problem in 7.04 easy to fix using dpkg reconfig.

---

### Post by doKtor_hallam on 2007-10-16
ok, well, i guess i will check ati for any latest drivers, then i will go back to dpkg reconfig and try again.
i can add the resolutions i want in reconfig, and when i exit and save it is also saving a backup of the file, but then i reboot and it is reverting back. i will check further and see that it is in fact saving the changes properly i guess.
i will let you know.
thanks

---

