---
title: "Help with MenCoder"
date: 2009-02-16
forum: Multimedia Software
---

### Post by mr_gourami on 2009-02-16
This I think should be simple. But i am so lost and frustrated. A friend of mine wrote this code for me so i can very easily rip dvds, a seperate file for each title. Now what i want to do instead is rip a dvd that has only one title and instead rip each chapter individually. I have been trying for the last 2 hours to figure out how to edit the code below so instead of ripping mulitple titles instead it rips chapters. But I am lost. I failed computer coding in highschool and i see i still have no clue as to what i am doing. I am sure it should be simple, could anyone just modify that code below so instead of titles it rips chapters? 
I know the code is -chapters but i have no idea how to work with the $ or counters or whatnot... I would ask my firend who set this up but he left the country yesterday





#!/bin/bash
#
# Encode DVD files to mpeg4 for Madison
#
# Usage: ripdvd <name> <nr_of_titles>

if [ $# -ne 2 ];
then
echo "Usage: ripdvd <name> <nr_of_titles>"
exit 0
fi

counter=1

while [ "$counter" -le "$2" ];
do
nice -n 19 mencoder dvd://"$counter" -o "$1"_"$counter".avi -oac mp3lame -ovc xvid -lameopts preset=medium:vol=7 -xvidencopts turbo:pass=1:bitrate=-716800:threads=2 -alang en
nice -n 19 mencoder dvd://"$counter" -o "$1"_"$counter".avi -oac mp3lame -ovc xvid -lameopts preset=medium:vol=7 -xvidencopts pass=2:bitrate=-716800:threads=2 -alang en
counter=$(( $counter + 1 ))
done

---

