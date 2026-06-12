---
title: "dvd decrypter problem"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by cmongini on 2006-02-02
i have installed dvd shrink and decrypter following 
[http://www.ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink+decrypter](http://www.ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink+decrypter)

win32codecs and libdvdcss2 are installed, DMA as well.
 dvdshrink seems to be ok (actually not really tried yet!) but dvd decrypter says that it does not recognize any drives. (same problem that some people had in the thread above!) i tried to fix the problem with the suggestion by awtomlinson: 
> i have the solution to dvdshrink not recognizing my dvd or cd drives. in winecfg, even though the drive mapping will appear, you must select the drive, then click Show Advanced. Then, under Type, ensure it is set to CD-ROM. even though winecfg mapped the drive as /media/cdrom0, its type was defaulted to local hard drive. everything works great now.
i set my drive to CDROM as described, went to advanced, but the option "Autodetect from Drive" is not implemented yet on my machine! i don´t know what should i give in " manually assign" 

an other problem that might be related:  in [http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

there is a suggestion  to set in settings > dvd I/O  >interface to SPTI Microsoft. This choice can´t be eanbled on my machine...... 
can anybody help me? 
it was already kind of a hassle to come to this point of the installation, so i would like to continue....

thanks in advance

---

### Post by Sutekh on 2006-02-02
I experienced this problem using DVD Decrypter. You should be able to fix this by running 'winecfg' and settings the windows compatability for DVD Decrypter to Win NT 4.0.

---

### Post by grimmson on 2006-02-02
I had the same problems. Try to configure additional drives in wine be for installing programs. I had to uninstall wine, delete the wine dir, reinstall, set nt4, add additional drives then install for everythin to work properly. good luck.

---

### Post by cmongini on 2006-02-03
thanks for the suggestions, i followed them and now , when i run the decrypter it doesn´t tell me anymor that he doesn´t detect any device, but: 
see attachment....

---

### Post by Sutekh on 2006-02-03
Yeah you want the additional drives, in 'winecfg' use the Autodetect button in 'Drives'

Then make sure that your cdrom drive is set.

Choose the CDROM device, in my screenshot its /media/cdrom - H:

Choose 'Show Advanced' - and make sure the Type is CD-ROM

---

### Post by cmongini on 2006-02-03
i did it but my situation looks like that! ( the little_caesar is just the dvd i have in the drive)

---

### Post by Sutekh on 2006-02-03
What version of wine are you using?  It looks different to mine.  I have wine 0.9.6.

---

### Post by cmongini on 2006-02-03
mine is the actual one ( i just downloaded it today again...following the tip of grimmson) it says wine version :CVS   in the about window, and  wine 20050725
in the terminal if i ask wine --version...probably i wouldn´t be able to download a previous one....

---

### Post by Sutekh on 2006-02-03
The latest version (as of today) is now 0.9.7.

Your version - 20050725 is very old (25 July 2005).  How did you download it.  Using apt-get or another way?

---

### Post by Sutekh on 2006-02-03
I just checked out the [Ubuntu Repositories]("http://packages.ubuntu.com") and noticed that the version of wine available through them is 20050725.

So for you to get the latest version of wine, you will need to update your sources.list.  First you should backup the current one
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_20060204
```
(I just used todays date to make it unique)
Then you need to edit the list and add the WineHQ repositories in
```

sudo gedit /etc/apt/sources.list

```
Just paste these lines in somewhere near the end
```

deb http://wine.sourceforge.net/apt binary/
deb-src http://wine.sourceforge.net/apt source/

```
Once you have added the Wine repositories, you can save the file and then you can use apt at the terminal to install wine or use Synaptic.

The apt way
```

sudo apt-get update
sudo apt-get install wine

```
It should recognise that you have a version of wine installed and that the new one should replace it.
If it installs ok then you need to run the configuration program
```

winecfg

```

Then follow the options (adding extra drives, change drive type to CD-RROM) to setup wine.  Then you should be able to get DVD Decrypter working, fingers crossed.

---

### Post by cmongini on 2006-02-04
thanks for your extensive help, unfortunately the wine server seems to be down, but i´m sure i´ll be able to get the packets in the next days...

---

