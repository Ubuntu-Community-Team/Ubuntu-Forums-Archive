---
title: "Ripping audiobooks [Tip]"
date: 2010-04-13
forum: Multimedia Software
---

### Post by kumoshk on 2010-04-13
For those of you who rip audiobooks from CD to listen to as OGG Vorbis files (on an MP3 player or some such), I have concocted a quick way of doing so, while minimizing the the file size and retaining sufficient quality. Each CD's worth of these files should be just over 11MB. The resulting files work a lot better than Speex, in my opinion, actually. This is a semi-manual method, however, as you have to make the folder hierarchy yourself (but it's faster in practice than using Sound Juicer or some such).

Anyway, I use the regular cp command instead of cdparanoia, seeing as it's a lot faster (and I don't notice a huge difference in the results, either). I use oggenc to encode the OGG Vorbis files (you can tweak the settings there if you want higher or lower quality, but this works perfectly for me, and I always have plenty of room for loads of books on my Sansa e280 this way).

Install a program that lets you right-click on a folder in nautilus to open a terminal starting at that directory:
```
sudo apt-get install nautilus-open-terminal
``` (You may have to log out or restart before this program will work)

Make sure oggenc is installed:
&#8226; If you have 32-bit Ubuntu, do this:
```
sudo apt-get install vorbis-tools
```
&#8226; If you have 64-bit Ubuntu 9.10, the above will likely install a faulty version of oggenc. There's a bug or something in 64-bit. Instead, get the source code for the 32-bit version, compile it on a 32-bit installation of Linux and put it on your 64-bit computer; make sure you have the libraries that allow you to run 32-bit binaries, and put a link to oggenc in your path (e.g. ~/bin). Let me know if you need help there.

Make a script with the following code:
```
#!/bin/bash

cp ~/.gvfs/"cdda mount on sr0"/* ./
eject -r
oggenc -q 0.0 --resample 14000 --downmix *.wav
rm *.wav

```
You may need to switch "cdda mount on sr0" with something else. Check ~/.gvfs/ for directories, and whatever is in there when your CD is mounted should be what you should replace it with.

Put the script in your path (e.g. ~/bin), and make it executable (right click->properties->permissions and check to make it executable). Name it whatever you want, but remember what you name it. Don't give it an extension. If you had to create ~/bin you may have to log out or restart before it will be in your path.

Now, you're ready to rip CDs quickly and get tiny ogg files that are still listenable (for audiobooks):
Make the folder you want to rip the CD into. Put in your first CD. Right-click on the folder and open a terminal. Make sure your CD is mounted (if you have automount off like I do; I just click on it in Nautilus, and then hit the back button). Run your script (by typing its name). It'll rip it all for you and then eject it; put in your next CD and make a directory for your next CD while it's converting the files. Go on until you're done. Feel free to close all your terminals when they're done encoding the OGG Vorbis files.

Someone who knows more about scripting could make it encode each track directly after it finishes (rather all the tracks after the entire CD finishes). They might also be able give arguments to the script so you don't have to make the folder number manually. (i.e. running 'myScript 1' might create a folder entitled 1 and rip/encode the tracks into it). Anyway, I'm sure there are lots more improvements that could be made. If you want the terminal to close on its own when it's finished encoding, just type "yourScriptName; exit" instead of just your script's name.

If you want some kind of progress indicator, or more ripping options use cdparanoia instead of cp (e.g. 'cdparanoia -B' or some such instead of 'cp ~/.gvfs/"cdda mount on sr0"/* ./'), but from my experience it is significantly slower.

---

