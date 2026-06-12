---
title: "Help with script to autorun multimedia"
date: 2014-04-15
forum: Multimedia Software
---

### Post by rlaracuenti on 2014-04-15
New to bash scripting but so far things have been pretty straightforward. Basically trying to make this as easy as possible so other people can simply drop videos/images/pdfs in certain folders and the computer will autoplay them full screen and loop on boot. I'm half way there (pulling my hair out trying to get windows to do the same - what a nuisance), trying to deal with what happens when a genius puts images and videos at the same time. I know I can nest the if statements to set a priority (if no images then check video folder etc) but it doesn't seem like the most elegant way to go.

I'm curious to see if I can accomplish the same thing with just one folder. Where you can put images, documents, pdfs, powerpoint (hopefully...stubborn people) and it will autoplay them. Just not sure how to do it. I figured out how to return the number of files in the folder but not the type of files for example how many *.pdf 's are there in folder X? 

This is what I've got so far. Any pointers would be appreciated. Right now it's just set to echo to test the functionality. Trying to make it as idiot proof as possible.



```
#!/bin/bash

# a script to autoplay anything in certain folders

path_to_images="/home/bothed/Documents"
path_to_videos="/home/bothed/Videos"

# Other things to do:
# Add pdf and powerpoint functionality
#
minimum_image=30

#######################################################################
# Checks the folders to see how many files are there
#######################################################################

number_of_images=$(ls -1 $path_to_images | wc -l)

#echo $number_of_images

number_of_videos=$(ls -1 $path_to_videos | wc -l)

#echo $number_of_videos

echo "Minimum of $minimum_image must be in the folder dummy"
######################################################
# Test to see if there are images in the images folder
######################################################
if test  "$number_of_images" -ge "$minimum_image" 
    then
    # Change to run image command
    # eog -s $path_to_images
        echo "There are $number_of_images images that can be displayed"

else notify-send 'Images' 'There are no images to be played' -t 10000

fi
######################################################
# Test to see if there are videos in the videos folder
######################################################


if test  "$number_of_videos" -ge "$minimum_image" 
    then
    # Change to run video command
    # vlc -f -l $path_to_videos
        echo "There are $number_of_videos videos that can be played"

else notify-send 'Videos' 'There are no videos to be played' -t 10000

fi


```

---

