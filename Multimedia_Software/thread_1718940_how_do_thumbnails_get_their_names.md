---
title: "how do thumbnails get their names"
date: 2011-04-01
forum: Multimedia Software
---

### Post by jahst on 2011-04-01
If I delete my .thumbnails folder then look at a single image on my PC the thumbnail is automatically generated for that image. It always has some obscure id name such as 972c045e3b1386e78d95423022eb4fae.png

My guess is it's some type of hash or md5 name of the file.

So say I have a picture called cat.jpg

I used this image [http://upload.wikimedia.org/wikipedia/commons/2/22/Turkish_Van_Cat.jpg]("http://upload.wikimedia.org/wikipedia/commons/2/22/Turkish_Van_Cat.jpg")
and saved it as cat.jpg in /home/user/pics/cats

How exactly is the .thumbnail file name generated?

Goal:
My goal is to write a script that will periodically scan my pics folder and all subfolders and automatically generate a thumbnail for the photos without me having to first open the folder [thus having to wait for the thumbnail to be automatically generated]


Why:
Because I have old slow machines trying to access a central photo folder via wifi. The photos change often meaning that each time I try to access the photos, I have to wait for the thumbnails to be generated. So I want to have a script that will check and generate them for me before I have to look in each folder and wait. I'll probably just add it to a cron job and run each night or something.

Please help point me in the right direction as how the thumbnail name is generated. Any advice on the script would help, but i'd like to attempt it myself first.

I just cant figure out how that thumbnail name is generated.

Thanks!

---

### Post by lloyd_b on 2011-04-01
The filename is the md5 hash of the URI (Uniform Resource Identifier) for the file.  Basically the file name with full path, in the form:```
file:///home/user/image.jpg
```You can generate these from the command line with a command such as ```
echo -n "file:///home/user/image.jpg" | md5sum
```

Lloyd B.

---

### Post by jahst on 2011-04-01
Thanks. I was just logging back in to say I found the answer on another site.

[http://www.he1ix.org/2010/05/how-is-the-thumbnail-filename-related-with-the-file-it-belongs-to/]("http://www.he1ix.org/2010/05/how-is-the-thumbnail-filename-related-with-the-file-it-belongs-to/")

Was harder to find online than I thought it should be.
So now it's on these forums too.

Thanks again,




[COLOR="Red"]EDIT - what do I do about file names with spaces?[/COLOR]
My little script works great as long as no space in file name.
Even the command directly in the terminal gives wrong answer if the file name has a space in it. 

I've tried single quotes, double quotes, single quotes inside double quotes, even tried changing echo -n to echo -e and backslashing to escape double quotes around file name. What am I missing here?

---

### Post by jahst on 2011-04-01
[COLOR="Red"]What do I do about file names with spaces?[/COLOR]

My little script works great as long as no space in file name.
Even the command directly in the terminal gives wrong answer if the file name has a space in it.

I've tried single quotes, double quotes, single quotes inside double quotes, even tried changing echo -n to echo -e and backslashing to escape double quotes around file name. 

What am I missing here?

---

### Post by jahst on 2011-04-01
Got it.. needed to replace white space with %20 of all things.

And my final little script looks like this. I didnt test it large scale yet, but will over the next week or so. Should be much quicker than clicking on each folder and waiting for the thumbnails. This way they will be generated in advance. 

Did I do the GNU thing correctly... I just followed what I saw somebody else do for a simple script. Seems to simple to need it.


```


#!/bin/bash


# must have ImageMagick & Totem installed
photo_path="/home/user/photos"
tn_dim="128x96"


photo_exts=( .JPG .JPEG .PNG )
video_exts=( .MOV .AVI .MP4 .MPG .MPEG ) 




##############################################################

# 	 Copyright 2011 Christopher Bowhuis
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.


##############################################################





# First, we test whether bash supports arrays.
arraytest[0]='Array will be set if arrays work or' || (echo 'Failure: Unable to set array. Arrays may not be supported in this version of bash.' && exit 2)






IFS=$' \t\n'  # Ensure default IFS is set
# Internal Field Separator set to newline
OLDIFS=$IFS
IFS='
'





for files in ${photo_exts[@]} ; do 
echo "Searching for $files"
echo "in path $photo_path"
echo "----------------------------------"

	for i in `find $photo_path -type f -iname "*$files"`  # change -iname to -name for case sensitive 
	do

		echo "$i"
		ised=`echo "$i" | sed -e 's, ,%20,g'`  # needed to fix filenames with spaces
		file_hash=$(echo -n "file://$ised" | md5sum | awk '{ print $1 }')

			if [ -f ~/.thumbnails/normal/"$file_hash".png ] # check if thumbnail already exists
			then
				echo "$file_hash already exists...skipping"
			else
				echo "Generating thumbnail $file_hash"  
				convert -thumbnail $tn_dim "$i" ~/.thumbnails/normal/"$file_hash".png  # Generates photo thumbnails
			fi

		echo ""
		echo ""

	done
	
done


for files in ${video_exts[@]} ; do 
echo "Searching for $files"
echo "in path $photo_path"
echo "----------------------------------"

	for i in `find $photo_path -type f -iname "*$files"`
	do

		echo "$i"
		ised=`echo "$i" | sed -e 's, ,%20,g'`  # needed to fix filenames with spaces
		file_hash=$(echo -n "file://$ised" | md5sum | awk '{ print $1 }')

			if [ -f ~/.thumbnails/normal/"$file_hash".png ] # check if thumbnail already exists
			then
				echo "$file_hash already exists...skipping"
			else
				echo "Generating thumbnail $file_hash"  
				/usr/bin/totem-video-thumbnailer "$i" ~/.thumbnails/normal/"$file_hash".png   # Generates video thumbnails
			fi

		echo ""
		echo ""

	done
	
done







IFS=$OLDIFS # Restore old Internal Field Separator
echo "End of Script"
read




```


So I will use this code to ensure my thumbnails get updated by the only powerful PC I have, then I sync the generated thumbnails to the weaker machines. Especially helpful when trying to generate 1000's of thumbnails over a wifi using an 800mh PC. Would take me hours to do it that way. This way about 5 minutes to sync the thumbnails.

Hope it helps someone else.

---

