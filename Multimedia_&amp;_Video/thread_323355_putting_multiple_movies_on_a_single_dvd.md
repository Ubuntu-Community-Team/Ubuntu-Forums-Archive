---
title: "putting multiple movies on a single dvd"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by manish_m on 2006-12-22
i have couple of vcd's. i want to tanscode them, so that i can have multiple movies on a single 
(4.7 Gb) dvd.
can anybody tell me how to do this ? i m using dapper.
thanks in advance.

---

### Post by taurus on 2006-12-22
DeVeDe can do that and it's available from the repos...

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install devede
```

---

### Post by tagra123 on 2006-12-22
> **manish_m said:**
> i have couple of vcd's. i want to tanscode them, so that i can have multiple movies on a single 
(4.7 Gb) dvd.
can anybody tell me how to do this ? i m using dapper.
thanks in advance.


ffmpeg, mencoder, or tovid will get the files into the correct format to use. Tovid is the easiest to use.


dvdauthor should work to create the dvd structure.

I use it from the command line.

Create an xml file containing the files.

SomeMovies.XML
```

<dvdauthor>
    <vmgm />
    <titleset>
        <titles>
            <pgc>
                <vob file="File1.mpg"  />
		<vob file="File2.mpg"  />
		<vob file="File3.mpg"  />
            </pgc>
        </titles>
    </titleset>
</dvdauthor>

```


I use the script below it explains itself.

you'll need to create a directory (folder) named DVD -- see script


For my example you would have a drive mounted on /media  as tempdrive so for this example 

mkdir /media/tempdrive/mpgfiles 
mkdir /media/tempdrive/mpgfiles/DVD

gedit makedvdfrommpg

```
#!/bin/bash
#Change MYVIDEOPATH to where you store your viideos for this purpose, make a directory named DVD
MYVIDEOPATH=/media/tempdrive/mpgfiles/

if [ $# -ne 1]; then
         echo "Please Supply Filename and path to SOMEFILE.XML"
         exit 127
    fi
echo "Preparing MPG files for the DVD"
dvdauthor -o $MYVIDEOPATH/DVD -x  $1
echo "Writing DVD TO DISC"
growisofs -speed=1 -Z /dev/dvd -dvd-video $MYVIDEOPATH/DVD
echo "EJECT DVD"
eject /dev/cdrom
echo "$1 DVD Completed"
```

save the file and then 

chmod +x makedvdfrommpg.sh

now whenever you want to burn a movie dvd you can use the script to make and burn your dvds 

./ makedvdfrommpg SomeMovies.XML


once you know you have a good dvd then delete the contents of the MYVIDEOPATH/DVD folder.

Quick answer but drop a note if you have questions. Of all the gui programs I found this to be the easiest method -- right on the command line.

---

### Post by Jose Catre-Vandis on 2006-12-26
Thanks tagra123, this method works well for mpg files created by tovid, which refused to burn :)

---

