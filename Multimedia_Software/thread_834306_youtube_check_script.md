---
title: "youtube check script"
date: 2008-06-19
forum: Multimedia Software
---

### Post by Creative2 on 2008-06-19
hello folks 

edit: mm maybe wrong section

this script take a txt file where you have saved your youtube's links (one link for line)

and evalute if there is someo problems like :

 This video has been removed due to terms of use violation
 Embedding disabled by request
 This video has been removed by the user 

```
#!/bin/bash
# ===========================================================
#                            TubeCheck!
#                               of
#                 Creative2 an Kubuntu 8.04 user
#          http://fuocotools.byethost13.com/index.php
#                          18 june 2008
#
#     .
#
# ===========================================================
# Copyright (c) 2008-2010 Creative2 an Kubuntu 8.04 user
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included
# in all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR
# OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
# ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
# OTHER DEALINGS IN THE SOFTWARE.
# 
# Except as contained in this notice, the name(s) of the above copyright
# holders shall not be used in advertising or otherwise to promote the
# sale, use or other dealings in this Software without prior written
# authorization.
#
# 
#This script read a txt file where you have written youtube links and if there is problems you can look log file .
#
#
#
start=$SECONDS # take the time with this 
#
#
#
#
defaultfile="$HOME/links.txt"
oldlog="/tmp/youtubevalute/youtubeprolems.txt" #create some variables with own value
OutFolder="/tmp/youtubevalute/"
#
#Remove http:// from your links file 

Removehttp() {
	clear
http=$(sed -n "/http/p" "$defaultfile")
if [[ "$http" == "" ]];
then
	echo "links without http....OK..continue..."
else
	echo "links with http.......OK..continue..."
	sed -i "s,http://,,g" "$defaultfile"
	echo "rewriting links...done"
fi
}

if [[ -e "$defaultfile" ]];
then
Removehttp
else 
echo "no default links file detected...continue"
fi


#Remove the old log
if [[ -e $oldlog ]]; then
   rm $oldlog
fi

#ìRemove the old folder
if [[ -e $OutFolder ]]; then
   rm -R $OutFolder
fi
#
#Read where is the file with links 
   echo -n "Where is links file ? If you press ENTER I will use $HOME/links.txt  : "
   read 
if [[ "$REPLY" == "" ]]
then
   echo 'You have write nothing so Now i will read the default files! Lazy man'
elif [[ -e $defaultfile ]]
then
   echo "Ehi are you dummy?Default file doesn't exist . Plese create one first here $HOME/links.txt  "
   exit
else
   echo "Ok file exist now i will read it "   
   defaultfile="$REPLY"
	Removehttp
fi
#
#
#Create a folder where i can download youtube page if doesn't exist
if [[ ! -e $OutFolder ]]; then
   mkdir $OutFolder
fi
#
#
while read line; do
   nomemodificato=$(echo  "$line" | sed "s,www.youtube.com/watch?v=,,g")
   outputpath="$OutFolder""$nomemodificato"
   wget "$line" -O "$outputpath".html 
   echo -n "$line"  >> "$OutFolder"/youtubeprolems.txt
   echo -n " "
   sed -n '/This video has been removed due to terms of use violation/p' "$outputpath".html  >> "$OutFolder"/youtubeprolems.txt
   echo -n " "
   sed -n '/Embedding disabled by request/p' "$outputpath".html  >> "$OutFolder"/youtubeprolems.txt
   echo -n " "
   sed -n '/This video has been removed by the user/p' "$outputpath".html  >> "$OutFolder"/youtubeprolems.txt
   echo -n " "
   echo "" >>"$OutFolder"/youtubeprolems.txt;
done < "$defaultfile"
#
#
#
#
#
 
problema1=$(sed -n '/This video has been removed due to terms of use violation/p' "$OutFolder"/youtubeprolems.txt )
problema2=$(sed -n '/Embedding disabled by request/p' "$OutFolder"/youtubeprolems.txt )
problema3=$(sed -n '/This video has been removed by the user/p' "$OutFolder"/youtubeprolems.txt)

if [[ "$problema1" == "" && "$problema2" == "" && "$problema3" == "" ]] ;
then
   echo " Very well your links are good aheare  No problems ^__^'  "
else 
   echo "Damn there are some problems with your links  ? type the name of your prefered text editor like:  kate or gedit to open your log"
fi
read 
if [[ "$REPLY" == "" ]]
then
    exit
else
   $REPLY "$OutFolder"/youtubeprolems.txt
fi
   echo ""
   echo ""
   echo ""
   echo ""
   echo "Well i remember you your log is here    $oldlog"
   echo ""
   echo ""
   echo "your youtubepage are here  $OutFolder"
   echo ""
   echo ""
   echo ""

end=$SECONDS
   echo "S:)that's all folks"
   echo "i have made this job in  : $(($end - $start)) second "
exit 0
```

---

