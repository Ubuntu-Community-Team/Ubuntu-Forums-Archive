---
title: "Giving GNUM3d a facelift."
date: 2010-02-27
forum: Multimedia Software
---

### Post by LostDakota on 2010-02-27
I have to say, gnump3d is quite possibly my favorite piece of software. It was one of the first programs I installed when I switched to Ubuntu. I truly use it everyday. That being said, I felt like I needed it to be a bit more graphical. The one thing (and I mean 1) that I liked about iTunes was the CoverFlow. So I decided that I needed those all-important album covers. So I hacked together a bash script that would grab them for me and place them in the Album directory so they could be used in the html code. Now before I get into the process, you must know that I'm still learning so this/these scripts are in no way perfect, so use at your own risk. As a base, I had some .jpgs left over from the past, so I just renamed the Folder.jpg and put them in the Album directories. Then I used this for the ones I still needed.

```
#!/bin/bash
#Script to grab album covers from amazon.com in a round about way.

wget -O temp "http://www.albumart.org/index.php?srchkey=$1&itempage=1&newsearch=1&searchindex=Music"

sleep 1 && cat temp | grep amazon.com | head -n 1 | cut -f6- -d"'" | cut -f1 -d"'" > album ;

sleep 1 && wget -O Folder.jpg -i album ;

sleep 1 && rm temp album ;

mogrify -resize 256x256 Folder.jpg

```**Explanation:** To use the script, save it to /usr/bin and chmod 755 it. Next you have to cd to the directory of the album. 
```
drew@ubuntu-Server:~/Media/Music/Arctic Monkeys/Favourite Worst Nightmare$ AlbumScrub.sh favourite+worst+nightmare
```AlbumScrub.sh is the script and the next bit is the album name. You have to add the '+' so that albumart.org can query for the image. The first wget grabs the page and stores it in 'temp'. The next line strips away all the crap so you're left with just the url to amazon image which get stored in another temporary file 'album'. The next wget actually grabs the image from 'album' and saves it to 'Folder.jpg'. That is the meat of the script. All that's left is to rm 'temp' and 'album'. Mogrify (part of imagemagik) resizes the file to 256x256 (not necessary, but I find it appealing to have them uniform). 

I know how terribly inefficient this must seem to all the vets out there, but I find it does exactly what I need to clean up the stragglers. 

After I got done with that, I figured I should have band photos in the parent directories. So what follows is an adaptation of the first script. This one uses google instead of albumart.org (hence the '-U Mozilla' because google doesn't like wget. You have to masquerade as Mozilla for them to allow downloading the page). Like the first one, you must cd to the directory to have it work properly. Instead of '+', you have to use '%20' in between the words. I.E. ```
BandScrub.sh 10%20years%20band
```

```
#!/bin/bash

wget -O temp -U Mozilla "http://images.google.com/images?q=$1&um=1&hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&ie=UTF-8&sa=N&tab=wi"

sleep 1 && cat temp | tr '>' '\n' | grep imgurl | head -n 1 | cut -f3- -d"=" | cut -f1 -d"&" > band ;

sleep 1 && wget -O Folder.jpg -i band ;

sleep 1 && rm temp band ;

mogrify -resize 500x500 Folder.jpg
```Now a plea to the wise: Help me make this more efficient. I'm not sure yet how to traverse the directories and use pwd to get the input for the scripts. If you have 40G of music, you can imagine how tedious this can become. I don't intend this to be the defacto way to get art, but like I said it works for me. Hopefully someone will find this useful. 

I've attached what my setup looks like to give you some idea of what I was trying to accomplish.

---

