---
title: "Script for automatic DVD ripping with title"
date: 2010-04-26
forum: Multimedia Software
---

### Post by eremyja on 2010-04-26
Hey everybody!

Just thought id post a little script i put together for ripping dvd's with their title!
Here it is:
```
#!/bin/bash
name=$(lsdvd -c 2> /dev/null | grep "Disc Title" | gawk '{print $3}')
HandBrakeCLI -i /dev/dvd -o /home/jeremy/movies/$name.mp4 --preset="iPhone / iPod Touch" --longest
```***NOTICE!!!***
You will need:
HandbrakeCLI ([check here]("http://handbrake.fr/downloads2.php"))
lsdvd (apt-get)
libcssdvd(to read encrypted dvds. Read on to see how to get it!)

Be sure to change "/home/jeremy/movies/" to whatever folder you want the movie! And you might need to change "/dev/dvd" to "/media/cdrom" or whatever depending on your set up! Also, you can change the preset, or even the whole handbrake command to better suit your needs!

LIBCSSDVD
run these commands:
```

sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

```And now your set to play encrypted DVDs!!

Any opinions, ideas, or suggestions are welcome!

---

