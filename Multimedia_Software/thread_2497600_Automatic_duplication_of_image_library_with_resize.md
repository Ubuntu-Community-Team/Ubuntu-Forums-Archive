---
title: "Automatic duplication of image library with resize"
date: 2024-05-11
forum: Multimedia Software
---

### Post by pnuke on 2024-05-11
Hi,

I have a large image library of some hundreds of GBytes of all my life photos in high quality. I would like to create a copy of that library for a simple webserver gallery and would like to keep the size of the images below 4k with a higher compression. 

Is there a way to fully automate that process like rsync will keep track of two directories just with the additional resize? So everytime I run the script it'll just update the newly added images?

---

### Post by TheFu on 2024-05-11
Yes. This is possible.  There are resize scripts in these forums.  I've posted mine a few times over the decades.  The move/relocate/output location is something you'll need to create in a custom script - or pay someone to do.

Look at the "convert" tool in the ImageMagick tools.  You'll want to test on just a few files while you create the script.  Actually, I don't know if **convert** allows specifying the file size. You can definitely specify the resolution and the quality level. Then check the resulting filesize to see if it is small enough for the quality you seek.  

My image galley software will take a source directory of images, then creates 1024, 800, 640, 320 sized versions, if requested.  I only do 1024 and 800 sizes myself.
Say a source image is 1.7MB.
1024x575  resolution image is 28K.
800x449  resolution image is 20K.
The 100x56  thumbnail is 4.0K.

I don't see getting down to 4KB to be very useful, unless you only want thumbnails.

---

### Post by pnuke on 2024-05-17
It was quite the journey. Convert itself is not the problem, its the automatic duplication ala rsync thats challenging. 
Here is my script, which is unique for this purpose, it seems noone has attempted something like that ever before (at least nothing comparable can be found)

```

#!/bin/bash


originalsPicturesFolder="/home/xxx/Pictures/"


#transfer newly added images in the library to the photoview server
#there is one local export-direcory as reference. All photos and videos are resized amd transcoded into the export-directory
#from there the images are transferred to the server where the are automatically imported


#first detox all filenames (remove special characters and spaces), because that could mess up the following operations
/usr/bin/detox -r $originalsPicturesFolder


#convert all png/tif images and remove the originals
find $originalsPicturesFolder -iname "*.png" -exec /usr/bin/mogrify -format jpg -quality 85 "{}" \;
find $originalsPicturesFolder -iname "*.tif" -exec /usr/bin/mogrify -format jpg -quality 85 "{}" \;
find $originalsPicturesFolder -iname "*.png" -exec rm "{}" \;
find $originalsPicturesFolder -iname "*.tif" -exec rm "{}" \;


#convert all MOV files (MOV extension will be still present after that, MOV.mp4, but its an insecure hassle to change that in find-exec
find $originalsPicturesFolder -iname '*.mov' -exec ffmpeg -i {} -vcodec h264 -acodec mp2 -hide_banner -loglevel error -f mp4 {}.mp4 \; -exec touch -r {} {}.mp4 \;
find $originalsPicturesFolder -iname "*.mov" -exec rm "{}" \;




#then delete all files that are not present in the master anymore, without updating anything
/usr/bin/rsync -r --delete --existing --ignore-existing $originalsPicturesFolder /mnt/picExport




#parse array from rsync
i=0
while read line
do
    filearray[ $i ]="$line"
    (( i++ ))
    newFile="/mnt/picExport/"$line
    masterFile="$originalsPicturesFolder$line"
    newDIR="$(dirname "${newFile}")"
    filename=$(basename -- "$masterFile")
    extension="${filename##*.}"
    filename="${filename%.*}"


    #rsync is returning the directory itself, so just check against the file extensions (as long as a directory is not called jpg it works, but convert will just throw an error when directory is given)
    if [[ "$extension" = "jpg" ]]; then
        #create directory if not existent
        mkdir -p $newDIR
        #reduce image quality because its mainly used on mobile and web, originals are still here so we can just crank up quality in the feature and reconvert everything
        convert $masterFile -resize "3000x3000>" -quality 60 $newFile
        continue
    fi


    if [[ "$extension" = "mp4" ]]; then
        #create directory if not existent
        mkdir -p $newDIR
        #just copy the video as there is not much to gain in transcoding
        cp $masterFile $newFile
        continue
    fi




    echo "Unkown file: "$newFile" with the extension: "$extension


#rsync is used to determine what files are new, in this special mode only the filename is compared and a list is generated
#save the output of rsync in an array
done < <(/usr/bin/rsync -rn --ignore-existing --out-format="%n" $originalsPicturesFolder /mnt/picExport)






#now push everything to the library server
/usb/bin/rsync -ae --delete "ssh -i /home/xxx/.ssh/id_rsa" /mnt/picExport/ root@server:/media/pics




```

---

