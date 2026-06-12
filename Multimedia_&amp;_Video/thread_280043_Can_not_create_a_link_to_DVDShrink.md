---
title: "Can not create a link to DVDShrink"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by gargoyle on 2006-10-18
I installed Wine and DVDShrink but I did not create a link to my desktop.

I tried making a link but instead of running the program it wants to install it again if I click on the link on desktop.

I can run the program by going into my computer and double clicking on it. 

Why does not the desktop link work properly?? And how do I correct it?

---

### Post by x64Jimbo on 2006-10-18
You'll want to create a shortcut with this syntax:
wine </path/to/windows/binary.exe>
Make sure you're linking to the program you double-click on, not the installer file (you may want to delete the installer just to eliminate confusion)

---

### Post by gargoyle on 2006-10-19
Ok I tried to create a laucher for the program how ever it fails to launch.

This one was attemp #1 
**/home/ed17/.wine/drive_c/program\ files/dvd\ shrink/dvd\ shrink\ 3.2.exe**
It produced this error.
*Details: Failed to execute child process "/home/ed17/.wine/drive_c/program files/dvd shrink/dvd shrink 3.2.exe" (No such file or directory)*

This was attempt #2
**/home/ed17/.wine/drive_c/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe**
It produced no error but again it did nothing at all. I was as I had not click anything at all.

The ogrinal file names have capital letters and space in the name,I tried both with and without capital letters.

You said :**Make sure you're linking to the program you double-click on, not the installer file (you may want to delete the installer just to eliminate confusion)**

There is only one "exe" file in directory. But it produces 2 different results depending on where or how it is exexcuted.

If I double click it from the Nautils browser the program runs properly.

If I use the **make a link**
Here is the properties of it 
**/home/ed17/.wine/drive_c/Program Files/DVD Shrink/DVD Shrink 3.2.exe**
It wants to install the program, and not run it.

So how can the same **Program** give 2 differnt results??
Any ideas as to what I should do??

---

### Post by x64Jimbo on 2006-10-19
Go back and read my post. You have to run wine with the program's executable as the main argument.

---

### Post by srt4play on 2006-10-19
Try this:

```
wine "c:\program files\dvd shrink\dvd shrink 3.2.exe"
```

---

### Post by ahaslam on 2006-10-19
My launcher look like this:

***wine /home/ahaslam/.wine/drive_c/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe***

Tony.

---

### Post by aidanr on 2006-10-19
i tried dvd shink with wine and for me the ripping starts off fine and progressively slows down to a crawl, xdvdshink is native and is really good, not as good as dvdshink for reauthoring, nor is it as fast as dvdshink (under windows anyway) but it's a good alternative [http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

---

### Post by gargoyle on 2006-10-20
First off thanks for the replies on my problem.
After 11 different iterations I finally found one that worked.
**wine /home/ed17/.wine/drive_c/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe**

which turns out to be like Anthony Haslam's one
**wine /home/ahaslam/.wine/drive_c/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe**

Unfortunately for me I was not aware of Anthony's post so I had to work it out for myself. It a learning experience so the effort was not wasted.

It seem that space inside the file structure cause problems, it seem that this has been reported as a bug in Ubuntu if I read one post correctly. So you need to place a ** \ ** after any space such as **Program\ Files ** and **DVD\ Shrink\ 3.2.exe** for it to work properly. Spaces in file name and directories may not be a problem in Win but it still pose a slight problem in Ubuntu.

To aidanr:
I do not see where DVDShrink is any slower on Ubuntu then running in Windows. The only problem was with a badly scratched dvd with my Samsung drive had problems reading. It seems like each dvd drive is different in its read capabilities. Just like everything else in electronics the newest drive seems to work best.

I saw xdvdshink before but I was used to using DVDShrink so I though I would give it a try before going for xdvdshink. Maybe in the future I might try it out but for right now I will stick with DVDShrink.

Again I would like to thank all of you that posted trying to help me solve my problem.

---

### Post by ahaslam on 2006-10-20
Glad to see that you got it going ;)

Another native option is k9copy, it's good for a complete copy to a 4.7GB disc, but not as good as DVD Shrink for re authoring or quality settings.


Tony.

PS. I find it just as slow through WINE as under Windows ;)

---

