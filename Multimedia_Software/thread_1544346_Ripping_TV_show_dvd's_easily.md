---
title: "Ripping TV show dvd's easily?"
date: 2010-08-02
forum: Multimedia Software
---

### Post by __guppy on 2010-08-02
*I'm not interested in your view of the legalities involved - I own the dvds I wish to rip which is legal where I live, if you wish to debate the legalities please make a separate thread.*


I'm looking for a way to easily rip dvd's containing multiple features / episodes - preferable as easy as poping in the dvd pushing a button and coming back a later to repeat the process.

The reason that I want it that simple is not just that I'm lazy ;) but that it's alot of episodes and having to manually go through them would take even longer ( there are usually 2-4 episodes per disc )

Looking forward to your answer

---

### Post by dv3500ea on 2010-08-02
There are a number of programs that can rip from DVDs.

Try typing 'dvd rip' without the quotes into the search box in ubuntu software centre.

btw, you have a legal right to make a 'backup' of your DVDs

---

### Post by Naitsirhc Hsem on 2010-08-02
Thoggen is the best

---

### Post by __guppy on 2010-08-04
> **dv3500ea said:**
> There are a number of programs that can rip from DVDs.

Try typing 'dvd rip' without the quotes into the search box in ubuntu software centre.

btw, you have a legal right to make a 'backup' of your DVDs

Yes I'm aware that there are multiple programs that can rip features from DvDs ( my favorite so far is dvd::rip ), what I'm looking for is a program that will let me rip multiple features on the same disc in one go.

ie say I have a dvd "TVSHOW" on this there are 16 chapters - 4 of theese are episodes, I want to be able to tell the program to rip those 4 to what I name them ( and their subtitles ) - and then come back once it's done.

With 'dvd::rip queue' I can sort of do it by creating 4 projects per disc but it is rather cumbersome and each result will be named '<projectname>/avi/<chapter>/<chapter>.<ext>'

Which means a lot of renaming, I was rather hoping for a neat package for it - but it seems it doesn't exist.

---

### Post by Antenne on 2010-11-03
> **__guppy said:**
> I was rather hoping for a neat package for it - but it seems it doesn't exist.
I'm started out to do the same thing (storage space to waste and annoyed of dvd-drive noise) - did you find a suitable solution?

Thanks.

---

### Post by DarrenCT on 2010-12-08
You could just select each title from the drop down box in Handbrake, and create a new name for the file (i.e. Desperate Houswives S01E01)  Then "add to queue".  The click run once you've got them all selected!  I'm doing this right now.

---

### Post by Sosume on 2011-01-02
This is also something I regularly want to do, for instance making sure all the shows I've got on dvd can also be watched easily from XBMC.

I haven't found a good solution yet, so I wrote a simple script based on handbrake cli. Not that special, but does the job.

```


#!/bin/bash
# extractdvd.sh
# input must be:
#    - <devicename> (which can be anything lsdvd takes)
#    - <outputfolder> where do you want the ripped series
#    - <outputname> the base name of the output

INPUT_DVD=$1
OUTPUT_FOLDER=$2
OUTPUT_NAME=$3

LSDVDOUTPUT=$(lsdvd "$1")

# if available get the title and get the number of titles
TITLE=$(echo "$LSDVDOUTPUT" | grep -i Disc | sed 's/Disc Title: //g')
NOMTITLES=$(echo "$LSDVDOUTPUT" | grep -i Length | wc -l)
echo $NOMTITLES

# iterate over each title
for (( c=1; c <= $NOMTITLES+1; c++ )) do
        PREFIX=''
        if [ $c -lt  10 ]; then PREFIX="0" ; fi
        OUTPUT_NAME_TITLE=$OUTPUT_FOLDER"/"$OUTPUT_NAME"-"$PREFIX$c".m4v"
        HandBrakeCLI -i $INPUT_DVD -o $OUTPUT_NAME_TITLE -t $c
done

```

---

### Post by Glimps on 2012-11-19
I've modified your script a bit to add a starting point to the episode name and I've taken the liberty to modify the output name.


Now you can do something like :

```
sudo ./ripdvd.sh /media/dvd/ /target/ soa_s03_e 7
``` 

this will starts counting at 8 (7+1) so you can rip seasons on multiple DVDs. 

My output format only adds the 01, 02 to the title to be more compatible with XMBC's scrappers. 
Code is here :

```
 [https://gist.github.com/4114957](https://gist.github.com/4114957)
```

Thanks for the script

---

### Post by overdrank on 2012-11-19
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

