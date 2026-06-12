---
title: "How to Batch Encode to Xvid and Divx"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by chollis888 on 2007-04-11
Hey guys thought I would share a script I created to encode video to Xvid or Divx. It will also batch encode videos. All you'll need to do is install mplayer and mencoder, add codecs for the video formats you like to play and follow this easy how-to:
 
I call this script encoder.
 
I guess 1st you want to set it up to batch encode.
 
Open a terminal:
 
```
 mkdir -p ~/encoder/batch/ 
```2nd:
 
```
sudo gedit /usr/local/bin/encoder
```copy and paste to empty file:
 
```
#!/bin/bash

  BATCHLIST=~/encoder/batch.list
  BATCHFILE=~/encoder/batch/
  VIDEO="$1"
  OUT="$HOME/encoder/divx.${1%.*}.avi"
  OUT2="$HOME/encoder/xvid.${1%.*}.avi"
  RUN="gnome-terminal -x"

 
 

  function Divx1Pass {
    mencoder $VIDEO -ovc lavc -oac copy -ffourcc DX50 -o $OUT ||  mencoder $VIDEO -ovc lavc -oac pcm -ffourcc DX50 -o $OUT
}

  function Divx2Pass {
        mencoder $VIDEO -ovc lavc -lavcopts vpass=1 -oac copy -ffourcc DX50 turbo -o $OUT || mencoder $VIDEO -ovc lavc -lavcopts vpass=1 -oac pcm -ffourcc DX50 turbo -o $OUT
              mencoder $VIDEO -ovc lavc -lavcopts vpass=2 -oac copy -ffourcc DX50 -o $OUT || mencoder $VIDEO -ovc lavc -lavcopts vpass=2 -oac pcm -ffourcc DX50 -o $OUT
}

  function Xvid1Pass {
        mencoder $VIDEO -ovc xvid -oac copy -xvidencopts bitrate=760 -o $OUT2 || mencoder $VIDEO -ovc xvid -oac pcm -xvidencopts bitrate=760 -o $OUT2
}

  function Xvid2Pass {
       mencoder $VIDEO -oac copy -ovc xvid -xvidencopts pass=1 -o /dev/null || mencoder $VIDEO -oac pcm -ovc xvid -xvidencopts pass=1 -o /dev/null
              mencoder $VIDEO -oac copy -ovc xvid -xvidencopts pass=2:bitrate=760 -o $OUT2 || mencoder $VIDEO -oac pcm -ovc xvid -xvidencopts pass=2:bitrate=760 -o $OUT2
}



   function EditBatch {
       nautilus $BATCHFILE

}


   function Batch {
          ls $BATCHFILE > $BATCHLIST
            for i in $( ls $BATCHFILE ); do
             mencoder $BATCHFILE$i -oac copy -ovc xvid -xvidencopts pass=1 -o /dev/null || mencoder $BATCHFILE$i -oac pcm -ovc xvid -xvidencopts pass=1 -o /dev/null
              mencoder $BATCHFILE$i -oac copy -ovc xvid -xvidencopts pass=2:bitrate=760 -o $HOME/encoder/xvid.${i%.*}.avi || mencoder $BATCHFILE$i -oac pcm -ovc xvid -xvidencopts pass=2:bitrate=760 -o $HOME/encoder/xvid.${i%.*}.avi
          done
         
}

  function BYE {
       echo done
       exit
   }

  function Divx {
       echo "encoding with lavc to Divx5"
       OPTIONS="1pass 2pass"
       select opt in $OPTIONS; do  
          if [ "$opt" = "1pass" ]; then 
               Divx1Pass
             echo finished encoding $VIDEO with one pass
              exit
          elif [ "$opt" = "2pass" ]; then
              Divx2Pass
            echo finished encoding $VIDEO with 2 passes
              exit
          else
                echo bad option
           fi
       done
    }

function Xvid {
       echo "encoding with Xvid to Xvid"
       OPTIONS="1pass 2pass"
       select opt in $OPTIONS; do  
          if [ "$opt" = "1pass" ]; then 
               Xvid1Pass
             echo finished encoding $VIDEO with one pass
              exit
          elif [ "$opt" = "2pass" ]; then
              Xvid2Pass
            echo finished encoding $VIDEO with 2 passes
              exit
          else
                echo bad option
           fi
       done
    }
#if [ -z "$1" ]; then
# echo usage: encoder filename.avi
 # exit
#fi


OPTIONS="Divx Xvid EditBatch RunBatch Quit"
           select opt in $OPTIONS; do
               if [ "$opt" = "Quit" ]; then
                echo done
                exit
            elif [ "$opt" = "Divx" ]; then
                 Divx
            elif [ "$opt" = "Xvid" ]; then
                 Xvid
            elif [ "$opt" = "EditBatch" ]; then
                 EditBatch
            elif [ "$opt" = "RunBatch" ]; then
                 Batch
             OPTIONS="ClearBatch KeepBatch"   
          select opt in $OPTIONS; do  
          if [ "$opt" = "ClearBatch" ]; then  
            rm -v -f $BATCHFILE*.*
            rm $BATCHLIST
             BYE
         elif [ "$opt" = "KeepBatch" ]; then  
            BYE
          else
                echo bad option
           fi
               done

            else
                echo bad option
           fi
       done


```save and exit
 
3rd:
 
```
sudo chmod +x /usr/local/bin/encoder
```At this point encoder should be working and can be used like so:
 
```
encoder /path/to/file.whatever.
```It can be used to encode just about anything mplayer can play to divx or xvid, and will use the encoder folder in your home directory for output.
 
To batch encode you will need to put either the file to be encoded or a link to that file in the batch folder located within the encoder folder in your home directory(take out any spaces in the names) and then: 
 
```
encoder
```select run batch.
 
Now to make this even more useful you can set it up to be used by right clicking a file like so:
 
```
gedit ~/.gnome2/nautilus-scripts/encoder
```cut and paste to empty file:
 
```
#!/bin/bash
 
gnome-terminal -x encoder $1

```exit and save.
 
next:
 
```
chmod +x ~/.gnome2/nautilus-scripts/encoder
```now:
 
```
nautilus ~/.gnome2/nautilus-scripts/
```Ok you should be good to go you can right click on individual files go to scripts --> encoder or just right click on empty space in a directory to run your batch.

---

